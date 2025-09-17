# Loan Default Risk Prediction 

This notebook develops a machine learning workflow to predict the likelihood of loan defaults using borrower demographic, financial, and credit data. The model can help financial institutions assess applicant risk, minimize credit losses, and improve lending strategies.

---

### Table of Contents
1.  Import Libraries
2.  Load the Dataset
3.  Exploratory Data Analysis (EDA)
4.  Preprocessing
5.  Principal Component Analysis (PCA)
6.  Model Training and Evaluation

---

### Notebook
[Open Jupyter Notebook](./09142025_Loan_Default_Prediction_Model_Build_Pipeline_DA.ipynb)

---

### Dataset
The dataset has been taken from [Coursera's Loan Default Prediction Challenge deposited in Kaggle](https://www.kaggle.com/datasets/nikhil1e9/loan-default). The dataset contains **255,347** records with borrower demographic, financial, and credit history as features. All columns names and descriptions are outlined below:
- `LoanID` - A unique identifier for each loan
- `Age` - The age of the borrower
- `Income` - The annual income of the borrower
- `LoanAmount` - The amount of money being borrowed
- `CreditScore` - The credit score of the borrower
- `MonthsEmployed` - The number of months the borrower has been employed
- `NumCreditLines` - The number of credit lines the borrower has open
- `InterestRate` - The interest rate for the loan
- `LoanTerm` - The term length of the loan in months
- `DTIRatio` - The Debt-to-Income ratio
- `Education` - The highest level of education attained by the borrower
- `EmploymentType` - The type of employment status of the borrower
- `MaritalStatus` - The marital status of the borrower
- `HasMortgage` - Whether the borrower has a mortgage
- `HasDependents` - Whether the borrower has dependents
- `LoanPurpose` - The purpose of the loan
- `HasCoSigner` - Whether the loan has a co-signer
- `Default` - Indicates whether the loan defaulted or not

---

### Key Results
- **Models Tested**: Logistic Regression, Random Forest, and hybrid variations with PCA.
- **Best Performing Model**: Voting Classifier.
- **Evaluation Metrics (Test Set)**:
  - Accuracy: **70%**
  - Precision (default = 1): **0.23**
  - Recall (default = 1): **0.68**
  - F1-score (default = 1): **0.35**
  - ROC-AUC: **~0.76**
- **Insights**:
  - The model favors **recall** — it identifies more actual defaulters, even at the cost of false positives. This is valuable in lending contexts, where catching risky borrowers is more critical than approving every safe one.
  - **Top predictors** of default include:
    - Credit Score (lower strongly linked to default)
    - Debt-to-Income Ratio (higher ratio = higher risk)
    - Loan Amount & Interest Rate (larger, costlier loans are riskier)
  - PCA retained ~95% of data variance with *16 components*, helping reduce dimensionality without major information loss.

---

### Conclusion

This project demonstrates how machine learning can support **credit risk management** by identifying borrowers with a high likelihood of default. The optimized Random Forest model achieves strong recall, making it well-suited for early risk detection. Financial institutions could apply such models to **screen applications, refine risk-based pricing, and reduce portfolio losses**, ultimately improving lending strategies.

