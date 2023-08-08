```sql 
SELECT
      location
      , population
      , MAX(total_cases) AS 'MaxInfected'
      , MAX(total_deaths) AS 'MaxFatalities'
      , MAX((total_cases/population))*100 AS '%InfectedPerPop'
      , MAX((total_deaths/population))*100 AS '%FatalitiesPerPop'
      , (MAX(total_deaths)/MAX(total_cases))*100 AS '%FatalityRate'

FROM CovidDeaths

WHERE
      continent IS NULL
      AND location NOT LIKE '%income'
      AND location <> 'World'

GROUP BY location, population

ORDER BY '%InfectedPerPop' DESC
```
