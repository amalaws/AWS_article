---
title: "🤷‍♂️What is Athena and How to Create Table in AWS Athena ?"
datePublished: Fri Jan 24 2025 05:28:41 GMT+0000 (Coordinated Universal Time)
cuid: cm6abn5bt000t09iegktb4fhb
slug: what-is-athena-and-how-to-create-table-in-aws-athena
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737696450733/90b9945c-9186-41b6-a4a2-4fa32f8d7294.jpeg
tags: cloud, linux, aws, learning, cloud-computing, devops

---

**AWS Athena is a powerful and useful tool that allows users to analyze data stored in Amazon S3 using SQL. One of the most important step to use Athena is creating the table to organize the data and query it to get the desired results. In this article we will see how to create the table in aws Athena.**

## **👉What is AWS Athena?**

[**AWS Athena**](https://www.geeksforgeeks.org/aws-athena/) is a serverless query service tool provided by [**Amazon Web Services (AWS)**](https://www.geeksforgeeks.org/aws-tutorial/) that allows users to analyze the data stored in [**Amazon S3**](https://www.geeksforgeeks.org/introduction-to-aws-simple-storage-service-aws-s3/) using SQL. It can also be used for large scale data sets and we don't need to worry about managing the underlying infrastructure; it automatically handles configuration and software updates. Athena doesn't require a complex [**ETL (Extract, Transform, Load)**](https://www.geeksforgeeks.org/etl-process-in-data-warehouse/) process, so users with basic [**SQL**](https://www.geeksforgeeks.org/sql-tutorial/) skills can also use it at ease. In Athena we can also create tables and databases and the location of the data set is in S3 Also, the query results will be stored in S3. Athena supports various data formats like CSV (comma-separated values), JSON (JavaScript Object Notation), Parquet, etc.. Also, Athena is great for running quick queries and generating the required information from the data you want to analyze.

## Amazon Simple Storage Service (S3)

**Amazon S3 is a cloud based storage service that allows users to store and retrieve large amounts of data like images, videos, documents on the internet. In this particular article, we use S3 for uploading the data set where we need to run our query and store the results of that particular query.**

## **Pre-requisites**

* [**AWS Account**](https://www.geeksforgeeks.org/amazon-web-services-aws-free-tier-account-set-up/)
    
* **Knowledge on AWS services.**
    

## **Steps to Create Table in AWS Athena**

### **Step 1:** Creating S3 bucket.

* Head to the [**AWS console**](https://aws.amazon.com/console/) and we need to create the S3 bucket where we upload the data base file, which we need to run the query at the later point.
    
* On the home page navigate to the search bar and type S3 and open the first one as shown below and you will be redirected to the home page.
    

![Creating S3 bucket.](https://media.geeksforgeeks.org/wp-content/uploads/20240526111139/article-1-(1).png align="left")

* Click on create bucket and name your bucket as you like and go to the bottom of the page and click on [**'Create bucket'**](https://www.geeksforgeeks.org/amazon-s3-creating-a-s3-bucket/) as shown below.
    

![create bucket](https://media.geeksforgeeks.org/wp-content/uploads/20240531134059/image-(5)-(1)-(1).png align="left")

### **Step 2:** Uploading files to S3 bucket

* After you have successfully created the S3 bucket we need to upload the data on which we need to run queries using Athena in the CSV format.
    
* Click on upload as shown below and click o add files and upload the data from your local system and scroll to the bottom of the page and click on upload.
    

![Uploading files to S3 bucket](https://media.geeksforgeeks.org/wp-content/uploads/20240526112342/image-(3)-(1)-(1).png align="left")

### **Step 3:** Creating the destination bucket

* If you are using the Athena for the first time we need to create an additional bucket where it stores the query results. Follow the same above mentioned steps to create a bucket and now we can see there are two buckets as shown below.
    

### **Step 4:** Navigating to Athena

* Now head to the search bar and type Athena open the first one and you will be navigated to the home page of Athena as shown below.
    

![Navigating to Athena](https://media.geeksforgeeks.org/wp-content/uploads/20240526112514/article-5-(1).png align="left")

* And on the right side of your screen under get started for now I have opted for 'Query your data with Trion SQL' and you can choose according to your requirement and click on 'Launch query editor'.
    

### Step 5: Managing the settings

* If you are using Athena for the first time we need to make some changes to make sure that query results are stored in the bucket which we have created earlier. To do that go to the settings tab on the Athena home page as shown below.
    

![ Managing the settings ](https://media.geeksforgeeks.org/wp-content/uploads/20240526112622/article-6-(1).png align="left")

* On the settings tab click on 'M**anage'** at the right corner and you will be redirected to the tab where we need to add the S3 bucket. Click on **'Browse S3'** and choose the bucket name as shown below in which you want to store the query results.
    

### **Step 6:** Creating Table

* Now come to the Editor tab and under table and views section click on create and choose [**'S3 bucket data'**](https://www.geeksforgeeks.org/how-to-store-data-in-a-s3-bucket/) as shown below and you will be redirected to the page where you need to create the table and mange the settings.
    
* Under the table details give the table name as you wish and you can give the description about the table if you need to explain some information about that table. And under the **'Database configuration'** section if you are first time user you need to create a database and enter the name for it. Under column details we need enter the column and their type according to the dataset as shown below.
    

* Lastly under the **'Dataset'** we need to select the bucket which we have created and uploaded the CSV file. And scroll to the bottom and click on **'Create table'** as shown below.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737696106842/05972676-6ce0-43b4-8cc2-0ca094a25470.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737696071323/eefb119a-8279-4515-93bf-ca5199e121ce.jpeg align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737696305024/9af8b299-01b6-4b1c-a79a-2bf613c691c9.png align="center")
    

### **Step 7:** Successfully Created table

* And finally we can see the table with name has been created .
    

## Conclusion

AWS Athena is a powerful and serverless query service that enables users to analyze large datasets directly in Amazon S3 using standard SQL and stores the result in the S3 bucket. It can be easily integrated with S3 allowing users to query structured, and unstructured data in various formats like [**CSV, JSON**](https://www.geeksforgeeks.org/difference-between-json-and-csv/) etc..