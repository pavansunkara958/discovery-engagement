# Simulated Discovery Engagement — Meridian Specialty

A forward-deployed discovery engagement: five stakeholder interviews translated
into one scoped, measurable, twelve-week pilot.

| Deliverable | Document |
|---|---|
| Stakeholders and who can stop this | [stakeholder_map.md](stakeholder_map.md) |
| Five persona interviews | [interview_findings.md](interview_findings.md) |
| The bottleneck, and what was rejected | [bottleneck.md](bottleneck.md) |
| Measurable outcomes with baselines | [success_metrics.md](success_metrics.md) |
| Customer language vs evaluation harness | [eval_customer_split.md](eval_customer_split.md) |
| Objectives, deliverables, constraints, risks | [scope_document.md](scope_document.md) |
| Objective conditions for "done" | [exit_criteria.md](exit_criteria.md) |

---

## Customer context

**Meridian Specialty** is a managing general agent writing commercial property
and inland marine for mid-market accounts. ~$180M gross written premium, 45
people in underwriting operations, ~200 independent broker partners.

Submissions arrive as broker emails with 4–15 attachments — ACORD forms, loss
runs, statements of values, supplementals — in no standard format or order. An
underwriting assistant reads them, keys the data into a vendor-hosted policy
admin system, chases whatever is missing, and passes the file to an underwriter.

Submission volume is up **40% year on year**. Headcount is flat and two approved
requisitions have been open five months. Median submission-to-quote turnaround
is **6.2 business days** against a broker expectation of 3. Hit rate is **14%**
against a market comparable of 18–22%.

The CUO opened the engagement asking for "AI that underwrites submissions".

---

## Executive summary

**The bottleneck is not underwriting. It is the half hour of clerical work that
happens before any underwriting starts.**

A timed walkthrough of a real submission: 52 minutes, of which **31 were
extraction and completeness checking** and 21 were judgement. Across 11
assistants at ~15 submissions a day, that is roughly **28 hours a day** spent
reading PDFs. Every other complaint in the interviews — turnaround, hit rate,
declination speed, "70% of my day is data entry" — is downstream of it.

**Scope: extraction and completeness checking. No appetite decisions, no
quoting, no binding.**

Three reasons, in order of importance:

1. **Errors are recoverable.** A wrong field surfaces immediately to the person
   who can fix it. A wrong appetite decision may surface to nobody, and carries
   unfair-discrimination exposure.
2. **The room's own constraints select it.** Compliance requires a
   human-recorded declination; operations will not accept automated quoting.
   What survives those constraints is exactly the work that consumes the time.
3. **It is measurable this quarter.** Touch time and turnaround move in weeks.
   Hit rate takes a renewal cycle, and the pilot is funded for one.

### The reframe that matters

Meridian deployed an OCR tool two years ago at ~80% accuracy and abandoned it.
It did not fail on accuracy — **it failed because it was unverifiable.** Eight
correct fields indistinguishable from two wrong ones made checking cost more
than typing.

> "If it tells me it's 90% sure, that's useless. Tell me which three fields to
> look at." — Marcus Bell, Senior Underwriting Assistant

So the primary quality target is **not extraction accuracy**. It is the share of
fields a human accepts without re-reading, with everything else flagged
explicitly. A system at 85% accuracy that knows which 15% to flag beats one at
95% that does not — and a naive accuracy target would have selected the wrong
system.

That reframe came from a user's scepticism, not a sponsor's goal, which is the
argument for interviewing past the person holding the budget.

### Targets

| Metric | Baseline | Target |
|---|---|---|
| Assistant touch time | 52 min | ≤ 30 min |
| Fields accepted without check | 0% | ≥ 75% |
| Turnaround (median) | 6.2 days | ≤ 3.5 days |
| Incompleteness caught on arrival | 12% | ≥ 90% |
| False-clear rate | — | ≤ 2% (hard halt) |

Hit rate is **reported, not gated** — lagging, confounded, and agreed in writing
now so it cannot become the argument in month three.

### The two risks that decide this

**Security review of mailbox access.** The only item on the critical path that
cannot be compressed by working harder, and it had not started at the time of
discovery. Scheduled for week 1, ahead of any technical work.

**Adoption.** This customer has already abandoned one tool that met its numbers.
Accept-without-check is therefore a gate rather than a report, the user lead
co-designs the interface, and there is a stop condition at week 8.

---

## What this engagement deliberately did not do

It did not scope what the sponsor asked for. "AI that underwrites" is
incompatible with constraints that compliance and operations stated in their
first conversations — and saying so in week one, with the evidence, is the job.

What is left after the constraints happens to be where the time actually goes,
so the customer loses nothing they valued. **That is usually how it works out,
and it is only visible if you interview past the budget holder.**
