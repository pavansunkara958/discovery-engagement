# Interview Findings

Five interviews, 45 minutes each, conducted over four days. Notes are grouped by
persona. Direct quotes are marked; everything else is paraphrase.

**Method note.** Every interview ended with the same two questions: *"walk me
through the last one of these you did"* and *"what would you do with the time if
this went away?"* The first produces concrete steps instead of a description of
the process as it is supposed to work. The second separates a real bottleneck
from an annoyance — if nobody can name what they would do with the recovered
time, the problem is not costing what they think it is.

---

## 1 · Priya Raman — VP Underwriting Operations *(Department Leader)*

**Pain points**

- Submission-to-quote turnaround averages **6.2 business days**. Broker
  expectation is 3. "We lose business we never knew we were competing for."
- Volume is up 40% year on year; headcount is flat. Two underwriting assistant
  reqs were approved and have been open five months.
- **Declinations take as long as quotes.** A submission outside appetite still
  consumes 4–6 days before anyone says no. "That's the part that makes me
  angry. We spend our scarcest resource deciding not to do business."

**Objectives**

- Turnaround to 3 days or better without adding headcount.
- Decline out-of-appetite business within 24 hours.
- Take on 2025's volume growth with the team she has.

**Workflow challenges**

- Submissions arrive as broker emails with 4–15 attachments: ACORD forms, loss
  runs, SOVs, supplementals. No standard naming, no standard order.
- Assistants key data into the policy admin system by hand, then chase missing
  documents by email. A chase cycle costs 1–2 days per round trip.

**Constraints**

- Will not accept anything that binds or quotes without an underwriter.
- Budget approval requires a business case by end of quarter.

> "I don't want AI underwriting. I want my underwriters underwriting instead of
> reading PDFs."

---

## 2 · Marcus Bell — Senior Underwriting Assistant *(End User)*

Six years in the role. Processes 12–18 submissions a day.

**Pain points**

- Roughly **70% of his day is data entry and document chasing**, not judgement.
- Loss runs are the worst: "Every carrier formats them differently. I've seen
  the same carrier change format twice in a year."
- Missing-document chasing is the single biggest time sink. He estimates **1 in
  3 submissions arrives incomplete**, and he often does not notice until he is
  halfway through keying.

**Objectives**

- Stop retyping data that already exists in a document.
- Know a submission is incomplete **before** starting work on it, not after.

**Workflow challenges**

- Walked through his last submission: 14 attachments, 52 minutes total. **31 of
  those minutes were extraction and completeness checking**; 21 were judgement —
  reading the loss history and forming a view.
- Appetite checking is informal. He knows the rules by memory. New assistants
  take four months to get there and escalate constantly until they do.

**Constraints and concerns**

- Sceptical, specifically: "We had an OCR tool two years ago. It was right maybe
  eight times in ten, and checking the two took longer than typing all ten."
  **He will not use something he has to check line by line.**
- Wants to see what the system was unsure about, not just what it decided.

> "If it tells me it's 90% sure, that's useless. Tell me which three fields to
> look at."

*This is the most important constraint in the engagement. A tool that is
accurate but unverifiable gets abandoned, and this team has already abandoned
one.*

---

## 3 · Dana Osei — Head of IT & Data *(IT)*

**Pain points**

- The policy admin system is a vendor-hosted product with a documented REST
  API, but writes are rate-limited and the vendor charges per API call above a
  threshold.
- No document store worth the name — attachments live in mailbox folders and a
  shared drive.
- Two prior AI pilots stalled, both because "nobody owned the integration after
  the demo."

**Objectives**

- Anything new must run in their existing AWS account, in their VPC.
- Must not require a policy-admin migration. "That's a two-year project and it
  isn't this one."

**Workflow challenges**

- Mailbox access is possible via Microsoft Graph; security will need to approve
  the scope.
- No existing labelled data. "If you need a training set, someone has to make
  it, and that someone is Marcus."

**Constraints**

- Data must not leave the AWS account or the region.
- One engineer, half-time, for integration support. Named: Wei Chen.

> "I'll support it if it's a service with an owner. I won't support a notebook."

---

## 4 · Tom Whitfield — Chief Underwriting Officer *(Executive Sponsor)*

**Pain points**

- Hit rate is 14%; the market comparable is 18–22%. He attributes much of the
  gap to speed. "Brokers send to whoever answers first."
- Cannot quantify how much business is lost to turnaround, and that gap is
  itself a problem for him.

**Objectives**

- Hit rate to 18% within a year.
- Submission capacity up 30% without headcount.
- A defensible business case for the board in Q3.

**Constraints**

- **Any system touching underwriting decisions needs a documented audit trail.**
  "If a regulator asks why we declined, 'the model said so' is not an answer."
- Will fund a pilot, not a platform. Wants a result inside one quarter.

> "Show me it works on a hundred real submissions and I'll fund the rest."

---

## 5 · Sofia Marchetti — Compliance Officer *(Compliance & Security)*

**Pain points**

- Multi-state licensing means declination reasons must be defensible and
  consistent. Inconsistent declinations are an unfair-discrimination exposure.
- Loss runs and SOVs contain third-party commercial data under broker
  agreements that restrict downstream use.

**Objectives**

- Every automated determination traceable to the document and page it came from.
- No customer data used to train a vendor's model.

**Constraints — non-negotiable**

- No data to a third-party model provider without a signed DPA and zero-retention.
- **Appetite decisions are advisory only.** A human records the declination.
- Audit records retained seven years.

> "I'm not against this. I'm against not being able to explain it eighteen
> months later when someone asks."

---

## Cross-cutting observations

**1 · Everyone described the same bottleneck in different words.** Priya called
it turnaround, Marcus called it data entry, Tom called it hit rate, Dana called
it integration. All four are downstream of the same thing: a submission takes
half an hour of clerical work before anyone applies judgement to it.

**2 · The stated ask and the real constraint point in opposite directions.**
Tom asked for "AI that underwrites". Sofia requires that a human record every
declination, and Priya will not accept automated quoting. **The room does not
actually want what the sponsor asked for**, which is worth surfacing early
rather than discovering at the compliance review.

**3 · The prior failure is the most useful data point in the engagement.** The
OCR tool failed not because it was inaccurate but because it was *unverifiable*
— 80% accuracy with no indication of which 20% was wrong made checking cost
more than doing. Any proposal that cannot address that directly will be
rejected by the people who have to use it, regardless of what it scores.

**4 · There is no labelled data and no obvious owner for creating it.** This is
a schedule risk and it surfaced only because Dana raised it unprompted.
