# TLC303 - Use case 1 - Customer churn prediction using XGBOOST supervised binary classification

This use case involves the following steps as listed below. Please browse to the respective readme files for each step and execute the steps in the specfied order below.

**1. Launch Amazon Sagemaker Studio**

https://github.com/ajayravindranathan/tlc303/blob/main/Launch_Amazon_Sagemaker.md

**2. Permit Sagemaker in the Consumer account to access catalog and underlyting data**

https://github.com/ajayravindranathan/tlc303/blob/main/lakeformation_permissions_amazon_sagemaker.md


**3. Feature Engineering and feature export to Sagemaker Feature Store using Amazon Sagemaker Data Wrangler**

https://github.com/ajayravindranathan/tlc303/blob/main/DataPreparation_and_FeatureEngineering_using_sagemaker_datawrangler.md

**6. Build, Train and Test your xgboost model**

Info : If you would like to just browse through the code in the jupyter notebook, the below link shows the Amazon Sagemaker notebook you will be using: https://github.com/ajayravindranathan/tlc303/blob/main/TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

The actual steps to perform are as follows:

  1. Open a new terminal window on Sagemaker Studio

  <img width="300" alt="Screenshot 2021-11-18 at 11 35 19" src="https://user-images.githubusercontent.com/81493814/142408102-6aa35aee-6f9d-4a2c-959f-ada090377fa9.png">

  2. Paste the command  - `git clone https://github.com/ajayravindranathan/tlc303.git`

  3. Open the TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

  4. Ensure that the Python 3 Data science Kernel has been allocated and you have the ml.t3.medium instance allocated with 2        vCPU + 4 GiB memory. In order to confirm this, the top right hand corner of your Sagemaker notebook window should look as      in the below screenshot.

<img width="407" alt="Screenshot 2021-11-18 at 11 47 24" src="https://user-images.githubusercontent.com/81493814/142409787-e9e31b09-1d9b-4e8b-863c-fd857ce79a5f.png">

  5. Update the feature group name with the name of the feature group created in the previous step. You can check the name of the feature group on the Sagemaker Studio console as shown in the screen shots below:
 
 <img width="466" alt="Screenshot 2021-11-21 at 16 35 50" src="https://user-images.githubusercontent.com/81493814/142770712-d527f708-f9ab-4ff8-90c5-d6770fda08ff.png">
 
 <img width="1392" alt="Screenshot 2021-11-21 at 16 36 19" src="https://user-images.githubusercontent.com/81493814/142770732-dcaf1e5c-54be-4011-be73-3ddfdf214ba1.png">


Update this cell in the xgboost model notebook:

<img width="1177" alt="Screenshot 2021-11-21 at 16 38 20" src="https://user-images.githubusercontent.com/81493814/142770818-a89b00b5-bb2d-4f69-a4a2-83f410798dbb.png">

  7. Follow along the steps in the Sagemaker notebook. Enjoy!

You should see an output something like this at the end of the 'Evaluation' section if your execution was successful.

<img width="1310" alt="Screenshot 2021-11-21 at 16 40 04" src="https://user-images.githubusercontent.com/81493814/142770891-05321c7c-37dc-44f6-85ae-a1a6a1d68030.png">

The rest of the notebook is optional.

**Congratulations!!** You have now trained, tested and evaluated a binary classification model to predict customer churn using network and customer data.
