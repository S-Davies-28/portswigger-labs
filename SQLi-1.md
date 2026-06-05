# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

**Difficulty:** Apprentice

## Vulnerability
SQL injection in the WHERE clause in the category filter.

## How It Works
The application required released to equal 1 (meaning it is released) in it's SQL for the category filter, ans since it was not properly sanitised, I could inject OR 1=1-- into the SQL.
This comments out the SQL saying released must equal 1 and replaces it with my condition saying that 1 must equal 1, which it always does.

## What I Did
1. Noticed that the category filter in the url was passing directly into the database
2. Tested whether it was sanitised by passing ' into it, new products appeared so it was not
3. Injected +OR+1=1-- into the url to show all products
4. All unreleased products showed

## Key Payload / Command
' OR 1=1--

## Mitigation
They could use parameterised queries in order to treat inputted data as separate data, so it cannot be confused as code

## What I Learned
I learned how the basics of SQLi work and that -- is a comment and can comment out data after it.
I also learned that + represents a space, and that you must sanitise inputted data to prevent SQLi
