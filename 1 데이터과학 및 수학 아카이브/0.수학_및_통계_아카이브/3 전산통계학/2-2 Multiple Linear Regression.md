# 2-2. Multiple Linear Regression

- 영단어
    - stem from:~에서 비롯되다
    - implies: 내포하다, 수반하다
    - surrogate: 대리
    - $evident \,\,against$ : ~에 반하는 증거\
    - $by-chance$ : 우연히
    - observant reader: 관찰력 있는 독자
    - discrepancy,: 불일치, 괴리
    

## 1.다중선형회귀

### 1-1. 행렬 표기법

- 표기
    - $X_{ij}:$ $i$번째 관측치의 $j$번째 독립변수 값
    - $Y_i$: $i$번째 관측치의 종속변수
    - $\beta_0,\beta_1,\beta_2,...,\beta_p$ : 계수
    - $\epsilon$  :오차
- $\textbf{Y}=\textbf{X}\beta$+ $\epsilon$
    - $\begin{bmatrix} Y_1\\Y_2\\...\\Y_n \end{bmatrix}=\begin{bmatrix} 1&X_{11}&X_{12}&...&X_{1p}\\1&X_{21} &X_{22}&...&X_{2p}\\...\\1&X_{n1} & X_{n2} &...&X_{np} \end{bmatrix}\begin{bmatrix} \beta_0\\\beta_1\\...\\\beta_p \end{bmatrix}+\begin{bmatrix} \epsilon_1\\\epsilon_2\\...\\\epsilon_n \end{bmatrix}$

### 1-2.회귀 계수의 이론적 추정

- 순서
    - $y_i-\hat{y_i}$가 작을수록 $\hat{\beta_0},\hat{\beta_1},\hat{\beta_2},...,\hat{\beta_p}$가 잘 추정되었다고 볼 수 있다
    - 그렇기 때문에 각 $i$에 대하여 $e_i=y_i-\hat{y_i}$ 값을 측정하자. 그리고 제곱을 하면 $e_i^2=|y_i-\hat{y_i}|^2$, 종속변수의 관측치와 예측치 사이 거리의 제곱이 된다.  모든 관측치에 대하여  행렬 로 연산할 시 다음과 같다
    - $RSS=|\textbf{Y}-\textbf{X}\beta|^2=\langle \textbf{Y}-\textbf{X}\beta,\textbf{Y}-\textbf{X}\beta\rangle=$$(\textbf{Y}-\textbf{X}\beta)^T(\textbf{Y}-\textbf{X}\beta)=(\textbf{Y}^T-\beta^T\textbf{X}^T)(\textbf{Y}-\textbf{X}\beta)=\textbf{Y}^T\textbf{Y}-\textbf{Y}^T\textbf{X}\beta-\beta^T\textbf{X}^T\textbf{Y}+\beta^T\textbf{X}^T\textbf{X}\beta$
    - $=\textbf{Y}^T\textbf{Y}-2\beta^T\textbf{X}^T\textbf{Y}+\beta^T\textbf{X}^T\textbf{X}\beta$
    - 미분을 이용하여 $RSS$를 최소화하는 계수값을 찾자
    - $\cfrac{\partial{(RSS)}}{\partial\beta}=-2(\textbf{X}^T\textbf{Y})^T+2\beta^T(\textbf{X}^T\textbf{X})=-2\textbf{Y}^T\textbf{X}+2\beta^T\textbf{X}^T\textbf{X}=0$
    - $\beta^T\textbf{X}^T\textbf{X}=\textbf{Y}^T\textbf{X}$
    - $\beta^T=(\textbf{X}^T\textbf{X})^{-1}(\textbf{Y}^T\textbf{X})$
    - $\hat{\beta}=(\textbf{X}^T\textbf{X})^{-1}(\textbf{X}^T\textbf{Y})$ : 추정된 $\beta$값
    

### 1-3. 귀무가설 세우기

- 귀무가설 $H_0:\beta_0,\beta_1,\beta_2,...,\beta_p=0$ 이다
- 대립가설 $H_a$ : 최소 하나의 $\beta_j$는 0이 아니다
- 이 가설은 $F-Statistic$에 의해 계산된다
    - $F=\cfrac{(TSS-RSS)/p}{RSS(n-p-1)}$
    - $TSS=\sum_{i}(y_i-\bar{y})^2$
    - $RSS=\sum_{i}(y_i-\hat{y})^2$
- 다음은 증명없이 받아들이자
    - 선형모델가정이 참이라면$E\{RSS/(n-p-1)\}=\sigma^2$
    - 귀무가설이 참이라면 $E\{(TSS-RSS)/p)=\sigma^2$
    - 1에 가까울수록 귀무가설을 기각하지 못한다로 보면 된다
    - 통계 소프트웨어는 $F-statistic$과 관련된 $p-value$를 계산해준다
    - 계수의 부분집합에 대해 $F-statistic$을 측정할 수도 있다
        - 뒤에서 $q$개의 계수에 대해 귀무가설을 세우고 싶다면
        - $H_0=\beta_{p-q+1}=\beta_{p-q+2}=...=\beta_p$
        - $F=\cfrac{(RSS_0-RSS)/q}{RSS/(n-p-1)}$
- 역할
    - 독립변수의 수 $p$가 많아진다면 실제론 종속변수와 관련없지만 유의미한 $p-value$가 나오는 변수들이 나타난다.
    - 이에 반해 $F-statistic$ 는 독립변수의 수에 대해 보정하므로 이러한 취약점이 없다. 따라서 $F-statistic$은 독립변수 집합 전체가 종속변수와의 관련성이 없음을 보일수 있다
- 귀무가설이 기각된다고 판단되면 변수선택 과정으로 넘어간다

### 1-4. 변수 선택 $variation\,\,selection$

- 주어진 독립변수의 부분집합이 종속변수를 예측하는데에 유의미하다고 볼 수 있다. 그렇기 때문에 합리적인 모델을 세우기 위해선 유의미한 변수 부분집합을 찾는 과정이 필요하다
- $p$개의 독립변수 집합은 $2^p$ 개의 부분집합을 갖는다
- 방법론
    - $Forward\,\,Selection$
        1.  $null-model$을 세운다
        2. $p$개의 1차회귀곡선의 $RSS$를 측정하고, 가장 낮은 $RSS$을 갖는 변수의 회귀곡선을 $null-model$에 추가한다
        3. $p$개의 2차회귀곡선의 $RSS$를 측정하고, 가장 낮은 $RSS$를 갖는 변수의 회귀곡선을 앞의 방정식에 추가한다
        4. ….
        5. $p$개의 $k$차회귀곡선의 $RSS$를 측정하고, 가장 낮은 $RSS$를 갖는 변수의 회귀곡선을 앞의 방정식에 추가한다
        - 특정한 조건이 만족될 때까지  반복한다
    - $Backward\,\,Selection$
        1.  모든 변수를 가진 모델을 세운다
        2. 가장 큰 $p$값을 갖는 변수를 지운다
        3. 그다음 큰 $p$값을 갖는 변수를 지운다.
        4. ….
        - 특정한 조건을 만족할 때 까지 반복한다( 예를 들면 모든 변수가 특정 $p-value$ 역치 아래일때 멈추는 모델이 있다 )
    - $Mixed\,\,Selection$
        1. $null-model$을 세운다
        2. $Forward\,\,Selection$의 방법으로 변수를 추가시켜준다
        3. 추가한 변수가 $p-value$의 역치를 넘어서면 해당 변수를 지운다
        4. 모델안에 있는 변수들은 충분히 작은 $p-value$ 를 갖을때까지 시행한다

### 1-5. 모델 학습시키기

- 시그마 추정과 계산
    - $\sigma$는 일반적으로 알기 어렵고 대신 추정하는 값을 $RSE\,\,Residual\,\,Standard\,\,Error$라고 부른다
    - $RSE=\sqrt{\cfrac{RSS}{n-p-1}}$