# AssetLife TSC #1 – October 28, 2026

## Discussed

- **New repository**: v0.3.1 (alpha), Python ≥ 3.12, Apache 2.0. The public API keeps the same structure as ReLife.
- **CI**: checks formatting, linting and types; runs tests on Linux and Windows across 3 Python versions.
- **Tooling**: pre-commit hooks (see CONTRIBUTING.md), automatic PyPI releases, versioned docs.
- **Slide hosting**: LFX, a GitHub repo in the org, or a public drive. Undecided.
- **Marketing**: workshop idea from RTE.
  - Possible audiences: utilities in Australia and New Zealand, RTE asset managers, academics (potential contributors).
  - AI-driven demo debated: accessible for asset managers, but risky for non-experts (hallucinations). Not decided.

## Decisions

1. **Type checking: option D (unanimous).**
   - Blocking only on `develop` → `main` PRs; advisory on `develop`.
   - _Why:_ lowers the entry barrier for contributors; maintainers handle typing at release.
   - _Risk:_ typing debt piling up on `develop`.
2. **DataFrames: option A.**
   - `fit` methods accept DataFrames only (library-agnostic: pandas or polars). NumPy inputs dropped, including in NHPP.
   - _Why:_ a mixed API is ambiguous and doubles maintenance; DataFrames are natural for tabular data; an API break is acceptable while in alpha.

## Action items

- [ ] Configure the CI for option D.
- [ ] Implement the DataFrame API:
  - reference formats for lifetime and recurrent-event data;
  - Pydantic typing;
  - optional column mapping;
- [ ] Keep discussing the workshop privately; possible agenda item for the next TSC.

**Next TSC: November 25, 2026**
