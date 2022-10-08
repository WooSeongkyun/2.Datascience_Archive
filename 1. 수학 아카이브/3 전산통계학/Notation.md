# Notation

### 영단어

- cumbersome: 다루기 힘든

### 1.  갯수와 관련된 변수

- $n$ :관측치 $obervasion$의 갯수
- $p$ : 모델에 사용되는 독립변수의 수

### 2. 행렬 표기법

- $x_{ij}:$ $i$ 번째 관측치$observasion$의 $j$번째 특성(변수)의 값
- 변수가 $p$개 있고, 관측치가 $n$개 있는 데이터를 다음과 같은 행렬의 형태로 표기하자
    - $\bold{X}=\begin{pmatrix} x_{11} & x_{12}&...&x_{1p}\\x_{21}&x_{22}&...&x_{2p}\\...\\x_{n1}&x_{n2}&...&x_{np} \end{pmatrix}$이고
    - $j$번쨰 관측치를 ${x}_{j}=\begin{pmatrix} x_{1j}\\x_{2j}\\...\\x_{nj}\end{pmatrix}$라고 표기하면
    - $\bold{X}=\begin{pmatrix} {x}_{1}^t\\{x}_{2}^t\\...\\{x}_{n}^t\end{pmatrix}$ 이다
- $y_i$ : $i$ 번째 종속변수 관측값(실제로 관측된 값, 예측값 $\bold{X}\beta$과 대비)
-