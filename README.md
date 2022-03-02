# SQLAlchemy_Challenge_HM8

The aim of this project is to utilize SQLAlchemy ORM queries, Pandas and Matplotlib and do basic climate analysis given climate database.

The following instructions have been followed and asnwers were computed accordingly:

# Step 1 - Climate Analysis and Exploration

. Use the provided starter notebook and hawaii.sqlite files to complete your climate analysis and data exploration.


. Use SQLAlchemy create_engine to connect to your sqlite database.


. Use SQLAlchemy automap_base() to reflect your tables into classes and save a reference to those classes called Station and Measurement.


. Link Python to the database by creating an SQLAlchemy session.


. Important Don't forget to close out your session at the end of your notebook.

# Precipitation Analysis

. Start by finding the most recent date in the data set.


. Using this date, retrieve the last 12 months of precipitation data by querying the 12 preceding months of data. Note you do not pass in the date as a variable   to your query.


. Select only the date and prcp values.


. Load the query results into a Pandas DataFrame and set the index to the date column.


. Sort the DataFrame values by date.


Plot the results using the DataFrame plot method.

