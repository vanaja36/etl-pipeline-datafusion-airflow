# ETL Pipeline with Data Fusion, Airflow, and BigQuery

## 📌 About
This project demonstrates an **end-to-end ETL (Extract, Transform, Load) pipeline** built on **Google Cloud Platform** using:
- **Python** for data extraction and CSV generation
- **Google Cloud Storage (GCS)** as staging
- **Google Cloud Data Fusion** for transformation
- **BigQuery** as the data warehouse
- **Apache Airflow** for orchestration

The pipeline automates the process of generating synthetic employee data, staging it in GCS, transforming it in Data Fusion, and loading the cleaned data into BigQuery for analytics.
## 🚀 Architecture
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/962ea486-ef53-4c29-863b-4a2296f55b10" />


## 🛠️ Tools & Technologies
- **Google Cloud Data Fusion** → Data ingestion & transformation  
- **Apache Airflow** → Workflow orchestration & scheduling  
- **Google BigQuery** → Data warehouse for analytics  
- **Google Cloud Storage (GCS)** → Staging area for raw/processed data  
- **Python (Faker, GCS SDK)** → Data generation & extraction  
- **SQL** → Data validation  

## 🔄 Workflow Steps
1. **Extract (extract.py)**  
   - Generates synthetic employee data (100+ rows) using `Faker`.  
   - Saves data into a timestamped CSV file.  
   - Uploads CSV into GCS bucket (`gs://bkt-employee-data/employee_data/`).  

2. **Transform (Data Fusion Pipeline)**  
   - Cleans employee data.  
   - Removes duplicates, standardizes formats, and maps schema.  

3. **Load (BigQuery)**  
   - Transformed data is written into BigQuery table:  
     `project.dataset.employee_data`  

4. **Orchestration (Airflow DAG)**  
   - Runs `extract.py` to generate/upload CSV.  
   - Triggers Data Fusion pipeline.  
   - (Optional) Runs BigQuery validation SQL to confirm data load.  


