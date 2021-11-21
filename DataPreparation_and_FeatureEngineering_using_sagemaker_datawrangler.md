# TLC303 - UC1 - Data preparation and Feature engineering using Amazon Sagemaker Data Wrangler and Amazon Sagemaker Feature Store

Without good data, machine learning models are pretty much rendered powerless. Hence, data preperation is a critical step in the machine learning lifecycle.
In this section, we use the Data Wrangler module within Amazon Sagemaker to visually prepare and transform the data with the goal of preparing features that can be used by the xgboost model.

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

