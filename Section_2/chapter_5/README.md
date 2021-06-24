## [chapter_5]예지 보전 지능화

### 예지 보전 정의 및 사례 리뷰

#### 예지 보전 배경

- Digitalization and Technical trend • 생산성 및 제조 경쟁력 향상 목표 

- 고가의 스마트 설비도입 검토 • 유지 보수 비용 증가 

- OEE (Overall Equipment Effectiveness) 향상위한 

- 예지 보전 (Pdm, Predictive Maintenance)이 관심

  <br>
  
  

#### 예지 보전 문헌

Model-based algorithm : Kalman filter, Particle filter, Observer-based method, Control chart 등의 방법론을 통해 설비의 고장을 진단 및 예지 

반도체 웨이퍼 반송로봇(Wafer Transfer Robot, WTR) 고장을 예측한 연구 : 로봇 관절 모터의 펄스 형태의 신호 데이터 와 토크 데이터 활용 

정상상태의 대표파형을 선정 후, UCL(Upper Control Limit) 과 LCL(Lower Control Limit)를 활용하여 고장 예측.  (단, 대표파형을 다른 모델의 로봇에는 적용할 수가 없기에 범용성이 떨어지는 한계)

<br>



#### 예지 보전 정의 및 사례 리뷰

물류설비 AS/RS 의 Stacker crane 의 고장 진단 연구에서도 UCL, LCL 을 통한 고장을 예측하였다. 설비의 진동, 음향, 온도, 초음파 데이터를 활용하였으며, 예지보전을 위해서는 열화 파라메터의 정기적 또는 자동 측정이 전제조건임을 제시하였다

리니어 모터의 고장 진단 연구에서는 리니어 모터 고정자의 저항값 변화 데이터로 Extended Kalman filter 를 사용하였다. 하지만, 고장 진단만을 실시 하였으며, 선형시스템에만 활용할 수 있다는 한계

전체적으로 Kalman filter 를 사용한 예지, 진단 연구는 누적 샘플링 에러는 없었으나, 선형시스템과 가우시안 노이즈에만 적용이 가능한 한계가 있었으며, Particle filter 는 비선형 시스템과 비가우시안 노이즈에도 적 용 가능하였으나, 파티클 빈곤현상에 따른 누적 샘플링 에러발생과 많은 계 산 시간이 소요된다는 한계점

Fuzzy logic, Neural network, Support Vector Machine (SVM), Pattern  recognition, Gaussian process regression의 방법론 통한 설비의 고장 진 단 예지하였다

모터 펌프의 고장진단을 Data-driven approach 로 접근한 연구에서는 모터의 전류와 진동 데이터로 Chaos 기법을 사용하여 고장을 예측하였다 (충분한 데이터를 확보하지 못해 한계가 있었으며, 충분한 데이터를 통한 인공지능 기법의 고장예측 기법을 향후 연구 과제로 선정)

설비의 제어 특성에 따른 에너지 소비 패턴을 분석한 연구에서는 설비에서 소모되는 소비전력과 전류 데이터를 활용하여 Data-driven 의 패턴인식 방법론과 Neural network 로 설비의 고장 진단

<br>



#### 예지 보전 Data-driven approach

Data-driven approach 를 선택한 배경에는 Model-based algorithm  의 경우, Model 을 만들고 분석하는 시간이 오래 걸리며, 설비의 운행 사이클이 변하기 때문에 Model 을 만들기 어려움

결과적으로 Neural network 의 경우 데이터가 충분하지 않았을 때 정상을 이상으로 감지하는 경우가 있었고, 규칙기반의 학습 데이터 를 사용했을 때 성능이 좋음을 확인하였다. 단, 다양한 데이터가 확보된 경우에는 Neural network 의 정확도가 더 높아짐

Fuzzy Logic 과 Pattern Recognition 을 이용하여 설비의 열화 상 태를 진단한 연구 : 적외선 열화상 카메라로 측정한 설비의 온도와 온도 변화량, 전류 패턴을 사용 -> 기존 Model-based algorithm 을 활용한 열화상태 진단의 경우, 단순히 열화인지 아닌지를 구분하는 예측 시스템이었으며, 모델에 의존도가 높고, 트렌드 분석이 불가 한 단점이 있었으나 Data-driven approach 를 통해 기존 방법보다 우수함을 확인

유도전동기의 고장을 진단한 연구 : 전류값을 PCA 와 LDA 를 이용 특징벡터를 산출 후 검증 데이터를 이용하 여 각각의 매칭값을 산출하는 방법으로 고장 진단 실험에 노이즈가 존재한 경우에는 PCA 가 우수한 성능을 보였으며, 노이즈가 없는 경우는 LDA 가 우수함을 확인하였다

상황에 따라 Data-driven approach 의 방법론을 서로 융합하여 사용하는 것이 효과적. 유도전동기의 고장을 진단한 다른 연구에서는 전류 데이 터를 활용하여 다양한 실험 실시

특징 추출에 PCA 기법의 진단과 Kernal PCA 와 LDA 기법을 융합한 진단을 비교 실험, Kernal PCA 와 LDA  를 융합한 실험이 정확도가 높았으며, 고장 인식 결과의 분류 방법에는 Fuzzy Cmeans 보다 RBF Network(Radial  Basis Function Network)를 사용한 것이 인식결과 상승

복수의 데이터를 활용하여 유도전동기의 고장을 진단한 다른 연구 : Decision tree 기법에 전류 데이터와 진동데 이터를 함께 사용, 비교 실험을 통해 전류 데이터만 활용 할 때 보다 진동 데이터까지 함께 활용할 때 고장 진단 정확도가 높음을 확인. 이는 하나의 부품의 고장을 진단할 때 사용되는 데이터의 종류가 많으면 정확 도가 높아짐 의미

<br>

모델 학습 및 검증하기.ipynb

<br>

프로그램 전달하기_after

<br>

colab steel폴더 확인

