# Medical-Appointment-No-Show-Prediction-Exploratory-Data-Analysis
An initial Exploratory Data Analysis (EDA) project focused on a dataset of medical appointments in Brazil to identify key factors associated with patients failing to show up for their scheduled appointments.

📝 Project Purpose & Description

The purpose of this project is to perform a comprehensive Exploratory Data Analysis (EDA) on a dataset containing information about medical appointments. 
The primary goal is to uncover patterns and relationships between various patient characteristics and the target variable, "No-show". This initial analysis is crucial for:
1. Data Preparation: Cleaning, transforming, and formatting the raw data (e.g., date columns, handling bad data).
2. Feature Engineering: Creating new features (like sch_weekday and app_weekday) to derive more meaningful insights.
3. Bivariate Analysis: Visually and statistically examining which factors (age, gender, chronic diseases, etc.) have the strongest correlation with a patient missing their appointment.The insights gained will serve as the foundation for future work, such as building a predictive model to forecast appointment no-shows.
   
💻 Tech Stack

The analysis was performed using the Python programming language within a Jupyter Notebook environment, utilising the following core libraries:
1. Pandas: Used extensively for data loading, manipulation, cleaning, and transformation (e.g., handling date/time columns, grouping ages).
2. NumPy: Used for numerical operations, including conditional encoding of the target variable (No-show).
3. Matplotlib (plt): Used for basic visualisations (e.g., the initial "No Show" count plot).
4. Seaborn (sns): Used for advanced statistical visualisations (e.g., count plots comparing different feature distributions against the target variable and the correlation heatmap).


✨ Features & Highlights 

Business Problem

A high rate of missed medical appointments is a common and costly issue for healthcare providers, leading to wasted resources, reduced efficiency, and lost opportunities to serve other patients. The challenge is to determine which patient attributes contribute most significantly to a "No-show" appointment.

Goal of the Analysis

The core goal of this EDA is to perform data wrangling and initial feature-target analysis to understand the data's structure and identify potential predictive factors. The analysis aims to:

1. Clean Data: Transform date/time stamps into usable formats and handle invalid data points (e.g., negative age).
2. Structure Data: Rename confusing columns (Handcap to Handicap, No-show to No Show) and drop irrelevant identifiers (Patient ID, Appointment ID, Neighbourhood).
3. Feature Extraction: Calculate the day of the week for scheduling and appointment to analyze time-based patterns.
4. Variable Encoding: Convert categorical predictors (like Gender and Age_group) and the final target variable (No Show) into a numerical/dummy format suitable for modeling.

Walkthrough of Key Steps & Visuals

1. Initial Data Inspection using base_data.shape and base_data.info() confirmed the dataset contains 110,527 entries with 14 columns. Most data types were int64 and object, necessitating conversion for the date fields.
2. Data Cleaning via base_data.describe() and data filtering allowed for the identification and subsequent removal of a clear outlier: a minimum Age value of -1.
3. Feature Engineering involved calculating the day of the week for both the Scheduled Day (sch_weekday) and Appointment Day (app_weekday). The results showed appointments were overwhelmingly scheduled and held on weekdays (0-4), with very few on Saturday (5) and none on Sunday (6).
4. Data Grouping was performed by creating Age_group bins (e.g., [1-20], [21-40]) to transform the original Age column into distinct age brackets, facilitating better categorical analysis.
5. Target Variable Distribution (KPI) analysis, using No Show value counts and a bar plot, highlighted a data imbalance: 79.81% of patients Showed Up ("No" in original data, 0 in the final encoding) versus 20.19% who Did Not Show Up ("Yes," 1).
6. Bivariate Analysis involved using Count plots (e.g., comparing Hypertension vs. No Show by Gender) to provide visual evidence of how specific demographic and health factors correlate with missing the appointment.
7. Correlation Analysis employed a Heatmap of all dummy variables to confirm the strength and direction of relationships between all features and the target variable, thereby helping to prioritise features for model building.


📈 Business Impact & Insights

The EDA has provided initial insights into the factors that could drive appointment attendance:
- Gender: Female patients are generally more numerous across the entire dataset, which is reflected in both the "Showed Up" and "No Show" groups.
- Chronic Conditions: There is a visible, although preliminary, indication that patients with chronic conditions like Hypertension and Diabetes might have slightly higher attendance rates, potentially due to the seriousness of their health issue.
- Age Group: Younger patients ([1-20]) and those in their prime working/parenting years ([21-40], [41-60]) constitute the largest number of no-shows.
- SMS Received: Sending an SMS appears to be associated with a higher number of no-shows in the dataset, suggesting the current SMS strategy might be ineffective or that the message is being sent to patients who are already less likely to attend.
- Correlation (Technical Insight): The correlation matrix confirms that no single variable is strongly correlated with "No Show." This suggests a multi-factor predictive model will be required, focusing on a combination of lower-correlated features.
