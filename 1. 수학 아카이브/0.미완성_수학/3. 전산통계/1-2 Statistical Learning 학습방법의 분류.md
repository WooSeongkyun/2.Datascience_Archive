# 1-2. Statistical Learning: 학습방법의 분류

## 1.지도학습과 비지도학습

- 지도학습
    - 독립변수 관측치와 종속변수 관측치 데이터셋을 가지고 있을 때 데이터를 활용하여 모델을 학습시키는 방법
    - 종류
        - $linear\,\,regression$
        - $logistic\,\,regression$
        - $GAM$
        - $support\,\,vector\,\,machine$
- 비지도학습
    - 독립변수 관측치는 가지고 있으나 종속변수 관측치 데이터셋이 없는경우. 데이터를 활용하여 모델을 학습시키는 방법
    - 위의 데이터로 예측$predict$을 하는 모델을 학습시키는 것은 불가능하다.
    - 대신 독립변수간의 관계를 파악하는데에 활용할 수 있다
    - 종류
        - $cluster\,\,analysis$ 군집분석

## 2.회귀문제와 분류문제

- 회귀문제 $regression\,\,problem$
    - 종속변수가 연속된 값일 경우
- 분류문제 $classification\,\,problem$
    - 종속변수가 분류 및 정수일 경우

## 3.$Fitting$(잘 들어맞음) 측정하기

- 추정한 모델이 실제 현상을 얼마나 잘 예측하는지를 정량화하기 위해선 어떻게 식을 세워야 하는가?
- $MSE=\cfrac{1}n{}\sum_{i=1}^{n}(y_i-\hat{f}(x_i))^2=E[(y-\hat{f}(x))^2]$
    - $MSE$ : 평균 제곱 오차
    - $n$ : 관측치의 갯수
    - $y_i$ : $i$ 번째 관측대상의 종속변수 값
    - $\hat{f}(x_i)$ : $i$번째 추정치
    - ⇒ $MSE$가 작을수록 추정한 모델 $\hat{f}$가 정확히 예측한다고 해석한다
- 모델이 훈련 데이터셋에 잘 들어맞나는 하나도 중요하지 않다. 그보다는 앞으로 예측할 데이터가 잘 들어맞는가가 중요하다
    - 훈련 데이터셋을 $\{(x_1,y_1),(x_2,y_2),...,(x_n,y_n)\}$이라 표현하자
    - $\hat{f}(x_j) \sim y_j\,\,for\,\,j=1,2,...,n$ 는 별로 중요하지 않다
    - 대신 테스트셋 $\{ (a_1,b_1),(a_2,b_2),...,(a_m,b_m)\}$ 이 있어
    - $\cfrac{1}{m}\sum_{i=1}^{m}(b_i-\hat{f}(a_i))^2$이 최저가 되는 $\hat{f}$를 찾는 것이 목표이다
    - ⇒ 본질적 문제는 훈련 데이터셋에서 최소 $MSE$를 가지던 함수가 테스트 셋에서 최소 $MSE$를 가지리란 보장은 없다
    - 오히려 지나치게 과적합 $overfitting$한 모델은 최대한 데이터포인트에 가깝기 위해 꼬불꼬불하게 모양이 형성되며 그 결과 실제 함수와는 크게 다르게 된다
    

## 4.Bias- Variance Trade- off

- bias의 정의
    - $T$ 를 statistics, $\theta$를 추정하고자하는 파라미터라고 하자
    - $bias(T,\theta)=E(T)-\theta$
    -
- $MSE=E[(y-\hat{f}(x))^2]=Var(\hat{f}(x))+[Bias(\hat{f}(x))]^2+Var(\epsilon)$
    - 증명은 생략하고 받아들이자
- 성질
	- $MSE$를 최소화하기 위해선 $\hat{f}$의 bias와 variance를 최소화해야한다.
	- $Var$은 nonnegative이고 $Bias^2$ 또한 nonnegative이므로 $MSE>0$이다		    
- 해석
	- 편향bias 은 실제로 복잡한 현상을 단순한 모델로 근사함으로서 발생하는 에러이다
	 - 일반적으로 유연한 모델일수록 더 높은 분산variance값을 갖는다
- $Flexibility-Bias-Variance$ 관계
    - 일반적으로 $flexibility$가 올라갈수록 $bias$는 낮아진다
    - 일반적으로 $flexibility$가 올라갈수록 $variance$는 높아진다
    - $Var(\epsilon)$는 $irreducible$ $error$이다
    - 셋을 더한 $MSE$는 일반적으로 $concave\_downward$한 모양을 갖는다