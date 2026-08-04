# Azure-Synapse
# Azure Synapse Analytics ETL Pipeline using Medallion Architecture

## Overview

This project demonstrates an end-to-end Data Engineering solution built on **Azure Synapse Analytics** following the **Medallion Architecture (Bronze → Silver → Gold)**.

The solution ingests raw sales data into Azure Data Lake Storage Gen2, transforms it using Synapse Mapping Data Flows, and models it into a Star Schema consisting of Fact and Dimension tables using Serverless SQL Pool.

---

## Architecture

```
                    Source CSV Files
                           │
                           ▼
          Azure Data Lake Storage Gen2
                           │
                           ▼
                     Bronze Layer
                  (Raw Source Data)
                           │
                           ▼
             Synapse Mapping Data Flow
          (Data Cleansing & Transformation)
                           │
                           ▼
                     Silver Layer
             (Cleaned Parquet Files)
                           │
                           ▼
             Serverless SQL Pool
          External Tables & CETAS
                           │
                           ▼
                      Gold Layer
          Dimension Tables & Fact Table
                           │
                           ▼
                 Reporting & Analytics
```

---

## Tech Stack

- Azure Synapse Analytics
- Azure Data Lake Storage Gen2
- Azure Synapse Pipelines
- Mapping Data Flows
- Serverless SQL Pool
- Azure SQL
- SQL
- Parquet
- Git & GitHub

---

## Project Workflow

### Bronze Layer

- Raw CSV files are ingested into Azure Data Lake Storage Gen2.
- No transformations are applied.
- Acts as the raw data repository.

---

### Silver Layer

Data is transformed using Synapse Mapping Data Flows.

Transformations include:

- Data cleansing
- Removing duplicates
- Filtering invalid records
- Data type conversion
- Derived columns
- Writing output as Parquet files

---

### Gold Layer

Serverless SQL Pool is used to create analytical tables.

Created objects include:

- Master Key
- Database Scoped Credential
- External Data Source
- External File Format
- External Tables

Dimension tables are created using CETAS (CREATE EXTERNAL TABLE AS SELECT).

---

## Star Schema

```
                 DimCustomer
                      │
                      │
DimOrders ───── FactSales ───── DimProduct
                      │
                      │
                DimGeography
```

---

## Dimension Tables

### DimCustomer

Contains:

- CustomerID
- CustomerName
- CustomerEmail
- Domain
- DimCustomerKey

---

### DimProduct

Contains:

- ProductID
- ProductName
- ProductCategory
- DimProductKey

---

### DimOrders

Contains:

- OrderID
- OrderDate
- DimOrdersKey

---

### DimGeography

Contains:

- RegionID
- Country
- DimGeoKey

---

## Fact Table

The FactSales table stores transactional data.

Measures:

- Quantity
- UnitPrice
- TotalAmount

Foreign Keys:

- DimOrdersKey
- DimCustomerKey
- DimProductKey
- DimGeoKey

---

## Azure Synapse Features Used

- Azure Data Lake Storage Gen2
- Synapse Pipelines
- Mapping Data Flows
- Serverless SQL Pool
- OPENROWSET
- External Tables
- CETAS
- Database Scoped Credentials
- External Data Sources
- External File Formats
- Star Schema Data Modeling

---

## Repository Structure

```
Azure-Synapse-Medallion-Architecture
│
├── Data
│   └── Sample Sales Data
│
├── Pipelines
│   └── ETL Pipeline
│
├── DataFlows
│   └── BronzeToSilver
│
├── SQL
│   ├── Create Master Key.sql
│   ├── Create Credentials.sql
│   ├── Create External Data Sources.sql
│   ├── Create External File Formats.sql
│   ├── Create Silver External Table.sql
│   ├── Create DimCustomer.sql
│   ├── Create DimProduct.sql
│   ├── Create DimOrders.sql
│   ├── Create DimGeography.sql
│   └── Create FactSales.sql
│
├── Images
│   ├── Architecture.png
│   ├── Pipeline.png
│   ├── DataFlow.png
│   └── StarSchema.png
│
└── README.md
```

---

## Key Learnings

- Implemented Medallion Architecture using Azure Synapse Analytics.
- Built scalable ETL pipelines using Synapse Mapping Data Flows.
- Queried data using Serverless SQL Pool.
- Created External Tables over Parquet files stored in ADLS Gen2.
- Implemented Star Schema data modeling with Fact and Dimension tables.
- Used CETAS (CREATE EXTERNAL TABLE AS SELECT) to create analytical datasets.
- Applied surrogate key generation using `ROW_NUMBER()`.
- Designed an analytics-ready data warehouse for reporting.

---

## Future Enhancements

- Incremental data loading using Watermark columns.
- Data Quality validation framework.
- Automated pipeline scheduling with Synapse Triggers.
- CI/CD deployment using Azure DevOps or GitHub Actions.
- Power BI dashboards for business reporting.

---

## Author

**Aditi Aryan**

Data Engineer | Azure | SQL | Synapse Analytics | Data Warehousing | ETL | Azure Data Factory
