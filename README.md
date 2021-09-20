# Forecast Future Sales 

Source: Analytics Vidhya  
Event: Job-a-thon September 2021  
Files: TRAIN, TEST_FINAL, SAMPLE  
Context- Daily Sales of 365 stores from 1st Jan 2018 to 31st May 2019   
Problem Statement- Predict sales of each store for the next 2 months  

## EDA  
No. of orders is not available in test set, hence not considered  
No missing values in either dataset  
Sales is highly skewed with some values as 0 but none negative  
Most stores are of Store Type 0   
Most stores are located at Location Type 0  
Most stores are in the Region Code 0  
Highest Average Sales is of the Store Type 3  
Highest Average Sales is of the Location Type 1  
Highest Average Sales is of the Region Code 0  

## Feature Engineering
Using Date - Month, Week, Day  
Mean Sales Encoding- By store, By week, By month  
Encoding with Dimensions-  
Weekly_Reg_Sales: Mean Sales By Region,Location,Store_Type,Week,Holiday,Discount   
Weekly_Holidays:  Total Holidays By Region, Location, Store_Type, Week  
Date_block_num : Year and Month pairs  
Lag Features grouped by Date_block_num and Store_id:  
Monthly_Sales(Avg)  
date_avg_Sales  
Date_store_type_avg_sales  
date_location_avg_sales  
 date_region_avg_sales  
Trend Variable - delta_Sales_lag (Trend of avg monthly store sales by date_block_num)  

## Model Selection
Experimented with subsets of variables on:  
Catboost Regressor  
XGBoost Regressor  
K- Nearest Neighbours  
Random Forest  
SGD Regressor  
MLP Sequential Architecture  
Ensemble using Elastic Net on Level 1 predictions  


Post tuning hyperparameters, best approach:  
XGBoost  
AV Score (MSLE * 1000) -  
237.05



