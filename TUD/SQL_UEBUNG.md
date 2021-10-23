```sql
SELECT c.name SUM(s.population)
FROM country c INNER JOIN city s ON c.code=s.country
WHERE s.population > 1000000
GROUP BY c.name
ORDER BY 2


SELECT c.name, SUM(b2.length)
FROM country c INNER JOIN borders b1 ON c.code=b1.country1 OR c.code=b1.country INNER JOIN borders b2 ON c.code = b2.country1 OR c.code = b2.country2
WHERE c.code != 'D' AND b1.country = 'D'
GROUP BY c.name

SELECT c.name SUM(s.population)*100/c.population anteil
FROM city s INNER JOIN country c ON s.country = c.code
WHERE s.population > 1000000
GROUP BY c.name
HAVING SUM(s.population)*100 > 0.3*c.population
ORDER BY SUM(s.population)*100/c.population

SELECT c.name count(*)
FROM country c INNER JOIN borders b ON c.code=b.country1 OR c.code=b.country2
GROUP BY name
HAVING COUNT(*) > (SELECT COUNT(*)
                   FROM borders b
                   WHERE (b.country1='D' OR b.country2='D'))
                   

SELECT city
FROM located
WHERE river IS NOT NULL AND lake IS NOT NULL

SELECT DISTINCT c.name
FROM country c INNER JOIN geo_countain gm ON c.code=gm.country INNER JOIN mountain m ON gm.mountain = m.name
WHERE m.height > 4000

SELECT c.name
FROM country c INNER JOIN city s ON c.code=s.country INNER JOIN city hs ON c.code=hs.country AND c.capital = hs.name
WHERE s.population > hs.population

SELECT s.name, c.name
FROM country c INNER JOIN city s ON c.code=s.country
WHERE s.population = (SELECT MAX(population)
                      FROM city)
























```

