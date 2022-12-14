# 1-1. Statistical Learning: 통계학습의 기본개념

## 1. $Statistical\,\,Learning$이란 무엇인가?

- 통계학습은 1. 모델을 세우고 2.데이터를 학습시켜 3.데이터간 상호관계를 파악하려는 일련의 행동과 방법이다.
- 예: 광고와 특정 상품 사이 관계
    - 독립변수 $independent\,\,variable$ : 광고예산
        - $TV$ 예산
        - $radio$ 예산
        - $newspaper$ 예산
    - 종속변수 $dependent\,\,variable$ : 판매량
    - 이경우 다음과 같은 관심사를 가질 수 있다
        - 그 외에 어떤 미디어광고가 판매량에 영향을 줄 수 있을까?
        - 어떤 미디어 광고가 매출에 가장 큰 영향을 줄까?
        - TV 광고에 대한 특정 지출이 매출량을 얼마나 늘릴까?
- 명칭들
    - 독립변수는 $input/predictors/features$ 라고도 불린다
    - 종속변수는 $output/response$ 라고도 불린다
    - 우연오차항 $\,random\,\,error$ 은 원인을 알수 없거나 측정의 한계로 수식 보정이 불가능한 오차로 추정량이 0이다
- 표기법
    - 종속변수는 $Y$로 표기한다
    - 독립변수는 $X_j \,\,for\,\,j=1,2,3,...$으로 표기한다
    - 우연 오차항은 $\epsilon$이라 표기한다
    - 일반적인 형태의 함수는 다음과 같다
        - $Y=f(X)+\epsilon\,\,,\,\,X=(X_1,X_2,...,X_p)$

## **2.  함수 추정( 중요)**

### 2-1. 추정 오차

- $\hat{Y}=\hat{f}(X)$ 라고 정의한다 ($\hat{\epsilon}=0$ )
    - $\hat{f}$는 표본데이터를 활용하여 함수 $f$를 추정한 것이다
    - $\hat{Y}$는 $\hat{f}$에 $input$ $X$ 를 대입하여 나온 $output$이다
- $error$의 두 종류
    - $reducible\,\, error$
        - $\hat{f}$ 와 $f$의 차이
        - 줄일 수 있는 오류( $f$와 $\hat{f}$는 같은 독립변수를 갖으므로)
    - $irreducible\,\,error$
        - $f(X)$ 와 $Y$ 차이
        - 줄일 수 없는차이
        - 정확도 $accuracy$의 상한을 제한하는 역할을 한다

### 2-2. 추정방법

- $Parametric\,\,Method$
    - 함수 형태에 대해 가정한다.
        - 가장 단순한 형태의 가정은 함수 $f$가 선형이란 것으로 다음과 같다
        - $Y\sim f(X)=\beta_o+\beta_1X_1+\beta_2X_2+...+\beta_pX_p$
    - $training\,\,data$를 활용하여 모델을 학습시킨다.
        - 선형모델의 경우 파라미터 $\beta_0,\beta_1,\beta_2,...,\beta_p$의 추정을 한다
        - 가장 일반적인 방법은 최소제곱법 $ordinary\,\,least\,\,square$ 이다
    - 장점과 단점
        - 함수의 종잡을수 형태를 추정하는 문제를 파라미터 $\beta_0,\beta_1,\beta_2,...,\beta_p$를 추정하는 문제로 난이도를 낮춘다
        - 대신 이 가정한 함수의 형태가 진짜 함수 $f$와 다를수록 추정결과는 나쁠 수 밖에 없다
            - ⇒ 이러한 문제를 극복하기 위해 좀 더 다양한 유연한$flexible$ 형태의 모델  을 가정한다
            - ⇒ 한편 유연한 형태의 모델을 만들기 위해선 더 많은 수의 파라미터를 요구한다. 파라미터가 많은 모델은 $overfitting$이라 불리는 문제현상을 야기할 수 있다
- $Non-parametric\,\,Method$
    - 추정방법
        - 함수 형태에 대해 어떤 가정도 하지 않는다
        - 대신 함수가 데이터포인트와 최대한 근접해 있으며, 지나치게 구불구불하거나 거칠지 않다고 가정한다
    - 장점과 단점
        - 좀 더 다양한 함수의 형태를 추정하는 데 좋은 방식이다
        - 적은 수의 파라미터로 추정하는 것이 아니기에 큰 수의 관측값 데이터가 필요하다

### 2-3. 과적합, 과소적합 문제

- 일반적으로 모델 유연도 $\uparrow$,파라미터 수 $\uparrow$, 필요한 관측 데이터 수 $\uparrow$는 양의 상관관계를 갖는다
- 일반적으로 편향과 분산은 $trade-off$ 관계를 갖는다
- 과집합 $overfitting$
    - 파라미터 수$\uparrow$ , 훈련 데이터 수$\downarrow$ : 훈련데이터엔 잘 맞지만 테스트데이터엔 잘 맞지 않는 경우
    - 훈련 데이터셋에 따른 모델의 분산$variation$이 큰게 문제이다
- 과소집합 $underfitting$
    - 파라미터 수$\downarrow$, 훈련 데이터 수$\uparrow$ : 너무 단순한 모델을 세워 학습 데이터와 잘 맞지 않는 경우
    - 모델의 편향 $bias$이 큰게 문제이다


## 2-4. 모델 정확도와 해석가능성 사이 $trade-off$관계

- 한정적인 모델일수록 단순하여 해석하기 용이하다
- 복잡한 모델일수록 더 다양한 관계들을 표현할 수 있다