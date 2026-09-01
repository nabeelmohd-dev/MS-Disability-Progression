# Machine Learning Prediction of Long-Term Disability Progression in Multiple Sclerosis

[![R Version](https://img.shields.io/badge/R-v4.3%2B-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-brightgreen.svg)]()

A reproducible research repository evaluating missing data strategies, feature formulations, and supervised machine learning classifiers to predict **Unconfirmed Disability Progression (UDP)** in Multiple Sclerosis (MS) using longitudinal registry data.

---

## 📌 Executive Summary

Predicting long-term disability progression from early Expanded Disability Status Scale (EDSS) trajectories is critical for targeted MS clinical management. This project analyzes clinical registry cohorts across extended observation windows (6+ years) to evaluate:

1. **Missing Data Handling:** Comparing Complete Case Analysis, Median Imputation, Multivariate Imputation by Chained Equations (MICE with Predictive Mean Matching), and Bayesian MCMC Multiple Imputation (`jomo`).
2. **EDSS Trajectory Formulations:** Evaluating continuous linear OLS slopes, variance, and baseline metrics against discrete ordinal step-change representations.
3. **Supervised Classifiers:** Evaluating Penalized Logistic Regression (LASSO via `glmnet`), Random Forest, and Gradient Boosting (`gbm`) using cross-validation.

---

## 📂 Repository Architecture

```gcode
ms-disability-progression/
├── .gitignore                  # Strictly excludes raw patient files and temporary knitted outputs
├── ms-disability-progression.Rproj # RStudio project configuration
├── LICENSE                     # Open-source MIT License
├── README.md                   # Repository overview and setup documentation
├── MSDisabilityProgression.Rmd # Main end-to-end analytical notebook and execution report
├── data/
│   ├── raw/                    # Un-tracked raw clinical exports (.csv, .rds)
│   └── processed/              # Intermediate cleaned cohort matrices and imputed objects
└── outputs/
    ├── figures/                # Exported plots (ROC curves, calibration plots, trajectory charts)


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
  "rmarkdown",
  "ggpubr"
))

```

---

## ⚙️ Usage & Execution

1. Open `ms-disability-progression.Rproj` in RStudio to establish relative root paths.
2. Execute the single comprehensive RMarkdown document to run the entire data cleaning, imputation, modeling, and plotting workflow:

```R
rmarkdown::render("MSDisabilityProgression.Rmd")

```

Or open `MSDisabilityProgression.Rmd` directly in RStudio and click **Knit**.

---

## 📜 License & Author

Distributed under the **MIT License**. See `LICENSE` for details.

* **Author:** Nabeel Mohammed
* **Academic Context:** MSc Data Science Thesis

