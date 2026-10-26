# Known limitations

As of 2026-10-26:

- No application, lessons, implementation corpus, installer, or release workflow exists.
- Windows compatibility and both host architectures are unverified. The MSI must also run the x86 app on x64 Windows.
- Wasmtime native compilation has no 32-bit host support. Pulley or another interpreter needs a Windows x86 feasibility/performance check.
- Python WASI is a limited platform environment. Arbitrary pip/native extensions, networking, subprocesses and host automation are outside first-release scope.
- Replay remains a proposal. Correct tracing, safe value inspection, exceptions, limits and accessibility need proof.
- Stack, versions, terms, Windows matrix, schemas and full-gate command are not frozen.
- Offline WebView deployment, servicing, footprint and standard-user behavior remain unresolved.
- No learner trial, accessibility pass, runtime test, benchmark, security audit or failure drill has run.
- Curriculum counts and schedule are provisional; authoring/testing may dominate effort.
- Extra languages, collaboration, classrooms, sync, executable community packs and AI are deferred.
- The project name carries no claim of trademark exclusivity.

Planning and repository creation do not establish product readiness.
