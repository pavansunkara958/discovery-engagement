# Exit Criteria

Objective conditions that end the engagement. Each is measurable, has an owner,
and is verifiable by the customer without taking our word for it.

**Both parties can invoke these.** A stop condition only the vendor can call is
not a stop condition.

---

## Exit A — Success

All of the following, verified at week 12:

| # | Condition | Threshold | Verified by |
|---|---|---|---|
| A1 | Assistant touch time | ≤ 30 min median over ≥ 200 submissions | Priya, from instrumentation |
| A2 | Accept-without-check rate | ≥ 75% over the final 2 weeks | Marcus, from UI events |
| A3 | Incompleteness detected on arrival | ≥ 90% recall | gold set + live outcomes |
| A4 | False-clear rate | ≤ 2% | gold set |
| A5 | Critical-field accuracy on accepted fields | ≥ 98% | gold set |
| A6 | Median turnaround | ≤ 3.5 days | policy admin records |
| A7 | Traceability | 100% of fields cite document + page | Sofia, week-10 review |
| A8 | Audit record complete and retained | passes compliance review | Sofia |
| A9 | **The pods choose to keep using it** | stated by Marcus and both team leads | Priya |
| A10 | Handover complete | runbook, harness, gold set, named owner | Dana |

**A9 is not a formality.** Meridian has already deployed a tool that met its
numbers and was abandoned. A pilot that satisfies A1–A8 and fails A9 has not
succeeded — it has produced a report.

**A10 is what separates a pilot from a demo.** Dana has watched two AI pilots
stall after the demo because nobody owned them afterwards. Without a named
owner, a runbook and a re-runnable evaluation harness, the engagement has
delivered a thing that will rot.

---

## Exit B — Early stop, no fault

Invoked by either party. The work to date is documented and handed over.

| # | Condition | Checked at |
|---|---|---|
| B1 | Accept-without-check below 60% | week 8 |
| B2 | Touch time not below 40 min | week 10 |
| B3 | False-clear rate above 2% and not resolved within 2 weeks | any |
| B4 | Critical-field accuracy below 95% on accepted fields | any |
| B5 | Mailbox access not approved and fallback not viable | week 3 |
| B6 | Gold set below 100 labelled submissions | week 5 |
| B7 | Wei Chen's allocation drops below 30% for 2 consecutive weeks | any |

**B1 is the most likely and the most useful.** Failing at week 8 costs a third
of the engagement; discovering the same thing at week 12 costs all of it and the
sponsor's confidence in a second attempt.

**B5, B6 and B7 are customer-side conditions**, and they are stated here
deliberately. A pilot starved of access, labels or engineering time will fail,
and it is fairer to everyone to name that in advance than to deliver a bad
result and litigate why.

---

## Exit C — Immediate halt

Stop the same day. Resume only after written sign-off from Sofia.

| # | Condition |
|---|---|
| C1 | Any automated declination, quote or bind reaches a customer or broker |
| C2 | Customer data leaves the AWS account or the region |
| C3 | Data sent to a model provider without a signed DPA and zero-retention |
| C4 | An extracted field written to the policy admin system with no source citation |
| C5 | A regulator or broker raises a question the audit record cannot answer |

These map one-to-one onto constraints C1–C5 in the scope document. They are the
conditions under which the engagement stops being a quality problem and starts
being a compliance incident.

---

## What "done" produces

On Exit A:

1. **Pilot report** — measured results against P1–P4, with baselines and
   method, not estimates.
2. **Business case** — cost per submission before and after, projected capacity,
   avoided hires. Includes an honest note on the premium-loss figure, which
   Meridian cannot currently substantiate.
3. **Scale recommendation** — which lines of business next, what phase 2 costs,
   what phase 2 should *not* attempt.
4. **Operational handover** — runbook, evaluation harness, gold set, named
   owner, and the stop conditions carried forward into production.

On Exit B, items 1 and 4 still ship. **What was learned and what it cost is
worth more than nothing**, and it is what makes a second attempt cheaper rather
than politically impossible.

---

## The condition that is not on this list

There is no criterion for "the model is good enough". That is deliberate.

Every condition above is about what the system *lets a person do* — accept a
field without checking, find a gap on arrival, answer a regulator eighteen
months later, choose to keep using it. Model quality is an input to those, never
the thing being judged.

The tool Meridian abandoned would have passed a model-quality bar. It failed
every criterion on this page.
