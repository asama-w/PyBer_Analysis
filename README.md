# Analysis of PyBer's Rideshare Data
## 1) Analysis Overview
### 1.1) Purpose of the Analysis
This analysis is carried out via python to see the relationships between the ride-share fare and the three city types during a 4-month period, for PyBer company, which is a python-based ride-sharing app company. It aims to create a visualization which shows the total weekly fares for each city type, and discover the trends between the data, in order to assist PyBer in making business decisions regarding the differences between the ride-sharing data among these city types.

### 1.2) Overview of the Project
This analysis will be creating the followings;
+ The **summary data frame** of ride-sharing data by city types consisting of their statistical outputs and calculations.
+ The **data visualization as a multiple-line chart** of the total weekly fare of the three city types during 4 months, January to April, 2019.

The locations of the complete code used for this analysis and the visualization saved as a figure are as follow;
+ `PyBer_Challenge.ipynb`
+ `analysis/PyBer_fare_summary.png`

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

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/Additional%20Images/PyBer_summary_df.png width="90%" height="90%">

From the summary data frame, there are two visible trends, which are inversely proportional to each other:
+ **The trend of the total number of rides, numbers of drivers, and total collected fares**:<br /> **_Number of shares: Urban > Suburban > Rural_** <br /> The number are highest in Urban city type, follows by Suburban, and are lowest in Rural city type. 
+ **The trend of the average fare per ride and the average fare per driver**:<br /> **_Price per share: Rural > Suburban > Urban_** <br /> The average fares per ride is the cheapest in Urban areas, and average fare per driver is the lowest in the Urban area. While average fares per ride is the most expensive in the Rural area, the average fare per driver is the highest in the Rural areas.

> Note that the number of drivers in Urban cities is much higher than their number of rides, so the average fare per driver is low ($16. 57). On the other hands, there are lesser drivers in Suburban and Rural cities than the number of rides, thus their drivers makes larger amount per trip. Rural cities' drivers make $55.49 per trip, which is around 3 times higher than Urban cities's drivers.

This can be the results from the population differences in each area, or the life-style of the residences. The urban city area is highly populated and usually radiates a busy life-style where everything is time-limited. People may need to commute from here and there in a hurry, resulting in the higher number of rides, attracting more drivers as there are more ride's demands, creating the high total amount of collected fares, thus, the average fare per ride tends to be lower due to the larger numbers of shares, however, the average fare by driver is also lowest due to the higher number of drivers.

On the contrary, when the distance is getting further away from the urban city area, the number of rides decreases and so does the drivers. This may result from the lesser populations, or there are fewer reasons for people to travelling out of the city more than coming in to the city, thus the demand in the suburban area and rural area decrease respectively. With the lesser numbers to share the fare, the average fare per ride increase, but so does the average share per driver which is higher, meaning that the drivers in the rural cities make more money per trip than the drivers in suburban and urban cities.


### 2.3) Fare Per Week by City Types
To uncover the trends of how the differ in timeline (by week) affect the total fare of each city type, the new data frame that summarize the weekly total fare of each city types is created. The duration of the dataset which will be analyzed is from January 1st, 2019 through April 28th, 2019, or approximately 4 months. The overview of this data frame is shown in the following figure.

#### Total Weekly Fare by City Types (DataFrame)
The data frame contains the total fare per week of each city type.

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/Additional%20Images/Weekly_fare_summary_by_type.png width="25%" height="25%">

#### Total Weekly Fare by City Types (Multple-line Chart)
The multiple-line plot is used to visualize the trends of the total fare per week for Urban, Suburban, and Rural, from this data frame.

<img src= https://github.com/asama-w/PyBer_Analysis/blob/main/analysis/PyBer_fare_summary.png width="100%" height="100%">

The trends from the total-weekly-fare plot correlate with the data in the ride-sharing-summary-by-type data frame `pyber_summary`.

Readings from the plot;
+ The Urban and Suburban type show a positive trend despite the fluctuations, still on the rise by the 4th week of April when compare to the beginning of January.
+ The Urban area's fare remains over $2000 USD range, throughout the period despite some up-and-down in March, which is the highest total fare amount among the three city types, approximately 4 times higher than the total fare of the Rural type.
+ The Suburban stays in-between the Urban and Rural trends, in the range $750 and $1500 USD, with a sharp rise from the 2nd week to 4th week of April.
+ The Rural type, however, remains relatively low within $500 USD range throughout the four months.
+ There is a spike increase for every city type in the 4th week of February follows by a dip at the beginning of March. There might have been some situations that increase the demands in ride-sharing in the 4th week of February.
+ From the 2nd to 4th week of April, there is a sharp rise for Suburban cities, while the other two fares show slight decline.


## 3) Analysis Summary
The following table shows the key points summary of this ride-share data analysis.

|Urban|Suburban|Rural|
|:-----:|:-----:|:-----:|
|Highest generated total fares <br /> $39,854,28|Medium generated total fares <br /> $19,356.33| Lowest generated total fares <br /> $4,327.93|
|Number of drivers > Number of rides |Number of rides > Number of drivers|Number of rides > Number of drivers|
|Lowest avg driver's earning per trip <br /> $16.57|In-between <br /> $39.50|Highest driver's earning per trip <br /> $55.49|
|Cheapest avg ride fare per trip <br /> $24.53|Medium-high avg ride fare per trip <br /> $30.97| Most expensive avg ride fare per trip<br /> $34.62|

+ From the data frames and multiple-line plot, ride-sharing is not a high demand services in the rural city type. However, this results in a highest earning per trip of drivers among the three city types despite having a relatively low ride numbers.

+ The different demands in ride-sharing services may due to the population factors, the geographic factors, the economical factors, the needs of ride-sharing, or the price per ride that is relatively high in rural cities, and relatively low in urban cities. To attract more customers to use ride-sharing services in the rural and subrural area, the company may need to do more research on the habituals of the residences in the cities, the approachability of the app and services, and find the touch point of the fare that is competitively with the others transportation options available in the areas. The company can promote the app with the aim of top-tier but affordable riding experience in-mind, so that the riders will remember the brand PyBer, and think of it first when there is the need to commute. 

+ To increase the total fares in Suburban cities, where the demand trends seems to be rising, the company can do a seasonal promotional campaign, such as additional discount if the pick-up locations and trip-destinations is within the cities, promoting the ride-sharing services using friend-referring discount to attract more customers to use their ride-share app and keep the ride-sharing trend goings.

+ As the Urban's driver earning per trip is comparably low, one solution to make up for the low average fare per drivers while encouraging the drivers to keep working with PyBer is to gain more ride trips such that there are more rides than the drivers to increase the average earning. In the urban cities where the ride-sharing is already used widely, the company can do a surprise campaign to thanks the frequent riders, giving out discounts, or collecting points which can be converted to the ride fare money, or the company can aim to promote the ride services on a safety perspective, to maintain the current riders with the hope that they will use the service more frequently. 




