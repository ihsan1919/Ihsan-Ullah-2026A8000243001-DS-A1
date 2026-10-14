# Source, license, version and hash

## Primary source used (secondary data)
| Field | Value |
|---|---|
| Article | Roszkowska, E.; Kusterka-Jefmańska, M.; Jefmański, B. (2021). *Intuitionistic Fuzzy TOPSIS as a Method for Assessing Socioeconomic Phenomena on the Basis of Survey Data.* **Entropy 23(5):563** |
| DOI | https://doi.org/10.3390/e23050563 |
| Published | 1 May 2021 (received 25 Mar 2021, revised 22 Apr 2021, accepted 28 Apr 2021) |
| License | **CC BY 4.0** (statement printed in the article). MDPI page metadata (`dc.rights`) shows `creativecommons.org/licenses/by/3.0/`; the article's own notice says 4.0. Both permit reuse with attribution. |
| Parts used | Appendix A Tables A1–A6; main-text Tables 5, 6, 10, 11, 12, 13, 14; Section-5 decision-matrix fragment; numeric claims in Section 5 prose |
| Access | Article HTML, accessed 2026-09-30 (the MDPI PDF could not be downloaded from the build environment) |

## Upstream (original) data — not yet retrieved
| Field | Value |
|---|---|
| Survey | 2019 *Perception Survey on the Quality of Life in European Cities* (European Commission DG REGIO; fieldwork by Ipsos) |
| Eurostat table | `urb_percep`, DOI https://doi.org/10.2908/urb_percep (coverage 2004–2023; last data update 08/04/2024 per Eurostat page) |
| Reuse terms | Eurostat data: free reuse with acknowledgement (Eurostat copyright notice) |
| Status | **Pending.** Cross-check of appendix values against `urb_percep` is listed as an open verification item in `AI_USE_LOG.md`. |

## Frozen version
* Raw layer: `data/raw/*.txt` (verbatim transcription, pipe-delimited).
* Hashes: `data/MANIFEST.sha256` (SHA-256). Notebook cell 1 aborts if any hash differs.
* Code/data version for grading: the git **tag `ds-a1-v1.0`** (see README).
* Article PDF hash: *to be added by the student after downloading the PDF* (`sha256sum Entropy-23-00563.pdf`).
