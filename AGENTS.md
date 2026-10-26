# CodeTrail project rules

This is a planning repository. Do not present proposed behavior as implemented or start a build solely because a roadmap item exists.

- Confirmed scope: enjoyable Windows programming education for complete/returning beginners, Python first. Preserve the CodeTrail name.
- Keep the product free, offline for core learning, accessible, and useful in the first minute. No paid tiers, advertising, data sales, account requirement or AI dependency in the proposed first release.
- Build each named operation before its surfaces. Every GUI capability needs CLI coverage; every interactive Windows control needs a tooltip and accessible guidance.
- Candidate modules and stack are in docs/ARCHITECTURE.md and are not frozen. Prove x86/x64 execution, recovery, editor accessibility, and packaging before foundation freeze.
- Domain logic cannot import UI or storage implementations. Freeze contracts before large/parallel implementation. If workers are later authorized, scope their ownership; they never commit, push, merge, or release.
- Autosave and recover work. Important overwrites, resets, imports and migrations need preview, undo/backup and interruption recovery. Never run learner code with ordinary app privileges.
- Use original curriculum/assets; verify provenance, licenses, current upstream support, both architectures, and advisories before adoption. Pin versions and retain notices.
- Maintain docs/DECISIONS.md, docs/KNOWN-LIMITATIONS.md, docs/DEPENDENCIES.md, docs/PARITY.md and QUALITY.md. Follow budgets and evidence requirements in docs/VALIDATION.md.
- Coverage floors: 85% core/domain, 70% overall, and every safety/destructive path exercised. Inspect the complete formatter, strict linter/types and all-target tests on the integrated result before merge/release.
- Perform an adversarial review. Major waivers require the owner; never silently lower a gate or invent evidence. Release needs >=85/100, every dimension >=3/5, and no Fail.
- Public docs use plain language, actual behavior, and real screenshots. Keep private operating manuals, internal comparisons, credentials, personal data and machine paths out of the repository.
- Release exactly CodeTrail-Setup.exe, CodeTrail-Setup.msi and CodeTrail-Portable.zip as defined in docs/VALIDATION.md. No winget. Verify downloaded assets and preserve user data.

Build and full product gate: not established; create during foundation work. Corpus: not implemented. Public command/data/config surfaces: Experimental until explicitly stabilized.
