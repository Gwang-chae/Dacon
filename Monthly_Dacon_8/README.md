# 심리 성향 예측 AI 경진대회

<br>

### 개요

* [DACON 심리 성향 예측 AI 경진대회](https://dacon.io/competitions/official/235647/overview/)
* 심리학 테스트 분석 알고리즘 개발
* 국가 선거 투표자/미투표자의 심리학적 성향을 분석
* 프로젝트 수행기간 ( 2021.09.28 ~ 2021.11.02 )

---

➡️ **프로젝트 수행방향**

데이터 구성 : train.csv shape(45532, 78),  test.csv shape(11383, 77)

1. **데이터 전처리**
2. **데이터 가변수화**
3. **Neural Network 모델 작성**
4. **AutoML 사용**
5. **Neural Network를 wrappers를 사용하여 classifier 형태로 변형**
6. **변형한 Neural Network와 AUC 기준 AutoML 상위 8개 모델과 Soft Voting Ensemble**

---

📚 **Stack**

- Python
- Tensorflow
- Keras
- Pytorch

---

⁉️ **결과/성과, 느낀점**

- Private Score 0.77787(AUC) 기록

- 리더보드 기준 ( 64 / 581 등) 기록

- 데이터 가변수화 함수로 pandas에서 get_dummies 함수를 제공하는 것을 알게 되었음

- sklearn의 VotingClassifier 모듈을 사용하기 위해 Neural Network를 classifier 형태로 변형했음

  그러나, Soft Voting인만큼 각 모델 예측치를 구한 후 모델 수만큼 나눴으면 더 간편했을 것이라 생각됨

- 데이터 전처리 파트는 공유 코드를 참조했는데, 대회 근간이 되는 심리학 테스트의 사전지식을 분석한 점이 인상 깊었고

  도메인지식의 중요성을 다시 한번 깨닫게 되었음

- 정형데이터를 사용하는 대회는 참가자들간의 점수 격차가 상대적으로 적은 편으로,

  Public Score에 기댈 것이 아니라 내 모델의 Validation Score를 신뢰해야 한다는 것을 깨닫게 된 프로젝트였음