Healthcare Risk Analysis System
Overview
This project is a Healthcare Risk Analysis System built using Python, Pandas, NumPy, Matplotlib, and Seaborn.
The system generates a synthetic healthcare dataset for 10,000 patients and performs:
Data preprocessing
Risk classification
Statistical analysis
Correlation analysis
Data visualization
The project helps identify patient health risk levels based on:
Blood Pressure
Sugar Level
Cholesterol
Technologies Used
Python
NumPy
Pandas
Matplotlib
Seaborn
Project Features
Generate healthcare dataset
Analyze patient health metrics
Handle missing values
Categorize patient risk levels
Create age groups
Perform correlation analysis
Generate visualizations
Compare gender-based health statistics
Dataset Description
The dataset contains the following columns:
Column Name
Description
Patient_ID
Unique patient ID
Age
Patient age
Gender
Male/Female
Blood_Pressure
Blood pressure level
Sugar_Level
Blood sugar level
Cholesterol
Cholesterol level
Heart_Rate
Heart rate
Installation
Install required libraries using pip:
Bash
pip install numpy pandas matplotlib seaborn
Project Workflow
1. Import Libraries
Python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
2. Generate Dataset
Random healthcare data is generated using NumPy.
Python
np.random.seed(42)

n = 10000
3. Create DataFrame
Python
df = pd.DataFrame(data)
4. Display Dataset
First 5 Rows
Python
print(df.head())
Dataset Information
Python
print(df.info())
Missing Values
Python
print(df.isnull().sum())
5. Handle Missing Values
Missing numerical values are replaced using column means.
Python
df.fillna(df.mean(numeric_only=True), inplace=True)
6. Risk Classification
Patients are categorized into:
High Risk
Medium Risk
Low Risk
based on:
Blood Pressure
Sugar Level
Cholesterol
Risk Rules
Condition
Risk Level
BP > 140 OR Sugar > 160 OR Cholesterol > 240
High
BP > 120 OR Sugar > 140
Medium
Otherwise
Low
Risk Classification Function
Python
def risk_level(row):
    try:
        if (row["Blood_Pressure"] > 140 or
            row["Sugar_Level"] > 160 or
            row["Cholesterol"] > 240):
            return "High"

        elif (row["Blood_Pressure"] > 120 or
              row["Sugar_Level"] > 140):
            return "Medium"

        else:
            return "Low"

    except:
        return "Unknown"
7. Add Risk Column
Python
df["Risk"] = df.apply(risk_level, axis=1)
8. Statistical Analysis
Descriptive Statistics
Python
print(df.describe())
The analysis includes:
Mean
Standard deviation
Minimum values
Maximum values
Quartiles
9. Age Group Categorization
Patients are divided into age categories:
Age Range
Category
20–40
Young
40–60
Middle
60–80
Old
Python
df["Age_Group"] = pd.cut(
    df["Age"],
    bins=[20,40,60,80],
    labels=["Young","Middle","Old"]
)
10. Correlation Analysis
The project calculates correlations between:
Age
Blood Pressure
Sugar Level
Cholesterol
Heart Rate
Python
df.corr(numeric_only=True)
11. Gender-wise Blood Pressure Analysis
Python
df.groupby("Gender")["Blood_Pressure"].mean()
Example Output:
Gender
Average Blood Pressure
Female
129.39
Male
129.93
Data Visualizations
1. Blood Pressure Distribution
Python
df["Blood_Pressure"].hist()
plt.show()
2. Risk Category Distribution
Python
df["Risk"].value_counts().plot(kind='bar')
plt.show()
3. Age vs Blood Pressure
Python
plt.scatter(df["Age"], df["Blood_Pressure"])
plt.show()
4. Correlation Heatmap
Python
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True
)

plt.show()
Sample Insights
High blood pressure increases health risk.
High sugar levels indicate possible diabetic conditions.
Cholesterol contributes significantly to patient risk.
Correlation between medical variables is relatively low in this synthetic dataset.
Risk classification helps identify vulnerable patients quickly.
Project Outputs
The project generates:
Patient healthcare dataset
Risk classifications
Statistical summaries
Correlation matrix
Health visualizations
How to Run
Step 1: Save the File
Save the Python script as:
Bash
healthcare_risk_analysis.py
Step 2: Run the Program
Bash
python healthcare_risk_analysis.py
Future Enhancements
Add real healthcare datasets
Build disease prediction models
Use machine learning classification algorithms
Create dashboard using Plotly or Streamlit
Add patient report generation
Deploy as a web application
Example Output
Plain text
Patient Risk Categories:
High Risk
Medium Risk
Low Risk <img width="560" height="413" alt="screen shot 1" src="https://github.com/user-attachments/assets/706d4b23-7295-4cac-a451-9f1d018c5358" />
<img width="560" height="474" alt="screen shot 2" src="https://github.com/user-attachments/assets/75bc3b0d-654c-4e8b-acd1-52da3b7526c1" />
<img width="552" height="413" alt="screen shot 3" src="https://github.com/user-attachments/assets/64c4a65f-81c8-445d-ac85-8feec71e6c01" />
<img width="607" height="510" alt="screen shot 4" src="https://github.com/user-attachments/assets/f3b36e77-31f7-470e-89e4-18844092c24c" />



