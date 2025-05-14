# 📊 Customer Segmentation & Visualization – Advanced Analysis

Welcome to the **Customer Segmentation & Visualization – Advanced Analysis** project! This repository dives deep into customer behavioral patterns by leveraging rich visualizations and insights derived from advanced EDA techniques. The goal is to identify actionable trends that can help businesses reduce churn and optimize service delivery.

---

## 📁 Dataset Overview

The dataset contains customer information collected from a telecom company. Each row represents a customer with various attributes relating to demographic info, service subscriptions, billing behavior, and churn status.

### 🔑 Key Columns

| Column Name        | Description                                         |
| ------------------ | --------------------------------------------------- |
| `customerID`       | Unique customer identifier                          |
| `gender`           | Gender of the customer                              |
| `SeniorCitizen`    | Indicates if the customer is a senior citizen (0/1) |
| `Partner`          | Whether the customer has a partner                  |
| `Dependents`       | Whether the customer has dependents                 |
| `tenure`           | Number of months the customer has stayed            |
| `PhoneService`     | Whether the customer has phone service              |
| `MultipleLines`    | If the customer has multiple lines                  |
| `InternetService`  | Type of internet service                            |
| `OnlineSecurity`   | Whether the customer has online security            |
| `DeviceProtection` | Device protection status                            |
| `TechSupport`      | Tech support subscription status                    |
| `StreamingTV`      | Streaming TV subscription                           |
| `StreamingMovies`  | Streaming movie subscription                        |
| `Contract`         | Contract type (Month-to-month, One year, Two year)  |
| `PaperlessBilling` | Billing type                                        |
| `PaymentMethod`    | Customer's payment method                           |
| `MonthlyCharges`   | Monthly billing charges                             |
| `TotalCharges`     | Total charges over tenure                           |
| `Churn`            | Customer churn status (Yes/No)                      |
| `tenure_group`     | Categorical group based on tenure duration          |

---

## 🧰 Libraries Used

```python
import plotly.express as px
import plotly.graph_objects as go
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline
sns.set(color_codes=True)

import warnings
warnings.filterwarnings('ignore')
```

---

## 📊 Visualizations

This project uses a combination of `Plotly`, `Matplotlib`, and `Seaborn` to generate impactful insights:

### 1. 📈 Bar Chart – Payment Method vs Total Charges

Visualize total charges aggregated by each payment method to understand which payment types generate the most revenue.

```python
px.bar(df, x='PaymentMethod', y='TotalCharges', color='PaymentMethod', title="Total Charges by Payment Method")
```

---

### 2. 📉 Histogram – Senior Citizen Distribution

Analyze the age group distribution and its influence on service subscription.

```python
plt.hist(df['SeniorCitizen'], bins=2, color='skyblue')
plt.title('Senior Citizen Distribution')
plt.xlabel('Senior Citizen')
plt.ylabel('Count')
```

---

### 3. 📦 Boxplot – Monthly Charges

Understand the spread and outliers in monthly billing.

```python
sns.boxplot(data=df, x='MonthlyCharges', color='lightgreen')
plt.title('Monthly Charges Distribution')
```

---

### 4. 🧮 Count Plot – Churn Analysis

Examine the frequency of churned vs. retained customers.

```python
sns.countplot(data=df, x='Churn', palette='Set2')
plt.title('Customer Churn Count')
```

---

### 5. 🔥 Heatmap – Correlation Matrix

Explore correlation among numerical features.

```python
sns.heatmap(df[['SeniorCitizen', 'tenure', 'MonthlyCharges']].corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
```

---

### 6. 🍩 Donut Chart – Tenure Group Distribution

Display customer distribution across tenure groups using a donut chart with Plotly Express.

```python
fig = px.pie(df, names='tenure_group', title='Tenure Group Distribution', hole=0.4)
fig.show()
```

---

### 7. 📊 Grouped Bar – Tenure Group vs Monthly Charges (Plotly Go)

Visualize average monthly charges by tenure group.

```python
avg_charges = df.groupby('tenure_group')['MonthlyCharges'].mean().reset_index()
fig = go.Figure([go.Bar(x=avg_charges['tenure_group'], y=avg_charges['MonthlyCharges'])])
fig.update_layout(title='Avg Monthly Charges by Tenure Group', xaxis_title='Tenure Group', yaxis_title='Monthly Charges')
fig.show()
```

---

## 🎯 Key Insights

* 📉 **Senior Citizens** tend to churn more often and pay higher charges.
* 📦 **Month-to-month contracts** show the highest churn rate.
* 💳 Customers using **electronic checks** have higher churn compared to those using credit cards or bank transfers.
* 🎯 **Tech support and online security** subscriptions are linked with lower churn rates.

---

## ✅ Project Goals

* Perform advanced segmentation and EDA on telecom customer data.
* Build engaging, interactive, and publication-ready visualizations.
* Identify actionable business insights to **reduce churn** and **improve retention**.












