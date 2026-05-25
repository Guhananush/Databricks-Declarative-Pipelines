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
Medallion Architecture is a recommended data design pattern used in the Lakehouse architecture to organize data into multiple layers based on quality and processing stage.

It mainly consists of:

Bronze Layer → Raw data                  
Silver Layer → Cleaned and transformed data                   
Gold Layer → Business-ready data              

This architecture helps build scalable and reliable data pipelines using technologies like:

Delta Lake                 
Apache Spark                         
Databricks Delta Live Tables (DLT)

#Architecture Flow

Data Sources             
     ↓                         
 Bronze Layer           
     ↓                          
 Silver Layer                 
     ↓                      
 Gold Layer              
     ↓                      
BI / ML / Analytics

![expectations flow](./assets/expectations-flow.png)

![sample image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQx-SfzikhR2Xc7K_zwJEPObbGJ9TxD68OcwA&s)

