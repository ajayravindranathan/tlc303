# TLC303 - Usecase 2 - Throughput Forecasting

The 5G N3 interface performs the role of conveying user data from the RAN to the User Plane Function, making it possible to create both low- and high-latency services. The throughput of the N3 interface is a key measure when it comes to a 5G network and it is important to forecast any bottlenecks on this interface.

This use case shows how we can use the n3_thorughput data published by a producer on a consumer account that requires to forecast and take actions based on the outcome of the forecast.

By using QuickSight ML powered insights, we demonstrate how this functionality can be achieved with minimal machine learning knowledge.

The steps involved in this use case are as follows:

**1. Launch a Quicksight account**

On the search bar on the AWS Console, search for QuickSight

<img width="699" alt="Screenshot 2021-11-21 at 21 35 27" src="https://user-images.githubusercontent.com/81493814/142779814-9b1c529a-4680-485a-bd28-a4427416956f.png">

Click on QuickSight

Click on Sign up for QuickSight

<img width="844" alt="Screenshot 2021-11-21 at 21 33 51" src="https://user-images.githubusercontent.com/81493814/142779752-1eae0d53-fbbb-4aed-a28b-000c6d67283c.png">

Leave the Enterprise option selected and click on Continue

Provide an Account name and a Notification email address.

<img width="895" alt="Screenshot 2021-11-21 at 21 38 49" src="https://user-images.githubusercontent.com/81493814/142779920-7a81fbc7-d17a-4e1a-86c4-eb1b76c635cc.png">

In addition to the services selected by default in the "Allow access and autodiscovery for these resources" section, please select S3 and then select all buckets.

<img width="774" alt="Screenshot 2021-11-21 at 21 42 14" src="https://user-images.githubusercontent.com/81493814/142779992-b0de3409-ef47-478f-abc1-67cadb3f55d0.png">

**2. Provide permissions to the Quicksight user to access the catalog and database**

Find the Amazon QuickSight user ARN

Navigate to the Amazon console and click on the CloudShell button to initiate a CloudShell session.

<img width="899" alt="Screenshot 2021-11-21 at 21 54 35" src="https://user-images.githubusercontent.com/81493814/142780304-5249829b-a252-4a71-b2d1-49fc5acff9c6.png">

Once the CloudShell environment is instantiated and you get the prompt, enter the following command. Please ensure to swap the account id with your account id.

`aws quicksight list-users --aws-account-id <account_id> --namespace default --region us-east-1`

This command should return an output similar to the following screenshot.

<img width="784" alt="Screenshot 2021-11-21 at 21 52 15" src="https://user-images.githubusercontent.com/81493814/142780250-49ab8f3c-eb77-4392-9961-22b3360f493d.png">

Copy the ARN of the user

<img width="785" alt="Screenshot 2021-11-21 at 21 58 24" src="https://user-images.githubusercontent.com/81493814/142780406-856f44a4-18d6-40d1-9b1c-e18d87fb79ae.png">

**2. Provide the LakeFormation permissions to the QuickSight user**

Navigate to LakeFormation console and click on Datalake permissions.

Click on Grant
<img width="619" alt="Screenshot 2021-11-21 at 22 01 11" src="https://user-images.githubusercontent.com/81493814/142780509-13fec016-70fa-4003-8c31-a98412802eb3.png">

<img width="575" alt="Screenshot 2021-11-21 at 22 01 28" src="https://user-images.githubusercontent.com/81493814/142780514-958b930f-a517-4f61-9d8c-67c730eee9aa.png">



**3. Configure the dataset**

**4. Configure a line graph visual analysis of the throughput against time.**

**5. Configure the ML driven forecast**
  **a. Graph**
  **b. Narrative insight**
