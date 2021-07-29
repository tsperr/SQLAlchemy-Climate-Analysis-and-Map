# SQLAlchemy Climate Analysis and Map

## Step 1 - Climate Analysis and Exploration

Basic climate analysis and data exploration of your climate database are done with Python and SQLAlchemy. Analysis is completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.

### Precipitation Analysis

The analysis finds the date and precipitation from the past 12 months and loads them into a Pandas DataFrame. The DataFrame is sorted by the date and plotted with pandas. The summary statistics is printed.

### Station Analysis

The total number of stations in the dataset is found, and a query is designed to find the most active stations. The locations of those stations are listed in descending order. The following is calculated from this dataset:

  * Which station id has the highest number of observations?

  * Using the most active station id, calculate the lowest, highest, and average temperature.

 A query retrieves the last 12 months of temperature observation data (TOBS), and filtered by the station with the highest number of observations. The temperature is queried from the last 12 months, as well. The results are plotted in a histogram using bins. The session is closed. 
