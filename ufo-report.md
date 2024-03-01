# Introduction
I will analyze the data to answer the following questions about UFO sightings:
1. Do they occur more in the daytime or nightime?
2. Is it seasonal?
3. Are there trends over time?
4. What are the most common UFO descriptions? 
5. Where are the hotspots? Are they near landmarks, such as airports or government research centers? 

# Data Source
The sightings are from the National UFO Reporting Center (NUFORC) which was acquired by Sigmond Axel and can be found at https://github.com/planetsig/ufo-reports. I downloaded it as a .csv file.  

NUFORC allows the use of the data for non-commericial uses. There is a caveat on the website that states: "The National UFO Reporting Center makes no claims as to the validity of the information in any of these reports. Obvious hoaxes have been omitted, however most reports have been posted exactly as received in the author’s own words." The NUFORC website address is https://nuforc.org/.

# Data Exploration
There are 88,876 records and 11 variables. All variables are useable but some need extensive cleaning.

## Variable Descriptions
|Variable|Datatype|Description|Nulls|
|:---|:---|:---|:---|
|datetime|datetime|time of sighting, entered by user|0|
|city|string|entered by the user|0|
|state|string|entered by the user|7,409|
|country|string|entered by the user|12,365|
|shape|string|entered by the user|2,922|
|duration (seconds)|integer|entered by the user|2|
|duration (hours/min)|string|entered by the user|3,017
|comments|string|entered by the user|35|
|date posted|datetime|entered by the user|0|
|latitude|datetime|decimal|0|
|longitude|datetime|decimal|0|

# Data Cleaning
Several variable names are unrecognizable by SQL and have to be changed as shown in the following table:

|Variable|New name|
|:---|:---|
|duration (seconds|duration_sec|
|duration (hours/min)|duration_hour_min|
|date posted|date_posted|

Other tasks required for cleaning the data are:  
- Remove leading and trailing spaces.
- Remove punctuation marks.
- Remove duplicate records.

Locations 
- Remove records where latitude and longitude values equal zero
- Change strings to upper case to simplify SQL queries.
- Where country variable is null, extract it from city where possible.

## Filtering
**Age**  
The age for earning an annual salary can be assumed to apply only to adults, so remove records 

## New Variables
Records with a currency other than U.S. dollars must be converted to U.S. dollars for a 
