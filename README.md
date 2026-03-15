# Hi, I'm Daniel

Data engineer specialising in industrial and environmental systems. I build pipelines for IoT sensor data, emissions tracking, and sustainability reporting. My background is in environmental engineering and life cycle assessment (LCA). I transitioned into data engineering through real production work and have been systematically building towards modern DE architecture ever since.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-daniel--lee--wilkinson-blue?logo=linkedin)](https://www.linkedin.com/in/danielleewilkinson/)

**Current Focus:**
- Expanding streaming architecture skills (Kafka, Airflow). Actively building with Kafka in [**Aerostream**](https://github.com/daniel-lee-wilkinson/aerostream)
- Completing IBM Data Engineering Certificate

**Core Stack:**
Python · SQL · SQLite · DuckDB · pandas · GeoPandas · pytest · GitHub Actions · Streamlit · matplotlib · R

**Expanding into:**
BigQuery · dbt · Snowflake · Kafka · Docker · PostgreSQL

---

## Industrial IoT & CO₂ Capture

> *From automated scientific reporting → production pipeline with data quality monitoring → containerised streaming architecture*

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| **CO₂ Sensor KPI Report Generator** *(private)* | First production pipeline: ingests and persists IoT sensor data via API, calculates engineering KPIs, and generates structured scientific Word reports automatically. Reports use placeholder substitution to inject calculated values into narrative text, insert summary tables, and place matplotlib figures under the correct section headings (e.g. Results). Used by leadership for technical evaluation and operations review. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: aiohttp](https://img.shields.io/badge/Library-aiohttp-green) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Document Output: python-docx](https://img.shields.io/badge/Document_Output-python--docx-lightgrey) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-orange?logo=matplotlib) |
| [**Data Pipeline for IoT Sensor Data**](https://github.com/daniel-lee-wilkinson/extended_co2_sensor_kpi_pipeline) | Extended production pipeline processing 20GB of sensor data from an industrial CO₂ capture facility. Automated ingestion via API, cleaning, cycle splitting, 30+ KPI calculations, and Excel/SQLite reporting. Includes 69-test pytest suite and in-pipeline data quality checks with outlier flagging. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Scheduling: Windows Task Scheduler](https://img.shields.io/badge/Scheduling-Windows%20Task%20Scheduler-lightgrey) ![Output: Excel](https://img.shields.io/badge/Output-Excel-lightblue?logo=microsoft-excel) ![Tests: pytest (69)](https://img.shields.io/badge/Tests-pytest%20(69)-brightgreen) ![Data Quality: in-pipeline checks](https://img.shields.io/badge/Data_Quality-in--pipeline-blueviolet) |
| [**Aerostream: Sensor Stream Simulation Platform**](https://github.com/daniel-lee-wilkinson/aerostream) *(in development)* | Rebuilding the same industrial sensor context as a fully containerised streaming architecture. Simulates real-time sensor streams, processes and stores data via Kafka and PostgreSQL, and displays interactive metrics in a Streamlit dashboard. Sandbox for event-driven architecture and multi-service Docker deployment. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Streaming: Kafka](https://img.shields.io/badge/Streaming-Kafka-black?logo=apachekafka) ![Database: PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue?logo=postgresql) ![API: FastAPI](https://img.shields.io/badge/API-FastAPI-teal?logo=fastapi) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) ![Deployment: Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) |
| [**Energy Mix Optimisation for Carbon Capture Operations**](https://github.com/daniel-lee-wilkinson/energy_mix_optimisation) | Built an hourly optimisation model to size PV/Wind under land constraints and battery dispatch while minimising lifecycle global warming potential (GWP) of power supplied to carbon capture operations. Added demand sensitivity analysis, net CO2 accounting (removal credit), and executive-ready outputs (figures + presentation) for decision support. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.12-blue?logo=python) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Library: NumPy](https://img.shields.io/badge/Library-NumPy-green?logo=numpy) ![Optimization: SciPy](https://img.shields.io/badge/Optimization-SciPy-purple?logo=scipy) ![Data: NASA POWER API](https://img.shields.io/badge/Data-NASA%20POWER%20API-lightgrey) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-orange?logo=matplotlib) ![Metric: GWP Minimisation](https://img.shields.io/badge/Metric-GWP%20Minimisation-brightgreen) |

---

## Emissions & Sustainability Reporting

> *From regulatory compliance pipelines → multi-country emissions analysis*

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Aviation Emissions Compliance Register**](https://github.com/daniel-lee-wilkinson/aviation-emissions-compliance-register) | Simulates daily flight emissions and EU ETS compliance logic using synthetic data. Prototypes a regulatory reporting pipeline with CI, interactive dashboard, and automated document output. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Dash](https://img.shields.io/badge/Interface-Dash-purple?logo=plotly) ![Visualisation: Plotly](https://img.shields.io/badge/Visualisation-Plotly-orange?logo=plotly) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Document Output: python-docx](https://img.shields.io/badge/Document_Output-python--docx-lightgrey) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| [**European GHG & Agriculture Pipeline**](https://github.com/daniel-lee-wilkinson/ghg_emissions_data_vis) | End-to-end data engineering pipeline ingesting and harmonising heterogeneous emissions and agricultural data from five sources (FAOSTAT, World Bank API, UBA, Our World in Data, CITEPA) into a single DuckDB analytical database. Sources report different gas baskets (CO₂-only vs full GHG) and different reference years. The pipeline handles this explicitly and documents where cross-country comparisons are constrained by source heterogeneity. Analytical motivation: investigating why Spain's GHG emissions diverged from Italy, France, and Germany post-1990. Key finding: agricultural production patterns do not explain the divergence; a definitive sectoral explanation would require a harmonised dataset covering CO₂ , CH₄ and N₂O consistently across all four countries. Validates with Pandera schemas, separates staging and mart layers, and generates five publication-quality figures and an automated Word report. Includes an interactive React data flow diagram. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Database: DuckDB](https://img.shields.io/badge/Database-DuckDB-yellow?logo=duckdb) ![Validation: Pandera](https://img.shields.io/badge/Validation-Pandera-blueviolet) ![Architecture: Staging/Mart](https://img.shields.io/badge/Architecture-Staging%2FMart-lightgrey) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib%20%2F%20seaborn-orange?logo=matplotlib) ![Report: docx](https://img.shields.io/badge/Report-Node.js%20docx-lightgrey?logo=nodedotjs) ![Tests: pytest (91)](https://img.shields.io/badge/Tests-pytest%20(91)-brightgreen) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |

---

## Data Quality and Tooling


| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Schema Drift Detector**](https://github.com/daniel-lee-wilkinson/schema-drift-detector) | Lightweight CLI tool for validating CSVs against a YAML contract at ingestion time. Detects dtype mismatches, missing/extra columns, nullable and uniqueness violations, and min/max breaches. Statistical profiling flags median shifts across runs for recurring batch datasets. Produces one JSON report per file with configurable severity levels (`error`, `warning`, `info`). | ![Language: Python](https://img.shields.io/badge/Language-Python%203.13-blue?logo=python) ![Config: YAML](https://img.shields.io/badge/Config-YAML-lightgrey) ![Output: JSON](https://img.shields.io/badge/Output-JSON-lightgrey) ![Data Quality: contract--based](https://img.shields.io/badge/Data_Quality-contract--based-blueviolet) |

---

## Analytics Engineering & Internal Tools

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| **dbt Airbnb Analytics Project** | End-to-end analytics engineering project built on a modern ELT architecture using dbt for transformation, Snowflake as the data warehouse, Dagster for orchestration, and Preset for visualisation. Based on a real-world Airbnb dataset: includes staging and transformation models, modular tests, seeds, snapshots, Jinja macros, and documentation. Developed independently as part of a dbt Bootcamp on Udemy. | ![Language: SQL](https://img.shields.io/badge/Language-SQL-blue?logo=postgresql) ![Transformation: dbt](https://img.shields.io/badge/Transformation-dbt-darkgreen?logo=dbt) ![Warehouse: Snowflake](https://img.shields.io/badge/Warehouse-Snowflake-lightblue?logo=snowflake) ![Orchestration: Dagster](https://img.shields.io/badge/Orchestration-Dagster-purple?logo=dagster) ![Dashboard: Preset](https://img.shields.io/badge/Dashboard-Preset-orange?logo=apache-superset) |
| [**Capital Bikeshare SQL & BigQuery Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_sql) | SQL analysis of Capital Bikeshare trip data, extended from a local SQLite pipeline to cloud-based analytics via BigQuery. Query logic, data processing, and visualisation are decoupled into separate modules; BigQuery exports to CSV for offline plotting and faster iteration. Includes a modular ingestion pipeline, pytest suite covering BigQuery imports and plotting functions, and CI/CD via GitHub Actions. Demonstrates local-to-cloud progression on the same analytical problem. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Query: SQL](https://img.shields.io/badge/Query-SQL-blue) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Cloud: BigQuery](https://img.shields.io/badge/Cloud-BigQuery-blue?logo=googlebigquery) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-orange?logo=matplotlib) ![Tests: pytest](https://img.shields.io/badge/Tests-pytest-brightgreen) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| [**HR Skills Visualiser**](https://github.com/daniel-lee-wilkinson/hr_skills_visualiser) | Internal tool giving teams visibility over their collective skills. Split into two Streamlit apps: an employee-facing app (self-assessment across theoretical, practical, and interest dimensions) and a management app (gap analytics, per-person breakdown, CSV/Excel export). SQLite backend with full skill history for progression tracking. Includes a Faker-generated demo database and a pytest suite with isolated fixtures. Deployed via Docker Compose as two services sharing a named volume, with a custom entrypoint handling DB initialisation on first launch. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.12-blue?logo=python) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Visualisation: Plotly](https://img.shields.io/badge/Visualisation-Plotly-orange?logo=plotly) ![Library: Faker](https://img.shields.io/badge/Library-Faker-orange) ![Tests: pytest](https://img.shields.io/badge/Tests-pytest-brightgreen) ![Deployment: Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) |

---

## Further Projects

> *Selected additional work demonstrating pipeline breadth and analytical range.*

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Capital Bikeshare Multi-Month Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_multimonth_analysis) | End-to-end pipeline ingesting ~900MB of Capital Bikeshare trip data across 85 monthly ZIP archives (2018–2025). Handles schema drift as Capital Bikeshare changed column naming conventions over seven years — detecting format versions and remapping to a unified schema automatically. Surfaces seasonality trends, COVID-era behavioural shifts, and long-term membership growth. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-orange?logo=matplotlib) ![Scraping: BeautifulSoup](https://img.shields.io/badge/Scraping-BeautifulSoup-green) ![Schema Drift: handled](https://img.shields.io/badge/Schema_Drift-handled-blueviolet) ![Data: 900MB 2018--2025](https://img.shields.io/badge/Data-900MB%202018--2025-lightgrey) |
| [**DC Bikeshare GIS Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_station_analysis) | Spatial analysis of 110MB+ real Capital Bikeshare trip data to identify flow imbalances across Washington D.C. Designed a custom 5-category classification matrix (net sink, net source, high-turnover hub, balanced, low traffic) using GeoPandas clustering and ZIP-level destination analysis. Overlaid geocoded employer locations via OSM Nominatim API to support infrastructure planning recommendations. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: GeoPandas](https://img.shields.io/badge/Library-GeoPandas-green) ![Library: contextily](https://img.shields.io/badge/Library-contextily-green) ![Library: shapely](https://img.shields.io/badge/Library-shapely-green) ![Data: Real-world 110MB+](https://img.shields.io/badge/Data-Real--world%20110MB%2B-lightgrey) |

<!--
## Commented out — available on request

### Urban Mobility & Transport (remaining)
- CareerFoundry CitiBike Portfolio
- Public Transport Delay Analysis Pipeline
- Capital Bikeshare Demand Forecast

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
