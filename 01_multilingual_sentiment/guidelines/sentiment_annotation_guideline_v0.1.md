# Multilingual Sentiment Annotation Guideline
### 다국어 감성 라벨링 가이드라인 | 多语言情感标注指南

**Version:** 0.1
**Date:** 2026-08-28
**Task:** Multilingual Sentiment Annotation
**Languages:** English (EN) | Korean (KO) | Chinese (ZH)
**Label Set:** Positive | Neutral | Mixed | Unclear

--

## 1. Objective | 목적 | 目标

This guideline defines consistent annotation rules for sentiment 
classification across English, Korean, and Chinese review texts.

본 가이드라인은 영어, 한국어, 중국어 리뷰 텍스트에 대해 일관된 감성 라벨을 부여하기 위한 기준을 정의한다. 

本指南用于建立统一的情感标注标准，
对英语，对韩语和中文评论文本进行情感分类。

The annotation must be based only on the review text.
Existing ratings or ground-truth labels must not be referenced 
during manual annotation.

라벨링 시 리뷰 텍스트만을 기준으로 판단하며, 기존 별점이나, Ground Truth 라벨은 참고하지 않는다. 

人工标注时仅根据评论文本进行判断，
不得参考原始星级评分或 Ground Truth 标签.

---

# 2. Label Schema | 라벨 정의 | 标签定义

## 2.1 Positive | 긍정 | 正面

### Definition 

The overall opinion is clearly favorable.
전체적으로 만족, 칭찬, 추천 등 긍정적인 평가가 명확한 경우.

整体评价明确表达满意，赞扬，推荐等正面态度。

### Examples

**EN**

> "This product works perfectly. I would definitely buy it again."

→ `Positive`

**KO**

> "가격 대비 품질도 좋고 정말 만족합니다."

→ `Positive`

**ZH**

→ "质量很好，使用起来也很方便，下次还会购买。”

→ `Positive`

### Key Indicators 

- Satisfaction / 만족/ 满意
- Praise / 칭찬 / 赞扬
- Recommendation / 추천 / 推荐
- Repurchase intention / 재구매 의향 / 再次购买意愿

---

## 2.2 Negative | 부정 | 负面

### Definition

The overall opinion is clearly unfavorable.

불만, 비판, 실패 경험 등 부정적인 평가가 명확한 경우 

整体评价明确表达不满，批评或负面的使用体验。

### Examples

**EN**

→ "It stopped working after two days. Waste of money."

→ `Negative`

**KO**

→ "품질이 너무 안 좋고 다시는 구매하지 않을 것 같아요."

→ `Negative`

**ZH**

→ "质量太差了，用了两天就坏了，不会再买。”

→ `Negative`

### Key Indicators

- Dissatisfaction / 불만/ 不满
- Complaint / 불평 / 投诉
- Failure / 제품·서비스 실패 / 产品或服务故障
- Rejection / 비추천 / 不推荐

---

## 2.3 Neutral | 중립 | 中性

### Definition

The review mainly contains factual or descriptive information
without a clear positive or negative evaluation.

감정적인 평가보다 사실이나 정보 전달이 중심이며 
긍정 또는 부정의 방향이 명확하지 않는 경우.

评论主要描述事实或信息，
没有明显的正面或负面态度。

### Examples

**EN**

> "The package arrived yesterday and contains two pieces."

→ `Neutral`

**KO**

> "제품은 검은색이고 두 개가 들어 있습니다."

→ `Neutral`

**ZH**

> "产品是黑色的，包装里有两个。"

→ `Neutral`

### Important Rule

Do not classify a review as Neutral simply because the sentiment is weak.

단순히 감정의 강도가 약하다는 이유로 Neutral을 선택하지 않는다.

不能仅因为情感表达较弱就标注为 Neutral。

Example:

> "It's pretty good for the price."

→ `Positive`, not `Neutral`

---

## 2.4 Mixed | 혼합 | 混合

### Definition

Both meaningful positive and negative opinions are present,
and neither clearly dominates the overall evaluation.

긍정과 부정 평가가 동시에 존재하며
어느 한쪽이 전체 의견을 명확하게 지배하지 않는 경우.

评论同时包含明显的正面和负面评价，
且任何一方都没有明显占据主导。

### Examples

**EN**

> "The product is excellent, but the delivery was terrible."

→ `Mixed`

**KO**

> "제품 자체는 좋은데 배송이 너무 느렸어요."

→ `Mixed`

**ZH**

> "东西很好，但是物流实在太慢了。"

→ `Mixed`

### Dominance Rule

If one sentiment clearly dominates, use the dominant sentiment.

한쪽 감성이 명확하게 우세하면 Mixed가 아니라
우세한 감성으로 분류한다.

如果一种情感明显占主导，
则应标注主要情感，而不是 Mixed。

Example:

> "The box was slightly damaged, but the product itself is excellent."

→ `Positive`

---

## 2.5 Unclear | 판단 불가 | 不明确

### Definition

The sentiment cannot be determined reliably from the available text.

텍스트만으로 감성을 신뢰성 있게 판단하기 어려운 경우.

仅根据现有文本无法可靠判断情感倾向。

### Typical Cases

- Incomplete text / 불완전한 문장 / 文本不完整
- Meaningless text / 의미 불명 / 无明确含义
- Ambiguous sarcasm / 모호한 반어 / 难以判断的讽刺
- Insufficient context / 맥락 부족 / 上下文不足

### Examples

**EN**

> "Well... that was something."

→ `Unclear`

**KO**

> "ㅋㅋㅋ 이게 뭐지"

→ `Unclear`

**ZH**

> "呵呵，就这样吧。"

→ `Unclear`

---

# 3. Core Annotation Principles
## 공통 라벨링 원칙 | 通用标注原则

### 3.1 Judge Overall Sentiment
### 전체 의견을 판단 | 判断整体情感

Do not label based on individual positive or negative words.
Consider the overall meaning of the review.

개별 단어가 아니라 리뷰 전체의 의미를 기준으로 판단한다.

不要根据单个正面或负面词语进行判断，
应结合整条评论的整体含义。

Example:

> "The design is nice, but it stopped working after two days."

→ `Negative`

The product failure dominates the minor positive comment.

---

### 3.2 Do Not Use Star Ratings
### 별점 참고 금지 | 禁止参考星级评分

Annotators must not access original ratings or ground-truth labels.

라벨링 중 원본 별점이나 기존 라벨을 확인하지 않는다.

标注过程中不得查看原始星级评分或已有标签。

Use only:

- `review_title`
- `review_body`

---

### 3.3 Handle Negation Carefully
### 부정 표현 주의 | 注意否定表达

Negation may reverse the apparent sentiment.

부정 표현은 감성 방향을 반대로 바꿀 수 있다.

否定词可能改变原本的情感方向。

**EN**

> "Not bad at all."

→ `Positive`

**KO**

> "생각보다 나쁘지 않아요."

→ `Positive`

**ZH**

> "还不错。"

→ `Positive`

Negative example:

**EN:** "I don't recommend it."  
**KO:** "추천하고 싶지 않아요."  
**ZH:** "不推荐购买。"

→ `Negative`

---

# 4. Ambiguous Cases
## 애매한 사례 처리 | 模糊情况处理

### 4.1 Positive + Negative

If both opinions are meaningful and balanced:

→ `Mixed`

If one clearly dominates:

→ Dominant sentiment

---

### 4.2 Sarcasm | 반어법 | 讽刺

If sarcasm is clearly understandable, annotate the intended sentiment.

반어적 의미가 명확하면 실제 의도된 감성을 기준으로 판단한다.

如果讽刺含义明确，应按照实际表达的情感进行标注。

**EN**

> "Great. It broke after five minutes."

→ `Negative`

**KO**

> "와 정말 최고네요. 하루 만에 고장났어요."

→ `Negative`

**ZH**

> "真是太棒了，用一天就坏了。"

→ `Negative`

If the intended meaning cannot be determined confidently:

→ `Unclear`

---

# 5. Language-Specific Considerations
## 언어별 판단 기준 | 各语言注意事项

## 5.1 English (EN)

Pay particular attention to:

- Negation
- Idiomatic expressions
- Sarcasm
- Intensifiers
- Understatement

Examples:

> "Not worth the money."

→ `Negative`

> "Pretty good for the price."

→ `Positive`

> "Could be better."

→ Usually `Negative` or `Neutral` depending on context.

---

## 5.2 Korean (KO) | 한국어

주의해서 판단할 표현:

- 이중 부정
- 반어법
- 인터넷 은어
- 축약 표현
- ㅋㅋ / ㅎㅎ / ㅠㅠ 등의 감정 표현
- 존댓말을 사용한 비꼬는 표현

Examples:

> "나쁘지 않음"

→ `Positive`

> "돈 아깝다"

→ `Negative`

> "이 가격이면 뭐 괜찮네요"

→ `Positive`

> "참 잘도 만들었네요. 하루 만에 고장남."

→ `Negative`

`ㅋㅋ`, `ㅎㅎ` alone must not automatically be interpreted
as positive sentiment.

---

## 5.3 Chinese (ZH) | 中文

标注时特别注意：

- 否定词：不、没、无
- 程度副词：很、太、非常、挺
- 委婉表达
- 网络用语
- 反讽
- “还行 / 还好 / 一般”等上下文依赖表达

Examples:

> "还不错。"

→ `Positive`

> "不怎么样。"

→ `Negative`

> "一般般。"

→ Usually `Neutral` or weak `Negative`,
depending on context.

> "东西不错，就是物流太慢。"

→ `Mixed`

> "呵呵，质量真好，用一天就坏了。"

→ `Negative` if sarcasm is clear.

---

# 6. Confidence Level
## 신뢰도 | 置信度

Each annotation must include one confidence level.

모든 라벨에는 판단 신뢰도를 함께 기록한다.

每条标注都必须记录判断置信度。

| Level | Definition |
|---|---|
| `High` | Sentiment is explicit and unambiguous |
| `Medium` | Some interpretation is required |
| `Low` | Meaning is ambiguous or highly context-dependent |

### High

EN: "Absolutely terrible product."  
KO: "정말 최악의 제품입니다."  
ZH: "这个产品真的太差了。"

→ `Negative / High`

### Medium

EN: "Good, although a little expensive."  
KO: "괜찮긴 한데 조금 비싸네요."  
ZH: "还不错，就是有点贵。"

→ Requires contextual judgment

### Low

EN: "Well, I guess it works."  
KO: "뭐... 되긴 하네요."  
ZH: "嗯……勉强能用吧。"

→ Requires careful interpretation

---

# 7. Notes Field
## 비고 작성 | 备注栏

Use `notes` when the annotation requires explanation.

판단 근거를 남길 필요가 있는 경우 `notes`를 작성한다.

当情感判断需要进一步说明时填写 `notes`。

Recommended cases:

- Mixed sentiment
- Sarcasm
- Low confidence
- Language-specific expression
- Ambiguous interpretation
- Unclear label

Example notes:

`Positive product evaluation + negative delivery experience`

`Sarcasm indicates negative sentiment`

`Korean slang expressing dissatisfaction`

`Chinese expression "一般般" interpreted as weak negative`

---

# 8. Annotation Workflow
## 작업 프로세스 | 标注流程

1. Read `review_title` and `review_body`.
2. Identify the overall sentiment.
3. Assign ONE sentiment label.
4. Assign confidence: `High / Medium / Low`.
5. Add notes when necessary.
6. Flag difficult cases for QA review.
7. Do not check original ratings during annotation.

### Workflow

Raw Review
→ Blind Annotation
→ Confidence Assessment
→ Ambiguous Case Review
→ QA
→ Ground Truth Comparison
→ Error Analysis

---

# 9. Quality Assurance
## 품질 관리 | 质量控制

After annotation, perform the following QA procedures:

라벨링 완료 후 다음 QA 과정을 수행한다.

完成标注后进行以下质量检查：

- Review all `Low` confidence samples.
- Review all `Mixed` samples.
- Review all `Unclear` samples.
- Check missing annotation fields.
- Check label consistency across languages.
- Compare annotations with existing ground truth.
- Analyze disagreement cases.
- Document recurring ambiguity.
- Update the guideline when necessary.

---

# 10. Guideline Revision Policy
## 가이드라인 개정 | 指南修订规则

This document is a working guideline.

Pilot annotation will be conducted before the main annotation.

본 가이드라인은 Pilot Annotation 결과에 따라 수정될 수 있다.

本指南将在 Pilot Annotation 后根据实际案例进行修订。

### Planned Process

`Guideline v0.1`

→ `Pilot Annotation`

→ `Ambiguous Case Analysis`

→ `Guideline v0.2`

→ `Main Annotation`

→ `QA & Ground Truth Comparison`

→ `Final Guideline v1.0`
