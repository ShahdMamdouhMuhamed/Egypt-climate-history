# Egyptian Cities Climate History 

##  Project Overview

Egyptian Cities Climate History is an end-to-end Data Wrangling project that aims to collect, clean, transform, integrate, and analyze historical climate data across several Egyptian cities.

The project focuses on building a reliable daily climate dataset for Cairo, Alexandria, Aswan, Hurghada, and other Egyptian cities to investigate long-term temperature trends, seasonal variations, and extreme heat events.

By combining multiple heterogeneous data sources, we aim to create a consistent dataset that can support climate analysis and provide useful insights for students, researchers, and urban planners.

##  Project Objectives

- Collect historical climate records from multiple public data sources.
- Identify suitable NOAA weather stations for selected Egyptian cities.
- Process and clean raw temperature and rainfall measurements.
- Handle missing values, quality flags, and inconsistent data formats.
- Scrape long-term monthly climate averages from Wikipedia.
- Integrate NOAA and Open-Meteo datasets.
- Compare observed monthly averages with Wikipedia climate averages.
- Analyze yearly temperature trends and extreme heat days.
- Validate and publish a clean, documented climate dataset.

##  Data Sources

This project uses three heterogeneous public data sources:

### 1. NOAA GHCN-Daily

Historical daily climate observations from weather stations around the world.

- Temperature measurements are stored in tenths of degrees.
- Records include maximum temperature, minimum temperature, and precipitation.
- Contains quality flags, missing days, and stations with discontinued reporting.

Source: https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily

### 2. Open-Meteo Historical Weather API

Provides historical weather data for selected Egyptian cities using their geographical coordinates.

- Daily historical weather measurements.
- Data returned as parallel lists of dates and values.
- Used to complement and compare NOAA observations.

Source: https://open-meteo.com/en/docs/historical-weather-api

### 3. Wikipedia Climate Data

Climate tables for Egyptian cities containing long-term monthly averages.

- Monthly temperature averages.
- Values presented in both Celsius and Fahrenheit.
- Footnotes and inconsistent text formatting that require processing.

Source: https://en.wikipedia.org/wiki/Climate_of_Egypt

##  Project Workflow

The project follows an end-to-end Data Wrangling pipeline:

1. **Discovery:** Identify Egyptian weather stations and document their geographical locations and available historical coverage.

2. **Ingestion:** Download NOAA station files, preserve raw snapshots, calculate file hashes, and retrieve historical weather data from Open-Meteo.

3. **Cleaning:** Convert NOAA temperatures from tenths of degrees, handle quality flags, identify missing observations, and save rejected records.

4. **Scraping:** Extract monthly climate averages from Wikipedia and separate Celsius and Fahrenheit values.

5. **Transformation:** Reshape climate measurements into consistent columns and calculate monthly averages, yearly averages, and annual days above 40°C.

6. **Integration:** Combine NOAA and Open-Meteo observations using a source identifier and compare the results with Wikipedia climate averages.

7. **Validation:** Check temperature consistency, missing data coverage, and minimum/maximum temperature relationships.

8. **Publishing:** Produce the final daily climate datasets, reports, and visualizations.

##  Expected Visualizations

The project will include:

- Yearly average maximum temperature per city.
- Annual number of days above 40°C for Aswan and Cairo.
- Monthly climate averages compared with Wikipedia averages.
- Missing values per column before and after cleaning.
- Distribution of the main numerical variable before and after cleaning.
- Matched versus unmatched records during data integration.

##  Repository Structure

```text
egyptian-cities-climate-history/
│
├── data/
│   ├── raw/
│   ├── interim/
│   ├── rejected/
│   └── final/
│
├── reports/
│   ├── figures/
│   ├── source_evaluation.md
│   ├── data_quality_report.md
│   ├── cleaning_changelog.csv
│   ├── integration_report.md
│   ├── validation_report.md
│   └── visualization_notes.md
│
├── src/
│   ├── discovery.py
│   ├── ingestion.py
│   ├── cleaning.py
│   ├── scraping.py
│   ├── transformation.py
│   ├── integration.py
│   ├── validation.py
│   └── pipeline.py
│
├── notebooks/
├── logs/
│   └── pipeline.log
│
├── config.yaml
├── requirements.txt
├── schedule.md
└── README.md
```

##  Technologies Used

- Python 3
- Pandas
- Requests
- BeautifulSoup
- Matplotlib
- OpenPyXL
- lxml
- Git & GitHub

##  Team Members & Responsibilities

Our team consists of six members, with each member responsible for a specific part of the project.

| Role | Responsibility |
|---|---|
| Member 1 | File handling, source evaluation, and data profiling |
| Member 2 | API integration and data merging |
| Member 3 | Web scraping and text processing |
| Member 4 | Data cleaning and quality management |
| Member 5 | Date handling, transformation, and visualizations |
| Member 6 | Validation, publishing, documentation, and pipeline execution |

*Team member names and GitHub profiles will be added later.*

##  Installation & Usage

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/egyptian-cities-climate-history.git
```

### 2. Navigate to the project directory

```bash
cd egyptian-cities-climate-history
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment

Windows:

```bash
venv\Scripts\activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

### 6. Run the pipeline

```bash
python -m src.pipeline
```

*The pipeline command will be available after implementation.*

##  Known Limitations

- Historical station coverage may differ between cities.
- Some NOAA stations may contain missing years or discontinued observations.
- NOAA and Open-Meteo measurements may differ because of their underlying data sources and methodologies.
- Wikipedia climate averages may use different reference periods.
- Missing observations will be documented rather than automatically treated as zero.

##  Expected Deliverables

- Selected NOAA weather stations list with historical coverage.
- Daily climate dataset for each selected city.
- Rejected records and cleaning changelog.
- Source evaluation and data quality reports.
- Integration and validation reports.
- Climate visualizations.
- Comparison between observed climate data and Wikipedia averages.

---

**Academic Project:** Data Wrangling  
**Project:** Egyptian Cities Climate History  
**Team Size:** 6 Students  
**Repository:** egyptian-cities-climate-history

