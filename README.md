# Multilingual Sentiment Annotation & Quality Assurance

A multilingual data labeling portfolio project demonstrating an end-to-end
**text annotation and quality assurance workflow** across English, Chinese,
and Korean datasets.

---

## 1. Project Overview

This project demonstrates the design and execution of a **multilingual
sentiment annotation workflow** for English, Chinese, and Korean text data.

A total of **900 reviews (300 per language)** were prepared and evaluated
using a consistent annotation framework.

The project covers the complete annotation lifecycle, including:

- Data preparation
- Pilot annotation
- Annotation guideline development
- Full-scale annotation
- Quality assurance (QA)
- Agreement analysis
- Multilingual evaluation

Rather than focusing only on assigning sentiment labels, the project
emphasizes **annotation consistency, ambiguity handling, reproducible quality
checks, and cross-language quality evaluation**.

### Project at a Glance

| Item | Description |
|---|---|
| **Task** | Multilingual Sentiment Annotation |
| **Languages** | English (EN), Chinese (ZH), Korean (KO) |
| **Dataset Size** | 900 reviews (300 per language) |
| **Annotation Type** | Sentiment polarity + sentiment intensity |
| **Core Labels** | Positive, Negative, Unclear |
| **Quality Process** | Manual review + Programmatic QA + Agreement analysis |
| **Environment** | Python, Pandas, Jupyter Notebook, VS Code |
| **Version Control** | Git & GitHub |

---

## 2. Project Objectives

The primary objective of this project is to build and evaluate a
**consistent multilingual annotation workflow** across English, Chinese,
and Korean text datasets.

The project was designed around the following objectives:

1. **Develop a consistent annotation framework**
   - Define clear sentiment polarity and intensity criteria.
   - Apply the same core annotation principles across three languages.

2. **Establish a practical annotation workflow**
   - Conduct pilot annotation before full-scale labeling.
   - Refine annotation guidelines based on ambiguous and edge cases.
   - Apply the finalized guidelines to larger annotation batches.

3. **Implement systematic quality assurance**
   - Validate annotation outputs using programmatic QA checks.
   - Identify unclear cases, inconsistencies, and potential disagreements.
   - Review problematic samples before finalizing the dataset.

4. **Evaluate annotation quality across languages**
   - Analyze agreement and annotation consistency.
   - Compare quality patterns across English, Chinese, and Korean.
   - Identify language-specific challenges in sentiment interpretation.

5. **Create a reproducible annotation pipeline**
   - Organize datasets, notebooks, QA outputs, and documentation
     in a structured repository.
   - Use Python and Pandas to support repeatable validation
     and evaluation processes.

### Portfolio Focus

This project is designed to demonstrate practical capabilities in:

- Multilingual text annotation
- Annotation guideline development
- Sentiment classification
- Ambiguity and edge-case handling
- Annotation quality assurance
- Agreement analysis
- Data validation
- Reproducible workflow design

## 3. Dataset Overview

This project uses multilingual review datasets in **English, Chinese,
and Korean** to evaluate whether a consistent sentiment annotation
framework can be applied across different languages.

A total of **900 reviews** were included in the final annotation scope,
with **300 samples selected for each language**.

### Dataset Summary

| Language | Dataset | Text Type | Samples |
|---|---|---|---:|
| English (EN) | Amazon Reviews | Product reviews | 300 |
| Chinese (ZH) | Amazon Reviews | Product reviews | 300 |
| Korean (KO) | NSMC | Movie reviews | 300 |
| **Total** | - | - | **900** |



### Data Sources

#### English & Chinese

The English and Chinese samples were prepared from **Amazon product
review datasets** accessed through Hugging Face.

The review data provides natural user-generated text containing
positive, negative, mixed, and potentially ambiguous sentiment
expressions.

#### Korean

The Korean samples were prepared from the **Naver Sentiment Movie
Corpus (NSMC)**.

NSMC contains Korean movie reviews and provides a useful source for
evaluating sentiment annotation in naturally occurring Korean text.

### Sample Selection

For this portfolio project, **300 reviews per language** were selected
to create a manageable but sufficiently diverse annotation set.

The same overall annotation and QA framework was then applied across
the three language datasets.

### Standardized Data Structure

The multilingual data was organized using a common schema to support
consistent annotation and downstream quality analysis.

Key fields include:

- `review_id`
- `review_title`
- `review_body`
- `language`
- `product_category`
- `sentiment_label`
- `confidence`
- `notes`

This standardized structure allows annotation outputs from different
languages and source datasets to be validated and compared using the
same QA workflow.

> **Note:** The stored dataset uses the column name `confidence` for
> historical consistency. In the final annotation framework, this field
> represents **sentiment intensity (High / Medium / Low)** rather than
> annotator confidence.
---

## 4. Annotation Schema

Each review was annotated using two primary dimensions:

1. **Sentiment Polarity** - the overall direction of sentiment expressed
   in the review.
2. **Sentiment Intensity** - the strength of the sentiment expressed
   through linguistic and contextual cues.

This framework separates **what sentiment is expressed** from
**how strongly it is expressed**.

### 4.1 Sentiment Polarity

| Label | Definition |
|---|---|
| **Positive** | The review expresses an overall favorable opinion, satisfaction, approval, or recommendation. |
| **Negative** | The review expresses an overall unfavorable opinion, dissatisfaction, criticism, rejection, or complaint. |
| **Unclear** | The overall sentiment cannot be determined reliably because the text is ambiguous, mixed, context-dependent, or insufficiently evaluative. |

### 4.2 Sentiment Intensity

Sentiment intensity was assigned as **Low, Medium, or High** based on
the strength of the linguistic evidence in the review.

| Intensity | Definition |
|---|---|
| **Low** | Sentiment is implied or expressed mainly through factual description with little or no emotional language. |
| **Medium** | Sentiment is clearly expressed, but the emotional strength remains moderate without strong emphasis, rejection, warning, or repeated reinforcement. |
| **High** | Strong sentiment is explicitly expressed through intensified emotional language, repeated criticism or praise, strong recommendation or rejection, warnings, or multiple reinforcing statements. |

### 4.3 Intensity Decision Examples

#### Low

> "The seeds were spilled out into the shipping envelope."

**Negative / Low**

The event is negative, but the reviewer uses little emotional language.

#### Medium

> "Seal was broken. Product looks different than prior purchase."

**Negative / Medium**

The dissatisfaction is clear, but the emotional expression remains
moderate.

#### High

> "Very disappointed. Will not buy again."

**Negative / High**

The reviewer explicitly intensifies dissatisfaction and rejects future
purchase.

### 4.4 Intensity Decision Principle

Intensity is determined by **linguistic evidence of emotional strength**,
not simply by whether an event itself appears serious.

For example, a serious product problem described factually may still
receive **Low intensity**, while explicit rejection, strong emotional
language, repeated criticism, or warnings may indicate **High intensity**.

This distinction was introduced to reduce subjective interpretation
and improve consistency across annotation batches.

### 4.5 Combined Annotation

Polarity and intensity were evaluated separately and then combined to
represent the final annotation.

Examples include:

- `Positive / High`
- `Positive / Medium`
- `Negative / Low`
- `Negative / High`
- `Unclear`

This structure allows QA analysis to distinguish between:

- **Polarity disagreement** - disagreement about whether sentiment is
  Positive, Negative, or Unclear.
- **Intensity disagreement** - agreement on polarity but disagreement
  about how strongly the sentiment is expressed.
- **Exact disagreement** - disagreement on either polarity or intensity.

### 4.6 Schema Naming Note

The processed dataset retains the column name `confidence` from an
earlier version of the annotation schema.

In the finalized annotation framework, this variable represents
**sentiment intensity**, with the values:

- `High`
- `Medium`
- `Low`

The README and evaluation results therefore use the term
**sentiment intensity** to describe this annotation dimension.

---

## 5. Annotation Guidelines

A shared annotation guideline was developed to maintain consistent
decision-making across English, Chinese, and Korean reviews.

The guideline was initially tested during the **pilot annotation stage**
and refined based on ambiguous cases, disagreements, and recurring
annotation challenges.

### 5.1 Core Annotation Principles

The following principles were applied throughout the annotation process:

1. **Evaluate the overall sentiment**
   - Assign the label based on the reviewer's overall evaluation.
   - Do not determine sentiment from isolated positive or negative words.

2. **Prioritize the dominant sentiment**
   - When both positive and negative opinions appear, identify which
     sentiment represents the reviewer's main conclusion.
   - Use contextual meaning rather than simple keyword frequency.

3. **Separate polarity from intensity**
   - `sentiment_label` represents the overall direction of sentiment.
   - `confidence` stores the sentiment intensity level
     (`High`, `Medium`, or `Low`).
   - Intensity reflects the strength of emotional expression rather
     than annotator certainty.

4. **Use `Unclear` when sentiment cannot be reliably determined**
   - Do not force ambiguous reviews into Positive or Negative.
   - Flag difficult cases for additional review when necessary.

5. **Apply consistent principles across languages**
   - The same core decision framework was used for English, Chinese,
     and Korean.
   - Language-specific expressions were interpreted within their
     linguistic and cultural context.

### 5.2 Edge-Case Handling

Several recurring edge cases were identified during annotation.

| Edge Case | Decision Approach |
|---|---|
| **Mixed Sentiment** | Identify the dominant overall evaluation. If no dominant sentiment can be established, use `Unclear`. |
| **Sarcasm / Irony** | Interpret the intended meaning rather than the literal wording. Use `Unclear` when the intended sentiment cannot be determined reliably. |
| **Product vs. Delivery** | Consider whether the complaint or praise changes the reviewer's overall evaluation rather than relying only on product-related keywords. |
| **Short Reviews** | Use available context carefully. Very limited or non-evaluative text may be classified as `Unclear`. |
| **Implicit Sentiment** | Assign polarity only when contextual evidence is sufficiently strong; otherwise use `Unclear`. |
| **Conflicting Signals** | Evaluate the reviewer's final or dominant conclusion. Use `Unclear` when competing sentiment signals prevent a reliable overall decision. |
| **Language-Specific Expressions** | Interpret idioms, informal expressions, emphasis, and contextual cues according to the source language. |

### 5.3 Guideline Refinement

The annotation guideline was treated as an **iterative quality-control
document** rather than a fixed set of rules.

The refinement process followed this cycle:

`Pilot Annotation`
→ `Identify Ambiguous Cases`
→ `Review Decision Rules`
→ `Update Guidelines`
→ `Apply to Full Annotation`
→ `QA Review`

This process helped convert individual annotation decisions into
documented rules that could be applied more consistently across
subsequent annotation batches.

### 5.4 Guideline Versioning

The initial guideline was created before full-scale annotation and
updated after reviewing pilot and edge cases.

- **v0.1** - Initial multilingual annotation framework
- **v0.2** - Refined rules based on pilot annotation and edge-case review
- **v0.3** - Expanded decision rules based on batch-level QA findings
- **v0.4** - Finalized intensity criteria and edge-case guidance

Maintaining guideline versions provides traceability for changes in
annotation decisions and supports a more reproducible annotation
process.

---

## 6. Annotation Workflow

The project followed a structured annotation workflow designed to
improve consistency, traceability, and quality across all three
languages.

### 6.1 Workflow Overview

The overall process consisted of seven stages:

`Data Preparation`
→ `Pilot Annotation`
→ `Guideline Refinement`
→ `Batch Annotation`
→ `Quality Assurance`
→ `Agreement Analysis`
→ `Multilingual Evaluation`

### 6.2 Data Preparation

Raw review data was prepared and standardized before annotation.

Key preparation steps included:

- Selecting samples for each language
- Standardizing column names and data structure
- Assigning language identifiers
- Preparing annotation fields
- Creating processed datasets for annotation
- Validating dataset dimensions and required columns

The final annotation scope consisted of:

- **English:** 300 reviews
- **Chinese:** 300 reviews
- **Korean:** 300 reviews
- **Total:** 900 reviews

### 6.3 Pilot Annotation

A smaller set of samples was annotated before full-scale labeling.

The pilot stage was used to:

- Test the initial annotation schema
- Identify ambiguous sentiment expressions
- Evaluate sentiment intensity criteria
- Discover recurring edge cases
- Validate the practical usability of the guideline

Issues identified during the pilot were incorporated into subsequent
guideline revisions.

### 6.4 Guideline Refinement

The initial annotation guideline was refined based on observations
from the pilot annotation.

Special attention was given to cases involving:

- Mixed sentiment
- Sarcasm and irony
- Implicit sentiment
- Product versus delivery experience
- Short or context-limited reviews
- Language-specific expressions

This process resulted in a more detailed and consistent decision
framework for full-scale annotation.

### 6.5 Batch Annotation

Full annotation was performed in smaller batches rather than processing
all 900 reviews at once.

This approach made it possible to:

- Review annotation quality incrementally
- Detect inconsistencies earlier
- Manage ambiguous cases systematically
- Maintain a traceable annotation history
- Perform QA checks throughout the project

Each review received a sentiment polarity label and intensity level
according to the shared annotation guideline.

### 6.6 Quality Assurance

After annotation, programmatic and manual QA procedures were used to
validate the outputs.

QA checks focused on:

- Missing annotation values
- Invalid label values
- Dataset dimensions
- Language consistency
- Intensity inconsistencies
- Unclear cases
- Potential annotation disagreements
- Structural consistency across datasets

QA outputs were saved separately to support reproducibility and
further review.

### 6.7 Agreement Analysis

Agreement analysis was performed to evaluate annotation consistency
and identify cases requiring additional review.

The analysis focused on:

- Agreement patterns
- Disagreement cases
- Ambiguous samples
- Intensity patterns
- Cross-language differences

The results were used as an additional quality-control layer before
the final multilingual evaluation.

### 6.8 Multilingual Evaluation

After language-level QA and agreement analysis, the English, Chinese,
and Korean outputs were evaluated together.

The final evaluation was designed to assess:

- Dataset completeness
- Annotation consistency
- Polarity and intensity distributions
- Language-level quality differences
- Recurring multilingual annotation challenges

This final stage provides an integrated view of annotation quality
across the complete **900-review multilingual dataset**.

---

## 7. Quality Assurance Framework

Quality assurance was implemented as an integral part of the annotation
workflow rather than as a final inspection step.

The QA process combined **programmatic validation, manual review,
agreement analysis, and targeted review of ambiguous cases**.

Because the three language datasets were developed and reviewed through
different QA stages, agreement metrics are reported within their
respective evaluation contexts rather than treated as directly
comparable cross-language performance scores.

### 7.1 QA Methodology

The quality assurance process focused on four major areas:

1. **Structural Validation**
   - Verify the expected number of samples.
   - Check required annotation fields.
   - Detect missing or invalid values.
   - Confirm language and schema consistency.

2. **Annotation Validation**
   - Review sentiment polarity decisions.
   - Evaluate sentiment intensity assignments.
   - Identify ambiguous and `Unclear` cases.
   - Detect potential inconsistencies.

3. **Agreement Analysis**
   - Compare initial and reviewed annotations.
   - Measure agreement at the polarity and intensity levels.
   - Identify exact matches and disagreement patterns.

4. **Error Analysis**
   - Examine recurring disagreement types.
   - Separate direct polarity reversals from ambiguity-related cases.
   - Use difficult cases to refine annotation guidelines.

### 7.2 English QA Results

English annotation quality was evaluated across four QA batches covering
**80 reviews**.

| Metric | Result |
|---|---:|
| Reviews Evaluated | 80 |
| Overall Polarity Agreement | **92.5%** |
| Overall Intensity Agreement | **73.8%** |
| Overall Exact Agreement | **67.5%** |

#### Batch-Level Results

| Batch | Reviews | Guideline | Polarity | Intensity | Exact |
|---|---:|---|---:|---:|---:|
| EN Batch 01 | 20 | v0.2 | 100.0% | 45.0% | 45.0% |
| EN Batch 02 | 20 | v0.3 | 100.0% | 90.0% | 90.0% |
| EN Batch 03 | 20 | v0.3 | 70.0% | 80.0% | 55.0% |
| EN Batch 04 | 20 | v0.4 | 100.0% | 80.0% | 80.0% |

The English QA results show that **polarity decisions were substantially
more consistent than intensity assignments**.

The batch-level analysis also provided feedback for iterative guideline
development from **v0.2 to v0.4**.

### 7.3 Chinese QA Results

An interim QA review was conducted on **21 Chinese reviews** to identify
annotation inconsistencies and refine decision rules before finalization.

| Metric | Result |
|---|---:|
| Reviews Evaluated | 21 |
| Sentiment Agreement | **80.95%** |
| Intensity Agreement | **9.52%** |
| Exact Agreement | **0.00%** |
| Reviews Corrected | 21 |
| Correction Rate | 100.00% |

The interim review revealed a substantial difference between
**sentiment-level agreement and intensity-level agreement**.

Although sentiment agreement reached **80.95%**, intensity agreement was
only **9.52%**, resulting in no exact matches within this interim QA
sample.

Rather than interpreting the exact-match rate as overall dataset
accuracy, this result was used as a **diagnostic signal** to identify
weaknesses in the intensity criteria and support subsequent annotation
review and guideline refinement.

### 7.4 Korean QA Results

The Korean dataset was evaluated against the original NSMC sentiment
labels, providing a ground-truth comparison across all **300 reviews**.

| Metric | Result |
|---|---:|
| Total Samples | 300 |
| Ground-Truth Agreements | 260 |
| Total Disagreements | 40 |
| Overall Polarity Agreement | **86.7%** |
| Decisive Samples | 268 |
| Decisive Agreements | 260 |
| Decisive-Label Agreement | **97.0%** |
| Unclear-Related Disagreements | 32 |
| Direct Polarity Reversals | 8 |

The overall polarity agreement was **86.7%**.

However, after separating `Unclear` boundary cases, agreement on samples
receiving a decisive Positive or Negative annotation reached **97.0%**.

This indicates that most disagreement was associated with the boundary
between a decisive sentiment and `Unclear`, rather than direct confusion
between Positive and Negative sentiment.

### 7.5 Korean Disagreement Analysis

The 40 Korean disagreement cases were distributed as follows:

| Disagreement Type | Count | Percentage |
|---|---:|---:|
| Positive → Unclear | 19 | 47.5% |
| Negative → Unclear | 13 | 32.5% |
| Negative → Positive | 4 | 10.0% |
| Positive → Negative | 4 | 10.0% |

A total of **32 out of 40 disagreements (80%)** involved the `Unclear`
label, while only **8 cases (20%)** represented direct polarity
reversals.

### 7.6 Analysis of Unclear Cases

The Korean dataset contained **32 Unclear annotations (10.7%)**.

These cases were further categorized to understand the main sources
of annotation ambiguity.

| Unclear Category | Count | Percentage |
|---|---:|---:|
| Target Ambiguity | 8 | 25.0% |
| Descriptive / Non-evaluative | 8 | 25.0% |
| Insufficient Context | 8 | 25.0% |
| Implicit / Context-dependent | 7 | 21.9% |
| Mixed Sentiment | 1 | 3.1% |

The analysis shows that ambiguity was not dominated by a single error
type. Instead, it arose primarily from **target ambiguity,
non-evaluative language, insufficient context, and implicit sentiment**.

### 7.7 QA Key Takeaways

The QA process produced three important observations:

- **Polarity was generally more stable than intensity**, particularly
  in the English and Chinese QA samples.
- **Unclear boundary decisions were a major source of disagreement**
  in the Korean dataset.
- QA results were used diagnostically to **refine annotation rules and
  identify systematic sources of inconsistency**, rather than being
  treated only as final accuracy scores.

---

## 8. Agreement Analysis

Agreement analysis was conducted to identify systematic annotation
differences and evaluate the stability of the annotation framework.

The analysis distinguishes between **polarity agreement** and
**intensity agreement**, allowing different sources of annotation
difficulty to be evaluated separately.

### 8.1 Polarity Agreement

| Language | QA Reviewed | Agreements | Disagreements | Agreement Rate |
|---|---:|---:|---:|---:|
| English | 80 | 74 | 6 | **92.5%** |
| Chinese | 80 | 76 | 4 | **95.0%** |
| Korean | 300 | 260 | 40 | **86.7%** |

English and Chinese showed high polarity agreement at **92.5%** and
**95.0%**, respectively.

The Korean overall agreement rate was **86.7%**. However, most Korean
disagreements involved the `Unclear` label rather than direct
Positive–Negative reversals.

When only decisive Positive and Negative cases were considered, Korean
decisive-label agreement reached **97.0%**.

### 8.2 Intensity Agreement

Intensity agreement was evaluated for the English and Chinese QA
samples.

| Language | Reviewed | Agreements | Disagreements | Agreement Rate |
|---|---:|---:|---:|---:|
| English | 80 | 59 | 21 | **73.75%** |
| Chinese | 80 | 61 | 19 | **76.25%** |

Intensity agreement was lower than polarity agreement in both
languages.

| Language | Polarity Agreement | Intensity Agreement | Agreement Gap |
|---|---:|---:|---:|
| English | 92.50% | 73.75% | **18.75 pp** |
| Chinese | 95.00% | 76.25% | **18.75 pp** |

Both languages showed the same **18.75 percentage-point gap** between
polarity and intensity agreement.

This suggests that identifying the **direction of sentiment** was more
consistent than determining the **strength of emotional expression**.

### 8.3 English Disagreement Patterns

Among the 80 reviewed English samples:

- **6** contained polarity disagreements.
- **21** contained intensity disagreements.
- **26** contained at least one type of disagreement.

The higher number of intensity disagreements supports the finding that
sentiment strength required more subjective interpretation than
sentiment direction.

### 8.4 Chinese Disagreement Patterns

Among the 80 reviewed Chinese samples:

- **4** required sentiment changes.
- **19** required intensity changes.
- **21** required at least one annotation change.

As with English, intensity accounted for substantially more annotation
changes than polarity.

The consistency of this pattern across both languages indicates that
**intensity annotation was a cross-language challenge rather than an
isolated language-specific issue**.

### 8.5 Korean Disagreement Patterns

The 40 Korean polarity disagreements were distributed as follows:

| Disagreement Type | Count | Percentage |
|---|---:|---:|
| Positive → Unclear | 19 | 47.5% |
| Negative → Unclear | 13 | 32.5% |
| Negative → Positive | 4 | 10.0% |
| Positive → Negative | 4 | 10.0% |

A total of **32 of 40 disagreements (80.0%)** resulted in an `Unclear`
annotation.

Only **8 cases (20.0%)** represented direct Positive–Negative polarity
reversals.

This indicates that the primary Korean annotation challenge was
determining whether sufficient evidence existed for a decisive
sentiment label.

### 8.6 Cross-Language Findings

The agreement analysis revealed several recurring patterns:

1. **Polarity was relatively stable**
   - English polarity agreement: **92.5%**
   - Chinese polarity agreement: **95.0%**
   - Korean decisive-label agreement: **97.0%**

2. **Intensity was a major cross-language challenge**
   - English intensity agreement: **73.75%**
   - Chinese intensity agreement: **76.25%**
   - Both languages showed an **18.75 percentage-point gap** between
     polarity and intensity agreement.

3. **Ambiguity strongly affected Korean QA**
   - **32 of 40 disagreements (80.0%)** involved `Unclear`.
   - Direct Positive–Negative reversals occurred in only **8 cases**.

4. **Complex sentiment structures created difficult edge cases**
   - Mixed sentiment
   - Target ambiguity
   - Implicit or context-dependent sentiment
   - Possible ground-truth mismatch

### 8.7 Agreement Analysis Takeaway

The analysis demonstrates that annotation quality cannot be represented
by a single agreement score.

Different annotation dimensions produced different sources of
difficulty:

- **Polarity** was comparatively stable across languages.
- **Intensity** required greater interpretive judgment.
- **Ambiguity boundaries** were particularly important for Korean.

Separating these dimensions made it possible to identify specific
weaknesses in the annotation framework and convert disagreement cases
into actionable guideline improvements.

---

## 9. Multilingual Evaluation

The final multilingual evaluation consolidates annotation and QA results
across English, Chinese, and Korean to provide an overall view of the
project's annotation quality.

The completed dataset contains **900 annotated samples across three
languages**, with **460 samples included in language-specific QA
procedures**.

### 9.1 Final Evaluation Summary

| Metric | Result |
|---|---:|
| Languages | **3 (EN / ZH / KO)** |
| Total Annotated Samples | **900** |
| Total QA-Reviewed Samples | **460** |
| Overall QA Coverage | **51.1%** |
| English Polarity Agreement | **92.5%** |
| Chinese Polarity Agreement | **95.0%** |
| Korean Overall Agreement | **86.7%** |
| Korean Decisive Agreement | **97.0%** |
| English Intensity Agreement | **73.75%** |
| Chinese Intensity Agreement | **76.25%** |
| Korean Unclear Share of Disagreements | **80.0%** |

### 9.2 QA Coverage

Of the **900 annotated samples**, a total of **460 samples (51.1%)**
were included in structured QA procedures.

The QA scope consisted of:

- **English:** 80 of 300 samples
- **Chinese:** 80 of 300 samples
- **Korean:** 300 of 300 samples

QA coverage differed by language because the datasets were evaluated
using different validation strategies.

English and Chinese used sampled annotation review and agreement
analysis, while Korean enabled full-dataset comparison against the
original NSMC sentiment labels.

Therefore, the language-level agreement rates should be interpreted
within their respective QA designs rather than as directly equivalent
performance measures.

### 9.3 Polarity Performance

Polarity annotation showed relatively strong agreement across the
multilingual evaluation.

- English: **92.5%**
- Chinese: **95.0%**
- Korean overall: **86.7%**
- Korean decisive labels: **97.0%**

The Korean result demonstrates the importance of separating ambiguous
cases from direct polarity decisions.

Although overall agreement was **86.7%**, agreement among decisive
Positive and Negative annotations reached **97.0%**.

### 9.4 Intensity Performance

Intensity annotation showed lower agreement than polarity annotation
in both English and Chinese.

- English intensity agreement: **73.75%**
- Chinese intensity agreement: **76.25%**

In both languages, the difference between polarity and intensity
agreement was **18.75 percentage points**.

This consistent gap suggests that determining **how strongly sentiment
is expressed** requires greater interpretive judgment than identifying
the overall sentiment direction.

### 9.5 Ambiguity in Korean Annotation

Ambiguity was the dominant source of disagreement in the Korean
evaluation.

Among the 40 Korean disagreement cases:

- **32 cases (80.0%)** involved an `Unclear` annotation.
- **8 cases (20.0%)** represented direct Positive–Negative reversals.

This finding indicates that the major challenge was not distinguishing
positive from negative sentiment, but determining whether the available
text provided sufficient evidence for a decisive polarity label.

### 9.6 Multilingual Evaluation Findings

The final evaluation produced four major findings:

1. **Polarity annotation was relatively stable across languages.**
   English, Chinese, and decisive Korean annotations all achieved
   agreement above 90%.

2. **Sentiment intensity was more difficult to annotate consistently.**
   English and Chinese both showed an identical **18.75 percentage-point
   gap** between polarity and intensity agreement.

3. **Ambiguity requires explicit annotation rules.**
   Korean disagreement analysis showed that `Unclear` boundary cases
   accounted for **80.0% of disagreements**.

4. **QA design should reflect dataset characteristics.**
   Different source datasets required different validation strategies,
   including sampled annotation review and ground-truth comparison.

### 9.7 Final Evaluation Takeaway

The multilingual evaluation demonstrates that annotation quality is
multi-dimensional.

A high polarity agreement rate alone does not capture difficulties
related to **sentiment intensity, ambiguity, contextual interpretation,
or label boundaries**.

By separating these dimensions and analyzing disagreement patterns,
the project was able to identify specific annotation challenges and
translate them into actionable improvements to the annotation
guidelines and QA process.

---

## 10. Key Findings

The multilingual annotation and QA process revealed several practical
insights about sentiment annotation quality.

### 10.1 Sentiment Polarity Was More Stable Than Intensity

Polarity agreement was relatively high across the evaluated datasets:

- English: **92.5%**
- Chinese: **95.0%**
- Korean decisive-label agreement: **97.0%**

In contrast, intensity agreement was lower:

- English: **73.75%**
- Chinese: **76.25%**

Both English and Chinese showed an identical **18.75 percentage-point
gap** between polarity and intensity agreement.

This suggests that identifying whether a review is positive or negative
is generally more consistent than determining **how strongly the
sentiment is expressed**.

### 10.2 Intensity Requires More Explicit Decision Rules

Intensity disagreements occurred substantially more often than polarity
disagreements in both English and Chinese.

The annotation process showed that intensity cannot be determined only
by the severity of the event being described.

Instead, intensity should be based on observable linguistic evidence,
such as:

- Emotional emphasis
- Strong praise or criticism
- Explicit recommendation or rejection
- Repeated evaluative statements
- Warnings or purchase refusal

This finding led to more explicit Low / Medium / High decision rules
during guideline refinement.

### 10.3 `Unclear` Is an Important Quality-Control Label

The Korean evaluation demonstrated that ambiguity should not always be
forced into a binary Positive or Negative decision.

Among the **40 Korean disagreement cases, 32 (80.0%)** involved the
`Unclear` label.

The major sources of ambiguity included:

- Target ambiguity
- Descriptive or non-evaluative language
- Insufficient context
- Implicit or context-dependent sentiment
- Mixed sentiment

Treating `Unclear` as a meaningful annotation outcome helped separate
genuine polarity errors from cases where the available evidence was
insufficient for a reliable decision.

### 10.4 Disagreement Analysis Was More Informative Than a Single Score

A single agreement percentage did not fully explain annotation quality.

For example, Korean overall polarity agreement was **86.7%**, but
decisive-label agreement reached **97.0%** after separating ambiguous
`Unclear` cases.

Similarly, English and Chinese achieved high polarity agreement while
showing substantially lower intensity agreement.

Breaking agreement into **polarity, intensity, exact match, and
disagreement type** provided a more useful understanding of where
annotation inconsistencies occurred.

### 10.5 Guideline Development Is an Iterative Process

The annotation guideline evolved as new edge cases were identified
during pilot annotation, batch annotation, and QA.

The workflow followed an iterative cycle:

`Annotate`
→ `Measure Agreement`
→ `Analyze Disagreements`
→ `Refine Rules`
→ `Re-evaluate`

This process demonstrated that annotation guidelines should be treated
as **living quality-control documents** rather than static instructions.

### 10.6 Overall Takeaway

The main lesson from this project is that high-quality multilingual
annotation depends not only on language proficiency, but also on
**clear operational definitions, systematic QA, structured disagreement
analysis, and iterative guideline refinement**.

The project also demonstrated that different annotation dimensions can
produce different quality challenges, making dimension-level analysis
essential for building more consistent labeled datasets.

---

## 11. Challenges & Resolutions

The project involved several methodological and technical challenges
during multilingual annotation and QA.

Rather than treating these issues as isolated errors, they were used
to improve the annotation framework, validation process, and overall
workflow.

### 11.1 Inconsistent Intensity Interpretation

**Challenge**

Early QA showed that annotators could agree on sentiment polarity while
assigning different intensity levels to the same review.

This pattern was particularly visible in English and Chinese, where
intensity agreement was lower than polarity agreement.

**Resolution**

The intensity guideline was refined to focus on observable linguistic
evidence rather than the perceived severity of an event.

The revised criteria distinguished:

- **Low** - factual or weakly expressed sentiment
- **Medium** - clearly expressed but moderately emotional sentiment
- **High** - strongly intensified sentiment supported by explicit
  linguistic evidence

**Impact**

The revised framework provided clearer decision boundaries and made
intensity disagreements easier to identify and analyze during QA.

### 11.2 Ambiguous Sentiment Boundaries

**Challenge**

Some reviews did not contain enough evidence for a reliable Positive or
Negative decision.

This was especially important in Korean, where **80.0% of disagreement
cases involved the `Unclear` label**.

**Resolution**

Ambiguous cases were analyzed separately and categorized according to
their likely source, including:

- Target ambiguity
- Descriptive or non-evaluative language
- Insufficient context
- Implicit or context-dependent sentiment
- Mixed sentiment

**Impact**

Separating ambiguity from direct polarity errors produced a more
meaningful interpretation of annotation quality.

For Korean, overall agreement was **86.7%**, while agreement among
decisive Positive and Negative cases reached **97.0%**.

### 11.3 Cross-Language Dataset Differences

**Challenge**

The three language datasets did not have identical source
characteristics.

English and Chinese used product reviews, while Korean used movie
reviews from NSMC.

As a result, identical QA procedures could not always be applied
meaningfully across all three datasets.

**Resolution**

A shared core annotation framework was maintained while allowing
language- and dataset-specific QA strategies.

- English and Chinese used sampled review and agreement analysis.
- Korean used full-dataset comparison with the original NSMC labels.

**Impact**

This approach preserved a common annotation methodology without
incorrectly treating different QA designs as directly equivalent.

### 11.4 Schema and Terminology Evolution

**Challenge**

The annotation framework evolved during the project.

The processed datasets retained the field name `confidence`, while the
final guideline defined the variable more precisely as **sentiment
intensity**.

**Resolution**

The underlying dataset schema was retained for reproducibility, while
the final documentation explicitly defines:

`confidence` → `sentiment intensity`

The final QA and agreement analysis consistently use the terms
**polarity** and **intensity**.

**Impact**

Documenting the schema evolution preserves traceability while reducing
the risk of misinterpreting the annotation variable.

### 11.5 File and Pipeline Consistency

**Challenge**

As annotation batches, master datasets, QA outputs, and evaluation files
accumulated, inconsistent filenames and intermediate file references
caused execution errors during pipeline integration.

Examples included:

- Batch and master filename mismatches
- Missing intermediate file references
- Language-specific naming inconsistencies
- Variables referencing outdated intermediate outputs

**Resolution**

The project files were standardized and notebooks were validated using
full execution checks.

Key actions included:

- Standardizing language-specific filenames
- Separating batch, master, and QA outputs
- Correcting outdated file references
- Validating expected columns and dataset dimensions
- Re-running notebooks from beginning to end

**Impact**

The final workflow became more reproducible and reduced dependencies on
temporary notebook state or manually created intermediate variables.

### 11.6 Key Lesson

The most important lesson from these challenges was that annotation
quality depends on both **annotation methodology and pipeline
reliability**.

Clear guidelines alone are insufficient if datasets, schemas, QA
outputs, and evaluation logic are not consistently managed.

Combining annotation review with programmatic validation helped create
a more traceable and reproducible multilingual labeling workflow.

---

## 12. Repository Structure

The repository is organized to separate source data, annotation outputs,
QA artifacts, guidelines, notebooks, and downstream portfolio modules.

```text
data-labeling-portfolio/
│
├── 01_multilingual_sentiment/
│   │
│   ├── data/
│   │   │
│   │   ├── annotation/
│   │   │   ├── amazon_reviews_en_annotation_300.csv
│   │   │   ├── amazon_reviews_en_pilot_annotation_30.csv
│   │   │   ├── amazon_reviews_zh_annotation_300.csv
│   │   │   ├── amazon_reviews_zh_pilot_annotation_30.csv
│   │   │   ├── nsmc_ko_annotation_300.csv
│   │   │   └── nsmc_ko_pilot_annotation_30.csv
│   │   │
│   │   ├── processed/
│   │   │   ├── annotation_en_batch_01~04.csv
│   │   │   ├── annotation_ko_batch_01~10.csv
│   │   │   ├── annotation_ko_master.csv
│   │   │   ├── qa_en_batch_01~04.csv
│   │   │   ├── qa_metrics_ko.csv
│   │   │   ├── qa_unclear_summary_ko.csv
│   │   │   ├── qa_disagreements_ko.csv
│   │   │   ├── qa_zh_interim_30_109.csv
│   │   │   ├── qa_zh_interim_summary.csv
│   │   │   └── multilingual_qa_portfolio_metrics.csv
│   │   │
│   │   └── raw/
│   │       ├── amazon_reviews_en_ground_truth_300.csv
│   │       ├── amazon_reviews_zh_ground_truth_300.csv
│   │       ├── nsmc_ko_ground_truth_300.csv
│   │       └── ratings_train.txt
│   │
│   ├── docs/
│   │   ├── qa_summary_zh_final.md
│   │   └── qa_summary_zh_interim.md
│   │
│   ├── guidelines/
│   │   ├── sentiment_annotation_guideline_v0.1.md
│   │   ├── sentiment_annotation_guideline_v0.2.md
│   │   ├── sentiment_annotation_guideline_v0.3.md
│   │   ├── sentiment_annotation_guideline_v0.3 (2).md
│   │   └── sentiment_annotation_guideline_v0.4.md
│   │
│   ├── notebooks/
│   │   ├── 01_data_preparation.ipynb
│   │   ├── 02_pilot_annotation.ipynb
│   │   ├── 03_annotation_qa.ipynb
│   │   ├── 04_agreement_analysis.ipynb
│   │   └── 05_error_analysis.ipynb
│   │
│   └── results/
│
├── 02_image_labeling/
├── 03_autonomous_driving/
├── README.md
└── requirements.txt
```


| Directory          | Purpose                                               |
| :----------------- | :---------------------------------------------------- |
| `data/raw/`        | Original source and ground-truth datasets             |
| `data/annotation/` | Pilot and full annotation datasets                    |
| `data/processed/`  | Batch annotations, QA outputs, and evaluation metrics |
| `docs/`            | QA summaries and supporting documentation             |
| `guidelines/`      | Version-controlled annotation guidelines              |
| `notebooks/`       | Data preparation, QA, agreement, and error analysis   |
| `results/`         | Final analytical and portfolio outputs                |

This structure separates **source data, annotation artifacts, quality
outputs, and analytical code**, improving traceability and
reproducibility throughout the annotation workflow.

## 13. Tools & Technologies

The project combined manual multilingual annotation with Python-based
data validation and quality analysis.

| Tool / Technology | Application in This Project |
|---|---|
| **Python** | Data preparation, validation, QA, and agreement analysis |
| **Pandas** | Dataset transformation, aggregation, cross-tabulation, and QA metrics |
| **Jupyter Notebook** | Reproducible annotation, QA, and analysis workflows |
| **VS Code** | Development environment and project organization |
| **Git** | Version control and change tracking |
| **GitHub** | Repository management, documentation, and portfolio presentation |
| **Markdown** | Annotation guidelines, QA documentation, and project reporting |

### Technical Workflow

Python and Pandas were used to support the annotation process through:

- Dataset loading and preprocessing
- Schema and missing-value validation
- Annotation batch management
- Polarity and intensity comparison
- Agreement-rate calculation
- Disagreement extraction
- Unclear-case categorization
- Cross-language QA aggregation
- Final portfolio metric generation

### Reproducibility

The analytical workflow was organized into sequential Jupyter notebooks:

1. `01_data_preparation.ipynb`
2. `02_pilot_annotation.ipynb`
3. `03_annotation_qa.ipynb`
4. `04_agreement_analysis.ipynb`
5. `05_error_analysis.ipynb`

Separating the workflow into individual stages makes it easier to
trace how raw data progresses from preparation and annotation to
quality evaluation and error analysis.

Project dependencies are documented in:

`requirements.txt`

## 14. Skills Demonstrated

This project demonstrates practical capabilities across annotation,
quality assurance, multilingual analysis, and reproducible data
management.

### 14.1 Annotation & Guideline Design

- Multilingual sentiment annotation across English, Chinese, and Korean
- Sentiment polarity classification using Positive, Negative, and Unclear
- Sentiment intensity classification using Low, Medium, and High
- Annotation guideline development and versioning
- Pilot-based guideline refinement
- Mixed-sentiment and edge-case handling
- Ambiguity identification and resolution

### 14.2 Annotation Quality Assurance

- Programmatic annotation validation
- Manual QA review
- Polarity and intensity agreement analysis
- Disagreement extraction and classification
- `Unclear` case analysis
- Ground-truth comparison
- QA coverage measurement
- Systematic error-pattern identification

### 14.3 Multilingual Quality Analysis

- Cross-language annotation evaluation
- Identification of language-specific ambiguity patterns
- Comparison of polarity and intensity consistency
- Analysis of recurring multilingual annotation challenges
- Interpretation of results under different QA designs

### 14.4 Data & Technical Skills

- Python-based data validation
- Pandas data processing and aggregation
- Jupyter Notebook workflow development
- CSV dataset management
- Reproducible QA metric calculation
- Git version control
- GitHub repository management
- Markdown documentation

### 14.5 Quality Management Approach

The project applies a repeatable quality-management cycle:

`Define`
→ `Annotate`
→ `Validate`
→ `Measure`
→ `Analyze`
→ `Refine`

This approach demonstrates how annotation work can be managed as a
structured **data-quality process** rather than as an isolated manual
labeling task.

---

## 15. Limitations

Although this project demonstrates an end-to-end multilingual annotation
and QA workflow, several limitations should be considered when
interpreting the results.

### 15.1 Dataset Size

The project contains **900 annotated samples**, with 300 reviews per
language.

This scale is sufficient for demonstrating annotation methodology and
QA processes, but it is relatively small compared with production-level
labeling projects.

As a result, the observed agreement patterns should be interpreted as
portfolio-level findings rather than population-level estimates.

### 15.2 Different Source Domains

The datasets do not represent identical domains across all languages.

- English and Chinese data consist primarily of product reviews.
- Korean data consists of movie reviews from NSMC.

Differences in review context, writing style, and sentiment expression
may therefore influence annotation patterns.

The project evaluates a **shared annotation framework across languages**
rather than a controlled comparison of identical multilingual content.

### 15.3 Different QA Designs

QA coverage and validation methods differed by language.

- English: **80 of 300 samples reviewed**
- Chinese: **80 of 300 samples reviewed**
- Korean: **300 of 300 samples evaluated against source labels**

Overall structured QA coverage was **51.1% (460 of 900 samples)**.

Because the validation designs differ, language-level agreement rates
should not be interpreted as directly comparable performance scores.

### 15.4 Limited Independent Annotation

The project primarily represents an individual portfolio workflow
rather than a production-scale multi-annotator study.

Therefore, the agreement analysis should be interpreted as a measure of
**annotation consistency and QA revision patterns** within the project,
rather than as a formal estimate of inter-annotator reliability across
multiple independent annotators.

A larger study would benefit from multiple independent annotators and
formal inter-annotator agreement metrics.

### 15.5 Subjectivity of Sentiment Intensity

The distinction between `Low`, `Medium`, and `High` sentiment intensity
requires more interpretation than polarity classification.

This limitation is reflected in the QA results, where intensity
agreement was lower than polarity agreement for both English and
Chinese.

Although guideline refinement improved the operational definition of
intensity, some degree of subjective judgment remains unavoidable.

### 15.6 `Unclear` Label Boundaries

The `Unclear` label improves the ability to represent ambiguous cases,
but it also introduces an additional decision boundary.

Korean error analysis showed that **80.0% of disagreements involved
`Unclear`**, demonstrating that ambiguity handling itself can become a
significant source of annotation variation.

Further refinement of escalation and adjudication rules would help
reduce this uncertainty.

### 15.7 Overall Limitation

The results should therefore be viewed as evidence of a structured
**annotation and quality-assurance methodology**, rather than as a
benchmark for multilingual sentiment classification performance.

The primary value of the project lies in demonstrating how annotation
quality can be **defined, measured, diagnosed, and iteratively
improved**.

---

## 16. Future Improvements

The current project provides a structured foundation for multilingual
annotation and quality assurance. Several improvements could extend the
workflow toward a more production-oriented annotation environment.

### 16.1 Multi-Annotator Evaluation

Future iterations could introduce **multiple independent annotators**
for the same samples.

This would enable:

- Independent annotation before QA
- Formal inter-annotator agreement measurement
- Comparison of annotator-specific disagreement patterns
- More objective evaluation of guideline effectiveness

Formal reliability metrics such as **Cohen's Kappa** or **Fleiss'
Kappa** could also be incorporated depending on the number of
annotators.

### 16.2 Adjudication Workflow

A structured adjudication process could be added for samples where
annotators disagree.

A future workflow could follow:

`Independent Annotation`
→ `Agreement Check`
→ `Disagreement Review`
→ `Adjudication`
→ `Final Gold Label`

This would provide a clearer separation between initial annotations,
QA review, and final accepted labels.

### 16.3 Expanded Multilingual Dataset

The dataset could be expanded beyond the current **900 samples** to
evaluate whether the observed annotation patterns remain stable at
larger scale.

Future datasets could also include additional languages and more
diverse linguistic structures.

### 16.4 Controlled Cross-Language Comparison

A future version could use equivalent or translated content across
languages.

This would make it possible to distinguish more clearly between:

- Language-specific annotation challenges
- Dataset-domain differences
- Translation effects
- Cultural differences in sentiment expression

### 16.5 Enhanced Intensity Guidelines

Because intensity produced more disagreement than polarity, the
Low / Medium / High framework could be further refined.

Potential improvements include:

- More boundary examples
- Language-specific intensity indicators
- Additional contrastive examples
- Explicit escalation rules for borderline cases
- Calibration exercises before full annotation

### 16.6 Automated QA Expansion

The existing Python-based QA workflow could be extended with additional
automated checks, such as:

- Batch-level distribution monitoring
- Unexpected label-shift detection
- Duplicate annotation detection
- Schema validation
- Missing-value alerts
- Automated disagreement reports
- Guideline-version tracking

These checks could help identify annotation drift earlier in larger
labeling projects.

### 16.7 Annotation Tool Integration

Future versions could integrate a dedicated annotation platform such as
**Label Studio** or a comparable labeling environment.

This would allow the workflow to support:

- Annotator assignment
- Annotation history
- Role-based review
- Adjudication
- Progress tracking
- Exportable annotation metadata

### 16.8 Future Direction

The long-term goal would be to evolve the current portfolio workflow
into a scalable annotation pipeline that combines:

**Multilingual Annotation**
→ **Independent Review**
→ **Automated QA**
→ **Agreement Measurement**
→ **Adjudication**
→ **Gold Dataset Creation**

This would extend the project from an individual annotation portfolio
into a workflow closer to a production-scale data quality management
system.

---

## 17. Conclusion

This project demonstrates an end-to-end **multilingual sentiment
annotation and quality assurance workflow** across English, Chinese,
and Korean.

A total of **900 reviews across three languages** were annotated using
a shared polarity and sentiment-intensity framework. Among these,
**460 samples (51.1%)** were included in structured QA procedures using
sampled review, agreement analysis, or ground-truth comparison.

The final evaluation showed that sentiment polarity was relatively
stable, while sentiment intensity and ambiguous label boundaries
required greater interpretive judgment.

Key results include:

- **92.5%** English polarity agreement
- **95.0%** Chinese polarity agreement
- **97.0%** Korean decisive-label agreement
- **73.75%** English intensity agreement
- **76.25%** Chinese intensity agreement
- **80.0%** of Korean disagreements associated with `Unclear`

More importantly, the project demonstrates how disagreement can be used
as a **quality-improvement signal** rather than treated simply as an
annotation error.

Through iterative guideline development, programmatic validation,
disagreement analysis, and multilingual evaluation, the project
established a repeatable workflow for identifying and improving
annotation quality.

Overall, the project demonstrates practical capabilities in
**multilingual annotation, annotation guideline design, quality
assurance, error analysis, data validation, and reproducible workflow
management**.

---

## 18. Acknowledgments

This project was developed for educational and portfolio purposes using
publicly available review datasets.

### Data Sources

- **English & Chinese**
  - Amazon product review datasets accessed through the
    Hugging Face ecosystem.
  - Samples were selected and reorganized for multilingual annotation
    and quality-assurance practice.

- **Korean**
  - Naver Sentiment Movie Corpus (**NSMC**)
  - Korean movie-review data was used for sentiment annotation and
    ground-truth comparison.

### Open-Source Tools

This project was developed using open-source tools and libraries,
including:

- Python
- Pandas
- Jupyter Notebook
- Git

The datasets remain subject to their respective original licenses and
terms of use.

---

### Portfolio Note

This repository is a portfolio project designed to demonstrate
**multilingual data annotation, annotation guideline development,
quality assurance, disagreement analysis, and reproducible data
validation workflows**.

The annotation decisions, QA framework, error analysis, and project
documentation were developed specifically for this portfolio project.
