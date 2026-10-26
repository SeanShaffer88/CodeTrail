# CodeTrail quality scorecard

Updated 2026-10-26. **Product score: 0/100; not release-ready.** The product is unimplemented. This does not grade the usefulness of its planning documents.

| Dimension | Weight | Score / 5 | Verdict | Evidence and missing work |
|---|---|---|---|---|
| Correctness | 14 | 0 | Fail | No app or end-to-end tests |
| Security/privacy | 12 | 0 | Fail | Threat boundaries proposed; containment/audit untested |
| Robustness | 11 | 0 | Fail | No recovery/failure drills |
| Feature completeness | 9 | 0 | Fail | Targets recorded, unimplemented |
| Performance | 8 | 0 | Fail | Budgets only, no measurements |
| Maintainability | 7 | 0 | Fail | No implementation to assess |
| Modularity | 6 | 0 | Fail | Boundaries proposed, not frozen/enforced |
| UX/accessibility | 6 | 0 | Fail | No running UI or user checks |
| Scalability | 5 | 0 | Fail | No growth tests |
| Idiomatic quality | 5 | 0 | Fail | No product formatting/lint/type gate |
| Test/corpus | 5 | 0 | Fail | No runtime corpus or coverage |
| Self-documentation | 4 | 0 | Fail | No API/operation implementation or tested examples |
| Documentation | 4 | 0 | Fail | Plans exist; product help/usage pending |
| Diagnostics/support | 4 | 0 | Fail | No logs/errors/export implementation |

Total = sum(weight * score / 5). Release requires >=85/100, every dimension >=3/5 and no Fail. Each score needs named tests, corpus fractions, measurements or observed checks. Major waivers require owner approval, reason, impact and follow-up; none granted.

See [validation](docs/VALIDATION.md) and [capability evidence](docs/PARITY.md). Documentation checks cannot satisfy runtime gates.
