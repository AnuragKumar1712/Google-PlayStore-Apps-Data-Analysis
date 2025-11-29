Google Play Store Apps DataGoogle Play Store App Analytics & Rating Prediction
📌 Project Overview
This project analyzes the Google Play Store dataset to uncover key factors that drive app success. It
involves an end-to-end data science workflow, including data cleaning, exploratory data analysis
(EDA), feature engineering, machine learning for rating prediction, and customer sentiment analysis.
The goal is to provide actionable insights for developers and businesses to improve their app
performance and user satisfaction.
📂 Datasets
The project uses two datasets (originally from Kaggle):
1. googleplaystore.csv : Contains details of ~10,000 apps (Category, Rating, Size, Installs, Price,
Content Rating, etc.).
2. googleplaystore_user_reviews.csv : Contains 100 top reviews for each app with sentiment
pre-processed (Positive, Negative, Neutral).
🛠️Technologies Used
Python: Core programming language.
Pandas & NumPy: Data manipulation and cleaning.
Matplotlib & Seaborn: Data visualization.
Scikit-Learn: Machine learning (Random Forest Regressor) and preprocessing.
⚙️ Project Workflow
The project was executed in 8 distinct steps:
1. Data Loading & Inspection
Loaded datasets and performed initial health checks (data types, missing values, duplicates).
2. Data Cleaning
Fixed Data Types: Converted "Installs" ( 10,000+ -> 10000 ), "Price" ( $4.99 -> 4.99 ), and
"Size" ( 19M -> 19.0 ).
Error Handling: Removed a known "shifted" row (index 10472) where data was corrupted.
Standardization: Converted all sizes to Megabytes.
3. Missing Value Treatment
Imputation: Filled missing Ratings using the Median Rating of the app's specific Category .
Cleaning: Dropped rows with critical missing metadata (Android Ver, Current Ver).
4. Exploratory Data Analysis (EDA)
Category Popularity: "Family", "Game", and "Tools" are the most dominant categories.
Rating Distribution: Skewed towards high ratings (most apps are rated 4.0 - 4.5).
Pricing: ~90% of apps are Free.
5. Feature Engineering
Created new features to improve model performance:
Revenue : Estimated revenue ( Price * Installs ).
Size_Group : Bucketed apps into 'Small', 'Medium', and 'Large'.
Year_Updated : Extracted from the Last Updated timestamp.
Review_Ratio : Engagement metric ( Reviews / Installs ).
6. Pre-processing for ML
Encoding:
Binary: Type (Free=0, Paid=1).
Ordinal: Content Rating , Size_Group .
One-Hot: Category (converted to binary columns).
Split: Divided data into 80% Training and 20% Testing sets.
7. Machine Learning Model (Random Forest)
Trained a Random Forest Regressor to predict App Ratings.
Performance Metrics:
MAE (Mean Absolute Error): ~0.35 stars (The model's prediction is usually within 0.35 stars
of the actual rating).
Feature Importance: Identified that Reviews , Size , and Category are strong predictors
of an app's rating.
8. Customer Sentiment Analysis
Analyzed user reviews to understand subjectivity and polarity.
Found that Health & Fitness apps generally have the highest positive sentiment, while Game
apps show high variability (likely due to bugs or ads).
📊 Key Findings
1. Paid vs. Free: Paid apps tend to have slightly fewer installs but higher engagement from loyal
users.
2. Updates Matter: Apps updated in the last year (2018) correlate with higher ratings.
3. Size Impact: "Varies with device" and optimized (Medium) sizes perform better than massive,
unoptimized apps.
4. Sentiment: Neutral reviews are usually objective (feature requests), while extremely negative
reviews are highly subjective (emotional complaints).
🚀 How to Run
1. Clone this repository.
2. Install dependencies:
pip install pandas numpy matplotlib seaborn scikit-learn
3. Place googleplaystore.csv and googleplaystore_user_reviews.csv in the root directory.
4. Run the analysis script (e.g., in Jupyter Notebook or Python).
🔮 Future Work
Implement NLP (Natural Language Processing) on raw review text to categorize complaints (e.g.,
"bugs", "ads", "UI").
Test XGBoost or LightGBM models to potentially improve prediction accuracy.
Build a dashboard (using Streamlit) to interactively explore the data.
