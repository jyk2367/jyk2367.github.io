---
layout: default
title: SQL 응용
parent: 데이터베이스 구축
grand_parent: 정보처리기사

nav_order: 4.4
---

- [프로시저](#프로시저)
- [트리거](#트리거)
- [사용자 정의 함수](#사용자-정의-함수)
- [DBMS 접속](#dbms-접속)
- [웹 응용 시스템](#웹-응용-시스템)
- [JDBC](#jdbc)
- [ODBC](#odbc)
- [MyBatis](#mybatis)
- [동적 SQL](#동적-sql)
- [정적 SQL](#정적-sql)

# 프로시저
절차형 SQL을 활용해 특정 기능을 수행하는 일종의 트랜잭션 언어.  

- **절차형 SQL** : C, JAVA 등의 프로그래밍 언어와 같이 연속적인 실행이나 분기, 반복 등의 제어가 가능한 SQL
```
DECLARE (필수)
BEGIN (필수)
    CONTROL
    SQL
    EXCEPTION
    TRANSACTION
END (필수)

EXCEPTION : 예외처리
TRANSACTION : 수행된 데이터작업을 DB에 적용할지 취소할지 결정하는 처리부

CREATE[OR REPLACE] PROCEDURE 프로시저명(파라미터)
[지역변수 선언]
BEGIN
    프로시져 BODY;
END;
CREATE OR REPLACE PROCEDURE emp_change_s(i_사원번호 IN INT)
IS
BEGIN
    UPDATE 급여 SET 지급방식='S' WHERE 사원번호=i_사원번호;
    EXCEPTION
        WHEN PROGRAM_ERROR THEN
            ROLLBACK;
    COMMIT;
END;
EXECUTE 프로시저명;
DROP PROCEDURE 프로시저명;
```

# 트리거
DB 시스템에서 데이터의 삽입(Insert), 갱신(Update), 삭제(Delete) 등의 이벤트가 발생할 때마다 관련 작업이 자동으로 수행되는 절차형 SQL
```
DECLARE (필수)
EVENT (필수)
BEGIN (필수)
    CONTROL
    SQL
    EXCEPTION
END (필수)
```

# 사용자 정의 함수
프로시저와 유사하게 SQL을 사용하여 일련의 작업을 연속적으로 처리, 종료 시 처리 결과를 단일 값으로 반환하는 절차형 SQL.

```
DECLARE (필수)
BEGIN (필수)
    CONTROL
    SQL
    EXCEPTION
    RETURN(필수)
END (필수)

CREATE FUNCTION
~~
```

|구분|프로시저|사용자 정의 함수|
|--|--|--|
|반환값|없거나 1개 이상 가능|1개|
|파라미터|입출력 가능|입력만 가능|
|사용 가능 명령문|DML,DCL|SELECT|
|호출|프로시저, 사용자 정의 함수|사용자 정의 함수|
|사용 방법|실행문|DML에 포함|

# DBMS 접속
사용자가 데이터를 사용하기 위해 응용 시스템을 이용하여 DBMS에 접근하는 것을 의미

# 웹 응용 시스템
웹 서버와 웹 어플리케이션 서버(WAS)로 구성.

1. 사용자는 웹 서버에 접속해 데이터를 주고받는다
2. 웹 서버는 많은 수의 서비스 요청을 처리하므로 사용자가 대용량의 데이터를 요청하면 직접 처리하지 않고 WAS에게 요청을 전달한다
3. WAS는 수신한 요청을 트랜잭션 언어로 변환한 후 DBMS에 전달하여 데이터를 받는다
4. 받은 데이터는 처음 요청한 웹 서버로 다시 전달되어 사용자에게 도달한다.

# JDBC 
자바 언어로 다양한 종류의 데이터베이스에 접속하고 SQL문을 수행할 때 사용되는 표준 API.    
접속하려는 DBMS에 대한 드라이버(장치나 시스템을 제어하는데 사용하는 프로그램) 필요.

# ODBC
데이터베이스에 접근하기 위한 표준 개방형 API.  
접속하려는 DBMS의 인터페이스를 알지 못해도 ODBC 문장을 사용하여 SQL을 작성하면 ODBC에 포함된 드라이버 관리자가 해당 DBMS의 인터페이스에 맞게 연결해 준다.

# MyBatis
JDBC 코드를 단순화하여 사용할 수 있는 SQL Mapping 기반 오픈소스 접속 프레임워크.
SQL문장을 분리하여 XML파일을 만들고, Mapping을 통해 sql을 실행.

# 동적 SQL
개발 언어에 삽입되는 SQL 코드를 문자열 변수에 넣어 처리하는 것.  
- 문자열 변수에 담아 동적 처리.  
- NVL 함수 없이 로직을 통해 SQL작성.  
- 느림.  
- 사전 검사 불가능.  
```
SET @columnValue = 'incheon';

SET @sql = CONCAT('SELECT * FROM member WHERE address = ''', @columnValue, '''');

PREPARE stmt FROM @sql;
EXECUTE stmt;
DEALLOCATE PREPARE stmt;
```

# 정적 SQL
SQL 코드를 변수에 담지 않고 코드 사이에 직접 기술한 SQL문.  
```
SELECT * FROM member;
```