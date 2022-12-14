# 2-3. Linear Regression: 다른 고려사항

- 영단어
    - $balance$: 잔고
    - 

### 1.카테고리 변수

- 정성적/카테고리별/이산적 독립변수
    - 결과가 0과 1 두개일 경우
    - 결과가 2개 이상일 경우

### 2. 일반화된 회귀모델: 독립변수간의 독립성 가정 제거하기

- 일반화된 회귀모델: 독립변수간의 독립가정을 제거하기
    - 독립변수 $X_1,X_2$, 종속변수 $Y$, 오차항 $\epsilon$, 계수$\beta_0,\beta_1,\beta_2,\beta_3$가 있다하자.
    - 독립변수 $X_1$과 $X_2$가 상호간의 영향을 미친다고 하자
    - 그럼 수많은 모델의 가능성이 있지만 그중 하나는
        - $Y=\beta_0+\beta_1X_1+\beta_2X_2+\beta_3X_1X_2+\epsilon$
        - $Y=\beta_0+\tilde{\beta}(X_2)X_1+\beta_2X_2+\epsilon$ 이다
    - 계층적 구조 원리 $hierarchical\,\,principle$
        - 상호작용항 $X_1X_2$가 유효하면 항 $X_1,X_2$는 $p$값과 관계없이 포함하여야 한다

### 3. 다항식 회귀 $polynomial\,\,regression$

- 선형회귀를 할때 선형성의 조건은 독립변수가 아닌 계수에 있으므로 독립변수에 멱함수나 지수꼴이 오는 것도 가능하다

### 4.일반화된 회귀모델: 오차항간의 상관관계 가정 제거하기

- 실제로 많은 경우 인접한 시간대에 관측된 관측치들 오차는 양의 상관관계를 갖는다
- 실제로는 추정된 표준오차는 실제 표준오차값보다 작게 측정된다
- 그 결과 신뢰구간과 예측구간은 실제 더 좁을 것이다.
- $p$값 또한 실제로 더 낮은 값일것이다
- 오차항 상관관계 가정의 반례: $n$개의 데이터셋을 자기 스스로 복사해 붙여만든 $2n$의 데이터셋으로 학습시킨다고 하자. 오차항간 무상관관계를 가정하면 동일한 데이터를 썼음에도 신뢰구간은 $\sqrt{2}$ 더 작아진다

### 5.일반화된 회귀모델: 이분산성의 경우

- 등분산성($Var(\epsilon_i)=\sigma^2)$ 가정이 아닌경우
- $Fitted\,\,Values-Residuals$ 그래프가 깔때기모양인 현상이 발생하곤 한다