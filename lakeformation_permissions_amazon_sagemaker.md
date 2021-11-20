This section deals with providing permissions in Lake Formation to the database and the tables to Amazon Sagemaker so that the xgboost model in Sagemaker can access the catalog and the underlying data from the producer account.

1. Navigate to the home page of Amazon Sagemaker studio and copy the Execution role

<img width="557" alt="Screenshot 2021-11-20 at 08 47 17" src="https://user-images.githubusercontent.com/81493814/142720378-9ef8fa50-587b-4005-b771-7313d8a23944.png">

2. Navigate to the LakeFormation console and click on "Administrative roles and tasks" on the left pane

<img width="250" alt="Screenshot 2021-11-20 at 13 04 51" src="https://user-images.githubusercontent.com/81493814/142727391-d5f19e74-4cbe-4c52-99c2-3d26f82608c4.png">


3. Create resource links for the tlc-303 database and the 5g-cell and customer_churn tables. These tables contain the data required for your machine learning model.

Navigate to Tables on the left hand pane



5. Navigate to Data lake permissions on the left hand pane

<img width="250" alt="Screenshot 2021-11-20 at 13 16 22" src="https://user-images.githubusercontent.com/81493814/142727756-66587469-ba69-4544-8c4c-362a344c4556.png">

Click on Grant on the top right hand corner

<img width="1118" alt="Screenshot 2021-11-20 at 13 17 25" src="https://user-images.githubusercontent.com/81493814/142727796-51d4be5d-8552-4e84-ac6e-ce364b1cbc77.png">


3. Grant database creation priviledges to the Sagemaker execution role. This is so that you can use Sagemaker Data Wrangler and Sagemaker Feature Store for the feature engineering steps in the coming section.

<img width="1112" alt="Screenshot 2021-11-20 at 13 07 52" src="https://user-images.githubusercontent.com/81493814/142727490-445a746d-76df-4d10-8fe7-b4c568d8b249.png">

On the below screen shot choose the Sagemaker execution role from the list of IAM users and roles

<img width="536" alt="Screenshot 2021-11-20 at 13 10 13" src="https://user-images.githubusercontent.com/81493814/142727601-bf04fe2c-2016-4318-81ba-62171c5e072f.png">
