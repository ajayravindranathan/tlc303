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





2. Navigate to Lakeformation console. Navigate to Data lake permissions on the left hand pane

<img width="250" alt="Screenshot 2021-11-20 at 13 16 22" src="https://user-images.githubusercontent.com/81493814/142727756-66587469-ba69-4544-8c4c-362a344c4556.png">


Click on Grant on the top right hand corner

<img width="1118" alt="Screenshot 2021-11-20 at 13 17 25" src="https://user-images.githubusercontent.com/81493814/142727796-51d4be5d-8552-4e84-ac6e-ce364b1cbc77.png">

Search and select the Sagemaker execution role in the IAM users and roles field. Choose Named data and catalog resources in the LF-Tags or catalog resources section. Choose the database that was created by the datamesh scripts.

Select the tables for use case 3 usecase3_5gcell and usecase3_customerchurn in the Tables field.

<img width="930" alt="Screenshot 2021-11-27 at 00 39 45" src="https://user-images.githubusercontent.com/81493814/143662718-b652b814-2bf5-478d-bde6-02a1f44df92e.png">



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
