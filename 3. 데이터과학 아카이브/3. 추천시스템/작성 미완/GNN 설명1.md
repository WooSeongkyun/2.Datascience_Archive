## GNN(Graphic Neural Network)란?
- [레퍼런스](https://ganghee-lee.tistory.com/27)
- 그래프의 정의
	- 점들과, 점들을 잇는 선으로 이루어진 데이터 구조
	- 데이터의 관계나 상호작용을 분석하기 위하여 사용한다
	- 예
		- 페이스북 친구
		- 왓챠플레이 유저-영상 감상여부
- 그래프 데이터 표현하기
	-  Adjacency Matrix 
		- 노드간의 relationship 정보를 표현하는 행렬
		- $n$명의 node가 존재하면  $n\times n$ 행렬로 표현된다
		-  노드 $i$ 와 노드 $j$ 가 연결되어 있는 경우  Adjacency Matrix $\textbf{A}$의 성분 $\textbf{A}_{ij}$=$\textbf{A}_{ji}$=1  그외는 0으로 정의한다
	-  Feature Matrix: 각 개인이 가지는 정보를 표현하는 행렬 
		- feature의 수를 $m$개라고 정의한 경우 $n \times m$ 행렬이 생성된다. 이때 Feature Matrix를 $\textbf{H}$ 라 할때 $row_j(\textbf{H})$ 는  $node(j)$ 의 feature값들을 의미한다
 		
- 그래프 분석의 어려움
	- 동일한 그래프도 시각적으로 다르게 보여질 수 있다. 아래의 두 그래프는 인접행렬이 같으므로 동일한 그래프이다
		- ![](https://miro.medium.com/max/1400/1*gISJtYYFcSrbmSSatPwQ5Q.png)
	- 그래프는 사람이 이해할 수 있도록 시각화 하는 것은 어렵다
		- ![](https://miro.medium.com/max/1400/1*Re5pzIhfh5l9yKbjgBRAeg.png)

### 그래프를 사용하는 이유
- 관계나 상호작용같은 추상적인 개념을 다루는데 적합하다
- 복잡한 문제를 더 간단한 표현으로 단순화하거나 다른 관점으로 표현하여 해결할 수 있다
- 소셜 네트워크, 미디어의 영향, 바이러스의 확산등의 연구를 하고 모델링을 하는데 유리하다

### GNN의 종류
- Recurrent Graph Neural Network
- Spatial Convolutional Network
- Spectral Convolutional Network

### GNN이 다루는 문제
- Node Classification
	- Node Embedding을 통해 점들을 분류하는 문제
	- 대표적인 응용 영역으론 인용 네트워크, Reddit 게시물, Youtube 동영상등이 있다
- Link Prediction
	- 그래프의 점들 사이의 관계를 파악하고, 두 점 사이에 얼마나 연관성이 있을지 예측하는 문제이다. 
	- 대표적인 영역으론 페이스북 친구추천, 왓챠플레이(유튜브,넷플릭스) 영상 추천등이 있다
- Graph Classification
	- 그래프를 여러가지 카테고리로 분류하는 문제
	- 대표적인 영역 분자를 그래프 형태로 표현하는 것으로,  화학,생의학,물리학등이 있다


## Application of GNN
-  Scene graph generation by iterative message passing
	- CNN에 기반을 둔 많은 방법들이 이미지에서 물체를 탐지하는데엔 좋은 성능을 보이나, 물체 사이의 관계를 알지는 못한다. CNN으로 탐지된 물체들을 GNN의 방법을 통해 scene-graph를 만들어 그 관계를 파악할 수 있다
	
- Image generation from scence graphs
	- 기존의 이미지 생성방법은 GAN이나 Autoencoder를 사용하나, 아래의 그림 방법을 사용하면 scene graph로부터 이미지를 생성할 수 있다
	
- Machine Learning for Scent: Learning Generalization Perceptual Representations of Small Molecules
	- 분자구조를 그래프로 변환하고, GNN을 거치면 138개의 향기를 예측하는 것이 가능하다
	
- Graph Convolutional Matrix Completion
	- 유저-아이템 평점 행렬이 존재할 때, 기존 평점을 기반으로 message passing function을 활용하여 아직 평가가 없는 유저-영화 쌍의 예상 평점을 계산한다
	- ![](https://miro.medium.com/max/1400/1*7o-Fjb_uAdRcwxXO_WV3qg.png)
	- ![](https://miro.medium.com/max/1400/1*wxSeSt4BLQe_Xl_uY1RuAA.png)
	