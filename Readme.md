# 🛒 SmartCart Clustering System

## 📌 Project Overview

**SmartCart Clustering System** is an **unsupervised machine learning project** developed to segment e-commerce customers based on their demographics, purchasing behaviour, website activity, and customer engagement.

The dataset contains **2,240 customer records and 22 attributes**. The project applies data preprocessing, feature engineering, encoding, scaling, dimensionality reduction, and clustering algorithms to discover meaningful customer groups.

The identified customer segments can help an e-commerce business understand differences in customer behaviour and support **personalized marketing, customer engagement, and retention strategies**.

---

## 🎯 Problem Statement

SmartCart is a growing e-commerce platform serving customers across multiple countries. The company has collected extensive customer data containing demographic information, purchase behaviour, website activity, and customer response.

Currently, SmartCart uses generic marketing and engagement strategies for all customers without clearly understanding different customer behaviour patterns. This can result in inefficient marketing, missed opportunities to retain high-value customers, and delayed identification of different customer segments.

To address this problem, SmartCart aims to develop an **intelligent customer segmentation system using unsupervised machine learning**.

The system analyzes customer purchasing behaviour, engagement levels, spending patterns, and loyalty-related indicators to group customers into meaningful clusters.

---

## 🎯 Objectives

* Analyze customer demographic and purchasing data.
* Perform data cleaning and preprocessing.
* Handle missing values and potential outliers.
* Create meaningful features from existing customer attributes.
* Encode categorical variables.
* Scale numerical features for machine learning.
* Apply **Principal Component Analysis (PCA)** for dimensionality reduction.
* Determine a suitable number of customer clusters.
* Apply **K-Means Clustering**.
* Apply **Agglomerative Clustering**.
* Compare and visualize customer segments.
* Analyze income and spending patterns across clusters.
* Generate cluster summaries to understand customer behaviour.

---


## 🔧 Technologies Used

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Scikit-learn** – Machine learning and preprocessing
* **KMeans** – Customer clustering
* **Agglomerative Clustering** – Hierarchical clustering
* **PCA** – Dimensionality reduction
* **Kneed** – Elbow detection

---

## 🔄 Project Workflow

```text
Customer Dataset
       ↓
Data Loading
       ↓
Data Inspection
       ↓
Missing Value Handling
       ↓
Feature Engineering
       ↓
Feature Selection
       ↓
Outlier Removal
       ↓
Categorical Encoding
       ↓
Feature Scaling
       ↓
PCA Dimensionality Reduction
       ↓
Cluster Evaluation
       ↓
K-Means Clustering
       ↓
Agglomerative Clustering
       ↓
Cluster Visualization
       ↓
Cluster Characterization
       ↓
Customer Segmentation
```

---
## 📈 Cluster Analysis

After clustering, the customer groups are analyzed based on their characteristics.

The project examines:

* Customer income
* Total spending
* Purchase behaviour
* Customer characteristics
* Cluster sizes
* Spending patterns

## 💡 Business Applications

The customer segments discovered by the system can potentially support:

* Personalized marketing campaigns
* Customer engagement strategies
* Spending-pattern analysis
* Customer retention activities
* Identification of different customer groups
* More targeted promotional campaigns
* Data-driven customer relationship management

The clustering output provides a data-driven way to understand customer behaviour rather than applying the same strategy to every customer.

---

## 📁 Project Structure

```text
SmartCart-Clustering-System/
│
├── smartcart.ipynb
├── smartcart_customers.csv
├── README.md
```

---

## 📌 Key Highlights

* **2,240 customer records**
* **22 original customer attributes**
* Data cleaning and preprocessing
* Feature engineering
* Outlier handling
* One-Hot Encoding
* Standardization
* PCA-based dimensionality reduction
* Elbow Method
* Silhouette Score
* K-Means Clustering
* Agglomerative Clustering
* 3D cluster visualization
* Customer cluster characterization

---

## 👩‍💻 Project Type

**Machine Learning | Unsupervised Learning | Customer Segmentation | Data Analysis | Clustering**

---

## 📜 License

This project is intended for educational and portfolio purposes.
