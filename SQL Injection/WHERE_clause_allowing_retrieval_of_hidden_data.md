# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

## Explanation
The main goal of this lab was to identify where the application was not doing sufficient filtering when combining the **WHERE condition** with user input and to understand how this was allowing records to be displayed that were not normally visible.

## Solution
First, I checked the application for SQL injection by adding a single quote to the category parameter in the URL, which produced an error and confirmed a potential injection point.  
Next, I modified `...category=Gifts` to `...category=Gifts'--` and noticed that additional records appeared.
Finally, I tested `...category=Gifts'+OR+1=1--`, which caused the application to return all records, including those that were normally hidden.


## Notes 
To avoid this type of vulnerability, the application should use parameterized queries (prepared statements) instead of directly concatenating user input into SQL statements.
