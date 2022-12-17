# 1-3. Statistical Learning: KNN 분류법

### 5.분류 오차

- $error\,\,rate\equiv\cfrac{1}{n}\sum_{i=1}^{n}I(y_i\ne\hat{y_i})$
    - $if\,\,y_i=\hat{y_i} \,\,then\,\,I=1,\,\,\,\, y_i\ne\hat{y_i}\,\,then\,\,I=0$
- $Bayes \,\,Classifer$란 무엇인가?
    - 조건부 확률 $P(Y=j|X=x_i)$이 최대가 되는 클래스 $j$로 측정값 $x_i$를 할당하는 분류방식이다
    - 가장 낮은 $test\,\,error\,\,rate$를 만드는 분류방식이다
        - $Bayes\,\,error\,\,rate=1-max_jP[Y=j|X=x_0]$
    - 현실에서 독립변수를 전제로한 클래스의 확률분포 $P(Y=j|X=x_i)$는 알수가 없다. $KNN$는 이 조건부분포를 추정하는 방법이다.

### 6. $KNN$ $classifier$

- 작동 알고리즘
    - 특정 데이터포인트 $x_0$에 가장 가까운 $K$개의 데이터포인트를 찾는다 이때 이 $K$개의 원소를 $\mathscr{N}$ 이라 표현하자
    - 조건부확률 $P(Y=j|X=x_o)$의 값을 추정한다. $\mathscr{N}$내에 있는 원소중 클래스가 $j$인 데이터포인트의 수 / $K$로.  수식으로 표현하면 다음과 같다
        - $P(Y=j|X=x_0)=\cfrac{1}{K}\sum_{i\in\mathscr{N}}I(y_i=j)$
    - $x_0$를 가장 높은 확률을 가지는 클래스 값으로 분류한다
- $K$ 값에 따른 분류의 차이
    - $K$값이 작을수록 낮은 편차를 가지나 높은 분산을 갖는다
    - $K$값이 클수록 덜 유연하나 경계가 선형에 가까워 진다
- $1/K-Error\,\,rates$ 관계식
    - $1/K$ 값이 증가할수록($K$값이 작아질수록) $training\,\,error\,\,rate$는 커진다
    - $1/K$값에 대하여 $test\,\,error\,\,rate$ 는 $U$자 형을 가진다
