#  Understanding Madrid’s pollution levels during the COVID-19 lockdown in Spain.
- Studied NO2 levels across all air quality control stations in Madrid city to see the effect of lockdown in each station. 
- The average impact detected was a reduction in NO2 levels of 46%. 
- Used weather and temporal data to study the impact of each variable in NO2 levels.
- Used spatialisation of stations to observe differences and patterns.
- Built a linear model for each station, month and day of the week that predicted NO2 levels (RMSE ~ 5.93 µg/m3)
- Detected stations with a higher impact because of lockdown. Stations in the north of Madrid were more affected than station in the south. The highest impact was observed in the station located at Madrid's airport, and the lowest impact in the station located at Villa de Vallecas. 
- The results of this project could be used to improve Madrid's air quality by looking at the effect of mobility restrictions around the area of each station. 

## Packages
**Python Version**: 3.8.3

**Packages used**: pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib, seaborn, folium

**Requirements**: <code>pip install -r requirements.txt</code>

## Source of data
The data was downloaded from Madrid City Council's open data portal. [Pollution levels hourly data](https://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=f3c0f7d512273410VgnVCM2000000c205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD&vgnextfmt=default) and [hourly weather data](https://datos.madrid.es/sites/v/index.jsp?vgnextoid=fa8357cec5efa610VgnVCM1000001d4a900aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD). 

## Data cleaning
The following changes were made to the original data:
- For each type of data (air quality and weather):
	- Converted row time series to column time series to better handle de data. 
	- In the air quality data, selected only the NO2 pollutant, that was measured in all stations. 
	- Selected only verified instances. 
	- Merged both datasets by date and time.
- Repeated the process for the months of March, April, May and Jun for 2019 and 2020. 
- Merged all the months together. 
- Added a "Year" column, a "Day of the week" column and a "Lockdown" column. 
- Removed instances with incorrect data (one of the instances contained a temperature below 30ºC)
- Evaluated Mahalanobis distance of each instance and removed outliers. 

The final data contained 96.2% of the original data. 

## EDA
The temporal evolution of NO2 levels looked like this:
![plot](https://github.com/jorgerodpen/MadridPollution/blob/master/temporalevolution.png "Temporal evolution of NO2 levels")