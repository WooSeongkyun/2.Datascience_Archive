# 1. 데이터 정의 언어 DDL

상태: SQL

## 1.데이터 정의 언어 $Data\,\,Define\,\,Language$

- 데이터가 모여 테이블, 테이블이 모여 데이터베이스가 되는 구조: 그 구조를 정의하는 언어

### 2.$DDL$ 함수

### $show$ 현재 있는 데이터베이스/테이블 보기

- 데이터베이스보기
    - $show\,\,databases;$
- 테이블보기
    - $show \,\,tables;$
    
- 테이블의 구성요소 보기
    - $describe;$
- 지금사용할 데이터베이스 지정하기
    - $use;$

### $create$ 사용자/ 테이블/데이터베이스 생성하기

- 데이터 베이스 생성 $create\,\,database\,\,database\_name;$
- 테이블 형성  $create\,\,table\,\,table\_name($
    - $field\_name \,\,data\_type \,\,attr$
    - $field\_name \,\,data\_type \,\,attr$
    - $.... );$
- 사용자 생성 $create\,\,user\,\,user\_name\,\,identified\,\,by\,\,pw\_name$

### $alter$ 테이블의 필드 추가,삭제,이름 수정하기

- 테이블에 필드 추가
    - $alter\,\,table\,\,table\_name\,\,add\,\,field\_name\,\,dtype$
- 테이블에 필드 삭제
    - $alter\,\,table\,\,table\_name\,\,drop\,\,column\,\,field\_name$
- 테이블 필드 이름 수정
    - $alter\,\,table\,\,table\_name\,\,change\,\,old\_name\,\,new\_name \,\,dtype\,[opts];$
    - $dtype,opts$를 기존과 동일하게 쓰고 싶다면 다시 지정해야 한다

### $drop$ 데이터베이스와 테이블 삭제하기

- 데이터베이스 삭제하기
    - $drop\,\,database\,\,name$
- 테이블 삭제하기
    - $drop\,\,table\,\,name$