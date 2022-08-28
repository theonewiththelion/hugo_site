---
title: "Second Post First Data Engineering Project, Focus: Airflow"
date: 2022-08-21T23:20:46-05:00
draft: False
---
**Post is under construction, this is available for testing purposes only.**

    ETL Diagram of my first project

[![Screen-Shot-2022-08-21-at-11-36-01-PM.png](https://i.postimg.cc/x846jz3w/Screen-Shot-2022-08-21-at-11-36-01-PM.png)](https://postimg.cc/T5nVChS0)

    *Extraction:* API containing the crime data from Austin, Texas.

[![Screen-Shot-2022-08-27-at-6-58-10-PM.png](https://i.postimg.cc/rwWGK2Kp/Screen-Shot-2022-08-27-at-6-58-10-PM.png)](https://postimg.cc/YvrLsVNc)

    *Transform:* Was performed in Visual Studio utilizing Pandas.

[![Screen-Shot-2022-08-27-at-7-13-06-PM.png](https://i.postimg.cc/jdBBJf44/Screen-Shot-2022-08-27-at-7-13-06-PM.png)](https://postimg.cc/bsHm7sMZ)

    *Load:* Data was uploaded into the data warehouse Big Query (Google Cloud Datastore).

[![Screen-Shot-2022-08-27-at-7-18-15-PM.png](https://i.postimg.cc/rmWN3drM/Screen-Shot-2022-08-27-at-7-18-15-PM.png)](https://postimg.cc/gXzh62sT)

    *Airflow:* Chosen due to popularity
    Aiflow documentation: [Link](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html)

        Populating arguments

[![Screen-Shot-2022-08-27-at-7-20-32-PM.png](https://i.postimg.cc/MKhKKvch/Screen-Shot-2022-08-27-at-7-20-32-PM.png)](https://postimg.cc/JG5Wp75q)

        Declaring Dags

[![Screen-Shot-2022-08-27-at-7-22-10-PM.png](https://i.postimg.cc/NFXG1cSN/Screen-Shot-2022-08-27-at-7-22-10-PM.png)](https://postimg.cc/H8pCgfp5)

        Setting up Task & dependencies

[![Screen-Shot-2022-08-27-at-7-26-52-PM.png](https://i.postimg.cc/zG8WXtRm/Screen-Shot-2022-08-27-at-7-26-52-PM.png)](https://postimg.cc/RNpqgTRG)


    *Visualization:* Data Studio because of easy to share and fully customizable dashboards/reports.

[Data Studio Dashboard Link](https://datastudio.google.com/reporting/945a2d3e-37be-4a21-be3e-91a9c1c1e7c6/page/YjD0C)

[![Screen-Shot-2022-08-21-at-11-53-16-PM.png](https://i.postimg.cc/Twwm2YYm/Screen-Shot-2022-08-21-at-11-53-16-PM.png)](https://postimg.cc/f3GkBsdT)

