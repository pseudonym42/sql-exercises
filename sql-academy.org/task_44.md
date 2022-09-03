Find the maximum age (number of years) among grade 10 students 
(i.e. students which go to classes with '10' in their name).

For full details about the task see https://sql-academy.org/en/trainer/tasks/44

Note that the resultant field name should be `max_year`

```SQL
SELECT YEAR(CURDATE()) - YEAR(y.birthday) as max_year
FROM (
    SELECT birthday
    FROM (
        SELECT student 
        FROM Student_in_class AS sic
        INNER JOIN Class AS cl ON sic.class = cl.id
        WHERE cl.name LIKE '%10%'
    ) AS x
    INNER JOIN Student AS st ON x.student = st.id
    ORDER BY birthday ASC
    LIMIT 1
) AS y;

```