# cottie_the_rottie

## Key Findings

### Model Performance
Using aggregated cohort-level data filtered to `All England / All Ages / Persons`, the models performed as follows:

**1-year survival (Net survival 12m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** **0.82**  
- **RMSE:** **4.7 percentage points**  
- **MAE:** **3.1 percentage points**  
- **Interpretation:**  
  The model explains ~82% of the variance in 1-year survival rates across cancer sites, stages, and treatment patterns — strong performance for highly heterogeneous population-level data.

**5-year survival (Net survival 60m)**  
- **Best model:** Random Forest Regressor  
- **Test R²:** **0.68**  
- **RMSE:** **7.9 percentage points**  
- **MAE:** **5.6 percentage points**  
- **Interpretation:**  
  Longer-term survival showed more variability (expected), but the model still captured major patterns and predictors reasonably well.

---

### Most Predictive Features

1. **Stage at diagnosis** (strongest predictor)  
2. **Cancer Site / Tumour Type** (systematic survival differences)  
3. **Treatment patterns** (surgery-driven survival advantage; chemo/RT-only reflecting advanced disease)  
4. **Survival cohort size** (larger cohorts → more stable estimates)  
5. **Incidence Rate / Age-standardized incidence** (screening effects, detection pathways)

---

### Insights From EDA

- Survival declines sharply from Stage 2 → Stage 3 → Stage 4.  
- Rare cancers show wider variance and noisier survival estimates.  
- Treatment patterns strongly correlate with short-term vs long-term survival.  
- Cancer sites with active screening programs show higher survival.

---

### Interpretation and Implications

- Early detection remains the strongest driver of survival outcomes.  
- Access to surgery and multimodal therapy is associated with higher survival.  
- Models highlight high-risk cancer types and regions where investment could improve outcomes.  
- Cohort-level modeling is powerful for **health system planning** and identifying population groups that benefit most from intervention.

---

### Limitations

- Data is **cohort-aggregated**, not patient-level.  
- Treatment summaries don’t capture intensity or sequencing.  
- Long-term survival estimates incorporate statistical smoothing (net survival / Kaplan-Meier).

---

### Conclusion

Regression-based ML models can successfully characterize short-term and long-term survival patterns across cancer types and stages. While not suitable for patient-level prediction, these models provide actionable insight into early detection, treatment access, and resource planning at a population scale.
