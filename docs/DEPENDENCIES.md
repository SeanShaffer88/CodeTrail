# Candidate dependency register

No dependencies are adopted or pinned. Upstream documentation was consulted on 2026-10-26; this does not establish future bundle compatibility, security or complete license compliance.

| Candidate | Purpose | Adoption checks | Replacement and exit |
|---|---|---|---|
| Rust/Windows APIs | Operations and worker control | Pin toolchain; verify both host targets, CRT/runtime obligations | Large: retain operation protocol, replace engine |
| [Tauri 2](https://v2.tauri.app/security/) | Rust desktop shell | Pinned licenses/plugins, advisories, release activity, UI automation and packaging | Medium/large: retain operations, replace shell |
| [WebView2](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution) | Editor and local UI | Microsoft terms, lifecycle, servicing/network behavior, x86/x64 bundles | Large: replace UI host or web editor |
| [Monaco](https://github.com/microsoft/monaco-editor) | Code editing | Upstream identifies MIT; verify pinned notices and actual accessibility | Medium: keep document/trace model separate, swap editor adapter |
| [SQLite](https://www.sqlite.org/copyright.html) | Local progress/history | Upstream deliverable public domain; binding licenses, backup and build options separate | Medium: preserve exports, migrate records |
| [CPython WASI](https://github.com/python/cpython/tree/main/Platforms/WASI) | Contained Python | Pin stable CPython/SDK/runtime combination, PSF/component terms, modules, advisories | Medium/large: replace runtime through adapter, rerun curriculum |
| [Wasmtime](https://docs.wasmtime.dev/stability-platform-support.html) | Wasm execution/control | Pinned Apache-2.0/exception notices, dependencies, advisories, Windows x86 Pulley evidence | Medium: replace runtime behind worker protocol; revalidate all containment |
| [Wasmi](https://github.com/wasmi-labs/wasmi) | Alternative Wasm interpreter/WASI | Exact license/release/audit scope, Windows targets and performance | Medium: compare through same protocol/corpus |

Record exact versions/hashes, maintenance health, licenses, replacement effort and notices during feasibility. Recheck on major versions or annual refresh. Permissive licenses are preferred; copyleft, commercial or unclear terms need owner review before adoption. A dependency's historical audit is not certification of CodeTrail.
