Q1. [combine-two-tables](https://leetcode.com/problems/combine-two-tables/submissions/)

  - LEFT JOIN 
  
    ```MYSQL
    SELECT FirstName, LastName, City, State 
    FROM Person LEFT JOIN Address
    ON Person.PersonId = Address.PersonId
    ```
  
Q2. [second-highest-salary](https://leetcode.com/problems/second-highest-salary/submissions/)

  - 중첩 SELECT / IFNULL / LIMIT 1,1 
  
    ```MYSQL
    SELECT
    IFNULL(
    (SELECT DISTINCT Salary 
    FROM Employee 
    ORDER BY Salary DESC 
    LIMIT 1,1),NULL)
    AS SecondHighestSalary
    ```

Q3. [employees-earning-more-than-their-managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/submissions/)

  - WHERE 
  
    ```MYSQL
    SELECT A.Name AS Employee
    FROM Employee AS A ,Employee AS B
    WHERE A.Salary > B.Salary 
    AND A.ManagerId = B.Id 
    ```
 
Q4. [duplicate-emails](https://leetcode.com/problems/duplicate-emails/submissions/)

  - GROUP BY / HAVING

    ```MYSQL
    SELECT Email 
    FROM Person GROUP BY Email 
    HAVING COUNT(Email) > 1 
    ```
 
Q5. [customers-who-never-order](https://leetcode.com/problems/customers-who-never-order/solution/)

  - LEFT JOIN

    ```MYSQL
    SELECT C.NAME AS Customers 
    FROM Customers AS C 
    LEFT JOIN Orders AS O
    ON C.ID = O.CustomerID
    WHERE O.Id IS NULL
    ```
  - 중첩 SELECT / NOT IN 

    ```MYSQL
    SELECT C.Name AS Customers
    FROM Customers AS C
    WHERE C.Id NOT IN
    (
        SELECT CustomerId FROM Orders
    )
    ```
