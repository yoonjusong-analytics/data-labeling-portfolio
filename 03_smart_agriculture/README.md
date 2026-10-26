
# Smart Agriculture AI-Assisted Data Labeling

**MobileSAM 기반 스마트팜 식물 이미지 라벨링 및 Human-in-the-Loop 품질 검증 프로젝트**

## 01. Project Overview (프로젝트 개요)

### 1.1 Background (프로젝트 배경)

스마트팜(Smart Agriculture)은 컴퓨터 비전(Computer Vision)과 인공지능(AI)을 활용하여 작물의 생육 상태를 관찰하고, 식물 영역을 인식하며, 농업 환경의 자동화 수준을 높이는 분야이다.

이러한 AI 모델을 개발하기 위해서는 식물의 위치와 형태를 정확하게 표현하는 고품질 이미지 어노테이션(Image Annotation)이 필요하다.

그러나 수작업 기반의 이미지 라벨링은 많은 시간과 인력이 필요하며, 복잡한 식물 경계와 겹침 현상으로 인해 라벨링 품질의 일관성을 유지하기 어렵다.

본 프로젝트는 이러한 문제를 해결하기 위한 접근 방식으로 MobileSAM(Mobile Segment Anything Model)을 활용한 AI-Assisted Labeling(인공지능 보조 라벨링) 워크플로를 구축하였다.

모델이 생성한 Segmentation Mask(분할 마스크)를 Polygon Annotation(다각형 어노테이션)으로 변환하고, 정량적 품질 평가와 Human-Guided Correction(사람이 개입하는 수정 실험)을 수행하여 데이터 라벨링의 효율성과 품질 관리 가능성을 검토하였다.

### 1.2 Project Scope (프로젝트 범위)

본 프로젝트는 농업 이미지 데이터셋을 활용한 소규모 Pilot Study(파일럿 실험)이다.

주요 작업 범위는 다음과 같다.

- Dataset Understanding(데이터 이해) 및 이미지·라벨 구조 검증
- MobileSAM 기반 식물 전경 영역 분할
- Point Prompt(점 프롬프트)를 이용한 Segmentation Mask 생성
- Mask-to-Polygon Conversion(마스크의 다각형 변환)
- IoU, Dice, Precision, Recall 기반 잠정 품질 평가
- 오류 사례 분석 및 Human-Guided Prompt Correction
- Annotation Integrity Validation(어노테이션 무결성 검증)
- Quality Gate Assessment(품질 승인 기준 평가) 및 최종 QA 보고서 작성

본 프로젝트의 라벨링은 사람이 프롬프트를 지정하는 AI 보조 방식이며, 완전 자동 라벨링 시스템은 아니다.

### 1.3 Key Results (핵심 성과)

| 항목 | 결과 |
|---|---|
| Pilot Images | 5개 |
| Model | MobileSAM |
| Mean Baseline IoU | 0.7054 |
| Mean Dice | 0.8089 |
| Mean Precision | 0.9457 |
| Mean Recall | 0.7368 |
| Original Polygon Annotations | 7개 |
| Total Polygon Vertices | 641개 |
| Mean Polygon Conversion IoU | 0.9937 |
| Annotation Integrity Validation | 5/5 PASS |
| Human-Guided Correction | IoU 0.3379 → 0.5461 |
| Final Annotation Release | HOLD |

**평가 결과 해석 시 유의사항**

- Segmentation 성능은 Reference Label ID의 의미가 완전히 검증되지 않은 상태에서 계산한 잠정 결과이다.
- Polygon Conversion IoU는 원본 예측 마스크와 변환된 Polygon의 일치도를 나타내며, 실제 라벨 정확도를 의미하지 않는다.
- Human-Guided Correction은 수정 후보를 생성한 실험이며, 최종 Human QA 승인을 의미하지 않는다.
- 본 파일럿의 목적은 모델의 일반화 성능 입증이 아니라 AI 보조 라벨링과 품질 검증 워크플로의 구현 및 평가에 있다.

### 1.4 Project Focus (프로젝트 핵심 관점)

본 프로젝트는 모델 성능 자체보다 **AI-Assisted Labeling Workflow(인공지능 보조 라벨링 프로세스)와 Quality Assurance(품질 보증) 체계**에 중점을 두었다.

특히 모델 예측 결과를 그대로 최종 라벨로 사용하는 대신, 품질 지표를 통해 오류를 식별하고, 수정 실험을 수행하며, 구조적 무결성과 최종 승인 상태를 별도로 관리하는 과정을 구현하였다.

이를 통해 데이터 라벨링 실무에서 요구되는 Annotation Quality Management(어노테이션 품질 관리), Error Analysis(오류 분석), Human-in-the-Loop(사람이 검토 과정에 참여하는 방식)에 대한 이해와 적용 역량을 보여주고자 하였다.