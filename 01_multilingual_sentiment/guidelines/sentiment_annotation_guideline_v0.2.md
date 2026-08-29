# Multilingual Sentiment Annotation Guideline

**Version:** 0.2  
**Languages:** English (EN) / Korean (KO) / Chinese (ZH)  
**Label Set:** Positive | Negative | Neutral | Mixed | Unclear

---

## Revision Note

Version 0.2 incorporates findings from the multilingual pilot
annotation conducted on Korean, English, and Chinese review samples.

Major revisions include:

- Clarification of Neutral vs. Unclear
- Expansion of the dominant sentiment rule
- Definition of the sentiment target
- Clarification of core vs. secondary product attributes
- Separation of annotation confidence from sentiment intensity
- Expanded Korean, English, and Chinese language-specific guidance
- Guidance for template-like and reward-driven reviews
- Expanded notes and QA requirements

---

# 1. Purpose / 목적 / 目的

## EN
This guideline defines consistent annotation rules for multilingual
sentiment classification across English, Korean, and Chinese review data.

The goal is to improve:

- Annotation consistency
- Cross-language consistency
- Reproducibility
- QA reliability
- Interpretability of annotation decisions

## KO
본 가이드라인은 영어, 한국어, 중국어 리뷰 데이터의 감성 분류를
일관되게 수행하기 위한 기준을 정의한다.

주요 목적은 다음과 같다.

- 라벨링 일관성 향상
- 언어 간 판단 기준 통일
- 재현 가능한 annotation process 구축
- QA 신뢰성 향상
- 판단 근거의 명확성 확보

## ZH
本指南用于统一英语、韩语和中文评论数据的情感标注标准。

主要目标包括：

- 提高标注一致性
- 保持跨语言判断标准的一致性
- 提高标注过程的可复现性
- 提高质量检查（QA）的可靠性
- 明确标注判断依据

---

# 2. Annotation Scope / 라벨링 범위 / 标注范围

## 2.1 Text Used for Annotation

Annotators must make decisions based only on:

- `review_title`
- `review_body`

Both fields should be considered together when available.

If `review_title` is missing, annotate based on `review_body`.

## 2.2 Blind Annotation Rule

Do NOT use the following information during manual annotation:

- Original rating
- Ground-truth label
- Model prediction
- External review information

Ground truth may only be used after manual annotation during:

- QA
- Agreement analysis
- Error analysis

**Core principle:**

> Annotate the review text, not the original rating.

---

# 3. Label Definitions / 라벨 정의 / 标签定义

The official label set is:

`Positive | Negative | Neutral | Mixed | Unclear`

---

## 3.1 Positive

### EN
Use `Positive` when the overall review expresses a clearly favorable
evaluation, satisfaction, praise, recommendation, or positive experience.

Examples:

- "I really like this product."
- "Works perfectly and I would buy it again."
- "The delivery was fast and the product quality is excellent."

### KO
전체적으로 만족, 칭찬, 추천, 재구매 의향 등 긍정적인 평가가
명확한 경우 `Positive`를 사용한다.

Examples:

- "정말 만족합니다."
- "품질이 좋고 다시 구매하고 싶어요."
- "배송도 빠르고 제품도 훌륭합니다."

### ZH
当评论整体表达明确的满意、赞扬、推荐或积极使用体验时，
标注为 `Positive`。

Examples:

- "非常满意。"
- "质量很好，值得推荐。"
- "物流很快，产品也很好。"

---

## 3.2 Negative

### EN
Use `Negative` when the overall review expresses dissatisfaction,
complaint, disappointment, failure, rejection, or a negative experience.

Examples:

- "The product broke after one day."
- "Very disappointed."
- "I would not recommend this."

### KO
불만, 실망, 고장, 품질 문제, 서비스 실패, 구매 비추천 등이
전체 평가를 지배하는 경우 `Negative`를 사용한다.

Examples:

- "하루 만에 고장났어요."
- "정말 실망했습니다."
- "추천하지 않습니다."

### ZH
当评论整体表达不满、失望、质量问题、功能失败或不推荐时，
标注为 `Negative`。

Examples:

- "质量太差了。"
- "非常失望。"
- "不推荐购买。"

---

## 3.3 Neutral

### EN
Use `Neutral` when the review is understandable but contains no
meaningful positive or negative evaluation.

Examples:

- "The package arrived on Tuesday."
- "The movie is set in New York."

### KO
문장의 의미는 이해할 수 있지만 긍정 또는 부정 평가가 없는 경우
`Neutral`을 사용한다.

Examples:

- "배송은 화요일에 도착했습니다."
- "이 영화의 배경은 서울입니다."

### ZH
当评论内容可以理解，但没有明确或有意义的正面或负面评价时，
标注为 `Neutral`。

Examples:

- "星期二收到包裹。"
- "这本书一共有三百页。"

### Important Rule

Weak sentiment does NOT automatically mean `Neutral`.

For example:

- EN: "It's okay." → may still be Positive depending on context.
- KO: "나쁘지 않아요." → may be Positive.
- ZH: "还不错。" → may be Positive.

---

## 3.4 Mixed

Use `Mixed` when meaningful positive AND negative evaluations are both
present and neither clearly dominates the overall review.

Example:

> "The product is excellent, but the delivery was terrible."

Possible decision:

`Mixed`

However:

> "The product works perfectly, although the packaging was slightly damaged."

may still be:

`Positive`

because the positive evaluation clearly dominates.

### Important Rule

The presence of contrastive expressions does NOT automatically indicate
`Mixed`.

Examples:

- EN: but / however / although
- KO: 하지만 / 그런데 / 다만
- ZH: 但是 / 不过 / 就是

Always evaluate the overall sentiment.

---

## 3.5 Unclear

Use `Unclear` when the sentiment cannot be reliably determined.

Typical cases include:

- Incomplete text
- Meaningless text
- Insufficient context
- Highly ambiguous sarcasm
- Context-dependent expression
- Template-like text without reliable evaluation

Examples:

- "God's Not Dead"
- "ㅋㅋㅋㅋ"
- A fragment whose intended evaluation cannot be determined

`Unclear` does NOT mean that the annotator is uncertain about everything.
An annotator may confidently determine that the available text is
insufficient.

Therefore:

`Unclear / High`

is possible.

---

# 4. Neutral vs. Unclear Decision Rule

This distinction is especially important.

Ask:

> **Can the meaning of the review be understood reliably?**

### If YES:

If the text is understandable but contains no meaningful positive or
negative evaluation:

→ `Neutral`

### If NO:

If the intended sentiment cannot be reliably determined because the text
is incomplete, ambiguous, meaningless, or context-poor:

→ `Unclear`

### Summary

| Situation | Label |
|---|---|
| Meaning is clear, no sentiment | Neutral |
| Meaning or intended sentiment cannot be reliably determined | Unclear |
| Sentiment is weak but identifiable | Positive or Negative |

---

# 5. Overall Sentiment & Dominance Rule

Annotate the **overall sentiment of the review**, not isolated words.

Do NOT count the number of positive and negative expressions.

Instead, consider:

1. Main purpose of the review
2. Importance of the evaluated feature
3. Core product or service functionality
4. Review title
5. Final conclusion
6. Recommendation or rejection
7. Severity of the reported problem

## Example 1 — Negative Dominates

> "The ring is beautiful, but it started to tarnish after two weeks.
> Very disappointed."

Positive:
- Beautiful appearance

Negative:
- Product quality failure
- Tarnishing
- Explicit disappointment

Decision:

`Negative`

---

## Example 2 — Positive Dominates

> "The charger works great. The fan is a little loud, but overall
> it's excellent."

Negative:
- Minor noise issue

Positive:
- Core function works well
- Strong overall satisfaction

Decision:

`Positive`

---

## Example 3 — Mixed

> "The product is good, but one item was missing from my order."

Product evaluation:
- Positive

Fulfillment experience:
- Negative

If neither side clearly dominates:

`Mixed`

---

# 6. Sentiment Target / 감성 판단 대상 / 情感判断对象

The annotation target is the:

> **Overall customer experience expressed in the review**

The target is NOT limited to the physical product.

Relevant targets may include:

- Product quality
- Product functionality
- Content quality
- Physical or digital edition quality
- Delivery
- Packaging
- Order fulfillment
- Seller service
- Customer service

## Example

> "The shoes are good, but the box was damaged and the shoes arrived
> scratched."

Possible targets:

- Product itself → Positive
- Packaging / delivery → Negative

The annotator should apply the dominance rule to determine the overall
customer experience.

If both evaluations remain meaningful and balanced:

→ `Mixed`

---

# 7. Core Function vs. Secondary Attributes

The importance of an issue matters more than the number of positive or
negative statements.

### Core Function Failure

A major failure of the primary product function may outweigh minor
positive characteristics.

Example:

> "It looks nice and feels soft, but it does not work."

→ Usually `Negative`

### Minor Secondary Issue

A small secondary problem may not outweigh strong overall satisfaction.

Example:

> "Works perfectly. The packaging was slightly damaged."

→ Usually `Positive`

Annotators should consider the functional importance and severity of
each issue.

---

# 8. Negation / 부정 표현 / 否定表达

Negation may reverse sentiment polarity.

## EN

- "good" → Positive
- "not good" → Negative
- "not bad" → often mildly Positive

## KO

- "좋다" → Positive
- "좋지 않다" → Negative
- "나쁘지 않다" → often mildly Positive

## ZH

- "很好" → Positive
- "不太好" → Negative
- "还不错" → often mildly Positive

Always interpret the complete expression rather than individual
sentiment words.

---

# 9. Sarcasm / 반어·비꼼 / 反讽

Sarcasm should be annotated according to the intended sentiment when the
intention is sufficiently clear.

Example:

> "Great. It broke after one day."

→ `Negative`

If the sarcastic intention cannot be reliably determined:

→ `Unclear`

Use `notes` for ambiguous sarcasm.

---

# 10. Language-Specific Guidance

## 10.1 Korean / 한국어

Pay special attention to:

- Double negatives
- Sarcasm and irony
- Internet slang
- Abbreviations
- ㅋㅋ / ㅎㅎ / ㅠㅠ
- Honorific sarcasm
- Incomplete expressions

### Important

`ㅋㅋ` or `ㅎㅎ` alone does NOT automatically indicate Positive sentiment.

Depending on context, laughter markers may express:

- amusement
- sarcasm
- ridicule
- embarrassment
- discomfort
- no clear sentiment

If the intended sentiment cannot be determined:

→ `Unclear`

---

## 10.2 English

Pay special attention to:

- Negation
- Idioms
- Sarcasm
- Intensifiers
- Understatement
- Contrastive structures
- Core-function failure

Examples:

- "not bad" → often mildly Positive
- "absolutely terrible" → strong Negative
- "not exactly great" → Negative
- "works fine, but..." → evaluate the full context

Do not determine sentiment from `but`, `however`, or `although` alone.

---

## 10.3 Chinese / 中文

Pay special attention to:

- Negation
- Mild evaluative expressions
- Rhetorical questions
- Implicit dissatisfaction
- Contrastive expressions
- Context-dependent internet language

Common mild expressions include:

- 还不错
- 还好
- 还行
- 一般
- 有点

### Important

Mild expression does NOT automatically mean:

- `Neutral`
- `Medium confidence`
- `Low confidence`

Example:

> "书还不错，纸张也还好，发货很快。"

→ `Positive / High`

The sentiment intensity is mild, but the annotation decision is clear.

### Implicit Negative Sentiment

Negative sentiment may be expressed through:

- unmet expectations
- rhetorical questions
- comparison with better alternatives
- loss of interest
- delayed shipping
- service failure

Example:

> "以为可以媲美东野圭吾，不过是我的一厢情愿。"

→ `Negative`

Even without a strong negative adjective, the disappointment is clear.

---

# 11. Template-like and Reward-driven Reviews

Some reviews may contain:

- Generic copied text
- Repeated templates
- Reward-point language
- Promotional or non-product content

Example:

> "很好……这段话复制走了，既能赚积分，还省事。"

If reliable sentiment toward the product or customer experience is still
present:

→ Annotate the identifiable sentiment.

If reliable evaluation cannot be determined:

→ Consider `Unclear`

Borderline cases should be documented in `notes`.

---

# 12. Confidence Level

Confidence represents:

> **How certain the annotator is that the assigned label is correct.**

Confidence does NOT represent:

> **How strong the sentiment is.**

---

## 12.1 High

Use `High` when the label decision is explicit or unambiguous.

Examples:

> "Terrible product."

→ `Negative / High`

> "还不错。"

If the context clearly supports a mild positive evaluation:

→ `Positive / High`

---

## 12.2 Medium

Use `Medium` when some interpretation is required.

Typical situations:

- Competing positive and negative signals
- Dominance judgment is required
- Multiple sentiment targets
- Mild contextual ambiguity

---

## 12.3 Low

Use `Low` when the label remains highly ambiguous or context-dependent.

Typical situations:

- Ambiguous sarcasm
- Incomplete expression
- Highly context-dependent slang
- Multiple plausible interpretations

---

## Important Confidence Rule

Sentiment intensity ≠ annotation confidence.

A weak sentiment may receive `High` confidence.

A strong emotional expression may receive `Medium` or `Low` confidence
if its intended target or meaning is ambiguous.

---

# 13. Notes Field

The `notes` field is optional but strongly recommended for cases requiring
additional interpretation.

Use notes especially for:

- Mixed sentiment
- Unclear cases
- Low confidence
- Sarcasm
- Language-specific expressions
- Dominant-sentiment decisions
- Multiple sentiment targets
- Product vs. fulfillment conflicts
- Content vs. edition quality conflicts
- Template-like or reward-driven reviews

Notes should be:

- Short
- Objective
- Focused on the reason for the decision

Example:

> `Positive product evaluation, but delivery complaint dominates.`

Do NOT write long personal explanations.

---

# 14. Annotation Workflow

Follow the annotation process in this order:

`Raw Review`
→ `Blind Annotation`
→ `Confidence Assessment`
→ `Notes for Borderline Cases`
→ `Ambiguous Case Review`
→ `QA`
→ `Ground Truth Comparison`
→ `Error Analysis`

Ground truth must NOT be checked before manual annotation is completed.

---

# 15. Quality Assurance (QA)

QA should review:

1. Missing sentiment labels
2. Missing confidence values
3. All `Low` confidence cases
4. All `Mixed` cases
5. All `Unclear` cases
6. Dominant-sentiment consistency
7. Multiple sentiment-target conflicts
8. Recurring language-specific ambiguity
9. Cross-language consistency
10. Annotation distribution

### Important

Label distributions should be monitored but must NOT be artificially
balanced.

If a pilot or annotation sample contains:

- No Mixed cases
- No Neutral cases
- No Unclear cases
- No Low-confidence cases

this does not automatically indicate an annotation problem.

Labels must reflect the actual review text.

---

# 16. Cross-Language Consistency

The same core annotation principles should apply across English,
Korean, and Chinese.

Language-specific expressions may differ, but the following principles
must remain consistent:

- Overall sentiment
- Dominance rule
- Sentiment target
- Neutral vs. Unclear
- Mixed criteria
- Confidence interpretation

Language-specific rules should clarify linguistic differences without
changing the fundamental label definitions.

---

# 17. Guideline Revision Process

Guideline updates should be based on observed annotation evidence.

Revision workflow:

`Guideline v0.1`
→ `Multilingual Pilot Annotation`
→ `Pilot Findings & QA`
→ `Guideline v0.2`
→ `Main Annotation`
→ `QA & Ground Truth Comparison`
→ `Error Analysis`
→ `Guideline v1.0`

Do NOT overwrite previous guideline versions.

Each version should remain available for traceability and
reproducibility.

---

# 18. Version History

| Version | Stage | Main Changes |
|---|---|---|
| v0.1 | Initial Guideline | Initial multilingual sentiment rules |
| v0.2 | Post-Pilot Revision | Dominance, sentiment target, Neutral vs. Unclear, confidence clarification, expanded language-specific rules |
| v1.0 | Planned Final Version | Final revisions after main annotation, QA, ground-truth comparison, and error analysis |