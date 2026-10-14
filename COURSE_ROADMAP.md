# Reusing this case study in DS-A2 … DS-A6 and the final project

The same city-level IF data (this repo) plus its **public upstream sources** give one coherent case study for the whole course.
Items marked *verify* depend on access terms or coverage that must be confirmed before each assignment.

| Assignment | Question on this case | Data | Fuzzy / IF / PF angle |
|---|---|---|---|
| **A2** Inference & uncertainty | Which city-pair IFT differences are real? Minimum meaningful effect, e.g. ΔIFT ≥ 0.02 | Appendix shares + n≈700/city; better: 2019 respondent microdata (*verify download terms on the DG REGIO quality-of-life page*) | Bootstrap / permutation on IF scores; design-effect counterexample (A1 bootstrap is optimistic) |
| **A3** Regression baseline | What predicts satisfaction with **air quality (C8)** among respondents? | 2019/2023 microdata (~58–70k rows): age, sex, education, city fixed effects | Target = satisfied (μ component) at person level; **do not** predict IFT from C1–C10 (leakage, A1 §9) |
| **A4** Model comparison & calibration | Classify respondents “satisfied with city life” vs not; compare logistic, ridge, gradient boosting | Same microdata, grouped folds by city | Calibrated probabilities → city-level μ estimates → IF-TOPSIS; threshold choice from policy capacity |
| **A5** Rolling time series | Forecast city air-quality readings that relate to C8 | EEA air-quality measurements (daily/hourly PM2.5, NO2) for the same cities (*verify station coverage*) | Rolling origins ≥ 5; perception waves (2004–2023) are too few for rolling evaluation alone |
| **A6** Causal claim | Did low-emission zones raise satisfaction with air quality? | Waves 2012/2015/2019/2023 (2012/2015 via GESIS ZA5885/ZA6641, *verify*) + LEZ start dates | Difference-in-differences on μ(C8); negative control: C4 culture; mode change in 2023 is a threat |
| **Final project** | Robust fuzzy ranking of European cities under uncertainty | All of the above | IFS → **Pythagorean fuzzy** (μ²+ν² ≤ 1) and q-rung extensions; entropy weights; compare IF-TOPSIS, PF-TOPSIS, classic; rank intervals |

Related papers on the same data line (useful citations for the final project): Jefmański, Roszkowska & Kusterka-Jefmańska (2021)
*Entropy* 23:1636 (IF synthetic measure); follow-up on IF-entropy weights, *Entropy* 25:961 (2023); a Pythagorean fuzzification of
survey responses (Indian J. Sci. Technol.). Check each paper's licence before reusing its tables.
