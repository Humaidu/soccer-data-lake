# Soccer Data Lake
# Day 3 Of 30Days DevOps Challenge

This repository contains the setup_soccer_data_lake.py script, which automates the creation of a data lake for SOCCER analytics using AWS services. The script integrates Amazon S3, AWS Glue, and Amazon Athena, and sets up the infrastructure needed to store and query NBA-related data.

# Project Overview
The setup_soccer_data_lake.py script performs the following actions:

Creates an Amazon S3 bucket to store raw and processed data.
Uploads sample SOCCER data (JSON format) to the S3 bucket.
Creates an AWS Glue database and an external table for querying the data.
Configures Amazon Athena for querying data stored in the S3 bucket.

# Prerequisites
Before running the script, ensure you have the following:

Go to Sportsdata.io and create a free account
At the top left, you should see "Developers", if you hover over it you should see "API Resources"
Click on "Introduction & Testing"

Click on "SportsDataIO API Free Trial" and fill out the information & be sure to select NBA for this tutorial

You will get an email and at the bottom it says "Launch Developer Portal"

By default it takes you to the NFL, on the left click on SOCCER

Scroll down until you see "Standings"

You'll "Query String Parameters", the value in the drop down box is your API key. 

Copy this string because you will need to paste it later in the script

IAM Role/Permissions: Ensure the user or role running the script has the following permissions:

S3: s3:CreateBucket, s3:PutObject, s3:DeleteBucket, s3:ListBucket
Glue: glue:CreateDatabase, glue:CreateTable, glue:DeleteDatabase, glue:DeleteTable
Athena: athena:StartQueryExecution, athena:GetQueryResults

# START HERE 
# Step 1: Open Visual Studio Code or your preferred text editor

# Step 2: Create the setup_soccer_data_lake.py file

2. Go to [GitHub](https://github.com/Humaidu/soccer-data-lake)

-Copy the contents of setup_soccer_data_lake.py and paste it inside the setup_soccer_data_lake.py file in your VS CODE.

3. Find the line of code under #Sportsdata.io configurations that says "api_key" 
paste your api key inside the quotations


# Step 3: Create .env file
1. Dont forget to add the .env file in your .gitignore file

2. paste the following line of code into your file, ensure you swap out with your API key
```bash
SPORTS_DATA_API_KEY=your_sportsdata_api_key
NBA_ENDPOINT=https://api.sportsdata.io/v4/soccer/scores/json/Standings/EPL/2024
```

3. Save your work


# Step 4: Run the script
1. In your terminal type;
```bash
python3 setup_soccer_data_lake.py
```
-You should see the resources were successfully created, the sample data was uploaded successfully and the Data Lake Setup Completed

# Step 5: Manually Check For The Resources
1. In the Search Bar, type S3 and click blue hyper link name

-You should see 2 General purpose bucket named "Sports-analytics-data-lake"

-When you click the bucket name you will see 3 objects are in the bucket

2. Click on raw-data and you will see it contains "nba_player_data.json"

3. Click the file name and at the top you will see the option to Open the file

-You'll see a long string of various NBA data

4. Head over to Amazon Athena and you could paste the following sample query:
```bash
SELECT Name, Games, Wins, Losses, Points, Scope
FROM Standing
WHERE ShortName = 'MUN';
```

-Click Run
-You should see an output if you scroll down under "Query Results"

### **What We Learned**
1. Securing AWS services with least privilege IAM policies.
2. Automating the creation of services with a script.
3. Integrating external APIs into cloud-based workflows.


### **Future Enhancements**
1. Automate data ingestion with AWS Lambda
2. Implement a data transformation layer with AWS Glue ETL
3. Add advanced analytics and visualizations (AWS QuickSight)

