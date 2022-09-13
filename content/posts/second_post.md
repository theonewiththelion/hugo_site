---
title: "Basic ETL using Python, Big Query, Data Studio & Airflow"
date: 2022-08-21T23:20:46-05:00
draft: false
author: "Jonathan de Jesus"
#images: [Users/theonewiththelion/hugo_site/themes/LoveIt/images/Screen Shot 2022-09-09 at 12.40.02 PM.png]
description: "Here we learn how to use Airflow"
---
    ETL Diagram of my first project
    
[![Screen-Shot-2022-08-21-at-11-36-01-PM.png](https://i.postimg.cc/x846jz3w/Screen-Shot-2022-08-21-at-11-36-01-PM.png)](https://postimg.cc/T5nVChS0) 

    Extraction: API containing the crime data from Austin, Texas.
[![Screen-Shot-2022-09-09-at-12-40-02-PM.png](https://i.postimg.cc/vmLYf3KJ/Screen-Shot-2022-09-09-at-12-40-02-PM.png)](https://postimg.cc/Ty1vXqf0)

    Transform: Was performed in Visual Studio utilizing Pandas.
Transformation: Rename of Columns

[![Screen-Shot-2022-09-09-at-12-51-08-PM.png](https://i.postimg.cc/L6wQ3RKP/Screen-Shot-2022-09-09-at-12-51-08-PM.png)](https://postimg.cc/ppQBPwdV)

Transformation: Change format of "Date Ocurred" from Military time, to standard time

[![Screen-Shot-2022-09-09-at-12-52-55-PM.png](https://i.postimg.cc/76hSRGSZ/Screen-Shot-2022-09-09-at-12-52-55-PM.png)](https://postimg.cc/CByZBKv3)

Transformation: Change format of "Date Reported" from Military time, to standard time

[![Screen-Shot-2022-09-09-at-12-54-42-PM.png](https://i.postimg.cc/RFtw9rpk/Screen-Shot-2022-09-09-at-12-54-42-PM.png)](https://postimg.cc/xJ0XyZ25)


    Load: Data was uploaded into the data warehouse Big Query (Google Cloud Datastore).

[![Screen-Shot-2022-09-09-at-12-57-32-PM.png](https://i.postimg.cc/RCRNtVtP/Screen-Shot-2022-09-09-at-12-57-32-PM.png)](https://postimg.cc/231kRY2v)

    Airflow: Chosen due to popularity
[Aiflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html)

Defaulting arguments

[![Screen-Shot-2022-09-09-at-12-59-35-PM.png](https://i.postimg.cc/SNYbhgmW/Screen-Shot-2022-09-09-at-12-59-35-PM.png)](https://postimg.cc/ykKbhXgd)

Declaring DAGs

[![Screen-Shot-2022-09-09-at-1-00-30-PM.png](https://i.postimg.cc/PqVkH9vQ/Screen-Shot-2022-09-09-at-1-00-30-PM.png)](https://postimg.cc/3yGqCLBk)

Setting up Task & dependencies

[![Screen-Shot-2022-09-09-at-1-02-05-PM.png](https://i.postimg.cc/0Q10z2Sk/Screen-Shot-2022-09-09-at-1-02-05-PM.png)](https://postimg.cc/Lqv17Svw)

[![Screen-Shot-2022-09-09-at-1-02-56-PM.png](https://i.postimg.cc/tgjsP1BM/Screen-Shot-2022-09-09-at-1-02-56-PM.png)](https://postimg.cc/k2TMP53Q)

Airflow DAG: etl_workflow Graph

[![Screen-Shot-2022-09-10-at-11-31-12-AM.png](https://i.postimg.cc/DzRhVCwD/Screen-Shot-2022-09-10-at-11-31-12-AM.png)](https://postimg.cc/DWQHLPsd)


    Big Query Table: Easy connection to Data Studio
Table Schema

[![Screen-Shot-2022-09-09-at-1-05-07-PM.png](https://i.postimg.cc/X7xWxrNP/Screen-Shot-2022-09-09-at-1-05-07-PM.png)](https://postimg.cc/GHB6mhyP)

Table data (example)

[![Screen-Shot-2022-09-09-at-1-07-35-PM.png](https://i.postimg.cc/13ZCdQMN/Screen-Shot-2022-09-09-at-1-07-35-PM.png)](https://postimg.cc/jLZ4WBps)


    Visualization: Data Studio because of easy to share and fully customizable dashboards/reports.
[Data Studio Dashboard Link](https://datastudio.google.com/reporting/945a2d3e-37be-4a21-be3e-91a9c1c1e7c6/page/YjD0C)

[![Screen-Shot-2022-08-21-at-11-53-16-PM.png](https://i.postimg.cc/Twwm2YYm/Screen-Shot-2022-08-21-at-11-53-16-PM.png)](https://postimg.cc/f3GkBsdT)

