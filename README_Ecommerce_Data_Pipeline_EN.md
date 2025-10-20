# 🛒 E-commerce Data Pipeline

![Python](https://img.shields.io/badge/Python-3.9-blue)
![AWS](https://img.shields.io/badge/AWS-S3-orange)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-RDS-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-yellow)

## 📘 Project Overview

The **E-commerce Data Pipeline** is an end-to-end **ETL (Extract, Transform, Load)** project built by **MOSSOKE Christian – Data Engineer**.
It automates the process of collecting, cleaning, transforming, and storing e-commerce data from a local SQLite database into **AWS S3**, and finally into **Amazon RDS (PostgreSQL)** for further analytics and visualization.

This project demonstrates a full-stack **data-engineering workflow** from on-premise data to a cloud-based data warehouse.

## 🧠 Objectives
- ✅ Automate the ingestion of raw e-commerce data
- ✅ Apply transformation and data-quality checks using **Pandas**
- ✅ Store the cleaned datasets in **AWS S3**
- ✅ Load the transformed data into **Amazon RDS (PostgreSQL)**
- ✅ Generate insights and visualizations for business analysis

## 🏗️ Architecture

### 🔹 Minimal (GitHub-style) Diagram

```
+-------------+        +-------------+        +-------------+        +-------------+
|   SQLite    |  --->  |   Pandas    |  --->  |   AWS S3    |  --->  |   RDS (PostgreSQL) |
| (Raw Data)  |        |(Transform)  |        |(Storage)    |        |(Data Warehouse)   |
+-------------+        +-------------+        +-------------+        +-------------+
```

## ⚙️ Tech Stack

| Layer | Tools / Technologies |
|-------|----------------------|
| Data Source | SQLite |
| Data Processing | Python 3.9, Pandas |
| Cloud Storage | AWS S3 |
| Data Warehouse | Amazon RDS (PostgreSQL) |
| Visualization | Matplotlib |
| Others | boto3, sqlalchemy, psycopg2, os |

## 🔄 ETL Pipeline Steps

### 1️⃣ **Extract**
- Connect to a local **SQLite** database (`boutique_sql_cours.db`).
- Retrieve all tables dynamically.
- Export each table as a CSV into `raw/exported_csv/`.

### 2️⃣ **Transform**
- Load the CSVs with **pandas**.
- Remove duplicates and invalid records.
- Convert date fields to proper `datetime` objects.
- Build dimension tables: `dim_clients`, `dim_products`, `dim_time`.

### 3️⃣ **Load**
- Upload the cleaned CSVs to **AWS S3** (`christian-pipeline-bucket`).
- Connect to **Amazon RDS (PostgreSQL)**.
- Push the transformed data into RDS tables for analytics.

## 📊 Insights & Results

After loading the data into RDS, exploratory analysis reveals key business metrics:

- **Top 5 Products by Revenue**
- **Monthly Sales Trend**
- **Top Cities by Number of Orders**

Example insight (using `matplotlib`):

```python
# Example: Monthly revenue trend
monthly_sales = df_commandes.groupby(df_commandes['date_commande'].dt.to_period('M'))['montant_total'].sum()
monthly_sales.plot(kind='line', title='Monthly Revenue Trend')
```

💡 **Results** show:
- Continuous revenue growth over the last 6 months.
- Top categories include “Electronics” and “Home Appliances”.
- Paris and Lyon represent 40 % of total sales volume.

## 🚀 How to Run the Project

### 🔧 Requirements
- Python 3.9+
- AWS CLI configured with access credentials
- PostgreSQL RDS instance

### 📦 Installation

```bash
git clone https://github.com/christian-mossoke/ecommerce-data-pipeline.git
cd ecommerce-data-pipeline
pip install -r requirements.txt
```

### ▶️ Execution

```bash
python data_engineering_project1.ipynb
```

*(Or run all cells in Jupyter Notebook)*

## 🧩 Folder Structure

```
📦 ecommerce-data-pipeline
├── datasets/
│   └── boutique_sql_cours.db
├── raw/
│   └── exported_csv/
├── notebooks/
│   └── data_engineering_project1.ipynb
├── visuals/
│   ├── pipeline_diagram.png
│   └── insights_charts.png
└── README.md
```

## 👨‍💻 Author

**MOSSOKE Christian**
_Data Engineer_
📧 **christian.mossoke.pro@gmail.com**

## 🌟 Key Takeaways
- Building a **data pipeline** from scratch strengthens your ability to manage end-to-end workflows.
- Integration of **cloud technologies** (AWS S3 & RDS) demonstrates scalability and automation.
- Including analytics and visualization closes the loop between **data engineering** and **data analysis**.
