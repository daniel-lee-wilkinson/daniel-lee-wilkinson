## Hi there 👋

Welcome to my project portfolio.

I'm a Data Engineer and Sustainability Analyst specialising in automation, emissions tracking, and decision-support tools.

My projects include end-to-end data pipelines, KPI report generators, internal dashboards, and custom apps - built using Python, SQL, Streamlit, Dash, and SQLite.

This page showcases a mix of public and internal work. Where source code isn't available, summaries explain structure, logic, and impact.

Each project entry includes a short description and badges for the main technologies used. If you're interested in a project or want to collaborate, feel free to reach out.

---

### Data Engineering & Pipelines
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Capital Bikeshare SQL Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_sql) | Analysed April 2025 bikeshare data to identify station usage, rider behaviour, and temporal trends. Includes a modular data ingestion pipeline, test suite, and automated visual reporting using SQL and Python. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-lightgrey?logo=sqlite) ![Query Language: SQL](https://img.shields.io/badge/Query_Language-SQL-blue) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-orange?logo=matplotlib) ![Tests: pytest](https://img.shields.io/badge/Tests-pytest-green) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| [**Aviation Emissions Compliance Register**](https://github.com/daniel-lee-wilkinson/aviation-emissions-compliance-register) | Simulates daily CO₂ emissions from flights using synthetic data and evaluates EU ETS compliance. Outputs automated CSV/Word reports and a public dashboard. Features modular code, SQLite storage, and CI with formatting, syntax checks, and dependency validation. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Dashboard: Dash](https://img.shields.io/badge/Dashboard-Dash-purple) ![Visualisation: Plotly](https://img.shields.io/badge/Visualisation-Plotly-darkblue?logo=plotly) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-lightgrey?logo=sqlite) ![Document Output: python-docx](https://img.shields.io/badge/Document_Output-python--docx-lightgrey) ![CI: GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-brightgreen?logo=github-actions) |
| **CO₂ Sensor KPI Pipeline***(private)* | Built and scheduled a pipeline that collects sensor data via API, cleans and stores it, calculates KPIs, and produces Excel and Word reports daily | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: aiohttp](https://img.shields.io/badge/Library-aiohttp-grey) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Database: SQLite](https://img.shields.io/badge/Database-SQLite-grey?logo=sqlite) ![Document Output: openpyxl](https://img.shields.io/badge/Document_Output-openpyxl-grey) ![Document Output: python-docx](https://img.shields.io/badge/Document_Output-python--docx-grey) |
| [**Extended KPI Calculator**](https://github.com/daniel-lee-wilkinson/aerostream) *(in progress, private)* | Enhances the existing KPI pipeline with 20+ domain-specific engineering metrics calculated from sensor data and known equations. Fully automated and scheduled daily via Windows Task Scheduler. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Automation: Task Scheduler](https://img.shields.io/badge/Automation-Windows%20Task%20Scheduler-lightgrey) |


### Streaming and Event-Driven Systems

| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Aerostream: Sensor Stream Simulation Platform**](https://github.com/daniel-lee-wilkinson/aerostream) *(in development, private)* | Simulates real-time sensor streams in an industrial context, processes and stores data via Kafka and PostgreSQL, and displays interactive metrics in a Streamlit dashboard. Designed as a sandbox for event-driven architecture and containerised multi-service deployment. | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Streaming: Kafka](https://img.shields.io/badge/Streaming-Kafka-black?logo=apachekafka) ![Database: PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue?logo=postgresql) ![API: FastAPI](https://img.shields.io/badge/API-FastAPI-teal?logo=fastapi) ![Visualisation: Streamlit](https://img.shields.io/badge/Visualisation-Streamlit-red?logo=streamlit) ![Container: Docker](https://img.shields.io/badge/Deployment-Docker-lightblue?logo=docker) |



### Sustainability, LCA & Environmental Tools
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Streamlit Ecodesign Dashboard**](https://github.com/daniel-lee-wilkinson/aerostream) | Developed an interactive tool to estimate climate impact of design choices in mechanical systems | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) |
| [**Umberto R Package**](https://github.com/daniel-lee-wilkinson/openlca-2-r) *(private)* | Automated extraction, cleaning, and visualisation of life cycle assessment (LCA) data from Umberto 11 | ![Language: R](https://img.shields.io/badge/Language-R-blue?logo=r) ![Library: data.table](https://img.shields.io/badge/Library-data.table-green) ![Visualisation: ggplot2](https://img.shields.io/badge/Visualisation-ggplot2-blue) |

### Spatial & Mobility Analysis
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**DC Bikeshare GIS Analysis**](https://github.com/daniel-lee-wilkinson/capitalbikeshare_station_analysis) | Mapped usage patterns and spatial imbalances with clustering and geospatial overlays | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: GeoPandas](https://img.shields.io/badge/Library-GeoPandas-green) |

### Internal Tools & Automation
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Python Patent Tool**](https://github.com/daniel-lee-wilkinson/aerostream) *(internal GUI, private)* | GUI app that helps engineers assess patentability by generating and logging valid IKOFAX search queries for DEPATISnet (German Patent Office); designed for non-technical users with clipboard integration and reproducibility tracking | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Tkinter](https://img.shields.io/badge/Interface-Tkinter-grey) |
| [**Flask Skill-Gap Tool**](https://github.com/daniel-lee-wilkinson/skill-bubbles) *(in development)* | Visualises organisational skill distribution vs project demands based on user self-ratings and internal DB | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Flask](https://img.shields.io/badge/Interface-Flask-grey?logo=flask) |
| **Variable Network Visualiser** *(private)* | Interactive network graph to map and explore dependencies between engineering variables. Lines and arrows indicate strength and direction of relationships. Built collaboratively with research engineers to support knowledge transfer and internal model comprehension. | ![Language: R](https://img.shields.io/badge/Language-R-blue?logo=r) ![Visualisation: networkD3](https://img.shields.io/badge/Visualisation-networkD3-darkgreen) |

### Personal Projects & Fitness
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**Calorie Target Tracker**](https://github.com/daniel-lee-wilkinson/calorie_calculator) | App providing safe daily calorie targets based on weight goals, personalised activity (e.g. Zwift), and conservative burn estimates | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) |
| [**CLI Task Manager**](https://github.com/daniel-lee-wilkinson/task-webapp) *(private)* | Kanban-style CLI and Streamlit tool to prioritise tasks by energy and cognitive load | ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) |

### Training
| Project | Key Tasks | Skills Used |
|---------|-----------|-------------|
| [**CareerFoundry Portfolio**](https://github.com/daniel-lee-wilkinson/careerfoundry_DA) | Rebuilt a basic GSheets analysis project on CitiBike usage trends in Python and added a Streamlit calculator for transport/diet emissions | ![Tool: Google Sheets](https://img.shields.io/badge/Tool-Google_Sheets-grey?logo=googlesheets) ![Language: Python](https://img.shields.io/badge/Language-Python%203.11-blue?logo=python) ![Library: pandas](https://img.shields.io/badge/Library-pandas-green?logo=pandas) ![Visualisation: matplotlib](https://img.shields.io/badge/Visualisation-matplotlib-blue?logo=matplotlib) ![Interface: Streamlit](https://img.shields.io/badge/Interface-Streamlit-red?logo=streamlit) |
