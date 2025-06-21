"# New_York_Taxi_Data_Analysis_Pipeline" 
1. Project Overview
This project builds a complete ETL pipeline using **Mage**, **Pandas**, and **BigQuery** to ingest, transform, model, and analyze New York Taxi trip data. The data is normalized into a star schema for efficient querying and reporting.

2. Data Architecture
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

3. Data Model (Star Schema)

-Fact Table: fact_table
Metrics about each trip with foreign keys to all dimensions.

-imensions:

datetime_dim (pickup & dropoff time info)

passenger_count_dim

trip_distance_dim

rate_code_dim

pickup_location_dim

dropoff_location_dim

payment_type_dim


![Data Model Diagram](data_model.jpg) 


4. Report
[📄 View Full Report (PDF)](New_York_Taxi_Analysis.pdf)