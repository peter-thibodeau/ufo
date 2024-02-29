# Introduction

# Data Source

# Data Exploration
The table contains 28,014 records and 17 variables.

## Variable Descriptions
| Variable           | Datatype | Description |
| :---               | :---     | :--- |
| timestamp          | datetime | a unique string automatically assigned to each new record

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
