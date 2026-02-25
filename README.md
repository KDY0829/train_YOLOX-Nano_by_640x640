# GrabIT YOLOX-Nano Model Training

GrabIT 모바일 앱에 탑재될 상품 인식(Object Detection) 모델의 학습 및 변환 코드를 포함하는 디렉토리입니다. 모바일 환경의 제약을 고려하여 가볍고 빠른 YOLOX-Nano 모델을 채택했습니다.

## 📑 주요 파일 설명
* **`train_YOLOX-NANO.ipynb`**: 커스텀 데이터셋(49개 클래스)을 YOLOX 포맷에 맞추어 학습시키는 메인 파이프라인입니다.
* **`train_YOLOX_NANO_background.ipynb`**: 배경 데이터나 추가 증강 기법을 적용하여 모델의 강건성(Robustness)을 높이기 위한 학습 코드입니다.
* **`convert_YOLOX_to_TFLite.ipynb`**: 학습 완료된 PyTorch 모델(`.pth`)을 안드로이드 배포를 위해 TensorFlow Lite (`.tflite`) Float16 형식으로 변환하는 코드입니다.
* **`best_model_yolox_640.pth`**: 가장 높은 성능을 기록한 PyTorch 모델 체크포인트입니다.
* **`yolox_nano_49cls_float16.tflite`**: 최종적으로 안드로이드 앱의 `assets` 폴더에 들어가는 모바일 배포용 모델입니다.

## 🚀 실행 방법
* 권장 환경: **Google Colab (Pro 권장)** 또는 GPU가 탑재된 로컬 Jupyter 환경.
* 각 주피터 노트북(`.ipynb`) 파일을 열어 셀을 순차적으로 실행하여 데이터셋 준비, 모델 학습, TFLite 변환을 수행할 수 있습니다.
