# Validation and release plan

These are proposed budgets, not measurements. Freeze them after feasibility establishes a reproducible baseline. Never silently relax them to make a failure pass.

## Performance and scale

Reference class: 4-core Windows laptop, 8 GiB RAM, SSD, standard user, cold offline launch. Record exact hardware, OS, runtime, architecture, and workload. Exercise x86 and x64 separately, including the x86 MSI-installed app on x64.

| Metric | Initial target |
|---|---|
| Cold start | p95 <= 3 seconds to editable lesson across 30 cold launches |
| Interaction acknowledgement | p95 <= 100 ms for typing, navigation, Run and Stop feedback |
| Small exercise | p95 <= 1 second after runtime ready, <= 100 lines and short tests; measure cold runner separately |
| Stop | Worker termination/stopped state <= 1 second for endless loops and blocked input |
| Autosave | Durable acknowledgement within 500 ms under normal storage; recover every acknowledged batch; visibly report save failures |
| Memory | Combined process working set <= 350 MiB idle and <= 768 MiB for standard exercise/replay |
| Storage | <= 1 GiB installed per architecture; each complete release asset <= 900 MiB including required runtimes |
| Initial runner limits | 5-second deadline, 256 MiB guest memory, 256 KiB output, 20,000 trace events and 32 MiB trace storage; calibrate against lessons |
| Search | p95 <= 150 ms across 1,000 content items; measure 10x and 100x |
| Idle work | <= 1% total CPU average over 60 seconds after settling |
| Network | Zero app-initiated requests during core learning; optional update check tested separately |

Bound caches/rendering and show trace truncation explicitly. Exercise 10x history/content and 100x where feasible. A greater-than-10% regression in any budgeted metric blocks release unless the owner approves a documented major waiver.

## Test gates and corpus

Establish formatter, strict linter, strict type checks where applicable, and the complete test suite for all domain/GUI/CLI/worker targets. Inspect the full integrated gate before merge/release. Tests in only the domain library are insufficient.

Coverage floors: 85% core/domain, 70% overall, and every safety-relevant/destructive path exercised. Every bug fix includes a regression test. Use property/fuzz tests for parsers, paths, import formats, and worker messages.

The corpus must include:

- Valid alternative solutions and common wrong answers; off-by-one loops, recursion, exceptions, empty input/EOF, Unicode and huge integers.
- Infinite loops, output floods, trace floods, filesystem escapes, blocked network/process access, hostile HTML output, malformed/oversized messages.
- Valid, malformed, oversized, legacy and corrupt imports, schemas and saves.
- Every shared operation through GUI and CLI with equivalent outcomes and actionable errors.

Record fractions by category so safety failures cannot disappear in a blended score. For every mission, run reference solutions and alternative correct solutions, reject known wrong answers, review hints/prerequisites, and test exports in native CPython.

Deliberately kill app/worker mid-save and mid-run. Test full disk, locked/read-only files, permission denial, corrupt settings/database, interrupted migration, session loss, and older saves. Preserve original data, quarantine corruption, and provide recovery.

Audit pinned dependencies, licenses, build scripts, runtime provenance, and advisories. Block known critical vulnerabilities. Produce an SBOM for shipped components. Review the threat model and private security-reporting process before binaries.

## Accessibility and learner trials

Use Windows UI Automation and Microsoft guidance; target WCAG 2.2 AA for embedded web content. Test Narrator, keyboard-only use, and another screen reader where available. Check editor focus escape, indentation/errors, execution announcements, replay navigation and scene text equivalents. [Windows accessibility](https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility).

Check light/dark/high contrast, reduced motion, 100/125/150/200/300% DPI, 200% text, mixed-DPI monitors, minimum window and 4K/ultrawide. Use Per-Monitor DPI v2 behavior, fluid layouts, scalable graphics, and full interaction states. Every control needs a tooltip plus accessible name/role/state and keyboard path; essential guidance cannot require hover.

Observe 5–8 beginners on the first unit. Formative targets: >=80% complete the first code change within a minute; >=80% recover from a representative error using guidance; >=70% solve a new related task without copying a solution. Small samples identify defects; they do not establish statistical efficacy. Re-test after fixes.

At 1.0 and major versions, require fresh-profile first run, keyboard completion of every core workflow, and an observed non-developer attempt. An owner-only user checklist is Partially Verified. Skipping the gate requires an explicit major waiver.

## Evidence and review

Keep help, command examples, architecture, decisions, limitations, corpus/PARITY, and QUALITY current. Significant claims use Verified, Partially Verified, or Unverified with conditions. Test documented commands once implemented.

An explicitly adversarial review must check placeholders, happy-path-only behavior, silent scope reduction, invented APIs/facts, filtered gates, unsupported scores, GUI-only logic, oversized modules, duplicate logic, silent data loss, swallowed errors, unbounded work, exposed secrets, unjustified dependencies, and novelty that harms native behavior.

Required real captures after a build exists: fresh lesson, successful scene, useful failed-run feedback, replay, completed project/export, recovery, settings in light/dark/high contrast. No placeholder images or invented paths.

## Exactly three release assets

Build and test from the tagged source in CI:

1. **CodeTrail-Setup.exe:** selects the native x86 or x64 installer.
2. **CodeTrail-Setup.msi:** x86 MSI installing the x86 app on x86 or x64 Windows. It does not install native x64 code. MSI cannot declare Intel and x64 together. [Microsoft platform rule](https://learn.microsoft.com/en-us/windows/win32/msi/template-summary).
3. **CodeTrail-Portable.zip:** both portable builds, LICENSE, component notices and a PORTABLE note covering launch, storage, dependencies and unsigned status.

No extra loose portable EXE, installer bundle ZIP, checksum asset, or winget entry. Keep hashes in release notes/CI evidence. Re-download published files, verify hashes, MSI architecture, archive contents, and launch/install behavior before claiming shipment.

Test standard-user operation, EXE selection, MSI x86-on-x64 behavior, offline clean install, portable data locations, upgrades, rollback and data preservation on uninstall. Retain the previous release. Disclose unsigned status and actual runtime dependencies.
