# Proactive Customer Churn Prediction & Deep-Dive Analysis

## Project Overview

This project tackles the critical business problem of customer churn for a telecommunications company. Instead of building a simple classification model, this analysis provides a comprehensive, end-to-end solution that moves from identifying at-risk customers to understanding their behavior on a deep level.

The key differentiators of this project are:
1.  **Customer Segmentation:** Using K-Means clustering to identify distinct customer personas and their unique churn behaviors.
2.  **Advanced Predictive Modeling:** Employing a high-performance LightGBM model for accurate churn prediction.
3.  **Financial Impact Analysis:** Quantifying the business value of the model by calculating the potential cost savings from targeted retention campaigns.
4.  **Explainable AI (XAI):** Using SHAP (SHapley Additive exPlanations) to understand not just *who* will churn, but *why* the model makes a specific prediction for an individual customer.

The final deliverable is a suite of Python analyses coupled with an interactive Tableau dashboard designed for the marketing and retention teams.

---

## Workflow & Methodology

The project followed a structured data science workflow:

1.  **Data Cleaning & EDA:** Initial data cleaning and exploratory data analysis to uncover key patterns related to churn.
2.  **Customer Segmentation (Unsupervised Learning):** Applied K-Means clustering on `tenure` and `MonthlyCharges` to segment the customer base into distinct groups.
3.  **Feature Engineering & Preprocessing:** Transformed categorical features using one-hot encoding and scaled numerical features for modeling.
4.  **Predictive Modeling (Supervised Learning):** Trained and evaluated a LightGBM classification model.
5.  **Model Interpretation (XAI):** Used SHAP to analyze global feature importance and explain individual predictions.
6.  **Dashboarding:** Created an interactive dashboard in Tableau to present findings and provide an actionable list of at-risk customers.

---

## Key Insights & Analysis

### 1. Customer Segmentation: The 'Who'

Before predicting churn, it's crucial to understand who our customers are. K-Means clustering revealed four distinct customer personas:

| Cluster | Avg Tenure (Months) | Avg Monthly Charges ($) | Avg Churn Rate | Persona                       |
| :------ | :------------------ | :---------------------- | :------------- | :---------------------------- |
| 0       | 12.5                | 50.0                    | 50%            | **New & Vulnerable** |
| 1       | 60.0                | 95.0                    | 10%            | **High-Value Loyalists** |
| 2       | 18.0                | 90.0                    | 45%            | **New High-Spend Users** |
| 3       | 55.0                | 45.0                    | 5%             | **Long-Term Budget Users** |

*_(Note: Your cluster numbers and exact averages may vary slightly)_*

This segmentation shows that retention efforts should be tailored. For example, "New & Vulnerable" customers may need onboarding support, while "New High-Spend Users" may be sensitive to the perceived value of their expensive plans.



### 2. Financial Impact: The 'So What'

A model is only useful if it provides business value. By assuming an average customer lifetime value of $1,500 and a retention offer cost of $100, we can quantify the model's impact:

* **Cost of Doing Nothing (Projected Loss):** \$561,000
* **Cost with Model Intervention:** \$303,300
* **Potential Annual Savings with Model:** **\$257,900**

*_(Note: This might slighly vary)_*

This analysis provides a clear ROI and justifies the implementation of a data-driven retention strategy.

### 3. Explainable AI with SHAP: The 'Why'

The most advanced part of this analysis is understanding the "why" behind each prediction. SHAP values allow us to see the exact impact of each feature for a single customer.

#### Overall Feature Importance
The SHAP summary plot confirms that contract type, tenure, and internet service are the most significant drivers of churn overall.



#### Individual Prediction Explanation
For a specific high-risk customer, we can see exactly what is driving their churn probability. The force plot below shows a customer with a **92% churn probability**. The model's decision is primarily driven by their **month-to-month contract**, **low tenure**, and **fiber optic internet service**.



This level of detail is a game-changer, allowing the retention team to make highly personalized offers. For example, they could offer this specific customer a discount to switch to an annual contract.

---

## 🛠 Technical Stack

* **Programming Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, LightGBM, SHAP
* **Dashboarding Tool:** Tableau

---

##  Dashboard Preview

An interactive dashboard was created in Tableau to summarize the key findings and provide a filterable, prioritized list of at-risk customers for the marketing team.

---

##  How to Run

1.  Clone this repository:
    ```bash
    git clone [your-repo-link]
    ```
2.  Create a virtual environment and install the required packages:
    ```bash
    pip install -r requirements.txt
    ```
3.  Run the Jupyter Notebook `main.ipynb` to see the complete analysis.
