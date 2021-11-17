
# general

SQL is a powerful [[database]] language.

#lineendings should be terminated with semi-colon ;

#keywords should be capitalised

#singlequotes are for literal strings

#doublequotes are for identifiers

# commands (keywords)


SELECT -> returns results or set of results from a query
SELECT name, continent, region FROM country WHERE continent='Europe' ORDER BY Name LIMIT 5;

FROM -> tells where to get the data from in this case a table in our database. **Needs to be first after select**

ORDER BY -> returns results ordered by clauss i.e. FROM country ORDER BY name; **Must be after any WHERE clause**

AS -> creates an alias name for column this can be omitted!

LIMIT -> only returns the number of results after limit. e.g. LIMIT 5 returns first 5.

OFFSET -> offsets limit. e.g. if LIMIT 5 OFFSET 5 it will return from 5 to 10 not 0 to 5. **Needs to be last**


# functions

## count
Select COUNT(\*) FROM Country; returns a count of all rows in country table

SELECT COUNT(\*) FROM country WHERE population > 100000;
