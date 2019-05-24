---
layout: post
comments: true
title: "Journey of Data Science Project"
date: 2019-05-23
---

Although knowledge about various algorithms available is going to be very useful in coming up with the solutions but the process of model building involves much more than just agorithms. You need to have data in the usable format and with correct features for the model to give useful results. In fact, the data preprocessing takes up most of the time in model building. Let's list down the steps to be followed. 

### 1. Defining Objective

The first step of any model building process has to be defining the objective. It's very critical to be on the same page with your stakeholders in terms of what is expected at the end of the project. It's also important to get an understanding of how the results will be used for implementation as it might affect the approach taken during the exercise.

-- understand business objectives and requirements
-- understand how business functions and how it will use the data
-- how the results will impact the decision making
-- different departments in your client's organization might want different results

### 2. Transforming Business to Modelling Goals

Now that we have a clear understanding of what the business requirements are, we have to think about the execution plan. We need to decide on the data required to carry out modelling exercise. This step will also involve hypothesis creation where we form a set of hypothesis for our objectives. This is going to be helpful in the data exploration stage. We also decide on the type of model (not specific algorithm) to be used, if required.

-- hypothesis creation involves interviewing subject matter experts in the company/client's side
-- this should be done before data gathering. it helps you give additional suggestions to the clients.

### 3. Data Gathering

Once we have an execution plan in place, we start gathering data as per the hypothesis. This might require the help of a data engineer depending on the scale of the data and requirement of database. If there are large no. of data sources involved, a data mart has to be created to streamline the access of data.

-- identify sources - data from clients, macro economic (external data)external sources
-- structured - RDBMS (Oracle, Postgresql, Mysql, teradata,  Sql  Server, Redshift etc), flat files
-- unstructred - (NoSql means not only sql)- HDFS  (Hadoop distributed file system, hive,(impala may be) is used) ,MongoDB, Cassandra, hbase, flat files etc (handles structured as well)
-- Datawarehouse vs Data mart (specfic type of data)(subset of data warehouse)(structured)
-- Data Lake
-- APIs (GDPR)

-- spark is used for in-memory data processing (to cope up with disadvantage of hadoop)
-- Apache 



-- Databases, excel, csv, web scraping, Web APIs for Facebook, Twitter etc
-- Databases - MYSQL, Postgre sql, MongoDB

### 4. Data Preprocessing / Exploratory Analysis



### 5. Model Selection and Validation



### 6. Model Deployment and Maintenance







