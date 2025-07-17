# 1YOLO v8버전 영상 detect 하기
 이번 시간엔 YOLO v8 버전을 이용한 찍었던 영상의 차량과 사람을 탐지하는 코드를 짜보았다.

# 2 YOLO v11 버전 개요

<img width="1163" height="487" alt="화면 캡처 2025-07-17 112046" src="https://github.com/user-attachments/assets/4f59222a-f522-4027-a0f6-af8abc0706ed" />

# YOLO V11 버전의 주요기능
1. 향상된 특징 추출: YOLO11 향상된 백본 및 넥 아키텍처를 채택하여 더욱 정밀한 물체 감지 및 복잡한 작업 수행을 위해 특징 추출 기능을 향상시켰습니다.
2. 효율성과 속도에 최적화: YOLO11 은 정교한 아키텍처 설계와 최적화된 교육 파이프라인을 도입하여 처리 속도를 높이고 정확도와 성능 간의 최적의 균형을 유지합니다.\
3. 더 적은 파라미터로 더 높은 정확도: 모델 설계의 발전으로 YOLO11m은 COCO 데이터 세트에서 더 높은 평균 정밀도 (mAP)를 달성하는 동시에 YOLOv8m 보다 22% 적은 수의 매개변수를 사용하여 정확도 저하 없이 계산 효율을 높였습니다.
4. 다양한 환경에서의 적응성: YOLO11 은 엣지 디바이스, 클라우드 플랫폼, NVIDIA GPU를 지원하는 시스템 등 다양한 환경에 원활하게 배포할 수 있어 유연성을 극대화합니다.
5. 광범위한 지원 작업: 물체 감지, 인스턴스 분할, 이미지 분류, 포즈 추정, 방향성 물체 감지(OBB) 등 다양한 컴퓨터 비전 과제에 대응할 수 있도록 설계되었습니다( YOLO11 ).

# 3 YOLOv8 vs YOLOv11 비교

YOLO(You Only Look Once) 시리즈는 객체 탐지 분야에서 가장 널리 사용되는 모델 중 하나입니다. 본 문서에서는 **YOLOv8**과 **YOLOv11**의 주요 성능과 구조적 차이를 비교합니다.

---

## 📊 성능 비교

| 항목               | YOLOv8                    | YOLOv11                                 |
|--------------------|---------------------------|----------------------------------------|
| **정확도 (mAP@0.5)** | Nano: 37.3% ~ X‑large: 53.9% | Nano: 39.5% ~ X‑large: 54.7%              |
| **파라미터 수**     | Medium: 약 78.9M           | Medium: 약 68.0M (**약 14% 감소**)         |
| **CPU 추론 속도**   | Medium: 약 234.7ms (ONNX) | Medium: 약 183.2ms (**더 빠름**)           |
| **소형 객체 탐지**  | 양호                        | **우수 (YOLOv8 대비 향상됨)**            |
| **지원 태스크**     | Detection, Segmentation, Pose 등 | Detection, Segmentation, Pose, OBB 등 |
| **아키텍처 구성**   | 기존 C3, SPPF 구조 등       | **C3k2, SPPF, C2PSA 등 신규 구조 도입**    |

---

## 🧠 주요 특징 비교

### YOLOv8
- Ultralytics에서 개발
- Pythonic API 제공
- Segmentation, Pose Estimation 등 다양한 태스크 지원
- 널리 사용되는 안정적인 버전

### YOLOv11
- **경량화 + 정확도 개선**
- **소형 객체 탐지 강화**
- ONNX 기반 배포 시 더 빠른 처리 속도
- 새로운 아키텍처 블록(C3k2, C2f, C2PSA 등)으로 성능 향상
- 다양한 실전 데이터셋에서 우수한 성능 (과일, 드론 탐지 등)

---

## 📦 실전 벤치마크

- COCO, DOTA-v1, 과수원 이미지셋 등에서 YOLOv11이 YOLOv8보다 높은 정확도와 속도를 기록
- 특히 소형 객체 비중이 높은 환경에서 YOLOv11이 확실한 우위를 보임

---

## 📚 참고 링크

- [Ultralytics YOLOv8 Docs](https://docs.ultralytics.com)
- [YOLOv11 공식 소개 (Ultralytics)](https://docs.ultralytics.com/models/yolo11/)
- [YOLOv8 vs YOLOv11 비교](https://docs.ultralytics.com/compare/yolov8-vs-yolo11/)
- [YOLOv11 논문 (arXiv)](https://arxiv.org/abs/2407.12040)

---

## ✅ 결론

YOLOv11은 YOLOv8의 후속이자 **더 정확하고 효율적인 객체 탐지 모델**입니다. 기존 YOLOv8 기반 프로젝트를 운영 중이라면 YOLOv11은 충분히 고려할 만한 **업그레이드 옵션**입니다.
