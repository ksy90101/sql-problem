# [\[프로그래머스\] 모든 레코드 조회하기](https://programmers.co.kr/learn/courses/30/lessons/59034?language=mysql)

## 문제

### 문제 설명

ANIMAL_INS 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. ANIMAL_INS 테이블 구조는 다음과 같으며, ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

<br/>

| NAME | TYPE | NULLABLE |
| :-: | :-: | :-: |
| ANIMAL\_ID | VARCHAR(N) | FALSE |
| ANIMAL\_TYPE | VARCHAR(N) | FALSE |
| DATETIME | DATETIME | FALSE |
| INTAKE\_CONDITION | VARCHAR(N) | FALSE |
| NAME | VARCHAR(N) | TRUE |
| SEX\_UPON\_INTAKE | VARCHAR(N) | FALSE |

<br/>

동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID | ANIMAL_TYPE | DATETIME | INTAKE_CONDITION | NAME | SEX_UPON_INTAKE |
| :---: | :---: | :---: | :---: | :---: | :---: |
| A349996 | Cat | 2018-01-22 14:32:00 | Normal | Sugar | Neutered Male |
| A350276 | Cat | 2017-08-13 13:50:00 | Normal | Jewel | Spayed Female | 
| A350375 | Cat | 2017-03-06 15:01:00 | Normal | Meo | Neutered Male | 
| A352555 | Dog | 2014-08-08 04:20:00 | Normal | Harley | Spayed Female | 

..이하 생략

<br/>

본 문제는 Kaggle의  
[Austin Animal Center Shelter Intakes and Outcomes](https://www.kaggle.com/aaronschlegel/austin-animal-center-shelter-intakes-and-outcomes)  
에서 제공하는 데이터를 사용하였으며  
[ODbL](https://opendatacommons.org/licenses/odbl/1.0/)  
의 적용을 받습니다.
## 정답

- MySQL

```sql
SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID;
```

- Oracle

```sql
SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID;
```
## 설명

### SELECT
- 데이터 검색하고 칼럼을 가공 처리하여 조회를 가능하게 한다.
- 테이블 전체 조회
> SELECT * FROM 테이블명;
- 테이블 내 컬럼 조회
> SELECT 컬럼1, 컬럼2, ... FROM 테이블명;
- 테이블 내 특정 데이터만 조회
> SELECT * FROM 테이블명 WHERE 컬럼명 = "값";
- 특정 정렬 기준 조회
    - ASC : 오름차순(생략 가능)
    - DESC : 내림차순
> SELECT * FROM 테이블명 ORDER BY 컬럼명 [ASC/DESC]