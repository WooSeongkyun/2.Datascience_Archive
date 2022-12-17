# 6-4. 특이값 분해 SVD

## 6. 특이값 분해 $SVD: Sinulgar\,\,Value\,\,Decomposition$에 필요한 관련 정의 /정리

- 관련 정의  : 수반연산자의 일반화
  - 조건
	- 유한차원 내적공간 $V,W$이 있다고 하자
	- $V,W$에 정의된 내적이 각각 $\langle\cdot,\cdot \rangle_1, \langle\cdot,\cdot\rangle_2$ 라고 하자
	- 어떤 선형연산자 $T : V \rightarrow W$가 있다고 하자
  - 정의
	- 모든 $x\in V ,y\in W$에 대해 $\langle T(x),y \rangle_2=\langle x,T^*(y)\rangle_1$ 인 함수 $T^*:W\rightarrow V$를 $T$의 수반연산자라고 한다
- 관련 정의2 : 양의 정부호/ 준정부호
  - 조건
	- 유한차원 내적공간 $V$가 있고 자기수반 선형연산자 $T$가 있다고 하자
  - 정의
	- 모든 $x \ne0$에 대해 $\langle T(x),x \rangle >0$ 이면 양의 정부호$positive \,\,definite$라고 한다
	- 모든 $x \ne 0$에 대해 $\langle T(x),x \rangle \ge 0$이면 양의 준정부호$positive\,\,semidefinite$라고 한다
  - 이에 따라오는 성질
	- $T$가 양의 정부호(준정부호)이기 위한 필요충분조건은 모든 고윳값이 양수(음이 아닌 실수) 인 것이다
  - 증명
	- 준정부호 → 양수 증명 |
	     - $T$는 자기수반 선형연산자이므로 $T$의 고유벡터로 이루어진 정규직교기저 $\gamma=\{v_1,v_2,...,v_n\}$ 가 존재할 수 있고 다음과 같이 있다 하자
	     - $v \in V$에 대해 $v=\sum_{i=1}^{n} a_iv_i$ 로 적당한 스칼라 $a_i$가 있다하자. 그러면 정의에 따라 $\langle T(v),v \rangle \ge0$.  $\langle T(v),v) \rangle=\langle \sum_{i=1}^{n}a_i\lambda_i v_i,\sum_{j=1}^{n}a_jv_j \rangle=\sum_{i,j} a_i \bar{a_j}\lambda_i \delta_{ij}=\sum_{i}|a_i|^2\lambda_i \ge0$
	     - $|a_i|^2$ 는 임의의 음이 아닌 실수값을 가질 수 있으므로 $\lambda_i$또한 음이 아닌 실수를 가져야 한다
       - 양수 → 준정부호 증명 |
            - $\lambda_i$가 영이 아닌 실수면 당연히 $\langle T(v),v \rangle=\sum_{i}|a_i|^2\lambda_i$  또한 영이 아닌 실수값을 갖는다
            
- 관련 정리: $TT^*$
	- 조건
	    - 유한차원 내적공간 $V,W$와 선형변환 $T\rightarrow W$가 있다 하자
	  - 정리
	    - $TT^*$와 $T^*T$는 양의 준정부호다
	    - $rank(TT^*)=rank(T^*T)=rank(T)$
	  - 증명
		- 모든 $x \in V$에 대하여 $\langle T^*T(x),x \rangle=\langle T(x),T(x) \rangle >0$  (내적의 정의에 따라
		    -  $\langle TT^*(x),x \rangle = \langle T^*(x),T^*(x) \rangle >0$
		- $N(T^*T)=N(T)$ 증명하기
			- $N(T^*T) \subseteq N(T)$  증명 |
				- $x \in N(T^*T)$라 하자
				- $\langle T^*T(x),x \rangle=0$  ,  $\langle T(x),T(x) \rangle =0$
				- $x \in N(T)$
		  - $N(T) \subseteq N(T^*T)$ 증명 |
			- $x \in N(T)$라 하자
			- $T^*T(x)=T^*(0)=0$
			- $x\in N(T^*T)$
	    - 3-1 $page$ 정리를 활용하면 $rank(T)=rank(T^*)$임을 활용할 수 있으므로
	    - $rank(T)=rank(TT^*)=rank(T^*T)$

## 6-1. 선형변환의 특이값 분해$SVD$ 정리

- 조건
	- 유한차원 내적공간 $V,W$와 랭크 $r$인 선형변환 $T:V\rightarrow W$가 있다 하자
- 정리
	- $T(v_i)=$ $\begin{pmatrix} \sigma_iu_i  \,\,\,(1\le i \le r) \\  0 \,\,\,\,\,\,(i>r)\end{pmatrix}$
		- 이 되도록하는
		- $T^*T$의 고유벡터로 이루어진 $V$의 정규직교기저 $\beta=\{v_1,v_2,...,v_n\}$와
		- $T^*T$의 고유값의 제곱근에 해당하는 값인 $\sigma_i$
		- $W$의 정규직교기저 $\gamma=\{u_1,u_2,...,u_m\}$ 가 존재한다
- 증명
	- 위의 정리에 따라 $rank(T^*T)=r$ 이고 $T^*T$는 양의 준정부호이다
	- 즉 고유값 $\lambda_i$에 대응하는 고유벡터 $v_i$로 이루어진 정규직교기저 $\beta=\{v_1,v_2,...,v_n\}$이 존재한다
	- 이떄 $\lambda_1 \ge \lambda_2 \ge ... \ge \lambda_r \ge0$ 이고 , $i >r$ 일떄 $\lambda_i=0$을 두자
	- $\sigma_i=\sqrt{\lambda_i}, u_i=\displaystyle\frac{1}{\sigma_i}T(v_i)$라 정의하자 $\gamma=\{u_1,u_2,...,u_r\}$이 $W$의 정규직교부분집합임을 보일것이다
	- $\langle u_i,u_j \rangle= \langle \displaystyle\frac{1}{\sigma_i} T(v_i),\displaystyle\frac{1}{\sigma_j}T(v_j) \rangle=\displaystyle\frac{1}{\sigma_i\sigma_j}\langle T^*T(v_i),v_j \rangle=\displaystyle\frac{1}{\sigma_i\sigma_j}\langle \lambda_i v_i,v_j \rangle$
	- $=\displaystyle\frac{\lambda_i}{\sigma_i\sigma_j}\delta_{ij}=\delta_{ij}$
	- 따라서 $\{u_1,u_2,...,u_r\}$는 정규직교이다
	- 대체정리에 따라 $\{u_1,u_2,...,u_r\}$와 더불어 선형독립인 $m-r$개의 벡터를 찾고 그람-슈미트 과정을 하면 $\gamma=\{ u_1,u_2,...,u_r,u_{r+1},...,u_m\}$, $W$의 정규직교기저를 얻을 수 있다
  - $i>r$ 일 때 $T(v_i)$에 대해 살펴보자
      - $j>r$ 일때 $T^*T(v_j)=0$ 이고 $\langle T^*T(v_j),v_j \rangle= \langle T(v_j),T(v_j) \rangle=0$ 이므로 $T(v_j)$도 0이 된다
  - 이번엔 $T^*(u_i)$를 살펴보자
      - $T^*(u_i)=\sum_{j=1}^{n} \langle T^*(u_i),v_j \rangle v_j$
	      - $\langle T^*(u_i),v_j\rangle= \langle u_i,T(v_j)\rangle=\sigma_j \delta_{ij}$ $\,\,\,(1\le i \le r)$ $or$  $0 \,\,\,(i>r)$이 된다
	      - $T^*(u_i)=\sigma_i v_i \,\,\,(1\le i \le r)$ $or$ $0\,\,\,(i>r)$ 이다

## 6-2. 행렬의 특잇값 분해 정리

- 조건
	- 랭크가 $r$ 인 행렬 $\mathbf{A} \in \mathbf{M}_{m \times n}(F)$ 가 존재한다고 하자
	- 행렬 $\mathbf{A}$의 특이값이 $\sigma_1 \ge \sigma_2 \ge ...\ge \sigma_r >0$ 이라고 하자
	- 행렬 $\Sigma \in \mathbf{M}_{m \times n}(F)$  가 다음과 같이 정의되었다 하자
		- $\Sigma_{ij}= \sigma_i \,\,(i=j \le r)\,\,$ $or$  $else \,\,0$
- 정리
	- $\mathbf{A}=\mathbf{U}\Sigma \mathbf{V}^*$를 만족시키는 유니타리 행렬 $\mathbf{U} \in \mathbf{M}_{m \times m}(F)$ 와 유니타리 행렬 $\mathbf{V} \in \mathbf{M}_{n \times n}(F)$ 가 존재한다
- 증명
	- $T=L_A:F^n\rightarrow F^m$ 이라 하자
	- 앞의 정리를 따라 $T(v_i)=\sigma_iu_i \,\,(i \le i \le r)$ $or$ $0 \,\,(i>r)$ 을만족시키는
	- $F^n$의 정규직교기저 $\beta'=\{v_1,v_2,...,v_n\}$ 과
	- $F^m$의 정규직교기저 $\gamma'=\{u_1,u_2,...,u_m \}$이 존재한다
	- 또한 $F^n,F^m$의 표준기저를 각각 $\beta,\gamma$로 둔다면
	- $[T]_{\beta}^{\gamma}= [I]_{\gamma'}^{\gamma} [T]_{\beta'}^{\gamma'} [I]_{\beta}^{\beta'}$ 의 식이 성립한다
	- $[I(u_j)]_{\gamma}=[I]_{\gamma'}^{\gamma}[u_j]_{\gamma'}=col_j([I]_{\gamma'}^{\gamma})=[u_j]_{\gamma}=u_j$
	- $[I(v_j)]_{\beta}=[I]_{\beta'}^{\beta}[v_j]_{\beta'}=col_j([I]_{\beta'}^{\beta})=[v_j]_{\beta}=v_j$
	- 로 $[I]_{\gamma'}^{\gamma}=\mathbf{U}$ , $[I]_{\beta'}^{\beta}=\mathbf{V}$ 유니타리 행렬임이 증명된다

## 6-3. truncated SVD

- 조건
	- 랭크가 $r$ 인 행렬 $\mathbf{A} \in \mathbf{M}_{m \times n}(F)$ 가 존재한다고 하자
	- 행렬 $\mathbf{A}$의 특이값이 $\sigma_1 \ge \sigma_2 \ge ...\ge \sigma_r >0$ 이라고 하자
	- 행렬 $\Sigma \in \mathbf{M}_{m \times n}(F)$  가 다음과 같이 정의되었다 하자
		- $\Sigma_{ij}= \sigma_i \,\,(i=j \le r)$ $or$  $0 \,\,\,(else)$
- Statement
	- $\mathbf{A}=\mathbf{U}\Sigma \mathbf{V}^*$를 만족시키는 유니타리 행렬 $\mathbf{U} \in \mathbf{M}_{m \times m}(F)$ 와 유니타리 행렬 $\mathbf{V} \in \mathbf{M}_{n \times n}(F)$ 가 존재한다
	- $\mathbf{U}$ 의 $r$ 개 row를 갖는 부분행렬 $\mathbf{U}'$ 과 $\mathbf{V}$ 의 $r$ 개 column를 갖는 부분행렬 $\mathbf{V}'$ , $\Sigma$의  $(r \times r)$ 영역을 갖는 부분행렬  $\Sigma'$ 이 있다 하자 그러면
		- $\mathbf{A}=\mathbf{U}'\Sigma' (\mathbf{V}')^*$ 이 성립한다(be called compact SVD)
- 이미지

  - full SVD![](https://t1.daumcdn.net/cfile/tistory/2435CA425266197F02?download)
  - compact SVD ![](https://t1.daumcdn.net/cfile/tistory/23378F3352661E3336?download)
  - truncated SVD![](https://t1.daumcdn.net/cfile/tistory/2746F23952661E501D?download)
	- 0이 아닌 singular value까지 제거하여 이 경우에는 원래의 $\mathbf{A}$가 보존되지 않고 $\mathbf{A}$에 대한 근사행렬 $\mathbf{A}'$이 나오는 방정식

### truncated SVD 효과

- 데이터 차원을 줄임으로서
	- 오버피팅을 줄일 수 있다
	- 설명력이 낮은 피처들을 제거할 수 있다
- 입력데이터의 sparsity 를 줄일수 있다

 




























