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

<img width="836" alt="Screenshot 2021-11-20 at 08 12 08" src="https://user-images.githubusercontent.com/81493814/142719445-0f5ed7fc-d10a-4b13-a445-538e830eb7e7.png">


5. Give a name for the user profile as below.

<img width="848" alt="Screenshot 2021-11-20 at 08 04 43" src="https://user-images.githubusercontent.com/81493814/142719257-b45d1c01-cba0-4343-b7b8-94c336924411.png">


6. Select "Create new role"

<img width="846" alt="Screenshot 2021-11-20 at 08 10 12" src="https://user-images.githubusercontent.com/81493814/142719392-0eabde8a-e033-49e4-b0db-3c284e04bcf7.png">


7. Keep the default and click Create Role.

![image](https://user-images.githubusercontent.com/81493814/142718925-cf71a6d0-bac6-4dd4-a354-68dd51865abf.png)


8. You will see that the role is successfully created.

![image](https://user-images.githubusercontent.com/81493814/142718955-784fea77-ce85-4b24-ae73-c689c89e9adf.png)


9. Choose the newly created role and click Submit.

![image](https://user-images.githubusercontent.com/81493814/142718970-5bde18f6-4367-4a6d-8681-f69944213f99.png)


10. The SageMaker Studio environment will stay in **Pending** state for a few minutes.

![image](https://user-images.githubusercontent.com/81493814/142718987-8e33c530-1171-4ac5-8e62-6fd5988dc79e.png)


11. After a few minutes, the state will transition to **Ready**.

![image](https://user-images.githubusercontent.com/81493814/142719016-ba75784b-86d6-409a-ba40-1465477ce710.png)


12. Once Amazon SageMaker Studio is ready then click on Open Studio. The page can take 1 or 2 minutes to load when you access SageMaker Studio for the first time.

![image](https://user-images.githubusercontent.com/81493814/142719036-f0d23f96-63dd-4121-ac4b-3ddce6bc9e71.png)


13. You will be redirected to a new web tab that looks like this:

![image](https://user-images.githubusercontent.com/81493814/142719049-59de1a38-bdff-4ed9-ab1d-3b537c9e89b5.png)


14. Under Notebooks and compute resources, make sure that the Data Science SageMaker image is selected and click on Notebook - Python 3.

![image](https://user-images.githubusercontent.com/81493814/142719063-cc92e873-b268-458b-9743-0b43be180373.png)


15. You will land in the Untitled.ipynb notebook.

![image](https://user-images.githubusercontent.com/81493814/142719107-dede25cb-523f-4eb0-8e44-dd46afd95680.png)


16. You can rename the notebook by right clicking on the name.

![image](https://user-images.githubusercontent.com/81493814/142719135-f51183bd-019e-4a30-bf1f-af21ce462d8c.png)


**Congratulations!!** You have successfully created a SageMaker Studio domain and launched a SageMaker Studio Notebook.


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
