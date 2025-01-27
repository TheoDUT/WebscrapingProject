# Data recovery and cleaning
This repository contains the collected data that make up our dataset, as well as the notebook (Collecting_data.ipynb) used to collect and clean it.  

Our dataset consists of two CSV files:  
A file named "dataset.csv", which contains data scraped from Google Maps.  
It includes 9 columns and 99 rows, featuring information about tourism-related establishments in Paris.  
The 9 columns are: the establishment's name, its address, latitude, longitude, review score, number of reviews,
content of some reviews, the category of the establishment (art, museum, bike, cruise, mall, parks, tour),
and the impact of climate on these activities (ranging from 0 for low to 2 for high impact).  

A file named "daily_data.csv", which contains data obtained through an API call to Open-Meteo.  
It includes 20 columns and 3,654 rows, featuring meteorological data for Paris over the past 10 years.  
The columns are: Date, Weather Code, Maximum Temperature (2 m), Minimum Temperature (2 m), Mean Temperature (2 m),
Maximum Apparent Temperature (2 m), Minimum Apparent Temperature (2 m), Mean Apparent Temperature (2 m), Sunrise, Sunset, Daylight Duration,
Sunshine Duration, Precipitation Sum, Rain Sum, Snowfall Sum, Precipitation Hours, Maximum Wind Speed (10 m), Maximum Wind Gusts (10 m),
Dominant Wind Direction (10 m), and Shortwave Radiation Sum.


It was not necessary to clean the data from the API call as it was ready for use.  
However, several modifications had to be made to the Google Maps data:  
We started by rounding the latitude and longitude to two decimal places.  
Next, we cleaned the information in the *reviews* column.  
We began by removing the word *"stars"* from the part containing the user's rating.  
Then, we aimed to approximate the upload date of the review. To achieve this, we removed the phrase "il y a .." (e.g., "X months ago") 
and subtracted the indicated duration (X months, X weeks, X days) to estimate the publication date.  

Finally, we added two new columns:  
A "category" column, defining the type of establishment.  
A "weather_impact" column, indicating the extent to which we believe weather affects the user experience.  

Collecting 10 years of meteorological data for Paris provides a comprehensive, realistic, and fully exploitable dataset.  

For technical reasons, we decided to focus on only 7 categories of activities available in Paris, with around 14 establishments per category. 
However, many more options exist beyond those included in our dataset.  

# Here is a tutorial on how to use our app :

1. Open "Collecting_data.ipynb" on your computer (not googgle collab).
2. Execute every cells and wait for the datasets to be created.
3. Now that "dataset.csv" and "daily_dataset.csv" are created you can open "Prediction_project.ipynb" on Google Collab.
4. Then slide "dataset.csv" and "daily_dataset.csv" on the "file" part of google collab.
5. Execute every cells
6. Go on the last cell and update the "data" variable (used to create df_custom) with the input you want for the prediction
7. Execute the last cell
8. You now have a prediction of your activity rating based on your weather data