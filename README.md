# DS-A1 · Data Provenance and Measurement Audit — IF-TOPSIS city quality-of-life data

**Course:** Data Science (learn.spaiq.ai) · **Student:** *[name / ID]* · **Tag for grading:** `ds-a1-v1.0`

Audit of the intuitionistic-fuzzy decision data in Roszkowska, Kusterka-Jefmańska & Jefmański (2021), *Entropy* 23(5):563,
doi:10.3390/e23050563 (CC BY 4.0). The data cover 83 European cities × 10 satisfaction criteria from the 2019 EU Perception Survey (Eurostat `urb_percep`).

## Result in one paragraph
Published IF-TOPSIS scores reproduce exactly (83/83 within rounding). Two defects were found: mislabelled rows in the paper's
illustrative matrix, and a classic-TOPSIS comparator that treats "don't know" as 0, contrary to the stated method. The "don't know"
share acts as a measurement confounder (Rostock moves 13 ranks). Under an optimistic sampling model, only 11 of 82 adjacent ranks are
distinguishable. See `SUMMARY.md` and `report/DS-A1_report.pdf`.

## Repository map
```
data/raw/            verbatim transcriptions of the paper's tables (frozen)
data/MANIFEST.sha256 SHA-256 of every raw file (checked by notebook cell 1)
data/processed/      tidy CSVs produced by the notebook
src/ifdata.py        parsers + IF-TOPSIS implementation
notebooks/           DS-A1_provenance_audit.ipynb  (executed, outputs embedded)
results/             checks.json, reproduction tables, bootstrap output, runs/run_log.md
figures/             diagrams (DGP, lineage) and plots
report/              DS-A1_report.pdf
docs/                Graphviz sources of the diagrams
tools/               notebook builder, executor, PDF builder
archive/             rejected first source (kept for transparency)
DATA_CARD.md  DATA_DICTIONARY.md  SOURCE_LICENSE.md  AI_USE_LOG.md  SUMMARY.md  COURSE_ROADMAP.md
```

## Reproduce
```bash
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt jupyter
# either (preferred)
jupyter nbconvert --to notebook --execute --inplace notebooks/DS-A1_provenance_audit.ipynb
# or (what the recorded run used; no Jupyter needed)
python3 tools/run_notebook.py notebooks/DS-A1_provenance_audit.ipynb
python3 tools/build_report.py        # rebuilds report/DS-A1_report.pdf from results/
python3 tools/build_excel.py         # rebuilds report/DS-A1_dataset_and_calculations.xlsx (then recalc in Excel/LibreOffice)
node tools/build_word.js             # rebuilds report/DS-A1_report.docx (needs /tmp/docdata.json export, see script header)
```
No network access is needed. The seed is fixed (`20260923`). Graphviz `dot` is optional (it only renders the diagram PNGs).
The notebook stops at cell 1 if any raw file has changed.

## Publish
```bash
git init && git add . && git commit -m "DS-A1 provenance and measurement audit"
git tag ds-a1-v1.0 && git remote add origin <your GitHub URL> && git push -u origin main --tags
```
Submit on learn.spaiq.ai: the text of `SUMMARY.md` plus `https://github.com/<user>/<repo>/tree/ds-a1-v1.0`.
