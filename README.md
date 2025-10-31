# 🗺️ Geo-Temporal Customer Behavior ETL: Fuzzy Merge Analysis

## 🎯 Project Overview

This repository contains the complete Extract, Transform, and Load (ETL) pipeline developed to solve a critical e-commerce attribution challenge: linking approximately $\sim 500,000$ anonymous online browsing sessions to over $\sim 180,000$ finalized sales transactions using spatial and temporal proximity.

The core deliverable is a validated **Fact Table** enriched with the **Attributable Turnaround Time** ($\mathbf{T_{\text{purchase}} - T_{\text{browse}}}$), a key metric for understanding customer deliberation and optimizing the conversion funnel.

## ⚙️ Core Technical Challenge & Methodology

The project overcame the challenge of missing user IDs by implementing a sophisticated **Geo-Temporal Fuzzy Merge**.

* **Spatial Proximity:** Max $\mathbf{10 \text{ km}}$ distance (calculated via Haversine formula).
* **Temporal Proximity:** Max $\mathbf{48 \text{ hours}}$ elapsed time ($\mathbf{T_{\text{purchase}}}$ must occur after $\mathbf{T_{\text{browse}}}$).
* **Efficiency Driver:** The pipeline utilizes the **KD-Tree** spatial indexing structure (SciPy) to achieve high-speed nearest-neighbor searches, reducing complexity and making the merge feasible on large datasets.

---

## 📊 Key Analytical Findings

The rigorous linking criteria successfully isolated a small, high-signal cohort ($0.1008\%$ of all purchases) that is $100\%$ valid for attribution analysis.

### 1. Segmentation Breakdown

The separation confirms that the majority of traffic is instant/direct ($\mathbf{T=0}$), while the linked segment represents the distinct, deliberative customer journey.

| Classification | Count | Percentage |
| :--- | :--- | :--- |
| **FOCUSED (Unlinked)** | $180337$ | $99.8992\%$ |
| **HIGH (Linked)** | $119$ | $0.0659\%$ |
| **MEDIUM (Linked)** | $63$ | $0.0349\%$ |

---

### 2. Turnaround Time & Validation

The minimum observed time for a successful conversion was $\mathbf{22 \text{ hours}}$, validating the entire ETL process by confirming that the traceable cohort is mathematically distinct from immediate, instantaneous purchases.

* **Metric:** **Attributable Turnaround Time** ($\mathbf{T_{\text{purchase}} - T_{\text{browse}}}$).
* **Empirical Finding:** $\mathbf{Min = 22 \text{ hours}}$.

![Turnaround Time Distribution Histogram Placeholder]()

### 3. Financial and Behavioral Insights

* **Average Profit per Converted Customer:** $\mathbf{\$68.95}$ (Validates the superior financial quality of the linked segment).
* **Category Bias:** Analysis confirmed that the **linked cohort** purchases complex/high-value durable goods, while the **unlinked cohort** favors commodity or low-cost items, further validating the distinction.

![Category Mapping Visualization Placeholder]()

---

## 📂 Repository Contents

| Path | Description |
| :--- | :--- |
| **`notebooks/`** | Contains the core code and execution log. |
| `notebooks/supply-chain-etl-project-shaizam-adil-khan.ipynb` | The executable Python code for the 4-stage ETL pipeline. |
| **`documentation/`** | Formal project deliverables and reference files. |
| `documentation/Shaizam Adil Khan - ETL pipeline.pdf` | The final, detailed project report (PDF). |
| `documentation/SUMMARY.md` | Quick reference guide to methodology and terms. |
| **`assets/`** | All images and visualizations used in the markdown files. |
| `requirements.txt` | Lists all necessary Python dependencies (Pandas, SciPy, Geopy, etc.). |

---

## 🚀 Future Work

The resulting Fact Table is ready for:

1. **Predictive Modeling:** Building a classification model to predict **Customer Lifetime Value (CLV)** using $\mathbf{Turnaround\_Time\_Hours}$ as a feature.
2. **Unsupervised Clustering:** Identifying new, data-driven **Customer Segments**.

**Note:** If modeling is implemented, the code would be added as `src/model.py`.

---
