# PyBer_Analysis
## Overview
This analysis seeks to the data of PyBer, a Python-based ride sharing app company. Our goal is to perform exploratory data analysis on large dataset to determine the relationship between the type of ciity and the number of drivers and riders as well as the percentage of total fares, riders and drivers by type of city. To achieve this goal, We would create several visualizations, write python scripts using pandas library and matplotlib to create a variety of charts in the end, we hope to use the analysis and visulaizations we produce to improve access to ride sharing services and determine affordability for underserved neighbourhoods.

After creating initial results, our analysis moves to a second phase where we create a summary DataFrame of the ride-sharing data by city type. Then, using Pandas and Matplotlib, we would create a multiple-line graph that shows the total weekly fares for each city type. Finally, we would provide a summary of how the data differs by city type and how those differences can be used by decision-makers at PyBer.

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
1. Our initial results reveal that urban cities had the highest number of rides, drivers.
2. Our Summary Statistics for Number of Rides by City Type show that If we compare the average number of rides between each city type, we'll notice that the average number of rides in the rural cities is about 4 and 3.5 times lower than urban and suburban cities, respectively.
3. Our Box and Whisker plot analysis reveals that There is one outlier in the urban ride count data. Also, the average number of rides in the rural cities is about 4- and 3.5-times lower per city than the urban and suburban cities, respectively.
4. From our combined Ride fare data box-and-whisker plots, we see that there are no outliers. However, the average fare for rides in the rural cities is about $11 and $5 more per ride than the urban and suburban cities, respectively. Why do you think there is such a big difference? By looking at the number of riders for each city, can you get a sense of the overall revenue?
5. From our combined Driver Count data box-and-whisker plots The average number of drivers in rural cities is nine to four times less per city than in urban and suburban cities, respectively. By looking at the driver count data and fare data, can you get a sense of the overall revenue?

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

![PyBer_fare_summary](https://user-images.githubusercontent.com/67847583/119551360-2bd73900-bd5f-11eb-8244-e06a8f6febd2.png)








