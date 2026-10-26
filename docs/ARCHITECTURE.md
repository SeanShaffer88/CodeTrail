# Proposed architecture

Status: investigation, not frozen. No implementation or dependencies adopted.

## Candidate stack

Lead candidate: **Rust application operations, Tauri 2, a small TypeScript interface, Monaco Editor, SQLite, and a separate constrained Python worker**.

| Option | Benefit | Trade-off | Verdict |
|---|---|---|---|
| Rust and Tauri with web editor | Retains Rust preference and supports editor/visual lessons around one domain engine | WebView distribution, UI accessibility, IPC hardening | Investigate first |
| C# and WPF with editor component | Established Windows controls, layout, UI Automation | Changes language default; editor and sandbox still need work | Fallback if first option fails accessibility or packaging |
| Rust and native GUI toolkit | Could avoid WebView runtime | Rich accessible code editor and lesson rendering need stronger evidence | Defer pending concrete benefit |

These are fit judgments, not measured benchmarks. [Tauri security model](https://v2.tauri.app/security/), [WPF overview](https://learn.microsoft.com/en-us/dotnet/desktop/wpf/overview/).

## Boundaries and operations

~~~mermaid
flowchart TD
  GUI[Windows interface] --> OPS[Validated operations]
  CLI[CLI and JSON output] --> OPS
  OPS --> LEARN[Learning and progress rules]
  OPS --> CONTENT[Versioned curriculum]
  OPS --> DATA[Local storage and recovery]
  OPS --> SUP[Runner supervisor]
  SUP --> WORKER[Separate constrained worker]
  WORKER --> PY[Sandboxed Python runtime]
~~~

Domain modules must not import UI or storage implementations. Both interfaces call the same operations. Suggested modules: application operations, learning domain, content validation, persistence, runner supervisor, language adapter, desktop, and CLI.

Candidate operations: lesson.open, attempt.save, run.start/cancel, trace.read, hint.reveal, progress.query, review.next, project.import/export, backup.create/restore, settings.update, diagnostics.export. Also inventory document editing, undo, help, and configuration so parity covers every GUI capability. Specify typed inputs/results, stable errors, size limits, cancellation, and tests before UI wiring.

Use bounded versioned worker messages, validated paths/IDs, request correlation, and an authenticated intended-worker connection. The worker receives only explicit resources, not the privileged native command bridge or progress database. No local HTTP service is needed.

## Contained Python

Investigate pinned CPython WASI in a separate WebAssembly worker. Expose only input/output, approved read-only resources, and bounded scratch storage. No arbitrary host directories, environment secrets, sockets, shell, or process-launch capability. Exposed imports and directory capabilities determine the guest's access. [Wasmtime security](https://docs.wasmtime.dev/security.html).

**x86 is a feasibility gate:** Wasmtime's native Cranelift backend supports no 32-bit host. Pulley is a candidate interpreter, but the exact Windows target and Python performance must be tested. Wasmi with WASI is another candidate. A wasm32 guest does not imply a 32-bit Windows host works. [Wasmtime platforms](https://docs.wasmtime.dev/stability-platform-support.html), [Wasmi](https://github.com/wasmi-labs/wasmi).

Python WebAssembly has restricted/different process, threading, networking, and filesystem behavior. Publish a tested module list for the pinned runtime; no promise of arbitrary pip/native-extension compatibility. [Python availability](https://docs.python.org/3/library/intro.html#webassembly-platforms).

Native CPython in a restricted Windows process is an alternative requiring its own AppContainer/restricted-token, filesystem, network, and escape review. A subprocess, timeout, or Job Object alone is not a sandbox. Job Objects can manage limits and process lifetimes. Never silently fall back to unrestricted execution. [Microsoft Job Objects](https://learn.microsoft.com/en-us/windows/win32/procthread/job-objects).

## Initial threat model

Protect learner files, app data, OS integrity, and responsiveness against pasted/imported hostile code, malformed content, hostile output, and compromised dependencies.

- Treat guest execution, content parsing, worker messages, and UI rendering as separate trust boundaries.
- Enforce deadline/memory/output/trace limits and a reliable Stop action. Terminate stuck workers without losing editor contents.
- Never render output as trusted HTML or execute it as JavaScript. Validate native messages and block unexpected navigation. [WebView2 security](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/security).
- Bundle local assets; no remote scripts or executable community packs initially.
- Check imports for traversal, absolute/UNC/device paths, archive bombs, duplicate IDs, invalid encoding, symlinks/reparse points, and schema abuse.
- Separate the trusted judge from learner output; never accept a learner-supplied verdict. Offline grading remains advisory, without strong anti-cheating claims.
- Require exact dependency/runtime provenance, vulnerability audits, SBOM, an abuse corpus, and incident plan before public binaries.

## Storage and recovery

Installed mode uses app-owned local data; portable mode uses an explicit Data directory. Test unwritable locations and show a clear alternative. Expose data/log locations in settings/help.

SQLite is the candidate for attempts, progress evidence, settings, and revision metadata; export learner code as ordinary .py files. Version schemas/content packs and record activity version, runtime, input, and seed with runs. Never silently invalidate old work after curriculum changes.

Persist acknowledged edits durably with transactional writes and checkpoints. Restore text, cursor, selected lesson, and settings. Show saving and failed-save states honestly; crash recovery guarantees must refer to acknowledged persisted edits. Back up migrations, preserve originals on failure, quarantine malformed data, and never silently reset history.

Import/export previews conflicts and provides backup/undo. Explain how deletion affects retained backups. Bound local logs to 10 MiB or seven days, whichever is reached first; omit source, file contents, secrets, and personal paths by default. Diagnostics are inspectable and never sent automatically.

## Offline distribution

Bundle courses, help, fonts, editor, and Python assets; no CDNs or separate Python setup. WebView2 remains a deployment dependency even if Edge is present. Compare fixed-version bundling and offline Evergreen installation, including terms, servicing, x86/x64 footprint, and network behavior. Prefer a local packaged runtime for clean offline/portable use if it passes these checks. [WebView2 distribution](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution).

Freeze architecture only after exact runtime/version, licensing, standard-user behavior, Windows matrix, MSI deployment, EXE architecture selection, and performance are resolved.
