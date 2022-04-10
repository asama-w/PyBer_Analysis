# Analysis of PyBer's Rideshare Data
## 1) Analysis Overview
### 1.1) Purpose of the Analysis
This analysis is carried out via python to see the relationships between the ride-share fare and the three city types during a 4-month period, for PyBer company, which is a python-based ride-sharing app company. It aims to create a visualization which shows the total weekly fares for each city type, and discover the trends between the data, in order to assist PyBer in making business decisions regarding the differences between the ride-sharing data among these city types.

### 1.2) Overview of the Project
This analysis will be creating the followings;
+ The **summary data frame** of ride-sharing data by city types consisting of their statistical outputs and calculations.
+ The **data visualization as a multiple-line chart** of the total weekly fare of the three city types during 4 months, January to April, 2019.

The locations of the complete code used for this analysis and the visualization saved as a figure are as follow;
+ **Code**: `PyBer_Challenge.ipynb`
+ **Visualization's Figure**: `analysis/PyBer_fare_summary.png`

### 1.3) Resources
The resources and tools for this analysis are shown as below;
+ **Data Sources**: located in the `Resources` folder
	+ `city_data.csv`
	+ `ride_data.csv`
+ **Programming Language**: Python3
+ **Software**: Jupiter Notebook
+ **Library**: Matplotlib, Pandas

## 2) Analysis Results
### 2.1) Starter DataFrame
The overall PyBer data frame `pyber_data_df` is created by combing the city and ride data frames together. The following figure shows the overview of this data frame on which the analysis will be performed.

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/Additional%20Images/PyBer_data_df.png width="60%" height="60%">

### 2.2) Summary DataFrame of Ride-Sharing Data by City Types
There are 3 types of cities in this dataset: **Rural, Suburban, and Urban**.

As this analysis focus on the impact of different city types on the ride-sharing fares, the following statistical analysis per each city are performed on the data in `pyber_data_df` data frame, then put into a new data frame called `pyber_summary_df` to display the data summary.
+ Total Rides
+ Total Drivers
+ Total Fares
+ Average Fare per Ride
+ Average Fare per Driver

Examples of the code:
```python
# Find average total fare per ride for each city type
total_rides_by_type = pyber_data_df.groupby(["type"]).count()["ride_id"]
total_fares_by_type = pyber_data_df.groupby(["type"]).sum()["fare"]
avg_fare_per_ride = total_fares_by_type / total_rides_by_type
```

The summary data frame based on the city types, `pyber_summary_df`is present as the below figure. 

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/Additional%20Images/PyBer_summary_df.png width="80%" height="80%">

From the summary data frame, there are two visible trends, which are are inversely proportional to each other:
+ **The trend of the total number of rides, numbers of drivers, and total collected fares**: _Number: Urban > Suburban > Rural_ <br /> The number are highest in Urban city type, follows by Suburban, and are lowest in Rural city type. 
+ **The trend of the average fare per ride and the average fare per driver**: _Price: Rural > Suburban > Urban_ <br /> where the average fares are cheapest in the Urban area and most expensive in the Rural area.


### 2.3) Fare Per Week by City Types

#### Total Weekly Fare by City Types (DataFrame)
<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/Additional%20Images/Weekly_fare_summary_by_type.png width="25%" height="25%">

#### Total Weekly Fare by City Types (Multple-line Chart)

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/analysis/PyBer_fare_summary.png width="100%" height="100%">

## 3) Analysis Summary
(Three business recommendations addressing any disparities among the city types)
