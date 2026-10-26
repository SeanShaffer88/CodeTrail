## TL;DR

**CodeTrail** is a planned Windows program that helps complete and returning beginners learn Python by changing code, seeing what happens, solving puzzles, and making small projects.

**Status: planning.** This repository contains the product and engineering plans. There is no application, runnable course, or installer yet.

CodeTrail will be completely free: no paid tiers, purchases, advertising, or sale of user data. Optional donations will never unlock features or interrupt learning.

## The planned experience

- **Learn:** short lessons introduce one idea at a time.
- **Explore:** visual puzzles make the effect of code easy to see, with equivalent text descriptions.
- **Build:** small projects become ordinary Python files learners can keep.
- **Understand:** replay a recorded run to inspect variables, decisions, loops, and errors.
- **Return:** autosaved work, local progress, and optional review help learners resume.

Core learning will work offline without an account, a separate Python installation, or an AI service. Python is the confirmed first language; additional languages are a later direction.

## Project documents

| Document | Purpose |
|---|---|
| [Product plan](docs/PLAN.md) | Audience, experience, curriculum, scope, and delivery milestones |
| [Architecture](docs/ARCHITECTURE.md) | Candidate stack, operations, isolation, and data safety |
| [Capability matrix](docs/PARITY.md) | Include, Defer, Reject, and Investigate decisions |
| [Validation](docs/VALIDATION.md) | Budgets, tests, accessibility, learner trials, and releases |
| [Decisions](docs/DECISIONS.md) | Confirmed choices and recommendations |
| [Dependencies](docs/DEPENDENCIES.md) | Candidates and adoption checks |
| [Limitations](docs/KNOWN-LIMITATIONS.md) | Unresolved risks |
| [Quality](QUALITY.md) | Product readiness, currently unimplemented |

Read [AGENTS.md](AGENTS.md) and [CONTRIBUTING.md](CONTRIBUTING.md) before contributing. The first engineering milestone will establish the build, full validation command, pinned dependencies, and corpus. There are no application build/run commands yet.

## Windows and distribution

Windows x86 and x64 builds are requirements to validate, not current compatibility claims. Evaluate Windows 10 alongside supported Windows 11 releases. Native ARM64 is deferred.

Future GitHub Releases will contain exactly three CI-built assets:

- **CodeTrail-Setup.exe:** selects the native x86 or x64 installer.
- **CodeTrail-Setup.msi:** installs the x86 app on x86 or x64 Windows; it does not install native x64 code.
- **CodeTrail-Portable.zip:** both portable builds, LICENSE, notices, and a PORTABLE note.

Release contents and downloaded hashes must be verified. Releases will disclose unsigned status. No release exists. Screenshots will be captured from real Windows runs when a working build exists.

## License

Original project material uses the [MIT License](LICENSE). Third-party components retain their own notices and obligations. No external course text, exercises, or artwork are included.
