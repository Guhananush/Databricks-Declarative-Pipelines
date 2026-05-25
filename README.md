# Databricks-Declarative-Pipelines
Implementation of Medallion Architecture (Bronze, Silver, Gold layers) using Databricks, PySpark, and Delta Lake for scalable data engineering pipelines.

So, what is Databricks-Declarative-Pipelines means:
You describe what data transformation you want, and Databricks automatically handles how the pipeline runs.

It is the modern pipeline approach behind DLT (Delta Live Tables).

# what is DLT(Delta Live Tables)???
It is a framework used to build, automate, and manage data pipelines easily in Databricks.

Simple Meaning

Instead of writing complex ETL pipelines manually, DLT helps you:
Ingest data,
Clean and transform data,
Create tables automatically,
Monitor pipeline quality,
Handle errors and dependencies and 
with much less code.

Real-World Example

Suppose a company receives raw sales data every day.

Using DLT:

Raw data comes into a Bronze table           
Cleaned data goes to a Silver table                     
Final analytics-ready data goes to a Gold table     

This follows the Medallion Architecture in Databricks.

