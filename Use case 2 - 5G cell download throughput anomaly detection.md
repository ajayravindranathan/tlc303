# Use case 2 - 5G cell throughput anomaly detection using QuickSight ML Insights

This use case leverages the 5G cell information shared through the data mesh and uses it to do anomaly detection on the download throughput per hour. It also provides a visual way of exploring and analysing the top contributors to the anomalies.

1. Add new Dataset
Click on the Quicksight homescreen button on the top left, click on Datasets on theleft hand pane and then on Add Dataset on the top right.
<img width="929" alt="Screenshot 2021-11-26 at 13 30 43" src="https://user-images.githubusercontent.com/81493814/143588475-a8b25cd3-398a-474e-86e2-0b1f144de565.png">

2. Add new Analysis

a. Click on Athena
<img width="932" alt="Screenshot 2021-11-26 at 13 32 14" src="https://user-images.githubusercontent.com/81493814/143588654-4bbe6990-f73c-4643-9d1a-29aa048d63cf.png">

b. Give a name for the dataset as shown below and click on Create data source.
<img width="600" alt="Screenshot 2021-11-26 at 13 32 55" src="https://user-images.githubusercontent.com/81493814/143588729-5a5153c1-4d5a-4493-b084-0c81166a6afd.png">

c. Click on the usecase 2 table and then click select. The name of the usecase 2 table may be different when you run this workshop.
<img width="596" alt="Screenshot 2021-11-26 at 13 33 59" src="https://user-images.githubusercontent.com/81493814/143588851-a5138c5e-653f-477c-9048-56f7e7b2dff8.png">

d. Click on Visualize
<img width="599" alt="Screenshot 2021-11-26 at 13 34 55" src="https://user-images.githubusercontent.com/81493814/143588976-9598eb57-e317-4b2b-baa1-4377371910f8.png">

e. Lets make sure the data types on the dataset are all as we would expect them to be

Click on Edit dataset on the top of the screen as shown below:

<img width="549" alt="Screenshot 2021-11-26 at 13 37 41" src="https://user-images.githubusercontent.com/81493814/143589272-d3c19e12-6f7c-4683-92c1-9556a62f2cf3.png">

On the next screen click on the 3 dots and click on Edit
<img width="720" alt="Screenshot 2021-11-26 at 13 39 00" src="https://user-images.githubusercontent.com/81493814/143589424-c5b209df-355f-44bd-a216-89f3ef343442.png">

Change the dat
<img width="924" alt="Screenshot 2021-11-26 at 13 45 25" src="https://user-images.githubusercontent.com/81493814/143590247-298f179e-8245-4e4f-ad8f-510b210d189a.png">
