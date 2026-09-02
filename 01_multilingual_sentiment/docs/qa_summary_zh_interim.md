# Chinese Sentiment Annotation — Interim QA Summary

## 1. Overview

This document summarizes the interim quality assurance (QA) review
conducted for the Chinese sentiment annotation dataset.

The purpose of the QA process was to evaluate annotation consistency,
identify recurring disagreement patterns, and refine the annotation
guidelines based on observed errors.

### QA Scope

- Language: Chinese (ZH)
- Dataset: Amazon Product Reviews
- Annotation task: Sentiment Polarity + Sentiment Intensity
- Reviews evaluated: 80
- Review range: 30–109
- Polarity labels: Positive / Negative
- Intensity labels: Low / Medium / High

---

## 2. QA Results

| Metric | Result |
|---|---:|
| Reviews evaluated | 80 |
| Exact matches | 59 |
| Reviews requiring correction | 21 |
| Exact agreement | 73.75% |
| Sentiment agreement | 95.00% |
| Intensity agreement | 76.25% |

The results show that sentiment polarity classification was relatively
stable, while intensity classification was the primary source of
annotation disagreement.

---

## 3. Intensity Disagreement Analysis

A total of 19 intensity corrections were identified during QA.

| Initial Label | Final Label | Count | Share |
|---|---|---:|---:|
| Low | Medium | 9 | 47.4% |
| Medium | High | 6 | 31.6% |
| High | Medium | 3 | 15.8% |
| Medium | Low | 1 | 5.3% |
| **Total** | | **19** | **100%** |

### Key Finding

15 of the 19 intensity corrections involved increasing the initial
intensity level.

**Intensity underestimation rate among intensity corrections: 78.9%.**

This indicates a systematic tendency during initial annotation to assign
sentiment intensity below the level determined during QA.

---

## 4. Major Disagreement Patterns

### 4.1 Low vs. Medium

The most frequent disagreement occurred between Low and Medium intensity.

Initial annotations sometimes classified clear dissatisfaction as Low
when the issue had a meaningful impact on the overall user experience.

Examples of signals supporting Medium intensity include:

- Expectations were not met
- Perceived poor value for money
- Significant loss of interest
- Noticeable usability problems
- Multiple moderate complaints

### 4.2 Medium vs. High

The second major disagreement involved distinguishing Medium from High.

Initial annotation sometimes relied too heavily on emotional language
when determining intensity.

QA showed that practical issue severity should also be considered.

Examples supporting High intensity include:

- Product failure shortly after use
- Major physical damage
- Missing pages or unusable content
- Serious delivery or refund failure
- Strong purchase warnings
- Severe service failures

Therefore:

> Sentiment intensity should reflect both expression strength and issue severity.

---

## 5. Polarity Disagreement Analysis

Only 4 of the 80 reviewed annotations required a change in sentiment
polarity.

**Sentiment agreement: 95.00%.**

The main polarity disagreements occurred in reviews containing mixed
positive and negative opinions.

### Key QA Principle

When both positive and negative opinions are present:

1. Identify the primary evaluation target.
2. Determine the dominant overall sentiment.
3. Consider the reviewer's final conclusion.
4. Prioritize an explicit final evaluation when the reviewer changes
   their opinion.

---

## 6. Key Edge Cases

### Mixed Sentiment

A review may contain both positive and negative statements.

When a Mixed category is unavailable, the dominant overall evaluation
should determine the final polarity.

### Sentiment Reversal

Some reviewers change their evaluation after additional product use or
reading.

When an explicit final evaluation is provided, the latest overall
judgment should take precedence over the initial reaction.

### Product vs. Service Sentiment

Some reviews positively evaluate the product while strongly criticizing
delivery, customer service, or the platform.

The annotation should reflect the dominant sentiment expressed in the
review rather than automatically prioritizing product sentiment.

---

## 7. Guideline Improvement

The interim QA findings were incorporated into
`sentiment_annotation_guideline_v0.3.md`.

The primary refinement focused on:

- Clearer Low / Medium / High boundaries
- Issue severity as an intensity signal
- Mixed-sentiment decision rules
- Sentiment reversal handling
- Dominant-sentiment evaluation

---

## 8. QA Workflow

The annotation quality process follows an iterative workflow:

**Manual Annotation  
→ QA Review  
→ Disagreement Identification  
→ Error Pattern Analysis  
→ Guideline Refinement  
→ Subsequent Annotation**

This iterative approach is designed to improve annotation consistency
across subsequent batches.

---

## 9. Interim Conclusion

The Chinese annotation QA demonstrated high consistency in sentiment
polarity classification, with a 95.00% agreement rate.

Intensity classification showed greater ambiguity, with a 76.25%
agreement rate. The primary systematic pattern was intensity
underestimation, accounting for 78.9% of intensity corrections.

Based on these findings, the annotation guideline was refined to provide
clearer intensity boundaries and to incorporate practical issue severity
alongside linguistic expression strength.