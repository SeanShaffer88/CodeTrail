# CodeTrail product and delivery plan

Baseline: 2026-10-26. The name, beginner audience, and Python-first direction are confirmed. Content quantities, stack, budgets, and estimates are proposals. No application or curriculum has been implemented.

## Purpose and completeness

CodeTrail should help someone who has never programmed, or is returning after a break, understand code and enjoy making it work. A complete first release takes a learner from their first edited program through variables, decisions, loops, collections, functions, debugging, tests, and small projects.

Learners should be able to explain simple code, repair mistakes, solve an unfamiliar beginner task without a template, and export a working project. Core workflows must work offline, preserve work after interruption, provide staged help, and be accessible through keyboard, screen reader, and CLI. This is a fundamentals course, not a claim of complete Python mastery or job readiness.

## Project brief

| Field | Baseline |
|---|---|
| Users | Complete and returning beginners, learning independently. Initial tone should suit teens and adults; reading level and age range need learner testing. |
| Kind | New Windows desktop application with full CLI coverage. |
| Core workflows | Start a lesson; edit/run; understand/debug; practice/review; build/export; resume/recover. |
| Language | Python first; later tracks require a separate language adapter and authored curriculum. |
| Platform | Native x86 and x64 builds required. Evaluate Windows 10 22H2 and supported Windows 11 releases on x64. Exact compatibility follows tests and dependency lifecycle checks. |
| Stack | Rust/Tauri/editor/SQLite candidate, subject to feasibility; no adopted dependencies. |
| Network and AI | Core learning offline. Optional user-controlled update check only. No AI in the proposed first release. |
| Data | Local code, attempts, concept evidence, notes, settings, and bounded diagnostics; no account or credentials. |
| Scale | One local learner profile initially; growth workload of 1,000 content items and 10,000 attempts, with 10x and feasible 100x checks. |
| Risk | Apply Tier 2 engineering review to untrusted execution and import/export: threat model, SBOM, dependency review, and failure testing. |
| High-impact actions | Running learner code, overwriting exports/imports, resetting progress, restoring backups, migrations, installation/update/uninstall. |
| Stability | Commands, content schema, saves, and settings Experimental during development; declare Stable contracts at 1.0 with tested migrations. No plugin API initially. |
| License and business model | MIT for original material; preserve third-party terms. Free, optional quiet donations, no ads or data sales. |
| Governance | Elite v1.1 Core, desktop/CLI requirements and project defaults; latest three-asset Windows release policy. AI and parallel-work requirements apply if those scopes are adopted. |

## First minute and learning cycle

Open directly to a tiny editable Python program with a visible Run button. Ask the learner to change a value and run it; output and a small scene respond. No setup questionnaire, account, terminal, or language installation comes first. After success, offer Continue learning and Explore on my own.

Use the sequence **Predict → Run → Investigate → Modify → Make**, followed by optional later review. Begin with code comprehension, then gradually remove support until learners write independently. This adapts PRIMM; its published evidence concerns teacher-led secondary-school learning and does not prove effectiveness for this app or adults. [Study and scope](https://eprints.gla.ac.uk/229013/).

Activities should teach one main concept and fit roughly 5–15 minutes. Include prediction, arranging a few lines, repairing a bug, and typing real Python. Returning learners can use an optional placement activity or browse the searchable concept map.

## Three connected modes

| Mode | Experience | Outcome |
|---|---|---|
| Learn | Short explanation, runnable example, guided change, independent attempt | Understand and apply a concept |
| Explore | Code sorts parcels, routes a robot, manages supplies, or draws a pattern | Connect code with an observable result |
| Build | Project briefs, milestones, tests, optional help | Create useful ordinary Python files |

Provide a calm lesson list and an optional journey view over the same content. Story scenes are light and skippable, with complete text equivalents. Reward explaining, debugging, and improving code. Cosmetic achievements are optional. No lives, energy limits, paid hints, streak-loss punishments, compulsory timers, or public rankings in the beginner path.

## Code Replay

The distinguishing proposal is **Code Replay**: move through recorded execution events while the editor, variable values, and scene show what happened. Include an equivalent text event list for screen readers and CLI users.

Example: a loop collects two parcels when three are required. Replay shows each loop value and its stopping condition. A first hint asks the learner to inspect the stop value; a second gives a relevant example. A worked solution remains available on request, followed by a fresh transfer problem.

Replay is bounded observation of a run, not reversal of arbitrary side effects or a promise to debug every Python program. Prove line semantics, input handling, exceptions, recursion, safe value inspection, truncation, and performance before committing this feature.

## First-release curriculum

Proposed content budget: **8 units, 24 short lessons, 48 practice missions, and 3 capstone projects**. These are separate counts; review variants come from the mission pool. Re-estimate after one complete unit is authored and tested.

| Unit | Concepts | Example |
|---|---|---|
| 1. First steps | Run, edit, output, literals, variables | Change a greeting and scene label |
| 2. Values and input | Numbers, strings, types, input, conversion | Unit converter |
| 3. Decisions | Comparisons, booleans, if/elif/else | Route parcels |
| 4. Repetition | for/while, ranges, counters, termination | Collect supplies or draw patterns |
| 5. Collections | Lists, dictionaries, indexing, iteration | Small inventory |
| 6. Functions | Parameters, return values, scope, decomposition | Reusable mission steps |
| 7. Debugging and tests | Tracebacks, exceptions, assertions, edge cases | Repair a quiz |
| 8. Programs and data | Approved modules, sandbox files, JSON, project structure | Save and load project data |

Capstones: a branching text adventure, a quiz engine with a separate question file, and a task or collection tracker using sandboxed storage. Export source, required data, and a short README. Validate exports against a pinned native CPython version as well as the teaching runtime.

Advanced algorithms, interviews, web development, native GUI programming, arbitrary packages, and OS automation are outside the first curriculum. Later language tracks follow demand and execution feasibility.

## Content and feedback quality

Every activity needs a stable ID, objective, prerequisites, instructions, appropriate starter code, examples, tests, misconceptions, staged hints, reference solution, accessibility text, and provenance. Write original material.

Separate correctness from style suggestions; accept different valid algorithms. State teaching constraints before the attempt. Show expected/actual behavior and a useful failing case. Preserve raw Python errors alongside beginner explanations. For unfamiliar errors, avoid an invented diagnosis.

Progress distinguishes completion with help, independent success, and later success on a new task. Optional review uses simple documented rules. Passing tests is not proof of understanding; offline tests are inspectable, so this is not a tamper-proof certification system.

## Windows experience

Use a normal resizable window: searchable lesson list at left, editor central, scene/output beside it, and collapsible tests/hints/replay below. At small sizes use tabs for secondary panes. Keep the current objective and next action visible.

Use dark neutral surfaces and restrained red accents with complete light/high-contrast themes. Meaning never depends on color alone. Provide scalable graphics, reduced motion, adjustable editor text, visible focus, tooltips and accessible names for every interactive control. Essential guidance cannot depend on hover.

Include undo, autosave, crash recovery, recent work, restored sessions, drag-and-drop for supported files, and offline F1 help. Externalize UI strings; English is the initial content recommendation.

## Delivery milestones

Ranges assume one experienced implementer, curriculum review, and access to beginner testers. These are working-day estimates, not a promised calendar deadline.

| Milestone | Exit condition | Rough effort |
|---|---|---|
| 0. Feasibility | One editor task, contained Python, truthful replay, recovery, and clean offline packaging on x86/x64; resolve runtime/distribution choices | 5–10 days |
| 1. Foundation | Frozen operation contracts, module boundaries, schemas, test corpus, and complete validation command | 4–7 days |
| 2. Complete first unit | Three lessons, six missions, hints/review, GUI/CLI parity, recovery; observe 5–8 beginners and fix blocking confusion | 10–15 days |
| 3. Full curriculum | Remaining seven units and three capstones, all solutions/tests/hints/export paths checked | 20–35 days |
| 4. Release validation | Accessibility, security, performance, failure drills, docs, quality review, and three CI-built assets | 10–20 days |

Total: **49–87 working days**, roughly **10–18 working weeks before contingency**. x86 execution, tracing, accessibility, or learner feedback may require redesign. Record actual effort per slice and revise estimates from evidence.

The next engineering milestone should prove five things: contained Python on both architectures, a correct bounded replay, recovery of saved edits after termination, an accessible keyboard/screen-reader editor flow, and clean offline launch. Complete these before scaling curriculum production.
