# TLC303 - UC3 - Data preparation and Feature engineering using Amazon Sagemaker Data Wrangler and Amazon Sagemaker Feature Store

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


<img width="1400" alt="Screenshot 2021-11-27 at 00 49 14" src="https://user-images.githubusercontent.com/81493814/143662945-c57ac3ad-0be2-43ea-99cc-f8db7e139026.png">


Please note that the database and the tables will not appear if the permissions were not provided correctly on LakeFormation. Also, you should be able to see only the databases and tables that you provided permissions for in the previous step.


4. In the highlighted box below, please enter the following query:

`select * from <table_name>`

<img width="1403" alt="Screenshot 2021-11-27 at 00 50 05" src="https://user-images.githubusercontent.com/81493814/143662963-a544d131-d30d-43c8-be16-129562278ffa.png">


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

<img width="1357" alt="Screenshot 2021-11-27 at 00 53 02" src="https://user-images.githubusercontent.com/81493814/143663034-f6e37ce1-12a7-4b22-a5af-66dd30f8b8e4.png">


The screen should look as follows once you have finished this successfully:

<img width="1494" alt="Screenshot 2021-11-21 at 08 38 14" src="https://user-images.githubusercontent.com/81493814/142755431-b9a4c732-6a1d-4778-834d-e053fa2d2e1c.png">


6. Let us now inspect both datasets.

Click on the plus sign next to the customer churn source as shown in the below screen shot. then click on Add analysis.

<img width="760" alt="Screenshot 2021-11-21 at 09 16 04" src="https://user-images.githubusercontent.com/81493814/142756410-17639336-9260-4e92-8b0b-039a39e246e7.png">

You will see the data from the table previewed on the bottom pane. You can now select different types of analysis from the right hand pane. These out-of-the-box analysis types have been hand picked to help with the most common data exploration activities performed by a data scientist.

We will choose histogram as the analysis type and will provide night_charge as the x-axis and churn as the y-axis. This will let us analyse how the night charge affects the customers churn propensity. 

<img width="1517" alt="Screenshot 2021-11-21 at 09 18 47" src="https://user-images.githubusercontent.com/81493814/142756476-13746aaa-6b29-4265-8249-dfa8105325af.png">

Click on preview.

The following graph should appear.

<img width="942" alt="Screenshot 2021-11-21 at 09 24 04" src="https://user-images.githubusercontent.com/81493814/142756589-0ed60122-d12b-47d3-80b6-b53eee66455d.png">

Click on save to save this analysis.

Let us try another analysis on the 5gcell data. Lets look at how the ran health index changes by location.

<img width="1511" alt="Screenshot 2021-11-21 at 09 27 28" src="https://user-images.githubusercontent.com/81493814/142756678-5e2845c8-7d71-4b44-8c44-be1c4b13c9dd.png">

7. The common theme between the 5gcell data and the customer churn data is the location field.

We will now transform the 5gcell dataset to represent the average of the following features:
5g_ran_health_index_mwc_1
5g_availability_mwc_1
5g_accessibility_mwc_1
5g_mobility_mwc_1
5g_retainability_mwc_1
5g_cell_downlink_avg_throughput_den_huaw
5g_cell_uplink_avg_throughput_den_huaw
5g_user_downlink_avg_throughput_den_huaw

These features will allow us to understand how the etwork performed over the past 6 months in a particular location. This will add further dimensions to our understanding of the circumstances under which a customer churned.

In order to add this transformation, do the following steps:

a. Click on the '+' sign next to the 5gcell dataset and click on 'Add Transform'

<img width="396" alt="Screenshot 2021-11-21 at 13 20 05" src="https://user-images.githubusercontent.com/81493814/142763506-168477d1-6eca-458e-bb02-453b2c216787.png">

b. Click on Add step

<img width="475" alt="Screenshot 2021-11-21 at 13 26 57" src="https://user-images.githubusercontent.com/81493814/142763746-33a5d0d9-1a05-42ca-a63b-61d9264c66ac.png">

c. Click on 'Custom Transform'

<img width="459" alt="Screenshot 2021-11-21 at 13 27 28" src="https://user-images.githubusercontent.com/81493814/142763759-a5445af9-9603-4072-b6aa-96be7711ad40.png">

d. Choose 'PySpark SQL'

<img width="472" alt="Screenshot 2021-11-21 at 13 31 01" src="https://user-images.githubusercontent.com/81493814/142763891-beef4608-a7a4-40dd-a7d5-2678b606ba80.png">

e. Add the following query in the empty window as shown in the screenshot.

```
select location, 
avg(5g_ran_health_index_mwc_1) as avg_5g_ran_health_index_mwc_1,
avg(5g_availability_mwc_1) as avg_5g_availability_mwc_1,
avg(5g_accessibility_mwc_1) as avg_5g_accessibility_mwc_1,
avg(5g_mobility_mwc_1) as avg_5g_mobility_mwc_1,
avg(5g_retainability_mwc_1) as avg_5g_retainability_mwc_1,
avg(5g_cell_downlink_avg_throughput_den_huaw) as avg_5g_cell_downlink_avg_throughput_den_huaw,
avg(5g_cell_uplink_avg_throughput_den_huaw) as avg_5g_cell_uplink_avg_throughput_den_huaw,
avg(5g_user_downlink_avg_throughput_den_huaw) as avg_5g_user_downlink_avg_throughput_den_huaw
from df
group by location
```

<img width="468" alt="Screenshot 2021-11-21 at 13 31 55" src="https://user-images.githubusercontent.com/81493814/142763918-b42e054e-de02-4376-8a45-42bec1a22b32.png">

f. Click on Preview

<img width="1416" alt="Screenshot 2021-11-21 at 13 37 30" src="https://user-images.githubusercontent.com/81493814/142764104-50102724-58de-449c-822d-c949b0cee575.png">

Then Click on Add

8. We will now join the customer churn data with the network performance data.

Click on the + sign besides the customer churn dataset. Then click on Join.

<img width="780" alt="Screenshot 2021-11-21 at 13 38 53" src="https://user-images.githubusercontent.com/81493814/142764147-4a75e35c-189b-40f9-b708-fa9bdf089397.png">

Choose the transformed 5gcell dataset. Outcome from previous step.

<img width="1376" alt="Screenshot 2021-11-21 at 13 41 27" src="https://user-images.githubusercontent.com/81493814/142764224-c0ddbdad-8b44-44c9-a0a6-8cb4984e6b9f.png">

9. Click on Configure

<img width="1419" alt="Screenshot 2021-11-21 at 13 42 51" src="https://user-images.githubusercontent.com/81493814/142764259-f671578a-733f-4e2c-bd6c-b0dffeb1668c.png">

10. Choose the 'Left Outer' in the Join Type and then select 'location' on the left and 'location' on the right. Click on Apply.
 
<img width="1417" alt="Screenshot 2021-11-21 at 13 44 18" src="https://user-images.githubusercontent.com/81493814/142764310-1bd6770c-bf9a-42ad-8d1e-078628aaf9f9.png">

11. The output is visible in the bottom half of the screen. The location fields are renamed as 'locaton_0' and 'location_1'

<img width="932" alt="Screenshot 2021-11-21 at 13 46 26" src="https://user-images.githubusercontent.com/81493814/142764373-acf38702-01cd-4351-b21a-601878d6c73b.png">

Click on Add.

12. Now on the Joined dataset, we will do some transformations to prepare the data set for a ML algorithm.

a. We begin by one-hot encoding the categorical columns, namely "Intl_Plan" and "vmail_plan":

Click on the + sign next to the joined dataset, Add Transform, Add Step and then choose 'Encode Categorical'

<img width="470" alt="Screenshot 2021-11-21 at 13 49 11" src="https://user-images.githubusercontent.com/81493814/142764453-56d0a06c-9854-46b0-a15e-0f495c85cf1f.png">

Choose the following options:

<img width="477" alt="Screenshot 2021-11-21 at 13 51 50" src="https://user-images.githubusercontent.com/81493814/142764549-d7d212a5-846c-4c89-9b38-aefdab3a7503.png">

Click on Preview. Then click on Add.

**Repeat the above steps for vmail_plan column as well.**

b. Next add a Custom Transform and select Python (Pandas) in order to:
 i. Replace the churn values  - True. with 1 and False. with 0
 ii. Replace the '-' in the phone number with '' to make it a number.
 iii. Add 2 columns 'FS_ID' and 'FS_time'. These columns are required in order to export the features to the feature store.
 Code block as follows:
 ```
 import time
 import pandas as pd
 
 #change True. to 1 and False. to 0
 df['churn'] = df['churn'].replace(regex=r'True.' , value='1')
 df['churn'] = df['churn'].replace(regex=r'False.' , value='0')
 df['phone'] = df['phone'].replace(regex=r'-' , value='')
 
 # Add unique ID and event time for features store
df['FS_ID'] = df.index + 1000
current_time_sec = int(round(time.time()))
df['FS_time'] = pd.Series([current_time_sec]*len(df), dtype="float64")
```
Then click first on Preview and after having verified the result, click on Add to add this transformation step to the list of all the other steps.

c. Move the FS_ID and FS_time to the start of the columns. Please use the move column transform to achieve this.

d. Drop the location_1 column as there are 2 coulmns location_0 and location_1, which are duplicates. Use the drop column transform to achieve this.

e. Drop column location_0 usingthe drop column transform.

f. We now need to vectorize the only text coloumn in the dataset as the xgboost model can work on only numerical data

Click on the + sin after the flow and click on Add transform

<img width="1344" alt="Screenshot 2021-11-27 at 02 18 05" src="https://user-images.githubusercontent.com/81493814/143665046-ebfc6cad-282d-4bff-ba3b-818adbfb8658.png">

Click on Add step

<img width="510" alt="Screenshot 2021-11-27 at 02 18 23" src="https://user-images.githubusercontent.com/81493814/143665049-7f690651-e32c-4d19-93a6-a0e23a6549bc.png">

Choose Featurize Text:

<img width="478" alt="Screenshot 2021-11-27 at 02 19 29" src="https://user-images.githubusercontent.com/81493814/143665068-8e38fade-09fb-4de5-bba8-d839739c0b57.png">


Choose Vectorize on the transform field, choose Standard tokenizer, On the input column please choose location_0, on the output format choose columns, and finally click on Preview

<img width="460" alt="Screenshot 2021-11-27 at 02 23 15" src="https://user-images.githubusercontent.com/81493814/143665205-9fefae78-c9cd-45f1-a0ef-3100b2876a88.png">

<img width="447" alt="Screenshot 2021-11-27 at 02 23 36" src="https://user-images.githubusercontent.com/81493814/143665227-4928ed54-9af8-4af6-b33d-ba8e2cb31541.png">

Click on Add.

g. Then click on Add step. Choose Manage Columns. Choose Drop columns. Choose location_0 in the columns to drop field.

<img width="465" alt="Screenshot 2021-11-27 at 02 25 05" src="https://user-images.githubusercontent.com/81493814/143665281-553a6d15-0161-4ad3-a5b3-3d9041b55da0.png">

Click on preview and then Add.

<img width="449" alt="Screenshot 2021-11-27 at 02 24 00" src="https://user-images.githubusercontent.com/81493814/143665238-367ccd4a-30a1-419a-9a3e-2c44d05914fb.png">


13. Export the featuures to the Feature Store

Click on the Export tab as shown below:

<img width="644" alt="Screenshot 2021-11-21 at 16 06 04" src="https://user-images.githubusercontent.com/81493814/142769589-4517916d-cd01-4b99-9648-6455d7e81898.png">

Click on the final step and check all the transformation steps to include in the export.

<img width="896" alt="Screenshot 2021-11-21 at 16 08 14" src="https://user-images.githubusercontent.com/81493814/142769658-143623f0-3eeb-42f4-97a5-4562f29ecf7c.png">

Click on Export Step and choose 'Save to Sagemaker Featurestore via Jupyter notebook'

<img width="439" alt="Screenshot 2021-11-21 at 16 08 58" src="https://user-images.githubusercontent.com/81493814/142769684-48befdac-38ee-4bfc-96ff-69f634ae88d6.png">

This will trigger the creation of a jupyter notebook with pre-populated code for:
1. Creation of the feature group and configuration of it
2. Creation of a processing job to extract the data from source, run all the transformations in the flow and export to the feature store.

Some configurations need to be done in this notebook to make it run:

Update the first cell with 'FS_ID' and 'FS_time' as shown below

<img width="1337" alt="Screenshot 2021-11-21 at 16 19 36" src="https://user-images.githubusercontent.com/81493814/142770132-625d584f-e231-4a1a-9761-6b058389aed6.png">

For easy reference, you can replace the code with the following code block:

```
record_identifier_feature_name = 'FS_ID'
if record_identifier_feature_name is None:
   raise SystemExit("Select a column name as the feature group record identifier.")

event_time_feature_name = 'FS_time'
if event_time_feature_name is None:
   raise SystemExit("Select a column name as the event time feature name.")
```

Next Update the following cell to switch off real-time Feature Store. Change the `True` to `None`.

<img width="1186" alt="Screenshot 2021-11-21 at 16 22 59" src="https://user-images.githubusercontent.com/81493814/142770266-42d2a36c-7160-491d-95fb-811354429319.png">

Now you can run all cells and await the completion of the Jupyter notebook. Successful completion will look like the below screen shot:

<img width="1354" alt="Screenshot 2021-11-21 at 16 24 52" src="https://user-images.githubusercontent.com/81493814/142770326-7e44c6cb-2838-4404-b047-ad5b591f222a.png">

**Congratulations!!** You have completed Feature Engineering and have your features ready to be used from the Amazon Feature Store.

Please carry on to Build, Train and Test your xgboost model by clicking the following link:

https://github.com/ajayravindranathan/tlc303/blob/main/Usecase%203-%20Build%20Train%20and%20Deploy%20the%20xgboost%20model.md
