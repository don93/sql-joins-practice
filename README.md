# Join Practice

Use the `world.sql` file to answer the following questions.

Remember, you can use the `.schema` command in the sqlite terminal to see the
format of all the current tables. It looks something like this:

```
sqlite> .schema
CREATE TABLE city (
    id integer NOT NULL,
    name text NOT NULL,
    countrycode character(3) NOT NULL,
    district text NOT NULL,
    population integer NOT NULL,
);
CREATE TABLE country (
    code character(3) NOT NULL,
    name text NOT NULL,
    continent text NOT NULL,
    region text NOT NULL,
    surfacearea real NOT NULL,
    indepyear smallint,
    population integer NOT NULL,
    lifeexpectancy real,
    gnp numeric(10,2),
    gnpold numeric(10,2),
    localname text NOT NULL,
    governmentform text NOT NULL,
    headofstate text,
    capital integer,
    code2 character(2) NOT NULL
);
CREATE TABLE countrylanguage (
    countrycode character(3) NOT NULL,
    "language" text NOT NULL,
    isofficial boolean NOT NULL,
    percentage real NOT NULL
);
```

## Find the Capital of Brazil
Write a query that returns the name of the capitol and the country for Brazil.

```
name        name      
----------  ----------
Brasilia  Brazil    
```

## Languages Spoken in the United States
Write a query that returns the name of each language and its percentage, ordered
from top to bottom starting with the highest percentage for just the United States.

## Percentage French Where Official

Query for the name of the country, the language, the percentage of the language, and
the state of whether the language `isofficial` for French.

```
name        language    percentage  isofficial
----------  ----------  ----------  ----------
Monaco      French      41.900002   t         
France      French      93.599998   t         
Saint Pier  French      0.0         t         
Belgium     French      32.599998   t         
Burundi     French      0.0         t         
Guadeloupe  French      0.0         t         
Haiti       French      0.0         t         
Canada      French      23.4        t         
Madagascar  French      0.0         t         
Martinique  French      0.0         t         
Mayotte     French      20.299999   t         
French Pol  French      40.799999   t         
Rwanda      French      0.0         t         
Switzerlan  French      19.200001   t         
New Caledo  French      34.299999   t         
Seychelles  French      1.3         t         
Vanuatu     French      14.2        t         
Luxembourg  French      4.1999998   t  
```

## Beware: Solutions Lurk Past 'ere

```
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
all work and no play makes jack a dull boy
```

## Solutions

Find the capitol of Brazil.

```sql
SELECT city.name, country.name
FROM city, country
WHERE city.countrycode = country.code
AND country.name = "Brazil"
AND country.capital == city.id;
```

```sql
SELECT "language",percentage
FROM countrylanguage, country
WHERE country.code = countrylanguage.countrycode
AND country.name = "United States"
ORDER BY percentage DESC;
```

```
SELECT country.name, "language", percentage, isofficial
FROM country JOIN countrylanguage
ON country.code = countrylanguage.countrycode
WHERE "language" = "French"
AND isofficial = 't';
```

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
