
🌍 COVID-19 Data Analysis Portfolio

This repository contains three independent data analysis and machine learning projects, each exploring a different aspect of the COVID-19 pandemic using publicly available datasets. The projects demonstrate a comprehensive data science workflow, including data cleaning, feature engineering, exploratory data analysis, and predictive modeling.

📋 Table of Contents
🌟 Overview
🌍 Project 1: Global COVID-19 Snapshot Analysis

📅 Project 2: Time-Series Analysis of COVID-19

⚕️ Project 3: US COVID-19 Mortality Analysis

🛠️ Technologies Used

🎯 Skills Demonstrated

🌟 Overview
This repository contains three independent data science projects, each exploring a different aspect of the COVID-19 pandemic using publicly available datasets. The projects showcase a complete data science workflow including:

✅ Data Cleaning & Missing Value Treatment
✅ Feature Engineering & Extraction
✅ Exploratory Data Analysis
✅ Predictive Modeling
✅ Model Evaluation & Validation

🌍 Project 1: Global COVID-19 Snapshot Analysis
Notebook: covid.ipynb
Tags: #DataCleaning #OneHotEncoding #FeatureEngineering

🎯 Project Objective
This project aims to clean and preprocess a comprehensive global dataset of COVID-19 metrics across different countries, preparing it for machine learning models that can predict total deaths based on pandemic indicators and demographic information.

🔍 Key Steps
Data Exploration: Understanding variable types and identifying missing values

Handling Missing Data: Smart imputation using median for numerical features and "Unknown" for categorical ones

Column Standardization: Renaming columns to consistent, usable formats

Categorical Encoding: Applying One-Hot Encoding to continents and WHO regions

Data Preparation: Separating features from target variable and scaling using StandardScaler

💡 Key Insights
Successfully transformed raw, unstructured data into a clean, analysis-ready dataset. The project demonstrates effective strategies for handling two of the most common challenges in real-world data science: missing values and categorical variables.

📅 Project 2: Time-Series Analysis of COVID-19
Notebook: covid_grouped.ipynb
Tags: #TimeSeries #RollingAverages #AdvancedFeatureEngineering

🎯 Project Objective
This project analyzes daily COVID-19 progression data across multiple countries, creating rich features capable of capturing temporal patterns and hidden trends in virus spread.

🔍 Key Steps
Date Processing: Converting date columns to proper datetime format

Temporal Feature Extraction: Deriving year, month, day, and day of week to capture periodic patterns

Rate Calculations: Creating death, recovery, and active case percentages

Rolling Averages: Computing 7-day moving averages for new cases and deaths per country

Categorical Encoding: Converting categorical variables to numerical codes using LabelEncoder

💡 Key Insights
Successfully engineered a rich dataset with 20+ features from simple time-series data. Rolling averages proved most valuable for smoothing daily fluctuations and revealing true pandemic trends, while day-of-week analysis uncovered fascinating reporting patterns.

⚕️ Project 3: US COVID-19 Mortality Analysis
Notebook: coviddeath.ipynb
Tags: #TargetEncoding #GradientBoosting #MortalityAnalysis

🎯 Project Objective
To analyze US COVID-19 mortality data and build a regression model predicting death counts based on demographic factors (state, age group) and pre-existing health conditions.

🔍 Key Steps
Data Cleaning: Removing redundant columns and handling suppressed data

Filtering: Focusing on specific age groups and removing summary rows

Handling Rare Categories: Grouping infrequent states into "Other" category

Target Encoding: Applying advanced encoding to high-cardinality categorical features

Log Transformation: Transforming skewed target variable for better model performance

Gradient Boosting: Building and evaluating a regression model

💡 Key Insights
The Gradient Boosting model achieved strong predictive performance, revealing that age and pre-existing conditions are the most critical factors in COVID-19 mortality. Target encoding proved exceptionally effective for incorporating high-cardinality categorical data.

🛠️ Technologies Used
Technology	Purpose
Python	Core programming language
Pandas & NumPy	Data manipulation and numerical operations
Matplotlib & Seaborn	Data visualization and exploratory analysis
Scikit-learn	Preprocessing, model training, and evaluation
Category Encoders	Advanced categorical encoding techniques
🎯 Skills Demonstrated
Data Wrangling: Cleaning messy real-world datasets

Missing Value Treatment: Strategic imputation techniques

Feature Engineering: Creating predictive features from raw data

Categorical Encoding: One-Hot, Label, and Target encoding

Time Series Analysis: Rolling averages and temporal patterns

Machine Learning: Building and evaluating regression models

Model Interpretation: Understanding feature importance and model limitations

