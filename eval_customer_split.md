# What the Customer Wants vs How We Evaluate Success

The customer's language and the evaluation harness are not the same thing, and
pretending otherwise is how engagements end in an argument about whether they
worked.

This document is the translation, and it is agreed **before** the build.

---

## The gap, line by line

| What the customer says | What they mean | How we actually evaluate it |
|---|---|---|
| "AI that underwrites submissions" | I want my team's time back | touch time P1, fields accepted without check P2 — **no underwriting decisions in scope** |
| "It should be accurate" | I shouldn't have to check it | **accept-without-check rate**, not extraction accuracy |
| "Faster turnaround" | brokers get answers in 3 days | median submission-to-quote P3, measured in the policy admin system |
| "Catch missing documents" | stop wasting a keying pass | recall on required-document detection, Q2 false-clear ≤ 2% |
| "Improve hit rate" | write more of what we quote | **not a pilot gate** — lagging, confounded, reported as business case |
| "Don't make compliance angry" | every decision explainable in 18 months | 100% of fields cite document + page; audit record per submission |

---

## The three translations that matter

### 1 · "Accurate" → accept-without-check rate

The sponsor asks for accuracy. The user asked for something different and more
specific:

> "If it tells me it's 90% sure, that's useless. Tell me which three fields to
> look at." — Marcus Bell

Meridian abandoned an 80%-accurate OCR tool. **It did not fail on accuracy.** It
failed because eight correct fields indistinguishable from two wrong ones meant
checking cost more than typing.

So the primary quality metric is not "what fraction of fields are right" but
**"what fraction can a human accept without re-reading"**. A system at 85%
accuracy that reliably flags its own uncertainty beats one at 95% that does not,
and a naive accuracy target would have selected the wrong system.

### 2 · "AI that underwrites" → AI that reads

Tom asked for automated underwriting. Sofia requires a human to record every
declination and Priya will not accept automated quoting.

**The stated ask is incompatible with the room's own constraints**, and saying
so in week one is the job. What is left after the constraints is extraction and
completeness checking — which is also where 31 of the 52 minutes are, so the
customer loses nothing they actually valued.

### 3 · "Improve hit rate" → don't gate on hit rate

Tom's success metric is B1. It moves over a renewal cycle, it is confounded by
pricing and market conditions, and the pilot is funded for one quarter.

Gating on it would mean the pilot is judged on noise. We gate on the leading
indicators that are plausibly causal (P1–P4) and report B1 as the business case.
**Agreed in writing now**, because "but hit rate didn't move" is otherwise a
perfectly reasonable thing for a sponsor to say in month three.

---

## The evaluation harness

Assertions, not impressions.

### Gold set

**150 real submissions**, stratified across broker, document type and
completeness, labelled field-by-field by Marcus and one other assistant.

| Property | Why |
|---|---|
| Two labellers on a 30-submission overlap | gives an inter-annotator agreement figure — without it, "the system disagrees with the label" cannot be distinguished from "the label is debatable" |
| Held-out slice never used for prompt iteration | otherwise the score measures memorisation and rises while nothing improves |
| Versioned with the system | a score without its dataset version is not a measurement |
| Labelling effort budgeted: ~3 days of Marcus's time | Dana flagged this; it is a real schedule cost, not a rounding error |

### Metrics

| Layer | Metric | Threshold |
|---|---|---|
| Extraction | per-field recall and precision on the gold set | critical fields ≥ 98% on accepted |
| Extraction | **accept-without-check rate** | ≥ 75% |
| Completeness | recall on missing required documents | ≥ 90% |
| Completeness | **false-clear rate** | **≤ 2%** |
| Calibration | flag precision | ≥ 60% |
| Traceability | fields citing document + page | 100% |
| Operational | touch time, turnaround, chase cycles | see success_metrics.md |

### What is deliberately *not* evaluated by a model

Extraction correctness is checked against human labels, not judged by another
model. These are questions with definite answers — did the system read
$5,000,000 where the document says $5,000,000 — and asking a probabilistic
instrument a question that has an exact answer produces a suite that is
*usually* right. Usually is not a standard you can ship an insurance system
against.

---

## Agreed failure conditions

Stated now, so "it didn't work" is a fact rather than an opinion:

1. Accept-without-check below 60% at week 8 → **stop.** The tool will not be
   adopted, and the earlier that is known the cheaper it is.
2. False-clear rate above 2% → **halt** until fixed. Worse than the status quo.
3. Touch time not below 40 minutes by week 10 → the time saving is not real.
4. Marcus and the assistant pod decline to use it in week 12 → it failed,
   whatever the metrics say.

**Condition 4 is the real one.** Meridian has already deployed a tool that
scored acceptably and was abandoned. A metric nobody acts on is not a result.
