## 토픽 모델링
- 문서 집합에서 토픽을 찾아내는 프로세스 이다
- LDA는문서가 토픽들의 혼합으로 구성되어 있으며, 토픽들은 확률 분포에 기반하여 단어들을 생성한다고 가정한다. 

## 잠재 디리클레 할당의 개요
- LDA의 가정
	- LDA는 단어의 순서는 해석에 영향을 미치지 않는다(중요하지 않다) 고 가정한다
- LDA 알고리즘 순서
	1. LDA는 각 문서가 어떤 토픽 분포비율을 계산한다
	2. 각 토픽들은 각 단어들의 분포비율을  계산한다. 
	- => 이 결과로 LDA가 토픽의 제목을 정해주지는 않지만, 알고리즘의 사용자는 토픽의 단어 분포비율을 봄으로서 '특정 단어에 대한 토픽이다'라고 해석할 수 있다
- LDA 수행하기
	- 사용자는 알고리즘 토픽 갯수 k개 지는하기
	- 모든 단어를 k개중하나의 토픽에 할당하기
	- 모든 문서의 모든 단어에 대하여 반복하기
	- 어떤 문서의 각 단어 $\omega$ 는 자신은 잘못된 토픽에 할당되어 있지만 다른 단어들은 전부 올바른 토픽에 할당되어 있는 상태라 가정하자. 이때 단어 $\omega$ 는 두 가지 기준에 따라 토픽이 째 할당 된다
	- ![](LDA%20이미지.png)


# 관련 논문

## LDA를 이용한 온라인 리뷰의 다중 토픽별 감성분석- TripAdvisor사례를 중심으로
- [레퍼런스 출처](https://koreascience.kr/article/JAKO201811648108694.pdf)
### 1. 서론
- 소셜 네트워크상에서 사람들이 본인의 생각과 느낌을 자유롭게 표현하는 활동들은 폭발적으로 증가하고 있다. 그중에서도 여행과 관련된 정보 검색은 가장 인기있는 온라인 활동중 하나이다. 고객들이 표출하는 감정과 서비스에 대한 평가가 비지니스에 대한 중요성이 점점 더 높아짐에 따라 이를 활용하고자 하는 노력도 커지고 있다
- 온라인 고객리뷰는 많은 고객에 의해 생산 및 재생산되므로, 이 전체 내용을 상세히 분석하는데엔 너무나도 많은 시간과 노력을 요구한다. 이에 따라 대량의 리뷰에서 고객들의 의견을 정확하게 추출해내는 자연어 처리 및 텍스트 마이닝과 같은 분석 기법 개발의 관심이 높아지고 있다
- 오피니언 마이닝 또는 감성분석이라 불리는 기법은 리뷰에서 유용한 정보를 추출하여 사용자의 성향이나 의견을 요약하거나 리뷰의 주제에 대해 긍정 또는 부정적 표현을 탐지하는 기술이다. 감성 분석은 문서수준, 문장수준,토픽수준으로 나뉜다. 본 연구는 토픽수준의 감성분석으로서 문서에 포함된 여러 토픽과 관련된 긍정 또는 부정적 뉘양스를 탐지하는 것이다.
- 토픽 기반의 감성분석은 고객의 감성을 세부적으로 잘 파악할 수 있다는 이점을 갖는다. 식당에 관련된 리뷰는 일반적으로 음식,환경,분위기,서비스등 여러 토픽에 대한 종합적 평가로 볼 수 있다. 고객은 전반적으로 좋다는 평가를 내렸음에도, 음식맛이나 분위기는 좋았지만 서비스는 별로였다등의 평을 내릴 수도 있다. 이런 경우의 이해를 위해서라도 토픽단위의 분석이 필요하다
#### 본 연구 방법
- 세계 주요 관광도시에 위치한 호텔의 리뷰 데이터를 수집 및 분석하였다
- 이때 여행객 리뷰에서 숨겨진 토픽을 추론하기 위해 LDA를 활용하였고, 추출된 토픽을 기반으로 감성분석을 실시하였다

### 2. 연구방법
- LDA(Latent Direchlet Allocation
	- 비지도 학습 알고리즘으로, 수많은 비구조적 문서에서 단어들간 관련성에 따라 토픽별로 분류하는 확률적 토픽모델링 알고리즘이다.
	- [LDA는Clustering 인가?](https://highdemandskills.com/lda-clustering/) => 결론; 아님
	- LDA의 목표는 문서별 각 토픽의 비율과, 각 토픽별 단어의 비율들을 알아내는 데에 있다
	- LDA 모형이 전체 토픽 개수 K개를 결정해야 하는데, 이때 최적의 K값을 구하기 위한 방법으로 혼잡도perplexity를 활용할 수 있다. 이 값이 낮을수록 LDA가텍스트를 분석할 때 우수한 일반화 능력을 갖는다
	- 이 연구에서는 토픽의 개수를 50,100,200개, 키워드는 top5를 활용하였다
- LDA기반 감성분석 Sentiment Analysis based on LDA
	- 감성분석 또는 오피니언 마이닝이라 불리는 기법은 텍스트데이터에 잠재되어 있는 사용자의 감정, 태도등을 유추하는 분석기법이다
	- 감성분석은 사전기반의 접근법을 활용할 수 있다 감성사전에 감성단어들의 감성수치를 미리 정의하여, 문서에 나타난 단어들을 보고 리뷰의 감성값을 계산하는 것이다.
	- Joint Sentimnet/ Topic Model(JST)라불리는 확률적 모델링 프레임웤은 감성분류와 토픽추출을 동시에 진행할 수 있는 모델이다

### 3. 연구 프레임워크
- 데이터 수집과 전처리
	- 트립 어드바이저에서 고객리뷰 크롤링
	- 평가 리뷰 DB에 저장
	- 불용어 제거
	- 리뷰 용어 DB에 저장
- 토픽별 문장 DB 구축
	- 토픽추출
		- LDA모델 적용
		- Topic개수 K개 결정
			- 혼잡도perplexitiy와 교차검증 cross-validation을 사용하기
		- Topic 추출
		- Topic Naming
	- 호텔 6개 속성 매칭
	- 토픽별 문장 추출
		- 토픽별 키워드 결정
		- 리뷰 문장에서 토픽별 키워드 매칭
		- 토픽별 포함한 문장 분류
- 토픽별 감성값 계산 및 검증
	- 문장의 감성값 계산
	- 호텔의 6개 속성 DB
	- 토픽별 감성값 DB활용
	- 분류 행렬
	- 결과 분석


- Tripadvisor는 rooms,loction,cleanliness,value,sleep quality, service 6개의 평가점수가 존재한다. 이를 활용하여 LDA를 실행하면 다음과 같은 결과를 얻을 수 있다

Keywords 결과
- rooms
	- shower, bathroom, water, TV, bath, toilet, towels, bed, room, floor, facing, floors, beds, double, space, single, area, design, décor, style, suite, upgrade, wifi, internet, view, views, cleanliness, noise, air conditioning, smell, television, bug, carpet, minibar, refrigerator, amenity, furniture, wall, window, phone, light, kitchen
- location
	- walk, station, minutes, road, minute, street, area, min, location, metro, tower, close, located, store, subway, convenient, airport, bus, mtr, mall, taxi, train, taxis, skytrain, sky, walking, distance, city, central
- cleanliness
	- clean, dirty, dirt, smell, stain, broken, mold
- value
	- free, charge, worth, price, cheap, budget, money, expensive
- sleep quality
	- noise, night, sleep, quiet, soundproof, bed comfort, room temperature
- service
	- staff, clean, breakfast, park, lounge, club, executive, drinks, wifi, internet, lobby, service, reception, guests, coffee, food, buffet, tea, fruit, restaurant, experience, dinner, front desk, concierge, amenities, pool, orchard, gym

## 토픽별 문장분류와 감성분석 과정
1. 수집한 리뷰를 문장 단위로 나눈다
2. 각 문장을 토픽으로 분류하고, 어휘기반 접근법 Lexicon-based Approach를 실행한다. 각 문장에 존재하는 긍정+(-부정) 단어 갯수를 계산하고, 각 토픽에 대하여 합한다. 그에 대한 값이 0 이상이면 긍정, 0 미만이면 부정으로 분류한다
	- 이러한 기술의 한계점은 언어가 사용되는 상황이나 환경에 대한 이해 없이 일반적 의미에만 의존한다는 것이다. (반어법등의 맥락을 비튼 표현들을 캐치해낼 수 없음)



## LDA  관련 코드
