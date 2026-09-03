# Machine Learning Prediction of Long-Term Disability Progression in Multiple Sclerosis

[![R Version](https://img.shields.io/badge/R-v4.3%2B-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-brightgreen.svg)]()

A reproducible research repository evaluating missing data strategies, feature formulations, and supervised machine learning classifiers to predict **Unconfirmed Disability Progression (UDP)** in Multiple Sclerosis (MS) using longitudinal registry data.

---

## 📌 Executive Summary

Predicting long-term disability progression from early Expanded Disability Status Scale (EDSS) trajectories is critical for targeted MS clinical management. Using a single-centre registry of 400 patients, features were extracted from the first three years since symptom onset and used to predict unconfirmed disability progression (UDP) in years four to six. After applying inclusion criteria, the final modelling cohort was 74 patients (17 UDP events). This project evaluates:

1. **Missing Data Handling:** Comparing Complete Case Analysis, Median Imputation, Multivariate Imputation by Chained Equations (MICE with Predictive Mean Matching), and Bayesian MCMC Multiple Imputation (`jomo`).
2. **EDSS Trajectory Formulations:** Evaluating continuous linear OLS slopes, variance, and baseline metrics against discrete ordinal step-change representations.
3. **Supervised Classifiers:** Evaluating Penalized Logistic Regression (LASSO via `glmnet`), Random Forest, and Gradient Boosting (`gbm`) using five-fold cross-validation.

### Key Findings

- The **ordinal EDSS arm**, which required no imputation, consistently outperformed the complete-case and median-imputed continuous strategies, achieving AUC 0.942–0.951 and Brier scores of 0.093–0.131 with the most stable cross-validation results of any strategy.
- **MICE gradient boosting** achieved the best result in the full comparison matrix: AUC 0.957, Brier score 0.073.
- Ordinal change in EDSS (net step change over the feature window) was the dominant predictor across both the random forest and gradient boosting models, roughly 6.6 times more important than the next-ranked feature.
- A tipping-point sensitivity analysis showed the study's conclusions were robust to plausible departures from the Missing At Random assumption (AUC range of 0.041 across the tested shifts).
- Complete case analysis was the least reliable strategy: it dropped 22 patients whose progression rate was higher than the retained cohort's, and produced the least stable cross-validated estimates of any strategy tested.

Full detail on methodology, results, and limitations is in the thesis document, `MSDisabilityProgression.pdf`.

---

## 📂 Repository Architecture

```
ms-disability-progression/
├── .gitignore                       # Strictly excludes raw patient files and temporary knitted outputs
├── ms-disability-progression.Rproj  # RStudio project configuration
├── LICENSE                          # Open-source MIT License
├── README.md                        # Repository overview and setup documentation
├── MSDisabilityProgression.Rmd      # Main end-to-end analytical notebook and execution report
├── MSDisabilityProgression.pdf      # Full thesis document (methods, results, discussion)
├── data/
│   ├── raw/                         # Un-tracked raw clinical exports (.csv, .rds)
│   └── processed/                   # Intermediate cleaned cohort matrices and imputed objects
└── outputs/
    └── figures/                     # Exported plots (ROC curves, calibration plots, trajectory charts)
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
git clone https://github.com/YOUR_USERNAME/ms-disability-progression.git
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

## 📊 Results Summary

Full comparison matrix (AUC and Brier score) across all five strategies and three models:

| Strategy | Model | AUC | Brier |
|---|---|---|---|
| Complete Case – Continuous | Random Forest | 0.935 | 0.163 |
| Median Imputed – Continuous | Gradient Boosting | 0.862 | 0.136 |
| No Imputation – Ordinal | Logistic Regression | 0.951 | 0.122 |
| MICE – Continuous | Gradient Boosting | **0.957** | **0.073** |
| Bayesian MI (jomo) – Continuous | Random Forest | 0.944 | 0.090 |

A null model predicting the marginal event rate (23%) achieves a Brier score of approximately 0.177, for reference. The full fifteen-row comparison matrix, calibration plots, and feature importance results are in Chapter 4 of the thesis document.

---

## 📜 License & Author

Distributed under the **MIT License**. See `LICENSE` for details.

* **Author:** Nabeel Mohammed
* **Academic Context:** MSc Data Science Thesis

