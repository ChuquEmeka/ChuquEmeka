<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&duration=3000&pause=1000&color=58A6FF&center=true&vCenter=true&width=600&lines=Hi%2C+I%27m+Emeka+%F0%9F%91%8B;Data+%26+Platform+Engineer;AWS+%7C+dbt+%7C+Airflow+%7C+Terraform" alt="Typing SVG" />

<br/>

I build production-grade data platforms end-to-end.<br/>
**PostgreSQL CDC → Bronze → PySpark → Silver → dbt → Gold → Redshift → AI Analytics Agent**

<br/>

Six years in real estate before engineering. I bring real business context to technical decisions.

<br/>

[![YouTube](https://img.shields.io/badge/YouTube-Data_Pipeline_Lab-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@Data_Pipeline_Lab)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Edeh_Emeka-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/edeh/)
![Profile Views](https://komarev.com/ghpvc/?username=ChuquEmeka&style=for-the-badge&color=0077B5&label=Profile+Views)

</div>

---

## GitHub Stats

<div align="center">
  <img height="180" src="https://github-readme-stats.vercel.app/api?username=ChuquEmeka&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
  <img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=ChuquEmeka&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />
</div>

<div align="center">
  <img src="https://streak-stats.demolab.com/?user=ChuquEmeka&theme=tokyonight&hide_border=true" />
</div>

---

## Tools & Technologies

**Cloud & Infrastructure**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=FF9900)
![Terraform](https://img.shields.io/badge/Terraform-623CE4?style=flat-square&logo=terraform&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=google-cloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)

**Data Processing & Transformation**

![Apache Spark](https://img.shields.io/badge/Spark-E25A1C?style=flat-square&logo=apache-spark&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)

**Orchestration & Serving**

![Apache Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apache-airflow&logoColor=white)
![AWS Step Functions](https://img.shields.io/badge/Step_Functions-FF4F8B?style=flat-square&logo=amazon-aws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/S3-569A31?style=flat-square&logo=amazon-s3&logoColor=white)
![Amazon Redshift](https://img.shields.io/badge/Redshift-8C4FFF?style=flat-square&logo=amazon-redshift&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)

**Languages & BI**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=power-bi&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat-square&logo=tableau&logoColor=white)

---

## Enterprise Data Platform

A complete production-grade AWS data platform built as a single coherent system.
All source, infrastructure, and application code lives in a dedicated GitHub organisation.

**Organisation:** [enterprise-data-platform-emeka](https://github.com/enterprise-data-platform-emeka)

| Repository | What it does |
|---|---|
| [terraform-platform-infra-live](https://github.com/enterprise-data-platform-emeka/terraform-platform-infra-live) | All AWS infrastructure across 9 Terraform modules: VPC, S3, Glue, Redshift, MWAA, ECS Fargate, Step Functions, and monitoring |
| [platform-analytics-agent](https://github.com/enterprise-data-platform-emeka/platform-analytics-agent) | Natural language → SQL → chart and insight via Claude API on ECS Fargate with FastAPI and Streamlit |
| [platform-glue-jobs](https://github.com/enterprise-data-platform-emeka/platform-glue-jobs) | PySpark Bronze to Silver ETL across 6 parallel Glue jobs |
| [platform-dbt-analytics](https://github.com/enterprise-data-platform-emeka/platform-dbt-analytics) | dbt Silver to Gold models with data quality tests on Athena |
| [platform-orchestration-mwaa-airflow](https://github.com/enterprise-data-platform-emeka/platform-orchestration-mwaa-airflow) | Airflow DAGs deployed on Amazon MWAA |
| [platform-cdc-simulator](https://github.com/enterprise-data-platform-emeka/platform-cdc-simulator) | PostgreSQL CDC event generator for end-to-end pipeline testing |

<details>
<summary><b>View architecture diagram</b></summary>
<br>

```mermaid
flowchart LR
    subgraph Source["Source Layer"]
        PG[PostgreSQL RDS] -->|WAL| DMS[AWS DMS CDC]
    end

    subgraph Bronze["Bronze Layer"]
        DMS --> S3B[S3 Bronze\nRaw Parquet]
    end

    subgraph Silver["Silver Layer"]
        S3B --> Glue[Glue PySpark\n6 ETL Jobs]
        Glue --> S3S[S3 Silver\nCleaned Parquet]
    end

    subgraph Gold["Gold Layer"]
        S3S --> DBT[dbt + Athena]
        DBT --> S3G[S3 Gold\nAggregated Parquet]
    end

    subgraph Serving["Serving Layer"]
        S3G --> RS[Redshift Serverless]
        S3G --> Agent[Analytics Agent\nECS Fargate + Claude API]
    end

    MWAA[MWAA Airflow] -.->|orchestrates| Glue
    MWAA -.->|orchestrates| DBT
```

</details>

---

## Other Projects

| Project | Stack | What it demonstrates |
|---|---|---|
| [Real Estate ELT Pipeline](https://github.com/ChuquEmeka/Databricks_Asset_Bundles_Real_Estate_Data_Pipeline_Youtube) | Databricks, Delta Live Tables, GCP | Medallion architecture with streaming ingestion on GCP |
| [Real Estate Valuation Pipeline](https://github.com/ChuquEmeka/real_estate_valuation_dbt_fusion_snowflake_aws_pipeline) | dbt Fusion, Snowflake, S3 | Multi-source transformation with Snowflake as the serving layer |
| [Healthcare Analytics Pipeline](https://github.com/ChuquEmeka/Airflow-dbt-bigquery-gcs-healthcare-data-pipeline) | Airflow, dbt, BigQuery, GCS | Full orchestration and transformation on Google Cloud |
| [Fraud Detection Pipeline](https://github.com/ChuquEmeka/DBT-Fraud-Detection-Data-Pipeline) | dbt, Snowflake | End-to-end analytics pipeline with dbt data modelling |
| [End-to-End Snowflake Pipeline](https://github.com/ChuquEmeka/End-to-End-Data-Pipeline-Snowflake-dbt-Tableau) | Snowflake, dbt, Tableau | Full pipeline from ingestion to Tableau BI dashboard |

---

<div align="center">

**Watch pipeline demos and tutorials on my YouTube channel**

[![YouTube](https://img.shields.io/badge/YouTube-Data_Pipeline_Lab-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@Data_Pipeline_Lab)

</div>
