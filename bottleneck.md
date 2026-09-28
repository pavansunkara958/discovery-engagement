# The Bottleneck

## Selected

> **Submission intake — extraction and completeness checking, before an
> underwriter sees the file.**

Specifically: reading 4–15 broker attachments, extracting the fields needed to
open a submission, and determining whether the package is complete enough to
underwrite.

**Not** appetite decisions. **Not** quoting. **Not** loss analysis.

---

## Why this one

### It is where the time actually goes

Marcus's last submission took 52 minutes: **31 minutes extraction and
completeness checking, 21 minutes judgement.** Across 11 assistants at ~15
submissions a day, the clerical half is roughly **28 hours a day of effort**
spent on work that produces no underwriting insight.

Every other pain in the interviews sits downstream of it:

| Stated pain | Who | Actually caused by |
|---|---|---|
| 6.2-day turnaround | Priya | 31 clerical minutes + 1–2 day chase cycles |
| Hit rate 14% vs 18–22% | Tom | brokers going to whoever answers first |
| "70% of my day is data entry" | Marcus | this, directly |
| Declines cost as much as quotes | Priya | incompleteness found late, appetite checked late |

Fixing intake moves all four. Fixing any of the others moves only itself.

### The consequences of error are recoverable

This is the property that makes it the right *first* bottleneck, and it is
worth more than the time saving.

| | Intake extraction | Appetite decision | Quoting |
|---|---|---|---|
| Wrong output | a field to correct | a declined submission | mispriced risk on the books |
| Caught by | the assistant, immediately | maybe nobody | an actuary, months later |
| Regulatory exposure | none | unfair discrimination | rate filing |
| Reversible | yes | awkwardly | no |

An extraction error surfaces in seconds to the person who can fix it. That
makes it a safe place to put a system that will sometimes be wrong — which any
such system will be.

### It is measurable this month

Turnaround, touch time and chase cycles are all already recorded or trivially
instrumented. Tom's hit-rate target is a **lagging** indicator that takes a
renewal cycle to move; a pilot funded for one quarter cannot be judged on it.

Intake gives a leading indicator that moves in weeks and is plausibly causal
for the lagging one.

### It is bounded by the constraints everyone already stated

- Sofia requires a human to record declinations → intake makes no declinations.
- Priya will not accept automated quoting → intake does not quote.
- Sofia requires page-level traceability → extraction naturally cites a source
  page; an appetite judgement does not.

**The constraints select the scope.** This is the only candidate that satisfies
all of them without negotiation.

---

## What was considered and rejected

**Automated appetite decisioning** — the sponsor's stated ask. Rejected: it
requires the human-in-the-loop that Sofia mandates and Priya wants, so the time
saved is the *decision*, which is 2 minutes, not the *reading*, which is 31.
It carries unfair-discrimination exposure, and it depends on extraction working
first. It is the right phase 2 and the wrong phase 1.

**Loss-run analysis and summarisation** — genuinely hard and genuinely valuable.
Rejected: it is the 21 minutes of judgement, not the 31 of clerical work, and
errors there are exactly the ones nobody catches. Wrong risk profile for a first
engagement.

**Broker portal to replace email submissions** — would eliminate the problem at
source. Rejected: an 18-month change-management programme against 200
independent brokers who have no incentive to adopt it. Not an AI project and
not this quarter.

**Policy admin migration** — Dana's words: "a two-year project, and it isn't
this one."

**Chasing missing documents automatically** — tempting, and half of it comes
free: knowing a submission is incomplete *on arrival* removes the wasted keying
before the gap is noticed. Sending the chase email is a small increment on top
and sits naturally in phase 2, once the completeness check is trusted.

---

## The constraint that shapes the solution

From Marcus, and it outranks accuracy:

> "If it tells me it's 90% sure, that's useless. Tell me which three fields to
> look at."

Meridian already abandoned an 80%-accurate OCR tool. It did not fail on
accuracy — it failed because **checking cost more than doing.** Eight correct
fields you cannot distinguish from two wrong ones is worth less than five
fields flagged as certain and five flagged for review.

So the target is not "highest extraction accuracy". It is **the highest
proportion of fields the assistant can accept without checking**, with
everything else routed to them explicitly. A system at 85% accuracy that knows
which 15% to flag beats one at 95% that does not.

That reframing is the single most important output of this discovery, and it
came from a user's scepticism rather than a sponsor's goal.
