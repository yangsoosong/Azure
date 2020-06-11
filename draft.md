<img src="https://4.bp.blogspot.com/--9GKuWgk5Xk/XHOt7_djBXI/AAAAAAAAGhI/re6OHdgcdvozR4n8zn0VuLLBh2FLo135gCLcBGAs/s400/Azure%2BData%2BFactory%2Band%2BData%2BPipeline.jpg" alt="Azure Data Factory" height="250"/>

In this blog post, we will talk about Azure and how utilizing the technology had positive impact on our data engineering project. We use Azure Data Factory to compose, orchestrate and monitor data collection, then we bring those data into Azure Blob Storage. Later we consume the collected data with Power BI clients and Azure Analysis services.

We spent many hours learning **Azure** and applying it to our project for few months or so. And if we could explain it in just few minutes, we believe we are going to provide a lot of value to the readers(mainly small business owners or small size companies) to consider Azure as their next tech stack.

The decision to use Azure instead of ~~AWS~~ was made due to the fact it is more cost effective and we will talk about this as well in our blog post.

## What is Azure Data Factory - how can it help to get data out of cloud services?

<img src="https://azurecomcdn.azureedge.net/cvt-79019141ab66488956a9bdab2a37a127c8b26bb437a895176c06dd32fc3f70b3/images/page/services/data-factory/img-valprop2.jpg" height="250"/>

According to Microsoft website, Azure Data Factory is
>... the platform that solves such data scenarios. It is the cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale. Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores. You can build complex ETL processes that transform data visually with data flows or by using compute services such as Azure HDInsight Hadoop, Azure Databricks, and Azure SQL Database.

>Additionally, you can publish your transformed data to data stores such as Azure SQL Data Warehouse for business intelligence (BI) applications to consume. Ultimately, through Azure Data Factory, raw data can be organized into meaningful data stores and data lakes for better business decisions.

[What is Azure Data Factory?
](https://docs.microsoft.com/en-us/azure/data-factory/introduction)

It is expensive work to integrate and maintain to take care of ETL across the data landscape.

Data Factory enables us to conduct following for incoming data:
* Composing
* orchestrating
* Monitoring

Data Factory also provides features such as Automatic Cluster Management, Retries for Transient Failures, Configurable Timeout Policies and Alerting.
Then, you can consume your data with BI and analytics tool or another tools to enrich insights.

A company is growing fast and the distributor/contributor of the products usually have different format of data. As company grows bigger, the issue of maintaining data format becomes more essential.

For our project, it was essential part of our project to standardize and normalize we combine data streams from as many as nine systems, depending on the number of customers that we have.

We can use Data Factory to build pipelines from different systems. The interoperability of Data Factory and Power BI enables our BI clients to freely create various data analysis models and consume data upon their needs.

## What is azure blob storage and what types of use could it be?  What would a company use it for?
First of all, what is BLOB?
According to Wikipedia, "A Binary Large OBject (BLOB) is a collection of binary data stored as a single entity in a database management system"

Azure Blob storage is Microsoft's object storage solution for the cloud.
Blob storage is optimized for storing massive amounts of unstructured data.

Unstructured data is data that doesn't adhere to a particular data model or definition, such as text or binary data.

An Azure storage account contains all of your Azure Storage data objects: blobs, files, queues, tables, and disks. The storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS. Data in your Azure storage account is durable and highly available, secure, and massively scalable.
___
**Blob**: A file of any type and size.
___
**Container**: A group of blobs. There is no limit to the number of blobs in a container. The name of a container must always be lowercase.
___
**Storage Account**: Azure offers three storage account types – General Purpose v1 (GPv1), General Purpose v2 (GPv2), and a dedicated blob storage account.
___

Users or client applications can access objects in Blob storage via HTTP/HTTPS, from anywhere in the world. Objects in Blob storage are accessible via the Azure Storage REST API, Azure PowerShell, Azure CLI, or an Azure Storage client library. Client libraries are available for different languages, including:

* .NET
* Java
* Node.js
* Python
* Go
* PHP
* Ruby

Although Blob Storage is designed to serve different functions, we will mainly focus on two of them:
* Storing data for backup and restore, disaster recovery, and archiving.
* Storing data for analysis by an on-premises or Azure-hosted service.

<img src="https://www.dremio.com/img/explained/azure-storage/image_0.png">

Azure Blob Storage thus allows business to lower storage costs, efficiently manage blobs, and deliver large availability via an auto-scaling environment, combined with other Azure tech stacks.

## How to connect to an azure storage account us bing the azure storage explorer
First, you need to install Azure Storage Explorer if you haven't done so.
Storage explorer enablbes you to manage database without connecting to Azure portal as it inhibits the data inside the explore(blob storage, sql files, etc.)

## Current data flow for our project
There are 7 different sources we need to collect data from. Most of them have the interface that we can talk directly but there are some of them that we need to use either http call or python databricks to call the data from.
