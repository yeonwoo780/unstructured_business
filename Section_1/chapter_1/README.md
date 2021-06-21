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

  

  

  

