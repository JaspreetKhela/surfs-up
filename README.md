# Surf Shop Analysis

## Overview of the Analysis

### Purpose
The purpose of this analysis was to determine whether or not the weather in June and December is ideal for operating a surf shop (which sells surf boards and ice cream) in different locations within Hawaii. Specifically, we wanted to determine the measures of central tendency and spread of temperatures by generating temperature summary statistics for each of the aforementioned months.

## Results
First, we can observe the temperature summary statistics of the temperature for June and December in the tables below.

### Summary Statistics
_____

<img width="150" alt="june_summary_statistics" src="https://user-images.githubusercontent.com/80941606/192936315-07b2c8a2-df6c-4018-bcc9-7f7060700b68.png">

**Table 1**: Temperature summary statistics for June.

_____

<img width="173" alt="december_summary_statistics" src="https://user-images.githubusercontent.com/80941606/192936339-1c452a8f-043b-4d2c-bd7a-5027fe13962a.png">

**Table 2**: Temperature summary statistics for September.

_____

### Insights

From the tables above, we can see that:
* The historical minimum temperature in June is eight degrees fahrenheit greater than that of December (which has a minimum temperature of fifty-six degrees fahrenheit). Assuming that prospective patrons would only consider purchasing ice cream if the local temperature was greater than sixty degrees fahrenheit, sales would be higher in June than they would be in December. Moreover, since December is on average colder than June is, the decreased ice cream sales and increased heating bill will shrink profit margins for the month of December.
* Given that the median and maximum temperatures for both June and December are comparable and given the point above, the surf shop can stay open for June and the first half of December (assuming that the day-by-day temperature decreases in the month of December as winter approaches). This rapid decline in temperature during December is supported by the fact that the standard devitation of the temperatures in December is greater than that of June.
* Given that June and December are roughly six months apart yet the measures of central tendency and spread between the two months are comparable (although, in particular, the mean temperature in June is roughly four degrees fahrenheit greater than that of December), one could make the argument that the surf shop could remain open for the entire year.

## Summary

### Take-Away
In summary, the surf shop could stay open for the entire year given that the temperature fluctuations throughout the year are minimal; thus, it would not be an issue serving ice cream throughout the year.

### Additional Queries
The following database queries would allow us to extract additional insights that will allow us to make more informed decisions on the viability of surf shops based on their prospective locations and temperatures at those locations.

_____

![stations_measurements_count](https://user-images.githubusercontent.com/80941606/193129043-ae5d9348-1fb3-404f-9662-d84aec70957f.png)

**Figure 1**: The temperature measurements counts grouped by measurement station.

The query used to create this figure was:
```
session.query(Measurement.station, func.count(Measurement.station)).group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
```
_____

Figure 1 illustrates a query for finding the location that we have the most temperature data on. As we can see, the "USC00519281" location has the most temperature measurements.

_____

![station_temperature_histogram](https://user-images.githubusercontent.com/80941606/193129061-43955b7d-82bf-4e51-94e4-b4685008d9da.png)

**Figure 2**: The temperature histogram for the station with the most measurements count.

The query used to create this figure was:
```
results = session.query(Measurement.tobs).filter(Measurement.station == 'USC00519281').filter(Measurement.date >= prev_year).all()
```
_____

Figure 2 illustrates a query that plots a temperature histogram for the location with the most temperature measurements found in Figure 1. 

We can see that the temperature at this location lingers mostly around seventy-five degrees fahrenheit for most of the year. This temperature is ideal for selling ice cream. Thus, we can recommend opening the surf shop in this and nearby locations.
