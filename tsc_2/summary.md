# AssetLife TSC #2 – November 25, 2026

## Discussed

- **SBOM & SPDX**: the license scan found no conflict between AssetLife and its
  dependencies. To meet open-source standards:
  - add SPDX headers to every source file (adapted to each file's comment
    syntax; the REUSE tool can automate this), checked in pre-commit and CI;
  - publish the SBOM in the docs (PR opened by Alban).
- **DataFrames in policies & stochastic processes**: pass one assets DataFrame
  (`a0`, `ar`, costs, covariates) instead of several 1D arrays.
  - Strategy inferred from the columns: `ar` present → age replacement,
    otherwise run-to-failure.
  - Alexis (in writing): unclear for users, test with a few users before
    implementing.
  - Nathan: in favor for policies; unsure for stochastic processes
    (mathematical objects, not an asset fleet).
  - Other points: explicit `one_cycle` argument; required cost columns
    validated per model type; mixed fleets (`ar = inf` for run-to-failure
    assets).
  - Output format (DataFrame vs NumPy) not settled.

## Decisions

1. **New `fit` design: approved.**
   - Any DataFrame (pandas, polars) via Narwhals; default columns `time`,
     `event` (or `time_inf`, `time_sup`), optional `entry`;
     `covar_column_names` for regressions; NHPP unchanged.
   - _Open:_ name of the column-mapping argument (`field_column_names` is not
     explicit enough).
2. **DataFrames in policies: on hold.**
   - _Why:_ William and Nathan in favor, but Alexis wants user testing first.
     Stochastic processes undecided.

## Action items

- [ ] Add SPDX headers and check them in pre-commit and CI.
- [ ] Merge the SBOM documentation PR.
- [ ] Rename the column-mapping argument, then release the new `fit` design.
- [ ] Write policy and stochastic-process examples and test them with a few users.

**Next TSC: January 2027** (no meeting in December)
