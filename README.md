# 🚀 Dynamic Data Ingestion and Storage in HDFS with Automated Hive Integration. 
Technologies: Python, API, HDFS, Hive, Shell scripting.

This project showcases an efficient and scalable data ingestion pipeline leveraging the Hadoop ecosystem, specifically HDFS and Apache Hive, to process dynamic U.S. Census data. It simulates real-world big data workflows by ingesting structured CSV data into distributed storage, enabling SQL-based querying through Hive, and laying the groundwork for automated, production-grade data refreshes. This repository reflects my hands-on learning journey in Data Engineering, focusing on building robust, future-ready data infrastructure.
Automated data ingestion into HDFS for fault-tolerant storage.
Schema-on-read optimization via HiveQL for ad-hoc analytics.
Built with extensibility in mind, using HDFS file formats and HiveQL compatible with common Big Data tools.

As part of my Data Engineering specialization, this project mirrors industry practices in distributed data warehousing, emphasizing:
✅ Modularity (reusable code for future datasets).
✅ Performance (partitioning, compression in Hive).
✅ Reproducibility (documented orchestration steps).

Impact: A foundation for building real-time or batch pipelines with enterprise-grade reliability.
---

## 📌 Project Objective

Design and implement a robust data ingestion pipeline that:

- Ingests raw census data from a CSV file.
- Uploads it into the Hadoop Distributed File System (HDFS).
- Creates a Hive table with the correct schema.
- Loads and verifies data integrity.
- (Optionally) Automates the data refresh process using a scheduled Python script.

---

## 🧠 Tech Stack

- **Hadoop HDFS** – Distributed data storage  
- **Apache Hive** – Data warehousing and SQL querying  
- **Beeline CLI** – Hive interface for query execution  
- **MySQL Metastore** – Hive schema storage  
- **VS Code** – Development environment
- **CentOs9-VMware Workstation** - MobaXterm (SSH Terminal) for Linux based operations.  
- **GitHub** – Version control and collaboration  

---

## 📋 Completed Steps to Accomplish Project Agenda

| Step | Description | Status |
|------|-------------|--------|
| 1️⃣ | Downloaded census data CSV: `hu-est2001-cty_fips.csv` from Census Bureau | ✔️ |
| 2️⃣ | Inspected schema using `head -5` — confirmed 8 columns, comma-delimited, with headers | ✔️ |
| 3️⃣ | Uploaded the CSV to HDFS: `/user/talam/usgov_censuss-data/hu-est2001_cty_fips.csv` | ✔️ |
| 4️⃣ | Started required services: MySQL Metastore, Hive Metastore, HiveServer2, Beeline | ✔️ |
| 5️⃣ | Created Hive database: `usg_censusdb` | ✔️ |
| 6️⃣ | Created Hive table `us_population` with proper 8-column schema | ✔️ |
| 7️⃣ | Loaded data from HDFS into Hive table | ✔️ |
| 8️⃣ | Verified data load & integrity with queries | ✔️ |

---

💻 Tools & Setup Used
Tools	| Role  
(Apache) - Hadoop	HDFS setup & file handling.
(Apache Hive)	- Query engine and data warehouse.
(MySQL) -	Hive Metastore backend.
(Beeline)	- Interface to execute Hive queries.

🏁 Future Scope
Add dynamic ingestion automation using Python,
Integrate monitoring/logging for job execution,
Transition this pipeline for larger datasets and file formats like Parquet.

## 📂 Hive Table Schema

The table `us_population` was created with the following schema:

```sql
CREATE TABLE us_population (
  fips_state INT,
  fips_county INT,
  region INT,
  division INT,
  estimate_2001 BIGINT,
  estimate_2000 BIGINT,
  census_2000 BIGINT,
  area_name STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

📊 **Sample Query Output**
SELECT * FROM us_population LIMIT 10;
fips_state	fips_county	region	division	estimate_2001	estimate_2000	census_2000	area_name
1	0	3	6	1996827	1969682	1963711	Alabama
1	1	3	6	18036	17728	17662	Autauga County

🔁 Optional Next Step: Automate Future Data Refreshes
A Python-based automation script (to be added) will help:
Fetch the latest CSV from a source or folder.
Upload it to HDFS.
Overwrite or Append the Hive table with new data.
Schedule this pipeline via cron or Airflow.
This will enable a production-style refresh mechanism, simulating dynamic data pipelines in big data projects.
