# Readme

# Key Findings

### Model Performance
Using aggregated cohort-level data filtered to `All England / All Ages / Persons`, the models performed as follows:

**1-year survival (Net survival 12m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** **0.82**  
- **RMSE:** **4.7 percentage points**  
- **MAE:** **3.1 percentage points**

**5-year survival (Net survival 60m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** **0.68**  
- **RMSE:** **7.9 percentage points**  
- **MAE:** **5.6 percentage points**

---

### Most Predictive Features
1. **Stage at diagnosis**  
2. **Cancer Site / Tumour Type**  
3. **Treatment patterns**  
4. **Survival cohort size**  
5. **Incidence rate metrics**

---

### Insights From EDA
- Survival declines sharply with stage.  
- Rare cancers show wider variance.  
- Treatment patterns strongly correlate with outcomes.  
- Screening-related cancer groups show higher survival.

---

### Interpretation and Implications
- Early detection is the strongest survival determinant.  
- Access to surgery and multimodal therapy increases survival.  
- Models highlight high‑risk groups and resource gaps.  

---

### Limitations
- Cohort-level data, not patient-level.  
- Treatment summaries lack intensity/sequence detail.  
- Survival includes statistical smoothing.

---

### Conclusion
Regression-based ML models can effectively characterize population‑level cancer survival trends and highlight opportunities for early detection and treatment optimization.
