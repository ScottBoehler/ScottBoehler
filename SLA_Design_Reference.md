# SLA Design Reference Guide
### Enterprise IT Operations | Design, Implementation & Ongoing Management

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** All customer-facing and internal service level agreements across managed services and IT operations

---

## Purpose & Scope

An SLA is a commitment — not a target, not a guideline, not a best effort. When you design an SLA, you are making a promise the business has to keep. When you manage an SLA, you are either keeping that promise or explaining why you didn't.

This guide covers both sides. How to design SLAs that are achievable and meaningful before a contract is signed, and how to manage, report, and remediate against those SLAs once they are active. Getting the design wrong makes the management impossible. Getting the management wrong makes the design irrelevant.

All SLA records, timers, and reporting are maintained in ServiceNow.

---

## Section 1 — SLA Design Fundamentals

### The Three Questions Every SLA Must Answer

Before writing a single SLA metric, answer these three questions. If you cannot answer all three, the SLA is not ready to be committed to.

**1. Can we actually deliver this?**
Not "can we deliver this on a good day" — can we deliver this consistently, across shifts, across vendors, when things go wrong. An SLA that requires perfect execution every time is not an SLA — it is a liability.

**2. How will we measure it?**
Every SLA metric must be measurable from an objective data source. ServiceNow timestamps, monitoring tool alerts, call records. If measurement requires human judgment or manual tracking, it will be disputed. Design for objective measurement from day one.

**3. What happens when we miss it?**
Define the consequence before the contract is signed. Financial credits, service credits, escalation rights, termination clauses. A customer who discovers the remedy for SLA misses only after you've missed them is a customer who feels deceived.

### SLA vs. OLA vs. UC

These three terms are often used interchangeably. They are not the same thing.

| Term | Full Name | Definition | Parties Involved |
|---|---|---|---|
| **SLA** | Service Level Agreement | External commitment to the customer defining what service performance the provider will deliver | Provider ↔ Customer |
| **OLA** | Operational Level Agreement | Internal agreement between teams within the provider organization that supports delivery of the SLA | Internal team ↔ Internal team |
| **UC** | Underpinning Contract | Agreement with a third-party vendor or supplier whose performance is required to meet the SLA | Provider ↔ Vendor |

**Critical design principle:** Every customer-facing SLA must be backed by OLAs and UCs that collectively cover the committed performance. If your SLA promises 4-hour resolution but your vendor UC only commits to 6-hour response, you have a gap before you've signed anything.

---

## Section 2 — SLA Design Process

### Step 1 — Understand the Customer's Business Requirements

Do not start with metrics. Start with the customer's business. What does downtime actually cost them? What is the business impact of a 4-hour outage vs. a 1-hour outage? What are their peak periods? What systems are truly mission-critical vs. important but not critical?

This conversation shapes everything. A customer whose billing system processes transactions 24x7 needs different SLAs than one whose billing runs in a nightly batch. The same metric means different things to different businesses.

Questions to answer before designing a single SLA:

- What are the customer's core business hours vs. extended hours vs. 24x7 requirements?
- Which systems or services are mission-critical — complete outage has immediate revenue impact?
- What is their tolerance for degraded performance vs. complete outage?
- Have they had SLA disputes with previous providers? What caused them?
- What are their regulatory or compliance requirements that affect uptime?

### Step 2 — Define the Service Scope

An SLA cannot be written until the service scope is clearly defined. Disputes about SLA performance almost always trace back to ambiguity about what was and was not in scope.

For each service covered by the SLA, define:

- **What is included:** Specific systems, applications, infrastructure components, geographies
- **What is excluded:** Components outside the provider's control, customer-managed systems, scheduled maintenance windows
- **Dependencies:** Third-party services, customer-provided infrastructure, vendor components
- **Maintenance windows:** Agreed scheduled maintenance periods exempt from SLA measurement

Document the scope in ServiceNow at the time the SLA record is created. Both parties must confirm the scope before SLA timers begin.

### Step 3 — Design the Metrics

#### Availability SLA

Availability is the most common SLA metric and the most commonly misunderstood. The formula matters.

```
Availability % = ((Agreed Service Time - Downtime) / Agreed Service Time) × 100
```

Key design decisions:

| Decision | Options | Recommendation |
|---|---|---|
| **Measurement period** | Monthly / Quarterly / Annual | Monthly — easier to track and remediate |
| **Agreed service time** | 24x7 / Business hours only / Custom | Define explicitly — "business hours" without definition will be disputed |
| **Downtime definition** | Full outage only / Degraded performance threshold | Define the degraded performance threshold — latency, error rate, transaction failure rate |
| **Exclusions** | Scheduled maintenance / Force majeure / Customer-caused outages | Document all exclusions explicitly |

**Common availability targets and what they actually mean:**

| SLA | Downtime per Month | Downtime per Year | Appropriate For |
|---|---|---|---|
| 99.9% ("three nines") | ~43 minutes | ~8.7 hours | Standard enterprise applications |
| 99.95% | ~22 minutes | ~4.4 hours | High-importance applications |
| 99.99% ("four nines") | ~4.3 minutes | ~52 minutes | Mission-critical / revenue-generating systems |
| 99.999% ("five nines") | ~26 seconds | ~5.3 minutes | Carrier-grade / life-safety systems |

Do not commit to four or five nines unless your infrastructure, staffing model, and vendor agreements can actually support it. Over-committing on availability is one of the fastest ways to destroy a customer relationship.

#### Response and Resolution SLAs

| Metric | Definition | Design Considerations |
|---|---|---|
| **Initial Response Time** | Time from incident reported to first acknowledgment | Measured from ticket creation in ServiceNow — not from when the customer called |
| **Time to Resolution** | Time from incident reported to service restored | Define "restored" — fully restored to pre-incident state, or acceptable workaround in place? |
| **Time to Workaround** | Time from incident reported to acceptable workaround in place | Valuable for complex incidents where full resolution takes longer |
| **Update Frequency** | How often the customer receives status updates during an active incident | Define interval and communication channel — email, portal update, phone call |

#### Tiered SLA Design

Not all incidents deserve the same response. SLA tiers align response commitments to business impact.

| Priority | Business Impact | Response | Workaround | Resolution |
|---|---|---|---|---|
| **P1 / Critical** | Complete outage — multiple users or systems, revenue impact | 15 minutes | 2 hours | 4 hours |
| **P2 / High** | Significant degradation — core functionality impaired | 30 minutes | 4 hours | 8 hours |
| **P3 / Medium** | Partial impact — workaround available | 2 hours | 8 hours | 24 hours |
| **P4 / Low** | Minimal impact — no workaround needed | 4 hours | N/A | 72 hours |

Adjust these targets based on the customer's specific business requirements from Step 1. These are starting points, not defaults.

### Step 4 — Define Remedies

SLA remedies must be defined before signing. The customer needs to know what recourse they have, and the provider needs to know the financial exposure of missing commitments.

Common remedy structures:

| Remedy Type | How It Works | Considerations |
|---|---|---|
| **Service Credits** | Customer receives a credit against their monthly invoice for each SLA miss | Cap credits at a percentage of monthly contract value — typically 10-30% |
| **Credit Accumulation** | Credits accumulate over a measurement period and are applied at period end | Simpler administration but delays customer visibility |
| **Termination Rights** | Customer may terminate the contract if SLA misses exceed a defined threshold | Define the threshold clearly — number of misses per period, or cumulative downtime |
| **Root Cause Requirement** | Provider must deliver a root cause analysis within a defined timeframe after each miss | Valuable — keeps the provider accountable beyond the financial remedy |

### Step 5 — Validate Against Operations

Before the SLA is committed to, validate it against the actual operational model. This is the step most commonly skipped — and the one that causes the most pain.

Validation checklist:

- [ ] OLAs are in place with all internal teams required to meet this SLA
- [ ] UCs with all relevant vendors cover the committed response and resolution times
- [ ] Staffing model supports 24x7 coverage if SLA requires it
- [ ] Monitoring and alerting is in place to detect breaches before they exceed SLA windows
- [ ] ServiceNow SLA timers are configured and tested for this customer and priority level
- [ ] Escalation path is defined and communicated to all required teams
- [ ] Maintenance window process is agreed and documented

If any item on this checklist is not confirmed, the SLA should not be signed. Signing an SLA without completing this validation is not a sales win — it is a future incident report.

---

## Section 3 — SLA Implementation in ServiceNow

Once an SLA is agreed and the contract is signed, it is configured in ServiceNow before the service goes live.

### ServiceNow SLA Configuration

| Configuration Item | Location in ServiceNow | Notes |
|---|---|---|
| **SLA Definition record** | Service Level Management → SLA Definitions | One record per SLA metric — response time, resolution time, update frequency |
| **SLA workflow** | SLA Definition → Workflow tab | Defines what happens at 50%, 75%, 90%, and 100% of SLA window |
| **Warning notifications** | SLA workflow → notification steps | Configure alerts at 75% of window — gives team time to act before breach |
| **Customer account mapping** | SLA Definition → Account field | Maps SLA to specific customer — ensures correct SLA fires for each account |
| **Priority mapping** | SLA Definition → Conditions | Ensures correct SLA fires based on incident priority (P1, P2, P3, P4) |
| **Exclusion schedules** | SLA Definition → Schedule field | Maps maintenance windows and business hours exclusions |
| **SLA dashboard** | Service Level Management → SLA Dashboard | Real-time view of all active SLA timers — current status, time remaining |

### Testing Before Go-Live

Never activate SLA timers in ServiceNow without testing first. Create test incidents for each priority level and confirm:

- Correct SLA fires for each priority
- Warning notifications trigger at 75% of window
- Exclusion schedules apply correctly during maintenance windows
- Reports pull correct data from the SLA module

A misconfigured SLA timer in ServiceNow will give you inaccurate compliance data and miss breach alerts. Find it in testing, not in a customer review.

---

## Section 4 — SLA Ongoing Management

### Monthly SLA Review Process

SLA management is not a passive activity. It requires active monthly review against every customer commitment.

**Monthly review agenda:**

1. Pull SLA compliance report from ServiceNow for the measurement period
2. Identify all breaches — document root cause for each
3. Identify all near-misses (resolved within final 10% of SLA window)
4. Calculate credit exposure if applicable
5. Prepare customer-facing SLA report
6. Identify corrective actions for recurring breach categories
7. Confirm all corrective actions from previous month are closed

### Customer SLA Reporting

Customers should never discover an SLA breach before the provider tells them. Monthly SLA reports go to the customer within the first week of the following month.

**SLA Report Structure:**

```
MONTHLY SERVICE LEVEL REPORT
Customer: [Name]
Reporting Period: [Month, Year]
Prepared by: [Service Delivery Manager Name]

SUMMARY
Overall SLA Compliance: [X]%
Target: [X]%
Status: [Met / Missed]

SLA PERFORMANCE BY METRIC
[Metric]     Target     Actual     Status
Availability   99.9%     [X]%      [Green/Red]
P1 Response    15 min    [X] min   [Green/Red]
P1 Resolution   4 hrs    [X] hrs   [Green/Red]

INCIDENTS DURING PERIOD
Total Incidents: [X]
Sev 1/P1: [X]
Sev 2/P2: [X]
SLA Breaches: [X]

BREACH DETAIL (if applicable)
Incident: [Ticket number]
Date: [Date]
Metric Missed: [Response / Resolution]
Target: [X] / Actual: [X]
Root Cause: [Summary]
Corrective Action: [Summary]
Credit Applied: [$ amount if applicable]

UPCOMING MAINTENANCE WINDOWS
[List scheduled maintenance for the following month]

SERVICE DELIVERY MANAGER CONTACT
[Name] | [Email] | [Phone]
```

### SLA Breach Remediation

When a breach occurs, the response matters as much as the breach itself.

1. **Acknowledge immediately** — do not wait for the customer to find it
2. **Explain what happened** — plain language, no jargon, no excuses
3. **Apply the contracted remedy** — credits processed without the customer having to ask
4. **Deliver the corrective action** — what specifically prevents this from happening again
5. **Follow up** — confirm the corrective action was implemented and is working

A customer who experiences an SLA breach and receives a proactive call, a clear explanation, the contracted credit, and a credible prevention plan is often more satisfied than one who never experienced a breach. How you handle failures defines the relationship more than the failures themselves.

### SLA Renegotiation Triggers

SLAs should be reviewed and potentially renegotiated when:

- The customer's business requirements change significantly
- The service scope changes — new systems, new geographies, new volumes
- Consistent SLA compliance above 99%+ for 12 months — consider tightening targets
- Consistent near-misses or breaches — targets may need adjustment or investment required
- New technology or tooling changes what is operationally achievable
- Contract renewal — use as an opportunity to align SLAs to current operational reality

---

## Section 5 — Common SLA Design Mistakes

These are the mistakes that create problems after the contract is signed. Know them before you sign.

| Mistake | Why It Happens | What It Costs |
|---|---|---|
| **Committing to targets not validated against operations** | Sales pressure to win the deal | Immediate breach after go-live — destroys the relationship at the start |
| **Vague scope definitions** | Assumed mutual understanding | Disputes about what is and isn't covered — every breach becomes a negotiation |
| **No maintenance window definition** | Overlooked during design | Planned maintenance counts against availability — inflates breach count |
| **Missing OLA/UC alignment** | Internal teams not consulted during design | Provider commits to 4-hour resolution but vendor only commits to 6-hour response |
| **Remedy caps not defined** | Assumed standard contract language covers it | Uncapped credit exposure — a bad month becomes a financial crisis |
| **No degraded performance definition** | Assumed "outage" was self-evident | Customer claims SLA breach during slowdown — no objective measure to reference |
| **No customer-caused exclusion** | Assumed it was implied | Provider penalized for outages caused by customer's own infrastructure or actions |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*An SLA that gets signed fast and falls apart in delivery is not a win — it is a countdown. Design it right before the ink dries.*
