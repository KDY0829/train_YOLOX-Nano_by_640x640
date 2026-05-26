# GrabIT YOLOX-Nano Model Training

> GrabIT Android 앱의 온디바이스 상품 인식을 위한 YOLOX-Nano 기반 학습 및 TFLite 변환 실험

## ✨ Highlights

| 구분 | 내용 |
|---|---|
| 목적 | 모바일 환경에서 동작 가능한 경량 객체 탐지 모델 학습 |
| 모델 | YOLOX-Nano |
| 입력 | 640x640 상품 이미지 |
| 결과 | TensorFlow Lite Float16 변환 후 GrabIT Android 앱 적용 |

---

## 1. 프로젝트 개요

이 레포지토리는 GrabIT Android 앱에 탑재될 상품 인식(Object Detection) 모델의 학습과 변환 과정을 정리한 모델링 레포입니다.

모바일 온디바이스 환경에서는 추론 속도와 모델 크기가 중요하기 때문에, 경량 객체 탐지 모델인 YOLOX-Nano를 사용했습니다. 학습된 PyTorch 모델은 Android 배포를 위해 TensorFlow Lite Float16 형식으로 변환했습니다.

---

## 2. 전체 흐름

```text
상품 이미지 데이터셋
  → YOLOX 포맷 변환
  → YOLOX-Nano 학습
  → best checkpoint 선정
  → TensorFlow Lite Float16 변환
  → GrabIT Android assets 적용
```

---

## 3. 주요 파일

| 파일 | 설명 |
|---|---|
| `train_YOLOX-NANO.ipynb` | 커스텀 데이터셋을 YOLOX 포맷에 맞춰 학습하는 메인 파이프라인 |
| `train_YOLOX_NANO_background.ipynb` | 배경 데이터와 증강 기법을 적용해 강건성을 높이기 위한 실험 |
| `convert_YOLOX_to_TFLite.ipynb` | PyTorch `.pth` 모델을 TensorFlow Lite Float16 형식으로 변환 |
| `best_model_yolox_640.pth` | 가장 높은 성능을 기록한 PyTorch 모델 체크포인트 |
| `yolox_nano_49cls_float16.tflite` | Android 앱 배포용 최종 모델 |

---

## 4. My Role

- GrabIT 서비스에 필요한 상품 인식 모델 학습 방향 설계
- YOLOX-Nano 기반 커스텀 상품 데이터셋 학습
- 모바일 환경 적용을 위한 경량 모델 선택
- PyTorch checkpoint를 TensorFlow Lite Float16 모델로 변환
- Android 앱에 적용 가능한 모델 파일 형태로 정리

---

## 5. Tech Stack

| 영역 | 기술 |
|---|---|
| Language | Python |
| Model | YOLOX-Nano |
| Framework | PyTorch, TensorFlow Lite |
| Runtime Target | Android On-Device |
| Environment | Google Colab, Jupyter Notebook |
| Task | Object Detection |

---

## 6. How to Run

권장 환경은 Google Colab 또는 GPU가 탑재된 로컬 Jupyter 환경입니다.

```text
1. train_YOLOX-NANO.ipynb 실행
2. 학습 완료 후 best_model_yolox_640.pth 저장
3. convert_YOLOX_to_TFLite.ipynb 실행
4. yolox_nano_49cls_float16.tflite 생성
5. GrabIT Android 앱 assets에 모델 적용
```

---

## 7. Related Repository

- [KDY0829/GrabIT-Android](https://github.com/KDY0829/GrabIT-Android)
