Q1. [입양 시각화 구하기(1)](https://programmers.co.kr/learn/courses/30/lessons/59412)

  - HAVING HOUR >= 9 AND HOUR <=19
  
  ```MYSQL
    SELECT HOUR(DAtETIME) AS HOUR, COUNT(DATETIME)AS COUNT
    FROM ANIMAL_OUTS
    GROUP BY HOUR(DATETIME) 
    HAVING HOUR >= 9 AND HOUR <=19
    ORDER BY HOUR
  ```
 - WHERE HOUR(DATETIME) BETWEEN 9 AND 19
 
  ```MYSQL
    SELECT HOUR(DATETIME) as HOUR, COUNT(DATETIME) as COUNT
    FROM ANIMAL_OUTS
    WHERE HOUR(DATETIME) BETWEEN 9 AND 19
    GROUP BY HOUR(DATETIME)
    ORDER BY HOUR(DATETIME)
```

Q2. [이름에 el이 들어가는 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59047)

  - WHERE / LIKE / AND
  
  ```MYSQL
    SELECT ANIMAL_ID, NAME 
    FROM ANIMAL_INS
    WHERE NAME LIKE '%EL%'
    AND ANIMAL_TYPE = 'DOG'
    ORDER BY NAME
  ```

Q3. [중복 제거하기](https://programmers.co.kr/learn/courses/30/lessons/59408)

  - DISTINCT
  
  ```MYSQL
    SELECT COUNT(DISTINCT NAME) AS COUNT FROM ANIMAL_INS
  ```

Q4. [최솟값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59038)

  - MIN

  ```MYSQL
    SELECT MIN(DATETIME) AS '시간' FROM ANIMAL_INS
  ```
  
Q5. [중성화 여부 파악하기](https://programmers.co.kr/learn/courses/30/lessons/59409)

  -  IF / LIKE / OR

  ```MYSQL
    SELECT ANIMAL_ID, NAME,
    IF(SEX_UPON_INTAKE LIKE '%Neutered%' OR SEX_UPON_INTAKE LIKE '%Spayed%','O','X') AS '중성화'
    FROM ANIMAL_INS
  ```
