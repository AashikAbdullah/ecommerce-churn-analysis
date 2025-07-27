# 📁 E-commerce Customer Churn Analysis (with RFM + ML)

This project performs **customer churn analysis** using online retail transaction data. It combines **data cleaning**, **RFM (Recency, Frequency, Monetary) feature engineering**, **churn labeling**, visual analysis, and **predictive modeling** to identify customers at risk of churning.

---

## 🎯 Objective

- Clean and preprocess raw e-commerce transaction data.
- Perform RFM-based feature engineering at the customer level.
- Label customers as Churned or Active based on behavior.
- Visualize patterns in customer segments.
- Train machine learning models to predict churn status.
- Select a final model based on F1 Score and interpretability.

---

## 📦 Dataset Overview

- **Source:** [Kaggle - E-commerce Data](https://www.kaggle.com/datasets/carrie1/ecommerce-data)
- **Time Period:** December 2010 to December 2011
- **Region:** UK-based online retailer
- **Original Records:** 541,909 transactions
- **Final Processed Customers:** 4,197 (after cleaning, aggregation & filtering)

> ⚠️ **Note**: The dataset is over 25MB and cannot be uploaded directly to GitHub.  
> Please download it from [Kaggle here](https://www.kaggle.com/datasets/carrie1/ecommerce-data) to reproduce the project.

---

## ⚙️ Process Summary

### ✅ 1. Data Cleaning
- Dropped rows with missing `CustomerID` or `Description`
- Removed duplicates
- Filtered negative `Quantity` and `UnitPrice` values
- Converted:
  - `InvoiceDate` to datetime
  - `CustomerID` to string for grouping

### ✅ 2. Initial Feature Engineering
- Created `Sales = Quantity × UnitPrice`

### ✅ 3. Exploratory Data Analysis (EDA)
- Top-selling countries and customers
- Monthly trends
- Removed outliers using IQR method from `Quantity` and `UnitPrice`

### ✅ 4. RFM Feature Engineering
Grouped by `CustomerID` to compute:
- **Recency**: Days since last transaction from reference date
- **Frequency**: Number of unique invoices
- **Monetary**: Total spend
- **TotalQuantity**
- **AvgOrderValue = Monetary / Frequency**

### ✅ 5. Churn Labeling
- Reference date = Last transaction date + 1 day
- Customers with no purchase in the last 6 months were labeled as `Churned`
- Others were labeled as `Active`

### ✅ 6. Churn Visual Analysis
- Distribution of RFM features for Churned vs Active
- Count plots for churn status
- Churn by customer segment (Low, Mid, High spender)

### ✅ 7. Predictive Modeling
- Models Built:
  - Logistic Regression (All + Selected Features)
  - Decision Tree
  - Random Forest
- Feature selection based on importance scores
- Evaluation using Accuracy, Precision, Recall, F1 Score
- Confusion matrices plotted

---

## ✅ Final Model Selected: Logistic Regression (with Selected Features)

| Model                     | Accuracy | Precision | Recall | F1 Score |
|--------------------------|----------|-----------|--------|----------|
| Logistic (Selected)      | 0.9988   | 0.9964    | 1.0000 | 0.9982   |
| Decision Tree (Selected) | 1.0000   | 1.0000    | 1.0000 | 1.0000   |
| Random Forest (Selected) | 1.0000   | 1.0000    | 1.0000 | 1.0000   |

🟢 Logistic Regression was selected because:
- It provides a strong **F1 Score (0.9982)** and generalizes well
- It is **simpler and more interpretable** than tree-based models
- Tree-based models showed perfect scores, which may indicate **overfitting** on small and clean data

---

## 💾 Exported Cleaned Dataset

The final processed customer dataset (4197 rows) was saved before model training.

## 🧠 Tech Stack

- Python
- Libraries: Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn
- Jupyter Notebook

---

## 📌 Conclusion

This project offers a data-driven approach to identify customer churn using RFM metrics and classification models.  
It empowers businesses to take proactive actions toward customer retention by:

- **Profiling churned customers**
- **Understanding behavior trends**
- **Building a predictive system to flag future churn**

---

## 📂 Author

**Aashik Abdullah**  
🔗 [LinkedIn](https://www.linkedin.com/in/aashikabdullah)  

