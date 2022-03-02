# SQLAlchemy_Challenge_HM8

The aim of this project is to utilize SQLAlchemy ORM queries, Pandas and Matplotlib and do basic climate analysis given climate database of Honolulu, Hawaii.

Two main works done are:
  1. Climate Analysis and exploration.
  2. Climate App
  3. Bonus challenges - Temperature analysis
                      - Daily rainfall average
  
Remarks for files in repository:
     
     . Analyses and visualizations for climate is can be found in the Jupyter notebook called climate_starter.ipynb.
     
     . Analyses and visualizations for temperature analysis_bonus_1 is can be found in the Jupyter notebook called temp_analysis_bonus_1_starter.ipynb.
     
     . Analyses and visualizations for temperature analysis_bonus_2 is can be found in the Jupyter notebook called temp_analysis_bonus_2_starter.ipynb
     
     . The Resources folder contains the hawaii.sqlite database file and 2 csv files containing the measurement and station tables.

     . The images folder contains visualization images from the analysis and bonus challenges.

     . The app.py file contains the code for a Flask web app to query the climate database.


The following instructions have been followed and asnwers were computed accordingly and results are included:

# Step 1 - Climate Analysis and Exploration

    . Use the provided starter notebook and hawaii.sqlite files to complete your climate analysis and data exploration.

    . Use SQLAlchemy create_engine to connect to your sqlite database.

    . Use SQLAlchemy automap_base() to reflect your tables into classes and save a reference to those classes called Station and Measurement.

    . Link Python to the database by creating an SQLAlchemy session.

    . Important Don't forget to close out your session at the end of your notebook.

# Precipitation Analysis

    . Start by finding the most recent date in the data set.

    . Using this date, retrieve the last 12 months of precipitation data by querying the 12 preceding months of data. Note you do not pass in the date as a                variable   to your query.

    . Select only the date and prcp values.

    . Load the query results into a Pandas DataFrame and set the index to the date column.

    . Sort the DataFrame values by date.

    . Plot the results using the DataFrame plot method.

![precp](https://user-images.githubusercontent.com/84547558/156428114-8c670ea9-e265-4bc6-844d-d5e535429b51.png)

    Fig.1 Precipitation amounts (inches) in Honolulu, Hawaii.

    . Use Pandas to print the summary statistics for the precipitation data.
    
![stst](https://user-images.githubusercontent.com/84547558/156428960-49a3142e-657e-4807-95b7-3aec89912dcd.png)
    
    Fig.2 Summary statistics for precipitation data.
    
# Station Analysis

. Design a query to calculate the total number of stations in the dataset. 

. Design a query to find the most active stations (i.e. which stations have the most rows?).
    
    . List the stations and observation counts in descending order.

    . Which station id has the highest number of observations?

    . Using the most active station id, calculate the lowest, highest, and average temperature.

    . Hint: You will need to use a function such as func.min, func.max, func.avg, and func.count in your queries.

. Design a query to retrieve the last 12 months of temperature observation data (TOBS).

    . Filter by the station with the highest number of observations.

    . Query the last 12 months of temperature observation data for this station.

    . Plot the results as a histogram with bins=12.

![temp](https://user-images.githubusercontent.com/84547558/156429655-bb2de60a-08b8-4aab-9b8f-25d45dfa0c78.png)

    Fig.3 Temperatures recoreded at station USC00519281 within 12 months.
    
    
# Step 2 - Climate App

 Now that you have completed your initial analysis, design a Flask API based on the queries that you have just developed.
   
    . Use Flask to create your routes.
  
# Routes
. /
   . Home page
     
   . List all routes that are available.
   
. /api/v1.0/precipitation

    . Convert the query results to a dictionary using date as the key and prcp as the value.

    . Return the JSON representation of your dictionary.

. /api/v1.0/stations

    . Return a JSON list of stations from the dataset.
    
. /api/v1.0/tobs

    . Query the dates and temperature observations of the most active station for the last year of data.

    . Return a JSON list of temperature observations (TOBS) for the previous year.
    
. /api/v1.0/<start> and /api/v1.0/<start>/<end>
  
     . Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.

     . When given the start only, calculate TMIN, TAVG, and TMAX for all dates greater than and equal to the start date.

     . When given the start and the end date, calculate the TMIN, TAVG, and TMAX for dates between the start and end date inclusive.

# Hints

    . You will need to join the station and measurement tables for some of the queries.

    . Use Flask jsonify to convert your API data into a valid JSON response object.
  
#  Bonus: Other Recommended Analyses
  
  . The following are optional challenge queries. These are highly recommended to attempt, but not required for the homework.

  . Use the provided temp_analysis_bonus_1_starter.ipynb and temp_analysis_bonus_2_starter.ipynb starter notebooks for each bonus challenge.
  
# Temperature Analysis I
  
        June and December temperature observations were retrieved by converting string dates to datetime objects in order to filter queries by month.

        Null hypothesis: The mean difference between the temperatures in June and December is zero.

       A paired t-test was used to compare the means of the same group in this case, the mean temperature observations are of the same stations,
       just for different timepoints. The p-value of 0.0001 is less than 0.05 so we reject the null hypothesis and conclude that the data is statistically              significant.
  
       The mean temperature difference between the June and December is a mere 3.9 degrees Fahrenheit. The result does not appear to show much 
       of a difference. But the t-test with very low p-value indicates that the difference is statistically significant. So while the difference is meaningful,          the actual difference is not, thereby indicating that you can travel to Hawaii and enjoy in 70 degrees temperature year-round.
  
  
  


  
  
