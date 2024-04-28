---
layout: default
title: SQL 응용
parent: 데이터베이스 구축
grand_parent: 정보처리기사

nav_order: 4.3
---

- [SQL(Structured Query Language)](#sqlstructured-query-language)
- [DDL(Data Define Language)](#ddldata-define-language)
- [DCL(Data Control Language)](#dcldata-control-language)
- [DML(Data Manipulate Language)](#dmldata-manipulate-language)
- [CREATE](#create)
- [ALTER](#alter)
- [DROP](#drop)
- [DELETE](#delete)
- [SELECT](#select)
- [DISTINCT](#distinct)
- [JOIN](#join)
  - [INNER JOIN](#inner-join)
    - [EQUI JOIN(NATURAL JOIN)](#equi-joinnatural-join)
    - [NON EQUI JOIN](#non-equi-join)
  - [OUTER JOIN](#outer-join)
    - [LEFT OUTER JOIN](#left-outer-join)
    - [RIGHT OUTER JOIN](#right-outer-join)
    - [SELF JOIN](#self-join)

# SQL(Structured Query Language)
국제 표준 데이터베이스 언어.  
관계형 데이터베이스를 지원하는 언어로 채택.
DDL, DML, DCL로 나뉨.

# DDL(Data Define Language)
SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하거나 변경 또는 삭제할 때 사용하는 언어.  
논리적 데이터 구조와 물리적 데이터 구조의 사상을 정의.  

- CREATE : SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의
- ALTER : TABLE의 정의 변경
- DROP : SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제

# DCL(Data Control Language)
데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의하는 데 사용

- COMMIT : 명령 결과를 물리적 디스크에 저장, 작업이 정상완료됨을 관리자에게 알림
- ROLLBACK : 데이터베이스 조작 작업이 비정상적으로 종료되었을 때 원래 상태로 복구
- GRANT : 데이터베이스 사용자에게 권한 부여
- REVOKE : 데이터베이스 사용자의 사용 권한을 취소

# DML(Data Manipulate Language)
데이터베이스 사용자가 응용프로그램이나 질의어를 통해 저장된 데이터를 실질적으로 처리하는데 사용되는 언어.  

- SELECT : 조건에 맞는 튜플 검색
- INSERT : 테이블에 새로운 튜플 삽입
- DELETE : 조건에 맞는 튜플 삭제
- UPDATE : 조건에 맞는 튜플 내용 변경

# CREATE
```
# 스키마
CREATE SCHEMA 스키마명 AUTHORIZATION 사용자_ID;
CREATE SCHEMA 대학교 AUTHORIZATION 홍길동;

# 도메인
CREATE DOMAIN 도메인명 AS 데이터 타입
    DEFAULT 기본값
    CONSTRAINT 제약조건명 CHECK(범위값);
CREATE DOMAIN SEX AS CHAR(1)
    DEFAULT '남'
    CONSTRAINT VALID-SEX CHECK(VALUE IN ('남','여'));

# 테이블
CREATE TABLE 테이블명
    (속성명 데이터_타입 [DEFAULT 기본값] [NOT NULL],...
    [,PRIMARY KEY(기본키_속성명,...)]
    [,UNIQUE(대체키_속성명,...)]
    [,FOREIGN KEY(외래키_속성명,...)]
        [REFERENCES 참조테이블(기본키_속성명,...)]
        [ON DELETE 옵션]
        [ON UPDATE 옵션]
    [,CONSTRAINT 제약조건명] [CHECK(조건식)]);
CREATE TABLE 학생
    (이름 VARCHAR(15) NOT NULL,
    학번 CHAR(8),
    전공 CHAR(5),
    성별 SEX
    생년월일 DATE,
    PRIMARY KEY(학번),
    FOREIGN KEY(전공)
        REFERENCES 학과(학과코드)
        ON DELETE SET NULL
        ON UPDATE CASCADE,
    CONSTRAINT 생년월일제약 CHECK(생년월일>='1980-01-01'));

# 뷰
CREATE VIEW 뷰명[(속성명[,속성명,...])]
AS SELECT;
CREATE VIEW 안산고객(성명, 전화번호)
AS SELECT 성명, 전화번호
FROM 고객
WHERE 주소='안산시';

# 인덱스
CREATE [UNIQUE] INDEX 인덱스명
ON 테이블명(속성명[ASC|DESC],[속성명[ASC,DESC]])
[CLUSTER];
CREATE UNIQUE INDEX 고객번호_idx
ON 고객(고객번호 DESC);

UNIQUE : 중복허용
CLUSTER : CLUSTERED INDEX - 실제 값 정렬됨
```

# ALTER
```
ADD : 새로운 속성 추가
ALTER TABLE 테이블명 ADD 속성명 데이터_타입 [DEFAULT '기본값'];

ALTER : 특정 속성의 DEFAULT값을 변경할 때 사용
ALTER TABLE 테이블명 ALTER 속성명 [SET DEFAULT '기본값'];

DROP COLUMN : 속성 삭제
ALTER TABLE 테이블명 DROP COLUMN 속성명 [CASCADE];
```

# DROP 
- CASCADE : 제거할 요소를 참조하는 다른 모든 개체를 함께 제거
- RESTRICT : 다른 개체가 제거할 요소를 참조중일 때는 제거를 취소

# DELETE
```
DELETE FROM 테이블명 [WHERE 조건];
```

# SELECT
```
SELECT [PREDICATE] [테이블명]속성명 [AS 별칭][,[테이블명,]속성명....]
    [,그룹함수(속성명)[AS 별칭]]
    FROM 테이블명[,테이블명,...]
    [WHERE 조건]
    [GROUP BY 속성명, 속성명,...]
    [HAVING 조건]
    [ORDER BY 속성명 [ASC | DESC]];

PREDICATE : 불러올 튜플 수를 제한할 명령어
- ALL
- DISTINCT : 중복 튜플 제거
- DISTINCTROW : 중복 튜플 제거 & 튜플 전체 대상
WHERE : 검색할 조건을 기술
ORDER BY절 : 특정 속성을 기준으로 정렬하여 검색할 때 사용
GROUP BY절 : 특정 속성을 기준으로 그룹화하여 검색할 때 사용
[집계함수]
- count
- sum
- avg
- max
- min
- stddev : 표준편차
- variance : 분산
HAVING절 : GROUP BY와 함께 사용되며, 그룹에 대한 조건 지정
UNION : 합집합
UNION ALL : 합집합 & 중복 출력
INTERSECTION : 교집합
EXCEPT : 차집합
```

# DISTINCT
중복 튜플 제거 & 튜플 전체 대상

# JOIN
2개 테이블의 튜플들을 결합하여 하나의 새로운 릴레이션 반환

## INNER JOIN

### EQUI JOIN(NATURAL JOIN)
INNER JOIN 방식 중 하나.  
대상 테이블에서 공통 속성을 기준으로 '='에 의해 같은 값을 가지는 행을 연결하여 결과를 생성하는 JOIN방법

### NON EQUI JOIN
'=' 조건이 아닌 나머지 비교 연산자, '>', '<' ...연산자를 사용하는 JOIN 방법

## OUTER JOIN
JOIN 조건에 만족하지 않는 튜플도 결과로 출력하기 위한 JOIN 방법. 

### LEFT OUTER JOIN
![left_outer_join](/docs_images/left_outer_join.png)  
INNER JOIN 결과에서 우측 항 릴레이션의 어떤 튜플과도 맞지 않는 좌측 향의 릴레이션에 있는 튜플들에 NULL값을 붙여서 추가.
```
SELECT [테이블명1.]속성명, [테이블명2.]속성명,....
    FROM 테이블명1 LEFT OUTER JOIN 테이블명2
    ON 테이블명1, 테이블명2;
```

### RIGHT OUTER JOIN
![right_outer_join](/docs_images/right_outer_join.png)  
INNER JOIN 결과에서 좌측 항 릴레이션의 어떤 튜플과도 맞지 않는 좌측 향의 릴레이션에 있는 튜플들에 NULL값을 붙여서 추가.

### SELF JOIN
같은 테이블에서 2개의 속성을 연결하여 EQUI JOIN을 하는 방법