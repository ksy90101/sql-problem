# [\[프로그래머스\] 역순 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59035)

## 문제 설명
ANIMAL_INS 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. ANIMAL_INS 테이블 구조는 다음과 같으며, ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME | TYPE | NULLABLE |
| :---: | :---: | :---: |
| ANIMAL_ID | VARCHAR(N) | FALSE |
| ANIMAL_TYPE | VARCHAR(N) | FALSE |
| DATETIME | DATETIME | FALSE |
| INTAKE_CONDITION | VARCHAR(N) | FALSE |
| NAME | VARCHAR(N) | TRUE | 
| SEX_UPON_INTAKE | VARCHAR(N) | FALSE |

동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

NAME | DATETIME
:---: | :---:
Rocky | 2016-06-07 09:17:00
Shelly | 2015-01-29 15:01:00
Benji | 2016-04-19 13:28:00
Jackie | 2016-01-03 16:25:00
*Sam | 2016-03-13 11:17:00
..이하 생략

본 문제는 [Kaggle의 Austin Animal Center Shelter Intakes and Outcomes](https://www.kaggle.com/aaronschlegel/austin-animal-center-shelter-intakes-and-outcomes)
에서 제공하는 데이터를 사용하였으며 [ODbL](https://opendatacommons.org/licenses/odbl/1-0/)의 적용을 받습니다.

## 정답

### ORACLE
```oracle
SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC;
```

```mysql
SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC;
```

### ORDER BY
- SELECT문을 사용했을때 정렬을 할때 사용합니다.
- 특정 컬럼에 대해서 오름차순, 내림차순을 할 수 있습니다.

> SELECT 컬럼 FROM 테이블 ORDER BY 정렬 기준이 될 컬럼 [ASC|DESC];

- 기본적으로 ASC(오름차순)이 적용이 되며, DESC는 내림차순으로 직접 명시해줘야 합니다.

- ORDER BY를 사용하지 않는다면 PK 기준으로 정렬되어 결과가 나옵니다.