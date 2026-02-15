# 🏥 Healthcare Patient Analytics Pipeline

An end-to-end Azure data pipeline built on **Medallion Architecture (Bronze → Silver → Gold)** to process real hospital patient records and generate analytics-ready insights.

---

## 🔧 Tech Stack
- **Azure Data Factory** — Pipeline orchestration & parameterized Copy Activity
- **Azure Databricks (PySpark)** — Data transformation & incremental loading
- **ADLS Gen2** — Data lake storage across all medallion layers
- **Azure Key Vault** — Secure secret management (no hardcoded credentials)

---

## 🏗️ What I Built

### Pipeline Flow
```
Raw CSV (Kaggle)
     ↓  ADF Copy Activity (CSV → Parquet + column mapping)
Silver Layer (cleaned Parquet)
     ↓  Databricks Notebook (PySpark transformations)
Gold Layer (3 analytics tables)
```

### Medallion Layers
| Layer | Format | Description |
|---|---|---|
| Bronze | CSV | Raw Kaggle dataset (55,500 rows, 8.4MB) |
| Silver | Parquet | Cleaned, typed, deduplicated (4.17MB) |
| Gold | Parquet | 3 aggregated analytics tables |

### Gold Tables
| Table | Insight |
|---|---|
| `readmission_rates` | Admissions by condition & type |
| `diagnosis_trends` | Cases by age group & year |
| `avg_treatment_costs` | Costs by condition, medication & insurer |

---

## ⚙️ Key Features
- **Parameterized ADF pipeline** — dynamic file paths, reusable across environments
- **Incremental loading** — watermark-based pattern processes only new records each run
- **Key Vault integration** — secrets fetched securely via Databricks secret scope
- **Managed Identity** — ADF authenticates to ADLS without stored credentials

---

## 📊 Dataset
[Hospital Patient Records — Kaggle](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)
55,500 rows | 15 columns | Patient admissions from 2019–2025

---


