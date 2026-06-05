# Lab: SQL injection UNION attack, finding a column containing text

**Difficulty:** Practitioner

## Vulnerability
Unsanitised queries for the category filter

## How It Works
I can utilise UNION to tag my own columns onto the existing SQL output table.
Once i know how many columns there are in the original table, I can probe for columns that accept strings.
Once i find one, I may enter my own string data.
String columns are also how usernames and passwords are stored, so identifying them is key.

## What I Did
1. I injected the SQL with ' ORDER BY 1-- until i got to 4 where it errored.
2. This tells me that there are 3 columns, so I double check with ' UNION SELECT NULL,NULL,NULL--.
3. That returned no errors, so next I probe for a column that accepts string by using a test value 'a' in ' UNION SELECT 'a',NULL,NULL-- for each column.
4. This returned errors on all except the middle column, so I know that accepts strings.
5. I then enter the string to complete the lab into this column using ' UNION SELECT NULL,'zyn2UK',NULL--.
6. This inserts 'zyn2UK' into the middle column of the application table.

## Key Payload / Command
' UNION SELECT NULL,'a',NULL--

## Mitigation
A developer must utilise parameterised queries to prevent SQL injection such as this.

## What I Learned
I learned that I can probe for accepted data types in UNION SQLi by utilising test values.
I also learnt that I can inject my own values into the database.
