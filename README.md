COVID-19 Data Analysis Portfolio


This repository contains three independent data analysis and machine learning projects, each exploring a different aspect of the COVID-19 pandemic using publicly available datasets. The projects demonstrate a comprehensive data science workflow, including data cleaning, feature engineering, exploratory data analysis, and predictive modeling.

Table of Contents

Project 1: Global COVID-19 Snapshot Analysis (covid.ipynb)

Project 2: Time-Series Analysis of COVID-19 (covid_grouped.ipynb)

Project 3: US COVID-19 Mortality Analysis (coviddeath.ipynb)

Technologies Used

Project 1: Global COVID-19 Snapshot Analysis
Notebook: covid.ipynb

Project Objective

The primary goal of this project is to perform data cleaning and preprocessing on a global, country-level snapshot of the COVID-19 pandemic (likely from mid-2020). The final objective is to prepare the dataset for a regression task: predicting the total number of COVID-19 deaths per country based on other pandemic metrics and demographic information.

Dataset Overview

The dataset consists of 209 rows (countries/regions) and 17 columns. It includes features such as:

Demographics: Population, Continent

Pandemic Metrics: TotalCases, TotalDeaths, TotalRecovered, ActiveCases, Serious,Critical

Testing: TotalTests, Tests/1M pop

Geographic Identifiers: Country/Region, WHO Region, iso_alpha

Key Steps & Methodology

Data Inspection & Cleaning:

Initial exploration revealed a significant number of missing values, particularly in columns like NewCases, NewDeaths, and NewRecovered.

These high-null columns were dropped as they provided little value for a static snapshot analysis.

For other numerical columns with missing values, the median was used for imputation to minimize the impact of outliers.

Categorical missing values (e.g., in WHO Region) were filled with "Unknown".

Column names were standardized to a lowercase, underscore-separated format (e.g., Country/Region -> country_region).

Feature Engineering:

The population column was converted to an integer data type.

One-Hot Encoding was applied to the continent and who_region columns to convert these categorical features into a numerical format suitable for machine learning models.

The country_region column, being a unique identifier, was dropped from the feature set.

Model Preparation:

The target variable (y) was set as totaldeaths.

The feature set (X) was created by dropping the target column and selecting only numerical data types (integers, floats, and the new boolean columns from one-hot encoding).

Feature Scaling: All features were standardized using StandardScaler to ensure they have a mean of 0 and a standard deviation of 1, which is a crucial step for many machine learning algorithms.

Results & Insights

This notebook successfully transforms a raw, messy dataset into a clean, structured format ready for predictive modeling. The key insight is the effective handling of missing data and categorical variables, which are common challenges in real-world datasets. The final output is a feature matrix (X) and a target vector (y) primed for a regression algorithm like Linear Regression, Random Forest, or Gradient Boosting.

Project 2: Time-Series Analysis of COVID-19
Notebook: covid_grouped.ipynb

Project Objective

This project analyzes a time-series dataset tracking the daily progression of the COVID-19 pandemic across multiple countries. The objective is to perform extensive feature engineering to create a rich dataset suitable for time-series forecasting or regression analysis on daily new cases and deaths.

Dataset Overview

The dataset is much larger, containing 35,156 rows and 11 columns. It tracks daily metrics from January to July 2020 for numerous countries. Key columns include:

Date, Country/Region

Confirmed, Deaths, Recovered, Active

New cases, New deaths, New recovered

WHO Region, iso_alpha

Key Steps & Methodology

Data Preprocessing:

Standardized column names and converted the Date column to a proper datetime format.

Ensured all numerical columns were of the correct numeric type.

Feature Engineering (Creating Predictive Features):

Rate Calculation: New features like Death Rate, Recovery Rate, and Active Rate were derived from cumulative columns to provide relative measures of the pandemic's impact.

Temporal Features: The date column was decomposed into year, month, day, and dayofweek to capture seasonal patterns and weekly trends.

Rolling Averages: To smooth out daily fluctuations and highlight underlying trends, 7-day rolling averages were calculated for both new_cases and new_deaths for each country.

Handling Missing Values: Initial NaN values from the rolling averages were filled with 0, and a linear interpolation method was used for any remaining gaps.

Label Encoding: Categorical columns (country_region, who_region, iso_alpha) were converted into numerical codes using LabelEncoder to make them usable by machine learning models.

Results & Insights

The project successfully engineers a comprehensive dataset with 20 features from a simple time-series format. The most valuable insights come from the creation of rolling averages, which effectively visualize the smoothed trend of the pandemic, and the decomposition of dates, which can reveal day-of-week effects in reporting. This dataset is now a powerful resource for building predictive models.

Project 3: US COVID-19 Mortality Analysis
Notebook: coviddeath.ipynb

Project Objective

The goal of this project is to analyze US COVID-19 mortality data and build a regression model to predict the number of deaths based on demographic factors (state, age group) and pre-existing health conditions.

Dataset Overview

The dataset contains 12,260 rows and 10 columns. It provides a detailed breakdown of COVID-19 deaths in the US.

Geographic Info: State

Demographic Info: Age Group

Health Context: Condition Group, Condition, ICD10_codes

Target Variable: Number of COVID-19 Deaths

Metadata: Flag (indicating suppressed data)

Key Steps & Methodology

Data Cleaning & Preprocessing:

Dropped redundant date columns that contained only a single value.

Addressed a significant number of missing values in the target variable (due to suppression rules for small counts) by filling them with 0.

Filled missing Flag values with "Unknown".

Converted the target variable to an integer type.

Filtering & Encoding:

Removed summary rows like "All ages" and "Not stated" to focus the analysis on specific age groups.

Removed a special state indicator ('YC') that was not a standard state.

Grouped rare states (with fewer than 50 occurrences) into an "Other" category to reduce noise.

Target Encoding: Applied target encoding to high-cardinality categorical features (State, Condition, ICD10_codes, Condition Group). This technique replaces each category with the mean of the target variable (Deaths_log) for that category, creating a powerful numerical feature.

Log Transformation: Applied a log transformation (np.log1p) to the target variable (Number of COVID-19 Deaths) to handle its skewed distribution and reduce the impact of extreme values.

Modeling with Gradient Boosting:

The final feature set (X) included the target-encoded categorical columns and the Age_encoded column.

The data was split into training and testing sets (80/20 split).

A GradientBoostingRegressor was trained on the log-transformed target variable.

Model performance was evaluated using Root Mean Squared Error (RMSE).

Results & Insights

The trained Gradient Boosting model achieved an RMSE of 0.681 on the log-transformed test data. This indicates that the model can predict the log of deaths with reasonable accuracy. The most significant insights from this analysis are the critical roles of age and pre-existing conditions in determining mortality risk. The use of target encoding proved to be an effective strategy for incorporating high-cardinality categorical data into the model.

Technologies Used

Python: Core programming language.

Pandas & NumPy: For data manipulation, cleaning, and numerical operations.

Matplotlib & Seaborn: For data visualization and exploratory analysis (though limited in these notebooks, they are imported).

Scikit-learn: For preprocessing (StandardScaler, LabelEncoder), model training (GradientBoostingRegressor), and evaluation metrics.

Category Encoders: For advanced categorical encoding techniques like TargetEncoder.

