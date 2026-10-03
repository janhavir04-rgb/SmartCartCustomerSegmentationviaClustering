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

## 📊 Dataset

The dataset contains **2,240 customer records and 22 original attributes**.

### 1. Customer Demographics

| Feature          | Description                                    |
| ---------------- | ---------------------------------------------- |
| `ID`             | Unique customer identifier                     |
| `Year_Birth`     | Year of birth of the customer                  |
| `Education`      | Highest education level achieved               |
| `Marital_Status` | Customer's marital status                      |
| `Income`         | Yearly household income                        |
| `Kidhome`        | Number of small children in household          |
| `Teenhome`       | Number of teenagers in household               |
| `Dt_Customer`    | Date when the customer enrolled with SmartCart |

### 2. Purchase Behaviour — Amount Spent

| Feature            | Description                    |
| ------------------ | ------------------------------ |
| `MntWines`         | Amount spent on wine products  |
| `MntFruits`        | Amount spent on fruits         |
| `MntMeatProducts`  | Amount spent on meat products  |
| `MntFishProducts`  | Amount spent on fish products  |
| `MntSweetProducts` | Amount spent on sweet products |
| `MntGoldProds`     | Amount spent on gold products  |

### 3. Purchase Behaviour — Frequency

| Feature               | Description                        |
| --------------------- | ---------------------------------- |
| `NumDealsPurchases`   | Purchases made using discounts     |
| `NumWebPurchases`     | Purchases made through the website |
| `NumCatalogPurchases` | Purchases made through the catalog |
| `NumStorePurchases`   | Purchases made in physical stores  |
| `NumWebVisitsMonth`   | Number of website visits per month |

### 4. Customer Feedback & Response

| Feature    | Description                                           |
| ---------- | ----------------------------------------------------- |
| `Recency`  | Number of days since the customer's last purchase     |
| `Complain` | Whether the customer complained in the last two years |
| `Response` | Customer response indicator                           |

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

## 🧹 Data Preprocessing

### Missing Values

Missing values in the `Income` feature are handled using the **median income**.

```python
df["Income"] = df["Income"].fillna(df["Income"].median())
```

### Feature Engineering

Several new features are created to better represent customer behaviour:

* **Age**
* **Customer Tenure**
* **Total Spending**
* **Total Children**

### Age

```python
df["Age"] = 2026 - df["Year_Birth"]
```

### Customer Tenure

The customer enrollment date is converted into a date format, and the number of days since the reference date is calculated.

```python
df["Customer_Tenure_Days"] = (
    reference_date - df["Dt_Customer"]
).dt.days
```

### Total Spending

Total spending is calculated by combining spending across the six product categories.

```python
df["Total_Spending"] = (
    df["MntWines"] +
    df["MntFruits"] +
    df["MntMeatProducts"] +
    df["MntFishProducts"] +
    df["MntSweetProducts"] +
    df["MntGoldProds"]
)
```

### Total Children

```python
df["Total_Children"] = df["Kidhome"] + df["Teenhome"]
```

---

## 🔤 Categorical Data Processing

The `Education` feature is grouped into broader categories:

* Basic / 2n Cycle → Undergraduate
* Graduation → Graduate
* Master / PhD → Postgraduate

The `Marital_Status` feature is transformed into:

* **Partner**
* **Alone**

These categorical features are then converted into numerical representations using **One-Hot Encoding**.

---

## 🚨 Outlier Handling

Potential outliers are investigated using visualizations and then filtered based on:

* Age
* Income

The implemented preprocessing removes records where:

```text
Age >= 90
Income >= 600,000
```

This helps reduce the effect of extreme values on clustering.

---

## 📉 Feature Scaling

The processed dataset is standardized using `StandardScaler`.

```python
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

Scaling is important because customer features have different numerical ranges.

---

## 📊 Principal Component Analysis (PCA)

**PCA** is applied to reduce the dimensionality of the scaled dataset.

The project uses:

```python
PCA(n_components=3)
```

The resulting three principal components are used to visualize the customer data in a 3D space and as input for the clustering experiments.

---

## 🔍 Finding the Number of Clusters

Two approaches are used to evaluate the number of clusters:

### 1. Elbow Method

The **Within-Cluster Sum of Squares (WCSS)** is calculated for different values of `K`.

The `KneeLocator` technique is used to identify the elbow point.

### 2. Silhouette Score

The **Silhouette Score** is calculated for cluster values from 2 to 10.

This provides another measure for evaluating the quality of the generated clusters.

---

## 🤖 Clustering Algorithms

### K-Means Clustering

The project applies K-Means clustering with **4 clusters**.

```python
kmeans = KMeans(
    n_clusters=4,
    random_state=42
)

labels_kmeans = kmeans.fit_predict(X_pca)
```

### Agglomerative Clustering

Hierarchical Agglomerative Clustering is also implemented with **4 clusters** using Ward linkage.

```python
agg_clf = AgglomerativeClustering(
    n_clusters=4,
    linkage="ward"
)

labels_agg = agg_clf.fit_predict(X_pca)
```

The resulting clusters are visualized using 3D PCA plots.

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

A cluster summary is generated using:

```python
cluster_summary = X.groupby("cluster").mean()
```

A scatter plot is also used to visualize the relationship between:

* **Income**
* **Total Spending**
* **Customer Cluster**

This helps identify differences in customer behaviour between the discovered groups.

---

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
└── requirements.txt
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
