# TensorRT_EX
## 작업 환경
- window10
- Cuda 11.1
- TensorRT 8.0.1.6
- Cudnn 8.2.0


## custom plugin example 완료 
- 전처리 기능을 수행하는 레이어(NHWC->NCHW, BGR->RGB, [0, 255]->[0, 1] (Normalize))
- plugin_ex1.cpp (plugin 예제 코드)
- preprocess.hpp (plugin 코드)
- preprocess.cu (전처리 기능 cuda kernel 함수)
- Validation/Validation.py (계산 결과 검증)


##  TensorRT 기본 예제 (진행중)
- 사용하기 편한 구조 (엔진 파일 유무에 따라 재생성 또는 엔진 파일 로드 작업 수행) (완료)
- 좀 더 쉽고 직관적 코드 구조
- TRT 모델용 웨이트 파일의 웨이트 구조를 딕셔너리에서 리스트로 변경 (파일 용량 50% 감소)


## 일반적인 TensorRT 모델 만드는 작업 순서 
0. 학습 프레임 워크에서 학습 완료된 모델을 준비(trt에서 사용 할 웨이트 파일 생성).     
1. TensorRT API를 사용하여 학습된 모델 구조와 동일하게 모델을 구현(코딩).     
2. 기존 학습 모델에서 웨이트를 추출하여 준비된 TensorRT 모델의 각각 레이어에 알맞게 웨이트를 전달.     
3. 완성된 코드를 빌드하고 실행.     
4. TensorRT 모델이 빌드되고 난 뒤 생성된 모델 스트림 Serialize 하여 엔진 파일로 생성.     
5. 이 후 작업에서 엔진파일만 로드하여 추론 수행(만약 모델 파리미터나 레이어 수정시 이전(4) 작업 재실행).     



## reference   
tensorrtx : https://github.com/wang-xinyu/tensorrtx

