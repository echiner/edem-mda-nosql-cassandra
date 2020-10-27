# Post Work: Inserting and reading data in real-time

## Introduction

In this exercise you will be implementing a real use case, inserting data in real-time and making it available for reporting.

The proposed architecture will be the following:

Data source --> Apache NiFi --> Cassandra --> Apache Zeppelin

In any case, feel free to implement the use case using other alternatives such as:

* Replace Apache Zeppelin with a Java microservice
* Replace Apache NiFi with custom code or using a different tool

## Use case

As explained during the course, these are typical use cases:

* Transaction logging: Purchases, test scores, movies watched and movie latest location
* Storing time series data (as long as you do your own aggregates)
* Tracking pretty much anything including order status, packages, etc.
* Storing health tracker data
* Weather service history
* Internet of things (IoT) status and event history

You will have to which use case to use, based on the previous list or a new one you choose.

## Tasks

You will have to perform the following tasks:

1. Define your use case
2. Find a dataset and data source
3. Define the data model
4. Implement the data ingestion into Cassandra (either with NiFi or something different)
5. Implement the data reporting from Cassandra (either with Zeppelin, MicroServices or something different)

## Deliverables

You will have to provide the following:

* Basic explanation of:
  * Use case
  * Dataset or data source selected
  * Final architecture implemented
* DDL of your data model
* Data ingestion implementation details (if NiFi was selected, then screenshots of workflow and basic config is enough)
* Data consumption implementation details (if Zeppelin was selected, then screenshots of reports is enough)
