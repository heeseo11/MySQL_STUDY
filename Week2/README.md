Q1. [고양이와 개는 몇 마리 있을까](https://programmers.co.kr/learn/courses/30/lessons/59040)

  - GROUP BY
  
  ```MYSQL
    SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS COUNT 
    FROM ANIMAL_INS 
    GROUP BY ANIMAL_TYPE 
    ORDER BY ANIMAL_TYPE
  ```

Q2. [루시와 엘라 찾기](https://programmers.co.kr/learn/courses/30/lessons/59046)

  - IN
  
  ```MYSQL
    SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE 
    FROM ANIMAL_INS 
    WHERE  NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
    ORDER BY ANIMAL_ID
  ```

Q3. [NULL 처리하기](https://programmers.co.kr/learn/courses/30/lessons/59410)

  - IF NULL
  
  ```MYSQL
    SELECT ANIMAL_TYPE, IFNULL(NAME,"No name") AS NAME, SEX_UPON_INTAKE 
    FROM ANIMAL_INS
    ORDER BY ANIMAL_ID
  ```

Q4. [동물 수 구하기](https://programmers.co.kr/learn/courses/30/lessons/59406)

  - SUM, MAX, MIN

  ```MYSQL
    SELECT COUNT(ANIMAL_ID) AS COUNT
    FROM ANIMAL_INS
  ```
  
Q5. [동명 동물 수 찾기](https://programmers.co.kr/learn/courses/30/lessons/59041)

  - GROUP BY 조건문 HAVING 

  ```MYSQL
     SELECT NAME, COUNT(NAME) AS COUNT 
     FROM ANIMAL_INS
     GROUP BY NAME HAVING COUNT(NAME) >= 2
     ORDER BY NAME
  ```
