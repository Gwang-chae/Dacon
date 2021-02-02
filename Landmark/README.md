## 랜드마크 분류 AI 경진대회

* [DACON 랜드마크 분류 AI 경진대회](https://dacon.io/competitions/official/235585/overview/)
* 대용량 이미지에서 랜드마크 이미지를 분류하는 인공지능 알고리즘 개발





## 개요

##### [융복합 프로젝트형] AI 서비스 개발과정 2차 팀 프로젝트

- 작업 기간
  - 2020.10.28 ~ 2020.11.16





- 활용 데이터
  * 1049개 클래스의 비식별화된 한국형 랜드마크 데이터셋
  * Trainset : 88,102장
  * Testset : 37,964장





- 프로젝트 수행 도구
  - Python
  - Tensorflow
  - Keras
  - AWS EC2





* 대회 평가 산식
  * `GAP`(Global Average Precision) 





## 프로젝트 수행방향

1. EDA

   * `Multi-Class Classificatin` 문제의 경우,  데이터 불균형으로 인해 특정 이미지에 `Overfitting`할 수 있음
   * 그러나, 주어진 Dataset에서는 큰 불균형 문제가 보이지 않음
   * Traniset, Validset 분할 시 `stratify` 옵션을 사용해 계층 샘플링 적용

   ![image](https://user-images.githubusercontent.com/65941859/106568290-75183880-6576-11eb-9c2c-a428b5948e93.png)

   

   

2. Preprocessing

   * 학습 속도 향상 및 데이터 관리의 용이성을 위해 `TFRecord`로 변환
     * `TFRecord` : `Google Protocol Buffer Format`을 통해 파일을 `Serialize`

   

   

3. Modeling

   * `Inception`, `InceptionResnet`, `MobileNet`, `DenseNet`, `EfficientNet-B5` 모델 생성
   * `Soft Voting` 앙상블을 통해 확률값 도출 

![image](https://user-images.githubusercontent.com/65941859/106570466-42237400-6579-11eb-861a-aeb59bb1d1a8.png)





## 프로젝트 결과 및 느낀점

* Private Score 0.99302 기록 ( `16 / 82등` )

![image](https://user-images.githubusercontent.com/65941859/106571295-50be5b00-657a-11eb-8c45-91554cb48823.png)





* 한계점
  * 같은 시점에서 확보된 데이터가 대부분으로 데이터의 다양성이 부족함
  * 특정 데이터가 수집된 시기의 외부요인의 영향을 크게 받음으로써 일반화가 어려움





* 제언
  * 상이한 시점과 외부요인을 고려하여 샘플링 된 고품질 Dataset 확보
  * GAN을 통해 날씨, 계절과 같은 외부요인을 적용한 이미지 증식 필요





* 느낀점
  * 사전 모델의 아키텍처를 그대로 사용하여 학습한 점이 아쉬웠음
  * 그러나 `CNN` 기반의 다양한 모델들을 접할 수 있었음
  * 이미지 데이터 처리 기법들에 대한 이해도를 높일 수 있는 프로젝트였음





## PPT

* [PPT](./landmark_classification.pptx)