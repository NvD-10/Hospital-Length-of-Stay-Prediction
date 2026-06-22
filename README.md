# 🏥 Hospital Length of Stay Prediction

A Machine Learning project that predicts the **Length of Stay (LoS)** of hospitalized patients using demographic, clinical, and laboratory data. Accurate prediction of patient stay duration helps hospitals optimize bed allocation, improve patient flow, reduce operational costs, and enhance healthcare service delivery.

---

## 📌 Project Overview

Hospital Length of Stay (LoS) is one of the most important operational metrics in healthcare management. Predicting how long a patient will remain hospitalized enables hospitals to better manage resources and improve care quality.

This project applies and compares two machine learning regression models:

- Linear Regression (Baseline Model)
- Random Forest Regression (Ensemble Model)

The dataset contains **100,000 patient records** and **27 clinical features**, including demographic information, medical history, comorbidity indicators, laboratory measurements, and vital signs.

---

## 🎯 Objectives

- Perform Exploratory Data Analysis (EDA)
- Assess and improve data quality
- Preprocess and engineer predictive features
- Train multiple regression models
- Evaluate model performance using standard metrics
- Identify the most influential factors affecting hospital stay duration

---

## 📊 Dataset Information

**Source:** Microsoft R Server Hospital Length of Stay Dataset

### Dataset Statistics

| Property | Value |
|-----------|--------|
| Records | 100,000 |
| Features | 28 |
| Target Variable | Length of Stay (days) |
| Missing Values | None |
| Duplicate Records | None |
| Data Type | Mixed (Numerical, Binary, Categorical) |

### Main Feature Categories

#### Demographic & Clinical History
- Readmission Count (`rcount`)
- Gender
- Secondary Diagnosis Count

#### Comorbidity Indicators
- Asthma
- Pneumonia
- Depression
- Malnutrition
- Renal Disease
- Substance Dependence
- Hemoglobin Disorders
- Psychological Disorders
- And others

#### Clinical Measurements
- Hematocrit
- Glucose
- Sodium
- Creatinine
- Blood Urea Nitrogen
- BMI
- Pulse Rate
- Respiration Rate
- Neutrophil Count

#### Target Variable
- `lengthofstay`
  - Minimum: 1 day
  - Maximum: 17 days
  - Mean: 4 days

---

## 🔧 Data Preprocessing

### 1. Data Cleaning
- Removed duplicate records
- Corrected invalid glucose value
- Handled categorical inconsistencies

### 2. Feature Removal

The following columns were excluded to prevent data leakage:

- `eid`
- `vdate`
- `discharged`
- `facid`

### 3. Encoding

- Gender:
  - Female → 0
  - Male → 1

- Readmission count (`5+`) converted to integer value `5`

### 4. Feature Engineering

Created a new feature:

```text
total_issues
```

This feature represents the total number of comorbidities present in a patient and serves as an overall health burden indicator.

### 5. Train-Test Split

```text
Training Set: 80%
Testing Set: 20%
Random State: 42
```

### 6. Feature Scaling

Applied StandardScaler for:

- Linear Regression

Not applied for:

- Random Forest Regression

---

## 🤖 Machine Learning Models

### Linear Regression

A baseline model that assumes a linear relationship between input features and hospital stay duration.

### Random Forest Regression

An ensemble learning algorithm that combines multiple decision trees to capture complex nonlinear relationships and feature interactions.

Configuration:

```python
RandomForestRegressor(
    n_estimators=100,
    random_state=42
)
```

---

## 📈 Evaluation Metrics

### R² Score

Measures how much variance in the target variable is explained by the model.

### RMSE (Root Mean Squared Error)

Measures average prediction error in days.

---

## 🏆 Results

| Model | R² Score | RMSE |
|---------|---------|---------|
| Linear Regression | 0.7522 | 1.1661 |
| Random Forest Regression | 0.9410 | 0.5687 |

### Key Findings

- Random Forest significantly outperformed Linear Regression.
- The model explained **94.1%** of the variation in patient length of stay.
- Average prediction error was reduced by approximately **51%** compared to the baseline model.

---

## 🔍 Feature Importance

| Rank | Feature | Importance |
|--------|----------|-----------|
| 1 | Readmission Count (`rcount`) | 0.5643 |
| 2 | Total Issues (`total_issues`) | 0.2132 |
| 3 | Hematocrit | 0.0387 |
| 4 | BMI | 0.0255 |
| 5 | Glucose | 0.0255 |
| 6 | Creatinine | 0.0253 |
| 7 | Sodium | 0.0251 |
| 8 | Respiration | 0.0247 |
| 9 | Pulse | 0.0238 |
| 10 | Neutrophils | 0.0162 |

### Insight

Patients with:
- Frequent prior admissions
- Multiple comorbidities
- Abnormal laboratory measurements

tend to have longer hospital stays.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/NvD-10/Hospital-Length-of-Stay-Prediction.git

cd Hospital-Length-of-Stay-Prediction
```

Install dependencies:

```bash
pip install // needed packages
```

---

## ▶️ Running the Project

Train the model:

```bash
python train.py
```

Run predictions:

```bash
python predict.py
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

---

## 📌 Future Improvements

- Hyperparameter tuning using GridSearchCV
- K-Fold Cross Validation
- XGBoost comparison
- LightGBM comparison
- Deep Learning approaches
- Real-time deployment using Flask or FastAPI
- Integration with Hospital Information Systems
- Interactive dashboard for hospital administrators

---

## 👨‍💻 Authors

- Kaleb Dagnachew (ETS0747/15)
- Kalkidan Agonafir (ETS0749/15)
- Kernemi Kidane (ETS0760/15)
- Lidiya Abebe (ETS0832/15)
- Meti Seboka (ETS0918/15)
- Nehemiah Mitiku (ETS1082/15)

---

## 📄 License

This project was developed for academic and educational purposes as part of the Introduction to Machine Learning course.
