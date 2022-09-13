---
title: "Basic ETL using Python, Big Query, Data Studio & Airflow"
date: 2022-08-21T23:20:46-05:00
draft: false
author: "Jonathan de Jesus"
#images: [Users/theonewiththelion/hugo_site/themes/LoveIt/images/Screen Shot 2022-09-09 at 12.40.02 PM.png]
description: "Here we learn how to use Airflow"
---
## ETL Diagram of my first project

### Idea:
Get data raw data from [Austin Crime](https://data.austintexas.gov/Public-Safety/Crime-Reports/fdj4-gpfu), transform it, store the data in the cloud and utilize a visualization too to properly present the data.

### List of Technology used in this project are:
- Visual Studio
- Python Pandas
- Big Query
- Data Studio
- Airflow

![](../etl_diagram.png)

## 1. Library Imports 

![](../Imports.png)

## 2. Extraction: API containing the crime data from Austin, Texas.

![](../api_extraction.png)

## 3. Transformation: Used Visual Studio & Pandas.

### Transformation: Rename of Columns

![](../transformation_rename.png)

### Transformation: Change format of "Date Ocurred" from military time, to standard time

![](../trasformation_date_occured.png)

### Transformation: Change format of "Date Reported" from military time, to standard time 

![](../transformation_date_reported.png)

## 4. Load: Upload data into Big Query.
![](../data_load.png)

## 5. Airflow: Preferred scheduler (and wanted to learn the application)
Useful: [Aiflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html)

### Defaulting arguments
![](../airflow_arguments.png)

### Declaring DAGs
![](../dags_setup.png)

### Setting up Task [] = Makes the task run parallel
![](../task_setup.png)

### Setting up dependencies
![](../dependencies_setup.png)

### Airflow DAG: etl_workflow Graph
![](../dag_workflow.png)

## 6. Big Query Table: Our preferred data warehouse
### Table Schema
![](../bigquery_schema.png)

### Table data (example)
![](../bigquery_data.png)


## 7. Data Studio: Our preferred visualization tool
[Dashboard Link](https://datastudio.google.com/reporting/945a2d3e-37be-4a21-be3e-91a9c1c1e7c6/page/YjD0C)

![](../visualization.png)

