# 3. 데이터 제어 언어 DCL

상태: SQL

### 1.데이터 제어 언어 $Data\,\,Control\,\,Langauge$

- 사용자에게 데이터베이스에 대한 접근을 제어한다
- 기존 $root$ 사용자는 최고 권한을 갖는 사용자이다
    - $root$ 사용자가 탈취되면 보안적 문제가 발생되므로 일반 사용자에게 $root$ 사용자 권한에 미치지 못하지 않는 부분적 권한을 부여하여 데이터 베이스를 관리하게 한다
    - $host$: 데이터베이스가 설치된 $ip$ 주소
    - $localhost$: 사용중인 컴퓨터의 $ip$주소

### 2.$DCL$ 함수

- 권한 부여하기
    - $grant\,\,permission\,\,on\,\,database\_name.table\_name\,\,to\,\,user\_name@localhost;$$database-name.*$ : 모든 테이블에 대한 권한 부여
- 권환 회수하기
    - $revoke\,\,permission\,\,on\,\,database\_name.table\_name\,\,from\,\,user-id@localhost;$
- 권한 정보 갱신하기
    - $flush\,\,previleged;$
- 권한 확인
    - $show\,\,grants\,\,for\,\,user\_name@host$
- 데이터, 트랜잭션 저장하기
    - $commit;$
- 데이터, 트랜잭션 취소하고 되돌리기
    - $rollback;$
    - 커밋하기 직전 시점으로 돌아간다