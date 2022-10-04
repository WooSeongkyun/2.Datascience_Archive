# 파일 입출력(with 판다스)

상태: 함수 / 클래스 / 모듈

## 1. 파일 입출력 명령어는 무엇이 있을까?

- 파일 생성
- 파일 수정
- 파일 저장

### 1-1. 파일 읽기/쓰기

- $file\_var =\,\,open('file\_name','mode')$
- 모드 종류
    - $'r'$ : 읽기 모드
    - $**'w'$ : 쓰기 모드**
        - **기존의 파일이 있을 경우 $w$로 열면 기존 파일 내용이 전부 삭제**
        - 기존 파일이 없을 경우 $w$로 열게 되면 새 파일이 만들어진다
    - $'x'$ : 쓰기 모드( 파일이 있으면 오류 발생)
    - $'a'$: 쓰기 모드 (파일이 있으면 뒤에 내용을 추가)
    - $'+'$: 읽기, 쓰기 모드
    - $'t'$ : 텍스트 모드
    - $'b'$ : 바이너리 모드( 시스템만 해석가능. 사용자는 못읽음)
- $pickle.dump(detail,file\_name)$
- 파일 읽을 때 경로: 둘중 하나로 입력하여야 한다
    - 상대경로
        - 작성중인 스크립트의 저장 위치에서 파일 위치까지 내려가는 경로
        - 예:data/대한민국_주요_도시_인구수.csv
    - 절대경로
        - 최상위 위치부터 시작하여 파일의 위치까지 내려가는 경로
        - 예:c:/jupyter/pandas/data/대한민국_주요_도시_인구수.csv
- 파일 닫기
    - $file\_var.close()$
    

### 1-2. 내용 추가/ 읽기

- 내용추가
    - $file\_var.write(detail)$
        - 변수 $detail$의 내용이 파일에 저장된다
- 파일 내용 한줄씩 순서대로 읽기
    - $file\_var.readline()$
        - 그렇기에 $while$문과의 조합이 잘 활용된다
        - 한줄을 읽으면 포인터(커서)가 다음줄로 이동한다
- 파일 내용 한줄 한줄을 요소로 리스트에 저장하기
    - $file\_var.readlines()$
        - $j+1$ 번째 줄 읽기
            - $lines=file\_var.readlines()$
            - $print(lines[j])$

### 1-2-1. 전체내용 읽기

```python

# 1. read() 활용법
# 파일 내용 전체를 문자열로 저장한다
print(file_var.read())

# 2. readlines() 활용법
# 파일 내용 한줄 한줄을 리스트의 각 요소로 저장한다
file_var =open('file_name','r')
lines=f.readlines()
for line in lines:
	print(line)
f.close()

# 3. readline() & while 활용법
file_var(file, 'r')
while True:
	line=f.readline()
	if not line:
		break
	else:
		print(line)
```

### 1.3 $with$문 문장구조

```python
with open('file_name','mode') as file_var:
file_var.write(x)
```

## 2.$csv$파일 정보 데이터프레임에 담기

- $df=pd.read\_csv('./file\_name.csv')$
- $df=pd.read\_excel('./file\_name.xlsx')$
    - 맨 처음 행이 열 이름으로 지정된다
    - 맨 처음 행이 열이름이 되지 않길 원하는 경우 $header=None$ 인자 입력
    - 인덱스를 사용하지 않길 원하는 경우 $index\_col=0\,\,or\,\,None$ 입력
    - 특정 열을 인덱스로 사용하고 싶은 경우 $index\_col=$$col\_name$ 입력


## 3.   .ipynb 파일에서 .py 파일로
`!jupyter nbconvert --to script File_name.ipynb`
