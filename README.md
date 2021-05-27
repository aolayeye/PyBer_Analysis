# PyBer_Analysis
## Overview
This analysis seeks to provide insights into ride accessibility and affordability for PyBer, a Python-based ride-sharing app company. Our goal is to perform exploratory data analysis on a large dataset to determine the relationship between the type of city, the number of drivers and riders, and the percentage of total fares, riders, and drivers by type of city. To achieve this goal, We would create several visualizations, write python scripts using pandas library and Matplotlib to create various charts. In the end, we hope to use the analysis and visualizations we produce to improve access to ride-sharing services and determine affordability for underserved neighborhoods.

After creating initial results, our analysis moves to a second phase where we make a summary DataFrame of the ride-sharing data by city type. Then, using Pandas and Matplotlib, we would create a multiple-line graph that shows the total weekly fares for each city type. Finally, we would summarize how the data differs by city type and how decision-makers can use those differences at PyBer to answer questions around ride accessibility and affordability.

### Control Flow
1. Import your data into a Pandas DataFrame.
2. Inspect the data to dertermine the shape of the data, what types of columns are present, and if the data is readable or needs to be converted in some way.
3. Merge your DataFrames.
4. Create a bubble chart that showcases the average fare versus the total number of rides with bubble size based on the total number of drivers for each city type, including urban, suburban, and rural.
5. Determine the mean, median, and mode for the following:
    - The total number of rides for each city type.
    - The average fares for each city type.
    - The total number of drivers for each city type.
6. Create box-and-whisker plots that visualize each of the following to determine if there are any outliers:
    - The number of rides for each city type.
    - The fares for each city type.
    - The number of drivers for each city type.
7. Create a pie chart that visualizes each of the following data for each city type:
    - The percent of total fares.
    - The percent of total rides.
    - The percent of total drivers.

### Intial Findings
1. A visual inspection of our bubble chart reveal that urban cities have the highest driver count and total number of rides. Conversely, rural cities with the lowest number of rides and smallest driver count have the highest fares.
    
    Note: Circle size correlates with driver count per city

![Fig1](https://user-images.githubusercontent.com/67847583/119573695-3f43cd80-bd7a-11eb-9669-27d007118de9.png)


3. Our Summary Statistics for Number of Rides by City Type show that If we compare the average number of rides between each city type, we'll notice that the average number of rides in the rural cities is about 4 and 3.5 times lower than urban and suburban cities, respectively.
4. Our Box and Whisker plot analysis reveals that There is one outlier in the urban ride count data. Also, the average number of rides in the rural cities is about 4- and 3.5-times lower per city than the urban and suburban cities, respectively.
5. From our combined Ride fare data box-and-whisker plots, we see that there are no outliers. However, the average fare for rides in the rural cities is about $11 and $5 more per ride than the urban and suburban cities, respectively. Why do you think there is such a big difference? The number of drivers in rural cities helps explain tis huge difference in fares, there are less number of drivers compared to riders. Rural cities have a mean of 4 drivers and mean ride count of 7 {ratio 1:2} Urban cities have mean 24 ride count and mean 36 {ratio 2:3}; Suburban mean driver 14 and mean ride count 17 {ratio 4:5} Looking at the number of riders, we can suggest that Urban cities have the highest revenue.
6. From our combined Driver Count data box-and-whisker plots The average number of drivers in rural cities is nine to four times less per city than in urban and suburban cities, respectively. By looking at the driver count data and fare data, can you get a sense of the overall revenue?


![Fig2](https://user-images.githubusercontent.com/67847583/119574617-5df69400-bd7b-11eb-9666-d2bf9a4ea832.png)
![Fig3](https://user-images.githubusercontent.com/67847583/119574780-98603100-bd7b-11eb-896e-a26193255b1e.png)
![Fig4](https://user-images.githubusercontent.com/67847583/119574892-c34a8500-bd7b-11eb-9ec0-bad9f31f6d78.png)


## Control Flow of the New Analysis
1. Create a Ride Sharing Summary DataFrame by city type
    - use the groupby() function to create a Series of data that has the type of city as the index, then apply the count() method to the "ride_id" column.
    - use the groupby() function to create a Series of data that has the type of city as the index, then apply the sum() method to the "driver_count" column.
    - use the groupby() function to create a Series of data that has the type of city as the index, then apply the sum() method to the "fare" column.
    - calculate the average fare per ride by city type by dividing the sum of all the fares by the total rides.
    - calculate the average fare per driver by city type by dividing the sum of all the fares by the total drivers.
    - create a PyBer summary DataFrame with all the data gathered in the previous steps
    - remove index name and format columns of the summary dataframe.
2. Create multiple-line chart of total fares for each city type
    - create a new DataFrame with multiple indices using the groupby() function on the "type" and "date" columns of the pyber_data_df DataFrame, then apply the sum() method on the "fare" column to show the total fare amount for each date.
    - reset the index and use the pivot() function to convert the DataFrame from the previous step so that the index is the "date," each column is a city "type," and the values are the "fare."
    - create a new DataFrame by using the loc method on the following date range: 2019-01-01 through 2019-04-29
    - reset the index of the DataFrame from the previous step to a datetime data type and create a new DataFrame by applying the resample() function to the modified DataFrame. Resample the data in weekly bins, then apply the sum() method to get the total fares for each week.
    - graph the resampled DataFrame from  the previous Step using the object-oriented interface method and the df.plot() method, as well as the Matplotlib "fivethirtyeight" graph style. Annotate the y-axis label and the title, then use the appropriate code to save the figure

## Results
Using the Pandas groupby() function with the count() and sum() methods on PyBer DataFrame columns, we get the total number of rides, total number of drivers, and the total fares for each city type. We Then, calculated the average fare per ride and average fare per driver for each city type. Finally, add this data to a new DataFrame, and then formatted the columns to obtain the following summary result.

Ride-Sharing Summary DataFrame

![PyBer_summary_DataFrame](https://user-images.githubusercontent.com/67847583/119545944-fa5b6f00-bd58-11eb-9b82-702276085bbb.png)


Using the object-oriented interface method and the df.plot() method, as well as the Matplotlib "fivethirtyeight" graph style, we graphed the resampled DataFrame from the previous result to obtain to fares for the weekly bins in the following graph.

Line Chart Showing Total Fares by City Type

![PyBer_fare_summary](https://user-images.githubusercontent.com/67847583/119575348-88951c80-bd7c-11eb-95e4-2f6988bf0443.png)



## Summary

1. One area to pay attention to is the rural cities where the mean ratio of drivers to riders is 1 to 2. PyBer needs to further investigate why there is a low driver count compared to number of rides. Research questions that could be asked include:
   - are rural distances typically longer in rural cities than in urban cities
   - are all rural cities accurately captured on maps
   - what is the actual market demand for PyBer in rural cities
   - are there really enough people requesting rides in rural cities
   - is internet connectivity an impediment to PyBer reach in rural cities
   - if PyBers mode of payment is credit card, does the rural population have credits cards or do they rely on cash to carry out their daily transactions.


2. Another recommendation is to find the sweet spot between average fare per ride (cost to the rider) and average fare per driver (revenue to the driver). A way to achieve the optimal solution to the optimization problem is to maintain a minimum threshold of driver count across all city types while increasing the number of riders. An increasing number of riders would reduce mean fares and lead to a multiplier effect on ride count. Similarly, maintaining a driver count threshold across different city types could result in fare per driver upper and lower boundaries that are not too far apart.


3. While the Average fare per driver is highest for rural cities ($55.49) with a mean ride count of 7, that amount pales compared to the $16 and average round count of 24 in urban cities. A potential research question for PyBer could be:
   - can a subscription model be introduced for riders in rural cities where there is flat fee structure for a specified period
   - can drivers be incentivized to drive in rural cities

    Answers to questions like these can help illuminate the disparities between the fares and driver count in rural and urban cities and provide concrete steps to making rides  affordable and accessible across all city types.






