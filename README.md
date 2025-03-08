# Superstore_Metrics

🏪 Superstore Metrics – AWS Data Pipeline
🚀 Transforming raw data into powerful business insights using AWS Glue, S3, Athena & QuickSight

📌 Project Overview
This project is an end-to-end data pipeline built using AWS services to process, analyze, and visualize Superstore sales data efficiently. The goal was to:
✅ Ingest structured data into AWS S3 with partitioning for optimized queries.
✅ Use AWS Glue Crawlers to automate schema discovery and create a metadata catalog.
✅ Run SQL queries using AWS Athena on partitioned data for efficient analysis.
✅ Generate a comprehensive EDA report using ydata-profiling for quick insights.
✅ Build an interactive dashboard in AWS QuickSight to visualize key business metrics.
✅ Cross-verify results in Microsoft Excel to ensure data accuracy and integrity.

By combining these tools, I built a fully automated ETL pipeline that transforms raw data into meaningful insights while maintaining scalability and performance.

⚙️ Tech Stack Used
AWS S3 – Cloud storage for raw data
AWS Glue – ETL & schema discovery via Crawlers
AWS Athena – Querying structured data from S3
AWS QuickSight – Business intelligence & dashboarding
ydata-profiling – Automated EDA & statistical summaries
Microsoft Excel – Data validation & cross-checking
📂 Project Workflow
Let’s break down the entire AWS Data Pipeline step by step.

1️⃣ Data Ingestion: Storing Raw Data in S3
🔹 The raw Superstore dataset was sourced from Kaggle.
🔹 Filtered data for only the years 2014-2017 to maintain relevance.
🔹 Created an AWS S3 Bucket (shahdb) to store the dataset.
🔹 Within the bucket, structured the data as:

ruby
Copy
Edit
S3://shahdb/orders/snapshot_year=2014/2014_data.csv
S3://shahdb/orders/snapshot_year=2015/2015_data.csv
S3://shahdb/orders/snapshot_year=2016/2016_data.csv
S3://shahdb/orders/snapshot_year=2017/2017_data.csv
🔹 Partitioning by year ensures optimized querying in Athena.

2️⃣ Schema Discovery & Cataloging with AWS Glue
🔹 Created an AWS Glue Database (db_store) to organize metadata.
🔹 Set up a Glue Crawler (orders_project) to scan the S3 data and create a table schema.
🔹 The crawler automatically identified column names, data types, and partitions.
🔹 This step eliminated the need for manual schema creation and ensured automated updates whenever new data was added.

📌 Why AWS Glue?
✔ Automates schema extraction & updates
✔ Stores metadata in the AWS Glue Data Catalog
✔ Makes S3 data easily queryable with Athena

3️⃣ Data Profiling & Exploratory Data Analysis (EDA)
🔹 Used ydata-profiling to generate an in-depth EDA report before querying the data.
🔹 Key insights gained:
✅ Missing values & potential outliers
✅ Correlation between numerical & categorical variables
✅ Distribution of key attributes like sales & profit
🔹 This step helped in understanding data integrity and optimizing future queries.

📌 Why ydata-profiling?
✔ Saves hours of manual EDA work
✔ Provides visual insights on missing values, correlations & distributions
✔ Helps in data cleaning & transformation decisions

4️⃣ Querying Data with AWS Athena
🔹 Connected AWS Athena to the AWS Glue Data Catalog for seamless querying.
🔹 Ran SQL queries to extract sales trends, customer segmentation, and profit analysis.
🔹 Optimized query performance using partitioning (snapshot_year).

Example Athena Query:

sql
Copy
Edit
SELECT snapshot_year, SUM(sales) AS total_sales, SUM(profit) AS total_profit
FROM db_store.orders
GROUP BY snapshot_year
ORDER BY snapshot_year;
📌 Why AWS Athena?
✔ Serverless SQL querying
✔ No need to manage databases
✔ Cost-effective (pay-per-query model)
✔ Works seamlessly with AWS Glue & S3

5️⃣ Data Validation using Microsoft Excel
🔹 After running queries in Athena, I cross-verified the results using Excel.
🔹 Used Pivot Tables & SUM functions to manually check sales & profit figures.
🔹 Ensured there were no discrepancies in data aggregation.

📌 Why Excel?
✔ Quick validation of query outputs
✔ Great for checking aggregates & trends
✔ Helps in debugging unexpected results

6️⃣ Data Visualization in AWS QuickSight
🔹 Built an interactive dashboard to showcase:
✅ Yearly sales & profit trends
✅ Top-selling product categories
✅ Region-wise performance
✅ Customer segmentation insights
🔹 Used AWS QuickSight's BI tools to create compelling visualizations.

📌 Why AWS QuickSight?
✔ Directly connects to Athena & S3
✔ Fast, interactive & scalable
✔ Great for business users & stakeholders

🎯 Final Thoughts & Key Learnings
🔹 Partitioning drastically improves query performance in Athena.
🔹 AWS Glue Crawlers automate schema discovery, saving time on manual metadata management.
🔹 ydata-profiling is a hidden gem that simplifies EDA and feature selection.
🔹 Excel remains a powerful yet underrated tool for cross-verifying query results.
🔹 Building an ETL pipeline in AWS is scalable, cost-effective, and highly automated!

