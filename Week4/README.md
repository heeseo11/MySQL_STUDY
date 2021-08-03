Q1. [있었는데요 없었습니다](https://programmers.co.kr/learn/courses/30/lessons/59043)

  - WHERE OUTS.DATETIME <= INS.DATETIME
  
  ```MYSQL
    SELECT INS.ANIMAL_ID, INS.NAME 
    FROM ANIMAL_INS AS INS INNER JOIN ANIMAL_OUTS AS OUTS
    ON INS.ANIMAL_ID = OUTS.ANIMAL_ID
    WHERE OUTS.DATETIME <= INS.DATETIME
    ORDER BY INS.DATETIME
  ```
  
Q2. [없어진 기록 찾기](https://programmers.co.kr/learn/courses/30/lessons/59042)

  - LEFT OUTER JOIN / is NULL
  
  ```MYSQL
    SELECT OUTS.ANIMAL_ID, OUTS.NAME
    FROM ANIMAL_OUTS AS OUTS
    LEFT OUTER JOIN ANIMAL_INS AS INS
    ON OUTS.ANIMAL_ID = INS.ANIMAL_ID
    WHERE INS.ANIMAL_ID is NULL
    ORDER BY OUTS.ANIMAL_ID
  ```

Q3. [헤비 유저가 소유한 장소](https://programmers.co.kr/learn/courses/30/lessons/77487)

  - IN / GROUP BY HAVING
  
  ```MYSQL
    SELECT ID, NAME, HOST_ID 
    FROM PLACES 
    WHERE HOST_ID IN ( 
        SELECT HOST_ID 
        FROM PLACES 
        GROUP BY HOST_ID 
        HAVING COUNT(*) >= 2
)
  ```

Q4. [오랜 기간 보호한 동물(1)](https://programmers.co.kr/learn/courses/30/lessons/59044)

  - LEFT JOIN / IS NULL

  ```MYSQL
    SELECT INS.NAME, INS.DATETIME 
    FROM ANIMAL_INS AS INS LEFT JOIN ANIMAL_OUTS AS OUTS
    ON INS.ANIMAL_ID = OUTS.ANIMAL_ID
    WHERE OUTS.ANIMAL_ID IS NULL
    ORDER BY INS.DATETIME 
    LIMIT 3
  ```
  
Q5. [DATETIME에서 DATE로 형 변환](https://programmers.co.kr/learn/courses/30/lessons/59414)

  - DATE_FORMAT(DATETIME, '%Y-%m-%d'

  ```MYSQL
    SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') AS 날짜
    FROM ANIMAL_INS
  ```

