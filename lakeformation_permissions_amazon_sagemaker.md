This section deals with providing permissions in Lake Formation to the database and the tables to Amazon Sagemaker so that the xgboost model in Sagemaker can access the catalog and the underlying data from the producer account.

1. Navigate to the home page of Amazon Sagemaker studio and copy/note the Execution role

<img width="557" alt="Screenshot 2021-11-20 at 08 47 17" src="https://user-images.githubusercontent.com/81493814/142720378-9ef8fa50-587b-4005-b771-7313d8a23944.png">

2. Navigate to Lakeformation console. Create a local database that will host the resource links of the tables that contain the data required for your machine learning model.

Click on Databases on the left hand pane

<img width="248" alt="Screenshot 2021-11-20 at 13 45 39" src="https://user-images.githubusercontent.com/81493814/142728627-0b884e12-38be-4d2f-842f-ce6f4fde3aa6.png">

Click on Create Database on the top right hand corner.

<img width="765" alt="Screenshot 2021-11-20 at 13 46 40" src="https://user-images.githubusercontent.com/81493814/142728663-a086c25a-f382-4ff8-bfe8-90ef2b23a37e.png">

Give the databse a name for example "local_tlc303" and click create.



3. Create resource links for the tlc-303 database and the 5g-cell and customer_churn tables. These tables contain the data required for your machine learning model.


Navigate to Tables on the left hand pane

<img width="244" alt="Screenshot 2021-11-20 at 13 39 13" src="https://user-images.githubusercontent.com/81493814/142728443-40407ccb-f737-4303-8626-b663cb5eedbf.png">

Select the 5gcell table from list of tables. 
<img width="1111" alt="Screenshot 2021-11-20 at 14 01 54" src="https://user-images.githubusercontent.com/81493814/142729084-09510d82-2ded-4b21-91e2-b7385828fb6a.png">

Click on Actions on the top pane and then choose "Create resource link".

<img width="164" alt="Screenshot 2021-11-20 at 13 50 31" src="https://user-images.githubusercontent.com/81493814/142728768-9a2a4563-af09-4da3-b61b-f9ebcadda7ab.png">

Provide a name and select the database created in the previous step in the database field.

<img width="692" alt="Screenshot 2021-11-20 at 13 53 08" src="https://user-images.githubusercontent.com/81493814/142728907-4a55baa6-339f-4007-ad44-05da4c008a33.png">

Click create.

**Repeat the above steps for the customer_churn table as well.**


4. Navigate to Data lake permissions on the left hand pane

<img width="250" alt="Screenshot 2021-11-20 at 13 16 22" src="https://user-images.githubusercontent.com/81493814/142727756-66587469-ba69-4544-8c4c-362a344c4556.png">


Click on Grant on the top right hand corner

<img width="1118" alt="Screenshot 2021-11-20 at 13 17 25" src="https://user-images.githubusercontent.com/81493814/142727796-51d4be5d-8552-4e84-ac6e-ce364b1cbc77.png">

Search and select the Sagemaker execution role in the IAM users and roles field. Choose Named data and catalog resources in the LF-Tags or catalog resources section. Choose the database that was created in Step 3 above in the databases field. Select the resource links that you created in step 5 in the tables field.

<img width="747" alt="Screenshot 2021-11-20 at 14 14 25" src="https://user-images.githubusercontent.com/81493814/142729518-c4679a1b-a984-45c4-92e5-700314712208.png">

Select "Select" and "Describe" as the Resource link permissions.

<img width="719" alt="Screenshot 2021-11-20 at 14 18 13" src="https://user-images.githubusercontent.com/81493814/142729628-e5e96dc3-cac9-4696-a81b-7d543eabc32d.png">

Leave All data access selected in the Data permissions section and click **Create**. 


5. Navigate to the LakeFormation console and click on "Administrative roles and tasks" on the left pane

<img width="250" alt="Screenshot 2021-11-20 at 13 04 51" src="https://user-images.githubusercontent.com/81493814/142727391-d5f19e74-4cbe-4c52-99c2-3d26f82608c4.png">

Grant database creation priviledges to the Sagemaker execution role. This is so that you can use Sagemaker Data Wrangler and Sagemaker Feature Store for the feature engineering steps in the coming section.

<img width="1112" alt="Screenshot 2021-11-20 at 13 07 52" src="https://user-images.githubusercontent.com/81493814/142727490-445a746d-76df-4d10-8fe7-b4c568d8b249.png">

On the below screen shot choose the Sagemaker execution role from the list of IAM users and roles

<img width="536" alt="Screenshot 2021-11-20 at 13 10 13" src="https://user-images.githubusercontent.com/81493814/142727601-bf04fe2c-2016-4318-81ba-62171c5e072f.png">
