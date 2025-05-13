
## IPL Data Analytics Pipeline with Medallion Architecture



## Description
This project implements a Medallion Architecture-based Data Lakehouse using Microsoft Azure to perform comprehensive analysis on IPL (Indian Premier League) datasets. The architecture follows a structured, layered approach:

Bronze Layer: Ingests raw IPL data (6 CSV files) from a GitHub repository using Azure Data Factory. A dynamic data pipeline was developed with Linked Services to extract and load data into Azure Data Lake Storage Gen2.

Silver Layer: Processes and transforms the raw data using Azure Databricks and PySpark, including data cleaning, schema enforcement, and normalization. The transformed data is written back to the Silver zone of the Data Lake. Entra ID (formerly Azure AD) is used for secure access to storage.

Gold Layer: Curated and business-ready data is prepared in Azure Synapse Analytics. Using Serverless SQL Pools, external tables and views are created from the Silver layer data. With CETAS (Create External Table As Select), curated outputs are stored in the Gold layer.

Visualization Layer: The final curated data is connected to Power BI using the Synapse SQL endpoint, enabling interactive dashboards for IPL match analysis, player performance, and team statistics.

Security is maintained through:
Managed Identity for secure access between Synapse and Data Lake.
Entra ID for Databricks to access ADLS.
## Authentication and Access
Azure Data Factory: Used Linked Services for GitHub and ADLS

Azure Databricks: Accessed ADLS using Entra ID

Synapse Analytics: Utilized Managed Identity to securely read data from Data Lake
## Technologies Used
| Component      | Technology                 |
| -------------- | -------------------------- |
| Ingestion      | Azure Data Factory (ADF)   |
| Storage        | Azure Data Lake Gen2       |
| Transformation | Azure Databricks (PySpark) |
| Analytics      | Synapse Analytics (SQL)    |
| Visualization  | Power BI                   |
| Authentication | Entra ID, Managed Identity |
