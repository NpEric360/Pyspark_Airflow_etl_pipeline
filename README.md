# Pyspark_Airflow_etl_pipeline

# End-to-End ETL Pipeline for Heart Failure Prediction

This repository contains an end-to-end ETL (Extract, Transform, Load) pipeline for heart failure prediction using a dataset available on Kaggle. The pipeline extracts and transforms the data using PySpark and converts it to the Apache Parquet file format. The processed data is then uploaded to an AWS S3 bucket.

## Dataset
- The heart failure prediction dataset used in this project can be found on Kaggle: [Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction/data).

## Pipeline Overview
1. **Data Extraction and Transformation**:
   - The project leverages PySpark for data extraction and transformation to ensure efficient processing of the dataset.

2. **Data Storage**:
   - The transformed data is stored in the Apache Parquet file format, which is well-suited for analytical workloads.

3. **AWS S3 Integration**:
   - The processed data is uploaded to an AWS S3 bucket, offering secure, scalable, and cost-effective storage for your data.

4. **AWS Crawler**:
   - An AWS crawler is employed to create table definitions based on the uploaded Parquet files. This step simplifies data access and ensures compatibility with services like Amazon Athena.

5. **Data Analysis with Amazon Athena**:
   - Amazon Athena is utilized to query the tables created by the AWS crawler. This provides a serverless, interactive query service for analyzing your data with SQL.

6. **Data Visualization with Tableau**:
   - To visualize your data and gain insights, you can connect Tableau to the destination S3 bucket containing all Amazon Athena queries. This enables powerful data visualization and reporting capabilities.




##File directory structure:

##Airflow Installation Folder:
-> airflow-webserver.pid
-> airflow.cfg
-> webserver_config.py
-> logs
-> dags
    -> DAG_0.py
    -> includes
        --> A_v1_first_setup.py
        --> B_v1_data_scrambler.py
        --> C_v1_etl_pyspark.py
        --> D_v1_write_to_s3.py
        --> data
            --> input_data.csv
            --> batches
                --> processed
                    --> heart_dirty_dataset_0.csv
                --> heart_dirty_dataset_1.csv
                -->
            --> parquets
                --> processed
                    --> heart_data2023_10_23_190556
                --> heart_data2023_10_23_20010
        


##Setup:
1. Copy the DAG folder to your Airflow installation folder. 
  It contains the main Airflow DAG which calls functions from:
  1. C_v1_etl_pyspark.py => Extracts and transforms input .csv files from the data directory. Writes each cleaned .csv file as a parquet.
  2. D_v1_write_to_s3.py => Uploads parquet files to S3 bucket and moves files to processed parquet directory.
2. Follow the installation and bootup setup instructions in setup


