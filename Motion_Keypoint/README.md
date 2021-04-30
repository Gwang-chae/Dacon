# 모션 키포인트 검출 AI 경진대회

<br>🔍 **Overview**

* [**DACON 모션 키포인트 검출 AI 경진대회**](https://dacon.io/competitions/official/235701/overview/)

- Motion Keypoint Detection 알고리즘 개발
- 스마트 헬스케어 산업에 적용 가능한 데이터 분석 방법
- 프로젝트 수행 기간 ( 2021.02.10 ~ 2021.04.05 )

<br>

---

👨🏻‍💻 **Role**

Object Detection 모델을 생성해 운동 동작을 취하고 있는 사람을 검출하고, Keypoint Detection 모델을 사용해 keypoint들을 찾아내었습니다.

- 데이터 구성 : Train 이미지 4195장, Test 이미지 1600장, 24개 keypoint의 (x, y) 좌표가 담긴 train용 csv 파일

1. 데이터 수집 및 전처리
   - Object Detection 모델 성능 향상을 목적으로 AI Hub에서 외부데이터 수집. Supervisely를 활용한 데이터 라벨링 수행
   - 제공된 train용 csv 파일에서 Human Error 발견, Supervisely로 직접 Human Error 수정
   - Train, Valid 폴더에 9:1 비율로 Train set, Validation set 분리
   - (x, y)의 최대, 최소값을 이용하여 객체마다의 bounding box file 생성
   - SOTA 모형 사용을 위해 COCO format 변환
2. Object Detection 모델 생성
   - Resnet backbone의 DetectoRS 모델 사용
   - 검증 결과 mAP Score 0.971 기록
   - 특정 운동 기구(철봉, 로잉머신)를 이용하는 이미지에서 사람이 아닌 의자를 오검출 하는 케이스 발견
   - 데이터 수집 과정에서 구한 외부데이터로 재학습
3. Keypoint Detection 모델 생성
   - DarkPose 모델 사용
   - 기존 COCO Keypoint Dataset이 17개의 포인트를 검출하는 목적으로 하기 때문에 24개의 포인트를 검출하도록 커스터마이징
   - 이미지 사이즈, multi-scale training/testing, Resnext backbone으로의 교체 등 다양한 조합으로 모델 성능 개선 시도

<br>

---

📚 **Stack**

- Python
- Tensorflow
- Keras
- Pytorch

<br>

---

⁉️ **결과/성과, 느낀점**

**결과/성과**

- Private Score 15.46656(RMSE) 기록
- 리더보드 기준 ( 19 / 156 등) 기록

**느낀점**

- 처음 Baseline을 짜면서 Image Data Augmentation시, Keypoint들을 이에 맞춰 수정하지 않아 낮은 성능으로 인해 어려움을 겪었음

- 이미지 각도에 따라 운동기구들이 bounding box 들어가는 이미지가 존재하기 때문에

  Test 이미지를 위한 bounding box file 생성 시 종종 운동기구의 범위까지 bouding box로 잡힘

  → 추가적인 훈련데이터 혹은 mask가 있으면 오차를 줄일 수 있을 것 같음

- 대회 막바지 제공 받은 train용 csv 파일에 human error가 있다는 점을 발견해서 급하게 데이터 프레임을 수정하여 재학습했으나,

  이 과정에서 데이터 프레임의 변경 사항이 저장되지 않아 오류들이 다시 재학습 되면서 Score를 끌어올리지 못했음.

  → 이 경험을 통해서 항상 제공받은 데이터가 완전하지 않다는 생각을 가져야 함을 깨닫게 되었고,  변경사항의 저장을 습관화해야겠다고 느낌.

<br>

---

**ToolBox**

1. [mmdetection](https://github.com/open-mmlab/mmdetection)

2. [mmpose](https://github.com/open-mmlab)