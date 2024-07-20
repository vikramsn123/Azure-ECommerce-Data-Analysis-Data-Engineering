# Azure-ECommerce-Data-Analysis-Data-Engineering
ECommerce data analysis using Azure data factory and Data bricks.
Overview of the E-Com project steps:

# Azure Data Lake Storage (ADLS) 📂

File (.csv) were downloaded from data.world and uploaded to an Azure ADLS path.

# Azure Data Factory (ADF) 🏭

This raw data is ingested into another Azure Data Lake Storage (ADLS) in .parquet format using Azure Data Factory (ADF), employing both scheduled ingestion for unchanged files and storage-based triggering methods for frequently changing files.

# Azure Event Grid/ Azure Function ⚡

An event grid triggers an Azure Function, which initiates an Azure Databricks Workflow (Job) by making a Rest API post request with the job ID from Databricks Workspace.

# Azure Databricks 🧱

This job comprises three Databricks Notebooks containing Apache PySpark code. The first notebook mounts the data from ADLS and ingests it into the bronze layer. Transformations are applied, and the data is saved in delta format as the silver layer. Finally, a business-aggregated dataframe is exported as a .csv file in ADLS.

# Snowflake ❄️

This process utilizes the medallion architecture to build a reliable, performant delta lake in ADLS. Using ADLS storage event triggering through Snowpipe, the ingested data is loaded into a Snowflake table.

# Architecture
![architecture](https://github.com/user-attachments/assets/9c994f99-6b92-43a7-96e9-a3e9402292ce)
