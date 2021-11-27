# Build, Train and Deploy an XGBOST binary classification model

Info : If you would like to just browse through the code in the jupyter notebook, the below link shows the Amazon Sagemaker notebook you will be using: https://github.com/ajayravindranathan/tlc303/blob/main/TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

The actual steps to perform are as follows:

  1. Open a new terminal window on Sagemaker Studio

  <img width="300" alt="Screenshot 2021-11-18 at 11 35 19" src="https://user-images.githubusercontent.com/81493814/142408102-6aa35aee-6f9d-4a2c-959f-ada090377fa9.png">

  2. Paste the command  - `git clone https://github.com/ajayravindranathan/tlc303.git`

  3. Open the TLC303-CustomerChurnPrediction-FeatureStore-XGBoost.ipynb

  4. Ensure that the Python 3 Data science Kernel has been allocated and you have the ml.t3.medium instance allocated with 2        vCPU + 4 GiB memory. In order to confirm this, the top right hand corner of your Sagemaker notebook window should look as      in the below screenshot.

<img width="407" alt="Screenshot 2021-11-18 at 11 47 24" src="https://user-images.githubusercontent.com/81493814/142409787-e9e31b09-1d9b-4e8b-863c-fd857ce79a5f.png">

If in case this does not come up automatically, then follow these steps:

Click on Edit and then choose Select all cells.

<img width="306" alt="Screenshot 2021-11-27 at 01 24 20" src="https://user-images.githubusercontent.com/81493814/143663913-51eae900-82e1-4635-aa05-1855307cdb1c.png">


Then click on Edit and select Copy Cells.

<img width="292" alt="Screenshot 2021-11-27 at 01 25 27" src="https://user-images.githubusercontent.com/81493814/143663936-3e256c44-4def-4663-8f27-41fb2d106622.png">


Navigate to the empty notebook you created in step 1 of this use case. Then click on Edit and then Paste cells below:

<img width="1853" alt="Screenshot 2021-11-27 at 01 26 35" src="https://user-images.githubusercontent.com/81493814/143663969-c0884a89-2f7b-4a2a-a2fc-8f37d8eef908.png">


  5. Update the feature group name with the name of the feature group created in the previous step. You can check the name of the feature group on the Sagemaker Studio console as shown in the screen shots below:
 
 <img width="466" alt="Screenshot 2021-11-21 at 16 35 50" src="https://user-images.githubusercontent.com/81493814/142770712-d527f708-f9ab-4ff8-90c5-d6770fda08ff.png">
 
 <img width="1392" alt="Screenshot 2021-11-21 at 16 36 19" src="https://user-images.githubusercontent.com/81493814/142770732-dcaf1e5c-54be-4011-be73-3ddfdf214ba1.png">


Update this cell in the xgboost model notebook:

<img width="1177" alt="Screenshot 2021-11-21 at 16 38 20" src="https://user-images.githubusercontent.com/81493814/142770818-a89b00b5-bb2d-4f69-a4a2-83f410798dbb.png">

  7. Run the cells from the first cell in your Sagemaker notebook one by one by using Shift+Enter on your keyboard . 
 
 All cells have descriptive explanation as to what is happening in each cell. Enjoy!

You should see an output something like this at the end of the 'Evaluation' section if your execution was successful.

<img width="1310" alt="Screenshot 2021-11-21 at 16 40 04" src="https://user-images.githubusercontent.com/81493814/142770891-05321c7c-37dc-44f6-85ae-a1a6a1d68030.png">

The rest of the notebook is optional.
