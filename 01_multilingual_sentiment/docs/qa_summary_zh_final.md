# Chinese Sentiment Annotation – Final QA Report

## 1. Project Scope

This report summarizes the final quality assurance process for the Chinese
sentiment annotation dataset.

The project involved manually annotating **300 Chinese Amazon reviews** using
two annotation dimensions:

- **Sentiment:** Positive / Negative
- **Intensity:** Low / Medium / High

The annotation process included initial labeling, interim QA review, error
analysis, guideline refinement, iterative review, and final dataset validation.

A formal interim QA review was conducted on **80 reviews (indices 30–109)**.
Both initial and final labels for this QA sample were preserved, allowing
reproducible measurement of annotation agreement and correction patterns.

The findings from this review were used to refine the annotation guideline
from its initial version to **v0.3**, with particular attention to intensity
classification and mixed-sentiment cases.


## 2. Final Dataset Quality

The final Chinese annotation dataset contains **300 completed reviews**.

| Quality Check | Result |
|---|---:|
| Total reviews | 300 |
| Completed annotations | 300 |
| Completion rate | 100% |
| Missing sentiment labels | 0 |
| Missing intensity labels | 0 |
| Duplicate review IDs | 0 |
| Invalid label values | 0 |

The final dataset therefore passed all structural and label-schema validation
checks.

### Final Label Distribution

#### Sentiment

| Label | Count | Share |
|---|---:|---:|
| Negative | 188 | 62.7% |
| Positive | 112 | 37.3% |

#### Intensity

| Label | Count | Share |
|---|---:|---:|
| High | 167 | 55.7% |
| Medium | 109 | 36.3% |
| Low | 24 | 8.0% |

Negative reviews accounted for approximately two-thirds of the annotated
sample. High-intensity labels were also relatively common, representing more
than half of the dataset.

These distributions describe only the selected 300-review sample and should
not be generalized to Chinese-language Amazon reviews overall.

## 3. Formal QA Results

A formal QA review was conducted on **80 reviews (indices 30–109)**.
For this sample, both the initial annotation and the final QA-reviewed labels
were preserved, allowing the agreement metrics to be reproduced.

| QA Metric | Result |
|---|---:|
| Reviews evaluated | 80 |
| Exact matches | 59 |
| Reviews requiring correction | 21 |
| Exact agreement | 73.75% |
| Sentiment agreement | 95.00% |
| Intensity agreement | 76.25% |
| Correction rate | 26.25% |

### Agreement Analysis

Sentiment polarity showed a high level of consistency, with **95.00% agreement**.
Only 4 of the 80 reviews required a sentiment correction.

Intensity classification was more challenging. **19 reviews required an
intensity correction**, resulting in an agreement rate of **76.25%**.

The difference between sentiment and intensity agreement indicates that the
main annotation challenge was not determining whether a review was broadly
positive or negative, but deciding **how strongly the sentiment should be
classified**.

### Reproducibility Note

These agreement metrics apply specifically to the **80-review formal QA sample**
and should not be interpreted as agreement results for the full 300-review
dataset.

Initial labels for the later annotation batches were not preserved in a
separate immutable QA table. Therefore, post-guideline agreement rates are not
reported as formal metrics in this report.

## 4. Error Pattern Analysis

The formal QA review identified **intensity classification** as the primary
source of annotation disagreement.

### Intensity Correction Patterns

Among the 80 reviews evaluated, **19 intensity labels** required correction.

| Initial → Final | Count | Share |
|---|---:|---:|
| Low → Medium | 9 | 47.4% |
| Medium → High | 6 | 31.6% |
| High → Medium | 3 | 15.8% |
| Medium → Low | 1 | 5.3% |
| **Total** | **19** | **100%** |

Of the 19 intensity corrections, **15 (78.9%) were upward adjustments**.

This pattern revealed a systematic tendency to underestimate sentiment
intensity during the initial annotation stage.

A major source of disagreement was the distinction between **emotional
expression** and **practical issue severity**. Some reviews used relatively
calm language while describing serious problems such as product failure,
major damage, or inability to perform the product's core function.

These cases demonstrated that emotional wording alone was not sufficient for
determining intensity.


### Sentiment Correction Patterns

Sentiment polarity was considerably more stable.

Only **4 of the 80 reviews** required a sentiment correction:

| Initial → Final | Count |
|---|---:|
| Negative → Positive | 2 |
| Positive → Negative | 1 |
| Mixed → Negative | 1 |
| **Total** | **4** |

Most sentiment disagreements involved reviews containing both positive and
negative signals.

These cases showed that polarity decisions should consider the **dominant
overall evaluation** and the **primary evaluation target**, rather than simply
counting positive and negative expressions.


### Primary QA Finding

The QA analysis identified two main sources of annotation inconsistency:

1. **Intensity underestimation**
   - Severe practical problems were sometimes assigned Low or Medium intensity
     because the reviewer did not use strongly emotional language.

2. **Mixed-sentiment ambiguity**
   - Reviews sometimes evaluated multiple targets, such as the product,
     packaging, delivery, seller, or secondary features.

These findings became the main basis for refining the annotation guideline.

## 5. Guideline Refinement

Based on the error patterns identified during formal QA, the annotation
guideline was refined to **version 0.3**.

The revision focused primarily on improving consistency in intensity
classification and resolving ambiguous mixed-sentiment cases.


### 5.1 Expression Strength + Issue Severity

The most important change was the introduction of two dimensions for
determining sentiment intensity:

**Intensity = Expression Strength + Issue Severity**

Intensity should not be determined solely by emotional wording.

A review may receive **High intensity** even when the language is relatively
calm if the reported issue has substantial practical impact.

Examples include:

- Failure of the product's core function
- Product becoming unusable shortly after purchase
- Severe physical damage or missing essential components
- Food, hygiene, or safety-related concerns
- Major service failures with significant customer impact

At the same time, the presence of a defect alone does not automatically justify
a High label. Minor cosmetic problems or limited inconveniences should normally
remain Low or Medium unless accompanied by strong sentiment expression or
substantial practical impact.


### 5.2 Mixed-Sentiment Decision Rule

When both positive and negative signals appear in the same review, the final
label should reflect the **dominant overall evaluation**.

The following factors are considered:

1. Overall evaluation
2. Final conclusion
3. Primary evaluation target
4. Practical impact of the reported issue

This prevents secondary complaints, such as packaging or delivery problems,
from automatically overriding a clearly positive evaluation of the core
product.


### 5.3 Primary Evaluation Target

Reviews may contain sentiment toward multiple targets, including:

- Product
- Seller
- Delivery service
- Packaging
- Platform
- Secondary product features

The annotation should prioritize the target that most strongly determines the
reviewer's overall evaluation.

This rule helps distinguish dissatisfaction with the core product from
complaints about secondary aspects of the purchase experience.


### 5.4 Sentiment Reversal

When a review changes direction during the text, the **latest explicit overall
evaluation** should generally receive greater weight.

For example, an initially positive description followed by a clear negative
final conclusion should normally be classified according to the final
evaluation.


### 5.5 Non-Evaluative and Ambiguous Reviews

Some reviews contain little direct product evaluation, such as:

- Expectations before actual use
- Plot or content summaries
- General reflections
- Copied or irrelevant text

Under the current binary sentiment schema, these cases must still be mapped to
the closest Positive or Negative label using the lowest reasonable intensity.

These cases were identified as candidates for future schema expansion using
labels such as **Neutral, Mixed, Unclear, or Non-evaluative**.


## 6. Key Findings

The QA process produced five key findings that informed the final annotation
workflow and guideline design.

### 6.1 Sentiment Was More Stable Than Intensity

Sentiment polarity achieved **95.00% agreement**, compared with **76.25% for
intensity** in the formal QA sample.

This indicates that determining whether a review was broadly positive or
negative was relatively consistent, while deciding the appropriate sentiment
strength was more challenging.


### 6.2 Initial Annotation Tended to Underestimate Intensity

Of the 19 intensity corrections, **15 (78.9%) were upward adjustments**.

This showed that severe product or service issues were sometimes assigned
insufficient intensity when reviewers expressed dissatisfaction in relatively
calm language.

The finding directly motivated the addition of **issue severity** to the
intensity decision criteria.


### 6.3 Mixed Reviews Required Target-Aware Decisions

Reviews containing both positive and negative signals were a major source of
polarity ambiguity.

Reliable classification required identifying the:

- Dominant overall evaluation
- Final conclusion
- Primary evaluation target
- Practical impact of the reported issue

This was particularly important when the core product evaluation differed from
comments about packaging, delivery, price, or secondary features.


### 6.4 Severity Rules Required Balanced Application

Adding issue severity improved the treatment of serious functional problems,
but later review also revealed the risk of assigning High intensity too
aggressively whenever a defect was present.

The final decision principle therefore became:

**High intensity = strong sentiment expression OR substantial practical impact**

Minor defects and limited inconveniences should not automatically receive a
High label.


### 6.5 The Binary Schema Has Practical Limitations

Some reviews contained weak, mixed, ambiguous, or non-evaluative content that
did not fit naturally into a binary Positive / Negative schema.

Future annotation projects could improve representational accuracy by
considering additional labels such as:

- Neutral
- Mixed
- Unclear
- Non-evaluative

This would reduce forced polarity decisions and provide clearer handling of
borderline cases.

## 7. Limitations & Future Improvements

Although the final dataset passed all structural validation checks, several
limitations were identified during the annotation and QA process.


### 7.1 Limited Formal QA Coverage

Formal agreement metrics were calculated from **80 reviews (indices 30–109)**,
for which both initial and final labels were preserved.

The remaining reviews were reviewed iteratively, but their first-pass labels
were not stored in a separate immutable QA dataset.

As a result, this project does not report a formal pre- and post-guideline
agreement comparison across the full 300-review dataset.


### 7.2 Annotation History Was Not Fully Preserved

QA corrections were incorporated directly into the working annotation dataset
during later annotation stages.

For future projects, the first-pass annotation should be preserved separately
before QA corrections are applied.

A more robust QA audit table should include:

- `review_id`
- `initial_sentiment`
- `initial_intensity`
- `final_sentiment`
- `final_intensity`
- `sentiment_changed`
- `intensity_changed`
- `qa_reason`
- `guideline_version`

This would allow annotation changes to be traced and agreement metrics to be
reproduced at any stage of the project.


### 7.3 Binary Sentiment Schema

The Positive / Negative schema required some ambiguous or non-evaluative
reviews to be assigned a polarity even when neither label represented the
content precisely.

Future schema design could consider additional categories such as:

- Neutral
- Mixed
- Unclear
- Non-evaluative

These categories could reduce forced classification and improve annotation
precision for borderline cases.


### 7.4 Single-Annotator QA Design

The annotations and QA decisions in this portfolio were produced within a
single annotation workflow rather than through independent multi-annotator
labeling.

Therefore, the reported agreement metrics represent **first-pass versus
QA-reviewed label consistency**, not inter-annotator agreement.

A future project could include two or more independent annotators and measure
metrics such as **Cohen's Kappa** or **Krippendorff's Alpha**.


### 7.5 Future QA Workflow

Based on the lessons from this project, a stronger annotation workflow would
follow:

**First-pass Annotation → Immutable Label Storage → Independent QA →
Error Categorization → Guideline Revision → Re-annotation →
Post-Revision Agreement Measurement → Final Validation**

This structure would make the annotation process more reproducible,
auditable, and suitable for larger-scale labeling projects.

## 8. Conclusion

This project completed the manual sentiment annotation and QA review of
**300 Chinese Amazon reviews**, producing a fully labeled dataset with no
missing labels, duplicate review IDs, or invalid label values.

The formal QA sample showed that sentiment polarity was relatively stable,
while intensity classification was the primary source of disagreement.
Error analysis revealed a systematic tendency to underestimate intensity,
particularly when severe product or service issues were expressed without
strong emotional language.

These findings were used to refine the annotation guideline to version 0.3.
The revised framework incorporated **expression strength, issue severity,
dominant overall evaluation, primary evaluation target, and sentiment
reversal** into the decision process.

The project also demonstrated that annotation quality is not achieved through
label completion alone. A reliable annotation workflow requires:

**Annotation → QA → Error Analysis → Guideline Refinement → Validation**

The most important outcome of the project was therefore not only the completed
300-review dataset, but also the development of a more consistent,
explainable, and reproducible annotation decision process.

Future iterations should preserve immutable first-pass labels, introduce
independent multi-annotator QA, and evaluate whether additional sentiment
categories can better represent ambiguous and non-evaluative reviews.