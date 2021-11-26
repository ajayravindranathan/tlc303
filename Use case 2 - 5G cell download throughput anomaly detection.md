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

f. Click on Edit dataset on the top of the screen as shown below:

<img width="549" alt="Screenshot 2021-11-26 at 13 37 41" src="https://user-images.githubusercontent.com/81493814/143589272-d3c19e12-6f7c-4683-92c1-9556a62f2cf3.png">


g. On the next screen click on the 3 dots and click on Edit

<img width="720" alt="Screenshot 2021-11-26 at 13 39 00" src="https://user-images.githubusercontent.com/81493814/143589424-c5b209df-355f-44bd-a216-89f3ef343442.png">



h. Change the date_extracted column data type to date.

<img width="924" alt="Screenshot 2021-11-26 at 13 45 25" src="https://user-images.githubusercontent.com/81493814/143590247-298f179e-8245-4e4f-ad8f-510b210d189a.png">



i. Next click on the Date data type on the Date_extracted column and click on Edit date format.

<img width="291" alt="Screenshot 2021-11-26 at 23 12 08" src="https://user-
images.githubusercontent.com/81493814/143660478-81ba646c-49c4-4e22-8a29-366bd3d5681f.png">


j. Update the date format as shown in the screen shot below:

<img width="593" alt="Screenshot 2021-11-26 at 23 13 12" src="https://user-images.githubusercontent.com/81493814/143660516-3bad694e-d638-429e-92ea-d0664db207d7.png">


k. Click on **Publish & Visualize** on the top right corner


3. Create a line graph for the 

a. Click on Visualize on the left hand pane


b. Cick on Line graph on the line graph visual type in the visual types section

<img width="259" alt="Screenshot 2021-11-26 at 23 18 01" src="https://user-images.githubusercontent.com/81493814/143660663-b1b44a16-876c-4276-8b3d-116a71daa157.png">


c. Drag Date extracted on the x-axis and 5g_downlink_traffic_volume_huaw on the y-axis

<img width="805" alt="Screenshot 2021-11-26 at 23 22 06" src="https://user-images.githubusercontent.com/81493814/143660792-558d40d6-0a66-4209-a32e-9fab7653ae9b.png">


d. Click on the chevron icon on the top right to pull down the field wells

<img width="1590" alt="Screenshot 2021-11-26 at 23 22 46" src="https://user-images.githubusercontent.com/81493814/143660804-f6cd8569-2ffa-4c1f-a402-31f2774b4e74.png">


e. Change the aggregate for date_extracted to hours

<img width="940" alt="Screenshot 2021-11-26 at 23 23 56" src="https://user-images.githubusercontent.com/81493814/143660845-130e0311-83d7-4ae9-9ccc-f3a13ec24011.png">


f. Change the aggregate for the value field well(5g_downlink_traffic_volume_huaw) to average

<img width="863" alt="Screenshot 2021-11-26 at 23 25 18" src="https://user-images.githubusercontent.com/81493814/143660872-6aa8aa88-4896-45ac-900a-61ae124d51c3.png">


g. The resulting graph should look like the below

<img width="775" alt="Screenshot 2021-11-26 at 23 25 39" src="https://user-images.githubusercontent.com/81493814/143660881-c22819c4-7041-4084-94f5-e3af6f8558b5.png">



4. Configure anomaly detection for this kpi.


a. Click on Add and then Add Insight (Top left)

<img width="198" alt="Screenshot 2021-11-26 at 23 26 30" src="https://user-images.githubusercontent.com/81493814/143660897-4a826160-efdd-43b1-9802-aa8a6bdc159e.png">


b. Choose Anomaly detection and then click on Select

<img width="617" alt="Screenshot 2021-11-26 at 23 27 17" src="https://user-images.githubusercontent.com/81493814/143660919-f0ea4c06-e4ea-4380-a087-fa14f64c75ca.png">


c. Drag Date Extracted, change its aggregate to hours and then drag 5g_downlink_traffic_volume_huaw and change its aggregate to average, select cellname_nrcell on the categories field

<img width="890" alt="Screenshot 2021-11-26 at 23 29 46" src="https://user-images.githubusercontent.com/81493814/143660991-ffadb511-ced6-4e46-b115-e60d9f1199af.png">


d. Click on Get started on the Insights pane.

The should bring up the following screen shown below

<img width="1904" alt="Screenshot 2021-11-26 at 23 31 39" src="https://user-images.githubusercontent.com/81493814/143661043-ce8eea11-332b-4d43-aa93-5fa9d4948023.png">


e. The bue dot shows the anomaly in the preview.

f. Next pick all 4 fields on the Top contributorsfield as shown in the following screen shot:

<img width="1892" alt="Screenshot 2021-11-26 at 23 32 20" src="https://user-images.githubusercontent.com/81493814/143661065-df49ee20-1f1c-4f18-8ad1-803a93125363.png">


g. You can also select the different cells to see the anomaly detection preview and top contributors change for that particular cell.

<img width="1036" alt="Screenshot 2021-11-26 at 23 34 04" src="https://user-images.githubusercontent.com/81493814/143661107-0e1f3db4-7432-472c-9904-371ad3bb6b0c.png">


h. Select all in the cellname_nrcell field once done and then click on Save at the top right. On the next screen click on Run now.

<img width="779" alt="Screenshot 2021-11-26 at 23 36 27" src="https://user-images.githubusercontent.com/81493814/143661161-4cae4552-577a-41ef-9c25-554974b18e58.png">


i. This will take about 3min to run. The following screen should appear after it finishes processing. Click on Explore Anmalies.

<img width="782" alt="Screenshot 2021-11-26 at 23 39 45" src="https://user-images.githubusercontent.com/81493814/143661242-2d1fd8fc-6370-48ca-b048-3a867192502d.png">

j. This will bring up the following screen with a zoomed in view to the anomalous data against the timeline, showing the top contributors on the left hand pane.

<img width="959" alt="Screenshot 2021-11-26 at 23 40 41" src="https://user-images.githubusercontent.com/81493814/143661256-ff80096b-9fdc-4457-a7b4-8bfb8b670dad.png">


k. You can drop the field well from the top to explore the configuration options available to see different controls available.

<img width="1656" alt="Screenshot 2021-11-26 at 23 44 32" src="https://user-images.githubusercontent.com/81493814/143661397-1d41458a-f490-4a76-aa9f-85c35f5bc220.png">


If you are feeling adventurous, you can switch the y-axis for other columns on the insight and check how other features behave and find anomalies in those.

**Congratulations!! you have completed the anomaly detection use case on 5g cell data. **

