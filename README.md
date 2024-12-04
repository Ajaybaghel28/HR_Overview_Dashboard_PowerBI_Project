# HR_Overview_Dashboard_PowerBI_Project

## Project Overview
The HR Overview Dashboard was created in Power BI to analyze key HR metrics, including employee demographics, retention rates, hiring and termination trends, and departmental statistics. This dashboard provides a comprehensive view of employee distribution across various demographics and departments, enabling data-driven decisions in HR management.

## Exploratory Data Analysis (EDA)
Before creating the dashboard, an Exploratory Data Analysis (EDA) was conducted on the HR dataset to gain preliminary insights, detect anomalies, and identify data patterns. Key steps and insights from EDA include:

### 1. Data Cleaning:
  - Handling Missing Values: Addressed missing values in fields such as termination date, birthdate, and department.
  - Outliers: Reviewed and examined outliers in age, salary, and tenure to ensure data accuracy.
  - Standardization: Unified date formats and standardized categorical values.

### 2. Data Transformation:
  - Age Calculation: Calculated age using the birthdate field and categorized it into age groups.
  - Tenure Calculation: Calculated employee tenure based on hire_date and termination date (if applicable).
  - Categorical Binning: Grouped income levels, tenure, and age into predefined categories for segmentation.

### 3. Univariate Analysis:
  - Analyzed gender distribution, department sizes, and identified the most populous departments.

### 4. Bivariate Analysis:
  - Investigated retention rates by department and age, identifying areas with higher turnover.

### 5. Multivariate Analysis:
- Explored location, age, and gender, and analyzed hiring and termination patterns for seasonal trends.

### 6. Initial Insights for Dashboard Design:
  - Identified key metrics, including demographics, departmental distribution, retention, and turnover rates.

## Key Components and Metrics
The dashboard highlights insights based on EDA findings, with the following key metrics and visualizations:

### 1. Employee Demographics Analysis
  - Gender Distribution: Visualizes the count of employees by gender (Male, Female, Non-Conforming).
  - Age and Retention Rate by Department: Displays average age and retention rate for each department.

### 2. Departmental Analysis
  - Number of Employees by Department: Shows employee counts across various departments.
  - Top 10 Cities by Employee Count: Highlights cities with the highest number of employees on a map.

### 3. Hiring and Termination Trends
  - Monthly Hiring and Termination Trends: Displays monthly hiring and termination rates over time.

### 5. Location Analysis
  - Total Employees by Location: Splits employee count between headquarters and remote locations.

## DAX Used
Here are some DAX queries used for advanced analysis in the dashboard:

### 1. Employee Count by Gender and Race:
 EmployeeDemographics = 
 SUMMARIZE(
    'HRData',
    'HRData'[gender],
    'HRData'[race],
    "EmployeeCount", COUNT('HRData'[id])
)

### 2. Retention Rate by Department:
 RetentionRateByDepartment = 
 DIVIDE(
    COUNTROWS(FILTER('HRData', ISBLANK('HRData'[termdate]))),
    COUNTROWS('HRData')
)

### 3. Average Age by Department:
 AverageAgeByDepartment = 
 CALCULATE(
    AVERAGE(DATEDIFF('HRData'[birthdate], TODAY(), YEAR)),
    'HRData'[department]
)

### 4. Monthly Hiring Trend by Department:
 MonthlyHiringTrend = 
 CALCULATE(
    COUNT('HRData'[id]),
    'HRData'[hire_date].[Month],
    'HRData'[department]
)

## Visualizations Used
  - Bar Charts: For gender distribution and employee count by department.
  - Line Charts: For visualizing monthly hiring and termination trends.
  - Map: Shows top cities by employee count.

This project highlights the importance of tracking and visualizing HR metrics for better workforce management and strategic planning. The combination of EDA and Power BI enables an effective approach to HR analytics, providing valuable insights to support data-driven decisions.

