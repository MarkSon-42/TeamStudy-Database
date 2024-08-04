# 생활코딩 PostgreSQL 입문수업

https://www.youtube.com/watch?v=dKuLA5BGPTY

# PostgreSQL 입문수업 요약

> Chrome extension : Transcript & Summery on Youtube 
> video summery text file ---> claude (prompt : change to this file as markdown language for blog post.)

## 1. 데이터베이스 소개

데이터베이스는 복잡한 정보를 표 형태로 관리하여 쉽게 다룰 수 있게 해줍니다. 소프트웨어 엔지니어들은 엑셀이나 구글 스프레드시트 대신 데이터베이스를 사용하여 데이터를 관리합니다.

### 데이터베이스의 중요성
- 많은 앱들이 데이터베이스를 핵심 부품으로 사용
- 사용자 요청 시 데이터베이스에서 데이터를 가져와 가공하여 표시
- 정보기술의 기반이 되는 중요한 요소

### 관계형 데이터베이스
- 가장 인기 있는 데이터베이스 패러다임
- 주요 제품: MySQL, Oracle, MS SQL Server, PostgreSQL
- PostgreSQL은 4번째로 인기 있는 관계형 데이터베이스 (2022년 기준)

## 2. PostgreSQL 소개 및 설치

PostgreSQL의 마스코트는 코끼리로, 강력한 기능과 뛰어난 성능을 상징합니다.

### 설치 과정
1. postgresql.org 방문
2. 다운로드 페이지에서 운영체제에 맞는 버전 선택
3. EDB에서 제공하는 설치 파일 사용 권장
4. 설치 중 비밀번호 설정 - 반드시 기억할 것

### 주요 구성 요소
- 서버: 데이터 보관 및 관리
- 클라이언트: pgAdmin (GUI), psql (CLI)

## 3. PostgreSQL 구조

### 서버-클라이언트 구조
- 서버: 데이터 관리
- 클라이언트: 서버에 접근하여 데이터 조작

### 데이터베이스 구조
1. 테이블 (Table): 데이터 저장 단위
2. 스키마 (Schema): 연관된 테이블 그룹
3. 데이터베이스 (Database): 스키마 그룹
4. 클러스터 (Cluster) / 데이터베이스 서버: 여러 데이터베이스 그룹

### SQL (Structured Query Language)
- 클라이언트가 서버와 통신하는 언어
- 데이터베이스 조작에 사용

## 4. pgAdmin 사용하기

pgAdmin은 PostgreSQL을 관리하는 GUI 도구입니다.

### 서버 연결
1. 서버 등록: 우클릭 > Register > Server
2. 연결 정보 입력:
   - 이름: 원하는 서버 이름
   - 호스트: localhost (로컬 서버)
   - 포트: 5432 (기본값)
   - 사용자 이름: postgres (기본 관리자 계정)
   - 비밀번호: 설치 시 지정한 비밀번호

### 데이터베이스 생성
1. Databases 우클릭 > Create > Database
2. 이름 지정 (예: opentutorials)

### 테이블 생성
1. Tables 우클릭 > Create > Table
2. 테이블 이름 지정 (예: topic)
3. 컬럼 추가:
   - id: SERIAL, PRIMARY KEY
   - title: VARCHAR(50), NOT NULL
   - body: TEXT
   - created: TIMESTAMP WITH TIME ZONE, DEFAULT NOW()

## 5. SQL 기본 - CRUD 작업

CRUD는 Create, Read, Update, Delete의 약자로, 데이터 조작의 기본 작업을 의미합니다.

### INSERT (생성)
```sql
INSERT INTO topic (title, body) 
VALUES ('INSERT SQL의 제목', 'INSERT가 어떤 것이다');
```

### SELECT (읽기)
```sql
SELECT * FROM topic;
```

### UPDATE (수정)
```sql
UPDATE topic 
SET title = '수정된 제목', body = '수정된 내용' 
WHERE id = 1;
```

### DELETE (삭제)
```sql
DELETE FROM topic WHERE id = 1;
```

## 6. 팁과 추천 사항

- SQL 문법은 외우려 하지 말고, 필요할 때 검색하여 사용하세요.
- "PostgreSQL cheat sheet"로 검색하면 유용한 SQL 명령어 목록을 찾을 수 있습니다.
- SQL 키워드는 관례적으로 대문자로 작성합니다 (예: SELECT, INSERT, UPDATE).
- 문자열 데이터는 항상 따옴표로 감싸야 합니다.
- 명령문 끝에는 세미콜론(;)을 잊지 마세요.

이 요약을 통해 PostgreSQL의 기본 개념과 사용법을 익힐 수 있습니다. 실제 데이터베이스 작업을 통해 더 깊이 있는 학습을 진행하시기 바랍니다.








### mac (apple silicon)환경에서 pgAdmin 실행창
<img width="1000" alt="Capture 30" src="https://github.com/user-attachments/assets/d45eac18-c62c-41f6-ad9e-529b13c96590">

### pgAdmin Dashboard
<img width="1000" alt="Capture 31" src="https://github.com/user-attachments/assets/7cd45a3f-ad79-41a6-bf7b-ed96f7d15333">

### pgAdmin SQL
<img width="1000" alt="Capture 32" src="https://github.com/user-attachments/assets/9c9bf9ce-6022-436a-96ac-9421b599b0b4">

### Query
<img width="1000" alt="Capture 33" src="https://github.com/user-attachments/assets/b007cc6e-edfe-4d83-b90d-130d9af664a3">

### SQL practice : Descending
<img width="1372" alt="Capture 34" src="https://github.com/user-attachments/assets/c226a362-20eb-43f6-a7e1-f4efc2d1e004">
