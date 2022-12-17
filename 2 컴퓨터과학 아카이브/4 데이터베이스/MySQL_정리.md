## MySQL 데이터베이스강좌

## 데이터의 조작 레벨
- 유저 레벨
	- 이를 위한 언어를 데이터 제어 언어 **Data Control Language** 라 한다
	- 사용자의 데이터베이스에 대한 접근권한을 제어한다
	
- 데이터베이스 레벨
	- 이를 위한 언어를 데이터 정의 언어 **Data Define Language**라 한다 
	- 데이터베이스의 생성 및 삭제, 테이블의 생성 및 수정 삭제, 필드의 생성 및 수정 삭제, 유저의 생성 및 수정 삭제등의 제어를 한다 
	
	- 관련 함수
		- `create` :  사용자나 데이터베이스,테이블을 생성한다
			- `create database database_name`
		- `drop` : 데이터베이스나 테이블을 삭제한다
			- `drop database database_name`
		- `alter` : 테이블의 필드를 추가,삭제 또는 이름을 변경한다
		- `show` : 데이터베이스와 테이블을 본다 
			- `describe` : 테이블의 구성요소를 본다
		- `use` : 사용할 데이터베이스를 지정한다
	
- 데이터 레벨
	- 이를 위한 언어를 데이터 조작 언어 **Data  Manipulation Langauge** 라 한다
	- 테이블에 데이터를 삽입,삭제,수정 및 조회등의 제어를 한다
	
	- 관련함수
		- `insert`
			- `insert into table_name values`
		- `delete`
			- `delete from table name where cond`
		- `update`
		- `select`
			- `select field_name from table_name`
			- 여러 바리에이션
				- `select count(field_name)` : 원소 갯수세기
				- `order by field name` : 특정 필드기준으로 정렬하기
				- `where field_name = var` : 특정 필드에서 특정 값을 만족시키는 원소를 찾아서 출력하라고 조건을 걸기




