# TLC303 - Use case 3 - Grant required permissions to Amazon Sagemaker using AWS LakeFormation

This section deals with providing permissions in Lake Formation to the database and the tables to Amazon Sagemaker so that the xgboost model in Sagemaker can access the catalog and the underlying data from the producer account.

1. Navigate to the home page of Amazon Sagemaker studio and copy/note the Execution role

<img width="557" alt="Screenshot 2021-11-20 at 08 47 17" src="https://user-images.githubusercontent.com/81493814/142720378-9ef8fa50-587b-4005-b771-7313d8a23944.png">

On the Services search bar, search for IAM and open it in a new tab

Click on Roles on the left pane.

Search for the Amazon Sagemaker execution role noted in step 1.

<img width="1914" alt="Screenshot 2021-11-27 at 00 26 27" src="https://user-images.githubusercontent.com/81493814/143662418-7555c0ff-18a2-4ed1-b042-03846463af02.png">


Click on the role.

Click on add in-line policy on the right.

<img width="1600" alt="Screenshot 2021-11-27 at 00 27 03" src="https://user-images.githubusercontent.com/81493814/143662427-ed6eebf0-e2bc-4ef2-9752-8459b8b128af.png">


Click on JSON tab 

<img width="1294" alt="Screenshot 2021-11-27 at 00 27 48" src="https://user-images.githubusercontent.com/81493814/143662436-f22c0cce-3916-4c61-ba1d-f6a71a4386aa.png">


Replace json in the box with the json shown below:

```{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "lakeformation:GetResourceLFTags",
                "glue:SearchTables",
                "glue:GetDatabase",
                "lakeformation:SearchDatabasesByLFTags",
                "glue:GetTables",
                "lakeformation:GetDataAccess",
                "glue:GetPartitions",
                "lakeformation:SearchTablesByLFTags",
                "lakeformation:ListLFTags",
                "lakeformation:GetLFTag",
                "glue:GetDatabases",
                "glue:GetTable",
                "glue:CreateDatabase"
            ],
            "Resource": "*"
        }
    ]
}
```
Click on review policy.


Name the policy SagemakerLakeFormationPolicy. Click on Create Policy. The policy should now appear in the list of policies on the role.

<img width="1610" alt="Screenshot 2021-11-27 at 00 33 43" src="https://user-images.githubusercontent.com/81493814/143662583-cc49896b-6269-47a3-884f-6f270de30916.png">





2. Navigate to Lakeformation console. Navigate to Databases on the left hand pane


<img width="926" alt="Screenshot 2022-05-11 at 04 40 02" src="https://user-images.githubusercontent.com/81493814/167819695-ae86531c-4915-4f02-a501-030a48c48811.png">


Select the resource link, which is the row in Italics. Then click on Actions -> Grant on the top right hand corner

<img width="1011" alt="Screenshot 2022-05-11 at 04 41 49" src="https://user-images.githubusercontent.com/81493814/167820047-a5f6565a-4013-4bf7-8422-4b92712dc86e.png">


Search and select the Sagemaker execution role in the IAM users and roles field. 

Select the tables for use case 3 usecase3_a_customer_churn_prediction and usecase3_b_customer_churn_prediction in the Tables field.


<img width="729" alt="Screenshot 2022-05-11 at 04 46 02" src="https://user-images.githubusercontent.com/81493814/167820856-d44d02f2-b7d8-42cd-965b-952eb061d13f.png">

<img width="930" alt="Screenshot 2021-11-27 at 00 39 45" src="https://user-images.githubusercontent.com/81493814/143662718-b652b814-2bf5-478d-bde6-02a1f44df92e.png">

<img width="1117" alt="Screenshot 2022-05-11 at 04 36 46" src="https://user-images.githubusercontent.com/81493814/167819080-ab0f363c-00d2-405f-b88a-00a8572a0787.png">


Select "Select" and "Describe" as the Table permissions.

<img width="830" alt="Screenshot 2021-11-27 at 00 41 47" src="https://user-images.githubusercontent.com/81493814/143662745-8b1c1685-9b67-4242-8108-c9b96c35f3b0.png">

Click on Grant.


5. Navigate to the LakeFormation console and click on "Administrative roles and tasks" on the left pane

<img width="250" alt="Screenshot 2021-11-20 at 13 04 51" src="https://user-images.githubusercontent.com/81493814/142727391-d5f19e74-4cbe-4c52-99c2-3d26f82608c4.png">

Grant database creation priviledges to the Sagemaker execution role. This is so that you can use Sagemaker Data Wrangler and Sagemaker Feature Store for the feature engineering steps in the coming section.

<img width="1112" alt="Screenshot 2021-11-20 at 13 07 52" src="https://user-images.githubusercontent.com/81493814/142727490-445a746d-76df-4d10-8fe7-b4c568d8b249.png">

On the below screen shot choose the Sagemaker execution role from the list of IAM users and roles

<img width="536" alt="Screenshot 2021-11-20 at 13 10 13" src="https://user-images.githubusercontent.com/81493814/142727601-bf04fe2c-2016-4318-81ba-62171c5e072f.png">

Click on Grant.

**Congratulations!!** You have now provided the required permissions for Sagemaker to ingest data, run feature engineering tasks, train and test the model, and finally deploy a real-time endpoint for inference. 

Proceed to step 3 by clicking on the following link:

https://github.com/ajayravindranathan/tlc303/blob/main/Usecase%203%20-%20DataPreparation_and_FeatureEngineering_using_sagemaker_datawrangler.md

