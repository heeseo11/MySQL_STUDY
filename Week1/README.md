

Q1. [모든 레코드 조회하기](https://programmers.co.kr/learn/courses/30/lessons/59034)

  - 오름차순 정렬
  
  ```MYSQL
    SELECT * 
    FROM ANIMAL_INS 
    ORDER BY ANIMAL_ID ASC
  ```

Q2. [역순 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59035)

  - 내림차순 정렬
  
  ```MYSQL
    SELECT NAME, DATETIME 
    FROM ANIMAL_INS 
    ORDER BY ANIMAL_ID DESC
  ```

Q3. [아픈 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59036)

  - 조건문 
  
  ```MYSQL
    SELECT ANIMAL_ID, NAME 
    FROM ANIMAL_INS 
    WHERE INTAKE_CONDITION = "Sick"
  ```

Q4. [최댓값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59415)

  - 최댓값 구하기
  - TABLE 이름 변경

  ```MYSQL
    SELECT MAX(DATETIME) AS "시간" 
    FROM ANIMAL_INS
  ```
