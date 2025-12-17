# dbt for Solo Engineers: When It Helps, When It Doesn’t

> “dbt reduces cognitive load by externalising SQL dependencies and execution order into an explicit, inspectable graph.”

This note documents **when dbt-core is genuinely useful for a solo engineer**, what problems it actually solves, and **why I chose not to use it** in a real, Python-first CO₂ KPI pipeline.

This is not a dbt tutorial. It is an engineering decision record.

---

## When dbt *is* worth using

dbt tends to add value when **SQL is the primary transformation language** and you want to externalise structure that would otherwise live in your head.

In practice, this usually means:

- SQL is the main transformation language, not a helper
- Transformations are layered (raw → clean → KPIs)
- You revisit old projects and need fast re-orientation
- You dislike hidden state and implicit execution order
- You value structure and reproducibility over speed
- There is a stable, persisted handoff table where:
  - rows are semantically meaningful (e.g. cycles, process intervals)
  - table structure changes infrequently
  - multiple downstream calculations depend on it
- After this handoff, Python can stop caring what happens downstream

In this scenario, dbt functions as a **build system for SQL**, replacing mental bookkeeping with an explicit, inspectable graph.

---

## When dbt *is not* worth using

dbt often becomes overhead when **Python is the dominant orchestration and logic layer**.

This is typically the case when:

- Work is exploratory or frequently thrown away
- Pipelines are small, linear, and easy to reason about
- SQL is a thin wrapper around Python logic
- Python controls execution order end-to-end
- SQL is tightly coupled to Python loops and conditionals
- KPIs are computed inline during iteration
- There is no clean, stable handoff table
- Introducing dbt would require refactoring working code
- The pipeline is stable and rarely changes structurally

In these cases, dbt introduces a second mental model without removing existing complexity.

---

## What problems dbt actually solves

### 1. Implicit execution order → explicit graph  
**Problem:** hidden ordering logic and fragile mental bookkeeping  

- *Before dbt*: “Run A, then B, unless C changed.” Order lives in comments or memory.  
- *With dbt*: dependencies are declared with `ref()`. Order is derived. Impact is visible in the DAG.

---

### 2. Ad-hoc SQL → build artefacts  
**Problem:** SQL degrades into a stateless mess over time  

- *Before dbt*: SQL files are “things you run”; state lives in the database.  
- *With dbt*: SQL is compiled; outputs are reproducible from inputs. “Build the project” has meaning.

---

### 3. Self-imposed discipline → enforced modularity  
**Problem:** entropy creeping in when you’re the only enforcer  

- *Before dbt*: giant queries, table reuse “just this once”, skipped validation.  
- *With dbt*: models are isolated units, reuse requires `ref()`, tests are first-class.

---

### 4. Late failures → cheap correctness checks  
**Problem:** silent data breakage discovered weeks later  

dbt tests are trivial to add, cheap to run, and tied to the model graph—much harder to forget or half-implement.

---

### 5. Forgotten intent → self-documenting structure  
**Problem:** returning after 6 months and asking “why did I do this?”  

The DAG, model names, and dependencies encode intent with little extra effort.

---

## What dbt does *not* help with

- Ingestion  
- APIs  
- Streaming  
- Orchestration  
- Heavy Python logic  
- Exploratory analysis  

If your pipeline is **Python-first and SQL-secondary**, dbt may add coordination cost rather than clarity.

---

## Case study: CO₂ KPI pipeline (why I chose *against* dbt)

### Overview

This pipeline processes raw CO₂ capture system sensor data via API and produces validated, cycle-level and daily KPIs.  
It is maintained by a single engineer and prioritises correctness, reproducibility, and low cognitive overhead.

The system is **Python-first**, with SQL used as an embedded computation tool.

---

### Pipeline steps (authoritative flow)

1. **Data ingestion (Python)**  
   - Retrieve raw sensor time series  
   - Persist to SQLite / DuckDB  
   - Log failures and partial imports  

   *Rationale:* IO-bound, stateful, error-prone logic belongs in Python.

2. **Cleaning and validation (Python)**  
   - Remove invalid values, gaps, duplicates  
   - Enforce domain-specific checks  
   - Exclude bad data deliberately  

   *Rationale:* Procedural, exception-heavy logic.

3. **Cycle and process identification (Python)**  
   - Define cycles from step codes and transitions  
   - Handle temporal logic and edge cases  
   - Assign semantic identities  

   *Rationale:* This defines **meaning**, not just computation. SQL is a poor fit.

4. **Cycle-level data assembly (Python)**  
   - Aggregate cleaned data into stable, semantic rows  
   - Compute duration, energy, CO₂ mass  

   *Rationale:* Python remains the source of truth for correctness.

5. **KPI calculations (Python + embedded SQL)**  
   - SQL for aggregations and per-row formulas (e.g. `A * B`)  
   - Python controls execution and iteration  

   *Rationale:* SQL is used where it is strongest, but is not the orchestration layer.

6. **Export and reporting (Python)**  
   - Excel, Word, SQLite outputs  
   - Deterministic and reproducible  

   *Rationale:* Reporting is procedural and format-specific.

---

### Why dbt was not introduced

- Although dbt excels in SQL-first pipelines, this system’s control flow and domain logic are Python-dominant, which makes dbt a poor fit without a fundamental redesign.
- Core domain logic (cycle detection) is stateful and procedural  
- Introducing dbt mid-pipeline would require non-trivial refactoring of a stable, correctness-critical system, without a corresponding reduction in complexity or failure modes. 
- dbt would not reduce system-level cognitive load in this architecture because it would introduce a second execution model without replacing the existing Python control flow.

This was a **deliberate architectural decision**, not a limitation.

---

## Design principle applied

> **Use dbt where it reduces thinking.  
> Do not use it where it adds coordination cost.**

The pipeline is structured so dbt *could* be added later if a stable, SQL-first handoff layer becomes central. Until then, Python remains the authoritative layer by design.

---

## Summary

dbt is a powerful tool for SQL-first, layered transformation workflows - even for solo engineers.  
In this case, after evaluation, it was intentionally not adopted because the pipeline’s complexity is semantic and procedural rather than relational. Choosing *not* to use dbt here reflects architectural judgement, not tool avoidance.
