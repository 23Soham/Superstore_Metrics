

# 🏪 **Superstore Metrics – AWS Data Pipeline**  
🚀 **Transforming raw data into actionable business insights using AWS Glue, S3, Athena & QuickSight**  

<p align="center">
  <img width="1016" img src="/Users/sohamshah/Documents/GitHub/Superstore_Metrics/Pipeline.jpg" alt="Superstore Data Pipeline Workflow" width="700">
</p>

---

## **📌 Project Overview**  
This project is an **end-to-end data pipeline** that processes and analyzes **Superstore sales data** using AWS services. The pipeline ensures **automated data ingestion, transformation, querying, and visualization** to extract key business insights.  

✅ **Stored structured data in AWS S3** with partitioning for optimized queries.  
✅ **Used AWS Glue Crawlers** to automate schema discovery and metadata management.  
✅ **Queried partitioned data using AWS Athena** for performance-efficient analysis.  
✅ **Performed exploratory data analysis (EDA) with `ydata-profiling`** to detect missing values & patterns.  
✅ **Built an AWS QuickSight dashboard** to visualize key metrics like **sales trends, profit distribution, and top customers**.  
✅ **Cross-verified calculations using Microsoft Excel** to ensure accuracy and validation.  

---

## **⚙️ Tech Stack Used**  
- 🛢️ **AWS S3** – Cloud storage for structured data  
- 🔄 **AWS Glue** – ETL processing & schema discovery  
- 🔍 **AWS Athena** – Querying partitioned data  
- 📊 **AWS QuickSight** – Business intelligence & dashboarding  
- 📈 **ydata-profiling** – Automated EDA reports  
- 📑 **Microsoft Excel** – Data validation & cross-checking  

---

## **📂 Project Workflow**
This pipeline **automates the transformation of raw data into business insights** through a well-defined sequence of steps.

### **1️⃣ Data Ingestion: Storing Raw Data in S3**  
The **Superstore dataset** was sourced from **[Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)** and filtered to include data from **2014 to 2017**.  

🔹 **Created an AWS S3 Bucket (`shahdb`)** to store the structured dataset.  
🔹 **Partitioned data by `snapshot_year`** for optimized querying in Athena.  
🔹 The folder structure follows:  
   ```
   S3://shahdb/orders/snapshot_year=2014/2014_data.csv
   S3://shahdb/orders/snapshot_year=2015/2015_data.csv
   S3://shahdb/orders/snapshot_year=2016/2016_data.csv
   S3://shahdb/orders/snapshot_year=2017/2017_data.csv
   ```
🔹 **Why Partitioning?**  
   - Reduces query scan time by **only scanning relevant partitions**.  
   - Saves **AWS Athena querying costs**.  
   - Improves **data retrieval speed**.

---

## **2️⃣ Schema Discovery & Cataloging with AWS Glue**  
To manage and structure the data, I leveraged **AWS Glue Crawlers**, which **automatically detect schema changes and update metadata** in the AWS Glue Data Catalog.

🔹 Created an **AWS Glue Database (`db_store`)** to store metadata.  
🔹 Configured a **Glue Crawler (`orders_project`)** to scan S3 and detect:  
   ✅ **Column names & data types**  
   ✅ **Partition keys (`snapshot_year`)**  
   ✅ **Automatic updates when new data is added**  

📌 **Why AWS Glue Crawlers?**  
✔ Eliminates manual schema creation  
✔ Automatically detects new data partitions  
✔ Stores structured metadata in the AWS Glue Data Catalog  

---

## **3️⃣ Data Profiling & Exploratory Data Analysis (EDA)**
Before querying, I used **ydata-profiling** to **automatically generate EDA reports** and understand the dataset better.  

🔹 **Key Insights Identified:**  
   ✅ **Missing values** in certain attributes  
   ✅ **Correlation between sales, profit, and discount**  
   ✅ **Outlier detection for high-profit transactions**  
   ✅ **Category-wise sales contribution**  

📌 **Why ydata-profiling?**  
✔ Saves hours of manual EDA  
✔ Generates **statistical reports & visualizations**  
✔ Helps in **feature selection & anomaly detection**  

---

## **4️⃣ Querying Data with AWS Athena**  
With structured metadata in the AWS Glue Data Catalog, I used **AWS Athena** to query partitioned data efficiently.

🔹 **Example Athena Query:**  
```sql
SELECT snapshot_year, SUM(sales) AS total_sales, SUM(profit) AS total_profit
FROM db_store.orders
GROUP BY snapshot_year
ORDER BY snapshot_year;
```
🔹 **Optimized query performance** by using **partition pruning** (`snapshot_year`).  

📌 **Why AWS Athena?**  
✔ Serverless SQL querying with no infrastructure to manage  
✔ Works seamlessly with AWS Glue & S3  
✔ Cost-effective (pay-per-query pricing)  

---

## **5️⃣ Data Validation using Microsoft Excel**  
After running SQL queries in Athena, I **cross-verified key metrics using Excel**.  

🔹 **Used Pivot Tables** to check:  
   ✅ Sales and Profit calculations  
   ✅ Customer segmentation accuracy  
   ✅ Category-wise product contribution  
🔹 **Ensured no discrepancies** before visualizing the data in QuickSight.  

📌 **Why Excel?**  
✔ Quick validation of query outputs  
✔ Helps catch unexpected inconsistencies  
✔ Useful for final checks before visualization  

---

## **6️⃣ Data Visualization in AWS QuickSight**  
To showcase key insights, I designed a **fully interactive AWS QuickSight dashboard** covering:  

✅ **Yearly Sales & Profit Trends**  
✅ **Top-Selling Categories & Customer Segments**  
✅ **Geographical Profit & Sales Analysis**  
✅ **Best Performing Ship Modes**  

<p align="center">
  <img src="Superstore_Dashboard.png" alt="Superstore Metrics Dashboard" width="700">
</p>

📌 **Why AWS QuickSight?**  
✔ Native AWS integration with **Athena & Glue**  
✔ Interactive & scalable for **big data visualization**  
✔ Ideal for **business intelligence & stakeholder reporting**  

---

## **🎯 Final Thoughts & Key Learnings**  
🔹 **Partitioning improves query performance and reduces Athena costs**.  
🔹 **AWS Glue Crawlers automate schema updates**, making ETL seamless.  
🔹 **ydata-profiling accelerates EDA**, simplifying feature selection.  
🔹 **Excel remains an underappreciated tool** for data validation.  
🔹 **Building a serverless AWS data pipeline is scalable, cost-effective, and efficient!**  

---

## **📌 Want to Explore the Full Project?**  
🔗 **Check out the complete GitHub repository:**  
👉 [Superstore Metrics GitHub Repository](https://github.com/23Soham/Superstore_Metrics)  

👀 **Let’s connect!** How do you optimize **ETL pipelines, data profiling, and cloud analytics?** Would love to hear your thoughts! 🚀  

#AWS #DataEngineering #ETL #AWSGlue #Athena #QuickSight #Excel #CloudComputing #BigData #BusinessIntelligence #ydataProfiling #DataPipeline #MachineLearning #Analytics #DataScience #DataVisualization  

---
