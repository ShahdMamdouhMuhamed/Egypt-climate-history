# Egyptian Cities Climate History (Project 3)

## 1. Question
A clean daily climate record (max, min, rain) for Cairo, Alexandria, Aswan and Hurghada, to compare long-term warming and extreme-heat days (>40 °C).

## 2. Sources
| Source | Type | Main defects |
|---|---|---|
| NOAA GHCN-Daily station files | file | tenths of °C, one row per element, quality flags, gaps, stations that stop |
| Open-Meteo historical API | API | parallel lists of times/values |
| Wikipedia climate tables | scraped | °C and °F in one cell, footnotes |

See `reports/source_evaluation.md`.

## 3. How to run
```bash
python -m venv .venv && source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# edit config.yaml: contact_email, personal_twist, date_window
python -m src.pipeline --discover      # builds reports/station_match_review.csv -> pick station_id per city in config.yaml
python -m src.pipeline --download      # first-time download (raw + MANIFEST hashes)
python -m src.pipeline                 # one command, offline, from saved raw data
pytest
```

## 4. Row counts
_TODO: raw / rejected / final per source and how they reconcile._

## 5. Key cleaning decisions
_TODO: 5-8 decisions (divide by 10, QFLAG rejection, never fill gaps, fuzzy threshold, ...)._

## 6. Figures
_TODO: 6 figures with one finding each (see reports/visualization_notes.md)._

## 7. Limitations
_TODO_

## 8. Team roles
| # | Role | Files owned |
|---|---|---|
| 1 | Files & profiling | `s1_discovery.py`, `s2_ingest.py` (GHCN), `data_quality_report.md`, MANIFEST |
| 2 | API & integration | `s2_ingest.py` (Open-Meteo), `s6_integrate.py`, `integration_report.md` |
| 3 | Scraping & text | `s3_scrape.py`, station fuzzy match |
| 4 | Cleaning | `s4_clean.py`, `cleaning_changelog.csv`, `data/rejected/` |
| 5 | Dates, transform, figures | `s5_transform.py`, `s8_figures.py` |
| 6 | Validation & publishing | `s7_validate.py`, `pipeline.py`, config, README, data dictionary |
