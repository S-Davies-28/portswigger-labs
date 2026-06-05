# Lab: SQL injection vulnerability allowing login bypass

**Difficulty:** Apprentice

## Vulnerability
The login function's SQL input was uncleansed so was vulnerable to SQL injection

## How It Works
The SQL contains SQL like SELECT * FROM users WHERE username = '' AND password = ''.
Since data is not cleansed, i may enter the username as administrator, since i know that's correct, but add '-- after it.
This comments out the password requirement, and therefore needs no password

## What I Did
1. I knew the username was administrator, and the data was uncleansed
2. I entered the username as administrator'--
3. This comments out the password requirement, so I gain access without needing a password

## Key Payload / Command
administrator'--

## Mitigation
Use parameterised queries so user input is always treated as data not code

## What I Learned
I learned that I can manipulate username inputs to gain access to information i am not authorised to see and an account I do not own.
