# Hi, I'm Daniel

Data engineer specialising in industrial and environmental systems. I build production-grade pipelines for IoT sensor data, emissions tracking, and sustainability reporting. My background is in environmental engineering and life cycle assessment (LCA); I transitioned into data engineering through real production work on industrial CO₂ capture systems.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-daniel--lee--wilkinson-blue?logo=linkedin)](https://www.linkedin.com/in/danielleewilkinson/)

**Stack:** Python · SQL · DuckDB · Polars · pandas · GeoPandas · Dagster · pytest · GitHub Actions · Docker · Kafka · BigQuery · dbt · Streamlit · R

---

## Industrial Sensor Data Pipeline (Dagster)

A production-grade pipeline for an industrial CO₂ capture unit — the third generation of a system I built, broke, and rebuilt better.

The pipeline fetches time-series sensor data from a REST API, detects process cycles across six sequential phases, calculates 30+ engineering KPIs per cycle per adsorption module, and exports results to DuckDB. Built to replace a fragile legacy of ad hoc scripts.

**What it does:** pre-flight checks (env vars, API auth, UUID reachability) → parallelised fetch via `ThreadPoolExecutor` → atomic Parquet writes (temp + rename) → schema validation at ingest with graceful drift handling → cycle detection → KPI calculation → asset-level data quality checks → performance monitoring (timing + memory via psutil) per stage. All failures raise explicitly and are collected before reporting. Runs on a weekly cron schedule as a persistent Windows service (WinSW).

**pytest suite** covering config invariants, fetch logic, schema validation, cycle detection, KPI arithmetic, and run metrics. CI via GitHub Actions. Synthetic data generation for all tests - no dependency on real API access.

[**LINK: co2-pipeline-dagster**](https://github.com/daniel-lee-wilkinson/co2-pipeline-dagster) · ![Dagster](https://img.shields.io/badge/Orchestration-Dagster-purple?logo=dagster) ![Polars](https://img.shields.io/badge/Library-Polars-blue?logo=polars) ![DuckDB](https://img.shields.io/badge/Database-DuckDB-yellow?logo=duckdb) ![Parquet](https://img.shields.io/badge/Storage-Parquet-lightgrey?logo=apacheparquet) ![pytest](https://img.shields.io/badge/Tests-pytest%20(242)-brightgreen) ![CI](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions)

---

## Capital Bikeshare — Independent Research

Four connected projects using real Washington D.C. bikeshare data as a vehicle for engineering and analytical depth. Each builds on or complements the others.

| Project | What it is |
|---------|------------|
| [**Multi-Month Pipeline**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_multimonth_analysis) | End-to-end pipeline ingesting ~900MB across 85 monthly ZIP archives (2018–2025). Detects schema format versions and remaps to a unified schema automatically — Capital Bikeshare changed column conventions over seven years. Surfaces seasonality trends, COVID-era behavioural shifts, and long-term membership growth. |
| [**GIS & Spatial Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_station_analysis) | Spatial analysis of 110MB+ trip data to identify flow imbalances across D.C. Custom 5-category classification matrix (net sink, net source, high-turnover hub, balanced, low traffic) using GeoPandas clustering and ZIP-level destination analysis. Employer locations geocoded via OSM Nominatim API. |
| [**Demand Forecast**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_demand_forecast) | ARIMA/ARIMAX time series models with weather covariates forecasting station-level demand. |
| [**SQL & BigQuery Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_sql) | Modular pipeline extended from SQLite to BigQuery. Query logic, processing, and visualisation decoupled into separate modules. pytest suite covering BigQuery imports and plotting functions. CI via GitHub Actions. |

---

## Emissions & Sustainability Reporting

> *From regulatory compliance pipelines → multi-country emissions analysis → real-time streaming*

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Aviation Emissions Compliance Register**](https://github.com/daniel-lee-wilkinson/aviation-emissions-compliance-register) | Simulates daily flight emissions and EU ETS compliance logic using synthetic data. Prototypes a regulatory reporting pipeline with CI, interactive dashboard, and automated document output. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Dash](https://img.shields.io/badge/Interface-Dash-purple?logo=plotly) ![Visualisation: Plotly](https://img.shields.io/badge/Visualisation-Plotly-orange?logo=plotly) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Document Output: python-docx](https://img.shields.io/badge/Document_Output-python--docx-lightgrey) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| [**European GHG & Agriculture Pipeline**](https://github.com/daniel-lee-wilkinson/ghg_emissions_data_vis) | End-to-end pipeline ingesting and harmonising heterogeneous emissions and agricultural data from five sources (FAOSTAT, World Bank API, UBA, Our World in Data, CITEPA) into a single DuckDB analytical database. Sources report different gas baskets and reference years — handled explicitly with documented constraints on cross-country comparisons. Staging/mart architecture, Pandera validation, five publication-quality figures, automated Word report. 91-test pytest suite. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Database: DuckDB](https://img.shields.io/badge/Database-DuckDB-yellow?logo=duckdb) ![Validation: Pandera](https://img.shields.io/badge/Validation-Pandera-blueviolet) ![Architecture: Staging/Mart](https://img.shields.io/badge/Architecture-Staging%2FMart-lightgrey) ![Tests: pytest (91)](https://img.shields.io/badge/Tests-pytest%20(91)-brightgreen) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| [**Aerostream**](https://github.com/daniel-lee-wilkinson/aerostream) *(in development)* | Streaming pipeline simulating real-time aviation emissions data across airline and aircraft type combinations, each with distinct emissions/km profiles. A Streamlit dashboard displays live compliance status against mock EU ETS allowance limits. Sandbox for event-driven architecture and multi-service Docker deployment. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Streaming: Kafka](https://img.shields.io/badge/Streaming-Kafka-black?logo=apachekafka) ![Database: PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue?logo=postgresql) ![API: FastAPI](https://img.shields.io/badge/API-FastAPI-teal?logo=fastapi) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) ![Deployment: Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) |

---

## Data Quality & Tooling

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Schema Drift Detector**](https://github.com/daniel-lee-wilkinson/schema_drift_detector) | Lightweight CLI tool for validating CSVs against a YAML contract at ingestion time. Detects dtype mismatches, missing/extra columns, nullable and uniqueness violations, and min/max breaches. Statistical profiling flags median shifts across runs for recurring batch datasets. Produces one JSON report per file with configurable severity levels (`error`, `warning`, `info`). | ![Language: Python](https://img.shields.io/badge/Language-Python%203.13-blue?logo=python) ![Config: YAML](https://img.shields.io/badge/Config-YAML-lightgrey) ![Output: JSON](https://img.shields.io/badge/Output-JSON-lightgrey) ![Data Quality: contract--based](https://img.shields.io/badge/Data_Quality-contract--based-blueviolet) |

---

## Analytics Engineering & Internal Tools

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| **dbt Airbnb Analytics Project** | End-to-end analytics engineering project: dbt for transformation, Snowflake as the data warehouse, Dagster for orchestration, Preset for visualisation. Staging and transformation models, modular tests, seeds, snapshots, Jinja macros, and documentation. | ![Language: SQL](https://img.shields.io/badge/Language-SQL-blue?logo=postgresql) ![Transformation: dbt](https://img.shields.io/badge/Transformation-dbt-darkgreen?logo=dbt) ![Warehouse: Snowflake](https://img.shields.io/badge/Warehouse-Snowflake-lightblue?logo=snowflake) ![Orchestration: Dagster](https://img.shields.io/badge/Orchestration-Dagster-purple?logo=dagster) ![Dashboard: Preset](https://img.shields.io/badge/Dashboard-Preset-orange?logo=apache-superset) |
| [**HR Skills Visualiser**](https://github.com/daniel-lee-wilkinson/hr_skills_visualiser) | Internal tool giving teams visibility over their collective skills. Two Streamlit apps: employee self-assessment and management gap analytics. SQLite backend with full skill history. Faker-generated demo database, isolated pytest fixtures, Docker Compose deployment with shared named volume and custom entrypoint. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.12-blue?logo=python) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Tests: pytest](https://img.shields.io/badge/Tests-pytest-brightgreen) ![Deployment: Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) |

---

## Further Projects

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Energy Mix Optimisation for Carbon Capture Operations**](https://github.com/daniel-lee-wilkinson/energy_mix_optimisation) *(in progress)* | Hourly optimisation model sizing PV/Wind under land constraints and battery dispatch while minimising lifecycle GWP of power supplied to carbon capture operations. Demand sensitivity analysis, net CO₂ accounting, NASA POWER API. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.12-blue?logo=python) ![Optimization: SciPy](https://img.shields.io/badge/Optimization-SciPy-purple?logo=scipy) ![Data: NASA POWER API](https://img.shields.io/badge/Data-NASA%20POWER%20API-lightgrey) ![Metric: GWP Minimisation](https://img.shields.io/badge/Metric-GWP%20Minimisation-brightgreen) |

---

## DataTalksClub Data Engineering Zoomcamp

> *Nine-week structured course building end-to-end data pipelines with industry-standard tools*

| Module | Key Tasks | Skills Used |
|--------|-----------|-------------|
| [**Module 1: Containerisation & Infrastructure as Code**](https://github.com/daniel-lee-wilkinson/data-engineering-zoomcamp/blob/main/homework/hw1.md) | Containerised PostgreSQL + pgAdmin with Docker Compose. Ingested NYC green taxi trip data in pandas and PostgreSQL. Provisioned GCS and BigQuery with Terraform. | ![Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) ![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue?logo=postgresql) ![Terraform](https://img.shields.io/badge/IaC-Terraform-purple?logo=terraform) ![BigQuery](https://img.shields.io/badge/Cloud-BigQuery-blue?logo=googlebigquery) |

<!--
## Commented out — available on request

### Urban Mobility & Transport (remaining)
- CareerFoundry CitiBike Portfolio
- Public Transport Delay Analysis Pipeline

### Emissions & Sustainability (remaining)
- Umberto R Package

### Analytics Engineering & Internal Tools (remaining)
- Python Patent Tool

### Coursework & Foundations
- Python Mini ETL Project (Coursera)
- SQL Purchase Funnel Analysis

### Personal Projects & Fitness
- Calorie Target Tracker
- CLI Task Manager
-->
