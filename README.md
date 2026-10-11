<a href="https://chuquemeka.dev">
  <img src="./assets/banner.svg" alt="Emeka Nweke Edeh, Data Platform Engineer. Visit chuquemeka.dev" width="100%" />
</a>

<div align="center">

[![Website](https://img.shields.io/badge/Website-chuquemeka.dev-5FD3A5?style=for-the-badge&logo=googlechrome&logoColor=white)](https://chuquemeka.dev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Edeh_Emeka-0077B5?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0yMC40NSAyMC40NWgtMy41NnYtNS41N2MwLTEuMzMtLjAyLTMuMDQtMS44NS0zLjA0LTEuODUgMC0yLjE0IDEuNDUtMi4xNCAyLjk0djUuNjdIOS4zNVY5aDMuNDF2MS41NmguMDVjLjQ4LS45IDEuNjQtMS44NSAzLjM3LTEuODUgMy42IDAgNC4yNyAyLjM3IDQuMjcgNS40NnY2LjI4ek01LjM0IDcuNDNhMi4wNiAyLjA2IDAgMSAxIDAtNC4xMyAyLjA2IDIuMDYgMCAwIDEgMCA0LjEzek03LjEyIDIwLjQ1SDMuNTZWOWgzLjU2djExLjQ1ek0yMi4yMiAwSDEuNzdDLjc5IDAgMCAuNzcgMCAxLjczdjIwLjU0QzAgMjMuMjMuNzkgMjQgMS43NyAyNGgyMC40NWMuOTggMCAxLjc4LS43NyAxLjc4LTEuNzNWMS43M0MyNCAuNzcgMjMuMiAwIDIyLjIyIDB6Ii8%2BPC9zdmc%2B)](https://www.linkedin.com/in/edeh/)
[![YouTube](https://img.shields.io/badge/YouTube-Data_Pipeline_Lab-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@Data_Pipeline_Lab)

</div>

## About

Data Platform Engineer based in Berlin with 5+ years of experience designing and delivering data platforms on AWS, GCP and Databricks.

I own platforms end to end: cloud infrastructure and networking, CDC ingestion, lakehouse modelling, orchestration, serving, observability and CI/CD. I care about clean environment boundaries, reproducible delivery, and systems the next engineer can understand.

**Focus areas:** cloud data platforms · CDC and event-driven ingestion · medallion architecture · analytics engineering · infrastructure as code · applied AI on trusted data

---

## Flagship Build: Enterprise Data Platform on AWS

A multi-repo platform that turns PostgreSQL change events into business-ready analytics, answered in plain English through a browser or Slack.

```mermaid
flowchart LR
    classDef src fill:#1f2933,stroke:#8b958f,color:#e6ebe8
    classDef bronze fill:#3a2614,stroke:#c98a4b,color:#f3dcc4
    classDef silver fill:#2a3035,stroke:#a9b4bd,color:#e6ebe8
    classDef gold fill:#3a3010,stroke:#e2b93b,color:#f6e7b0
    classDef serve fill:#10291f,stroke:#5fd3a5,color:#d6f5e8

    PG["PostgreSQL<br/>+ AWS DMS CDC"]:::src --> BRZ["Bronze<br/>S3 raw CDC"]:::bronze
    BRZ --> SLV["Silver<br/>Glue PySpark"]:::silver
    SLV --> GLD["Gold<br/>dbt on Athena"]:::gold
    GLD --> RS["Redshift<br/>Serverless"]:::serve
    GLD --> AGT["Analytics agent<br/>Web + Slack"]:::serve
```

- **Ingestion:** PostgreSQL RDS with AWS DMS full load and CDC into an immutable S3 Bronze layer
- **Processing:** 6 parallel Glue PySpark jobs reconcile CDC into Silver, with invalid records quarantined
- **Modelling:** 15 tested dbt models on Athena build the Gold layer
- **Serving:** Redshift Serverless, plus a FastAPI/Streamlit analytics agent on ECS Fargate with a Slack gateway
- **Operations:** Step Functions orchestration (MWAA alternative), Terraform across 9 modules, GitHub Actions CI/CD
- **Reliability:** private networking, encryption, least-privilege IAM, data quality gates, CloudWatch alarms and audit logging
- **Efficiency:** a full pipeline run finishes in 10–12 minutes, with cost-aware infrastructure lifecycle

| Repository | Purpose |
|---|---|
| [terraform-platform-infra-live](https://github.com/enterprise-data-platform-emeka/terraform-platform-infra-live) | Networking, storage, processing, serving and orchestration infrastructure |
| [platform-glue-jobs](https://github.com/enterprise-data-platform-emeka/platform-glue-jobs) | Bronze → Silver PySpark jobs with CDC reconciliation and validation |
| [platform-dbt-analytics](https://github.com/enterprise-data-platform-emeka/platform-dbt-analytics) | Silver → Gold dbt models on Athena |
| [platform-analytics-agent](https://github.com/enterprise-data-platform-emeka/platform-analytics-agent) | Natural-language analytics agent with guarded SQL generation |
| [platform-orchestration-mwaa-airflow](https://github.com/enterprise-data-platform-emeka/platform-orchestration-mwaa-airflow) | Airflow implementation of the end-to-end pipeline |

[View the full organisation →](https://github.com/enterprise-data-platform-emeka)

---

## Selected Projects

| Project | Stack | What it shows |
|---|---|---|
| [Databricks Real Estate Pipeline](https://github.com/ChuquEmeka/Databricks_Asset_Bundles_Real_Estate_Data_Pipeline_Youtube) | Databricks, Delta Live Tables, GCP | Medallion lakehouse with Asset Bundles and CI/CD |
| [Real Estate Valuation](https://github.com/ChuquEmeka/real_estate_valuation_dbt_fusion_snowflake_aws_pipeline) | dbt Fusion, Snowflake, S3 | Multi-source valuation pipeline with automated delivery |
| [Healthcare Pipeline on GCP](https://github.com/ChuquEmeka/Airflow-dbt-bigquery-gcs-healthcare-data-pipeline) | Airflow, dbt, BigQuery, GCS | Orchestrated transformation on Google Cloud |
| [Real-Time IoT Pipeline](https://github.com/ChuquEmeka/iot-kafka-bigquery-gcs-real-time-data-pipeline) | Kafka, BigQuery, GCS | Streaming ingestion for analytics |
| [Fraud Detection Pipeline](https://github.com/ChuquEmeka/DBT-Fraud-Detection-Data-Pipeline) | dbt, Snowflake, S3 | Fraud analytics modelling with CI/CD |
| [Sales Analytics Pipeline](https://github.com/ChuquEmeka/End-to-End-Data-Pipeline-Snowflake-dbt-Tableau) | Snowflake, dbt, Tableau | Incremental star-schema modelling through to BI |

---

## Core Stack

![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![Spark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
