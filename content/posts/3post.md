---
title: "Azure ETL: PowerBI - Coming Soon/Work in Progress - Screenshots pending"
date: 2022-09-10T11:28:17-05:00
draft: False
author: "Jonathan de Jesus"
description: ""
---

## ETL Diagram from Austin API data to PowerBI
### Idea:
Extract data from [Austin](https://data.austintexas.gov/Health-and-Community-Services/Austin-Animal-Center-Outcomes/9t4d-g238), separate the information into three different tables, transform the data, upload it to Azure SQL and Visualize the information in PowerBI.
(Insert diagram)

### List of Technology used on this project:
List of skills used in this project are:

- Visual Studio
- Python - Pandas, SQLAlchemy, Functions(I know, right?)
- Azure SQL
- PowerBI
- Data Modeling

## ETL Information:

### Extraction

1. Import Libraries

```Python
from datetime import date, datetime
from sqlalchemy import create_engine
from sqlalchemy import Table, Column, Integer, String, MetaData, DateTime, Float
import urllib
import json
import requests
import pandas as pd
```
2. Create connection to Database
3. Extract data from API 
4. Create 3 tables in Azure SQL
5. Store data in 3 different tables: names, dates, outcome

### Transformation:

1. Extract information from tables - Azure SQL
2. Transform column monthyear, split values into two new columns
3. Transform column date, split information into 3 new columns
4. Transform column date of birth, take the information on the left of “T”
5. delete columns: Date time, month year
6. Load values into the table dates: since is tjhe only table where I performed transformation

### Load: *pending*

1. Created 3 new table (Production simulation)
2. Load records into new tables

### Visualization: 

1. Will be using PowerBI