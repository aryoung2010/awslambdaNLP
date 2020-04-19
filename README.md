         ___        ______     ____ _                 _  ___  
        / \ \      / / ___|   / ___| | ___  _   _  __| |/ _ \ 
       / _ \ \ /\ / /\___ \  | |   | |/ _ \| | | |/ _` | (_) |
      / ___ \ V  V /  ___) | | |___| | (_) | |_| | (_| |\__, |
     /_/   \_\_/\_/  |____/   \____|_|\___/ \__,_|\__,_|  /_/ 
 ----------------------------------------------------------------- 


# Creating a Serverless Engineering Solution to Analyze Wikipedia Snippits with Amazon Comprehend

This github repository contains code used to create Lambda functions as a part of
a serverless solution to NLP that uses AWS Cloud9, Lambda, DynamoDB, SNS, and S3 Buckets to 
analyze text with the Amazon Comprehend service.

This service allows developers to perform common NLP algorithms on text used in their
applications and tools, allowing them to incorporate text analysis as part of a
serverless workflow.

This code builds on functions created through a Pragmatic AI Lab Tutorial by Noah Gift.
I have added to the original functionality of the code by adding the functionality to 
"Detect Entities" using Amazon Comprehend, in addition to the orignal functionality that
analyzes sentiment. 

This repository is not a complete tutorial- for further information, reference
the source github by Noah Gift at https://github.com/noahgift/awslambda. There, 
you will find the tutorial where from which I created this repo. 

In brief, the architecture flow for this porject is as follows:

<img src="https://camo.githubusercontent.com/bb29cd924f9eb66730bbf7b0ed069a6ae03d2f1a/68747470733a2f2f757365722d696d616765732e67697468756275736572636f6e74656e742e636f6d2f35383739322f35353335343438332d62616537616638302d353437612d313165392d393930392d6135363231323531303635622e706e67">

The primary steps in the lab were:

### Step 1: Create an AWS Cloud9 Environment
* This allows you to create a space to work in that streamlines the integration process within AWS without having to deal with credential complications.

### Step 2: Create a DynamoDB called "fang" that stores the names of example items
* This will be the table that the "producer" Lambda function pulls from, to look up snippets of text from Wikipedia using the wikipedia package.
* This could really be a list of anything that you choose, but a list of FANG companies is used for this example.

### Step 3: Create an S3 Bucket to store the outcomes
* This is an S3 bucket to store the output tables that are created by the "consumer" Lambda function
* The output will be .csv tables with analyzed fields- "Sentiment" and "Entities" 

### Step 4: Create an SQS Queue
* This queue, called "producer", will collect the messages pulled and place them in the queue, where the "consumer" function 
will find them, process them, and store them in the S3 bucket, before deleting them. 


### Step 5: Create the "producer" and "consumer" Lambda functions
* These are available in this provided github code, simply deploy them from you Cloud9 environment
* You can then create a trigger within the Lambda Function console, to create a CloudWatch event at 
whatever time interval you designate. 

##### Happy Cloud Coding!