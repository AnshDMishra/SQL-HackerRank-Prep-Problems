### Prepare SQL Basic Join

#
**[Average population of each continent](https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?isFullScreen=true)**

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows:

### CITY
|  Field  |  Type  |
|----|----|
|  ID  |  NUMBER  |
|  NAME  |  VARCHAR2 (17)|
|  COUNTRYCODE  | VARCHAR2 (3) |
|  DISTRICT  |  VARCHAR2 (20)  |
|  POPULATION  |  NUMBER |


### COINTRY
| Field          | Type        |
|----|----|
| Code           | char(3)     |
| Name           | char(52)    |
| Continent      | char(50)    |
| Region         | char(26)    |
| SurfaceArea    | float(10,2) |
| IndepYear      | smallint(6) |
| Population     | int(11)     |
| LifeExpectancy | float(3,1)  |
| GNP            | float(10,2) |
| GNPOld         | float(10,2) |
| LocalName      | char(45)    |
| GovernmentForm | char(45)    |
| HeadOfState    | char(60)    |
| Capital        | int(11)     |
| Code2          | char(2)     |


**Solution**
```sql
SELECT Country.Continent, FLOOR(AVG(City.Population))
FROM Country, City 
WHERE Country.Code = City.CountryCode 
GROUP BY Country.Continent ;

```

#
**[The Report](https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true)**

You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

| _Column_ | _Type_ |
|----|----|
|  ID  |  Integer|
|  Name | String |
|  Marks  | Integer |

Grades contains the following data:

| Grade | Min_Mark |  Max_Mark  |
|----|----|----|
|  1  |  0  |  9  |
|  2  |  10  |  19  |
|  3  |  20  |  29  |
|  4  |  30  |  39  |
|  5  |  40  |  49  |
|  6  |  50  |  59  |
|  7  |  60  |  69  |
|  8  |  70  |  79  |
|  9  |  80  |  89  |
|  10  |  90  |  100  |

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. 
The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, 
order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. 
If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

Sample Input
| ID | Name |  Marks  |
|----|----|----|
|  1  |  Julia  |  88  |
|  2  |  Samantha  |  68  |
|  3  |  Maria  |  99  |
|  4  |  Scarlet  |  78  |
|  5  |  Ashley  |  63  |
|  6  |  Jane  |  81  |


Sample Output
```
Maria 10 99
Jane 9 81
Julia 9 88 
Scarlet 8 78
NULL 7 63
NULL 7 68
```

##### Note

Print "NULL"  as the name if the grade is less than 8.

Explanation
Consider the following table with the grades assigned to the students:

| ID | Name |  Marks  |  Grade  |
|----|----|----|----|
|  1  |  Julia  |  88  |  9  |
|  2  |  Samantha  |  68  |  7  |
|  3  |  Maria  |  99  |  10  |
|  4  |  Scarlet  |  78  |  8  |
|  5  |  Ashley  |  63  |  7  |
|  6  |  Jane  |  81  |  9  |


So, the following students got 8, 9 or 10 grades:

Maria (grade 10)
Jane (grade 9)
Julia (grade 9)
Scarlet (grade 8)
  
#
**Solution**
```sql
SELECT 
CASE WHEN grd.grade < 8 THEN NULL 
WHEN grd.grade >= 8 THEN std.name END,
grd.grade, std.marks FROM students std, grades grd
WHERE std.marks BETWEEN grd.min_mark AND grd.max_mark
ORDER BY grd.grade DESC, std.name ASC;

```
  
  
  




