# 🏥 Hospital Length of Stay Prediction Using Machine Learning

A machine learning project that predicts the **Length of Stay (LoS)** of hospitalized patients using demographic information, comorbidity indicators, laboratory measurements, and vital signs.

Accurate prediction of hospital stay duration helps healthcare institutions optimize resource allocation, improve patient flow, reduce operational costs, and enhance overall healthcare delivery.

---

## 📌 Project Overview

Hospital Length of Stay (LoS) is one of the most important operational metrics in healthcare management. Predicting how long a patient is likely to remain hospitalized enables hospitals to improve bed utilization, staff planning, and patient care efficiency.

This project develops and compares multiple machine learning regression models to predict patient length of stay using clinical and demographic information.

### Models Evaluated

* Linear Regression
* Ridge Regression
* Decision Tree Regression
* Random Forest Regression
* XGBoost Regression

---

## 🎯 Objectives

* Perform Exploratory Data Analysis (EDA)
* Assess data quality and consistency
* Clean and preprocess clinical data
* Engineer meaningful predictive features
* Train multiple regression models
* Compare model performance
* Identify factors influencing hospital stay duration

---

## 📊 Dataset Information

**Source:** Microsoft R Server Hospital Length of Stay Dataset

Source Documentation:

https://microsoft.github.io/r-server-hospital-length-of-stay/input_data.html

### Dataset Statistics

| Property          | Value                              |
| ----------------- | ---------------------------------- |
| Records           | 100,000                            |
| Features          | 28                                 |
| Target Variable   | Length of Stay (Days)              |
| Missing Values    | None                               |
| Duplicate Records | None                               |
| Data Type         | Numerical, Binary, and Categorical |

---

## 🧾 Feature Categories

### Demographic & Admission Information

* Readmission Count (rcount)
* Gender
* Secondary Diagnosis Count

### Comorbidity Indicators

* Asthma
* Pneumonia
* Depression
* Malnutrition
* Renal Disease
* Substance Dependence
* Hemoglobin Disorders
* Psychological Disorders
* Fibrosis and Other Chronic Conditions

### Clinical Measurements

* Hematocrit
* Glucose
* Sodium
* Creatinine
* Blood Urea Nitrogen
* BMI
* Pulse Rate
* Respiration Rate
* Neutrophil Count

### Target Variable

**lengthofstay**

* Minimum: 1 Day
* Maximum: 17 Days
* Mean: Approximately 4 Days

---

## 🔍 Exploratory Data Analysis

Several exploratory analyses were performed:

* Dataset structure inspection
* Missing value analysis
* Descriptive statistics
* Target variable distribution
* Correlation analysis
* Comorbidity frequency analysis
* Feature relationship exploration

### Key Findings

* No missing values were found.
* No duplicate patient records existed.
* One invalid negative glucose value was detected.
* Length of stay was right-skewed with most patients staying fewer than 6 days.
* Readmission count and comorbidity burden showed strong relationships with hospital stay duration.

---

## 🔧 Data Cleaning

### Data Quality Improvements

* Removed duplicate records
* Corrected invalid glucose measurement
* Standardized categorical values

### Removed Columns

The following columns were removed because they were identifiers or could introduce data leakage:

* eid
* vdate
* discharged
* facid

---

## ⚙️ Feature Engineering

### Encoding

#### Gender

* Female → 0
* Male → 1

#### Readmission Count

* "5+" converted to integer value 5

### New Feature Created

#### total_issues

Represents the total number of chronic conditions recorded for a patient.

```text
total_issues =
sum of all comorbidity indicators
```

This feature serves as an overall health burden indicator.

---

## 🧪 Data Preparation

### Train-Test Split

```text
Training Set : 80%
Testing Set  : 20%
Random State : 42
```

### Feature Scaling

Applied StandardScaler for:

* Linear Regression
* Ridge Regression

Not required for:

* Decision Tree
* Random Forest
* XGBoost

---

## 🤖 Machine Learning Models

### Linear Regression

Baseline regression model assuming a linear relationship between features and length of stay.

### Ridge Regression

Regularized linear regression used to reduce overfitting.

### Decision Tree Regression

Captures nonlinear relationships through recursive partitioning.

### Random Forest Regression

Ensemble learning model that combines multiple decision trees.

```python
RandomForestRegressor(
    n_estimators=100,
    random_state=42
)
```

### XGBoost Regression

Gradient boosting model capable of capturing complex feature interactions and nonlinear relationships.

```python
XGBRegressor(
    n_estimators=200,
    max_depth=6,
    learning_rate=0.1,
    random_state=42
)
```

---

## 📈 Evaluation Metrics

### R² Score

Measures how much variance in the target variable is explained by the model.

### RMSE

Root Mean Squared Error measures the average prediction error in days.

Lower RMSE indicates better prediction accuracy.

---

## 🏆 Model Performance

| Model             | R² Score  | RMSE      |
| ----------------- | --------- | --------- |
| Linear Regression | ~0.75     | ~1.17     |
| Ridge Regression  | ~0.75     | ~1.17     |
| Decision Tree     | Evaluated | Evaluated |
| Random Forest     | ~0.94     | ~0.57     |
| XGBoost           | ~0.97     | ~0.40     |

### Best Model

🏆 **XGBoost Regression**

Performance:

```text
R² Score ≈ 0.971
RMSE ≈ 0.397
```

The model explains approximately 97% of the variation in patient length of stay while maintaining very low prediction error.

---

## 🔍 Feature Importance

The most influential predictors included:

* Readmission Count (rcount)
* Total Issues (total_issues)
* Hematocrit
* BMI
* Glucose
* Creatinine
* Sodium
* Respiration Rate
* Pulse Rate
* Neutrophil Count

### Insight

Patients with:

* Frequent prior admissions
* Multiple comorbidities
* Abnormal laboratory measurements

tend to experience longer hospital stays.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost
* Jupyter Notebook

---

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/NvD-10/Hospital-Length-of-Stay-Prediction.git

cd Hospital-Length-of-Stay-Prediction
```

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

---

## ▶️ Running the Project

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Hospital_Length_of_Stay_Prediction.ipynb
```

Run all cells sequentially.

---

## 📌 Future Improvements

* Hyperparameter tuning with GridSearchCV
* K-Fold Cross Validation
* LightGBM comparison
* CatBoost comparison
* Deep Learning approaches
* Real-time deployment using Flask or FastAPI
* Integration with Hospital Information Systems
* Interactive analytics dashboard

---

## 👨‍💻 Authors

* Kaleb Dagnachew (ETS0747/15)
* Kalkidan Agonafir (ETS0749/15)
* Kernemi Kidane (ETS0760/15)
* Lidiya Abebe (ETS0832/15)
* Meti Seboka (ETS0918/15)
* Nehemiah Mitiku (ETS1082/15)

---

## 📄 License

This project was developed for academic and educational purposes as part of the Introduction to Machine Learning course.
