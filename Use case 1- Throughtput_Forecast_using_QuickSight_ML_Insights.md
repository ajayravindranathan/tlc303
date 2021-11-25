# TLC303 - Usecase 1 - Throughput Forecasting

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

**3. Add the dataset**

Click on Datasets on the home screen.

<img width="909" alt="Screenshot 2021-11-21 at 23 19 44" src="https://user-images.githubusercontent.com/81493814/142782885-8ecfe14a-63a7-40df-b2e4-98113a49dfde.png">

Click on New dataset

Choose Athena on the following screen

<img width="887" alt="Screenshot 2021-11-21 at 23 20 29" src="https://user-images.githubusercontent.com/81493814/142782898-92d15c12-89b3-44f9-8964-9bacee03ca27.png">

Give a name for the dataset in the Data source name field. Leave he Athen workgroup as [primary]. Click on Create data source.

<img width="600" alt="Screenshot 2021-11-21 at 23 21 04" src="https://user-images.githubusercontent.com/81493814/142782919-26b6faba-3812-46b1-985c-ea5a38c13338.png">

On the following screen choose n3_throughput and click on Select.
The database and the table will not appear if the permissions in Lakeformation have not been provided correctly.

<img width="597" alt="Screenshot 2021-11-21 at 23 22 58" src="https://user-images.githubusercontent.com/81493814/142782967-1e0f0913-87a9-4906-8784-1a4b46ddf1ee.png">

Leave the defaults on the following screen and click on Visualize

<img width="598" alt="Screenshot 2021-11-21 at 23 24 13" src="https://user-images.githubusercontent.com/81493814/142782994-72527329-9d71-4ef8-a9dc-823aef7add5a.png">

**4. Configure the dataset**

Go to datasets, click on n3_throughput, click on edit dataset

<img width="600" alt="Screenshot 2021-11-21 at 23 09 39" src="https://user-images.githubusercontent.com/81493814/142782606-88181cef-37cc-4ef9-8f96-2e2a3cd5d0ac.png">

Update the datatype of date_timestamp to Date as in the following screen shots

<img width="509" alt="Screenshot 2021-11-21 at 23 12 25" src="https://user-images.githubusercontent.com/81493814/142782708-2be50272-dc00-4a9e-891f-beb863ccafa8.png">

<img width="908" alt="Screenshot 2021-11-21 at 23 11 51" src="https://user-images.githubusercontent.com/81493814/142782685-d397c395-1516-445e-b018-bf8b7e57b6ae.png">

<img width="599" alt="Screenshot 2021-11-21 at 23 13 43" src="https://user-images.githubusercontent.com/81493814/142782736-d149e403-e336-4f08-9f76-c52841c4a307.png">

Click on Save & Visualise

**4. Configure a line graph visual analysis of the throughput against time.**

Choose line graph in the visual types.

<img width="908" alt="Screenshot 2021-11-21 at 23 32 08" src="https://user-images.githubusercontent.com/81493814/142783331-965de738-e81a-4032-be34-6a136122ac27.png">

Drag data_timestamp to x-axis and value to y-axis. Change he Aggregate to Average on the value as shown below:

<img width="902" alt="Screenshot 2021-11-21 at 23 33 49" src="https://user-images.githubusercontent.com/81493814/142783383-469b3f38-4987-402f-9bee-ea26656c1531.png">

Try changing the x-axis aggregate to hour to get a much more granular view of the variation of value(throughput).

<img width="574" alt="Screenshot 2021-11-21 at 23 35 18" src="https://user-images.githubusercontent.com/81493814/142783437-b7b52a8e-839e-4701-ad62-cfab49002487.png">

**5. Configure the ML driven forecast**
  **a. Graph**
  
  Click on the three dots and then click on Add Forecast.
  
  <img width="604" alt="Screenshot 2021-11-21 at 23 37 47" src="https://user-images.githubusercontent.com/81493814/142783548-342020cc-27ea-4620-b26e-7644f8b90732.png">

This should immediately bring up the forecast as shown below.

<img width="550" alt="Screenshot 2021-11-21 at 23 38 29" src="https://user-images.githubusercontent.com/81493814/142783574-1680b5ca-40a4-4396-9098-24372b6dc562.png">

To view the forecast at a granularity of 1 day, please slide the bar on the x-axis closer to the current date.

<img width="556" alt="Screenshot 2021-11-21 at 23 40 21" src="https://user-images.githubusercontent.com/81493814/142783651-ba2699b7-1a34-499b-a526-92e38a333efa.png">


  **b. Narrative insight**

To add a narative insight, click on Add on the top let corner and choose Add Insight

<img width="188" alt="Screenshot 2021-11-21 at 23 41 02" src="https://user-images.githubusercontent.com/81493814/142783693-ece70fa5-72ea-4cdb-9913-389280eafe4f.png">

Choose Forecast on the computation type

<img width="599" alt="Screenshot 2021-11-21 at 23 42 06" src="https://user-images.githubusercontent.com/81493814/142783726-cb56d469-ca37-4442-ab5e-0f65a12fb27f.png">

Add data_timestamp and value as dimensions by dragging and dropping them on the Insight window.
By default, the aggregate for the value field comes up as Sum.

<img width="901" alt="Screenshot 2021-11-21 at 23 43 49" src="https://user-images.githubusercontent.com/81493814/142783782-99a155b4-2bd3-4172-a89a-7c0ca27703be.png">

Change the aggregate to Average

<img width="565" alt="Screenshot 2021-11-21 at 23 45 24" src="https://user-images.githubusercontent.com/81493814/142783821-8245c3b5-b7c8-4927-b5a2-ed778a14edca.png">

This comes up with a narrative forecast as follows:

<img width="555" alt="Screenshot 2021-11-21 at 23 45 52" src="https://user-images.githubusercontent.com/81493814/142783836-988151b7-e369-462b-a43d-ef8418ddfbca.png">

**Congratulations!!** You have now been able to forecast the average throughtput on the n3 interface using Amazon Quicksight ML insights. As you see you have been able to do this without needing to do any data preparation or feature engineering or training and testing an ML model. This demonstrates how the power of pre-trained Random cut forest ML models has been placed in the hands of everyday BI users.
