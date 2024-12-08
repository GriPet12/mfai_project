<!--
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
-->
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

## **Model Details**

### **Architecture of the Neural Network**

The neural network implemented in this project is a **fully connected feedforward neural network**, designed for binary classification. Its main goal is to predict whether a loan application will be approved (`loan_status = 1`) or denied (`loan_status = 0`). Below is a detailed breakdown of the model's structure:  

### Model constructor
Input Layer, Hidden Layer, Output Layer, Learning rate(default = 0.1), Number of epochs(default = 5002)

#### **1. Input Layer**
- **Size:** The input layer accepts a vector of size equal to the number of features in the dataset (after preprocessing).  
- **Features:** This includes scaled numeric features (e.g., `person_income`, `loan_amnt`) and encoded categorical features (e.g., `person_home_ownership`, `loan_intent`).  

#### **2. Hidden Layer**
- **Number Of Layers With Neurons:** 2 layers.
- **Activation Function:** **ReLU (Rectified Linear Unit)**, defined as:<br>
  <div align="center">$$ReLU(z) = \max(0, z)$$</div><br>
  ReLU introduces non-linearity, enabling the model to learn complex patterns in the data.

#### **3. Output Layer**
- **Number of Neurons:** 1 neuron.
- **Activation Function:** **Sigmoid**, defined as:<br>
  <div align="center">$$\sigma(z) = \frac{1}{1 + e^{-z}}$$</div><br>
  Sigmoid squashes the output into a range between 0 and 1, which is interpreted as the probability of loan approval.

---

### **Training Process**

#### **1. Forward Propagation**
- Computes predictions by passing the input data through the layers:<br>
  <div align="center">$$z = X \cdot W + b \quad \text{and} \quad a_1 = ReLU(z)$$</div><br>
  Here, $$W, b$$ represent the weights and biases for the hidden and output layers.  

#### **2. Loss Function**
- The model uses **Binary Cross-Entropy Loss** to measure its performance:<br>
  <div align="center">$$\text{Loss} = -\frac{1}{m} \sum_{i=1}^{m} \left[ y_i \cdot \log(\hat{y}_i) + (1 - y_i) \cdot \log(1 - \hat{y}_i) \right]$$</div><br>
  - $$y_i$$: Actual label (0 or 1).<br>
  - $$\hat{y}_i$$: Predicted probability.<br>
  - $$m$$: Number of samples.<br>

#### **3. Backward Propagation**
- Computes gradients of the loss with respect to weights and biases.  
- Updates weights using **Gradient Descent**:<br>
  <div align="center">$$W = W - \alpha \cdot \frac{\partial \text{Loss}}{\partial W} \quad \text{and} \quad b = b - \alpha \cdot \frac{\partial \text{Loss}}{\partial b}$$</div><br>
  - $$\alpha$$: Learning rate (set to 0.1 in this model).  

#### **4. Iterative Optimization**
- The model runs for 2501 iterations, printing the loss every 100 iterations to monitor training progress.  

---

### **Model Evaluation**

After training, the model's performance is evaluated based on its predictions:  
1. **Thresholding:** The sigmoid output $ \hat{y} $ is converted to binary predictions (0 or 1) based on a threshold of 0.5.  
2. **Metrics:** here the **F1-Score** metric is implemented to calculate prediction efficiency.

---

### **Advantages of This Model**
1. **Interpretability:** A simple architecture allows for easy understanding of the learning process.  
2. **Customizability:** The number of hidden neurons, learning rate, and iterations can be adjusted to optimize performance.  
3. **Scalability:** The neural network can be expanded with more layers or neurons for more complex datasets.  

---

This neural network serves as a solid starting point for predicting loan approvals. With additional refinement and evaluation, it could be adapted for real-world financial applications.
