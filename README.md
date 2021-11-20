# TLC303 - Use case 1 - Customer churn prediction using XGBOOST supervised binary classification

**1. Launch Amazon Sagemaker Studio**

Please follow the instructions in the below link:
https://github.com/ajayravindranathan/tlc303/blob/main/Launch_Amazon_Sagemaker.md

**2. Permit Sagemaker from Consumer account to access catalog and underlyting data**

Please follow the instructions in the below link:
https://github.com/ajayravindranathan/tlc303/blob/main/lakeformation_permissions_amazon_sagemaker.md


**3. Ingest data using Sagemaker Data Wrangler**

**4. Feature Engineering**

**5. Export features to Sagemaker Feature Store**

**6. Build, Train and Test your xgboost model**

Info : The below link shows the Amazon Sagemaker notebook you will be using:
https://github.com/ajayravindranathan/tlc303/blob/main/TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

1. Open a new terminal window on Sagemaker Studio

<img width="300" alt="Screenshot 2021-11-18 at 11 35 19" src="https://user-images.githubusercontent.com/81493814/142408102-6aa35aee-6f9d-4a2c-959f-ada090377fa9.png">

2. Paste the command  - `git clone https://github.com/ajayravindranathan/tlc303.git`

3. Open the TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

4. Ensure that the Python 3 Data science Kernel has been allocated and you have the ml.t3.medium instance allocated with 2 vCPU + 4 GiB memory. In order to confirm this, the top right hand corner of your Sagemaker notebook window should look as in the below screenshot.

<img width="407" alt="Screenshot 2021-11-18 at 11 47 24" src="https://user-images.githubusercontent.com/81493814/142409787-e9e31b09-1d9b-4e8b-863c-fd857ce79a5f.png">

5. Follow along the steps in the Sagemaker notebook. Enjoy!
