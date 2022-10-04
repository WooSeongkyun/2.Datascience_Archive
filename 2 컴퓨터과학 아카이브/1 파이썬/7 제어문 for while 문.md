# 제어문 : for / while 문

상태: 연산 / 자료형

## 1.$for$문이란 무엇인가?

- $sequence$ 순서형 ($list,tuple,range$,$str$처럼 인덱싱이 가능하고, 순서가 있는 자료형)의 첫 번째 원소부터 마지막 원소까지 차례대로 변수에 대입하여 반복하여 문장을 실행시키게하는  명령문
- 이터러블의 원솟값이 입력되는 변수를 카운터 변수 $counter\,\,variable$이라 부른다
- 집합을 사용하는 경우는 순서가 없기에 무작위로 출력되므로 거의 사용안한다

### 1-1. $for$ 문 문장구조

- $for$문에서

```python
for x in list(or tuple or range):
	수행할 문장 1
	수행할 문장 2
	...
	수행할 문장 n
```

### 1.2 리스트 내포 표현

- $for$ 내포문 기초 표현
    - $b= [f(x) \,\,for\,\, x\,\,in\,a]$
    - $b=[f(x_1),f(x_2),...,f(x_n)]$이 생성됨
- $for-if$ 내포문
    - $b= [f(x) \,\,for\,\,x\,\,in\,\,a\,\,if$ 조건 $]$
    - 조건에 부합하는 $x$가 $f(x)$의 $input$ 인 리스트가 만들어짐
- $for-if-else$ 내포문
    - $b= [f(x)\,\,if$ 조건 $\,\,else$ $g(x)$ $for \,\,x\,\,in\,\,a]$
    - 조건에 부합하는 $x$는 $f(x)$의 $input$으로 그 밖의 경우는 $g(x)$의 $input$으로 하는 리스트가 만들어짐
    

### 1-3. for문의 응용

- 변수에  $tuple$ 오기
    - $for$ $(x_1,x_2,...,x_n)$ $in$ $[(y_{11},y_{12},...,y_{1n}),(y_{21},y_{22},...,y_{2n}),...,(y_{m1},y_{m2},....,y_{mn})]$
- $for \,\,-continue$ 문
    - $for$ 문 아래 실행문 중에 $continue$를 만나면 $for$문 처음으로 돌아간다
- $for \,\,-\,\,range$ 문
    - $for$  변수 $in\,\,range(x)$ : 숫자 0부터 $x$ 미만 연속된 숫자
    - $for$  변수 $in\,\,range(x,y)$ : 숫자 $x$부터 $y$ 미만 연속된 숫자
    - $range(x,y)$로 생성된 객체를 $list$ 함수를 사용하면 리스트로 변환가능
- $for-else$ 문
    - $for$ 문이 정상적으로 작동하면($break$나 $continue$가 작동되지 않고 실행이 종료됨) $else$구문이 작동한다.
    
    ```python
    for 조건문:
    	실행문 1
    else:
    	실행문 2
    
    실행문 1이 정상 작동하면 실행문 2가 정상작동함
    실행문 1이 break나 continue에 의해 도중 중단하여 완료시 실행문 2는 실행되지 않음
    ```
    

### 1-4. 이중 for문 문장구조

```python
a= [x_1,x_2,...,x_n]
b= [y_1,y_2,...,y_m]

for x in a:
	실행문 1 f(x)
	for y in b:
		실행문 2 g(x,y)
```

- 실행순서
    - $f(x_1)$ 이 출력된다
        - $g(x_1,y_1)$이 출력된다
        - $g(x_1,y_2)$이 출력된다
        - ....
        - $g(x_1,y_m)$이 출력된다
    - $f(x_2)$가 출력된다
        - $g(x_2,y_1)$이 출력된다
        - $g(x_2,y_2)$가 출력된다
        - ...
        - $g(x_2,y_m)$이 출력된다
    - ...
    - $f(x_n)$이 출력된다
        - $g(x_n,y_1)$이 출력된다
        - $g(x_n,y_2)$가 출력된다
        - ....
        - $g(x_n,y_m)$이 출력된다

### 1-5. 파이썬 동적 변수 생성: $for$문으로 자동 변수 생성하기

```python
n=int(input('생성하고 싶은 변수 갯수를 입력하세요'))
for i in range(1,n+1):
    globals()[f'var{i}']= 0

#eval은 input으로 string을 받으며, 
#string을 변수나 식으로 해석하여 실행해주는 함수이다
for i in range(1,n+1):
    print(eval(f'var{i}'))

```

## 2.$While$문

- 조건문과 함께 쓰이며, 조건문이 참일 경우 실행문은 계속 수행된다
- $for$ 문과 $While$ 문의 차이
    - $for$ 문은 리스트나 튜플,  래인지,문자열 등과 함께 사용된다
        - 데이터 크롤링과 같이 자료를 리스트화하고, 리스트안에 값이 있는 지를 비교하는데에 사용한다
        - 무한 루프 불가능(언젠간 구성 요소가 떨어지기 마련이다)
    - $While$문은 조건만 걸어주면 알아서 반복하다
        - 무한 루프 가능

### 2-1. $While$문 문장구조

```python
while 조건문:
	수행할 문장 1
	수행할 문장 2
	...
	수행할 문장 n
```

### 2-2 $While$문 응용

```python
# 1. while- break 문
while 조건문:
	수행할 문장 1
	수행할 문장 2
	...
	break

# 2. while- continue 문
while 조건문:
 수행할 문장 1
 수행할 문장 2
 ...
 continue

# 3. 무한반복 While문 예시
while True:
	실행할 문장1
	조건문:
			실행할 문장2
			break
--------------------------------
조건문이 충족되어 break로 빠져나오지 않는 한
계속 반복되는 무한 츠쿠요미
```

- $while-break$ 문
    - 강제로 빠져나오고 싶을 경우 $break$를 사용한다
    - 주로 조건문 $if$와 같이 활용된다
- $while-continue$ 문
    - 실행문을 실행시키고 싶지 않으나 $while$문을 빠져나가고 싶지 않은 경우 사용한다
    
- 예시

```python
'''
여러 선택지중에서 해당 선택지가 나오기 전까지 구동하는 무한 루프 프로그램
1. Add
2. Del
3. List
4. Quit

'''
prompt= ''' 
1. Add
2. Del
3. List
4. Quit

Enter number:
'''

number=0
while number !=4 :
    print(prompt)
    number= int(input())
```