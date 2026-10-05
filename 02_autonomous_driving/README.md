# Autonomous Driving Data Labeling Portfolio


## 1. Project Overview(프로젝트 개요)

본 프로젝트는 **nuImages Dataset(데이터셋)**을 활용하여 자율주행 환경의 객체 특성을 이해하고, 실제 라벨링 작업부터 품질 검증까지 수행한 **Autonomous Driving Data Labeling(자율주행 데이터 라벨링) 포트폴리오 프로젝트**입니다.

먼저 Data Understanding(데이터 이해)을 통해 차량, 보행자, 교통 시설물 등 주요 객체의 분포와 **Occlusion(가림), Truncation(잘림), Small/Distant Object(소형·원거리 객체)** 등 라벨링 난이도에 영향을 주는 요소를 분석하였습니다.

이후 Annotation Guideline(라벨링 가이드라인)을 수립하고 **CVAT**을 활용하여 8장의 파일럿 이미지에 대해 직접 **2D Bounding Box(2D 바운딩 박스)** 라벨링을 수행하였습니다. 파일럿 라벨링에서는 총 **73개의 객체**를 라벨링하고 객체별 Class(클래스)와 주요 Attribute(속성)를 함께 기록하였습니다.

라벨링 완료 후에는 Annotation QA(라벨링 품질 검증)를 통해 데이터의 누락, 중복, 좌표 및 속성값의 일관성을 점검하였으며, Repeat Annotation(반복 라벨링)과 **IoU(Intersection over Union)** 분석을 활용하여 Bounding Box(바운딩 박스)의 재현성과 일관성을 정량적으로 평가하였습니다.

마지막으로 Object Matching Error Analysis(객체 매칭 오류 분석)를 수행하여 라벨링 과정에서 발생할 수 있는 오류 사례와 난이도 요인을 분석하고, 이를 바탕으로 자율주행 데이터 라벨링의 품질을 개선하기 위한 주요 시사점을 도출하였습니다.


## 2. Project Objectives(프로젝트 목표)

본 프로젝트의 목표는 자율주행 Dataset(데이터셋)의 특성을 이해하고, 실제 라벨링 환경에서 요구되는 **가이드라인 수립 → 라벨링 수행 → 품질 검증 → 오류 분석**의 전체 Workflow(워크플로우)를 경험하고 검증하는 것입니다.

주요 목표는 다음과 같습니다.

1. **Dataset Understanding(데이터셋 이해)**  
   nuImages Dataset(데이터셋)의 구조와 객체 분포를 분석하고, 자율주행 이미지에서 라벨링 난이도에 영향을 주는 주요 특성을 파악합니다.

2. **Annotation Guideline(라벨링 가이드라인) 수립**  
   Bounding Box(바운딩 박스), Occlusion(가림), Truncation(잘림), Small/Distant Object(소형·원거리 객체), Ambiguity(모호성) 등에 대한 일관된 라벨링 기준을 정의합니다.

3. **CVAT 기반 Pilot Annotation(파일럿 라벨링) 수행**  
   실제 라벨링 도구인 CVAT을 활용하여 객체별 Bounding Box(바운딩 박스), Class(클래스), Attribute(속성)를 직접 라벨링하고 가이드라인을 실제 데이터에 적용합니다.

4. **Annotation QA(라벨링 품질 검증)**  
   라벨링 결과의 결측값, 중복, Bounding Box(바운딩 박스) 좌표 및 Attribute(속성) 값 등을 점검하여 데이터의 완전성과 일관성을 검증합니다.

5. **Repeat Annotation & IoU Analysis(반복 라벨링 및 IoU 분석)**  
   동일 객체에 대한 반복 라벨링 결과를 비교하고 IoU(Intersection over Union)를 활용하여 Bounding Box(바운딩 박스)의 재현성과 일관성을 정량적으로 평가합니다.

6. **Error Analysis(오류 분석)**  
   Object Matching Error(객체 매칭 오류) 사례를 분석하여 Small/Distant Object(소형·원거리 객체), Occlusion(가림), Ambiguity(모호성) 등 라벨링 난이도와 오류 발생 요인의 관계를 파악합니다.


## 3. Dataset(데이터셋)

### 3.1 nuImages Dataset(데이터셋)

본 프로젝트에서는 자율주행 환경의 이미지와 객체 정보를 제공하는 **nuImages Dataset(데이터셋)**을 활용하였습니다.

nuImages는 실제 도로 환경에서 수집된 이미지 기반 Dataset(데이터셋)으로, 차량, 보행자, 교통 시설물 등 자율주행 인식에 필요한 다양한 객체 정보를 포함하고 있습니다. 이를 통해 실제 도로 환경에서 발생하는 **Occlusion(가림), Truncation(잘림), Small/Distant Object(소형·원거리 객체)** 등의 라벨링 난이도를 분석할 수 있습니다.

### 3.2 Dataset Selection(데이터셋 선정 이유)

nuImages Dataset(데이터셋)은 다음과 같은 이유로 본 프로젝트에 선정하였습니다.

- 실제 도로 환경에서 수집된 이미지 데이터를 활용할 수 있음
- 차량, 보행자, 교통 시설물 등 다양한 Object Class(객체 클래스)를 포함함
- Bounding Box(바운딩 박스) 기반 객체 라벨링을 분석하고 실습하기에 적합함
- 객체 크기, 가림, 잘림 등 실제 라벨링 과정에서 발생하는 다양한 난이도 사례를 확인할 수 있음
- CVAT을 활용한 Pilot Annotation(파일럿 라벨링)과 Annotation QA(라벨링 품질 검증) 과정으로 확장하기에 적합함

### 3.3 Project Dataset Scope(프로젝트 데이터 범위)

본 프로젝트에서는 전체 Dataset(데이터셋)을 직접 라벨링하는 대신, Data Understanding(데이터 이해)을 통해 전체적인 데이터 특성을 분석한 후 **8장의 이미지를 Pilot Dataset(파일럿 데이터셋)**으로 선정하여 집중적인 라벨링과 품질 검증을 수행하였습니다.

| 항목 | 내용 |
|---|---|
| Dataset(데이터셋) | nuImages |
| Domain(도메인) | Autonomous Driving(자율주행) |
| Data Type(데이터 유형) | Road Scene Image(도로 환경 이미지) |
| Annotation Type(라벨링 유형) | 2D Bounding Box(2D 바운딩 박스) |
| Pilot Images(파일럿 이미지) | 8 |
| Total Annotations(전체 라벨) | 73 |
| Annotation Tool(라벨링 도구) | CVAT |

파일럿 데이터는 단순 라벨링 실습이 아니라 **라벨링 가이드라인 적용, Attribute(속성) 기록, Annotation QA(라벨링 품질 검증), Repeat Annotation(반복 라벨링), IoU 분석 및 Error Analysis(오류 분석)**까지 연결할 수 있도록 활용하였습니다.


## 4. Project Workflow(프로젝트 진행 과정)

본 프로젝트는 자율주행 Dataset(데이터셋)에 대한 이해부터 실제 라벨링, 품질 검증 및 오류 분석까지 단계적으로 진행하였습니다.

```text
Dataset Selection(데이터셋 선정)
        ↓
Data Understanding(데이터 이해)
        ↓
Annotation Guideline(라벨링 가이드라인)
        ↓
Pilot Annotation(파일럿 라벨링)
        ↓
CVAT Labeling(CVAT 라벨링)
        ↓
Annotation QA(라벨링 품질 검증)
        ↓
Repeat Annotation(반복 라벨링)
        ↓
IoU Analysis(IoU 분석)
        ↓
Object Matching Error Analysis(객체 매칭 오류 분석)
        ↓
Final Evaluation(최종 평가)
```

### 4.1 Data Understanding(데이터 이해)

nuImages Dataset(데이터셋)의 구조와 주요 Object Class(객체 클래스)를 확인하고, Class Distribution(클래스 분포), 객체 크기, Occlusion(가림), Truncation(잘림) 등 라벨링 난이도에 영향을 주는 특성을 분석하였습니다.

### 4.2 Annotation Guideline(라벨링 가이드라인)

Data Understanding(데이터 이해) 결과를 기반으로 Bounding Box(바운딩 박스) 작성 기준과 주요 Attribute(속성)의 판단 기준을 정의하였습니다. 특히 Occlusion(가림), Truncation(잘림), Small/Distant(소형·원거리), Ambiguity(모호성) 등의 기준을 설정하여 라벨링 일관성을 확보하고자 하였습니다.

### 4.3 Pilot Annotation & CVAT Labeling(파일럿 및 CVAT 라벨링)

선정된 8장의 Pilot Image(파일럿 이미지)를 대상으로 CVAT에서 직접 Bounding Box(바운딩 박스)를 생성하고 Class(클래스)와 Attribute(속성)를 기록하였습니다. 총 73개의 객체를 라벨링하였습니다.

### 4.4 Annotation QA(라벨링 품질 검증)

CVAT에서 Export(내보내기)한 라벨링 데이터를 기반으로 Missing Value(결측값), Duplicate Object ID(중복 객체 ID), Bounding Box Coordinate(바운딩 박스 좌표), Class 및 Attribute Value(속성값) 등을 검증하였습니다.

### 4.5 Repeat Annotation & IoU Analysis(반복 라벨링 및 IoU 분석)

일부 객체를 다시 라벨링한 후 Reference Annotation(기준 라벨링)과 Repeat Annotation(반복 라벨링)의 Bounding Box(바운딩 박스)를 비교하였습니다. IoU(Intersection over Union)를 활용하여 반복 라벨링의 위치 일관성과 재현성을 정량적으로 평가하였습니다.

### 4.6 Object Matching Error Analysis(객체 매칭 오류 분석)

Reference Annotation(기준 라벨링)과 Repeat Annotation(반복 라벨링) 간 Object Matching(객체 매칭)이 정상적으로 이루어지지 않은 사례를 별도로 분석하였습니다. 오류 객체의 Small/Distant(소형·원거리), Occlusion(가림), Truncation(잘림), Ambiguity(모호성) 특성을 비교하여 라벨링 난이도와 오류 발생 요인을 확인하였습니다.

### 4.7 Final Evaluation(최종 평가)

라벨링 결과와 QA 및 Error Analysis(오류 분석) 결과를 종합하여 프로젝트의 주요 결과와 한계를 정리하고, 향후 라벨링 품질 개선을 위한 방향을 도출하였습니다.


## 5. Data Understanding(데이터 이해)

본격적인 라벨링에 앞서 nuImages Dataset(데이터셋)의 구조와 객체 특성을 파악하기 위해 Data Understanding(데이터 이해)을 수행하였습니다.

단순한 데이터 분포 확인을 넘어, 실제 자율주행 이미지에서 **어떤 객체가 라벨링하기 어렵고 어떤 조건에서 판단의 일관성이 낮아질 수 있는지**를 파악하는 데 중점을 두었습니다.

### 5.1 Dataset Structure(데이터셋 구조)

nuImages Dataset(데이터셋)의 주요 데이터 구조와 이미지 및 객체 라벨 정보를 확인하고, 이후 분석과 Pilot Annotation(파일럿 라벨링)에 필요한 정보를 추출하였습니다.

주요 분석 대상은 다음과 같습니다.

- Object Class(객체 클래스)
- Bounding Box(바운딩 박스) 좌표
- Object Size(객체 크기)
- Occlusion(가림)
- Truncation(잘림)
- 이미지별 Object Distribution(객체 분포)

### 5.2 Class Distribution(클래스 분포)

자율주행 환경에 등장하는 Object Class(객체 클래스)의 분포를 분석하여 데이터에 어떤 객체가 주로 포함되어 있는지 확인하였습니다.

차량 관련 객체뿐만 아니라 보행자와 도로 시설물 등 다양한 객체가 존재하며, 클래스별 데이터 수와 객체 특성에 차이가 있음을 확인하였습니다.

이러한 차이는 Pilot Dataset(파일럿 데이터셋) 선정 시 특정 클래스에만 편중되지 않고 다양한 객체 유형과 난이도를 포함하도록 하는 기준으로 활용하였습니다.

### 5.3 Object Size Analysis(객체 크기 분석)

Bounding Box(바운딩 박스)의 Width(너비), Height(높이), Area(면적)를 활용하여 객체 크기 분포를 분석하였습니다.

특히 이미지에서 차지하는 영역이 작은 **Small/Distant Object(소형·원거리 객체)**는 객체의 경계를 정확하게 판단하기 어렵고, 반복 라벨링 과정에서도 Bounding Box(바운딩 박스)의 위치 차이가 상대적으로 크게 나타날 가능성이 있으므로 주요 난이도 요소로 고려하였습니다.

### 5.4 Occlusion & Truncation Analysis(가림 및 잘림 분석)

객체가 다른 객체에 의해 가려지는 Occlusion(가림)과 이미지 경계 밖으로 일부 벗어나는 Truncation(잘림)을 분석하였습니다.

두 조건은 객체의 실제 경계를 판단하기 어렵게 만들 수 있으므로 Bounding Box(바운딩 박스)의 위치와 크기 결정에 영향을 줄 수 있는 주요 라벨링 난이도 요소로 정의하였습니다.

이에 따라 이후 Annotation Guideline(라벨링 가이드라인)에서는 Occlusion과 Truncation의 정도를 구분할 수 있도록 별도의 Attribute(속성) 기준을 설정하였습니다.

### 5.5 Labeling Difficulty Factors(라벨링 난이도 요인)

Data Understanding(데이터 이해)을 통해 이후 라벨링 과정에서 중점적으로 관리해야 할 주요 난이도 요인을 다음과 같이 정의하였습니다.

| Difficulty Factor(난이도 요인) | 주요 라벨링 이슈 |
|---|---|
| Small/Distant Object(소형·원거리 객체) | 객체 경계 식별 및 클래스 판단의 어려움 |
| Occlusion(가림) | 가려진 영역으로 인한 객체 경계 판단의 어려움 |
| Truncation(잘림) | 이미지 밖으로 벗어난 객체의 Bounding Box 판단 |
| Ambiguity(모호성) | 객체 경계 또는 Class(클래스) 판단의 불확실성 |
| Dense Scene(밀집 장면) | 인접 객체 간 경계 및 개별 객체 구분의 어려움 |

### 5.6 Data Understanding Summary(데이터 이해 요약)

Data Understanding(데이터 이해)을 통해 자율주행 데이터 라벨링에서는 단순히 객체를 탐지하여 Bounding Box(바운딩 박스)를 생성하는 것뿐만 아니라, **객체 크기, 가림, 잘림, 경계의 모호성 등 다양한 조건을 일관된 기준으로 판단하는 것이 중요**하다는 점을 확인하였습니다.

이 분석 결과를 기반으로 Pilot Annotation(파일럿 라벨링)에 적용할 Annotation Guideline(라벨링 가이드라인)과 Attribute Schema(속성 체계)를 설계하였습니다.


## 6. Annotation Guidelines(라벨링 가이드라인)

Data Understanding(데이터 이해)에서 확인한 객체 특성과 난이도 요인을 기반으로 Pilot Annotation(파일럿 라벨링)에 적용할 라벨링 가이드라인을 수립하였습니다.

가이드라인의 주요 목적은 라벨러의 주관적 판단 차이를 줄이고, 동일한 객체에 대해 가능한 한 일관된 Bounding Box(바운딩 박스)와 Attribute(속성)를 적용하는 것입니다.

### 6.1 Bounding Box(바운딩 박스) 기준

Bounding Box(바운딩 박스)는 이미지에서 확인 가능한 객체의 외곽에 최대한 밀착하여 생성하는 것을 기본 원칙으로 설정하였습니다.

주요 기준은 다음과 같습니다.

- 객체의 실제 외곽에 최대한 밀착하여 Bounding Box를 생성
- 객체 주변의 불필요한 Background(배경)를 최소화
- 서로 다른 객체가 인접한 경우 각각 개별 Bounding Box로 라벨링
- 동일한 종류의 객체가 여러 개 존재하더라도 하나로 묶지 않고 개별 객체로 라벨링
- 객체 일부가 가려지거나 이미지 밖으로 벗어난 경우에도 식별 가능한 객체는 가이드라인에 따라 라벨링
- 객체 경계가 명확하지 않은 경우 Ambiguity(모호성) Attribute를 활용하여 불확실성을 기록

특히 Traffic Cone(트래픽 콘)과 같이 작고 여러 개가 연속적으로 배치된 객체도 하나의 Bounding Box로 묶지 않고 **각 객체를 개별적으로 라벨링**하였습니다.

### 6.2 Class Schema(클래스 체계)

Pilot Annotation(파일럿 라벨링)에서는 다음 Object Class(객체 클래스)를 사용하였습니다.

| Class(클래스) | 설명 |
|---|---|
| Car | 일반 승용 차량 |
| Truck | 트럭 |
| Traffic Cone | 교통 통제용 콘 |
| Pedestrian | 보행자 |
| Construction Vehicle | 건설 및 작업 차량 |
| Trailer | 트레일러 |
| Barrier | 도로 차단 및 경계 시설물 |

객체의 Class(클래스)가 명확하지 않은 경우 주변 환경과 객체 형태를 함께 확인하고, 판단의 불확실성이 존재하는 경우 Ambiguity(모호성)에 해당 정보를 기록하도록 하였습니다.

### 6.3 Occlusion(가림)

Occlusion(가림)은 객체가 다른 객체나 구조물 등에 의해 가려진 정도를 나타냅니다.

| 값 | 판단 기준 |
|---|---|
| None | 객체가 가려지지 않음 |
| Partial | 객체 일부가 가려져 있으나 주요 형태를 확인할 수 있음 |
| Heavy | 객체의 상당 부분이 가려져 있어 전체 형태 판단이 어려움 |

Occlusion은 **이미지 내부에서 다른 객체 등에 의해 보이지 않는 경우**를 기준으로 판단하였습니다.

### 6.4 Truncation(잘림)

Truncation(잘림)은 객체의 일부가 이미지 프레임 밖으로 벗어나 보이지 않는 정도를 나타냅니다.

| 값 | 판단 기준 |
|---|---|
| None | 객체 전체가 이미지 안에 존재 |
| Partial | 객체 일부가 이미지 경계 밖으로 벗어남 |
| Heavy | 객체의 상당 부분이 이미지 밖으로 벗어나 있음 |

Occlusion(가림)과 Truncation(잘림)은 서로 다른 원인으로 객체의 일부가 보이지 않는 상태이므로 **각각 독립적으로 판단**하였습니다.

### 6.5 Small/Distant(소형·원거리)

Small/Distant(소형·원거리)는 이미지에서 객체의 크기가 작거나 원거리에 위치하여 경계 또는 Class(클래스) 판단이 어려운 객체를 구분하기 위한 Attribute(속성)입니다.

| 값 | 판단 기준 |
|---|---|
| False | 객체의 형태와 경계를 비교적 명확하게 확인할 수 있음 |
| True | 객체가 작거나 멀리 있어 경계 또는 세부 형태 판단이 어려움 |

이 속성은 이후 Repeat Annotation(반복 라벨링) 및 Error Analysis(오류 분석)에서 라벨링 난이도와 객체 매칭 오류의 관계를 분석하는 데 활용하였습니다.

### 6.6 Ambiguity(모호성)

Ambiguity(모호성)는 객체의 경계 또는 Class(클래스)를 명확하게 판단하기 어려운 경우를 기록하기 위한 Attribute(속성)입니다.

| 값 | 판단 기준 |
|---|---|
| None | 객체의 Class와 경계가 명확함 |
| Boundary | 객체의 외곽 경계 판단이 모호함 |
| Class | 객체의 Class 판단이 모호함 |

이를 통해 단순히 라벨링 결과만 기록하는 것이 아니라 **라벨러가 판단 과정에서 경험한 불확실성도 데이터로 관리**하도록 설계하였습니다.

### 6.7 Attribute Schema(속성 체계)

최종적으로 Pilot Annotation(파일럿 라벨링)에 적용한 주요 Attribute Schema(속성 체계)는 다음과 같습니다.

| Attribute(속성) | Values(값) |
|---|---|
| Occlusion | None / Partial / Heavy |
| Truncation | None / Partial / Heavy |
| Small/Distant | True / False |
| Ambiguity | None / Boundary / Class |
| Notes | 필요 시 추가 판단 근거 기록 |

### 6.8 Guideline Summary(가이드라인 요약)

본 프로젝트에서는 Bounding Box(바운딩 박스)의 위치뿐만 아니라 **객체의 가림, 잘림, 크기 및 거리, 경계와 클래스의 모호성**을 함께 기록하도록 라벨링 체계를 구성하였습니다.

이를 통해 Pilot Annotation(파일럿 라벨링)의 일관성을 확보하고, 이후 Annotation QA(라벨링 품질 검증)와 Repeat Annotation(반복 라벨링), IoU 및 Error Analysis(오류 분석)에서 라벨링 난이도를 정량적으로 분석할 수 있는 기반을 마련하였습니다.


## 7. Pilot Annotation with CVAT(CVAT 파일럿 라벨링)

Data Understanding(데이터 이해)과 Annotation Guideline(라벨링 가이드라인) 수립 후, 선정된 **8장의 Pilot Image(파일럿 이미지)**를 대상으로 CVAT을 활용하여 직접 객체 라벨링을 수행하였습니다.

각 객체에 대해 2D Bounding Box(2D 바운딩 박스)를 생성하고 Class(클래스)를 지정하였으며, Occlusion(가림), Truncation(잘림), Small/Distant(소형·원거리), Ambiguity(모호성) 등의 Attribute(속성)를 함께 기록하였습니다.


### 7.1 Annotation Results(라벨링 결과)

파일럿 라벨링 결과 총 **73개의 객체**가 라벨링되었습니다.

| 항목 | 결과 |
|---|---:|
| Pilot Images(파일럿 이미지) | 8 |
| Total Annotations(전체 라벨) | 73 |
| Object Classes(객체 클래스) | 7 |
| Annotation Type(라벨링 유형) | 2D Bounding Box |
| Annotation Tool(라벨링 도구) | CVAT |

### 7.2 Class Distribution(클래스 분포)

총 73개의 객체에 대한 Class Distribution(클래스 분포)은 다음과 같습니다.

| Class(클래스) | Count(개수) | 비율 |
|---|---:|---:|
| Car | 30 | 41.1% |
| Traffic Cone | 24 | 32.9% |
| Truck | 7 | 9.6% |
| Pedestrian | 5 | 6.8% |
| Construction Vehicle | 4 | 5.5% |
| Trailer | 2 | 2.7% |
| Barrier | 1 | 1.4% |
| **Total** | **73** | **100.0%** |

Car와 Traffic Cone이 전체 객체의 약 **74%**를 차지하였으며, Truck, Pedestrian, Construction Vehicle, Trailer, Barrier 등 다양한 도로 환경 객체도 함께 포함되었습니다.

### 7.3 Attribute Distribution(속성 분포)

#### Occlusion(가림)

| 값 | Count(개수) | 비율 |
|---|---:|---:|
| None | 32 | 43.8% |
| Partial | 31 | 42.5% |
| Heavy | 10 | 13.7% |
| **Total** | **73** | **100.0%** |

전체 객체 중 **41개(56.2%)**에서 Partial 또는 Heavy Occlusion(가림)이 확인되어, 파일럿 이미지에 가림이 존재하는 객체가 상당수 포함되어 있음을 확인하였습니다.

#### Truncation(잘림)

| 값 | Count(개수) | 비율 |
|---|---:|---:|
| None | 68 | 93.2% |
| Partial | 4 | 5.5% |
| Heavy | 1 | 1.4% |
| **Total** | **73** | **100.0%** |

대부분의 객체에서는 Truncation(잘림)이 발생하지 않았으며, 이미지 경계에 위치한 일부 객체에서만 Partial 또는 Heavy 상태가 확인되었습니다.

#### Small/Distant(소형·원거리)

| 값 | Count(개수) | 비율 |
|---|---:|---:|
| True | 41 | 56.2% |
| False | 32 | 43.8% |
| **Total** | **73** | **100.0%** |

전체 객체 중 **41개(56.2%)**가 Small/Distant Object(소형·원거리 객체)로 분류되어, 객체 크기와 거리가 파일럿 라벨링에서 중요한 난이도 요소임을 확인하였습니다.

### 7.4 Pilot Annotation Observations(파일럿 라벨링 관찰 결과)

파일럿 라벨링 과정에서는 단순히 객체의 Class(클래스)를 구분하는 것보다 **객체의 경계를 일관되게 판단하고 Attribute(속성)를 동일한 기준으로 적용하는 과정**이 중요했습니다.

특히 다음과 같은 사례에서 라벨링 난이도가 높아지는 경향을 확인하였습니다.

- 원거리에 위치하여 크기가 작은 객체
- 다른 차량이나 객체에 일부 또는 상당 부분 가려진 객체
- 이미지 가장자리에 위치하여 일부가 잘린 객체
- 여러 객체가 밀집되어 서로의 경계를 구분하기 어려운 경우
- 저해상도 또는 객체 형태가 불명확하여 Class 또는 Boundary(경계) 판단이 어려운 경우

이러한 파일럿 라벨링 결과를 바탕으로 다음 단계에서 Annotation QA(라벨링 품질 검증)를 수행하여 라벨링 데이터의 완전성과 일관성을 검증하였습니다.

## 8. Annotation QA(라벨링 품질 검증)

Pilot Annotation(파일럿 라벨링) 완료 후 CVAT에서 Export(내보내기)한 데이터를 대상으로 Annotation QA(라벨링 품질 검증)를 수행하였습니다.

QA의 목적은 단순히 라벨링 개수를 확인하는 것이 아니라 **데이터의 완전성, Bounding Box(바운딩 박스)의 유효성, Class(클래스) 및 Attribute(속성)의 일관성**을 체계적으로 검증하는 것입니다.

### 8.1 QA Validation Process(QA 검증 과정)

다음 항목을 중심으로 라벨링 데이터를 검증하였습니다.

| QA 항목 | 검증 내용 |
|---|---|
| Annotation Count(라벨 수) | 전체 객체 및 이미지 수 확인 |
| Missing Value(결측값) | 필수 Column(컬럼)의 누락 여부 확인 |
| Duplicate Object ID(중복 객체 ID) | 동일 Object ID의 중복 여부 확인 |
| Data Type(데이터 유형) | 좌표 및 Attribute의 데이터 유형 확인 |
| Bounding Box Validation(바운딩 박스 검증) | 좌표값과 박스 구조의 유효성 확인 |
| Class Validation(클래스 검증) | 정의되지 않은 Class 존재 여부 확인 |
| Attribute Validation(속성 검증) | 허용된 Attribute 값 사용 여부 확인 |
| Distribution Check(분포 확인) | Class 및 Attribute 분포의 이상 여부 확인 |

### 8.2 Basic Validation(기본 검증)

최종 QA 데이터에 대한 Basic Validation(기본 검증) 결과는 다음과 같습니다.

| Validation Metric(검증 지표) | 결과 |
|---|---:|
| Total Annotations(전체 라벨) | 73 |
| Unique Images(고유 이미지) | 8 |
| Duplicate Object IDs(중복 객체 ID) | 0 |
| Missing Required Values(필수값 결측) | 0 |

전체 73개 라벨이 8장의 이미지와 정상적으로 연결되어 있었으며, 중복 Object ID와 필수 데이터 누락은 확인되지 않았습니다.

### 8.3 Bounding Box Validation(바운딩 박스 검증)

Bounding Box(바운딩 박스)의 좌표 데이터가 정상적인 객체 영역을 구성하는지 확인하였습니다.

주요 검증 기준은 다음과 같습니다.

- `x_min < x_max`
- `y_min < y_max`
- Bounding Box의 Width(너비)와 Height(높이)가 0보다 큰지 확인
- 좌표값이 올바른 Numeric Data Type(숫자형 데이터 유형)인지 확인
- 이미지와 Bounding Box 정보가 정상적으로 연결되어 있는지 확인

이를 통해 잘못된 좌표 순서나 유효하지 않은 Bounding Box가 분석 과정에 포함되는 것을 방지하였습니다.

### 8.4 Attribute Validation(속성 검증)

Occlusion(가림), Truncation(잘림), Small/Distant(소형·원거리), Ambiguity(모호성) 등의 Attribute(속성)가 사전에 정의한 값의 범위 내에서 일관되게 기록되었는지 확인하였습니다.

CVAT Export(내보내기) 데이터를 pandas로 불러오는 과정에서 일부 `None` 값이 `NaN`으로 인식되는 현상을 확인하였습니다.

이는 실제 라벨링 값의 누락과 구분할 필요가 있으므로 데이터 로딩 및 전처리 과정에서 **의미상 `None`인 값과 실제 Missing Value(결측값)를 구분하여 처리**하였습니다.

이를 통해 Attribute Distribution(속성 분포)이 실제 라벨링 결과를 정확하게 반영하도록 정리하였습니다.

### 8.5 Distribution Check(분포 검증)

Class(클래스)와 주요 Attribute(속성)의 분포를 확인하여 특정 값의 비정상적인 누락이나 예상하지 못한 값이 존재하는지 점검하였습니다.

특히 다음 항목을 확인하였습니다.

- Class별 객체 수
- Occlusion 단계별 분포
- Truncation 단계별 분포
- Small/Distant True/False 분포
- Ambiguity 유형별 분포

Distribution Check(분포 검증)는 데이터 오류 확인뿐만 아니라 이후 Repeat Annotation(반복 라벨링)과 Error Analysis(오류 분석)에서 사용할 난이도 변수를 확인하는 과정으로도 활용하였습니다.

### 8.6 QA Result(QA 결과)

Annotation QA(라벨링 품질 검증)를 통해 Pilot Dataset(파일럿 데이터셋)의 구조적 완전성과 주요 Attribute(속성)의 일관성을 확인하였습니다.

최종 데이터는 **73개의 라벨, 8개의 고유 이미지, 중복 Object ID 0건, 필수값 결측 0건**으로 정리되었습니다.

또한 QA 과정에서 단순한 오류 탐지를 넘어 **CVAT Export 데이터와 pandas의 데이터 표현 방식 차이**, Attribute 값의 의미 및 데이터 유형을 함께 검토함으로써 후속 분석에 사용할 수 있는 일관된 데이터 구조를 확보하였습니다.

이후 동일 객체를 다시 라벨링하는 Repeat Annotation(반복 라벨링)을 수행하고 IoU(Intersection over Union)를 활용하여 Bounding Box(바운딩 박스)의 재현성과 라벨링 일관성을 추가로 평가하였습니다.

## 9. Repeat Annotation & IoU Analysis(반복 라벨링 및 IoU 분석)

Annotation QA(라벨링 품질 검증) 이후 Bounding Box(바운딩 박스) 라벨링의 **재현성과 일관성**을 정량적으로 평가하기 위해 Repeat Annotation(반복 라벨링)과 IoU Analysis(IoU 분석)를 수행하였습니다.

기존 라벨링 결과를 Reference Annotation(기준 라벨링)으로 설정하고, 선정된 객체를 다시 라벨링한 Repeat Annotation(반복 라벨링) 결과와 비교하였습니다.

### 9.1 Repeat Annotation(반복 라벨링)

전체 Pilot Annotation(파일럿 라벨링) 중 서로 다른 난이도 조건을 포함하는 **16개의 객체**를 선정하여 반복 라벨링을 수행하였습니다.

분석 Sample(샘플)은 다음과 같은 Attribute(속성)를 고려하여 구성하였습니다.

- Small/Distant(소형·원거리)
- Occlusion(가림)
- Truncation(잘림)
- Ambiguity(모호성)
- Difficulty Score(난이도 점수)

이를 통해 단순히 라벨링하기 쉬운 객체만 비교하지 않고 다양한 난이도 조건에서 Bounding Box(바운딩 박스)의 일관성을 확인하고자 하였습니다.

### 9.2 IoU(Intersection over Union)

IoU(Intersection over Union)는 두 Bounding Box(바운딩 박스)가 얼마나 겹치는지를 나타내는 지표입니다.

Reference Annotation(기준 라벨링)과 Repeat Annotation(반복 라벨링)의 교집합 영역을 합집합 영역으로 나누어 계산합니다.

```text id="8kg31r"
IoU = Intersection Area(교집합 영역) / Union Area(합집합 영역)
```

IoU 값은 `0~1` 범위로 표현되며, **1에 가까울수록 두 Bounding Box가 유사한 위치와 크기로 생성되었다는 의미**입니다.

따라서 본 프로젝트에서는 IoU를 반복 라벨링의 Bounding Box 일관성을 평가하는 정량적 지표로 활용하였습니다.

### 9.3 Object Matching(객체 매칭)

IoU를 계산하기 위해 먼저 Reference Annotation(기준 라벨링)과 Repeat Annotation(반복 라벨링)에서 동일 객체를 서로 연결하는 Object Matching(객체 매칭) 과정을 수행하였습니다.

객체가 정상적으로 Matching(매칭)된 경우 두 Bounding Box 간 IoU를 계산하고, 정상적으로 매칭되지 않은 경우에는 별도의 Object Matching Error(객체 매칭 오류) 사례로 분리하였습니다.

이를 통해 **Bounding Box 위치 차이와 객체 자체의 매칭 실패를 서로 다른 품질 문제로 구분**하여 분석하였습니다.

### 9.4 Difficulty-based Analysis(난이도 기반 분석)

IoU 결과는 전체 값만 확인하는 것이 아니라 객체의 난이도 특성과 함께 비교하였습니다.

특히 다음 조건이 Bounding Box 일관성에 어떤 영향을 줄 수 있는지 확인하였습니다.

| Difficulty Factor(난이도 요인) | 분석 관점 |
|---|---|
| Small/Distant | 작은 객체에서 Bounding Box 차이가 증가하는지 확인 |
| Occlusion | 가림 정도에 따라 객체 경계 판단이 달라지는지 확인 |
| Truncation | 이미지 경계의 잘림이 Bounding Box 판단에 영향을 주는지 확인 |
| Ambiguity | 경계 또는 Class의 모호성이 반복 라벨링에 영향을 주는지 확인 |
| Difficulty Score | 복합 난이도 증가에 따른 IoU 변화 확인 |

이러한 분석을 통해 IoU를 단순한 하나의 점수로 평가하기보다 **어떤 객체 조건에서 라벨링 일관성이 낮아질 수 있는지**를 파악하는 데 활용하였습니다.

### 9.5 Object Matching Error(객체 매칭 오류)

반복 라벨링 비교 과정에서는 IoU 계산뿐만 아니라 Reference Annotation과 Repeat Annotation 간에 동일 객체가 정상적으로 연결되지 않는 Object Matching Error(객체 매칭 오류)도 확인하였습니다.

총 **6건의 Object Matching Error 사례**를 별도로 분리하여 객체별 Attribute(속성)와 난이도 특성을 추가 분석하였습니다.

이는 단순한 Bounding Box 위치 차이보다 **객체 식별 또는 매칭 단계에서 발생할 수 있는 품질 문제**를 확인하기 위한 과정입니다.

### 9.6 IoU Analysis Summary(IoU 분석 요약)

Repeat Annotation(반복 라벨링)과 IoU Analysis(IoU 분석)를 통해 라벨링 품질을 단순 육안 검토에 의존하지 않고 **정량적인 지표를 활용하여 평가하는 프로세스**를 구축하였습니다.

또한 IoU 결과와 Small/Distant(소형·원거리), Occlusion(가림), Truncation(잘림), Ambiguity(모호성) 등의 난이도 변수를 함께 분석하여 객체 특성과 라벨링 일관성의 관계를 확인할 수 있도록 하였습니다.

이 과정에서 확인된 **6건의 Object Matching Error(객체 매칭 오류)**는 별도의 Error Analysis(오류 분석)를 통해 발생 특성과 주요 난이도 요인을 추가로 분석하였습니다.

## 10. Object Matching Error Analysis(객체 매칭 오류 분석)

Repeat Annotation(반복 라벨링)과 Object Matching(객체 매칭) 과정에서 정상적으로 매칭되지 않은 **6건의 오류 사례**를 별도로 분석하였습니다.

분석의 목적은 단순히 오류 개수를 확인하는 것이 아니라, 오류 객체에서 반복적으로 나타나는 **Small/Distant(소형·원거리), Occlusion(가림), Truncation(잘림), Ambiguity(모호성)** 등의 특성을 확인하여 라벨링 난이도와 오류 발생 가능성의 관계를 탐색하는 것입니다.

### 10.1 Error Case Summary(오류 사례 요약)

총 6건의 Object Matching Error(객체 매칭 오류)에서 확인된 주요 Attribute(속성) 분포는 다음과 같습니다.

| Attribute(속성) | 주요 결과 | 비율 |
|---|---:|---:|
| Small/Distant = True | 5 / 6 | 83.3% |
| Occlusion = Partial | 3 / 6 | 50.0% |
| Occlusion = Heavy | 2 / 6 | 33.3% |
| Occlusion = Partial + Heavy | 5 / 6 | 83.3% |
| Ambiguity = Boundary | 3 / 6 | 50.0% |
| Truncation = None | 6 / 6 | 100.0% |

### 10.2 Small/Distant Object(소형·원거리 객체)

6건의 오류 사례 중 **5건(83.3%)**이 Small/Distant=True로 분류된 객체였습니다.

이는 소형·원거리 객체가 이미지에서 차지하는 영역이 작기 때문에 객체의 위치와 경계를 정확하게 판단하기 어렵고, Reference Annotation(기준 라벨링)과 Repeat Annotation(반복 라벨링) 간 객체 식별 및 매칭 과정에서도 어려움이 발생할 수 있음을 보여주는 사례입니다.

다만 오류 사례의 수가 제한적이므로 Small/Distant가 객체 매칭 오류의 직접적인 원인이라고 단정하기보다는 **추가 검토가 필요한 주요 난이도 요인**으로 해석하였습니다.

### 10.3 Occlusion(가림)

오류 사례 중 Partial Occlusion(부분 가림)은 **3건**, Heavy Occlusion(심한 가림)은 **2건**으로 나타났습니다.

두 조건을 합하면 전체 오류 사례의 **5건(83.3%)**에서 일정 수준 이상의 Occlusion이 확인되었습니다.

객체 일부가 다른 객체나 구조물에 의해 가려진 경우 객체의 전체 형태와 경계를 판단하기 어려워질 수 있으므로, Occlusion은 Small/Distant와 함께 추가적인 품질 관리가 필요한 조건으로 확인되었습니다.

### 10.4 Ambiguity(모호성)

6건의 오류 사례 중 **3건(50.0%)**에서 Boundary Ambiguity(경계 모호성)가 확인되었습니다.

이는 객체의 존재 자체보다 **어디까지를 하나의 객체 경계로 판단할 것인지**가 반복 라벨링 과정에서 일관성에 영향을 줄 수 있음을 보여줍니다.

따라서 경계가 불명확한 객체에 대해서는 Annotation Guideline(라벨링 가이드라인)에 구체적인 예시를 추가하거나 QA 과정에서 별도로 검토하는 방법을 고려할 수 있습니다.

### 10.5 Truncation(잘림)

오류 사례 6건 모두에서 Truncation은 **None**으로 나타났습니다.

따라서 이번 오류 사례만을 기준으로 볼 때 Truncation이 주요 공통 특성으로 나타나지는 않았습니다.

이는 오류 사례에서 반복적으로 나타난 Small/Distant 및 Occlusion과 대조되는 결과이며, 객체 매칭 오류의 특성을 분석할 때 모든 난이도 Attribute(속성)가 동일한 방식으로 작용하지 않을 수 있음을 보여줍니다.

### 10.6 Error Pattern Summary(오류 패턴 요약)

이번 Object Matching Error Analysis(객체 매칭 오류 분석)에서는 다음과 같은 패턴을 확인하였습니다.

- 오류 사례의 **83.3%**가 Small/Distant Object(소형·원거리 객체)
- 오류 사례의 **83.3%**에서 Partial 또는 Heavy Occlusion(부분 또는 심한 가림) 확인
- 오류 사례의 **50.0%**에서 Boundary Ambiguity(경계 모호성) 확인
- 오류 사례에서는 Truncation(잘림)이 공통적인 난이도 요인으로 나타나지 않음

특히 **Small/Distant와 Occlusion이 오류 사례에서 높은 빈도로 관찰**되었으며, 객체의 크기와 가림 상태가 라벨링 및 객체 매칭 과정에서 추가적인 검토가 필요한 조건임을 확인하였습니다.

### 10.7 QA Implications(QA 시사점)

Error Analysis(오류 분석) 결과를 기반으로 다음과 같은 품질 개선 방향을 도출하였습니다.

1. Small/Distant Object(소형·원거리 객체)에 대한 별도의 QA 기준 강화
2. Partial 및 Heavy Occlusion 객체의 우선 검토
3. Boundary Ambiguity 사례에 대한 가이드라인 예시 확대
4. 고난도 객체에 대한 Second Review(2차 검토) 적용
5. 반복 오류 사례를 활용한 Annotation Guideline(라벨링 가이드라인) 지속 개선

이번 분석은 제한된 Pilot Dataset(파일럿 데이터셋)을 기반으로 한 탐색적 분석이므로 전체 자율주행 데이터에 일반화하기에는 한계가 있습니다. 그러나 **라벨링 → QA → 반복 라벨링 → 오류 분석 → 가이드라인 개선**으로 이어지는 품질 관리 프로세스를 구축했다는 점에서 의미가 있습니다.

## 11. Key Findings(핵심 발견)

Data Understanding(데이터 이해), Pilot Annotation(파일럿 라벨링), Annotation QA(라벨링 품질 검증), Repeat Annotation(반복 라벨링) 및 Error Analysis(오류 분석)를 통해 다음과 같은 주요 결과를 확인하였습니다.

### 11.1 라벨링 품질은 Bounding Box만으로 평가하기 어렵습니다

자율주행 데이터 라벨링에서는 객체에 Bounding Box(바운딩 박스)를 생성하는 것뿐만 아니라 **Occlusion(가림), Truncation(잘림), Small/Distant(소형·원거리), Ambiguity(모호성)** 등의 객체 특성을 함께 관리하는 것이 중요함을 확인하였습니다.

이러한 Attribute(속성)는 라벨링 난이도를 설명하고, 이후 QA 및 오류 분석에서 어떤 객체를 우선적으로 검토해야 하는지 판단하는 데 활용할 수 있습니다.

### 11.2 파일럿 데이터에서도 다양한 난이도 조건이 확인되었습니다

8장의 Pilot Image(파일럿 이미지)에서 총 **73개의 객체**를 라벨링하였으며, 이 중 **41개(56.2%)**가 Small/Distant=True로 분류되었습니다.

또한 **41개(56.2%)**의 객체에서 Partial 또는 Heavy Occlusion(부분 또는 심한 가림)이 확인되었습니다.

따라서 제한된 파일럿 데이터에서도 객체 크기와 가림 등 다양한 난이도 조건을 포함하여 라벨링 가이드라인과 QA 프로세스를 검토할 수 있었습니다.

### 11.3 QA에서는 데이터의 의미와 저장 형식을 함께 확인해야 합니다

CVAT Export(내보내기) 데이터를 pandas로 처리하는 과정에서 Attribute의 `None` 값이 `NaN`으로 인식되는 사례를 확인하였습니다.

이를 통해 Missing Value(결측값)를 단순히 프로그램 출력만으로 판단하기보다 **원본 라벨의 의미와 데이터 저장·로딩 방식을 함께 확인하는 과정이 필요**하다는 점을 확인하였습니다.

최종 QA 결과에서는 **73개 라벨, 8개 이미지, 중복 Object ID 0건, 필수값 결측 0건**으로 데이터의 구조적 완전성을 확인하였습니다.

### 11.4 반복 라벨링을 통해 일관성을 정량적으로 검토할 수 있습니다

선정된 **16개의 객체**를 대상으로 Repeat Annotation(반복 라벨링)을 수행하고 Reference Annotation(기준 라벨링)과 비교하였습니다.

IoU(Intersection over Union)를 활용함으로써 Bounding Box(바운딩 박스)의 일관성을 육안 검토에만 의존하지 않고 정량적으로 평가할 수 있는 QA 프로세스를 구성하였습니다.

또한 정상적인 Bounding Box 비교와 Object Matching Error(객체 매칭 오류)를 분리함으로써 **위치 차이와 객체 식별·매칭 문제를 서로 다른 품질 이슈로 관리**할 수 있었습니다.

### 11.5 소형·원거리 및 가림 객체는 우선적인 QA 검토 대상이 될 수 있습니다

총 **6건의 Object Matching Error(객체 매칭 오류)** 중:

- **5건(83.3%)**이 Small/Distant=True
- **5건(83.3%)**이 Partial 또는 Heavy Occlusion
- **3건(50.0%)**이 Boundary Ambiguity
- **6건(100.0%)**이 Truncation=None

으로 나타났습니다.

표본의 규모가 작기 때문에 인과관계를 일반화할 수는 없지만, 이번 Pilot Dataset(파일럿 데이터셋)에서는 **Small/Distant와 Occlusion이 오류 사례에서 반복적으로 관찰되는 특성**임을 확인하였습니다.

따라서 실제 QA 프로세스에서는 이러한 난이도 조건을 가진 객체를 우선 검토하거나 Second Review(2차 검토) 대상으로 지정하는 방식을 고려할 수 있습니다.

### 11.6 Overall Finding(종합 결과)

본 프로젝트를 통해 자율주행 데이터 라벨링의 품질 관리는 단순한 오류 수정이 아니라,

**Data Understanding(데이터 이해) → Guideline(가이드라인) → Labeling(라벨링) → QA(품질 검증) → Repeat Annotation(반복 라벨링) → Error Analysis(오류 분석) → Guideline Improvement(가이드라인 개선)**

으로 이어지는 반복적인 품질 관리 과정으로 접근할 필요가 있음을 확인하였습니다.

특히 객체의 난이도 Attribute(속성)를 라벨링 단계부터 구조적으로 기록하면 이후 QA 과정에서 오류 패턴을 분석하고, 우선 검토 대상을 정의하며, 라벨링 가이드라인을 개선하는 데 활용할 수 있습니다.


## 12. Project Deliverables(프로젝트 산출물)

본 프로젝트에서는 자율주행 데이터에 대한 이해부터 라벨링, 품질 검증 및 오류 분석까지의 전체 과정을 기록하기 위해 다음과 같은 산출물을 구성하였습니다.

### 12.1 Data Understanding Notebook(데이터 이해 노트북)

nuImages Dataset(데이터셋)의 구조와 주요 객체 특성을 분석한 Notebook(노트북)입니다.

주요 분석 내용은 다음과 같습니다.

- Dataset Structure(데이터셋 구조) 확인
- Class Distribution(클래스 분포) 분석
- Bounding Box(바운딩 박스) 및 Object Size(객체 크기) 분석
- Occlusion(가림) 및 Truncation(잘림) 분석
- Small/Distant Object(소형·원거리 객체) 분석
- 라벨링 난이도 요인 도출

분석 결과는 이후 Pilot Dataset(파일럿 데이터셋) 선정과 Annotation Guideline(라벨링 가이드라인) 설계에 활용하였습니다.

### 12.2 Annotation Guideline(라벨링 가이드라인)

Pilot Annotation(파일럿 라벨링)에 적용할 객체 및 Attribute(속성) 판단 기준을 정리하였습니다.

주요 기준은 다음과 같습니다.

- Bounding Box(바운딩 박스)
- Object Class(객체 클래스)
- Occlusion(가림)
- Truncation(잘림)
- Small/Distant(소형·원거리)
- Ambiguity(모호성)
- Excluded Object(제외 객체)

가이드라인은 실제 CVAT 라벨링 과정에서 발생한 판단 사례를 반영하여 일관된 라벨링 기준을 유지하는 데 활용하였습니다.

### 12.3 CVAT Pilot Annotation(파일럿 라벨링 결과)

CVAT을 활용하여 **8장의 이미지에서 총 73개의 객체**를 직접 라벨링한 결과입니다.

각 객체에는 다음 정보가 포함됩니다.

- Object ID(객체 ID)
- Class Label(클래스 라벨)
- Bounding Box Coordinates(바운딩 박스 좌표)
- Occlusion(가림)
- Truncation(잘림)
- Small/Distant(소형·원거리)
- Ambiguity(모호성)
- Notes(비고)

### 12.4 Annotation QA Notebook(라벨링 품질 검증 노트북)

CVAT Export(내보내기) 데이터를 기반으로 라벨링 데이터의 구조와 품질을 검증한 Notebook(노트북)입니다.

주요 QA 항목은 다음과 같습니다.

- Missing Value Check(결측값 확인)
- Duplicate Object ID Check(중복 객체 ID 확인)
- Data Type Validation(데이터 유형 검증)
- Bounding Box Validation(바운딩 박스 검증)
- Class 및 Attribute Validation(클래스 및 속성 검증)
- Distribution Check(분포 검증)

### 12.5 Repeat Annotation & IoU Analysis(반복 라벨링 및 IoU 분석)

선정된 **16개 객체**를 다시 라벨링하고 Reference Annotation(기준 라벨링)과 비교하여 Bounding Box(바운딩 박스)의 일관성을 평가한 분석 결과입니다.

주요 산출물은 다음과 같습니다.

- Repeat Annotation Data(반복 라벨링 데이터)
- Reference & Repeat Object Matching(기준·반복 객체 매칭)
- IoU Calculation(IoU 계산)
- Difficulty-based Analysis(난이도 기반 분석)
- IoU Visualization(IoU 시각화)

### 12.6 Object Matching Error Analysis(객체 매칭 오류 분석)

Repeat Annotation(반복 라벨링) 과정에서 확인된 **6건의 Object Matching Error(객체 매칭 오류)**를 별도로 분석한 결과입니다.

Small/Distant(소형·원거리), Occlusion(가림), Truncation(잘림), Ambiguity(모호성) 등의 Attribute(속성)를 기준으로 오류 사례의 특성을 분석하고 QA 개선 방향을 도출하였습니다.

### 12.7 Deliverables Summary(산출물 요약)

| Deliverable(산출물) | 주요 목적 |
|---|---|
| Data Understanding Notebook | 데이터 구조 및 라벨링 난이도 분석 |
| Annotation Guideline | 일관된 라벨링 판단 기준 정의 |
| CVAT Pilot Annotation | 실제 객체 라벨링 수행 |
| Processed Annotation Data | QA 및 후속 분석용 정제 데이터 |
| Annotation QA Notebook | 데이터 완전성 및 일관성 검증 |
| Repeat Annotation Data | 반복 라벨링 결과 기록 |
| IoU Analysis | Bounding Box 일관성 정량 평가 |
| Object Matching Error Analysis | 오류 특성 분석 및 QA 개선 방향 도출 |
| README | 전체 프로젝트 과정 및 결과 요약 |

각 산출물은 **Data Understanding(데이터 이해) → 라벨링 기준 수립 → 실제 라벨링 → QA → 정량 평가 → 오류 분석**의 전체 Workflow(워크플로우)를 재현할 수 있도록 구성하였습니다.

## 13. Project Structure(프로젝트 구조)

본 프로젝트는 Raw Data(원본 데이터), Processed Data(가공 데이터), 분석 Notebook(노트북), 시각화 결과 등을 구분하여 관리할 수 있도록 다음과 같은 구조로 구성하였습니다.

```text
data-labeling-portfolio/
│
├── data/
│   ├── raw/
│   │   └── nuImages 원본 데이터
│   │
│   └── processed/
│       └── pilot/
│           ├── CVAT Export 데이터
│           ├── QA용 정제 데이터
│           └── Repeat Annotation 데이터
│
├── notebooks/
│   ├── Data Understanding
│   ├── Pilot Annotation
│   ├── Annotation QA
│   ├── IoU Analysis
│   └── Object Matching Error Analysis
│
├── images/
│   ├── Data Understanding 시각화
│   ├── CVAT 라벨링 예시
│   ├── QA 결과 시각화
│   └── IoU 및 Error Analysis 시각화
│
├── README.md
├── requirements.txt
└── .gitignore
```

### 13.1 `data/raw`

nuImages Dataset(데이터셋)의 원본 데이터를 관리하는 디렉터리입니다.

Raw Data(원본 데이터)는 분석 및 라벨링의 기준 데이터로 유지하며, 원본 파일을 직접 수정하지 않고 필요한 데이터는 별도의 Processed Data(가공 데이터)로 생성하는 방식으로 관리하였습니다.

### 13.2 `data/processed`

Pilot Annotation(파일럿 라벨링), Annotation QA(라벨링 품질 검증) 및 후속 분석에서 생성된 가공 데이터를 관리합니다.

특히 `processed/pilot`에는 CVAT에서 Export(내보내기)한 라벨링 결과와 QA 및 Repeat Annotation(반복 라벨링)에 사용되는 데이터를 구분하여 저장하였습니다.

### 13.3 `notebooks`

프로젝트의 주요 분석 및 검증 과정을 단계별 Notebook(노트북)으로 관리합니다.

Notebook은 다음과 같은 Workflow(워크플로우)를 따라 구성하였습니다.

```text
Data Understanding
        ↓
Pilot Annotation
        ↓
Annotation QA
        ↓
Repeat Annotation & IoU Analysis
        ↓
Object Matching Error Analysis
```

각 Notebook에는 분석 목적, 실행 코드, 결과, Observation(관찰 결과) 및 Summary(요약)를 함께 기록하여 분석 과정과 판단 근거를 확인할 수 있도록 구성하였습니다.

### 13.4 `images`

Data Understanding(데이터 이해), Annotation QA(라벨링 품질 검증), IoU 및 Error Analysis(오류 분석) 과정에서 생성된 주요 Chart(차트)와 Visualization(시각화) 결과를 관리하기 위한 디렉터리입니다.

README 및 향후 Portfolio Presentation(포트폴리오 프레젠테이션)에서 핵심 분석 결과를 시각적으로 보여주는 데 활용할 수 있습니다.

### 13.5 Repository Management(저장소 관리)

프로젝트의 재현성과 관리 편의성을 높이기 위해 다음과 같은 파일을 함께 관리합니다.

- `README.md`: 프로젝트 전체 과정 및 주요 결과 설명
- `requirements.txt`: Python Package(파이썬 패키지) 및 실행 환경 관리
- `.gitignore`: 불필요한 환경 파일 및 대용량 원본 데이터의 Git 추적 제외

이와 같은 구조를 통해 **원본 데이터 → 가공 데이터 → 분석 → QA → 결과물**을 명확하게 분리하고, 프로젝트의 전체 Workflow(워크플로우)를 쉽게 확인할 수 있도록 구성하였습니다.

## 14. Tools & Environment(도구 및 환경)

본 프로젝트에서는 자율주행 Dataset(데이터셋) 분석, 객체 라벨링, 품질 검증 및 결과 시각화를 위해 다음과 같은 도구와 환경을 활용하였습니다.

### 14.1 Development Environment(개발 환경)

| Tool / Environment(도구 및 환경) | 활용 목적 |
|---|---|
| Python 3.12.9 | 데이터 처리 및 분석 |
| Jupyter Notebook | 단계별 분석, QA 및 결과 기록 |
| VS Code | Notebook 및 프로젝트 파일 관리 |
| Git / GitHub | Version Control(버전 관리) 및 포트폴리오 관리 |
| Virtual Environment(가상 환경) | 프로젝트별 Python Package(패키지) 관리 |

### 14.2 Annotation Tool(라벨링 도구)

**CVAT(Computer Vision Annotation Tool)**을 Pilot Annotation(파일럿 라벨링)의 주요 도구로 사용하였습니다.

CVAT에서는 다음 작업을 수행하였습니다.

- 2D Bounding Box(2D 바운딩 박스) 생성
- Object Class(객체 클래스) 지정
- Occlusion(가림) 기록
- Truncation(잘림) 기록
- Small/Distant(소형·원거리) 기록
- Ambiguity(모호성) 기록
- 라벨링 결과 Export(내보내기)

이를 통해 실제 Computer Vision(컴퓨터 비전) 데이터 라벨링 환경에서 객체와 Attribute(속성)를 구조적으로 관리하였습니다.

### 14.3 Python Libraries(파이썬 라이브러리)

데이터 분석과 품질 검증에는 다음과 같은 주요 Python Library(파이썬 라이브러리)를 활용하였습니다.

| Library(라이브러리) | 활용 목적 |
|---|---|
| pandas | 라벨링 데이터 로딩, 정제 및 QA |
| NumPy | 수치 계산 및 데이터 처리 |
| Matplotlib | 분석 결과 시각화 |
| nuImages Devkit | nuImages 데이터 구조 및 라벨 정보 접근 |

Python 기반 분석을 통해 CVAT에서 생성된 라벨링 결과를 단순 저장하는 데 그치지 않고, 데이터 구조와 품질을 정량적으로 검증하였습니다.

### 14.4 Analysis & QA Environment(분석 및 QA 환경)

Jupyter Notebook을 활용하여 프로젝트의 주요 분석 과정을 단계별로 기록하였습니다.

각 Notebook(노트북)은 기본적으로 다음 구조를 따르도록 구성하였습니다.

```text id="h59ydj"
Objective(분석 목적)
    ↓
Data Preparation(데이터 준비)
    ↓
Analysis / Validation(분석 및 검증)
    ↓
Visualization(시각화)
    ↓
Observation(관찰 결과)
    ↓
Summary(요약)
```

이를 통해 코드 실행 결과뿐만 아니라 **분석 목적, 결과 해석 및 판단 근거**를 함께 기록하여 프로젝트의 재현성과 가독성을 높이고자 하였습니다.

### 14.5 Version Control(버전 관리)

Git과 GitHub를 활용하여 프로젝트 진행 단계별 변경 사항을 관리하였습니다.

Data Understanding(데이터 이해), Pilot Annotation(파일럿 라벨링), Annotation QA(라벨링 품질 검증), IoU Analysis(IoU 분석), Error Analysis(오류 분석) 등의 주요 작업 단위별로 변경 내용을 Commit(커밋)하여 프로젝트 진행 과정을 추적할 수 있도록 관리하였습니다.

또한 `.gitignore`를 활용하여 Virtual Environment(가상 환경), 불필요한 임시 파일 및 GitHub에서 직접 관리할 필요가 없는 데이터가 Repository(저장소)에 포함되지 않도록 관리하였습니다.

### 14.6 Environment Management(환경 관리)

프로젝트 실행에 필요한 Python Package(파이썬 패키지)는 Virtual Environment(가상 환경)에서 관리하고, 주요 Dependency(의존성)는 `requirements.txt`를 통해 기록하여 동일한 분석 환경을 재구성할 수 있도록 하였습니다.

이와 같은 환경 구성을 통해 **CVAT 기반 라벨링과 Python 기반 QA 및 분석을 하나의 Workflow(워크플로우)로 연결**하였습니다.


## 15. Limitations(한계)

본 프로젝트는 자율주행 데이터 라벨링의 전체 Workflow(워크플로우)를 직접 수행하고 품질 관리 과정을 검증하는 Pilot Project(파일럿 프로젝트)로 진행되었습니다. 따라서 분석 결과를 해석할 때 다음과 같은 한계가 있습니다.

### 15.1 Limited Sample Size(제한된 표본 크기)

Pilot Annotation(파일럿 라벨링)은 **8장의 이미지와 73개의 객체**를 대상으로 수행하였습니다.

또한 Repeat Annotation(반복 라벨링)은 **16개의 객체**를 대상으로 진행하였으며, Object Matching Error Analysis(객체 매칭 오류 분석)에서 확인된 오류 사례는 **6건**입니다.

따라서 이번 프로젝트에서 확인된 객체 분포와 오류 패턴을 전체 nuImages Dataset(데이터셋)이나 일반적인 자율주행 데이터의 특성으로 일반화하기에는 한계가 있습니다.

### 15.2 Single Annotator(단일 라벨러)

본 프로젝트의 Pilot Annotation(파일럿 라벨링)과 Repeat Annotation(반복 라벨링)은 동일한 라벨러가 수행하였습니다.

따라서 IoU Analysis(IoU 분석)는 동일 라벨러의 반복 작업에 대한 **Intra-Annotator Consistency(라벨러 내 일관성)**를 확인하는 데 의미가 있으며, 여러 라벨러 간 판단 차이를 평가하는 **Inter-Annotator Agreement(라벨러 간 일치도)**를 측정한 결과는 아닙니다.

실제 대규모 라벨링 프로젝트에서는 여러 라벨러의 결과를 비교하여 가이드라인의 해석 차이와 라벨러 간 일관성을 추가로 검증할 필요가 있습니다.

### 15.3 Limited Error Cases(제한된 오류 사례)

Object Matching Error(객체 매칭 오류)는 총 **6건**으로, 통계적으로 충분한 규모의 오류 데이터라고 보기 어렵습니다.

Small/Distant(소형·원거리)와 Occlusion(가림)이 오류 사례에서 높은 빈도로 관찰되었지만, 이를 객체 매칭 오류의 직접적인 원인으로 단정할 수는 없습니다.

따라서 본 프로젝트의 Error Analysis(오류 분석)는 **오류 발생 가능성이 높은 조건을 탐색하기 위한 분석**으로 해석하는 것이 적절합니다.

### 15.4 Limited Scene Diversity(제한된 장면 다양성)

8장의 Pilot Image(파일럿 이미지)만을 사용하였기 때문에 다양한 도로, 날씨, 조도, 교통 밀도 및 촬영 조건을 충분히 포함하지 못했습니다.

실제 자율주행 데이터에서는 Day/Night(주간/야간), Weather Condition(기상 조건), Dense Traffic(밀집 교통), 복잡한 교차로 등 다양한 환경에 따라 라벨링 난이도가 달라질 수 있습니다.

### 15.5 Bounding Box-focused Evaluation(바운딩 박스 중심 평가)

본 프로젝트의 정량적 품질 평가는 주로 2D Bounding Box(2D 바운딩 박스)와 IoU(Intersection over Union)를 중심으로 수행하였습니다.

따라서 Segmentation(세그멘테이션), Tracking(추적), 3D Bounding Box(3D 바운딩 박스) 등 자율주행 데이터에서 활용되는 다른 라벨링 유형의 품질은 평가하지 않았습니다.

### 15.6 Limitation Summary(한계 요약)

본 프로젝트의 결과는 대규모 자율주행 Dataset(데이터셋)의 품질을 대표하기 위한 것이 아니라, 제한된 Pilot Dataset(파일럿 데이터셋)을 활용하여 **라벨링 가이드라인 수립 → 실제 라벨링 → QA → 반복 라벨링 → 정량 평가 → 오류 분석**의 전체 품질 관리 프로세스를 구축하고 검증하는 데 목적이 있습니다.

따라서 분석 결과는 확정적인 결론보다는 향후 데이터와 라벨러 규모를 확대하여 검증할 수 있는 **초기 품질 관리 기준과 개선 방향을 도출한 결과**로 해석하였습니다.


## 16. Future Improvements(향후 개선 방향)

본 프로젝트에서 구축한 라벨링 및 품질 관리 Workflow(워크플로우)를 실제 대규모 자율주행 데이터 환경으로 확장하기 위해 다음과 같은 개선 방향을 고려할 수 있습니다.

### 16.1 Dataset Expansion(데이터셋 확대)

현재 8장의 Pilot Image(파일럿 이미지)를 대상으로 수행한 라벨링을 더 많은 이미지로 확대하여 분석 결과의 신뢰성을 높일 수 있습니다.

특히 다음과 같은 다양한 Driving Condition(주행 조건)을 포함할 필요가 있습니다.

- Day / Night(주간 / 야간)
- Weather Condition(기상 조건)
- Urban / Suburban Road(도심 / 외곽 도로)
- Dense Traffic(밀집 교통)
- Intersection(교차로)
- Small/Distant Object(소형·원거리 객체)가 많은 장면

데이터 규모와 Scene Diversity(장면 다양성)를 확대하면 특정 조건에서 반복적으로 발생하는 라벨링 오류를 보다 안정적으로 분석할 수 있습니다.

### 16.2 Multi-Annotator Evaluation(다중 라벨러 평가)

현재의 Intra-Annotator Consistency(라벨러 내 일관성) 평가를 여러 라벨러가 참여하는 방식으로 확장할 수 있습니다.

동일한 이미지와 객체를 여러 라벨러가 독립적으로 라벨링하고 결과를 비교하여 **Inter-Annotator Agreement(라벨러 간 일치도)**를 측정할 수 있습니다.

이를 통해 다음과 같은 항목을 추가로 평가할 수 있습니다.

- Bounding Box(바운딩 박스) 위치 차이
- Class(클래스) 판단 일치도
- Attribute(속성) 판단 일치도
- 라벨러별 오류 패턴
- 가이드라인 해석 차이

### 16.3 Difficulty-based QA(난이도 기반 QA)

모든 객체를 동일한 방식으로 검토하기보다 Object Difficulty(객체 난이도)에 따라 QA 우선순위를 설정하는 방식을 적용할 수 있습니다.

이번 Pilot Analysis(파일럿 분석)에서 오류 사례에 상대적으로 많이 나타난 Small/Distant(소형·원거리), Occlusion(가림), Boundary Ambiguity(경계 모호성) 등의 Attribute(속성)를 활용하여 고난도 객체를 우선적인 Second Review(2차 검토) 대상으로 지정할 수 있습니다.

이를 통해 제한된 QA Resource(품질 검증 자원)를 상대적으로 검토가 필요한 객체에 집중하는 방식을 검토할 수 있습니다.

### 16.4 Annotation Guideline Improvement(라벨링 가이드라인 개선)

실제 라벨링 및 Error Analysis(오류 분석)에서 발견된 사례를 지속적으로 가이드라인에 반영할 수 있습니다.

특히 다음과 같은 사례를 Example-based Guideline(사례 기반 가이드라인)으로 추가할 수 있습니다.

- 작은 원거리 객체의 Bounding Box 기준
- Partial / Heavy Occlusion 판단 사례
- Partial / Heavy Truncation 판단 사례
- Boundary Ambiguity 사례
- Class Ambiguity 사례
- 인접하거나 겹쳐 있는 객체의 구분 기준

이를 통해 텍스트 중심의 규칙뿐만 아니라 실제 이미지 사례를 활용하여 라벨러 간 판단 차이를 줄일 수 있습니다.

### 16.5 QA Automation(QA 자동화)

현재 Notebook(노트북)에서 수행한 일부 검증 작업을 자동화하여 대규모 라벨링 데이터에도 적용할 수 있습니다.

자동화 가능한 주요 항목은 다음과 같습니다.

- Missing Value Check(결측값 확인)
- Duplicate Object ID Check(중복 객체 ID 확인)
- Bounding Box Coordinate Validation(좌표 검증)
- 허용되지 않은 Class 및 Attribute 탐지
- 비정상적인 Bounding Box Size(바운딩 박스 크기) 탐지
- Class 및 Attribute Distribution Monitoring(분포 모니터링)
- QA Report(QA 보고서) 자동 생성

이를 통해 반복적인 검증 작업을 줄이고 QA 과정의 일관성과 효율성을 높일 수 있습니다.

### 16.6 Advanced Annotation Tasks(고급 라벨링 작업)

향후 프로젝트에서는 2D Bounding Box(2D 바운딩 박스)를 넘어 자율주행 분야에서 활용되는 다양한 Annotation Task(라벨링 작업)로 확장할 수 있습니다.

예를 들어 다음과 같은 영역을 추가로 검토할 수 있습니다.

- Semantic Segmentation(의미론적 세그멘테이션)
- Instance Segmentation(인스턴스 세그멘테이션)
- Object Tracking(객체 추적)
- 3D Bounding Box(3D 바운딩 박스)
- LiDAR Point Cloud Annotation(라이다 포인트 클라우드 라벨링)

이를 통해 Image-based Annotation(이미지 기반 라벨링)에서 Video 및 3D Sensor Data(3D 센서 데이터)까지 자율주행 데이터 라벨링 경험을 확장할 수 있습니다.

### 16.7 Future Improvement Summary(향후 개선 요약)

향후에는 **데이터 규모 확대 → 다중 라벨러 평가 → 난이도 기반 QA → 가이드라인 개선 → QA 자동화 → 고급 라벨링 유형 확장**의 방향으로 프로젝트를 발전시킬 수 있습니다.

특히 본 프로젝트에서 구축한 **Labeling → QA → Repeat Annotation → Error Analysis → Guideline Improvement**의 반복 구조를 유지하면서 데이터 규모와 라벨러 수를 확대하면, 보다 체계적인 자율주행 데이터 품질 관리 Workflow(워크플로우)로 발전시킬 수 있습니다.

## 17. Summary(프로젝트 요약)

본 프로젝트에서는 **nuImages Dataset(데이터셋)**을 활용하여 자율주행 데이터의 특성을 분석하고, Annotation Guideline(라벨링 가이드라인) 수립부터 CVAT 기반 Pilot Annotation(파일럿 라벨링), Annotation QA(라벨링 품질 검증), Repeat Annotation(반복 라벨링), IoU Analysis(IoU 분석) 및 Object Matching Error Analysis(객체 매칭 오류 분석)까지 데이터 라벨링의 전체 Workflow(워크플로우)를 수행하였습니다.

8장의 Pilot Image(파일럿 이미지)에서 **7개 Class(클래스), 총 73개의 객체**를 직접 라벨링하고 객체별 Occlusion(가림), Truncation(잘림), Small/Distant(소형·원거리), Ambiguity(모호성) 등의 Attribute(속성)를 구조적으로 기록하였습니다. 이후 QA를 통해 **중복 Object ID 0건, 필수값 결측 0건**을 확인하고, 16개 객체에 대한 Repeat Annotation과 IoU를 활용하여 Bounding Box(바운딩 박스)의 재현성과 일관성을 정량적으로 검토하였습니다.

Object Matching Error(객체 매칭 오류) 6건을 추가 분석한 결과, Small/Distant와 Occlusion이 오류 사례에서 상대적으로 높은 빈도로 관찰되었습니다. 제한된 Pilot Dataset을 기반으로 한 결과이므로 이를 일반적인 인과관계로 해석할 수는 없지만, 이러한 객체 특성을 **난이도 기반 QA와 Second Review(2차 검토)의 우선순위를 설정하기 위한 후보 지표**로 활용할 가능성을 확인하였습니다.

본 프로젝트를 통해 데이터 라벨링은 단순히 객체에 Bounding Box를 생성하는 작업이 아니라, **명확한 기준을 수립하고 결과를 검증하며 오류 패턴을 다시 가이드라인에 반영하는 반복적인 품질 관리 과정**임을 확인하였습니다.

최종적으로 본 프로젝트는 다음과 같은 End-to-End Workflow(전체 과정)를 구축하고 직접 적용하는 데 중점을 두었습니다.

**Data Understanding(데이터 이해) → Annotation Guideline(라벨링 가이드라인) → CVAT Labeling(CVAT 라벨링) → Annotation QA(라벨링 품질 검증) → Repeat Annotation(반복 라벨링) → IoU Analysis(IoU 분석) → Error Analysis(오류 분석) → Guideline Improvement(가이드라인 개선)**