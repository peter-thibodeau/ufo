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
|datetime|datetime|time of sighting, entered by user|0|1,207 have less than 10 chars which is NG|
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

Note 1: there are 1,494 records where latitude and longitude both equal zero, that location is in the middle of the Indian Ocean and therefore not useful.

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
- Revove datetime strings that are less that 10 characters in length.

## Filtering
- City strings that contain location unspecified, unspecified location, unspecified, not specified, deleted, unknown, above, a field, hoax, airplane, and plane and will be removed.
- City strings that hold only the name of a state or country will be removed because they are to vague.
- Records where city and country are null don't hold enough information to determine a location and will be removed.
- Remove records where shape is null because shape is need for describing the UFO.
- Vales of zero latitude and zero longitude are located in the middle of the Indian Ocean and will be removed.
- There are 12,365 missing country values and 7,409 missing state values, but one or the other is required to determine location, records with missing country values will be removed.

## New Variables
- Add country code where missing if country name is in city string.
