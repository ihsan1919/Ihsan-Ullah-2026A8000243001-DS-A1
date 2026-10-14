# Data Card — IF quality-of-life assessments of 83 European cities (2019)

**Motivation.** Published by Roszkowska et al. (2021) to show how survey shares (satisfied / unsatisfied / don't know) can be
represented as intuitionistic fuzzy values and ranked with IF-TOPSIS without inventing numeric scores for ordinal answers.
**This repository** uses it as a course dataset for a fuzzy multi-criteria decision-making case study (DS-A1 to DS-A6).

**Composition.** 83 greater cities (EU, EFTA, UK, Western Balkans, Türkiye) × 10 service-satisfaction items, each cell a triple
(μ, ν, π) rounded to 3 dp. Plus published IFT scores, ranks, classes and classic-TOPSIS comparators. No personal data:
all values are city-level aggregates of ≈700 interviews per city.

**Collection (upstream).** 2019 *Perception Survey on the Quality of Life in European Cities*, European Commission DG REGIO,
fieldwork by Ipsos, 12 Jun–27 Sep 2019 (with a summer pause), 58,100 interviews (as reported in the paper). Weighting and design
details are **not** in the paper; see the DG REGIO methodology report before using for inference.

**Pre-processing by the paper.** Categories 3+4 → μ, 1+2 → ν, 99 → π; equal weights; IFP = (1,0,0), IFN = (0,1,0); normalized
Euclidean distance with three parameters.

**Pre-processing here.** Verbatim transcription → pipe-delimited text (hashed) → tidy CSV. Only change: a diacritic-insensitive join
key (`Białystok` vs `Bialystok` spelling differs between tables).

**Known issues found by this audit.**
1. Section-5 matrix fragment labels rows London/Stockholm/Wien but shows Aalborg/Amsterdam/Zurich values.
2. Published classic-TOPSIS scores are reproduced only if “don't know” is scored 0, contradicting the stated method.
3. Ties at 3 dp and sub-rounding gaps (Antalya/Cluj-Napoca) make some published rank orders non-identifiable from the published data.
4. π is not pure “uncertainty”: it rises for items that respondents do not use (schools C7, sports C3), so IFT partly reflects population composition.
5. Mean ± sd classification depends on which cities are in the set.

**Intended uses.** Teaching and methodological research on fuzzy / IF / Pythagorean-fuzzy MCDM, uncertainty in composite indicators,
measurement audits. **Out-of-scope uses.** Ranking cities for investment or relocation decisions; claims about objective quality of
life; causal claims; comparisons with other survey waves without a comparability check (the 2023 wave changed mode in part of the cities).

**Maintenance.** Frozen at tag `ds-a1-v1.0`. Upstream values should be refreshed from Eurostat `urb_percep` (doi:10.2908/urb_percep).

**License / citation.** CC BY 4.0 — cite Roszkowska et al. (2021), doi:10.3390/e23050563, and Eurostat `urb_percep`.
