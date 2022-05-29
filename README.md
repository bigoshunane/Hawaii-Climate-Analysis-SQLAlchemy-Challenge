# Hawaii Climate Analysis


## Project objective

The aim of this project is to utilize SQLAlchemy ORM queries, Pandas and Matplotlib and do basic climate analysis given climate database of Honolulu, Hawaii.

Two main works done are:

  1. Climate Analysis and exploration.
  
  2. Climate App
  
  3. Bonus challenges   
              
      -  Temperature analysis
      -  Daily rainfall average
  
Remarks for files in repository:
     
. Analyses and visualizations for climate is can be found in the Jupyter notebook called [climate_starter.ipynb.](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/blob/main/climate_starter.ipynb)
     
. Analyses and visualizations for temperature analysis_bonus_1 is can be found in the Jupyter notebook 

  named [temp_analysis_bonus_1_starter.ipynb.](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/blob/main/temp_analysis_bonus_1_starter.ipynb)
     
. Analyses and visualizations for temperature analysis_bonus_2 is can be found in the Jupyter notebook 

  named [temp_analysis_bonus_2_starter.ipynb.](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/blob/main/temp_analysis_bonus_2_starter.ipynb)
     
. The [Resources](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/tree/main/Resources)folder contains the hawaii.sqlite database file and 2 csv files containing the measurement and station tables.

. The [images](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/tree/main/Images) folder contains visualization images from the analysis and bonus challenges.

. The [app.py](https://github.com/bigoshunane/SQLAlchemy_Challenge_HM8/blob/main/app.py) file contains the code for a Flask web app to query the climate database.


The following instructions have been followed and asnwers were computed accordingly and results are included:

## Step 1 - Climate Analysis and Exploration

  -  Use the provided starter notebook and hawaii.sqlite files to complete your climate analysis and data exploration.
  -  Use SQLAlchemy create_engine to connect to your sqlite database.
  -  Use SQLAlchemy automap_base() to reflect your tables into classes and save a reference to those classes called Station and Measurement.
  -  Link Python to the database by creating an SQLAlchemy session.
  -  Important Don't forget to close out your session at the end of your notebook.

## Precipitation Analysis

  -  Start by finding the most recent date in the data set.
  -  Using this date, retrieve the last 12 months of precipitation data by querying the 12 preceding months of data. Note you do not pass in the date as a                variable   to your query.

     -  Select only the date and prcp values.
     -  Load the query results into a Pandas DataFrame and set the index to the date column.
     -  Sort the DataFrame values by date.
     -  Plot the results using the DataFrame plot method.

![precp](https://user-images.githubusercontent.com/84547558/156428114-8c670ea9-e265-4bc6-844d-d5e535429b51.png)

    Fig.1 Precipitation amounts (inches) in Honolulu, Hawaii.

    . Use Pandas to print the summary statistics for the precipitation data.
    
![stst](https://user-images.githubusercontent.com/84547558/156428960-49a3142e-657e-4807-95b7-3aec89912dcd.png)
    
    Fig.2 Summary statistics for precipitation data.
    

## Station Analysis

-  Design a query to calculate the total number of stations in the dataset.
-  Design a query to find the most active stations (i.e. which stations have the most rows?).
    
     -  List the stations and observation counts in descending order.
     -  Which station id has the highest number of observations?
     -  Using the most active station id, calculate the lowest, highest, and average temperature.
     -  Hint: You will need to use a function such as func.min, func.max, func.avg, and func.count in your queries.

-  Design a query to retrieve the last 12 months of temperature observation data (TOBS).

    -   Filter by the station with the highest number of observations.
    -   Query the last 12 months of temperature observation data for this station.
    -   Plot the results as a histogram with bins=12.

![temp](https://user-images.githubusercontent.com/84547558/156429655-bb2de60a-08b8-4aab-9b8f-25d45dfa0c78.png)

Fig.3 Temperatures recoreded at station USC00519281 within 12 months.
    -  The database was queired to determine the total number of stations:9 
    - The most active station was determined to be 'USC00519281'
   
   ![s9](https://user-images.githubusercontent.com/84547558/156440524-87fd1706-c0a4-4b0f-abdb-aa36bff5338e.png)

Fig.4 The list of stations and observation counts in descending order.
    
    
## Step 2 - Climate App

-   Now that you have completed your initial analysis, design a Flask API based on the queries that you have just developed.
    -  Use Flask to create your routes.
  
## Routes
. /
   . Home page
     
   . List all routes that are available.
   
-   /api/v1.0/precipitation
    -  Convert the query results to a dictionary using date as the key and prcp as the value.
    -  Return the JSON representation of your dictionary.

-   /api/v1.0/stations
     -  Return a JSON list of stations from the dataset.
    
-   /api/v1.0/tobs
     -  Query the dates and temperature observations of the most active station for the last year of data.
     -  Return a JSON list of temperature observations (TOBS) for the previous year.
    
-   /api/v1.0/<start> and /api/v1.0/<start>/<end>
    -  Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.
    -  When given the start only, calculate TMIN, TAVG, and TMAX for all dates greater than and equal to the start date.
    -  When given the start and the end date, calculate the TMIN, TAVG, and TMAX for dates between the start and end date inclusive.

## Hints
-  You will need to join the station and measurement tables for some of the queries.
-  Use Flask jsonify to convert your API data into a valid JSON response object.
  
##  Bonus: Other Recommended Analyses
  
 -  The following are optional challenge queries. These are highly recommended to attempt, but not required for the homework.
 -  Use the provided temp_analysis_bonus_1_starter.ipynb and temp_analysis_bonus_2_starter.ipynb starter notebooks for each bonus challenge.
  
## Temperature Analysis I
  
 -  Hawaii is reputed to enjoy mild weather all year. Is there a meaningful difference between the temperature in June and December?
 -  The the average temperature in June at all stations across all available years in the dataset was: 74.94 F.
 -  The the average temperature in December at all stations across all available years in the dataset was: 71.04 F.
 -  Using a paired t-test, it was determined the difference in the means was statistically significant and the analysis and plot are given below.

  
  
![tem11](https://user-images.githubusercontent.com/84547558/156441478-2c3f5631-d4de-4bcc-8363-1d664fa2713d.png)

Fig.5 Scatter and histogram plots of June and December temperatures.

June and December temperature observations were retrieved by converting string dates to datetime objects in order to filter queries by month.
Null hypothesis: The mean difference between the temperatures in June and December is zero.
A paired t-test was used to compare the means of the same group in this case, the mean temperature observations are of the same stations,
just for different timepoints. The p-value of 0.0001 is less than 0.05 so we reject the null hypothesis and conclude that the data is statistically      significant.The mean temperature difference between the June and December is a mere 3.9 degrees Fahrenheit. The result does not appear to show much 
of a difference. But the t-test with very low p-value indicates that the difference is statistically significant. So while the difference is meaningful,  the actual difference is not, thereby indicating that you can travel to Hawaii and enjoy in 70 degrees temperature year-round.
  
  
## Temperature Analysis II
  
-  A function called calc_temps that will accept a start date and end date in the format %Y-%m-%d and return the minimum, average, and maximum temperatures for   that range of dates was used to calculate the min, avg, and max temperatures for my trip using the matching dates from the previous year:

      . The lowest temperature recorded was: 58.0 F
      . The highest temperature recorded was: 87.0 F
      . The average temperature recorded was: 74.6 F
  
![bar](https://user-images.githubusercontent.com/84547558/156444805-ab4bfb41-3e5a-439a-8ac6-bcb57eafd5c4.png)
  
Fig.6 The min, avg, and max temperatures plotted as a bar chart.
  
  
## Daily Rainfall Average
  
-  Now that you have an idea of the temperature lets check to see what the rainfall has been, you don't want a when it rains the whole time!
-  Calculate the rainfall per weather station using the previous year's matching dates.
-  Sort this in descending order by precipitation amount and list the station, name, latitude, longitude, and elevation.

 ![r](https://user-images.githubusercontent.com/84547558/156447971-6796d883-91fa-4f8b-b662-1b82471de1e2.png)

Fig.7 Calculated the rainfall per weather station using the previous year's matching dates.

## Daily Temperature Normals
  
-   Calculate the daily normals for the duration of your trip. Normals are the averages for the min, avg, and max temperatures. 
    You are provided with a function called daily_normals that will calculate the daily normals for a specific date. This date string
    will be in the format %m-%d. Be sure to use all historic TOBS that match that date string.
  
    -  Set the start and end date of the trip.
    -  Use the date to create a range of dates.
    -  Strip off the year and save a list of strings in the format %m-%d.
    -  Use the daily_normals function to calculate the normals for each date string and append the results to a list called normals.
    -  Load the list of daily normals into a Pandas DataFrame and set the index equal to the date.
    -  Use Pandas to plot an area plot (stacked=False) for the daily normals.
  
![ar](https://user-images.githubusercontent.com/84547558/156448798-54b78941-33e1-4c33-94ba-81cf3ec179ca.png)  
  
Fig.8 Area plot for daily min, ave and max temperatures.


  
  
  
# References
Menne, M.J., I. Durre, R.S. Vose, B.E. Gleason, and T.G. Houston, 2012: An overview of the Global Historical Climatology Network-Daily Database. Journal of Atmospheric and Oceanic Technology, 29, 897-910, https://doi.org/10.1175/JTECH-D-11-00103.1

© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.


  
  
