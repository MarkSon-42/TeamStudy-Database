# [과제1] PostgreSQL 입문수업



## 1. Database
서비스를 위한 데이터 베이스 만들기 name: opentutorials
## 2. Schema
자동으로 제공되는 스키마 사용
## 3. Table
이름: topic

**id: 식별자(중복 X)**
  - 타입 | serial: 1씩 증가
 
**title: 짧은 텍스트**
  - 타입 | character varying : 가변적 길이의 문자
 
**body: 긴 텍스트**

**created: 날짜와시간**
  - 타입 | timestamp with time zone 
  - default 값: now()

---

    CREATE TABLE public.topic
    (
    id serial NOT NULL,
    title character varying(50) NOT NULL,
    body text,
    created timestamp with time zone NOT NULL DEFAULT now(),
    PRIMARY KEY (id)
    );

---

## 4. SQL
뜻: 구조화된 지리 언어

**★SQL로 CRUD 하는 법을 알아보자**
Create - *Insert*
Read - *Select*
Upadte - Update
Delete - Delete

--- 
### (1) INSERT
테이블에 값 채워넣기

    INSERT INTO topic (title, body) VALUES('Select','Select is ...');
    INSERT INTO topic (title, body) VALUES('Update','Update is ...');
    INSERT INTO topic (title, body) VALUES('Delete','Delete is ...');

### (2) SELECT

    SELECT * FROM topic; #모든 컬럼을 가져오고 싶다
    SELECT id, title FROM topic where id <> 1 ORDER BY id DESC LIMIT 2;

- DESC/ ASC
- Where: 원하는 데이터 선택
- Limit: 행의 양을 설정할 수 있음 


### (3) UPDATE

    UPDATE topic SET title='수정', body = '수정 is ..' WHERE id = 2; 

- 반드시 Where문을 사용할 것. 아니면 모든 행의 값이 수정됨

### (4) Delete

    DELETE FROM topic WHERE id=7;

- 반드시 Where문을 사용할 것. 신경써야 함

---


## 5. JOIN
관계형 데이터베이스는  분리된 데이터 테이블을 하나의 테이블로 합쳐서 가져올 수 있는 기능을 포함함. 이것을 **Join**이라고 함.

테이블 구성 분리에 대한 고민 해결: Relational Data Modeling 

- Index: 성능 향상의 핵심. 데이터 가져올 때의 편리함 갖게 됨
- Backup: 데이터를 안전하게 보관
- Cloud: 우리 컴퓨터에 직접 DB 설치, 운영 - 굉장히 어려운 일. 이것을 대신해주는 비즈니스를 Cloud라고 함
- Programming: Application의 일부분으로, 데이터베이스를 안전하게 저장하고 신속하게 조회하는 용도의 부품으로 사용함. 이를 위해서는 프로그래밍 쪽으로 조작하는 방법을 알아야 함.


