## Polarity Edge Cases

The annotation schema uses binary polarity labels:

- **Positive**
- **Negative**

Reviews may contain mixed, balanced, or limited information.
Annotators should not create additional polarity labels such as
Mixed, Neutral, or Unclear when the dominant sentiment can
reasonably be determined.

### Core Principle

> **Mixed content does not necessarily require a Mixed label.**

Polarity represents the **dominant evaluative direction** of the review.

When both positive and negative statements are present, consider:

1. The primary issue being evaluated
2. The relative weight of positive and negative evidence
3. The reviewer's overall conclusion
4. Behavioral signals such as return, replacement, rejection,
   recommendation, or purchase avoidance

### Mixed Content

A review may acknowledge positive qualities while still expressing
an overall negative evaluation.

**Example**

> "Disappointed in the sizing ... other than that it is a very nice garment."

→ **Negative / Medium**

The garment receives positive feedback, but the primary evaluation
concerns dissatisfaction with incorrect sizing.

---

### Neutral-Looking Reviews

Balanced or restrained language does not automatically indicate
neutral sentiment.

If the reviewer reports product failure, dissatisfaction, return,
replacement, or recommends an alternative, determine whether these
signals establish a dominant polarity.

**Example**

> "It worked as intended for several months but then it sorta just died out."

→ **Negative / Medium**

The review acknowledges previous functionality but ultimately evaluates
product failure.

---

### Short or Apparently Unclear Reviews

Short text should not automatically be treated as unclear.

If sufficient evaluative evidence exists, assign polarity normally.

**Example**

> "See through - the thin material."

→ **Negative / Low**

The text is brief but contains a clear negative evaluation of product quality.

### Polarity Decision Rule

When polarity appears ambiguous:

**Step 1 — Identify evidence**

Separate positive and negative statements.

**Step 2 — Identify the main evaluation target**

Determine what aspect of the product or experience drives the review.

**Step 3 — Examine the conclusion**

Look for dissatisfaction, praise, return, replacement, recommendation,
rejection, or purchase avoidance.

**Step 4 — Assign dominant polarity**

Choose **Positive** or **Negative** based on the overall evaluative direction.

### Important Distinctions

- Mixed content ≠ Mixed label
- Balanced language ≠ Neutral sentiment
- Short text ≠ Unclear sentiment

| Version | Change |
|---|---|
| v0.4 | Added dominant polarity rules and edge-case guidance for mixed, neutral-looking, and short/unclear reviews based on QA findings from English Production Batch 03. |