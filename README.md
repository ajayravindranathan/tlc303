# TLC303 - Use case 1 - Customer churn prediction using XGBOOST supervised binary classification

**1. Launch Amazon Sagemaker Studio**

Amazon SageMaker Studio is a web-based, integrated development environment (IDE) for machine learning that lets you build, train, debug, deploy, and monitor your machine learning models. Studio provides all the tools you need to take your models from experimentation to production while boosting your productivity.

Here are the one-time steps for onboarding to Amazon SageMaker Studio using Quick Start:

1. Open AWS console and switch to AWS region where your Lakeformation datalake is configured.

![image](https://user-images.githubusercontent.com/81493814/142717597-4b1844a1-2f46-402d-a151-2d8989be66ce.png)


2. In the search bar, type SageMaker and click on Amazon SageMaker.

![image](https://user-images.githubusercontent.com/81493814/142717644-c502c03f-3dfb-4d56-a0d1-80ff40b11250.png)


3. Click on Amazon SageMaker Studio (first option on the left pane or orange button on the right).

<img width="1266" alt="Screenshot 2021-11-20 at 06 58 16" src="https://user-images.githubusercontent.com/81493814/142717743-8ce4ec15-1dee-49c5-83fa-aff78ed7cae4.png">

4. Leave the Quick setup option selected

<img width="868" alt="Screenshot 2021-11-20 at 07 01 12" src="https://user-images.githubusercontent.com/81493814/142717810-14725823-48a9-40ed-9b64-a2a97a1cdaab.png">

5. Select "Create new role"

<img width="840" alt="Screenshot 2021-11-20 at 07 13 02" src="https://user-images.githubusercontent.com/81493814/142718025-c53ee80b-23bf-4813-a659-bf2a12a5d1c7.png">

6. 

**2. Permit Sagemaker from Consumer account to access catalog and underlyting data**

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
