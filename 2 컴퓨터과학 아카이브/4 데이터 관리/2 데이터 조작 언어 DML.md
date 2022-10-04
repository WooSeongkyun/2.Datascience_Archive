# 2. 데이터 조작 언어 DML

상태: SQL

### 1.데이터 조작언어 $Data\,\,Manipulation\,\,Language$

- 데이터를 테이블에 삽입,조회,수정,삭제를 할 수 있는 언어

### 2.$DML$ 함수

- 데이터 삽입하기
    - $insert\,\,into\,\,table\_name(field\_name_1,field\_name_2,...,field\_name_n)$$values(val_1,val_2,...,val_n);$
- 데이터 조회하기
    - $select\,\,field\_name_1,field\_name_2,...,field\_name_n\,\,from$$table\_name\,\,[options]$
    - $options$
        - 특정 조건 부여하기
            - $where \,\,condition$
            - $aggregate\,\,function$을 조건문에 사용하는경우 $where$ 대신 $having$을 사용해야 한다
        - 출력 데이터 갯수$n$개로 제한하기
            - $limit\,\,n$
        - 테이블의 모든 필드 데이터 보기
            - $select\,\,*$
        - 원소 갯수 세기
            - $select\,\,count(field\_name)$
        - 특정 필드기준으로 정렬하여 출력하기
            - $order\,\,by\,\,field\_name$ $[desc]$
            - $default$는 오름차순, $desc$를 추가하면 내림차순이다
            - $field\_name$ 대신 숫자$n$를 입력할 수 있으며 이때 숫자$n$은 $select$ 명령어의 $n$번째 파라미터 필드로 해석한다
        - 특정 필드의 카테고리별 갯수 세기
            - $select\,\,field\_name,count(field\_name)\,\,from\,\,table\_name$
            $\,\,\,\,\,group\,\,by\,\,field\,\,name$ 
            - $count$외에 그룹별로 평균,최댓값등의 연산$aggregate\,\,function$을 하는 데에 활용할 수 있다
        - 중첩된 $select$문 :$query$문 내부에 사용되는 $select$ 문
        
- 데이터 수정하기
	- $update\,\,table\_name\,\,set\,\,field\_name_1=val_1,field\_name_2=val2,...field\_name_n=val_n\,\,where[cond]$
    - $where\,\, condition$에 변경하고자 하는 대상의 조건을 입력한다
- 데이터 삭제하기: DELETE
    - $delete\,\,from\,\,table\_name\,\,  where[cond]$
    - $where\,\, condition$에 변경하고자 하는 대상의 조건을 입력한다

> 조건-비교(첨가하여 씀): $where$
> 
> - $a= b$  :  $a$와 $b$가 같을 경우
> - $a > b:$ $a$ 가 $b$보다 크다
> - $a ≥ b :$ $a$가 $b$보다 크거나 같다