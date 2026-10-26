# Smart Agriculture Labeling — Final QA Report

Generated: 2026-10-26

## 1. Project Overview

- Model: MobileSAM
- Task: AI-Assisted Plant Foreground Segmentation
- Pilot Images: 5
- Annotation Format: Polygon JSON
- Evaluation Status: Provisional
- Final Release Status: HOLD

## 2. Baseline Performance

| Metric | Mean |
|---|---:|
| IoU | 0.7054 |
| Dice | 0.8089 |
| Precision | 0.9457 |
| Recall | 0.7368 |

위 지표는 5개 이미지의 단순 평균이며,
Reference Label ID 매핑이 검증되지 않은 잠정 결과이다.

## 3. Image-Level Performance

| Image | IoU | Dice | Precision | Recall | QA Status |
|---|---:|---:|---:|---:|---|
| ave-0035-0001.jpg | 0.9046 | 0.9499 | 0.9538 | 0.9461 | Pass Candidate |
| ave-0035-0002.jpg | 0.8526 | 0.9204 | 0.9366 | 0.9048 | Pass Candidate |
| ave-0035-0003.jpg | 0.7232 | 0.8394 | 0.9654 | 0.7424 | Review |
| ave-0007-0007.jpg | 0.7087 | 0.8295 | 0.9360 | 0.7448 | Review |
| ave-0032-0006.jpg | 0.3379 | 0.5051 | 0.9365 | 0.3458 | Correction Required |

## 4. Annotation Integrity

- Images: 5
- Original Polygons: 7
- Original Vertices: 641
- Integrity PASS: 5/5
- Polygon Conversion PASS: 5/5
- Mean Conversion IoU: 0.9937

Conversion IoU는 Polygon이 원본 예측 마스크를
얼마나 충실하게 재현하는지 측정한다.
실제 Segmentation 정확도와는 구분된다.

## 5. Human-Guided Correction

| Image | Baseline IoU | Corrected IoU | Delta | QA Status |
|---|---:|---:|---:|---|
| ave-0032-0006.jpg | 0.3379 | 0.5461 | +0.2082 | pending_human_review |

수정은 Human-Guided Prompt Selection 방식으로 수행되었다.
수정 결과는 별도 후보 Annotation으로 저장되었으며,
최종 Human QA 승인을 받지 않았다.

## 6. Quality Gate Assessment

| Gate | Result |
|---|---|
| G1 File Integrity | 5/5 PASS |
| G2 Polygon Conversion | 5/5 PASS |
| G3 Provisional IoU >= 0.80 | 2/5 |
| G4 Label Mapping | UNVERIFIED |
| G5 Human Approval | PENDING |
| Final Release | 0/5 APPROVED |

IoU 0.80은 본 파일럿의 내부 검토 기준이다.

## 7. Limitations

1. Reference Label ID와 255의 의미가 최종 검증되지 않았다.
2. 평가 지표는 잠정 Reference Mask를 기준으로 산출되었다.
3. Point Prompt는 사람이 선택했으므로 완전 자동 라벨링이 아니다.
4. Polygon 구조 검증은 실제 경계 정확성을 보장하지 않는다.
5. Polygon Self-intersection 및 모든 세부 객체의 수동 검수는 미완료이다.
6. Experiment E는 최종 승인된 Annotation이 아닌 수정 후보이다.
7. 파일럿 이미지 5개만으로 일반화 성능을 판단할 수 없다.

## 8. Final Conclusion

MobileSAM 기반 AI 보조 라벨링 파이프라인을 구축하고,
다중 이미지 평가, Polygon 변환, 오류 분석,
Human-Guided Correction 및 Quality Gate 검증을 수행하였다.

기술적 산출물의 구조적 무결성은 검증되었으나,
의미적 라벨 검증과 최종 Human QA가 완료되지 않아
Annotation Release는 HOLD 상태로 유지한다.
