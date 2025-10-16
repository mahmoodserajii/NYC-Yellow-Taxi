# NYC Yellow Taxi Fare Prediction (Q1 2018)

## Introduction
This project analyzes the Q1 2018 New York City Yellow Taxi dataset, containing over 305,000 trip records.  
The focus was to clean and transform messy data, engineer meaningful features, and build a predictive model to forecast taxi fare amounts.

## Business Problem
Raw taxi trip data contains inconsistencies, missing values, and anomalies that hinder accurate analysis.  

The objective was:
- Improve data quality and consistency  
- Build a robust fare prediction model  
- Enable insights for revenue management, pricing strategies, and urban transport analytics  

## Data Analysis Workflow
The project followed a standard data science lifecycle:

1. Data Understanding – load, inspect, and summarize raw dataset  
2. Preparation (Cleaning and Engineering) – resolve inconsistencies, impute missing values, generate analytical features  
3. Visualization – explore trends, hotspots, and trip dynamics  
4. Modeling – build and evaluate regression models for fare prediction  
5. Evaluation – compare models using R², MAE, and RMSE  

## Data Cleaning
Key steps included:

- Datetime: Converted pickup/dropoff timestamps, corrected negative durations  
- Trip Duration: Imputed extreme values with grouped means  
- VendorID: Fixed invalid entries, restricted to [1, 2, 6, 7]  
- Passenger Count: Filled missing values, clamped to 1–6  
- RatecodeID: Flagged unknowns with 99  
- Store and Forward Flag: Standardized as boolean  
- Congestion Surcharge: Set to 0 (not applicable in Q1 2018)  
- Airport Fee, Improvement Surcharge, MTA Tax: Corrected and standardized  
- Trip Distance: Replaced negatives, zeros, and outliers with imputed values  
- Payment Type: Fixed invalid paymeny types based on total amount 
- Tip Amount: Set to 0 for all cash payments  
- Amount Columns: Corrected signs, replaced anomalies with grouped means  
- JFK Flat Rate: Standardized to ±52 for flat-rate trips  

## Feature Engineering
- Trip Duration in minutes from timestamps  
- Time Buckets (morning, midday, evening rush, night, etc.)  
- Adjusted Total Amount recomputed for accurate totals  

## Visualization
Exploratory analysis included:

- Top 20 pickup-dropoff routes  
- Payment type distributions  
- Time-bucket economics  
- Interactive Folium maps for spatial hotspots  
- Demand trends and customer payment preferences  

## Modeling
A regression pipeline was developed using 11 curated features.

- Train/Validation/Test Split: 60/20/20 on a 50k sampled dataset  
- Preprocessing: ColumnTransformer for scaling and one-hot encoding  
- Models Evaluated: Random Forest, XGBoost, Support Vector Regression  
- Hyperparameter Tuning: RandomizedSearchCV on a 20k subset  

### Results
- Random Forest performed best:
  - R² = 0.93  
  - MAE = $0.86 (~7% of average fare $13)  
  - RMSE = $2.72  

## Conclusion
- The dataset was successfully cleaned and engineered for analysis  
- Predictive models were built, with XGBoost outperforming alternatives  
- Achieved strong predictive accuracy, valuable for fare forecasting and urban mobility insights  

