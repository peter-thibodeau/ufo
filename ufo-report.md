# Introduction
I will analyze the data to answer the following questions about UFO sightings:
1. Do they occur more in the daytime or nightime?
2. Is it seasonal?
3. Are there trends over time?
4. What are the most common UFO descriptions? 
5. Where are the hotspots?
6. Are there certain landmarks that are hotspots, such as airports or government research centers? 

# Data Source
The sightings are from the National UFO Reporting Center (NUFORC) which was acquired by Sigmond Axel and can be found at https://github.com/planetsig/ufo-reports. I downloaded it as a .csv file.  

NUFORC allows the use of the data for non-commericial uses. There is a caveat on the website that states: "The National UFO Reporting Center makes no claims as to the validity of the information in any of these reports. Obvious hoaxes have been omitted, however most reports have been posted exactly as received in the author’s own words." The NUFORC website address is https://nuforc.org/.


# Data Exploration
There are 88,876 records and 11 variables.

## Variable Descriptions
|Variable|Datatype|Description|
|:---|:---|:---|
|datetime|datetime|time of sighting|
|city|string|entered by the user|
|state|string|entered by the user|
|country|string|entered by the user|
|shape|string|entered by the user|
|duration (seconds)|integer|entered by the user|
|duration (hours/min)|string|entered by the user|
|comments|string|entered by the user|
|date posted|datetime|entered by the user|
|latitude|datetime|decimal|
|longitude|datetime|decimal|


## Nulls and Unique Values
| Variable           | Null     | Unique  |
| :---| :--- | :--- |
| timestamp          | 0        | 0            |
| age                | 0        | 0            |

## Variable Handling
| Variable           | Note                                      | Omit|
| :--- | :--- | :--- |
| timestamp          | not relevant to analysis                  | Omit|
| age                | not relevant to analysis                  | Omit|

# Data Cleaning
- Remove leading and trailing spaces.
- Remove duplicate records.
- Remove null values in industry, education, gender, and race variables.
- Change strings to upper case.
- Remove punctuation marks.
- Change the datatype of annual_salary to an integer.

## Filtering
**Age**  
The age for earning an annual salary can be assumed to apply only to adults, so remove records 

## New Variables
Records with a currency other than U.S. dollars must be converted to U.S. dollars for a 
