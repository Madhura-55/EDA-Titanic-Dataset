# 🚢 Data Storytelling: Analysing Survival on the Titanic

An end-to-end Exploratory Data Analysis (EDA) project on the Titanic dataset, uncovering the key factors that influenced passenger survival through data cleaning, visualization, feature engineering, and correlation analysis.

---

## 📌 Project Objective

To perform a comprehensive, step-by-step EDA to understand what factors determined survival on the Titanic — confirming the "women and children first" narrative and revealing stark social inequalities through data.

---

## 📁 Dataset

- **Source:** [Titanic Dataset – GeeksForGeeks 21-Days-21-Projects](https://github.com/GeeksforgeeksDS/21-Days-21-Projects-Dataset)
- **Local File:** titanic.csv
- **Size:** 891 rows × 12 columns
- **Target Variable:** `Survived` (0 = No, 1 = Yes)

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `pandas` | Data loading, manipulation, and cleaning |
| `numpy` | Numerical operations |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualizations |
| `ydata-profiling` | Automated data profiling report |

---

## 📊 Project Workflow

### 1. Data Loading & Inspection
- Loaded dataset using `pd.read_csv()`
- Inspected shape, data types, and missing values using `.info()` and `.describe()`

### 2. Data Cleaning
- **Age:** Filled missing values with the median (robust to skew/outliers)
- **Embarked:** Filled 2 missing values with the mode
- **Cabin:** Created a new binary feature `Has_Cabin` (1/0), then dropped the original column due to ~77% missing data

### 3. Univariate Analysis
- Analyzed distributions of individual features
- Most passengers were male, traveled in 3rd class, and embarked from Southampton ('S')
- `Fare` is heavily right-skewed with significant outliers

### 4. Bivariate Analysis
- Compared each feature against the `Survived` target
- Used bar plots, histograms, and FacetGrids

### 5. Feature Engineering
- `FamilySize` = `SibSp` + `Parch` + 1
- `IsAlone` = 1 if `FamilySize == 1`, else 0
- `Title` extracted from passenger names using regex and grouped rare titles

### 6. Multivariate Analysis
- Explored interactions between `Pclass`, `Sex`, `Age`, and `Survived`
- Used violin plots and categorical plots (`catplot`)

### 7. Correlation Analysis
- Generated a heatmap of the correlation matrix for all numerical features

### 8. Automated Profiling
- Used `ydata-profiling` to generate a full HTML profiling report (`sample.html`)

---

## 🔍 Key Findings

1. **Sex / Title** — Strongest predictor. Females (Mrs, Miss) had ~75% survival rate vs. ~18% for males (Mr). Young boys (Master) also had a notably higher survival rate than adult men.
2. **Passenger Class** — Clear survival hierarchy: 1st class (>60%) > 2nd class > 3rd class (<25%).
3. **Age** — Infants and children had higher survival rates. Peak non-survivors were in the 20–40 age range.
4. **Family Size** — Small families (2–4 members) had the highest survival rates. Solo travelers and very large families fared worse.
5. **Fare / Cabin** — Having a cabin and paying a higher fare (proxy for wealth) strongly correlated with survival.
6. **Port of Embarkation** — Cherbourg ('C') passengers had a higher survival rate, likely because more 1st class passengers boarded there.

---

## 📂 Output Files

| File | Description |
|---|---|
| `eda_titanic.ipynb` | Main analysis notebook |

---

## 🚀 How to Run

```bash
# Clone the repo
git clone https://github.com/Madhura-55/eda_titanic

# Install dependencies
pip install pandas numpy matplotlib seaborn ydata-profiling

# Open the notebook
colab notebook eda_titanic.ipynb
```

---

## 📈 Next Steps

This EDA lays the foundation for building a **machine learning classification model** to predict passenger survival using the engineered features identified here.
