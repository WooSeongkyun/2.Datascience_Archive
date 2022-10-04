# 2-1. Simple Linear Regression

### 단어정리

- dull: 지루한
- jumping-off: 출발점
- overstate:과장되다
- live up to :~에 걸맞다
- straightforward: 직접적인
- catch-all: 잡동사니 통

## 1. $Linear\,\,Regression$은 무엇인가?

- 특징
    - 정량적인 종속변수를 예측하는데 쓰이는 도구이다.
    - 현대 통계학습중 일반화된 선형회귀법이 많은 부분을 차지한다
- 정의
    - 독립변수 $X_1,X_2,...,X_n$과 종속변수 $Y$, 계수 $\beta_0,\beta_1,...,\beta_n$, 오차항 $\epsilon_1,\epsilon_2,...,\epsilon_n$이 있다하자
    - 다음과 같은 가정이 성립한다 하자
        - 비확률변수$nonstochastic$ :독립변수 $X_1,X_2,...,X_n$는 비확률변수이다(상수취급한다)
        - 선형성$linearity$: 계수와 종속변수 사이 선형성을 갖는다
        - 독립성:$independence$ 독립변수가 다른 독립변수에 영향을 주지 않는다
        - 등분산성$homoskedasticity$: $Var(\epsilon_i)=\sigma^2$$\,\,for\,\,i=1,2,...$
        - 정규성$normality$: $\epsilon\sim \mathscr{N}(0,\sigma^2)$
        - $i\ne j$일때 $Cov(\epsilon_i,\epsilon_j)=0$ 이다
- 정의
    - 모델형태가  $Y=\sum_{i=1}^{n}\beta_{i}X_i+\beta_0+\epsilon$ 이라고 가정하자. 그 계수값 $\beta_0,\beta_1,\beta_2,...,\beta_n$ 을 구한뒤, 해당 모델로 종속변수를 예측하는 일련의 방법론을 선형회귀라고 부른다

## 1-1. 단순선형회귀 $Simple\,\,Linear\,\,Regression$

### 1-1.회귀계수의 이론적 추정

- 조건
    - 독립변수 $X$와 종속변수 $Y$, 계수(파라미터) $\beta_0,\beta_1$이 있다하자
    - 훈련 데이터셋 $\{(x_1,y_1),(x_2,y_2),...,(x_n,y_n)\}$이 있다하자
    - 예측값 $\hat{y_i}=\hat{\beta_0}+\hat{\beta_1}x_i$라고 하자
- 순서
    - $y_i-\hat{y_i}$가 작을수록 $\hat{\beta_0},\hat{\beta_1}$이 잘 추정되었다고 볼 수 있다
    - 그렇기 때문에 각 $i$에 대하여 $e_i=y_i-\hat{y_i}$ 값을 측정하자. 그리고 제곱을 하면 $e_i^2=|y_i-\hat{y_i}|^2$, 종속변수의 관측치와 예측치 사이 거리의 제곱이 된다.
    - 이 값을 $i$에 대하여 모으자. 모은값이 작으면 작을수록 계수 추정이 잘 되었다고 해석할 수 있다
    - $RSS=\sum_{i=1}^n|y_i-\hat{y_i}|^2=\sum_{i=1}^n(y_i-(\hat{\beta_0}+\hat{\beta_1}x_i))^2$
        - $residual\,\,sum\,\,of\,\,square$라 부른다
    - 미분을 이용하여 $RSS$를 최소화하는 계수값을 찾기
        - $\cfrac{\partial{(RSS)}}{\partial{\hat{\beta_0}}}=-2\sum_{i}(y_i-\hat{\beta_0}-\hat{\beta_1}x_i)=0$
        - $\cfrac{\partial{(RSS)}}{\partial{\hat{\beta_1}}}=-2\sum_{i}(y_i-\beta_0-\beta_1x_i)x_i=0$
        - $n\hat{\beta_0}+\hat{\beta_1}\sum_{i}x_i=\sum_{i}y_i$
        - $\hat{\beta_0}\sum_{i}x_i+\hat{\beta_1}\sum_{i}x_i^2=\sum_{i}x_iy_i$
        - $\begin{bmatrix} \hat{\beta_0} \\ \hat{\beta_1} \end{bmatrix}=\cfrac{1}{n\sum_{i}x_i^2-(\sum_{i}x_i)^2} \begin{bmatrix} \sum_{i}x_i^2 & -\sum_{i}x_i \\ -\sum_{i}x_i &n \end{bmatrix}\begin{bmatrix} \sum_{i}y_i \\ \sum_{i} x_iy_i\end{bmatrix}$
        - $n\bar{x}=\sum_{i}x_i, n\bar{y}=\sum_{i}y_i$로 두자
        - $\begin{bmatrix} \hat{\beta_0} \\ \hat{\beta_1} \end{bmatrix}=\cfrac{1}{n(\sum_{i}x_i^2-n\bar{x}^2)} \begin{bmatrix} \sum_{i}x_i^2 & -n\bar{x}\\ -n\bar{x} &n \end{bmatrix}\begin{bmatrix} n\bar{y}\\ \sum_{i} x_iy_i\end{bmatrix}=\cfrac{1}{n(\sum_{i}(x_i-\bar{x_i})^2)} \begin{bmatrix} n\bar{y}\sum_{i}x_i^2 -n\bar{x}\sum_{i}x_iy_i\\ -n^2\bar{x}\bar{y} + n\sum_{i}x_iy_i \end{bmatrix}$
        - $\begin{bmatrix} \hat{\beta_0} \\ \hat{\beta_1} \end{bmatrix}=\cfrac{1}{\sum_{i}(x_i-\bar{x})^2}\begin{bmatrix} \bar{y}\sum_{i}x_i^2 -\bar{x}\sum_{i}x_iy_i\\   \sum_{i}x_iy_i-n\bar{x}\bar{y} \end{bmatrix}$
        - $\begin{bmatrix} \hat{\beta_0} \\ \hat{\beta_1} \end{bmatrix}=\cfrac{1}{\sum_{i}(x_i-\bar{x})^2}\begin{bmatrix} \bar{y}\sum_{i}x_i^2 -\bar{x}\sum_{i}x_iy_i\\   \sum_{i}(x_i-\bar{x})(y_i-\bar{y}) \end{bmatrix}$
        - $\sum_{i}(x_i-\bar{x})^2\hat{\beta_1}+n\bar{x}\bar{y}=\sum_{i}x_iy_i$
        - $\bar{y}\sum_{i}x_i^2-\bar{x}(\sum_{i}(x_i-\bar{x})^2\hat{\beta_1}+n\bar{x}\bar{y})$
        - $=\bar{y}(\sum_{i}x_i^2-n\bar{x}^2)-\hat{\beta_1}\bar{x}\sum_{i}(x_i-\bar{x})^2$
        - $\therefore \hat{\beta_0}=\bar{y}-\hat{\beta_1}\bar{x}$
- 계수 계산하기(최종 요약)
    - $\begin{bmatrix} \hat{\beta_0} \\ \hat{\beta_1} \end{bmatrix}= \begin{bmatrix} \bar{y}-\hat{\beta_1}\bar{x}\\ \cfrac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}{\sum_{i=1}^{n}(x_i-\bar{x})^2}:\cfrac{S(x,y)}{S(x,x)} \end{bmatrix}$

### 1-2. 계수의 결정계수 측정하기

- 관련 개념
    - 편향성 $bias$
        - 어떤 모수 파라미터 $\theta$와 그것의 추정 $\hat{\theta}$ 가 있을 때  다음을 $\theta$의 편향성이라 부른다.
        - $bias(\theta)=E(\hat{\theta})-\theta$
        - 만약 $bias(\theta)=0$이면 파라미터 $\theta$는 비편향$unbiased$이라고 부른다
    - 표준오차$standard\,\,error$
        - 표본통계량의 표준편차
        - 표본통계량(관측치)이 모수(예측치)에서 얼마나 벗어날지, 그 가능성은 어느정도일 지 계산할 때 쓰인다.
        - $SE(\hat{\mu})^2=Var(\hat{\mu})=Var(\cfrac{1}{n}\sum_{i=1}^{n}x_i)=\cfrac{1}{n^2}\sum_{i=1}^{n}Var(x_i)=\cfrac{n\sigma^2}{n^2}=\cfrac{\sigma^2}{n}$
    - 잔차 표준 오차 $Residual\,\,Standard\,\,Error$
        - 관측치가 추정한 회귀선으로부터 얼마나 벗어날지에 대한 평균값
        - $RSE=\sqrt{RSS/(n-2)}$
- 결정계수 $Coefficient\,\,of\,\,Determination$
    - 종속변수의 분산 중 독립변수로 설명되는 비율이다. 이 값이 1에 가까우면 완벽한 $linear-form$ 관계이고, 0에 가까우면 어떤 $linear-form$적 관계도 아니다
    - 예측$prediction$의 경우 $R^2$의 값은 중요하나, 변수간의 관계를 설명하는 해석이 목적이라면 $R^2$이 중요한 기준이 되지 않는다
    - $R^2=\cfrac{TSS-RSS}{TSS}=1-\cfrac{RSS}{TSS}$
    - $where \,\,TSS=\sum_{i}(y_i-\bar{y})^2:\,\,total\,\,sum\,\,of\,\,square$
    - $TSS$는 회귀전에 측정 가능한데 반해 $RSS$는 회귀 후에 측정 가능한 특성을 가진다
    - $R^2$이 1에 가까울수록 회귀모델이 종속변수의 변동을 잘 설명하고, 0일수록 그렇지 않은 경향이 있다( 0에 가까울수록 모델이 잘못되었을 확률이 높다)
- 계수의 기댓값과 분산 측정하기
    - $\hat{\beta_1}=$ $\cfrac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}{\sum_{i=1}^{n}(x_i-\bar{x})^2}=\cfrac{\sum_{i=1}^{n}x_iy_i -x_i\bar{y}-\bar{x}y_i+\bar{x}\bar{y}}{\sum_{i=1}^{n}(x_i-\bar{x})^2}=\cfrac{\sum_{i=1}^{n}(x_i-\bar{x})\bar{y}}{\sum_{i=1}^{n}(x_i-\bar{x})^2}$
    - $E(\hat{\beta_1})=E(\cfrac{\sum_{i=1}^{n}(x_i-\bar{x})\bar{y}}{\sum_{i=1}^{n}(x_i-\bar{x})^2})=\cfrac{\sum_{i=1}^{n}(x_i-\bar{x})}{\sum_{i=1}^{n}(x_i-\bar{x})^2}(\beta_0+\beta_1x_i)=\cfrac{\sum_{i=1}^{n}(x_i-\bar{x})}{\sum_{i=1}^{n}(x_i-\bar{x})^2}\beta_1x_i=\cfrac{\sum_{i=1}^{n}(x_i-\bar{x}^2)}{\sum_{i=1}^{n}(x_i^2-\bar{x}^2)}\beta_1=\beta_1$
    - $Var(\hat{\beta_1})=Var(\sum_{i=1}^n\cfrac{x_i-\bar{x}}{\sum_{i=1}^{n}(x_i-\bar{x})^2}y_i)=\sum_{i=1}^{n}Var(y_i)Var(\cfrac{x_i-\bar{x}}{\sum_{i=1}^{n}(x_i-\bar{x})^2})=\sum_{i=1}^{n}\sigma^2(\cfrac{x_i-\bar{x}}{\sum_{i=1}^{n}(x_i-\bar{x})^2})^2=\sigma^2\sum_{i=1}^{n}\cfrac{(x_i-\bar{x})^2}{(\sum_{i=1}^{n}(x_i-\bar{x})^2)^2}=\cfrac{\sigma^2}{\sum_{i=1}^{n}(x_i-\bar{x})^2}$
    - $E(\hat{\beta_0})=E(\bar{y}-\hat{\beta_1}\bar{x})=E(\beta_0+\beta_1\bar{x})-E(\hat{\beta_1})\bar{x}=E(\beta_0)=\beta_0$
- 증명하지 않고 받아들이기( 증명이 너무 복잡함)
    - $Var(\hat{\beta_1})=\sigma^2[\cfrac{1}{n}+\cfrac{\bar{x}^2}{\sum_{i=1}^n(x_i-\bar{x})^2}]$
- 시그마 추정과 계산
    - $\sigma$는 일반적으로 알기 어렵고 대신 추정하는 값을 $RSE\,\,Residual\,\,Standard\,\,Error$라고 부른다
    - $RSE=\sqrt{RSS/(n-2)}$
    - $\hat{SE}(\hat{\beta_1})$은 $\sigma$대신 추정한 $RSE$를 사용한 값으로 원칙상 $\hat{SE}$로 쓰는 것이 맞으나 표기상의 편리를 위해 햇표기를 생략한다
- $\hat{\beta_1}$의 신뢰구간
    - $\hat{\beta_1}$ 는 정규분포를 따른다( 증명하지 않고 받아들인다)
    - 신뢰구간: 모수가 포함될 것이라고 예측되는 범위, 그 범위내에 포함될 확률인 신뢰수준과 쌍으로 서술되어야 한다
    - 약 95%의 신뢰구간은 $\hat{\beta_1}\pm 2\cdot SE(\hat{\beta_1})$

### 1-3. 회귀계수 $t-test$ 하기

- $H_0$  귀무 가설:  $X$와 $Y$사이엔 아무 관계도 없다 $\leftrightarrow \beta_1=0$
- $H_a$ 대립 가설: $X$와 $Y$ 사이엔 관계가 존재한다 $\leftrightarrow \beta_1 \ne 0$
- $t=\cfrac{\hat{\beta_1}-0}{SE(\hat{\beta_1})}$ : $SE(\hat{\beta_1})=\hat{\beta_1}$의 표준편차
- 만약 귀무가설이 참이라면 $Y=\beta_0 +\epsilon$이 된다