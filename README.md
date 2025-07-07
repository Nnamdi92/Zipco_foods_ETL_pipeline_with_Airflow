# 🍕 Zipco Foods ETL Pipeline with Apache Airflow

A robust, automated ETL pipeline built using **Apache Airflow**, designed to streamline sales and inventory data processing for Zipco Foods. This project extracts transactional data, performs data cleaning and normalization, and loads it into Azure Blob Storage for downstream analytics and reporting.

---

## 📌 Project Overview

Zipco Foods operates across multiple outlets and generates large volumes of transactional data daily. This project automates the ETL workflow to support real-time analytics and enhance decision-making.

---

## ⚙️ Tech Stack

| Component             | Description                                               |
|----------------------|-----------------------------------------------------------|
| **Python**           | Core ETL scripting and data processing using `pandas`     |
| **Apache Airflow**   | Orchestration and scheduling of the ETL pipeline          |
| **Azure Blob Storage** | Centralized cloud storage for cleaned data             |
| **GitHub**           | Version control and collaboration                         |
| **Pandas / NumPy**   | Data wrangling and transformation                         |

---

## 📁 Project Structure

```bash
zipco_transaction/
├── data/
│   ├── zipco_transaction.csv
│   ├── clean_data.csv
│   ├── products.csv
│   ├── customers.csv
│   ├── staff.csv
│   └── transactions.csv
├── zipcovenv/                   # Virtual environment (excluded from Git)
├── .env                         # Azure credentials
├── .gitignore
├── create_user.txt
├── dag_script.py               # Defines Airflow DAG
├── Etl_pipeline.ipynb
├── Extraction.py
├── Transformation.py
├── Loading.py
├── README.md
└── requirements.txt
```

---

## 🔄 Workflow Summary

### 🟦 Extraction

- Reads `zipco_transaction.csv` into a pandas DataFrame

### 🟧 Transformation

- Removes duplicates  
- Handles missing values  
- Normalizes into 2NF/3NF: Products, Customers, Staff, Transactions

### 🟩 Loading

- Saves transformed files  
- Uploads all CSVs to Azure Blob Storage

---

## 📦 Airflow DAG Flow

```text
extraction_layer ➝ transformation_layer ➝ loading_layer
```

Each task is a Python function triggered by Airflow's `PythonOperator`.

---

## ☁️ Azure Integration

The cleaned datasets are uploaded to Azure Blob Storage under:

- `rawdata/cleaned_zipco_transaction_data.csv`
- `cleaneddata/products.csv`
- `cleaneddata/customers.csv`
- `cleaneddata/staff.csv`
- `cleaneddata/transactions.csv`

### 🔐 .env File

Create a `.env` file with the following structure:

```env
AZURE_STORAGE_CONNECTION_STRING=your_connection_string_here
CONTAINER_NAME=your_container_name
```

---

## 🚀 Running the Project

### 1. Clone the repository

```bash
git clone https://github.com/Nnamdi92/Zipco_foods_ETL_pipeline_with_Airflow.git
cd Zipco_foods_ETL_pipeline_with_Airflow
```

### 2. Create a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start Airflow

```bash
airflow standalone
```

### 5. Open the Airflow UI

Visit: [http://localhost:8080](http://localhost:8080)

Create a user if not automatically set:

```bash
airflow users create --username  --firstname  --lastname  --role  --email  --password 
```

### 6. Trigger the DAG

Find and trigger the DAG named:

```bash
real_zipco_dag
```

---

## 📈 Output

The pipeline creates and uploads the following cleaned datasets:

- `clean_data.csv`
- `products.csv`
- `customers.csv`
- `staff.csv`
- `transactions.csv`

All are stored in Azure Blob Storage and available for analytics and dashboarding.

---

## 📖 Case Study Reference

This project was developed as part of a case study on Apache Airflow orchestration for Zipco Foods.  


---

## 👨‍💻 Author

**Nnamdi Echezona**  
📧 [echezonannamdi@gmail.com](mailto:echezonannamdi@gmail.com)  


---

## 📜 License

This project is licensed under the MIT License.
