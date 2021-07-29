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

## Step 2 - Climate App

A Flask API is designed based on the queries.


### Routes

* `/`

  * Home page.

* `/api/v1.0/precipitation`

  * Convert the query results to a dictionary using `date` as the key and `prcp` as the value.

  * Return the JSON representation of your dictionary.

* `/api/v1.0/stations`

  * Return a JSON list of stations from the dataset.

* `/api/v1.0/tobs`
  * Query the dates and temperature observations of the most active station for the last year of data.

  * Return a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

  * Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.

  * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date.

  * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive.

## Hints

* You will need to join the station and measurement tables for some of the queries.

* Use Flask `jsonify` to convert your API data into a valid JSON response object.

- - -

## Bonus: Other Recommended Analyses

* The following are optional challenge queries. These are highly recommended to attempt, but not required for the homework.

* Use the provided [temp_analysis_bonus_1_starter.ipynb](temp_analysis_bonus_1_starter.ipynb) and [temp_analysis_bonus_1_starter](temp_analysis_bonus_2_starter.ipynb) starter notebooks for each bonus challenge.

### Temperature Analysis I

* Hawaii is reputed to enjoy mild weather all year. Is there a meaningful difference between the temperature in, for example, June and December?

* Use pandas to perform this portion.

  * Convert the date column format from string to datetime.

  * Set the date column as the DataFrame index

  * Drop the date column

* Identify the average temperature in June at all stations across all available years in the dataset. Do the same for December temperature.

* Use the t-test to determine whether the difference in the means, if any, is statistically significant. Will you use a paired t-test, or an unpaired t-test? Why?

### Temperature Analysis II

* You are looking to take a trip from August first to August seventh of this year, but are worried that the weather will be less than ideal. Using historical data in the dataset find out what the temperature has previously looked like.

* The starter notebook contains a function called `calc_temps` that will accept a start date and end date in the format `%Y-%m-%d`. The function will return the minimum, average, and maximum temperatures for that range of dates.

* Use the `calc_temps` function to calculate the min, avg, and max temperatures for your trip using the matching dates from a previous year (i.e., use "2017-08-01").

* Plot the min, avg, and max temperature from your previous query as a bar chart.

  * Use "Trip Avg Temp" as the title.

  * Use the average temperature as the bar height (y value).

  * Use the peak-to-peak (TMAX-TMIN) value as the y error bar (YERR).

    ![temperature](Images/temperature.png)

### Daily Rainfall Average

* Now that you have an idea of the temperature lets check to see what the rainfall has been, you don't want a when it rains the whole time!

* Calculate the rainfall per weather station using the previous year's matching dates.

  * Sort this in descending order by precipitation amount and list the station, name, latitude, longitude, and elevation.


### Daily Temperature Normals

* Calculate the daily normals for the duration of your trip. Normals are the averages for the min, avg, and max temperatures. You are provided with a function called `daily_normals` that will calculate the daily normals for a specific date. This date string will be in the format `%m-%d`. Be sure to use all historic TOBS that match that date string.

  * Set the start and end date of the trip.

  * Use the date to create a range of dates.

  * Strip off the year and save a list of strings in the format `%m-%d`.

  * Use the `daily_normals` function to calculate the normals for each date string and append the results to a list called `normals`.

* Load the list of daily normals into a Pandas DataFrame and set the index equal to the date.

* Use Pandas to plot an area plot (`stacked=False`) for the daily normals.

  ![daily-normals](Images/daily-normals.png)

* Close out your session.

## Rubric

[Unit 10 Rubric - SQLAlchemy Homework - Surfs Up!](https://docs.google.com/document/d/1gT29iMF3avSvJruKpcHY4qovP5QitgXePqtjC6XESI0/edit?usp=sharing)

- - -

## References

Menne, M.J., I. Durre, R.S. Vose, B.E. Gleason, and T.G. Houston, 2012: An overview of the Global Historical Climatology Network-Daily Database. Journal of Atmospheric and Oceanic Technology, 29, 897-910, [https://doi.org/10.1175/JTECH-D-11-00103.1](https://doi.org/10.1175/JTECH-D-11-00103.1)

- - -

© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.
