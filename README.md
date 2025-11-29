# 📱 Google Play Store App Analytics & Rating Prediction

*A Complete End-to-End Data Science Project*

This project analyzes the **Google Play Store dataset** to identify key factors that influence app success and to **predict app ratings** using machine learning. It covers the full data science pipeline—data cleaning, EDA, feature engineering, model building, and sentiment analysis of user reviews.

The insights generated can help app developers, product managers, and businesses make **data-driven decisions** to improve app quality and user satisfaction.

---

## 📂 Datasets Used

**1. `googleplaystore.csv`**
Contains metadata for ~10,000 apps including:

* Category, Rating, Size
* Installs, Price, Type
* Content Rating, Reviews
* Last Updated, Android Version, etc.

**2. `googleplaystore_user_reviews.csv`**
Contains 100 pre-processed (Positive/Negative/Neutral) reviews per app.

---

## 🛠 Technologies & Libraries

* **Python** – Core language
* **Pandas, NumPy** – Data cleaning & transformation
* **Matplotlib, Seaborn** – Visualization
* **Scikit-Learn** – Machine learning (Random Forest), preprocessing

---

## ⚙️ Project Workflow (Step-by-Step)

### **1. Data Loading & Initial Inspection**

* Loaded both datasets
* Checked shape, datatypes, missing values, duplicates
* Identified corrupted entries

### **2. Data Cleaning**

* Fixed data types for:

  * **Installs** (`10,000+` → `10000`)
  * **Price** (`$4.99` → `4.99`)
  * **Size** (`19M` → `19.0 MB`)
* Standardized all sizes to **Megabytes**
* Removed known corrupted row (`index 10472`)
* Cleaned non-numeric characters

### **3. Missing Value Treatment**

* Imputed missing **Ratings** using **median per Category**
* Dropped rows with critical missing fields:
  *Android Ver*, *Current Ver*

### **4. Exploratory Data Analysis (EDA)**

Key insights:

* **Most common categories:** Family, Game, Tools
* **Rating distribution:** Mostly 4.0–4.5
* **Pricing:** ~90% apps are free
* Visualized distributions, correlations, counts, and install patterns

### **5. Feature Engineering**

Created additional predictive features:

* **Revenue Estimate** = Price × Installs
* **Size_Group** = Small / Medium / Large
* **Year_Updated** = Extracted from Last Updated
* **Review_Ratio** = Reviews ÷ Installs

### **6. ML Preprocessing**

* Encoding:

  * Binary: `Type (Free=0, Paid=1)`
  * Ordinal: `Content Rating`, `Size_Group`
  * One-Hot: `Category`
* Train-test split: **80% Train, 20% Test**

### **7. Rating Prediction Model**

Model Used: **Random Forest Regressor**

**Performance:**

* **MAE ≈ 0.35 stars** (model predicts ratings within ~0.35 of actual)
* **Important features:** Reviews, Size, Category, Year Updated

### **8. Sentiment Analysis (User Reviews)**

* Analyzed sentiment polarity (Positive/Negative/Neutral)
* Findings:

  * **Health & Fitness** apps see the most positive sentiments
  * **Game** apps show highly variable sentiment (bugs, ads, crashes)
  * Neutral reviews mostly contain objective suggestions

---

## 📊 Key Insights & Findings

* **Free vs Paid:**
  Paid apps have lower installs but stronger user engagement.

* **Frequent Updates Improve Ratings:**
  Apps updated more recently (especially 2018) tend to have higher ratings.

* **Optimal App Size Matters:**
  Moderate-sized, well-optimized apps outperform extremely heavy ones.

* **User Sentiment Trends:**
  Negative reviews are highly emotional; neutral reviews focus on feature requests.

---

## ▶ How to Run

1. Clone the repository
2. Install dependencies:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. Place both datasets in the project folder:

   * `googleplaystore.csv`
   * `googleplaystore_user_reviews.csv`
4. Run the notebook or Python script:

   ```bash
   jupyter notebook
   ```

---

## 🚀 Future Improvements

* Implement **NLP topic modeling** to automatically classify complaint types (UI issues, bugs, ads, performance).
* Experiment with advanced models: **XGBoost**, **LightGBM**, **CatBoost**.
* Deploy an **interactive Streamlit dashboard** to explore insights dynamically.
* Build a **real-time app rating prediction API**.

---
