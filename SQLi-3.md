# Lab: SQL injection UNION attack, determining the number of columns returned by the query

**Difficulty:** Practitioner

## Vulnerability
I was able to do a UNION attack due to unsanitised SQL input

## How It Works
UNION will join 2 SELECT queries, but they must have the same number of columns or it errors.
I just probed for the number of columns in the search filter query.
Knowing this lets me continue my attack (next labs)

## What I Did
1. Probed to find column number incrementally using ' ORDER BY 1--, ' ORDER BY 2-- etc.
2. I found that it returned an error on ' ORDER BY 4--, so i knew it had 3 columns.
3. I then confirm whether this is correct by injecting ' UNION SELECT NULL,NULL,NULL-- into the url.
4. This confirms that there are 3 columns, otherwise an error would be returned.

## Key Payload / Command
' ORDER BY 4--
' UNION SELECT NULL,NULL,NULL--

## Mitigation
There should be parameterised queries to prevent SQLi

## What I Learned
I learnt that I can find how many columns a query returns to the application using a UNION attack.
This is needed to perform a full UNION attack.
