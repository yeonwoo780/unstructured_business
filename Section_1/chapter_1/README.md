## [chapter_1] Object Detection과 Segmentation

### Localization/Detection/Segmentation

- Localization: 단 하나의 Object 위치를 Bounding box로 지정하여 찾음

  Regression 수행하여 찾음

  <br>

- Object Detection: 여러 개의 Object들에 대한 위치를 Bonding box로 지정하여 찾음

  <br>

- Segmentation: Detection보다 더 발전된 형태로 Pixel 레벨 Detection 수행

  <br>

### Localization과 Detection

- Localization/Detection은 해당 Object의 위치를 Bounding box로 찾고, Bounding Box내의 오브젝트를 판별

  <br>

- Localization/Detection은 Bounding box regression(box의 좌표값을 예측)과 Classification 두개의 문제가 합쳐져 있습니다

  <br>

- Localization에 비해 Detection은 두개 이상의 Object를 이미지의 임의 위치에서 찾아야 하므로 상대적으로 Localization 보다 여러가지 어려운 문제에 봉착

  <br>

### Object Detection의 주요 구성 요소

- 영역 추정 : 

  Region Proposal

  <br>

- Detection을 위한Deep Learning 네트웍 구성 : 

  Feature Extraction & Network Prediction

  <br>

- Detection을 구성하는 기타 요소 :

  IOU, 

  NMS (None Maximum Suppressing), 

  mAP , 

  Anchor box

  <br>

### Selective Search – Region Proposal의 대표방법

빠른 Detection과 높은 Recall 예측 성능을 동시에 만족하는 알고리즘 

컬러, 무늬(Texture), 크기(Size), 형태(Shape)에 따라 유사한 Region을 계층적 그룹핑 방법으로 계산 

Selective Search는 최초에는 Pixel Intensity기반한 graph-based segment 기법에 따라 Over Segmentation을 수행

<br>

- Selective Search의 수행프로세스

1. 개별 Segment된 모든 부분들을 Bounding box로 만들어서 Region Proposal 리스트로 추가

   <br>

2. 컬러, 무늬(Texture), 크기(Size), 형태(Shape)에 따라 유사도가 비슷한 Segment들을 그룹핑함.

   <br>

3. 다시 1번 Step Region Proposal 리스트 추가, 2번 Step 유사도가 비슷한 Segment들 그룹핑을 계속 반복 하면서 Region Proposal을 수행

   <br>



### Object Detection 성능 평가Metric - IoU

- IoU: Intersection over Union

  모델이 예측한 결과와 실측(Ground Truth) Box가 얼마나 정확하게 겹치는가를 나타내는 지표

  IOU = Area of Overlap / Area of Union : 교집합 / 합집합

  <br>

### NMS(Non Max Suppression)

Object Detection 알고리즘은 Object가 있을 만한 위치에 많은 Detection을 수행하는 경향이 강함.

NMS는 Detected 된 Object의 Bounding  box중에 비슷한 위치에 있는 box를 제거하고 가장 적합한 box를 선택하는 기법

<br>

- NMS 수행 로직

1. Detected 된 bounding box별로 특정 Confidence threshold 이하 bounding box는 먼저 제거(confidence score < 0.5)

   <br>

2. 가장 높은 confidence score를 가진 box 순으로 내림차순 정렬하고 아래 로직을 모든 box에 순차적으로 적용.

   높은 confidence score를 가진 box와 겹치는 다른 box를 모두 조사하여 IOU가 특정 threshold 이

   상인 box를 모두 제거(예: IOU Threshold > 0.4 )

   <br>

3. 남아 있는 box만 선택

   <br>



### mAP (mean Average Precision)

실제 Object가 Detected된 재현율(Recall)의 변화에 따른 정밀도(Presion)의 값을 평균한 성능 수치

<br>

정밀도(Precision)는 예측을 Positive로 한 대상 중에 예측과 실제 값이 Positive로 일치한 데이터의 비율을 뜻합니다.  Object Detection에서는 검출 알고리즘이 검출 예측한 결과가 실제 Object들과 얼마나 일치하는지를 나타내는 지표입니다.

<br>

재현율(Recall)은 실제 값이 Positive인 대상 중에 예측과 실제 값이 Positive로 일치한 데이터의 비율을 뜻합니다. Object  Detection에서는 검출 알고리즘이 실제 Object들을 빠뜨리지 않고 얼마나 정확히 검출 예측하는지를 나타내는 지표 입니다.

<br>

재현율이 상대적으로 더 중요한 지표인 경우는 실제 Positive 양성인 데이터 예측을 Negative로 잘못 판단하게 되면 업무상 큰 영향이 발생하는 경우 : 암 진단, 금융사기 판별

<br>

정밀도가 상대적으로 더 중요한 지표인 경우는 실제 Negative 음성인 데이터 예측을 Positive 양성으 로 잘못 판단하게 되면 업무상 큰 영향이 발생하는 경우: 스팸 메일

<br>
