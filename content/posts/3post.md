---
title: "Azure ETL: PowerBI - Coming Soon/Work in Progress"
date: 2022-09-10T11:28:17-05:00
draft: False
author: "Jonathan de Jesus"
description: ""
---

## ETL Diagram from Austin API data to PowerBI
### Idea:
Extract data from (Link to data), separate the columns into three different tables, transform the information, upload into Azure SQL and Visualize the information in PowerBi.
(Insert diagram)

### List of Technology used in this project are:
List of skills used in this project are:

- Visual Studio
- Python - Pandas, SQLAlchemy
- Azure SQL
- PowerBI
- Data Modeling

### Steps:

## Extraction

1. Import Libraries
2. Create connection to Database
3. Extract data from API 
4. Create 3 tables in Azure SQL
5. Store data in 3 different tables: names, dates, outcome

## Transformation:

1. Extract information from tables - Azure SQL
2. Transform column monthyear, split values into two new columns
3. Transform column date, split information into 3 new columns
4. Transform column date of birth, take the information on the left of “T”
5. delete columns: Date time, month year
6. Load values into the table dates: since is tjhe only table where I performed transformation

## Load: *pending*

1. Created 3 new table (Production simulation)
2. Load records into new tables

## Visualization: 

1. Will be using PowerBI