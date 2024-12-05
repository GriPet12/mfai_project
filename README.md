# **MFAI Project - Loan Approval Prediction**
**The goal for this project is to predict whether an applicant is approved for a loan.**

## [Competition - Loan Approval Prediction](https://www.kaggle.com/competitions/playground-series-s4e10)

## [Train Dataset](https://drive.google.com/file/d/1jk9o22ubUvFh0ywrPje-LUS9N8Vy_0IE/view?usp=drive_link)

## [Test Dataset](https://drive.google.com/file/d/1q41Ro07XX6te2loEXL3pgAWkyMrDaUZs/view?usp=drive_link)

## **Descriptions of Loan Data**

**Descriptions for the column names based on the data provided:**


*   `id`: Unique identifier for each record.

*   `person_age`: Age of the individual, categorized into ranges.

*   `person_income`: Income of the individual, categorized into income ranges.

*   `person_home_ownership`: Homeownership status, which includes categories like 'RENT', 'MORTGAGE', etc.

*   `person_emp_length`: Employment length of the individual, categorized into ranges based on years.

*   `loan_intent`: The purpose of the loan, with categories such as 'EDUCATION', 'MEDICAL', etc.

*   `loan_grade`: The credit grade of the loan, such as 'A', 'B', etc.

*   `loan_amnt`: Loan amount, categorized into ranges.

*   `loan_int_rate`: Loan interest rate, categorized into percentage ranges.

*   `loan_percent_income`: Percentage of the individual’s income that the loan represents, categorized into - ranges.

*   `cb_person_default_on_file`: Whether the person has a history of loan default, with values 'true' or 'false'.

*   `cb_person_cred_hist_length`: Length of the individual’s credit history, categorized into ranges.

*   `loan_status`: with values representing whether the loan status approval( binary values)


The dataset is a about loan applications, including personal, financial, and loan details. 
It's likely used for predicting whether a person will default on a loan, making it a binary classification problem. 
The goal is to figure out which applicants are at higher risk of not paying back their loans based on their age, income, employment, loan purpose, credit history, and other related information.

---

## **Exploratory Data Analysis (EDA)**  
1. **Numeric Columns:** Distributions and boxplots for columns like `person_age`, `person_income`, and `loan_amnt`.  
2. **Categorical Analysis:** Frequency plots and loan default rates based on features such as `loan_intent` and `loan_grade`.  

### Key Visualizations:  
- Histograms and line plots for numeric data to identify trends.  
- Boxplots to detect outliers in numeric features.  
- Bar plots to observe default frequencies for categorical variables.  

---

## **Data Preprocessing**  

1. **Removing Redundant Columns:**  
   The `id` column was dropped as it does not contribute to prediction.  

2. **Handling Missing Values:**  
   - Checked for null and duplicate values.  
   - Addressed missing values through imputation or removal if necessary.  

3. **Encoding Categorical Variables:**  
   - Used `LabelEncoder` to transform categorical columns into numeric formats.  

4. **Scaling Numeric Features:**  
   - Standardized numerical columns using `StandardScaler` for effective model training.  

---