---
layout: post
comments: true
title: "Journey of Data Science Project"
date: 2019-05-23
---

As we start working on an Analytics Project, we tend to think about the algorithms we are going to use and hence, as a data scientist our focus never really shifts to the other very important attributes. Although knowledge about various algorithms available is going to be very useful in coming up with the solutions but the process of model building involves much more than just agorithms. We need to have data in the usable format and with correct set of features for the model to give useful results. Without proper business knowledge infused into the data preparation, the results out a model is most probably going to be just garbage. In fact, the data preprocessing takes up most of the time in a model building exercise. So, let's list down the steps to be followed while executing a Machine Learning Project -

### 1. Defining Objective

The first step of any model building process has to be defining the objective. This will involve understanding how a business functions (domain knowledge is very crucial) and how it will use the data. It's very critical to be on the same page with your stakeholders in terms of what is expected at the end of the project. It's also important to get an understanding of how the results will be used for implementation as it might affect the approach taken during the exercise. Also, various departments within an organization might consume the results in a very different manner. Someone working on the field might want a very granular level insights while on the other hand someone like a CEO might just want info about Key Performance Indicators(KPIs). Overall, this step includes mapping out business objectives.

### 2. Transforming Business Objectives to Data Goals

Now that we have a clear understanding of what the business requirements are, we have to think about the data required for project execution. This step is often missed by the practitioners or is considered once the data is available from the clients end. This will lead to lost opportunity of giving valuable suggestions to your client for tracking additional data as once we have seen the data, it becomes difficult to think about all the possible factors from an open mind. For this, we should interview the subject matter experts from the client's side as well as from our own organization. They will help us create hypothesis based on their domain knowledge. We will then use these hypothesis to come up with the set of data required. The list of hypothesis collated is also going to be helpful in the data exploration stage as we will have a direction to move into as try to test them for their validity.

### 3. Data Gathering

Next, we start gathering data from various sources. This might require the help of a data engineer depending on the scale and complexity of the data. First, we need to identify all the sources from which we will obtain the data. Different data sources might be -
- Clients giving access to their database.
- Clients trasferring data through flat files.
- External Sources - This might involve scrapping data from various websites.

Some social media platforms provide their own APIs (Application Program Interface) for accessing data. But the introduction of GDPR(General Data Protection Regulation) means one cannot access a user's data without their consent. Appropriate changes have been made in the APIs accordingly.



If there are large no. of data sources involved, a data mart has to be created to streamline the access of data.

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








