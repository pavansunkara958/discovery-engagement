# Stakeholder Map

**Customer:** Meridian Specialty — a managing general agent writing commercial
property and inland marine for mid-market accounts. ~$180M gross written
premium, 45 people in underwriting operations, submissions arrive by broker
email.

---

## Who matters, and for what

| Stakeholder | Role | Cares about | Can they stop this? |
|---|---|---|---|
| **Tom Whitfield** | Chief Underwriting Officer | hit rate, capacity, board business case | **Yes — funds it** |
| **Priya Raman** | VP Underwriting Operations | turnaround, throughput, team capacity | **Yes — owns the process** |
| **Marcus Bell** | Senior Underwriting Assistant | not retyping data, not checking line by line | **Yes, informally — non-adoption kills it** |
| Underwriting assistants (×11) | End users | same as Marcus | collectively yes |
| Underwriters (×14) | End users, downstream | quality of what reaches them | indirectly |
| **Dana Osei** | Head of IT & Data | integration burden, ownership, hosting | **Yes — controls access** |
| Wei Chen | Platform engineer | the actual integration work | no, but is the only capacity |
| **Sofia Marchetti** | Compliance Officer | auditability, declination consistency, data use | **Yes — veto** |
| Raj Patel | CISO *(not yet interviewed)* | mailbox scope, data residency, vendor review | **Yes — veto** |
| Broker partners (×~200) | External | speed of response | no |

---

## By category

### Executive sponsors

**Tom Whitfield (CUO)** — economic buyer. Frames the problem as hit rate; will
fund a pilot, not a platform; wants a board-ready result in one quarter.

**Priya Raman (VP Underwriting Ops)** — the day-to-day sponsor and the one who
will live with the outcome. In practice she is the more important of the two:
Tom decides whether it is funded, Priya decides whether it is used.

### Department leaders

Priya, plus two team leads not separately interviewed who manage the assistant
pods. Both should be interviewed before the scope is signed — **they set the
daily work allocation, and a change they did not agree to will not hold.**

### End users

Eleven underwriting assistants and fourteen underwriters. The assistants are
where the time goes and where adoption is decided.

**Marcus Bell is the swing vote.** Six years in the role, trusted by the pod,
and already burned by one failed OCR tool. He will not use something he has to
check line by line. Winning him wins the group; losing him means the tool sits
unused while the metrics say it works.

### IT

**Dana Osei** gates access to the mailbox and the policy admin system, and has
watched two AI pilots stall after the demo. Her condition is ownership: "I'll
support a service with an owner, not a notebook."

**Wei Chen** is the single named engineering resource, half-time. He is the
project's real capacity constraint, not the model.

### Security

**Raj Patel (CISO)** — *interviewed second-hand through Dana; a direct
conversation is scheduled before scope sign-off.* Controls Microsoft Graph
mailbox scope approval, third-party vendor review, and data residency.

**This is the largest open risk in the map.** Mailbox access is a broad
permission and a security review of it has not started. A four-week security
review discovered in week three is how a one-quarter pilot becomes two.

### Compliance

**Sofia Marchetti** — veto authority, and the only stakeholder whose
requirements are genuinely non-negotiable: human-recorded declinations,
document-and-page traceability, no data to a third-party model without a DPA
and zero retention, seven-year audit retention.

She is not an obstacle. She stated her conditions clearly in the first
conversation, which is more than most sponsors do.

---

## What this map tells you

**Three people can stop this, and only one of them is the sponsor.** Tom funds
it; Sofia and Raj can veto it; Marcus can quietly fail to adopt it. A plan that
optimises only for the funder fails on one of the other three.

**The security conversation is the critical path.** Everything else can proceed
in parallel; mailbox scope approval cannot be compressed and has not started.
It is the first thing to schedule, ahead of any technical work.

**The economic buyer and the process owner want different things.** Tom wants
hit rate, which is a lagging indicator he cannot currently attribute. Priya
wants turnaround, which is leading, measurable this month, and plausibly causal
for Tom's number. **Scope to Priya's metric and report to Tom's** — otherwise
success takes a year to demonstrate, and the pilot is only funded for a quarter.
