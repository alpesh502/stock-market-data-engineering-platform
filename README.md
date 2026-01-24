#  End-to-End Stock Market Data Engineering & Analytics Platform

##  Project Objective
The objective of this project is to design and implement a **production-grade data engineering pipeline** for stock and cryptocurrency market data that supports **automated ingestion, incremental processing, historical tracking, and analytics-ready reporting**.

This project demonstrates how raw market data is ingested, refined, historized, and finally exposed for analytics using **real-world cloud data engineering patterns**.

---

##  Project Overview
This project implements an **end-to-end data pipeline** using **Azure Data Factory, Azure Data Lake Gen2, Azure Databricks, Delta Lake, and Power BI**.

Market data such as **Open, High, Low, Close (OHLC) prices and Trading Volume** is ingested from **APIs and CSV-based sources**, processed through a **Raw → Bronze → Silver → Gold architecture**, and visualized using **interactive Power BI dashboards** with automated refresh.

---

##  Target Users
- **Data Analysts** – for price trend and volume analysis  
- **Business & Finance Teams** – for monitoring market movements  
- **Decision Makers** – for KPI-driven insights  

---

##  Data Used
The project works with **time-series market data** for stocks and cryptocurrencies.

### Key Attributes
- Date / Trade Date  
- Open Price  
- High Price  
- Low Price  
- Close Price  
- Trading Volume  

### Data Sources
1. **API Source**
   - Used for incremental market data ingestion  
   - Triggered and orchestrated using Azure Data Factory  

2. **CSV Files**
   - **Historical CSV** – full backfill of historical market data  
   - **Snapshot CSV** – daily point-in-time market state  

---

##  Solution Architecture
The project follows a **layered Raw → Bronze → Silver → Gold architecture** to ensure scalability, auditability, and analytics readiness.

![Solution Architecture](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/stock_market(architecture).png)

---

##  Raw Layer (Azure Data Lake – ADF Ingestion)
- Data ingested using **Azure Data Factory pipelines**
- Supports:
  - API-based ingestion
  - CSV-based ingestion
- Stores raw data **exactly as received**
- Used for traceability, replay, and audit purposes  

![ADF Raw Ingestion](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/ADF_Ingestion.png)

---

##  Bronze Layer (Databricks)
- Raw data from ADLS loaded into Databricks
- Minimal transformations applied
- Schema inferred and standardized
- Data stored as **Delta tables**
- Acts as a clean landing zone for downstream processing  

![Bronze Layer](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/bronze_layer.png)

---

##  Silver Layer (Databricks – Incremental & SCD Type 2)
- Data cleansing and validation applied
- Column standardization and type casting
- **Incremental processing implemented**
- **Slowly Changing Dimension (SCD Type 2)** logic applied to track:
  - Price changes
  - Volume changes
  - Historical state of records
- Delta Lake `MERGE` operations used
- Optimized for accurate and reliable analytics  

![Silver Layer](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/silverlayer(db).png)

---

##  Gold Layer (Databricks – Analytics Ready)
- Business-ready Delta tables
- Aggregation-friendly schema
- Optimized for BI consumption
- Designed specifically for **Power BI dashboards**

Gold datasets include:
- Market price history  
- Daily snapshot state  
- Current trading metrics  

![Gold Layer](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/gold_layer.png)

---

##  Data Processing & Automation (Azure Databricks)
- **PySpark** used for all transformations
- **Delta Lake** provides:
  - ACID transactions
  - Schema enforcement
  - Incremental merges
  - SCD Type 2 implementation
- Separate notebooks for:
  - Bronze layer
  - Silver layer
  - Gold layer
- Databricks Jobs configured for fully automated execution  

![Databricks Pipeline](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/Databricks_Pipeline.png)

---

##  Analytics & Visualization (Power BI)
- Power BI connected to **Databricks SQL Warehouse**
- Star-schema modeling with a **central Date Dimension**
- Interactive dashboards featuring:
  - Date slicers
  - Trading volume KPIs
  - OHLC price trend analysis
- Automated refresh to reflect the latest market data  

![Power BI Dashboard](https://github.com/alpesh502/stock-market-data-engineering-platform/blob/main/powerbi_dashboard.png)

---

##  Business Value
- Eliminates manual data preparation  
- Maintains full historical traceability using **SCD Type 2**  
- Enables incremental and scalable data processing  
- Provides a **single source of truth** for market analytics  
- Architecture easily extensible for new stocks and cryptocurrencies  

---

##  Tech Stack
- Azure Data Factory  
- Azure Data Lake Gen2  
- Azure Databricks  
- Delta Lake  
- PySpark  
- SQL  
- Power BI  

---

##  Author
**Alpesh Singh**  
Aspiring Data Engineer  
Azure | Databricks | SQL | Power BI  
