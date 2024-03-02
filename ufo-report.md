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
- There are 88,876 records and 11 variables.
- There are 9 duplicate records.

## Variable Descriptions
|Variable|Datatype|Description|Nulls|Notes|
|:---|:---|:---|:---|:--|
|datetime|datetime|time of sighting, entered by user|0||
|city|string|entered by the user|0|22,017 unique cities|
|state|string|entered by the user|7,409||
|country|string|entered by the user|12,365|6 unique countries|
|shape|string|entered by the user|2,922|29 unique shapes|
|duration (seconds)|integer|entered by the user|2||
|duration (hours/min)|string|entered by the user|3,017||
|comments|string|entered by the user|35||
|date posted|datetime|entered by the user|0||
|latitude|datetime|decimal|0|note 1|
|longitude|datetime|decimal|0|note 1|

Note 1: zero latitude and longitude is located in the middle of the Indian Ocean and therefor not useful.

# Data Cleaning
Several variable names are unrecognizable by SQL and have to be changed as shown in the following table:

|Variable|New name|
|:---|:---|
|duration (seconds|duration_sec|
|duration (hours/min)|duration_hour_min|
|date posted|date_posted|

- Remove leading and trailing spaces.
- Change strings to upper case to simplify SQL queries.
- Remove duplicate records.
- Remove punctuation marks in city.

## Filtering
- City records with strings that contain location unspecified, unspecified location, unspecified, not specified, deleted, unknown, above, a field, hoax, airplane, and plane and will be removed.
- City records that hold only the name of a state will be removed.
- Records where city and country are null don't hold enough information to determine a location and will be removed.
- There are 22,017 unique city values those that are less than 5% of total will be removed to keep plotting manageable.
- Remove records where shape is null because shape is need for describing the UFO.
- Vales of zero latitude and zero longitude are located in the middle of the Indian Ocean and will be removed.

## New Variables
- Add country code where missing if country name is in city string.
