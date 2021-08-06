Q1. [오랜 기간 보호한 동물(2)](https://programmers.co.kr/learn/courses/30/lessons/59411)

  - DATADIFF, INNER JOIN
  
  ```MYSQL
    SELECT INS.ANIMAL_ID, INS.NAME 
    FROM ANIMAL_INS  INS 
    INNER JOIN ANIMAL_OUTS OUTS 
    ON INS.ANIMAL_ID = OUTS.ANIMAL_ID
    ORDER BY DATEDIFF(INS.DATETIME, OUTS.DATETIME)
    LIMIT 2
  ```
  
Q2. [보호소에서 중성화한 동물](https://programmers.co.kr/learn/courses/30/lessons/59045)

  - WHERE / AND
  
 ```MYSQL
    SELECT OUTS.ANIMAL_ID, OUTS.ANIMAL_TYPE, OUTS.NAME 
    FROM ANIMAL_INS INS 
    INNER JOIN ANIMAL_OUTS OUTS 
    ON INS.ANIMAL_ID = OUTS.ANIMAL_ID
    WHERE (INS.SEX_UPON_INTAKE = 'Intact Male' OR INS.SEX_UPON_INTAKE = 'Intact Female') 
    AND (OUTS.SEX_UPON_OUTCOME = 'Spayed Female' OR OUTS.SEX_UPON_OUTCOME = 'Neutered Male')
    ORDER BY OUTS.ANIMAL_ID
 ```
 
  - JOIN / AND

 ```MYSQL
    SELECT I.ANIMAL_ID, I.ANIMAL_TYPE, I.NAME 
    FROM ANIMAL_INS as I 
    JOIN ANIMAL_OUTS as O 
    ON I.ANIMAL_ID = O.ANIMAL_ID 
    AND I.SEX_UPON_INTAKE != O.SEX_UPON_OUTCOME
    ORDER BY I.ANIMAL_ID
 ```
 
  - WHERE / AND / (조건 OR 조건)
 ```MYSQL
    SELECT I.ANIMAL_ID, I.ANIMAL_TYPE, I.NAME
    FROM ANIMAL_INS AS I 
    INNER JOIN ANIMAL_OUTS AS O
    ON I.ANIMAL_ID = O.ANIMAL_ID
    WHERE I.SEX_UPON_INTAKE like "Intact%" and (O.SEX_UPON_OUTCOME like "Spayed%" or O.SEX_UPON_OUTCOME like "Neutered%")
    ORDER BY I.ANIMAL_ID ASC;
 ```

Q3. [입양 시각 구하기(2)](https://programmers.co.kr/learn/courses/30/lessons/59413)

  - @HOUR
  
  ```MYSQL
    SET @HOUR = -1;
    SELECT (@HOUR := @HOUR +1) AS HOUR,
        (SELECT COUNT(HOUR(DATETIME)) 
        FROM ANIMAL_OUTS 
        WHERE HOUR(DATETIME)=@HOUR) AS COUNT 
        FROM ANIMAL_OUTS
    WHERE @HOUR < 23;
  ```
  
  - WITH RECURSIVE

 ```MYSQL
    WITH RECURSIVE T AS (
    SELECT 0 AS NUM
    UNION ALL 
    SELECT NUM + 1
    FROM T
    WHERE NUM <= 22)  -- 반복되는 문장 정지 조건 
    SELECT NUM AS HOUR, COUNT(DATETIME)
    FROM T LEFT JOIN ANIMAL_OUTS AS A
    ON T.NUM = HOUR(A.DATETIME)
    GROUP BY HOUR
    ORDER BY HOUR;
 ```


Q4. [우유와 요거트가 담긴 장바구니](https://programmers.co.kr/learn/courses/30/lessons/62284)

  - 중첩 SELECT / INNER JOIN 

  ```MYSQL
    SELECT Yogurt.CART_ID
    FROM (SELECT CART_ID FROM CART_PRODUCTS WHERE NAME = 'Yogurt') Yogurt
    INNER JOIN (SELECT CART_ID FROM CART_PRODUCTS WHERE NAME = 'Milk') Milk
    ON Yogurt.CART_ID = Milk.CART_ID
  ```
 
  - WHERE / AND

  ```MYSQL
    SELECT Yogurt.CART_ID
    FROM CART_PRODUCTS AS Yogurt, CART_PRODUCTS  AS Milk
    WHERE Yogurt.CART_ID = Milk.CART_ID AND Yogurt.NAME = "Yogurt" AND Milk.NAME = "Milk"
    ORDER BY CART_ID ASC;
  ```
  
  - GROUP_CONCAT
  ```MYSQL
    SELECT CART_ID
    FROM CART_PRODUCTS
    GROUP BY CART_ID
    HAVING
        GROUP_CONCAT(NAME SEPARATOR ' ') LIKE '%Milk%'
        AND
        GROUP_CONCAT(NAME SEPARATOR ' ') LIKE '%Yogurt%'
  ```
 
Q5. [어린 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59037)

  - SELECT / WHERE / !=

  ```MYSQL
    SELECT  ANIMAL_ID, NAME 
    FROM ANIMAL_INS
    WHERE INTAKE_CONDITION != 'Aged'
    ORDER BY ANIMAL_ID
  ```

