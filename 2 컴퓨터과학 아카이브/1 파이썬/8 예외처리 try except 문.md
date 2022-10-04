# 예외처리: try / except 문

상태: 연산 / 자료형

## 1. 다양한 오류들

### 1-1. 존재하지 않는것을 입력

- FileNotFoundError:No such file or directory
    - 없는 파일을 열거나 실행시키려 했을 때 발생
- ImportError
    - 없는 모듈을 호출하는 경우 발생
- NameError: name ‘something’ is not defined
    - 없는 변수/함수를 호출하는 경우 발생
- KeyError
    - 딕셔너리에 없는 key값을 입력하는 경우 발생
- AttributeError: ‘list’ object has no attribute ‘value’
    - 리스트에 없는 속성을 호출

### 1-2.문법 오류

- IndentationError
    - expected an indentated block: 들여쓰기를 해야되는데 모자라다
    - unexpected indent: 들여쓰기가 과도하게 되었다
    - unindent does not match any oter indentation level: 공백space와 탭tab을 혼용했을 때 발생하는 에러
- SyntaxError 문법오류
    - EOL while scanning string literal: ‘’ ,”” 따옴표 짝이 맞지 않는다
    - invalid syntax: in 뒤에는 리스트나 묶음자료형이 나와야 한다
    - can’t assign to literal: 변수 명칭이 맨처음 숫자로 지정하는 경우
- TypeError
    - 데이터 타입이 맞지 않은 인자가 들어가는 경우
- ValueError :
    - 함수 안에  의도하지 않은 실행인자가 들어오는 경우
- IndexError: list index out of range
    - 리스트 범위를 넘어선 인덱싱을 하면 발생하는 오류
- ZeroDivisionError
    - 0으로 나누려 할 경우 생기는 에러
- RecursionError: maxumum recursion depth exceeded
    - 재귀 함수 선언 후 종료 조건이 설정되지 않아서 과도하게 호출하게 되어 에러

## 2. 예외처리

- 오류를 무시하고 프로그램을 정상적으로 실행하기 위해 사용하는 명령어

```python
#이때 발생오류명은 생략가능함
# except 발생오류명1,발생오류명2,... 등을 적으면 or 조건으로 해당 오류중
# 하나만 발생해도 오류 발생시 실행될 명령문들이 작동함
#finally 하단엔 오류 발생 유무와 상관없이 무조건 실행시킬 명령문을 작성함
try:
	실행할 명령문 1
	실행할 명령문 2
	...
except 발생오류명:
	오류 발생시 실행할 명령문 1
	오류 발생시 실행할 명령문 2
	....
finally:
	무조건 실행시킬 명령문 1
	무조건 실행시킬 명령문 2
	...
```

### 1-1. $except$  발생오류 $as \,\,x:$

```python
try:
	span()
except NameError as x:
	print(x)
=> name 'spam' is not defined
# x는 except 구문 내에서만 사용가능하다
```