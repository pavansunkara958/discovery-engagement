# Success Metrics

Every metric below has a **measured baseline**, a target, and a named owner. A
target without a baseline is a wish, and one without an owner is nobody's.

**Baseline method.** Two weeks of timing across 4 assistants and 180
submissions, plus 6 months of policy-admin history for turnaround and hit rate.
Figures below are that sample, not estimates.

---

## Primary — the pilot is judged on these

| # | Metric | Baseline | Target | Owner |
|---|---|---|---|---|
| P1 | **Assistant touch time per submission** | 52 min | **≤ 30 min** | Priya |
| P2 | **Fields accepted without manual check** | 0% | **≥ 75%** | Marcus |
| P3 | **Submission-to-quote turnaround** (median) | 6.2 days | **≤ 3.5 days** | Priya |
| P4 | **Incompleteness detected on arrival** | 12% | **≥ 90%** | Marcus |

**P2 is the adoption metric and the one to watch.** It is the direct answer to
the tool Meridian already abandoned: not "how accurate is it" but "how much of
its output does a human accept without re-reading". A system can score well on
extraction accuracy and fail here, and if it fails here nothing else matters
because the tool will not be used.

**P4 is where the days come from.** Today an assistant discovers a missing loss
run 20 minutes into keying, then waits 1–2 days for the broker. Detecting it on
arrival removes both the wasted keying and one chase cycle.

---

## Secondary — tracked, not gating

| # | Metric | Baseline | Target | Owner |
|---|---|---|---|---|
| S1 | Time to decline out-of-appetite business | 4–6 days | ≤ 1 day | Priya |
| S2 | Submissions processed per assistant per day | 15 | 22 | Priya |
| S3 | Chase cycles per submission | 1.4 | ≤ 0.8 | Marcus |
| S4 | New-assistant time to productivity | 4 months | 2 months | Priya |

---

## Business outcomes — reported, not gating

| # | Metric | Baseline | Target | Horizon |
|---|---|---|---|---|
| B1 | Hit rate | 14% | 18% | 12 months |
| B2 | Submission capacity without headcount | — | +30% | 6 months |
| B3 | Avoided hires | — | 2 FTE | 12 months |

**These are deliberately not pilot gates.** Hit rate is a lagging indicator
that takes a renewal cycle to move and is confounded by market conditions,
pricing and broker relationships. A one-quarter pilot judged on B1 would be
judged on noise.

The pilot is gated on P1–P4, which move in weeks, and B1–B3 are reported as the
business case for the board.

---

## Quality metrics — the floor, not the goal

| # | Metric | Threshold | Consequence if breached |
|---|---|---|---|
| Q1 | Critical-field extraction accuracy (insured name, address, effective date, limits) | ≥ 98% on accepted fields | halt; these carry policy-issuance risk |
| Q2 | **False-clear rate** — package marked complete but missing a required document | **≤ 2%** | halt |
| Q3 | Traceability — every extracted field cites source document and page | 100% | halt; compliance requirement |
| Q4 | Flag precision — flagged fields that genuinely needed correction | ≥ 60% | review; below this, users start ignoring flags |

**Q2 is the dangerous one.** A false clear sends an incomplete submission to an
underwriter who wastes time and then chases anyway — worse than today, because
today the assistant catches it eventually. **A missed document must fail toward
flagging, never toward clearing.**

**Q4 is what keeps flags credible.** Flag everything and P2 collapses; flag
nothing and Q2 breaks. The system is calibrated between those two failures, and
Q4 is how that calibration is monitored.

---

## The cost of doing nothing

Volume up 40%, headcount flat, two reqs open five months:

| | Annual |
|---|---|
| Clerical time at current volume | ~7,300 assistant-hours |
| At 2026 projected volume | ~10,200 hours |
| Equivalent headcount | ~5 FTE |
| Estimated premium lost to turnaround | $2.1M–$4.4M GWP |

The premium figure is **Tom's estimate and is not defensible** — Meridian does
not track why brokers do not send business. Quantifying it is itself a
deliverable, because a business case built on an unverified number will not
survive the board.

---

## How these get measured

| Metric | Source | Instrumented? |
|---|---|---|
| P1 touch time | timestamped assistant actions | **new — 1 week to build** |
| P2 accept-without-check | UI event: accept vs edit | **new — part of the pilot UI** |
| P3 turnaround | policy admin, already recorded | existing |
| P4 incompleteness on arrival | pilot output vs assistant outcome | new |
| Q1, Q2 | labelled gold set of 150 submissions | **new — see eval split** |

**Three of these do not exist yet.** Building the measurement is part of the
engagement, not a precondition of it — and it is scheduled explicitly, because
a pilot that cannot measure P1 and P2 cannot be judged and will be renewed or
cancelled on opinion.
