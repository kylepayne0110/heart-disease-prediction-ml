# Heart Disease Prediction with Machine Learning

## 🎯 Project Overview

Built and evaluated multiple supervised learning models to predict heart disease from clinical measurements using a dataset of 303 patients with 14 clinical variables. Compared logistic regression and random forest approaches for both classification and regression tasks, achieving **84.8% AUC** with an advanced logistic model.

## 📊 Key Results

| Model | Accuracy | Precision | Recall | AUC | RMSE |
|-------|----------|-----------|--------|-----|------|
| **Logistic Regression (Simple)** | 73.6% | 73.2% | 81.2% | 80.1% | - |
| **Logistic Regression (Advanced)** | 76.2% | 78.2% | 78.2% | **84.8%** | - |
| **Random Forest Classifier** | 98.8% (train) / 65.2% (test) | 73.1% | 67.9% | - | - |
| **Random Forest Regressor** | - | - | - | - | 20.85 bpm |

## 🛠️ Technologies & Methods

**Programming & Tools:**
- R programming language
- Jupyter Notebooks
- Statistical packages: `ResourceSelection`, `pROC`, `rpart.plot`, `randomForest`

**Machine Learning Techniques:**
- Logistic regression with interaction terms and polynomial features
- Random forest classification with hyperparameter tuning
- Random forest regression for continuous outcome prediction
- Train/test validation splitting

**Statistical Methods:**
- Hosmer-Lemeshow goodness-of-fit testing
- Wald hypothesis testing for coefficient significance
- ROC curve analysis and AUC calculation
- Confusion matrix metrics (accuracy, precision, recall)
- Feature engineering (quadratic terms, interaction terms)

## 🔬 Models Developed

### Model 1: Simple Logistic Regression
**Predictors:** Age, resting blood pressure, exercise-induced angina, maximum heart rate

**Key Finding:** Exercise-induced angina and maximum heart rate were significant predictors (p < 0.001), while age and blood pressure were not significant in this specification.

### Model 2: Advanced Logistic Regression ⭐ (Recommended)
**Predictors:** Age, age², chest pain type (categorical), resting blood pressure, maximum heart rate, age×heart rate interaction

**Key Findings:**
- Chest pain type indicators were highly significant (p < 0.001)
- Age×heart rate interaction was significant (p = 0.036)
- Improved discrimination over simple model (AUC: 0.848 vs 0.801)
- Better balance of precision and recall

**Clinical Interpretation:** Risk increased for patients with non-typical angina chest pain types, and the effect of maximum heart rate on heart disease risk varied by age through the interaction term.

### Model 3: Random Forest Classifier
**Configuration:** 49 trees (optimized via error curve analysis)

**Key Findings:**
- Excellent training performance (98.8% accuracy) but moderate test performance (65.2%)
- Evidence of overfitting despite tuning
- Less interpretable than logistic regression for clinical applications

### Model 4: Random Forest Regressor
**Configuration:** 29 trees optimized for predicting maximum heart rate

**Performance:** RMSE of 20.85 bpm on test set (training RMSE: 11.55 bpm)

**Use Case:** Acceptable for rough estimation or imputation of missing heart rate values, but not precise enough to replace actual measurement.

## 📈 Visualizations

The analysis includes:
- ROC curves comparing model discrimination ability
- Error curves for random forest hyperparameter tuning
- Confusion matrices for classification performance
- Model diagnostics and goodness-of-fit assessments

## 💡 Business Value & Applications

**Healthcare Screening:**
- Convert patient profiles into predicted probabilities for triage and prioritization
- Adjust probability thresholds based on institutional goals (e.g., maximize recall for screening)

**Clinical Decision Support:**
- Identify high-risk patients for early intervention
- Guide conversations about cardiovascular risk factors

**Research Insights:**
- Chest pain type, blood pressure, and maximum heart rate emerged as key risk indicators
- Age-related effects on heart rate risk were non-linear (captured by interaction terms)

## 📁 Repository Contents

- `MAT_303_Project_Two_Jupyter_Notebook.html` - Complete R analysis notebook with code and outputs
- `MAT_303_Project_Two_Summary_Report.pdf` - Detailed technical report with interpretations
- `README.md` - This file

## 🔍 Dataset Information

**Source:** Heart disease dataset with 303 patient records

**Variables (14 total):**
- **Outcome:** `target` (0 = no heart disease, 1 = heart disease)
- **Demographics:** age, sex
- **Clinical measurements:** resting blood pressure, serum cholesterol, fasting blood sugar, max heart rate
- **Diagnostic indicators:** chest pain type, resting ECG results, exercise-induced angina, ST depression, ST slope, vessels colored by fluoroscopy, thalassemia

## 🎓 Statistical Methodology

**Model Evaluation Framework:**
1. **Goodness-of-fit:** Hosmer-Lemeshow test assessed whether observed outcomes matched predicted probabilities
2. **Coefficient testing:** Wald tests identified significant predictors at α = 0.05
3. **Discrimination:** ROC curves and AUC measured ability to separate disease vs. no-disease cases
4. **Classification metrics:** Confusion matrices provided accuracy, precision, and recall
5. **Validation:** Train/test splits prevented overfitting and assessed generalization

**Feature Engineering:**
- Quadratic age term to capture non-linear age effects
- Age×heart rate interaction to model how the heart rate effect varies by age
- Categorical encoding of chest pain types

## 📝 Model Selection Rationale

**Recommended Model:** Logistic Regression Model 2 (Advanced)

**Reasons:**
1. **Best test set performance:** Highest AUC (84.8%) and accuracy (76.2%)
2. **Interpretability:** Coefficients directly link predictors to odds of disease
3. **Clinical utility:** Easy to explain to healthcare professionals
4. **Balanced metrics:** Good precision and recall without severe overfitting
5. **Significant predictors:** Chest pain type, blood pressure, heart rate, and interaction terms all significant

**Why not Random Forest?**
- Severe overfitting (98.8% training accuracy → 65.2% test accuracy)
- Less interpretable for clinical applications
- Would require additional tuning and validation

## 🚀 Future Improvements

- Cross-validation for more robust performance estimates
- Additional feature engineering (e.g., blood pressure × age interactions)
- Ensemble methods combining logistic and tree-based models
- External validation on separate hospital datasets
- Cost-sensitive learning to account for false negative consequences

## 👨‍💻 Author

**Kyle Payne**  
Data Analyst | Machine Learning | Healthcare Analytics  
[LinkedIn](https://linkedin.com/in/kyle-payne-68408812a/) | [GitHub](https://github.com/kylepayne0110)

---

*This project demonstrates machine learning model development, statistical hypothesis testing, model evaluation, and clinical data analysis for healthcare risk prediction applications.*
