# 🎓 Education Project: ACT Performance and Socioeconomic Factors

## 📘 Project Overview
This project analyzes how community and socioeconomic conditions influence academic performance across U.S. public high schools, measured by **average ACT scores**.  
Using national datasets from **EdGap.org** and the **National Center for Education Statistics (NCES)**, the analysis explores how poverty, education level, income, and demographics predict school-level outcomes.

Conducted as part of **DATA 5100: Foundations of Data Science** at Seattle University, this project applies exploratory data analysis and regression modeling to study how inequality affects educational opportunity.

---

## 🗂️ Project Structure

```
education/
├─ data/                  # Raw and processed data
├─ code/                  # Jupyter notebooks and Python scripts
├─ reports/               # Generated reports and visualizations
├─ requirements.txt       # Dependencies
└─ README.md              # Project documentation
```

---

## 🧾 Data

| Dataset | Description | Source |
|----------|--------------|--------|
| **EdGap_data.xlsx** | School-level socioeconomic and achievement data | [EdGap.org](https://github.com/brian-fischer/DATA-5100/blob/main/EdGap_data.xlsx) |
| **ccd_sch_029_1617_w_1a_11212017.csv** | NCES Common Core of Data (CCD) School Directory | [Dropbox link](https://www.dropbox.com/scl/fi/fkafjk8902sq8ptxh94r2/ccd_sch_029_1617_w_1a_11212017.csv?rlkey=gucrdz5f6e38bezz2y3yalxbw&e=2&dl=0) |
| **CCD Membership Data** | Enrollment by race and ethnicity | [NCES](https://nces.ed.gov/ccd/) |

**Sample size:** 7,846 public high schools  
**Unit of analysis:** School level (not individual students)

---

## ⚙️ Analysis

### 🧩 Overview
The analysis examines whether **school-level ACT performance** can be predicted using social and economic characteristics of the surrounding community.  
It draws on three educational frameworks:
- **Resource Availability Theory:** Higher income and education → stronger school resources  
- **Family Structure Models:** Family stability supports student achievement  
- **Opportunity Gap Framework:** Systemic inequities limit access for low-income and minority students  

### 🧮 Methods
Four stages of analysis were completed using Python (`pandas`, `statsmodels`, `scikit-learn`):

1. **Exploratory Data Analysis (EDA):**  
   - Examined distributions and correlations.  
   - Identified strong negative relationships between ACT scores and both poverty and minority share.  

2. **Single-Factor Models:**  
   - Median income (R² = 0.212)  
   - Minority percentage (R² = 0.286)  

3. **Multiple Regression Model:**  
   - Six socioeconomic predictors tested; all significant (p < 0.05).  
   - R² = 0.609.  

4. **Reduced Three-Factor Model:**  
   - Retained poverty (% free/reduced lunch), community education (% adults with college degrees), and minority composition (% minority students).  
   - R² = 0.608 — nearly identical fit to the full model.  
   - Mean Absolute Error (MAE) = 1.17 ACT points.

---

### 📊 Results

| Factor | Coefficient (β) | Standardized β | Relationship |
|---------|-----------------|----------------|---------------|
| % Free/Reduced Lunch | -6.74 | -1.61 | Negative |
| % Adults with College Degrees | 2.43 | 0.31 | Positive |
| % Minority Students | -0.08 | -0.29 | Negative |

- **Model fit:** R² = 0.608 (≈61% of score variation explained)  
- **Most influential factor:** School poverty rate  
- **Model validity:** Residuals showed no violations of linearity or constant variance.

---

### 💬 Discussion
- **Poverty** was the strongest predictor, reflecting the impact of limited resources, teacher turnover, and lower parental support.  
- **Community education level** positively influenced performance, likely due to higher funding and educational expectations.  
- **Minority composition** correlated negatively with ACT scores, consistent with research showing that schools serving larger minority populations often face greater structural inequities.  
- **Unemployment and family structure** had smaller yet measurable effects, indicating that broader community stability also contributes.  
- The model explains about 61% of variation, leaving 39% attributable to other influences such as instruction quality, leadership, and student motivation.

---

## 🏛️ Key Takeaways
- School-level poverty is the **strongest and most consistent** predictor of ACT performance.  
- Targeted funding and student-support programs should focus on schools with high poverty rates.  
- Broader community investments in education and workforce development are also essential to close opportunity gaps.  

---

## ⚙️ Dependencies
Install project requirements using:
```bash
pip install -r requirements.txt
