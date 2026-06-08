# Lab: SQL injection UNION attack, retrieving data from other tables

**Difficulty:** Practitioner

## Vulnerability
Unsanitised inputs allows for SQL injection

## How It Works
I was told that there was a separate table called users which contained 2 columns, username and password.
I used methods from previous labs to check there were 2 columns, then used SELECT FROM to select the username and password columns from the users table.
Using UNION, I linked the 2 tables so they both were displayed on the page.

## What I Did
1. I checked how many columns there were in the original table because if I am to link the users table, they must have the same number of columns.
2. I did this by injecting ' UNION SELECT NULL,NULL--, then ' UNION SELECT NULL,NULL,NULL-- into the category filter. 
3. The one with 2 nulls did not error, but 3 did so i know there are 2 columns.
4. Now i can link the two tables by injecting ' UNION SELECT username,password FROM users--.
5. This links the two tables, so the usernames and passwords from the user tables is displayed.
6. I then used the displayed admin details to sign in as an admin.

## Key Payload / Command
' UNION SELECT username,password FROM users--

## Mitigation
Use parameterised inputs to prevent SQL injection.

## What I Learned
I learnt that UNION is the act of combining two tables into one to display data that is intended to be private.
