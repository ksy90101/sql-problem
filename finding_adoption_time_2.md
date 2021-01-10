# [\[프로그래머스\] 입양 시각 구하기(2)](https://programmers.co.kr/learn/courses/30/lessons/59413)

## 문제 설명

ANIMAL_OUTS 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. ANIMAL_OUTS 테이블 구조는 다음과 같으며, ANIMAL_ID, ANIMAL_TYPE, DATETIME, NAME, SEX_UPON_OUTCOME는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

NAME | TYPE | NULLABLE
:---: | :---: | :---:
ANIMAL_ID | VARCHAR(N) | FALSE
ANIMAL_TYPE | VARCHAR(N) | FALSE
DATETIME | DATETIME | FALSE
NAME | VARCHAR(N) | TRUE
SEX_UPON_OUTCOME | VARCHAR(N) | FALSE

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

### 예시
SQL문을 실행하면 다음과 같이 나와야 합니다.

HOUR | COUNT
:---: | :---:
0 | 0
1 | 0
2 | 0
3 | 0
4 | 0
5 | 0
6 | 0
7 | 3
8 | 1
9 | 1
10 | 2
11 | 13
12 | 10
13 | 14
14 | 9
15 | 7
16 | 10
17 | 12
18 | 16
19 | 2
20 | 0
21 | 0
22 | 0
23 | 0

본 문제는 [Kaggle의 Austin Animal Center Shelter Intakes and Outcomes](https://www.kaggle.com/aaronschlegel/austin-animal-center-shelter-intakes-and-outcomes)
에서 제공하는 데이터를 사용하였으며 [ODbL](https://opendatacommons.org/licenses/odbl/1-0/) 의 적용을 받습니다.

## 참고자료
[ORACLE, MYSQL 날짜에서 각 값들을 추출하기 🧐](https://github.com/ksy90101/TIL/blob/master/database/datetime-extract-each-value.md)

## 정답

### MYSQL 
```mysql
SET @HOUR = -1;

SELECT (@HOUR := @HOUR + 1) AS HOUR, (SELECT COUNT(*)
                                      FROM ANIMAL_OUTS
                                      WHERE HOUR(DATETIME) = @HOUR
) AS COUNT
FROM ANIMAL_OUTS
WHERE @HOUR < 23
ORDER BY HOUR;
```

### ORACLE
```oracle
SELECT l.lvl AS HOUR , NVL(a.CNT, 0) AS COUNT
FROM (SELECT
          LEVEL-1 AS lvl
      FROM dual
      CONNECT BY LEVEL <= 24
     ) l,
     (SELECT
          EXTRACT(HOUR FROM CAST(DATETIME AS TIMESTAMP)) AS H, COUNT(*) AS CNT
      FROM ANIMAL_OUTS
      GROUP BY EXTRACT(HOUR FROM CAST(DATETIME AS TIMESTAMP))) a
WHERE l.lvl = a.H(+)
ORDER BY HOUR;
```