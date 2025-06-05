# Credit_Risk_Assessment

This notebook presents a comprehensive data analysis on credit risk assessment using loan application data. It includes a step-by-step exploratory data analysis (EDA) to uncover relationships between borrower attributes (such as income, age, loan amount, and interest rate) and their repayment status (fully repaid or defaulted).
Based on the insights from EDA, a Random Forest Classifier is trained to predict the likelihood of loan repayment for new applicants, achieving a final accuracy of 93%

# 📌 Credit Risk Analysis Project

---

## 🎯 Goal

The goal of this project is to analyze borrower data and build models that predict loan repayment outcomes. Specifically, we aim to:

* Identify key demographic and financial factors influencing default risk.
* Explore relationships between age, income, home-ownership, and loan purpose.
* Train and evaluate baseline and advanced models (Logistic Regression, Random Forest) to achieve high prediction accuracy.

---

## 🔍 Discoveries (Question-Based Approach)

### 1. Age and Outliers

* **Average Age**: 27
* **Outlier Definition**: Borrowers over 40 were classified as statistical outliers.

### 2. Loan Purpose by Age Group

* **Young (20–30)** → **EDUCATION**
* **Middle (30–40)** → **MEDICAL**
* **Old (40+)** → **PERSONAL**

```text
Most Common Loan Intent per Age Group:
age_group
  Young (20–30)     EDUCATION
  Middle (30–40)      MEDICAL
  Old (40+)          PERSONAL
dtype: object
```

### 3. Home-Ownership Distribution (Overall and by Age)

* **Overall**: Renting is the most common home-ownership status.
* **By Age Group**:

  * Young (20–30): **RENT**
  * Middle (30–40): **RENT**
  * Old (40+): **RENT**

### 4. Loan Defaults by Home-Ownership

* **Renters** represent the largest share of loan defaults—indicating higher default risk among rental borrowers.

### 5. Income Distribution

* **Largest Segment**: Middle income (\$40 000–\$60 000 annual).
* **Income Classes**:

  * **Poor**: < \$40 000
  * **Middle**: \$40 000–\$60 000
  * **Rich**: \$60 000–\$80 000
  * **Very Rich**: ≥ \$80 000

### 6. Home-Ownership vs. Income Class

* **Poor & Middle**: Predominantly **renters** (> 55 %).
* **Rich & Very Rich**: Majority hold **mortgages** (> 48 % and > 63 %, respectively).

### 7. Loan Repayment by Income Class

```text
Percentages by Income Class:
loan_status       Repaid  Default
income_class                     
  Poor (<40k)         60.3     39.7
  Middle (40–60k)     78.8     21.2
  Rich (60–80k)       84.8     15.2
  Very Rich (>80k)    90.9      9.1
```

* **Observation**: Default rates decrease as income increases.

### 8. Loan Purpose by Income Class

* **Poor (<\$40k)** → **MEDICAL**
* **Middle (40–60k)** → **EDUCATION**
* **Rich (60–80k)** → **EDUCATION**
* **Very Rich (≥\$80k)** → **EDUCATION**

```text
Most Common Loan Intent per Income Class:
income_class
  Poor (<40k)           MEDICAL
  Middle (40–60k)     EDUCATION
  Rich (60–80k)       EDUCATION
  Very Rich (>80k)    EDUCATION
dtype: object
```

### 9. Age Group vs. Income Class (Row-Percentages)

| age\_group     | Poor (<40k) | Middle (40–60k) | Rich (60–80k) | Very Rich (>80k) |
| -------------- | ----------- | --------------- | ------------- | ---------------- |
| Young (20–30)  | 27.5 %      | 28.7 %          | 21.1 %        | 22.8 %           |
| Middle (30–40) | 24.2 %      | 25.6 %          | 20.2 %        | 30.0 %           |
| Old (40+)      | 22.4 %      | 25.7 %          | 20.9 %        | 30.9 %           |

---

## 📈 Experiments & Results

### Baseline Model

* **Model**: Logistic Regression
* **Accuracy**: 0.86

### Experiment 1: Removing Outliers

1. Identified most predictive features for the target variable.
2. Analyzed feature distributions and detected outlier observations (age > 40).
3. Filtered dataset to remove outliers.
4. Reran Logistic Regression → **Accuracy: 0.87** (≈ 10 % relative improvement).
5. Trained Random Forest on filtered data → **Accuracy: 0.93**.

### Experiment 2: Dropping Less Effective Features

* **Dropped Columns**:
  `cb_person_default_on_file`, `loan_grade_B`, `loan_grade_F`, `loan_grade_G`
* **Result**: No significant change in Logistic Regression (remained 0.87).

---

## 🏆 Conclusion

* Demographic factors (age, income, home-ownership) and loan purpose are highly predictive of loan repayment behavior.
* Removing outliers and focusing on the most informative features led to a noticeable gain in baseline model performance.
* The Random Forest model achieved **93 %** accuracy, demonstrating effectiveness in credit risk prediction for this dataset.

---

*Made with ✨ data insights and 📊 machine learning.*
*Dataset: https://www.kaggle.com/datasets/urvishvekariya/credit-risk-assessment*
