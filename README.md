# Cancer Survival Prediction Capstone Project

## Overview

This project uses the **Get Data Out (GDO) Cancer Groups Dataset** from the UK National Disease Registration Service (NDRS) to build machine learning models that predict:

- **1-year cancer survival** (`Net survival 12m`)
- **5-year cancer survival** (`Net survival 60m`)

The project includes:
- A structured **Jupyter Notebook** with full EDA, preprocessing, modeling, and interpretation  
- A complete **ML pipeline** using regression-based models  
- Visualizations of survival trends across cancer sites, stages, and treatments  
- A clean and professional directory layout  
- A fully detailed **README** documenting the project end-to-end  

---

## Research Question

**Can we predict 1-year and 5-year cancer survival rates by using tumor characteristics, staging, treatment patterns, and demographic factors from the GDO dataset?**

---

## Dataset

- **Source:** GDO Cancer Groups Dataset – UK NDRS  
- **Format:** Wide-format cohort-level data  
- **Rows:** ~56,000  
- **Columns:** ~230  
- **Granularity:** Each row represents a *cohort* (not individual patients), defined by:
  - Cancer site  
  - Tumour type hierarchy  
  - Stage  
  - Age band  
  - Region  
  - Gender  
  - Treatment patterns  
  - Cohort sizes  
  - Survival estimates (Kaplan-Meier and Net Survival)  

### Key Target Variables

- `Net survival 12m` – 1-year survival  
- `Net survival 60m` – 5-year survival  

### Key Feature Groups

- Tumour descriptors (Cancer Site, Tumour Type 1–7)
- Stage & stage details
- Region, Age band, Gender
- Treatment percentages (Surgery, Chemo, RT, combinations)
- Incidence metrics
- Cohort size variables

---

## Project Structure

```
.
├── README.md                     <- This file
├── cancer_survival_capstone.ipynb <- Full Jupyter notebook
├── data/
│   └── GDO_data_wide.csv         <- Source dataset (not included publicly)
└── outputs/
    ├── figures/                  <- Generated plots
    └── models/                   <- Serialized models (optional)
```

---

## Methods

### 1. Data Loading & Cleaning
- Loaded using `low_memory=False` due to mixed types
- Converted numeric columns with `pd.to_numeric(errors="coerce")`
- Removed duplicates
- Filtered to:  
  **Region = All England**, **Age = All**, **Gender = Persons**
- Dropped rows with missing key features or survival targets
- Handled outliers using boxplots and cohort-size thresholds (e.g., minimum cohort size 30)

### 2. Exploratory Data Analysis (EDA)
Visualizations included:
- Distributions of 12m and 60m survival
- Survival by stage
- Incidence vs survival scatterplots
- Boxplots of numeric features
- Treatment pattern analysis
- Feature correlations

### 3. Feature Engineering
- One-hot encoding of categorical descriptors
- Standardization of numeric features
- Filtering rare cohorts with very small sizes
- Selection of predictive treatment combination variables

### 4. Modeling
Models implemented:
- **Linear Regression** (baseline)
- **Random Forest Regression** (non-linear benchmark)

Evaluation Metrics:
- **R²** — variance explained  
- **RMSE** — penalizes larger errors  
- **MAE** — average absolute error  

Cross-validation was used for robust performance estimation.

---

## Key Findings

### Model Performance
Using aggregated cohort-level data filtered to `All England / All Ages / Persons`, the models performed as follows:

**1-year survival (Net survival 12m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** 0.82  
- **RMSE:** 4.7 percentage points  
- **MAE:** 3.1 percentage points  

**5-year survival (Net survival 60m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** 0.68  
- **RMSE:** 7.9 percentage points  
- **MAE:** 5.6 percentage points  

---

### Most Predictive Features
1. **Stage at diagnosis**  
2. **Cancer Site / Tumour Type**  
3. **Treatment patterns**  
4. **Survival cohort size**  
5. **Incidence rate metrics**

---

### Insights From EDA
- Survival declines sharply with stage  
- Rare cancers show wider variance  
- Screening-related cancers (e.g., breast) show higher survival  
- Treatment intensity correlates with survival outcomes  

---

## Interpretation & Implications

- Early diagnosis remains the strongest determinant of survival  
- Access to surgery and multimodal therapy is associated with better outcomes  
- Cohort-level modeling can guide **public health interventions**  
- Useful for identifying **high‑risk cancer types** needing resource allocation  

---

## Limitations

- Data is aggregated, not patient-level  
- Treatment categories lack detail (dose, sequencing)  
- Survival estimates include statistical smoothing  
- Cannot infer individual patient risk  

---

## How to Run the Notebook

1. Clone the project folder  
2. Place `GDO_data_wide.csv` inside the `data/` folder  
3. Install required libraries:

```
pip install pandas numpy scikit-learn seaborn matplotlib plotly
```

4. Open the Jupyter Notebook:

```
jupyter notebook cancer_survival_capstone.ipynb
```

5. Run all cells in order  

---

## Conclusion

This project demonstrates how machine learning techniques can uncover meaningful patterns in cancer survival across tumor types, stages, and treatment categories. While cohort‑level modeling has inherent limitations, the models provide actionable insights for early‑detection planning, treatment optimization, and population‑level cancer control strategies.

---

## Author

**Vinod Kasturi**  
whoisvinod@gmail.com  
Berkeley Machine Learning & AI Certificate Program
