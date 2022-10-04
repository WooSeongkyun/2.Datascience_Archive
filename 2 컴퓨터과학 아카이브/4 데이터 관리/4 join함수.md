# 4.  $join$ 함수

상태: SQL

## 1. $join$이란 무엇인가?

- 두 개 이상의 테이블이나 데이터베이스를 연결하여 마치 하나의 테이블 및 데이터베이스인 것 처럼 검색을 할 수 있게 해주는 명령어이다.
- 이때 테이블로 연결되기 위해선 적어도 하나의 칼럼은 서로 공유되고 있어야 한다

## 2. $join$의 종류

- 교집합 $inner\,\,join$
    - 두 테이블의 공통열과, 그 열원소를 포함하는 데이터를 각각의 테이블에서 가져와 출력하는 함수
    - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$
    - $from\,\,table\_A\,\,inner\,\,join\,\,table\_B\,\,on\,\,table\_A.key_A=table\_B.key_B$
    
    - $inner\,\,join$ 대신 $natural\,\,join$을 사용할 수 있다. $natural\,\,join$은 공통된 열을 자동으로 찾아준다.
    - 같은 이름, 같은 값을 가진 열이 존재한다면 $table\_A.key_A=table\_B.key_B$ 을$using(col\_name)$으로 대체하여 사용할 수 있다. 이경우 $key$ 열이 하나만 출력된다
    
- 외집합 $outer\,\,join$
    - $left-join$
        - 두 테이블의 공통열과, 그 열원소를 포함하는 데이터를 오른쪽 테이블에서, 왼쪽 테이블에선 전체 데이터를 가져와 출력하는 함수
        - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$
        - $from\,\,table\_A\,\,left\,\,join\,\,table\_B\,\,on\,\,table\_A.key_A=table\_B.key_B$
    - $right-join$
        - 두 테이블의 공통열과, 그 열원소를 포함하는 데이터를 왼쪽 테이블에서, 오른쪽 테이블에선 전체 데이터를 가져와 출력하는 함수
        - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$
        - $from\,\,table\_A\,\,right\,\,join\,\,table\_B\,\,on\,\,table\_A.key_A=table\_B.key_B$
    - $full-join$
        - 두 테이블 각각의 전체 데이터를 가져와 출력하는 함수
        - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$
        - $from\,\,table\_A\,\,full\,\,join\,\,table\_B\,\,on\,\,table\_A.key_A=table\_B.key_B$

## 2.$subquery$.

- 쿼리문 안에 또 하나의 쿼리문이 포함되어 있는 구조
- $from$ 에서의 $subquery$
    - $inner\,\,query$에서 조회된 값을 테이블처럼 활용할 수 있다
    - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$$from\,\,(select\sim \,\,from)$
- $where$ 에서의 $subquery$
    - $select\,\,field\_name_1,field\_name_2,...,field\_name_n$$from\,\,table\_name\,\,where\,\,field\_name_1\,\,in\,$
        
         $(select\,\,\sim\,\,from)$