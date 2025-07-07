# 🍕 Zipco Foods ETL Pipeline with Apache Airflow

A robust, automated ETL pipeline built using **Apache Airflow**, designed to streamline sales and inventory data processing for Zipco Foods. This project extracts transactional data, performs data cleaning and normalization, and loads it into Azure Blob Storage for downstream analytics and reporting.

---

## 📌 Project Overview

Zipco Foods operates across multiple outlets and generates large volumes of transactional data daily. This project automates the ETL workflow to support real-time analytics and enhance decision-making.

---

## ⚙️ Tech Stack

| Component         | Description                                                 |
|------------------|-------------------------------------------------------------|
| **Python**       | Core ETL scripting and data processing using `pandas`       |
| **Apache Airflow** | Orchestration and scheduling of the ETL pipeline            |
| **Azure Blob Storage** | Centralized cloud storage for cleaned data                  |
| **GitHub**        | Version control and collaboration                           |
| **Pandas/NumPy** | Data wrangling and transformation                           |

---

## 📁 Project Structure

```bash
zipco_project/
│
├── dags/
│   └── dag_script.py               # Defines the Airflow DAG and task flow
│
├── Extraction.py                   # Reads raw CSV data
├── Transformation.py              # Cleans and normalizes the data
├── Loading.py                     # Uploads cleaned data to Azure Blob Storage
│
├── data/
│   └── zipco_transaction.csv       # Raw input data
│   └── clean_data.csv              # Cleaned dataset
│   └── products.csv                # Normalized products table
│   └── customers.csv               # Normalized customers table
│   └── staff.csv                   # Normalized staff table
│   └── transactions.csv            # Final transactions table
│
└── .env                            # Stores Azure credentials

🔄 Workflow Summary
Extraction

Reads zipco_transaction.csv into a pandas DataFrame.

Transformation

Removes duplicates

Handles missing values

Normalizes into 2NF/3NF: Products, Customers, Staff, Transactions

Loading

Saves transformed files

Uploads to Azure Blob Storage

The entire pipeline is orchestrated with Apache Airflow using a DAG (dag_script.py).

📦 Airflow DAG Flow
extraction_layer ➝ transformation_layer ➝ loading_layer
Each task is a Python function triggered by Airflow's PythonOperator.

☁️ Azure Integration
The final cleaned datasets are stored in Azure Blob Storage under two folders:

rawdata/cleaned_zipco_transaction_data.csv

cleaneddata/ → products.csv, customers.csv, staff.csv, transactions.csv

Make sure to set up your Azure connection string and container name in a .env file:
AZURE_STORAGE_CONNECTION_STRING=your_connection_string_here
CONTAINER_NAME=your_container_name

🚀 Running the Project
1. Clone the repository:
git clone https://github.com/Nnamdi92/Zipco_foods_ETL_pipeline_with_Airflow.git
cd zipco-etl-pipeline

2. Create a virtual environment:
python3 -m venv venv
source venv/bin/activate

3. Install dependencies:
pip install -r requirements.txt

4. Start Airflow:
airflow standalone

5. Open the UI: http://localhost:8080
 Username/Password: set via airflow users create or shown at first launch

6. Trigger the DAG named: real_zipco_dag

📈 Output
The pipeline creates and uploads the following datasets:

clean_data.csv

products.csv

customers.csv

staff.csv

transactions.csv

All are stored in Azure Blob Storage and available for analytics.

📖 Case Study Reference
This project was developed as part of a case study on Apache Airflow orchestration for Zipco Foods. 

👨‍💻 Author
Nnamdi Echezona
Email: echezonannamdi@gmail.com
