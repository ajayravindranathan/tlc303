# TLC303 - UC1 - Data preparation and Feature engineering using Amazon Sagemaker Data Wrangler and Amazon Sagemaker Feature Store

Without good data, machine learning models are pretty much rendered powerless. Hence, data preperation is a critical step in the machine learning lifecycle.
In this section, we use the Data Wrangler module within Amazon Sagemaker to visually prepare and transform the data with the goal of preparing features that can be used by the xgboost model.

We will use two datasets:
1. The 5gcell data, which gives us information on the network performance over a period of a few months per 5gcell. 
2. Customer churn data, which gives us historical data on each customers subscribed product features, price plans, usage and whether they churned or not.

Please follow the following steps on the Amazon Sagemaker console - 

1. Open the Sagemaker studio. On the left pane, click on the highlighted icon.

<img width="347" alt="Screenshot 2021-11-21 at 07 43 54" src="https://user-images.githubusercontent.com/81493814/142753959-3832ab68-d395-4a2b-a072-30d04bfac781.png">

Choose Data Wrangler from the drop down. Then click on new flow.

<img width="318" alt="Screenshot 2021-11-21 at 07 46 08" src="https://user-images.githubusercontent.com/81493814/142754014-3f4ee9cc-89a4-4e5b-ab1f-3af1884cf49a.png">

You can rename the newly created Flow by right-clicking on the tab. Provide any name you prefer - for example - TLC303-customerchurn.flow

<img width="340" alt="Screenshot 2021-11-21 at 07 48 48" src="https://user-images.githubusercontent.com/81493814/142754102-8e2c7a1a-48fb-4e6a-978d-4d5137a11ebb.png">


2. We will now import data using Amazon Athena as the data source. Click on Amazon Athena on the below screen.

<img width="499" alt="Screenshot 2021-11-21 at 07 48 20" src="https://user-images.githubusercontent.com/81493814/142754095-4c8c62c7-4530-45d4-90bc-8b1b11c5af52.png">


3. Select the data catalog and the database that was created in the Datamesh setup lab. You should be able to see the tables on the right hand side as below - 

<img width="1513" alt="Screenshot 2021-11-21 at 07 54 24" src="https://user-images.githubusercontent.com/81493814/142754251-a09cf878-2b7e-4bab-92e5-87517683def6.png">

Please note that the database and the tables will not appear if the permissions were not provided correctly on LakeFormation. Also, you should be able to see only the databases and tables that you provided permissions for in the previous step.


4. In the highlighted box below, please enter the following query:

`select * from <table_name>`

<img width="1509" alt="Screenshot 2021-11-21 at 08 10 46" src="https://user-images.githubusercontent.com/81493814/142754685-c40dd663-f666-4257-b45c-f59b0bc21623.png">

Unselect Enable Sampling as the data you are working with in this workshop in not too large. Sampling is checked by default assuming very large datasets (multiple GBs/TBs).

Click on Run.

Once you are able to see the results successfully, click on Import (Orange button on the top right).

<img width="409" alt="Screenshot 2021-11-21 at 08 27 32" src="https://user-images.githubusercontent.com/81493814/142755104-756c8dfd-1b6c-4cc7-92a7-2858a8cffed7.png">

Give a name for the dataset for example tlc303-5gcell and then click Add.

This will bring up the following screen where a validation process kicks off for the data being imported.

<img width="1231" alt="Screenshot 2021-11-21 at 08 30 34" src="https://user-images.githubusercontent.com/81493814/142755217-cdffd55f-d9b0-4406-aea5-190c6c3fbd4e.png">

Once validation is successful, you should see the screen as follows:

<img width="1239" alt="Screenshot 2021-11-21 at 08 30 46" src="https://user-images.githubusercontent.com/81493814/142755205-997fd3e4-70a4-40a9-a202-cfa3ace85943.png">


5. Repeat the steps in step 4 for the customer churn table as well.
The screen should look as follows once you have finished this successfully:

<img width="1494" alt="Screenshot 2021-11-21 at 08 38 14" src="https://user-images.githubusercontent.com/81493814/142755431-b9a4c732-6a1d-4778-834d-e053fa2d2e1c.png">


