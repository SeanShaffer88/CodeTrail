# Decision log

## 2026-10-26 baseline

| Decision | Status | Reason and alternative |
|---|---|---|
| CodeTrail name/repository | Confirmed by owner | Selected from naming options; preserve this name |
| Complete and returning beginners | Confirmed by owner | Guided fundamentals first; advanced practice later |
| Python first | Confirmed by owner | One coherent curriculum; multiple launch languages expand scope |
| Free/offline/no account | Project requirement | Local learning and privacy; cloud features need a separate decision |
| Three release assets with x86/x64 | Updated project requirement | EXE chooses native build; one MSI installs x86 on either OS; ZIP contains both |
| Rust/Tauri/editor/SQLite | Proposed | Fits Rust preference and editor needs; WPF retained as accessibility/packaging alternative |
| WASI Python and constrained worker | Investigate | Explicit host capabilities; x86 interpreter performance/tracing unresolved |
| Code Replay | Investigate | Makes execution understandable; needs truthful trace and limit tests |
| 8 units/24 lessons/48 missions/3 capstones | Proposed | Complete fundamentals scope; revise effort from one tested unit |
| No AI in version 1 | Proposed | Authored feedback supports offline learning; AI requires separate consent/evaluation |
| English initially, localization-ready UI | Proposed | Controls initial content cost without hard-coded UI text |
| MIT for original material | Standing default applied | Dependencies/assets retain their own terms |

## Foundation decisions

Resolve exact runtime/versions, x86/x64 support, WebView distribution, Windows support matrix, measured budgets, data/migration contracts, and full-gate command. Failure to support x86 or adequate isolation requires a material decision; never silently remove an architecture or weaken containment.

## Estimate record

PLAN.md contains a preliminary 49–87 working-day full-product range. Each implementation slice must record scope/effort beforehand, actual outcome afterward, and reasons for major differences. No implementation slice has begun.
