# AWS Snowflake Integration using Docker

## Introduction
This project aims to demonstrate the integration between Amazon Web Services (AWS), Snowflake, and Docker. The goal is to set up an environment where data is transferred from AWS S3 to Snowflake, transformed, and stored for reporting purposes. The process involves setting up Airflow using Docker, creating tables in Snowflake, loading data from AWS S3, performing transformations, and finally visualizing the results.

## Prerequisites
To successfully run this project, ensure you have the following installed:
- Docker Desktop
- Visual Studio Code
- Astro CLI

## Installation Steps
1. Install Docker Desktop by running the `install.exe` file.
2. Install Visual Studio Code.
3. Download the `docker-compose.yaml` file from [Apache Airflow Documentation](https://airflow.apache.org/docs/apache-airflow/2.5.1/docker-compose.yaml).
4. Open Visual Studio Code.
5. Create a new file named `.env` and add the following lines:
AIRFLOW_IMAGE_NAME=apache/airflow:2.4.2
AIRFLOW_UID=50000

6. Run `docker-compose up -d` to start the Docker containers.
7. Create an Admin user in Airflow by running:


## Data Preparation
1. Inside the `include` folder, create a new folder named `data`.
2. Create a CSV file named `order_header.csv` with the following content:

order_id,customer_id,purchase_date,amount
ORDER1,CUST1,1/1/2021,100
ORDER2,CUST2,2/2/2022,200
ORDER3,CUST3,3/3/2023,300
3. Upload the `order_header.csv` file to an AWS S3 bucket.

## Snowflake Setup
1. Access the Snowflake platform.
2. Create a worksheet.
3. Run the following SQL commands to set up the database, warehouse, and schema:

CREATE DATABASE ASTRO_SDK_DB;
CREATE WAREHOUSE ASTRO_SDK_DW;
CREATE SCHEMA ASTRO_SDK_SCHEMA;
4. Create the `customers_table` and `reporting_table` using the provided SQL commands.

## Airflow Configuration
1. Add connections on the Airflow server:
- AWS S3 connection
- Snowflake connection

## Running the Data Pipeline
1. Navigate to the `dags` folder in Airflow.
2. Add the necessary DAG file for orchestrating the data pipeline.
3. Run the DAG, which will:
- Pull data from AWS S3
- Transform the data
- Load it into Snowflake tables

## Conclusion
By following the steps outlined in this project, you will have successfully set up a data pipeline that transfers data from AWS S3 to Snowflake using Dockerized Apache Airflow. This enables seamless data integration and reporting capabilities within your environment.

## Credits
- [Apache Airflow Documentation](https://airflow.apache.org/docs/apache-airflow/2.5.1/docker-compose.yaml)
- [Snowflake Documentation](https://docs.snowflake.com/en/user-guide/getting-started-tutorial-using-web-interface.html)


