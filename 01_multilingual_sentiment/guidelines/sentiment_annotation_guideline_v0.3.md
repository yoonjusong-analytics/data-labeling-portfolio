## Sentiment Intensity

Intensity represents the **strength of sentiment expressed in the text**,
not the objective severity of the product, delivery, or service problem.

> **Core Principle**
>
> Problem severity ≠ Sentiment intensity
>
> A serious problem does not automatically receive a High intensity label.
> Annotators should evaluate how strongly the reviewer expresses their
> sentiment through language.

### Low

Assign **Low** when:

- The review mainly reports a negative or positive event factually.
- Emotional language is absent or minimal.
- The sentiment is implied rather than strongly expressed.

**Example**

> "The seeds were spilled out into the shipping envelope."

→ **Negative / Low**

The event is negative, but the reviewer uses little emotional language.

---

### Medium

Assign **Medium** when:

- The sentiment is clearly expressed.
- The reviewer communicates dissatisfaction, criticism, or approval.
- Emotional strength is noticeable but not strongly intensified.
- The review does not contain strong rejection, warning, or repeated
  emotional emphasis.

**Example**

> "Seal was broken. Product looks different than prior purchase."

→ **Negative / Medium**

The dissatisfaction is clear, but the emotional expression remains moderate.

---

### High

Assign **High** when there is clear linguistic evidence of strong sentiment.

Indicators may include:

- Strong emotional expressions
  (`very disappointed`, `terrible`, `worst`, etc.)
- Repeated criticism or praise
- Explicit rejection or strong recommendation
- Purchase refusal
  (`will not buy again`)
- Warning other customers
  (`don't waste your money`)
- Multiple reinforcing statements expressing strong sentiment

**Example**

> "Very disappointed. Will not buy again."

→ **Negative / High**

The reviewer explicitly intensifies dissatisfaction and rejects future purchase.

---

### Decision Rule

When deciding between Medium and High, ask:

**"Is the sentiment itself strongly expressed, or is the underlying problem
simply serious?"**

If the problem is serious but the language remains factual or restrained,
do **not** automatically assign High intensity.

| Version | Change |
|---|---|
| v0.3 | Refined sentiment intensity criteria based on QA findings from English Production Batch 01. Clarified the distinction between problem severity and expressed sentiment intensity. |