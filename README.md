# 🌦️ End-to-End Weather Data Pipeline using OpenWeather API & Databricks

## 📌 Project Overview
This project demonstrates an end-to-end **data engineering pipeline** built using the **Medallion Architecture (Bronze, Silver, Gold)**.  
Weather data is ingested from the **OpenWeather API**, processed using **PySpark in Databricks**, and stored as **Delta tables** for analytics and reporting.

---

## ⚙️ Tech Stack
- Databricks (Community / Free Edition)
- PySpark
- Delta Lake
- Python (requests, json)
- OpenWeather API

---

## 🏗️ Architecture
Weather API (Raw JSON)
->   Bronze Layer (Raw Data)
->   Silver Layer (Cleaned & Transformed Data)
->   Gold Layer (Aggregated Data)
->   BI / Analytics (Power BI / SQL)



---

## 🧱 Medallion Architecture

### Bronze Layer (Raw Ingestion)
- Stores raw API data (JSON format)
- Append-only data for reprocessing and recovery
- Schema-on-read

### Silver Layer (Cleaned & Refined)
- Parsed and structured data
- Deduplicated and validated
- Standardized formats
- Business transformations applied

### Gold Layer (Analytics Ready)
- Aggregated datasets
- Business-level metrics
- Optimized for reporting and querying

---

## 🔄 Pipeline Workflow
1. **Data Ingestion**
   - Extracts weather data from OpenWeather API using API key authentication
   - Stores raw JSON data into Bronze layer (Databricks Volumes)

2. **Data Parsing**
   - Parses nested JSON using predefined schema (StructType)
   - Flattens complex structures (arrays, nested fields)

3. **Data Transformation (Silver Layer)**
   - Cleans and standardizes data
   - Deduplicates (city + timestamp)
   - Converts epoch time to readable format
   - Adds metadata columns (event_time, ingestion_time)

4. **Data Analysis (Gold Layer)**
   - Calculates average temperature and humidity per city
   - Extracts latest weather records using window functions
   - Stores curated datasets as Delta tables

---

## ⚡ Delta Lake Features Used
- ACID Transactions  
- Time Travel (`VERSION AS OF`)  
- Schema Enforcement & Evolution  
- MERGE, UPDATE, DELETE support  
- Table History (`DESCRIBE HISTORY`)  

---

## 🔄 Orchestration
Pipeline orchestration is implemented using **Databricks Jobs** with modular notebooks:
- `Data_Ingestion` – API data extraction
- `Data_Parsing` – JSON parsing and structuring
- `Data_Transformation` – Data cleaning and Silver layer creation
- `Data_Analysis` – Aggregations and Gold layer generation

**Features:**
- Task-level dependencies  
- Sequential execution  
- Monitoring and failure handling  
- Re-runnable pipeline  

---

## ✅ Data Quality & Validation
- Null checks on critical fields (temperature, city)  
- Deduplication validation  
- Schema validation  
- Controlled transformations for consistency  

---

## ⚠️ Limitations (Free Edition)
- Only Databricks Volumes are writable  
- No support for Auto Loader or streaming  
- Limited support for checkpoints and external storage  

---

## 🔮 Future Enhancements
- Incremental & real-time data ingestion  
- Advanced error handling and retry mechanisms  
- Data quality framework integration  
- CI/CD pipeline implementation  
- Performance optimization (partitioning, Z-ordering)  
- Data governance using Unity Catalog  
- Dashboard integration using Power BI  

---

## 📊 Key Outcomes
- Built a complete end-to-end API-based data pipeline  
- Implemented Medallion Architecture (Bronze → Silver → Gold)  
- Leveraged Delta Lake for reliability and versioning  
- Designed modular, reusable, and scalable workflows  
- Delivered analytics-ready datasets for reporting  

---

## 📌 Conclusion
This project demonstrates a fully functional, end-to-end API-driven data pipeline using Databricks.  
Data is ingested from external APIs, processed through structured transformation layers, and delivered as analytics-ready datasets.  

The pipeline is modular, scalable, and designed with industry best practices such as **Medallion architecture, Delta Lake optimization, and job orchestration**, making it suitable for real-world data engineering use cases.

