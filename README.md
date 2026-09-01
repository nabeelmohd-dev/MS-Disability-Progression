Here is a complete, publication-ready **`README.md`** structured like a professional open-source data science repository.

### How to use this:

1. In your project folder, open **`README.md`** in VS Code, RStudio, or Notepad.
2. Select all existing text (`Ctrl + A`) and delete it.
3. Copy the entire markdown block below and paste it directly into the file.
4. Save the file (`Ctrl + S`).

---

```markdown
# Machine Learning Prediction of Long-Term Disability Progression in Multiple Sclerosis

[![R Version](https://img.shields.io/badge/R-v4.3%2B-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-brightgreen.svg)]()

A modular, reproducible research repository evaluating missing data strategies, feature formulations, and supervised machine learning classifiers to predict **Unconfirmed Disability Progression (UDP)** in Multiple Sclerosis (MS) using longitudinal registry data.

---

## 📌 Executive Summary

Predicting long-term disability progression from early Expanded Disability Status Scale (EDSS) trajectories is critical for targeted MS clinical management. This project analyzes clinical registry cohorts across extended observation windows (6+ years) to evaluate:

1. **Missing Data Handling:** Comparing Complete Case Analysis, Median Imputation, Multivariate Imputation by Chained Equations (MICE with Predictive Mean Matching), and Bayesian MCMC Multiple Imputation (`jomo`).
2. **EDSS Trajectory Formulations:** Evaluating continuous linear OLS slopes, variance, and baseline metrics against discrete ordinal step-change representations.
3. **Supervised Classifiers:** Evaluating Penalized Logistic Regression (LASSO via `glmnet`), Random Forest, and Gradient Boosting (`gbm`) using nested 5-fold cross-validation.

---

## 📂 Repository Architecture

```gcode
ms-disability-progression/
├── .gitignore                      # Strictly excludes raw patient files and temporary R output
├── ms-disability-progression.Rproj # RStudio project configuration
├── LICENSE                         # Open-source MIT License
├── README.md                       # Repository overview and setup documentation
├── MSDisabilityProgression.Rmd     # Primary synthesis notebook and execution report
├── data/
│   ├── raw/                        # Un-tracked raw clinical exports (.csv, .rds)
│   └── processed/                  # Intermediate cleaned cohort matrices and imputed objects
├── R/                              # Modularized pipeline execution scripts
│   ├── 01_data_cleaning.R          # Parsing, type casting, date normalization, deduplication
│   ├── 02_cohort_selection.R       # Patient eligibility criteria and visit count filters
│   ├── 03_feature_engineering.R    # OLS slope calculations, variances, EDSS step changes
│   ├── 04_imputation.R             # MICE PMM and Bayesian MCMC (jomo) imputation chains
│   ├── 05_feature_selection.R      # LASSO variable selection across imputed datasets
│   └── 06_model_evaluation.R       # Cross-validation loops, ROC-AUC, Brier score computations
└── outputs/
    ├── figures/                    # Exported plots (ROC curves, calibration plots, trajectory charts)
    └── tables/                     # Performance metrics tables (CSV / LaTeX format)

```

---

## 🔒 Data Privacy & Governance

> [!WARNING]
> **Patient Privacy Notice:** This repository contains **no patient-level clinical data or identifiable registry exports**. All datasets located within `data/raw/` and `data/processed/` are explicitly ignored via `.gitignore` to comply with HIPAA, GDPR, and institutional health data governance policies.

---

## 🚀 Getting Started

### Prerequisites

* **R Environment:** `v4.3.0` or higher (tested on `v4.5.1`)
* **IDE:** [RStudio](https://posit.co/download/rstudio-desktop/) (recommended)

### Installation

Clone the repository to your local system:

```bash
git clone [https://github.com/YOUR_USERNAME/ms-disability-progression.git](https://github.com/YOUR_USERNAME/ms-disability-progression.git)
cd ms-disability-progression

```

Install the required dependency packages in R:

```R
install.packages(c(
  "tidyverse", 
  "mice", 
  "jomo", 
  "glmnet", 
  "randomForest", 
  "gbm", 
  "pROC", 
  "rmarkdown"
))

```

---

## ⚙️ Usage & Pipeline Execution

1. Open `ms-disability-progression.Rproj` in RStudio to establish relative root paths.
2. Execute individual scripts sequentially inside `R/` or run the primary synthesis report:

```R
rmarkdown::render("MSDisabilityProgression.Rmd")

```

---

## 🧪 Pipeline Stage Descriptions

| Stage Script | Core Functionality |
| --- | --- |
| **`01_data_cleaning.R`** | Parses raw EDSS visit logs, cleans date entries, handles visit deduplication, standardizes treatment history. |
| **`02_cohort_selection.R`** | Implements inclusion rules ($\ge 2$ EDSS visits in Y0–3, $\ge 1$ visit in Y4–6) to build modeling cohorts. |
| **`03_feature_engineering.R`** | Derives individual longitudinal trajectory slopes, baseline disability metrics, and progression targets. |
| **`04_imputation.R`** | Fits parallel MICE and Bayesian MCMC chains to populate missing covariates without data leakage. |
| **`05_feature_selection.R`** | Applies L1 penalized LASSO models across imputed sets to extract stable feature subsets. |
| **`06_model_evaluation.R`** | Evaluates predictive performance across classifiers using 5-fold CV (ROC-AUC, Brier Score, calibration). |

---

## 📜 License & Author

Distributed under the **MIT License**. See `LICENSE` for details.

* **Author:** Nabeel Mohammed
* **Academic Context:** MSc Data Science Thesis, University of Limerick

```

<ElicitationsGroup message="What would you like to do next?">
  <Elicitation label="Draft 01_data_cleaning.R" query="Let's start drafting the code for R/01_data_cleaning.R based on MSDisabilityProgression.Rmd"/>
  <Elicitation label="Connect repo to GitHub" query="How do I create a GitHub repository and push this local project to it?"/>
</ElicitationsGroup>

```