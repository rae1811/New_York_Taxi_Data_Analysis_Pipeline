# New_York_Taxi_Data_Analysis_Pipeline 
## 1. Project Overview
This project builds a complete ETL pipeline using **Mage**, **Pandas**, and **BigQuery** to ingest, transform, model, and analyze New York Taxi trip data. The data is normalized into a star schema for efficient querying and reporting.

## 2. Data Architecture
[Uber Data (CSV in GCS)] 
    ↓ (API Pull via Mage)
[Raw Data Loader Block] 
    ↓
[Transformer Block]
    ├─ Creates Dimension Tables (datetime, passenger_count, etc.)
    └─ Creates Fact Table (trip metrics)
    ↓
[BigQuery Export Block]
    → Tables in Dataset: `datetime_dim`, `fact_table`, etc.
    ↓
[SQL Final Table Big Query]
    → Tables in Dataset: `tbl_analytics`
    ↓
[Reporting Layer]
    → Looker 


![Data Architecture Diagram](architecture.jpg) 
## 3. Data Model – Star Schema
**Fact Table:**

- `fact_table`: Contains key trip metrics (fare amount, duration, etc.) and foreign keys to all dimension tables.

**Dimension Tables:**

- `datetime_dim`: Pickup & dropoff timestamps  
- `passenger_count_dim`: Number of passengers  
- `trip_distance_dim`: Distance traveled in miles  
- `rate_code_dim`: Taxi rate code (e.g., Standard Rate)  
- `pickup_location_dim`: Pickup zone and borough  
- `dropoff_location_dim`: Dropoff zone and borough  
- `payment_type_dim`: Payment method (e.g., Credit Card, Cash)


![Data Model Diagram](data_model.jpeg) 


## 4. Report
Explore the full analytics dashboard here:  
[View on Looker Studio](https://lookerstudio.google.com/u/0/reporting/9348b42b-5d04-4cac-9bbb-274a6bac29ce/page/24rOF/edit?s=srkBWtGhzeY)
[**View Full Report (PDF)**](New_York_Taxi_Analysis.pdf)


## 5. Tools & Technologies

- [Mage](https://www.mage.ai/) – Modern data orchestrator for ETL  
- **Pandas** – Data wrangling and transformation  
- **Google BigQuery** – Scalable cloud data warehouse  
- **Looker** – BI tool for dashboarding and reporting  
- **Google Cloud Storage (GCS)** – Source CSV file storage  
