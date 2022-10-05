---
title: "Azure ETL: PowerBI - Coming Soon/Work in Progress"
date: 2022-09-10T11:28:17-05:00
draft: False
author: "Jonathan de Jesus"
description: ""
lightgallery: true

toc:
  auto: false
---

## ETL Diagram from Austin API data to PowerBI
### Idea:
Extract data from [Austin](https://data.austintexas.gov/Health-and-Community-Services/Austin-Animal-Center-Outcomes/9t4d-g238), separate the information into three different tables, transform the data, upload it to Azure SQL and Visualize the information in PowerBI.

(Insert diagram)

### List of Technology used on this project:
List of skills used on this project are:
- Visual Studio
- Python - Pandas, SQLAlchemy, Functions(I know, right?)
- Azure SQL
- PowerBI
- Data Modeling (basic)

## ETL Information:

### Setup
1. Import Libraries
{{< admonition note "Library" >}}
```python
from datetime import date, datetime
from sqlalchemy import create_engine
from sqlalchemy import *
import urllib
import json
import requests
import pandas as pd
```
{{< /admonition >}}

2. Create connection to database - Azure SQL
{{< admonition note "Library" >}}
```python
#Azure Server information
server = 'animalserver.database.windows.net'
database = 'animaldatabase'
username = 'azureuser'
password = 'Azure_Password' 
driver= '{ODBC Driver 18 for SQL Server}'

#Azure Server Information Parameters
params = urllib.parse.quote_plus('DRIVER='+driver+';SERVER=tcp:'+server+';PORT=1433;DATABASE='+database+';UID='+username+';PWD='+ password)
#Learn how to create the connection
conn_str = 'mssql+pyodbc:///?odbc_connect={}'.format(params)
#Create Engine - VERY IMPORTANT
engine_azure = create_engine(conn_str,echo=True)
#Create metadata object, help at the creation of tables
meta = MetaData()
```
{{< /admonition >}}

### Extraction
1. Extract data from API and save into three dataframes; names, dates, & outcomes.
{{< admonition note "Extraction" >}}
```python
#Extraction    
#Extract data from API
#Save information into dataframe called names    
def api_extraction_names():
    animal_shelter_api = requests.get("https://data.austintexas.gov/resource/9t4d-g238.json?$limit=10")
    animal_shelter_table = animal_shelter_api.text
    json.loads(animal_shelter_table)
    animal_shelter_table = pd.read_json(animal_shelter_table)

    names = animal_shelter_table[["animal_id","name","animal_type","breed","color"]]
    print(names.head())

    return names

#Extract data from API
#Save information into dataframe called dates    
def api_extraction_dates():
    animal_shelter_api = requests.get("https://data.austintexas.gov/resource/9t4d-g238.json?$limit=10")
    animal_shelter_table = animal_shelter_api.text
    json.loads(animal_shelter_table)
    animal_shelter_table = pd.read_json(animal_shelter_table)

    dates = animal_shelter_table[["animal_id","datetime","monthyear","date_of_birth"]]
    print(dates.head())
    
    return dates

#Extract data from API
#Save information into dataframe called outcome    
def api_extraction_outcome():
    animal_shelter_api = requests.get("https://data.austintexas.gov/resource/9t4d-g238.json?$limit=10")
    animal_shelter_table = animal_shelter_api.text
    json.loads(animal_shelter_table)
    animal_shelter_table = pd.read_json(animal_shelter_table)
    
    outcome = animal_shelter_table[["animal_id","outcome_type","sex_upon_outcome","age_upon_outcome"]]
    print(outcome.head())
    
    return outcome
```
{{< /admonition >}}

### Transformation:
1. Transform column "monthyear", split values into two new columns
2. Transform column "date", split information into 3 new columns
3. Transform column "date of birth", take the information on the left of “T”
4. delete columns; "Date time" and "monthyear"
{{< admonition note "Transform" >}}
```python
#Transformation
#Separate values from column monthyear into two new columns date and date time, information from dates dataframe (not yet a table)
#Separate the column date, into 3 new columns date year, date motnh, date day
#separate the colum date of birth and accepting only everything before the value "T"
#Delete the columns datetime and monthyear
def transformation_dates(dates):
  
    #Documentation https://learn.microsoft.com/en-us/sql/machine-learning/data-exploration/python-dataframe-pandas?view=sql-server-ver16

    #documentation - https://datascienceparichay.com/article/pandas-split-column-by-delimiter/
    #take month year and separrate the values
    dates[['Date', 'date_time']] = dates['monthyear'].str.split('T', expand = True)
    
    dates[['date_year', 'date_month', 'date_day']] = dates['Date'].str.split('-', expand = True)
    
    #Documentation
    #https://stackoverflow.com/questions/40705480/python-pandas-remove-everything-after-a-delimiter-in-a-string
    #Separate the field date of birth after the value "T"
    dates['date_of_birth'] = dates['date_of_birth'].str.split('T').str[0]
    
    #drop "datetime", "monthyear"
    #extract_dates.drop(['datetime','monthyear'], axis=1)
    del dates['datetime']
    del dates['monthyear']
    
    print(dates)
    return dates

```
{{< /admonition >}}

### Load:
1. Create three tables in Azure SQL
2. Load records into new tables using the three dataframes used in the extraction step
{{< admonition note "Table creation & data load" >}}
```python
def load_animal_shelter(names, outcome, dates):
    
    p_names = Table(
        'p_names', meta,
        Column('animal_id', String(20), primary_key = True),
        Column('name', String),
        Column('animal_type', String),
        Column('breed', String),
        Column('color', String),
    )
    
    p_dates = Table(
        'p_dates', meta,
        Column('animal_id', String(20), primary_key = True),
        Column('datetime', DateTime),
        Column('monthyear', String),
        Column('date_of_birth', String)
    )
    
    p_outcome = Table(
        'p_outcome', meta,
        Column('animal_id', String(20), primary_key = True),
        Column('outcome_type', String),
        Column('sex_upon_outcome', String),
        Column('age_upon_outcome', String)
    )
    
    meta.create_all(engine_azure)
    print("Tables created")
    
    #Will update this with a function later on
    names.to_sql('p_names', con=engine_azure, if_exists='replace', index=False)
    print("Table names Populated")
    outcome.to_sql('p_dates', con=engine_azure, if_exists='replace', index=False)
    print("Table dates Populated")
    dates.to_sql('p_outcome', con=engine_azure, if_exists='replace', index=False)
    print("Table outcome Populated")
```
{{< /admonition >}}

### Azure SQL
1. See list of tables and columns
2. See Query and results
![](../azure_sql.png)

### Visualization: PowerBI
1. Dashboard present: 
    - Total of records
    - Distribution of animal type
    - Type of animal and their breed
    - Reason of leaving shelter
    - Sex outcome when leaving the shelter
    
    ![](../Visualization1.png)

2. Select animal type to filter dashboard

    ![](../Visualization2.png)


