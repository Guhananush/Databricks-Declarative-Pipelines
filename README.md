# Databricks-Declarative-Pipelines
Implementation of Medallion Architecture (Bronze, Silver, Gold layers) using Databricks, PySpark, and Delta Lake for scalable data engineering pipelines.You just declare what you want – and DLT takes care of how it should be done.

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

# BENEFITS

Built-in DLT supports something called Expectations – where you can define rules (like "this column should never be null"). If a record breaks the rule, DLT will drop it or send it to quarantine – and you don’t have to write extra code to handle it. Data Quality Check.

### AUTOMATIC DEPENDENCY MANAGEMENT                 
You don’t need to worry about the order of transformations. Just define your tables and DLT figures out which table depends on which and runs things in the correct order.

### INCREMENTAL PROCESSING
DLT is smart – it only processes new or changed data using something called Change Data Capture (CDC).

### UNIFIED BATCH AND STREAMING
Normally, batch and streaming pipelines are built and maintained separately. But with DLT, you can use the same code for both. It detects whether your data source is streaming and handles it accordingly.  

# Lakeflow code editor in Databricks

Lakeflow Code Editor in Databricks is the coding environment used to write and manage data pipelines using code instead of only visual tools.

It is mainly used for creating:                

ETL pipelines                       
Streaming pipelines                                        
Batch workflows                               
Declarative Pipelines (DLT)          

Using languages like:                
   Python             
   SQL 
   
### What it does?Lakeflow Code Editor allows developers to:

Write pipeline logic                 
Define tables and transformations             
Schedule workflows                  
Debug and test pipelines                
Manage production data engineering tasks          

### Lakeflow Code Editor = a coding workspace in Databricks where data engineers write and manage pipeline code for data processing.

<img width="777" height="292" alt="image" src="https://github.com/user-attachments/assets/8494ce4e-1316-4f79-9a23-cb89ea3969cc" />

# Batch View
Batch View refers to a view or dataset created using batch processing.

That means:

Data is processed at fixed intervals                   
Entire chunks of data are handled together                  
Not continuous like streaming   

## What is Batch Processing?                      

Batch processing means:

Collect data for some time              
Process it together in one job           

Example:                 
Sales data processed every night at 12 AM               
Daily attendance report     

# Streaming Table

A Streaming Table continuously processes new incoming data in real time or near real time.

 ##### It works incrementally.

### Main Idea:         
Reads only newly arrived records               
Updates automatically                  
Used for live pipelines     

## How It Works

New data arrives → system processes only the new rows → table updates continuously

# Append Flow API
It is used to continuously add (append) new records from a source into a target streaming table without modifying or deleting existing records.

## Simple Meaning

### Think of it like a logbook:

Existing data stays as it is.
New incoming data is added to the end.
Old records are not updated or removed.

### Why Use Append Flow?                   
Ingest streaming data          
Process event logs            
Collect sensor/IoT data                   
Store clickstream data                 
Build Bronze layer tables in the Medallion Architecture        

#### Append Flow API = a Lakeflow API that continuously writes new incoming data to a target table by adding rows only, without changing existing data.

# Data Quality Checks with Expectation          

      

![expectations flow](./assets/expectations-flow.png)

Use expectations to apply quality constraints that validate data as it flows through ETL pipelines. Expectations provide greater insight into data quality metrics and allow you to fail updates or drop records when detecting invalid records.   

This article has an overview of expectations, including syntax examples and behavior options. For more advanced use cases and recommended best practices, see Expectation recommendations and advanced patterns.

# What are expectations?                    

Expectations are optional clauses in pipeline materialized view, streaming table, or view creation statements that apply data quality checks on each record passing through a query. Expectations use standard SQL Boolean statements to specify constraints. You can combine multiple expectations for a single dataset and set expectations across all dataset declarations in a pipeline.

# create_auto_cdc_flow

The create_auto_cdc_flow() function creates a flow that uses Lakeflow Spark Declarative Pipelines change data capture (CDC) functionality to process source data from a change data feed (CDF).

## Syntax

from pyspark import pipelines as dp

dp.create_auto_cdc_flow(                
  target = "<target-table>",                           
  source = "<data-source>",                    
  keys = ["key1", "key2", "keyN"],                        
  sequence_by = "<sequence-column>",                            
  ignore_null_updates = <bool>,                             
  apply_as_deletes = None,                          
  apply_as_truncates = None,                        
  column_list = None,                                   
  except_column_list = None,                                 
  stored_as_scd_type = <type>,                                
  track_history_column_list = None,                                
  track_history_except_column_list = None,                            
  name = None,                        
  once = <bool>                             
)                                   
                 
For create_auto_cdc_flow processing, the default behavior for INSERT and UPDATE events is to upsert CDC events from the source: update any rows in the target table that match the specified key(s) or insert a new row when a matching record does not exist in the target table. Handling for DELETE events can be specified with the apply_as_deletes parameter.                      

To learn more about CDC processing with a change feed, see The AUTO CDC APIs: Simplify change data capture with pipelines. For an example of using the create_auto_cdc_flow() function, see AUTO CDC examples.









