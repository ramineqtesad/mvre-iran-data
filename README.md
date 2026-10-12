# MVRE Iran research data

Research data and baseline reconstruction for **Minimum Viable Resilient Economy under Compound Shocks: Design and Evaluation of the MVRE Framework for Iran**.

**Coverage:** Iran, 2005–2021 · 20 indicators · 7 dimensions · 340 nonmissing input values.

This package is prepared for publication as version **0.1.0**. It does not assign a DOI or claim journal acceptance. See [Persian guide](README_FA.md).

## Contents

| File | Meaning |
| --- | --- |
| `data/harmonized_input_A_2005_2021.csv` | Complete baseline inputs before the four log transforms and direction alignment; harmonized, not original downloads |
| `data/harmonized_input_B_2006_2020.csv` | Matched three-year robustness windows; not independent annual observations |
| `data/f01_native_period_mapping.csv` | Native F01 periods and central-year mapping |
| `data/variable_dictionary.csv` | Archived variable names, units, directions, transforms and source-lineage status |
| `data/frozen_transform_anchors.csv` | Frozen aligned minima/maxima and transformation rules |
| `data/dimension_map.csv` | Indicator membership and hierarchical equal weighting |
| `data/normalized_A_2005_2021.csv` | Reconstructed normalized scores |
| `data/dimension_scores_and_mvre.csv` | Seven dimension scores, MVRE, candidate boundary and relative classification |
| `data/benchmark_mvre.csv` | Archived 10-decimal reference series used for validation |
| `code/reproduce_baseline.py` | New, dependency-free baseline reproduction script |
| `docs/provenance.md` | Scope, source snapshots, limitations and data-rights boundary |
| `docs/validation_report.json` | Numerical verification results |
| `docs/index.html` | Persian data landing page for GitHub Pages |

## Reproduce

From the repository root, using Python 3:

```sh
python code/reproduce_baseline.py
```

The script reads the harmonized A matrix, applies the four recorded natural-log transforms and nine adverse sign reversals, uses frozen aligned Min–Max anchors without clipping, averages indicators within dimensions, and averages the seven dimensions equally. It tests midpoints of distinct MVRE scores and minimizes within-group squared deviations subject to at least four observations per group. It writes normalized scores, dimension/index results and a validation report.

All 17 baseline values match the archived 10-decimal benchmark within `1e-9`; the observed maximum discrepancy is approximately `4.6648e-11`. The candidate boundary is approximately `0.5312435648`, with nine lower and eight upper observations. These are numerical validation results, not statistical uncertainty estimates.

## Interpretation

F01 remains a native overlapping three-year measure assigned to its center year. The candidate boundary is relative and fitted within the historical sample; it is not an adequacy floor or structural collapse threshold. Historical anchors may yield values below zero or above one on future data. Equal dimension weights do not imply equal indicator weights, equal causal importance or equal variance contributions.

Original provider-download provenance is incomplete for some variables. The dictionary preserves the dated archived audit status. This release does not reproduce the paper's full Monte Carlo, bootstrap, random-weight and recovery experiments. Their original code is not presented as recovered.

## Citation and rights

Cite the dataset title, creator Ramin Gozarani Eghtesad, version and the actual repository or release URL once published. `CITATION.cff` supplies dataset metadata; no repository address or DOI has been invented. The MIT license in `LICENSE-CODE` covers only the new code. Original third-party data remain governed by their source providers' terms.

## Publish

Suggested repository name: `mvre-iran-data`. Follow `PUBLISH_FA.md` to upload the extracted contents and optionally activate the accompanying GitHub Pages site. Keep the publication URL out of the manuscript until the repository is actually accessible.
