# Data dictionary

## `data/processed/ifv_long.csv` — one row per city × criterion (830 rows)
| Column | Type | Range | Meaning |
|---|---|---|---|
| `City` | string | 83 values | Greater city as named in the paper (UTF-8; diacritics kept) |
| `criterion` | string | C1…C10 | Survey item, see table below |
| `mu` | float (3 dp) | [0, 1] | Membership = share of respondents *rather* or *very satisfied* |
| `nu` | float (3 dp) | [0, 1] | Non-membership = share *rather* or *very unsatisfied* |
| `pi` | float (3 dp) | [0, 1] | Hesitation = share *don't know / no answer / refused* |
| `criterion_label` | string | – | Plain-language item label |

Constraint: `mu + nu + pi = 1 ± 0.0015` (rounding). Source table: A2 (mu), A1 (nu), A3 (pi).

| Code | Item: “How satisfied are you with … in your city?” | Direction |
|---|---|---|
| C1 | public transport | benefit |
| C2 | health care services, doctors and hospitals | benefit |
| C3 | sports facilities (sports fields, indoor halls) | benefit |
| C4 | cultural facilities (concert halls, theatres, museums, libraries) | benefit |
| C5 | green spaces (parks, gardens) | benefit |
| C6 | public spaces (markets, squares, pedestrian areas) | benefit |
| C7 | schools and other educational facilities | benefit |
| C8 | quality of the air | benefit |
| C9 | noise level | benefit |
| C10 | cleanliness | benefit |

## `data/processed/published_results.csv` — one row per city (83 rows)
| Column | Source | Meaning |
|---|---|---|
| `IFT_pub` | Table A4 | Published IF-TOPSIS coefficient (3 dp) |
| `CL_pub` | Table A5 | Published classic-TOPSIS coefficient (3 dp) |
| `rank_IFT_pub` | Table 11 | Published rank by IFT (1 = best) |
| `rank_CL_pub` | Table 14 | Published rank by classic TOPSIS |
| `class_IFT_pub` | Table 12 | very high ≥0.8 · high [0.6,0.8) · medium [0.4,0.6) · low [0.2,0.4) · very low <0.2 |
| `class_CL_pub` | Table A6 | Same bands applied to `CL_pub` |

## Raw files (`data/raw/`)
| File | Content |
|---|---|
| `A1_nonmembership_nu.txt`, `A2_membership_mu.txt`, `A3_hesitation_pi.txt` | 83 × 10 IFV components |
| `A4_ift_coefficients.txt`, `A5_classic_topsis.txt` | Published coefficients (4 city/value pairs per printed row) |
| `T11_rank_ift.txt`, `T14_rank_classic.txt`, `T12_class_ift.txt`, `A6_class_classic.txt` | Published ranks / classes |
| `T05_likert_3cities.txt` | 4-point Likert + DK shares (%) for London, Stockholm, Wien |
| `T06_T07_T10_three_cities.txt` | Aggregated classes (%), distances, Section-5 matrix fragment, Table 13 statistics, prose claims |

## Results (`results/`)
| File | Meaning |
|---|---|
| `checks.json` | Every audit check: PASS / FLAG / FAIL + detail |
| `ift_reproduction.csv` | Recomputed d+, d−, IFT vs published values and ranks |
| `classic_topsis_variants.csv` | Four candidate classic-TOPSIS definitions vs published scores (3 cities) |
| `rank_intervals_bootstrap.csv` | Optimistic 90% rank intervals (B = 2000, seed 20260923) |
| `dk_counterexample_ranks.csv` | Ranks with and without the DK penalty |
