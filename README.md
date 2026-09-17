# 👥 Customer Segmentation using RFM Analysis & K-Means Clustering

A data analytics and machine learning project that segments e-commerce customers based on their purchasing behavior using **RFM Analysis** and **K-Means Clustering**.

## 📌 Project Overview

Customer segmentation helps businesses understand different types of customers and create targeted marketing strategies.

In this project, customer behavior is analyzed using three important RFM metrics:

- **Recency** – How recently a customer made a purchase
- **Frequency** – How often a customer made purchases
- **Monetary** – How much a customer spent

These metrics are transformed, scaled, and used with **K-Means Clustering** to identify meaningful customer segments.

---

## 🎯 Objectives

- Clean and preprocess e-commerce transaction data
- Calculate customer-level RFM metrics
- Apply log transformation to reduce skewness
- Standardize RFM features
- Determine an appropriate number of clusters
- Perform K-Means customer segmentation
- Analyze and visualize customer segments
- Generate a final customer segmentation dataset
- Provide business insights from the identified segments

---

## 📊 Dataset

The project uses the **Online Retail Dataset** from the UCI Machine Learning Repository.

🔗 Dataset Source:  
https://archive.ics.uci.edu/dataset/352/online%2Bretail

The dataset contains transactional information from a UK-based online retail business.

### Main Features

| Feature | Description |
|---|---|
| InvoiceNo | Unique invoice number |
| StockCode | Product code |
| Description | Product description |
| Quantity | Number of products purchased |
| InvoiceDate | Date and time of transaction |
| UnitPrice | Price per unit |
| CustomerID | Unique customer identifier |
| Country | Customer's country |

---

## 🧹 Data Preprocessing

The following preprocessing steps were performed:

- Removed duplicate transactions
- Removed cancelled invoices
- Removed transactions with non-positive quantities
- Removed transactions with non-positive unit prices
- Removed records with missing Customer IDs
- Removed records with missing product descriptions
- Removed non-product/service transaction codes
- Reset the dataset index

After preprocessing, customer-level RFM metrics were calculated.

---

## 📈 RFM Analysis

For each customer, the following metrics were calculated:

### Recency

Number of days since the customer's most recent purchase.

**Lower Recency = More Recent Customer**

### Frequency

Number of purchases/transactions made by the customer.

**Higher Frequency = More Regular Customer**

### Monetary

Total amount spent by the customer.

**Higher Monetary = Higher Customer Value**

---

## 🔄 Log Transformation

RFM values can be highly skewed because a small number of customers may have very high purchase frequency or spending.

Therefore, log transformation was applied to reduce skewness and make the features more suitable for clustering.

The transformed RFM features were then standardized using **StandardScaler**.

After scaling:

- Mean ≈ 0
- Standard deviation ≈ 1

---

## 🤖 Customer Segmentation

**K-Means Clustering** was used to group customers with similar purchasing behavior.

The number of clusters was evaluated using:

- Elbow Method
- Silhouette Score

### Silhouette Scores

| Number of Clusters (K) | Silhouette Score |
|---:|---:|
| 2 | 0.4328 |
| 3 | 0.3365 |
| 4 | 0.3375 |
| 5 | 0.3162 |
| 6 | 0.3124 |
| 7 | 0.3092 |
| 8 | 0.3033 |
| 9 | 0.2811 |
| 10 | 0.2767 |

Based on the clustering analysis and business interpretability, **4 customer segments** were used for the final segmentation.

---

## 👥 Customer Segments

The final segmentation contains **4,338 customers**.

| Segment | Customer Type | Customers | Percentage |
|---:|---|---:|---:|
| 0 | High-Value Customers | 713 | 16.44% |
| 1 | Inactive / Low-Value Customers | 1,622 | 37.39% |
| 2 | Recent Low-Frequency Customers | 837 | 19.29% |
| 3 | Regular / Valuable Customers | 1,166 | 26.88% |

---

## 🔍 Segment Profiles

| Customer Segment | Recency | Frequency | Monetary |
|---|---:|---:|---:|
| High-Value Customers | 12.17 | 13.75 | 8088.02 |
| Inactive / Low-Value Customers | 181.51 | 1.32 | 341.00 |
| Recent Low-Frequency Customers | 17.70 | 2.19 | 557.32 |
| Regular / Valuable Customers | 71.64 | 4.08 | 1801.78 |

### High-Value Customers

These customers purchase frequently, purchased recently, and have high overall spending.

### Inactive / Low-Value Customers

These customers have not purchased recently and have relatively low purchase frequency and spending.

### Recent Low-Frequency Customers

These customers have purchased recently but have relatively low purchase frequency and spending.

### Regular / Valuable Customers

These customers show regular purchasing behavior with moderate-to-high frequency and monetary value.

---

## 📊 Visualizations

The project includes visualizations such as:

- RFM distributions
- Elbow Method for selecting K
- Customer Segment Distribution
- RFM Segment Profile Heatmap
- Customer Segment Percentage Distribution

---

## 📁 Project Structure

```text
Customer-Segmentation/
│
├── data/
│   ├── customer_segments.csv
│   └── segment_summary.csv
│
├── notebooks/
│   └── 01_customer_segmentation.ipynb
│
├── .gitignore
└── README.md
