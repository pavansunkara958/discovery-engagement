# Scope Document

**Engagement:** Submission Intake Assistant — Pilot
**Customer:** Meridian Specialty (MGA, commercial property & inland marine)
**Duration:** 12 weeks · **Status:** for sign-off

---

## 1 · Objectives

1. Reduce assistant touch time per submission from **52 to ≤ 30 minutes**.
2. Achieve an **accept-without-check rate ≥ 75%** on extracted fields.
3. Detect **≥ 90%** of incomplete submissions **on arrival**, with a false-clear
   rate **≤ 2%**.
4. Reduce median submission-to-quote turnaround from **6.2 to ≤ 3.5 days**.
5. Produce a defensible business case for scaling, with measured figures.

Objectives 1–4 are measurable inside the pilot window. Objective 5 is the
sponsor's actual requirement and depends on 1–4 being instrumented.

---

## 2 · In scope

| Deliverable | Description | Week |
|---|---|---|
| D1 | **Gold set** — 150 labelled submissions, two labellers on a 30-submission overlap | 3 |
| D2 | **Evaluation harness** — per-field recall/precision, accept-without-check, false-clear rate, run on demand | 4 |
| D3 | **Extraction service** — ACORD forms, loss runs, SOVs, supplementals → structured fields with document+page citation | 7 |
| D4 | **Completeness check** — required-document detection per line of business, biased toward flagging | 8 |
| D5 | **Assistant review UI** — field-level accept/edit, uncertainty flags, source-document pane | 9 |
| D6 | **Policy admin integration** — write extracted fields, respecting rate limits | 10 |
| D7 | **Audit record** — per submission: inputs, outputs, citations, human edits, 7-year retention | 10 |
| D8 | **Operational instrumentation** — touch time, accept rate, turnaround, chase cycles | 5 |
| D9 | **Pilot report** — measured results against P1–P4, business case, scale recommendation | 12 |

**Pilot population:** 2 assistant pods (6 assistants), inland marine and
commercial property, ~40 submissions a day.

---

## 3 · Out of scope

Explicitly, and with the reason — so each is a decision rather than an omission.

| Not in scope | Why | Revisit |
|---|---|---|
| Automated appetite decisions | Compliance requires a human-recorded declination; saves 2 min, not 31 | Phase 2 |
| Automated quoting or binding | Priya's hard constraint | Not planned |
| Loss-run analysis and summarisation | This is the judgement half; errors here are the ones nobody catches | Phase 3 |
| Automated broker chase emails | Small increment once completeness is trusted | Phase 2 |
| Broker submission portal | 18-month change programme against 200 independent brokers | Not an AI project |
| Policy admin migration | "A two-year project, and it isn't this one" — Dana Osei | Not planned |
| Any line of business beyond the two piloted | Different required-document sets | Phase 2 |

---

## 4 · Constraints

### Hard — non-negotiable

| # | Constraint | Source |
|---|---|---|
| C1 | No automated declination, quote or bind. Advisory output only. | Sofia, Priya |
| C2 | Every extracted field cites source document and page. | Sofia |
| C3 | No customer data to a third-party model provider without signed DPA and zero-retention. | Sofia, Raj |
| C4 | Runs in Meridian's AWS account, in-region. Data does not leave. | Dana, Raj |
| C5 | Audit records retained 7 years. | Sofia |
| C6 | No policy admin migration; integrate via existing REST API. | Dana |

### Practical

| # | Constraint | Impact |
|---|---|---|
| C7 | One engineer, half-time (Wei Chen) | **the real capacity limit** — not the model |
| C8 | Policy admin API is rate-limited and metered above a threshold | batch writes; budget the calls |
| C9 | No existing labelled data | ~3 days of Marcus's time, scheduled in D1 |
| C10 | Mailbox access requires CISO approval, not yet started | **critical path** |
| C11 | Result needed inside one quarter for the Q3 board | fixes the 12-week window |

---

## 5 · Risks

| # | Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|---|
| R1 | **Security review of mailbox scope delays start** | High | **High** | Start week 1, before technical work. Fallback: shared-drive drop for the pilot. |
| R2 | **Assistants don't adopt it** — the tool that already failed here | **High** | Medium | Accept-without-check is a gate, not a report. Marcus co-designs the UI. Week-8 stop condition. |
| R3 | Gold-set labelling slips; Marcus has a day job | High | Medium | Book the time with Priya in writing; 100 submissions is a usable floor |
| R4 | Loss-run format variety defeats extraction | Medium | Medium | Stratify the gold set by carrier format; flag unknown formats rather than guessing |
| R5 | Wei Chen is pulled onto other work | High | Medium | Named in the scope with an agreed allocation; escalation path to Dana |
| R6 | False clears exceed 2% | **High** | Low | Bias to flagging; hard halt condition |
| R7 | Sponsor judges the pilot on hit rate | Medium | **High** | Agreed in writing now (see eval_customer_split.md) |
| R8 | Model provider unavailable or changes behaviour | Medium | Medium | Pin versions; the harness detects regressions before users do |

**R1 and R2 are the ones that decide this engagement.** R1 is the only item on
the critical path that cannot be compressed by working harder. R2 has already
happened once at this customer, which makes it the highest-prior risk in the
list.

---

## 6 · Stakeholders and commitments

| Name | Role | Committed |
|---|---|---|
| Tom Whitfield | CUO, sponsor | funding; Q3 board slot |
| Priya Raman | VP Underwriting Ops, process owner | pilot pods; assistant time; weekly review |
| Marcus Bell | Senior UW Assistant, user lead | ~3 days labelling; UI co-design; week-8 verdict |
| Dana Osei | Head of IT & Data | system access; Wei Chen at 50% |
| Wei Chen | Platform engineer | integration, 50% for 12 weeks |
| Sofia Marchetti | Compliance | requirements sign-off; audit review at week 10 |
| Raj Patel | CISO | **mailbox scope approval — week 1, not yet started** |

**Two team leads have not been interviewed.** They set daily work allocation,
and a change they did not agree to will not hold. Scheduled before sign-off.

---

## 7 · Governance

- **Weekly** — 30 min with Priya: metrics against P1–P4, blockers.
- **Week 4, 8, 12** — checkpoint with Tom against the stop conditions.
- **Week 10** — compliance review with Sofia against C1–C5.
- **Stop conditions** are in `eval_customer_split.md` and are binding on both
  sides. Either party may invoke them.

A stop condition that only the vendor can invoke is not a stop condition.
