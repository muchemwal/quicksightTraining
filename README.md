# Nhlane - Lidwala Data-analysis-using-AWS-services-Athena-Glue-S3-IAM-Quicksight

This is an end-to-end simple data analytics solution using AWS services. From uploading the csv file to S3 bucket to visualizing results in Quicksight.The dataset used in this project is the data science job salaries from kaggle 'kaggle.com/datasets/ruchi798/data-science-job-salaries'. 

Variables include work_year, experience_level, enployement_type, job_type, salary, salary_currency, salary_in_usd, employee_residence, remote_ratio, company_location, company_size.The data analytics process will be  done as follows:

Step 1- First, we create an IAM user to grant access permission to s3. In the search bar we type IAM > users > add users



![Logo](https://media-exp1.licdn.com/dms/image/C4D0BAQEipPlD2LXJ7A/company-logo_200_200/0/1576126564913?e=1673481600&v=beta&t=epOCv95eFzfTr1644FyVWRnWLZ9W_GP_NRqDfG1C4MI)

Step 1- First, we create an IAM user to grant access permission to s3. In the search bar we type IAM > users > add users.


1a- Set user details and access type then next permissions.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/1a.png)

1b- We proceed by choosing Copy permiisions from existing user for this training.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/1b.png)

1c-Review all the details and create user.

Step 2- S3 buckets are created. The lidwala-training-(langton) will hold the raw file, while the lidwala-training-(langton-results) will hold the query results from  Athena.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/2.png)

2a- The csv file is uploaded to the lidwala-training-langton.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/2a.png)

Step 3- Moving on to Athena. Before we can create our table we need to choose the bucket where the output query will be sent. In the Athena query editor we select settings > manage > browse s3 to choose the appropriate bucket.

3a- In Glue data catalogue, we select >create table using crawler> AWS glue crawler > add crawler to retrieve data information schema automatically.

 3a i.

 ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20i.png)
   
   ii a. Link the S3 bucket from the previous step (2) to the crawler.

 ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20ii.png)
   
   ii b. Set the classification for csv with hearder information.

 ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20classification.png)
   
   iii. Leave Sucurity to default.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20iii.png)
 

   iv. Set table Prefix to your "name_" and frequency to "On demand"

   ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20iv.png)
 
   v. Save the Crawler.

   ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20v.png)
 
   vi. Execute the crawler to create the table.

   ![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/3%20vi.png)
   

Step 4- Data query is performed in Athena, then results are loaded to lidwala-training-result.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/4%20a.png)

Step 5- Now quicksight needs to access S3 to build report. But before quicksight can read the s3 bucket, we have to make sure it has permission to do so. We navigate the account section by clicking on top right > manage quicksight > security & permissions > manage > select s3 bucket.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/5.png)

5a- Next we set up a new data source to access S3 from quicksight new analysis > new dataset > Athena >  direct query.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/5%20Athena.png)

5b- Explore QuickSight regions and use (N.Virginia) for settings.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/QuickSight%20Region.png)

6. After the data is imported, we create a report in Quicksight. Our interest was to identify top 5 popular data science salary in US based on job titlte, experience level, employment type, and remote job ratio by job title.

![iam](https://raw.githubusercontent.com/muchemwal/quicksightTraining/main/6.png)
