Q1. [Delete Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/)

  - DELETE
  
    ```MYSQL
    DELETE P1 
    FROM Person P1, Person P2
    WHERE P1.Email = P2.Email 
    AND P1.Id > P2.Id
    ```
  
Q2. [Rising Temperature](https://leetcode.com/problems/rising-temperature/)

  - DATEDIFF
  
    ```MYSQL
    SELECT W1.id
    FROM Weather AS W1, Weather AS W2
    WHERE DATEDIFF(W1.recordDate,W2.recordDate) = 1 
    AND W1.Temperature > W2.Temperature
    ```
    
  - INNER JOIN
  
    ```MYSQL
    SELECT W1.id
    FROM Weather AS W1 
    INNER JOIN Weather AS W2 ON DATEDIFF(W1.recordDate,W2.recordDate) = 1
    WHERE W1.Temperature > W2.Temperature
    ```


Q3. [Big Countries](https://leetcode.com/problems/big-countries/)

  - WHERE, OR
  
    ```MYSQL
    SELECT name, population, area  
    FROM World 
    WHERE area > 3000000 OR population > 25000000
    ```
 
Q4. [Classes More Than 5 Students](https://leetcode.com/problems/classes-more-than-5-students/)

   - GROUP BY / HAVING

      ```MYSQL
      SELECT class 
      FROM courses 
      GROUP BY class
      HAVING COUNT(DISTINCT student)>=5
      ```
 
Q5. [Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)

  - MOD 

    ```MYSQL
    SELECT id, movie, description, rating 
    FROM Cinema 
    WHERE MOD(id, 2) = 1 
    AND description != 'boring'
    ORDER BY rating DESC
    ```
