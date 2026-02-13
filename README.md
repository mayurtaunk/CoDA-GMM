# Financial Risk Clustering of Indian Listed Firms via Compositional Data Geometry

**Author:** Mayur Taunk
**Affiliation:** Faculty of Engineering and Technology, Parul University, India
**Paper Status:** Submitted to *International Journal of Intelligent Engineering and Systems (IJIES)*

---

## 📌 Project Overview
This repository contains the core clustering algorithm and validation code for the research paper **"Financial Risk Clustering of Indian Listed Firms via Compositional Data Geometry."**

The study proposes a novel unsupervised framework to detect financial risk in the Indian stock market (NSE) by moving beyond static industry classifications. It utilizes **Compositional Data Analysis (CoDa)** to correct geometric biases in financial ratios and **Gaussian Mixture Models (GMM)** to identify latent risk clusters.

---

## 🛠️ Data Pipeline & Methodology
This project follows a rigorous 3-phase pipeline. **Phase 1 and 2 (Data Preparation)** were performed offline due to the proprietary nature of the raw financial data. **Phase 3 (Clustering & Validation)** is fully reproducible in this repository.

### ✅ Phase 1: Data Curation (Pre-Processing)
* **Source:** We extracted raw **XBRL financial statements** (Balance Sheet, P&L, Cash Flow) directly from the **National Stock Exchange (NSE)**.
* **Census:** The dataset covers a complete census of **2,067 listed firms** for the period FY 2020-2025.
* **Sparsity Handling:** Instead of standard mean imputation (which destroys volatility), we applied a novel **"Entity-Specific Texture Repair"** algorithm to interpolate missing values while preserving firm-specific variance.

### ✅ Phase 2: Geometric Transformation (Pre-Processing)
* **Closure:** Raw financial values were normalized to handle the "Unit Sum Constraint" (Assets = Equity + Liabilities).
* **Transformation:** The closed data was transformed using **Isometric Log-Ratio (ilr)** coordinates. This maps the data from the restricted Simplex geometry to open Euclidean space, making it mathematically valid for clustering.

### 🚀 Phase 3: Risk Clustering (Reproducible Here)
* **Input:** The `processed_ilr_data.csv` file in this repo contains the output of Phase 2 (the transformed coordinates).
* **Algorithm:** We apply **Gaussian Mixture Models (GMM)** to these coordinates.
* **Validation:** The code calculates the **Bayesian Information Criterion (BIC)** to determine the optimal number of clusters ($K=19$) and validates the "Logistics Paradox" (Delhivery vs. Blue Dart).

---

## 📂 Repository Contents

| File | Description |
| :--- | :--- |
| **`GMM_Risk_Clustering.ipynb`** | **(Main Code)** Loads the processed data, runs the GMM algorithm, minimizes BIC, and assigns risk labels. |
| **`ilr_coordinates.csv`** | **(Input Data)** The geometrically transformed (ilr) coordinates. Use this to verify the clustering results. |
| **`final_cluster_labels.csv`** | **(Output)** The final list of firms and their assigned Risk Cluster (0-18). |
| **`Validation_and_Forensics.ipynb`** | **(Paper Figures & Case Study)** Generates the **"Cluster DNA" Heatmaps** (Fig 3 & 4) and performs the forensic comparison of *Delhivery* vs. *Blue Dart* (The Logistics Paradox). |

---

## ⚠️ Data Availability Note
Due to restrictions on the raw NSE XBRL dataset, the original financial statements cannot be shared publicly. However, the **processed ilr-coordinate dataset** is provided to allow researchers to:
1.  **Verify the Clustering Logic:** Run the GMM algorithm to reproduce the 19 risk archetypes.
2.  **Validate Findings:** Confirm the separation of "Operational Strangers" (e.g., *Delhivery* and *Blue Dart*) into distinct clusters.

---

## 📜 Citation
If you use this code or methodology, please cite:
> M. Taunk, V. Patidar. "Financial Risk Clustering of Indian Listed Firms via Compositional Data Geometry," *International Journal of Intelligent Engineering and Systems*, 2026 (Under Review).
