
# AWS data engineering project
<img src="https://github.com/Jira-saki/AWS-DataEngineering-Ecommerce/blob/main/image/Ecommerce%20Dataengineering.drawio.png" width="1400">

# Introduction & Goals
- Creating Data pipeline for ECOMMERCE dataset for analysis. 
- Creating data pipeline from streaming process.

- Analysis output data using BI tools

# Contents

- [The Data Set](#the-data-set)
- [Used Tools](#used-tools)
  - [Connect](#connect)
  - [Buffer](#buffer)
  - [Processing](#processing)
  - [Storage](#storage)
  - [Visualization](#visualization)
- [Pipelines](#pipelines)
  - [Stream Processing](#stream-processing)
    - [Storing Data Stream](#storing-data-stream)
    - [Processing Data Stream](#processing-data-stream)
  - [Batch Processing](#batch-processing)
  - [Visualizations](#visualizations)
- [Conclusion](#conclusion)
- [Follow Me On](#follow-me-on)





# The Data Set
- Typically e-commerce datasets are proprietary and consequently hard to find among publicly available data. However,http://archive.ics.uci.edu/ml/index.php has made this dataset containing actual transactions from 2010 and 2011. The dataset is maintained on their site, where it can be found by the title "Online Retail".


- The E-commerce dataset having 8 Columns and 541909 rows in CSV file. 

  Columns list : 
  - InvoiceNo 
  - StockCode
  - Description 
  - Quantity 
  - InvoiceDate 
  - UnitPrice 
  - CustomerID
  - Country
- The dataset had columns with a clear descripton of products and the Invoice Date which can be used to visualise the data on timely basis e.g. weekly sales, monthly sales, and quaterly sales.
- Find which product had the most sales according to specific season ,monthly revenue , quartery revenue.

# Used Tools

- Used tools of this project as follow:
  
    - API gateway
    - AWS Kinesis firehose Delivery stream
    - AWS Kinesis Data Streams
    - AWS lambda (Python3)
    - AWS glue
    - AWS S3
    - AWS Redshift
    - DynamoDB
    - AWS Athena 
    - Jupyter notebook


## Connect
  - API gateway: POST (to ingest data) 
    & GET (to send query to DynamoDB) method
## Buffer
  - AWS Kinesis Data streams
## Processing
  - AWS Kinesis firehose Delivery stream to S3 as destination. 
    
  - AWS lambda functions using Python3
    
  - AWS glue: Glue crawler and Create datacatalog in the streaming process and carry out ETL between S3 and Redshift in the batch process
## Storage
  - S3: Store raw data and transformed parquet data

  - Redshift: Store data for complex analysis and connect to Tableau or Quicksight Dashboard
    
  - DynamoDB: Store data with two tables (Customer & Invoice tables)

## Visualization
  - Tableau: Connect to redshift
  - AWS Athena : Connect to S3 (also Ad-hoc Query)
  - S3 Select

# Pipelines
- Explain the pipelines for processing that you are building
- Go through your development and add your source code

# Stream Processing
- Data ingestion: Ingest data in CSV into AWS Kinesis through API gateway

- Data cleansing: 

  - Create new lambda fuctions in AWS which can play key roles of cleaning in AWS

  - Null values changed to unknown in CustomerID: test-cleaning
  - Changing type to Parquet and timestamp: (InvoiceDate): writeToS3
  - Data nomalisation can be done if necessary for preidictive analysis or machine learning

- Data processing & Storage: Bring and send data from Kinesis to storage(S3 or Redshift) and process data
  -  Create S3 bucket in AWS
  , Add 2 folders 1. Raw folder , 2. Transformed folder 
     


  - Create a Lambda function and put down the Lambda code (writeToS3) to store new data in the S3

  - Give the Lambda roles in IAM to read kinesis and write data in S3
  - Create Dynamo DB (test-customer table)
      
        Keys: "Partition key - CustomerID (String)" and "Sort Key - InvoiceNo (String)" Columns: Country, Description, InvoiceDate, Quantity, Stockcode, UnitPrice

  - Create Dynamo DB (test-invoice table)
          
          Keys: "Partition key - InvoiceNo (String)" and "Sort Key - StockCode (String)" Columns: Country, Description, InvoiceDate, Quantity, UnitPrice




# Batch Processing

  - Create Glue Crawler to craw Raw Data in S3 Raw data Bucket for Data catalog
  - Create Glue ETL job, Clean Schemas transform data to parquet file, load into S3 transformed folder  

    
 

# Visualizations
## BI Analytics

- Quicksight dashboard can be connected to output data directly with S3, Athena, Redshift.
- Tableau dashboard can be connected with Redshift.

  

# Conclusion
- As hands-on experience on AWS Platform data engineering with free tier limitation. I have learn also how to save cost of each service.

- The data piplines established, i have learn from all the principles of data engineering  can carry out ETL process and enable to get insights through analysis

- Streaming process may causes error sometimes, need AWS SNS or cloudwatch to monitoring the updates.


# Follow Me On
Add the link to your LinkedIn Profile

