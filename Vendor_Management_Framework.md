# Vendor Management & Third-Party Performance Framework
### Enterprise IT Operations | Managing Vendors, Carriers, and MSPs in the Critical Path

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** Service Delivery Managers, Operations Leaders, and Account Managers responsible for managing third-party vendor performance across managed services, carrier relationships, and enterprise technology engagements

---

## Purpose & Scope

When a vendor fails, the customer does not call the vendor. They call the Service Delivery Manager.

That is the reality of vendor management in IT operations. The customer signed a contract with the provider — not with the carrier, not with the platform vendor, not with the MSP in the supply chain. Whatever happens inside that supply chain is the provider's problem to manage and the SDM's responsibility to own.

This framework covers how to classify vendors by risk, how to align vendor commitments to customer-facing SLAs before a contract is signed, how to track and review vendor performance, and how to escalate through a vendor support chain when performance is not meeting the standard. It is written from the perspective of someone who has managed carrier escalations, platform vendor relationships, and third-party MSP performance at scale — and learned what works when the pressure is on.

---

## Section 1 — Why Vendor Management Is a Service Delivery Function

### The SDM Owns the SLA — Regardless of Who Is in the Critical Path

Every customer-facing SLA the SDM signs up for is a commitment the SDM owns. When a vendor is in the critical path of delivering against that SLA — a carrier providing the network, a platform vendor providing the cloud infrastructure, an MSP providing field support — the SDM's SLA commitment does not change. The vendor's performance problem becomes the SDM's performance problem.

This is the part of vendor management that gets misunderstood most often. The instinct when a vendor fails is to point at the vendor and tell the customer "that is outside our control." That instinct is wrong — for two reasons.

First, the customer does not care whose fault it is. They care whether their service is working. "The carrier is at fault" does not restore their system or meet their SLA. It is an explanation, not a solution.

Second, the SDM chose that vendor, or accepted a solution design that included that vendor. The vendor risk was known — or should have been known — before the contract was signed. Treating vendor failure as an external surprise is a failure of vendor management, not just a failure of the vendor.

### What "Owning the Vendor Relationship" Actually Means

Owning the vendor relationship does not mean the SDM personally fixes the vendor's technical problem. It means:

- The SDM knows who to call at the vendor when the support queue is not moving
- The SDM has documented the vendor's escalation path before an incident happens — not during one
- The SDM tracks vendor performance against contracted commitments every month — not just when something goes wrong
- The SDM is the single point of contact between the customer and every vendor in the supply chain — the customer never has to manage a vendor relationship the provider brought into the engagement
- When a vendor fails during a major incident, the SDM manages the vendor bridge while the Incident Commander manages the overall response — two separate roles, not one

### The Commercial Reality

Vendor failure that causes a customer SLA breach creates two problems simultaneously. The first is the customer relationship — the breach needs to be managed, explained, and remediated. The second is commercial — the provider may owe the customer a service credit for the breach, and separately may be owed a credit from the vendor whose failure caused it.

The SDM needs to track both. Customer credits are not absorbed silently — every vendor-caused breach is documented and the vendor credit recovery process is initiated. That process starts with documentation — if the vendor failure is not logged with timestamps, ticket numbers, and impact in ServiceNow, the credit recovery conversation has no foundation.

---

## Section 2 — Vendor Classification Framework

Not all vendors carry the same risk. Managing a critical path carrier with the same intensity as a commodity software license vendor wastes time and misses the risks that actually matter. Classify vendors by their potential impact on the customer SLA and apply oversight proportionally.

### Vendor Tiers

| Tier | Classification | Definition | Examples |
|---|---|---|---|
| **Tier 1** | Critical Path | Vendor failure directly causes customer SLA breach. No workaround available. | Primary network carrier, cloud infrastructure provider, core platform vendor, identity provider |
| **Tier 2** | Supporting | Vendor failure degrades service or increases resolution time but does not immediately breach SLA. Workaround available short-term. | Secondary carrier, monitoring tool vendor, backup platform, regional ISP |
| **Tier 3** | Commodity | Vendor failure has minimal or no direct impact on customer SLA. Easily replaced. | Software licensing, hardware procurement, non-critical tooling |

### Oversight by Tier

| Activity | Tier 1 | Tier 2 | Tier 3 |
|---|---|---|---|
| **Underpinning Contract review** | Before contract signed — mandatory | Before contract signed — mandatory | Not required |
| **Performance tracking in ServiceNow** | Monthly — every metric | Quarterly | As needed |
| **Formal vendor review meeting** | Monthly | Quarterly | Annual or on request |
| **Escalation path documented** | Yes — before first incident | Yes | No |
| **Executive contact identified** | Yes | Yes | No |
| **Credit recovery process defined** | Yes | Yes | No |

### Classifying a New Vendor

When a new vendor is introduced into a service — either at contract design or during an active engagement — classify them before they are activated. Ask three questions:

1. If this vendor goes offline for four hours, does the customer's SLA breach?
2. Is there a viable workaround that keeps the customer operational?
3. How long does the workaround hold before customer impact becomes significant?

If the answer to question one is yes and question two is no — that vendor is Tier 1 regardless of how the sales team described them.

---

## Section 3 — Underpinning Contracts and OLA Alignment

### The Gap That Causes the Most Pain

The most common vendor management failure happens before the engagement goes live — when a customer-facing SLA is committed to without validating that the vendor's underpinning contract (UC) actually supports it.

Example:
- Customer SLA: P1 resolution within 4 hours
- Internal escalation to carrier: 30 minutes to acknowledge
- Carrier UC: 6-hour response SLA for P1 tickets

The math does not work. The provider has committed to a 4-hour resolution but the carrier they depend on has a 6-hour response commitment. The gap is 2 hours before the carrier has even started working the problem.

This gap is discovered in one of two ways — in the design phase during a proper UC review, or during the first major incident when the SDM is staring at a breach they cannot prevent.

The first is a planning conversation. The second is a crisis.

### UC Review Before Contract Signature

Every Tier 1 and Tier 2 vendor involved in a new customer engagement must have their UC reviewed before the customer contract is signed. The review confirms:

| Check | Question |
|---|---|
| **Response alignment** | Does the vendor's response SLA give the SDM enough time to meet the customer's response SLA? |
| **Resolution alignment** | Does the vendor's resolution SLA support the customer's resolution SLA — with time for internal escalation? |
| **Coverage hours** | Does the vendor's support coverage match the customer's coverage requirement? A vendor with business hours support cannot back a 24x7x365 customer SLA. |
| **Escalation path** | Is there an escalation path beyond the support queue? Named contacts, account manager, executive escalation? |
| **Credit structure** | If the vendor misses their UC commitment, what is the credit? Is it sufficient to offset the customer credit owed? |
| **Force majeure** | What events exempt the vendor from their UC? Do those exemptions create unacceptable gaps in the customer SLA? |

If the UC review identifies a gap — the SDM has three options before the contract is signed:

1. **Renegotiate the vendor UC** — get the vendor to tighten their commitment to match the customer requirement
2. **Adjust the customer SLA** — if the vendor cannot support the commitment, the customer SLA needs to reflect that reality
3. **Find an alternative vendor** — if neither option is acceptable, a different vendor is needed

What is not an option is signing the customer contract knowing the UC gap exists and hoping it never surfaces. It will surface. And it will surface at the worst possible moment.

### OLA Alignment

Internal teams that are part of the resolution path need Operational Level Agreements (OLAs) that back the customer-facing SLA just as vendor UCs do. The same alignment check applies:

- Does the internal team's response commitment give enough time to meet the customer SLA?
- Is the internal escalation path documented and current?
- Are on-call schedules maintained and accurate?

An OLA that exists on paper but has not been reviewed in six months is not a functioning OLA — it is a document. Validate OLAs quarterly alongside UC reviews.

---

## Section 4 — Vendor Performance Tracking

### What to Measure

Vendor performance is tracked against the commitments in the UC. Every Tier 1 vendor has a performance record in ServiceNow updated monthly. Every Tier 2 vendor is reviewed quarterly.

| Metric | Definition | Source |
|---|---|---|
| **Response SLA Compliance** | Percentage of tickets acknowledged within the UC response window | ServiceNow — vendor ticket acknowledgment timestamps |
| **Resolution SLA Compliance** | Percentage of tickets resolved within the UC resolution window | ServiceNow — vendor ticket resolution timestamps |
| **Escalation Response Rate** | When the SDM escalated beyond the support queue, how long did it take to get a response? | ServiceNow work notes — escalation log entries |
| **Incident Contribution Rate** | Percentage of customer incidents where the vendor was a contributing factor | ServiceNow — incident records with vendor involvement flag |
| **Credit Recovery Rate** | Percentage of vendor UC breaches where a credit was successfully recovered | Tracked separately — finance and commercial team input |
| **MTTR Impact** | Average additional time added to incident MTTR when the vendor was involved | Calculated from ServiceNow incident and vendor ticket timestamps |

### Tracking in ServiceNow

Every vendor interaction during an incident is logged in ServiceNow — not in an email, not in a personal notebook. The work notes on the incident record are the system of record.

What to log for every vendor interaction:

- Time the vendor ticket was opened
- Ticket number from the vendor's system
- Name of the vendor contact engaged
- Time of each vendor update — what they said, what they committed to
- Time vendor acknowledged the escalation if escalated
- Time vendor confirmed resolution from their side
- Any commitments made by the vendor regarding credits or follow-up

This log is what the credit recovery conversation is built on. No log — no leverage.

### Vendor Ticket Linkage in ServiceNow

Every vendor ticket opened during an incident is linked to the ServiceNow incident record under the Related Records tab. This creates the full audit trail — internal incident record, vendor ticket, timestamps, and resolution sequence — in one place.

When a customer asks "what was the carrier doing during those four hours?" the answer is one click away. When the SDM is pursuing a UC credit, the documentation is already built.

---

## Section 5 — Escalation Through Vendor Support Chains

### The Problem With Standard Support Queues

Standard vendor support queues are designed for average volume, average priority, and average urgency. A Sev 1 incident that is sitting in a standard queue is not being treated as a Sev 1 — it is being treated as the next ticket in line.

The SDM's job during a major incident is to get the vendor off the queue and into the incident. That requires knowing the escalation path before the incident happens.

### Escalation Path Documentation — Before the First Incident

Every Tier 1 vendor must have a documented escalation path on file before the engagement goes live. This document is reviewed and updated quarterly — not when an incident exposes that the contacts are out of date.

For each Tier 1 vendor, document:

| Level | Contact | Phone | Email | Escalation Trigger |
|---|---|---|---|---|
| **L1 — Support Queue** | Support portal / main number | | | First point of contact — all tickets |
| **L2 — Support Manager** | Named contact | | | If L1 has not acknowledged within UC window |
| **L3 — Account Manager** | Named contact | | | If L2 has not escalated within 30 minutes of UC breach |
| **L4 — Executive Contact** | Named VP or Director | | | Sev 1 with no resolution path after 2 hours, or active customer escalation |

The contacts in this table are verified — not copied from a website. Verified means the SDM has called or emailed each contact and confirmed they are the right person for escalation. A contact list that has never been tested is not a contact list — it is a guess.

### How to Escalate Effectively

Escalation that moves has two components — urgency and specificity. Escalation that sits is either too vague to act on or not visible enough to the right person.

**When opening the vendor ticket:**
Do not write a vague subject line. Write the impact.

> "PRIORITY 1 — [Customer Name] — Complete [service] outage — [X] users impacted — SLA breach in [X] minutes"

That subject line gets a different response than "Service issue — please review."

**When escalating beyond the support queue:**
Do not ask if they can look at the ticket. State what you need and when you need it.

> "This is Scott Boehler, Service Delivery Manager at [Company]. We have an active Sev 1 for [Customer Name] — [X] users are down, we are [X] minutes from SLA breach, and your ticket [number] has not been acknowledged in [X] minutes. I need a technical resource engaged on this ticket in the next 15 minutes. Who is escalating this?"

That is not aggressive — it is specific. Specific escalations get faster responses than vague ones.

**When escalating to the account manager:**
The account manager is not a technical resource — they are a relationship and commercial resource. Use them to apply pressure, not to troubleshoot.

> "I need you to escalate ticket [number] internally. We have a Sev 1 active, your support team has not met the UC response window, and we are heading toward a customer SLA breach that will result in a credit claim against your UC. I need this treated as your highest priority right now."

**Document every escalation contact in ServiceNow work notes as it happens** — time, name, what you said, what they committed to. This is the audit trail.

### After the Incident — The Escalation Debrief

After every major incident where a vendor escalation was required, conduct a brief debrief with the vendor account manager. The debrief covers:

- Did the vendor meet their UC commitments during this incident?
- If not — what caused the miss and what is being done about it?
- Is a UC credit owed?
- What process change is the vendor making to prevent recurrence?

This debrief does not need to be long. It needs to happen — and the outcome needs to be documented in ServiceNow.

---

## Section 6 — Vendor Bridge Management During Major Incidents

### Two Roles — Not One

During a major incident involving a vendor, there are two distinct management responsibilities that must not be collapsed into one person:

**Incident Commander (IC)** — owns the overall incident response. Manages the bridge call, drives the resolution timeline, communicates with the customer, declares all-clear.

**Vendor Bridge Owner** — owns the vendor relationship during the incident. Manages the vendor ticket, escalates through the vendor's support chain, provides vendor updates to the IC, logs all vendor interactions in ServiceNow.

When the SDM tries to do both simultaneously — manage the customer bridge and manage the vendor escalation — both suffer. The customer bridge loses focus and the vendor escalation loses momentum.

On Sev 1 incidents, assign a dedicated Vendor Bridge Owner before the main bridge opens. This is typically a senior technical account manager or operations lead — someone who knows the vendor's escalation chain and can work it independently.

### The Vendor Bridge Owner's Responsibilities

- Open the vendor ticket immediately — do not wait for the internal investigation to rule out other causes. Open it in parallel.
- Escalate through the vendor's support chain per the documented escalation path
- Provide the IC with a vendor status update every 30 minutes — same cadence as the internal technical updates
- Log every vendor interaction in ServiceNow work notes in real time
- Do not put the vendor on the main customer bridge unless the IC specifically requests it — vendor calls add noise and confusion to an already complex bridge

### Vendor Update Format to the IC

The Vendor Bridge Owner provides a structured update to the IC every 30 minutes on the main bridge:

> "Vendor update — [time]. Ticket [number] opened at [time]. Current vendor status: [acknowledged / in progress / escalated to L2]. Last vendor contact: [name] at [time] — committed to [update / resolution / escalation] by [time]. Next vendor update due: [time]."

Thirty seconds. The IC has what they need. The vendor bridge owner goes back to working the escalation.

### When the Vendor Needs to Join the Main Bridge

The vendor joins the main bridge only when:

- The IC specifically requests their technical input to progress the resolution
- The vendor has identified the root cause and needs to walk the internal team through the remediation
- The customer has specifically requested vendor participation and the IC has approved it

The vendor does not join the main bridge because it is easier to manage one call instead of two. Two calls is the right structure — the discipline is worth it.

---

## Section 7 — Monthly Vendor Performance Review

### Purpose

The monthly vendor performance review is a structured conversation between the SDM and the vendor account manager. It covers performance data, open issues, and upcoming risks. It is not a complaint session and it is not a vendor sales call.

The SDM brings the data. The vendor explains the data. Both parties agree on action items.

### Who Attends

**Provider side:**
- Service Delivery Manager — owns the meeting and the data
- Technical Account Manager if open technical issues exist

**Vendor side:**
- Account Manager — minimum
- Support Manager or Operations Lead for Tier 1 vendors
- Executive contact for any month where performance was significantly below target

### Agenda — 45 Minutes

| Segment | Time | Content |
|---|---|---|
| **Performance Data Review** | 15 min | SDM presents vendor performance metrics from ServiceNow. Response SLA compliance, resolution SLA compliance, incident contribution rate. Provider's numbers — not the vendor's. |
| **Discrepancy Review** | 10 min | If the vendor's numbers differ from the SDM's numbers — resolve the discrepancy now. Not later. The agreed number is what goes on record. |
| **Open Issues** | 10 min | Any open escalations, unresolved incidents, pending credit claims. Status and owner for each. |
| **Action Items from Last Month** | 5 min | Every action item from last month reviewed. Completed, in progress, or overdue. |
| **New Action Items** | 5 min | Items identified in this meeting. Owner and due date before the meeting closes. |

### Bringing Your Own Data

The SDM brings ServiceNow data to the vendor review — not the vendor's own reporting. This is deliberate.

Vendor-provided performance reports are built on the vendor's measurement methodology. They may exclude tickets that timed out before acknowledgment. They may measure resolution from a different starting point than the SDM measures it. They may present compliance rates that look different from what the SDM experienced.

Neither number is necessarily wrong — they may simply be measuring different things. The discrepancy review resolves which number is correct and why. But the SDM who shows up with only the vendor's numbers has given up the ability to challenge the data.

### When Performance Is Below Target

The same framework that applies to customer service reviews applies to vendor reviews. State the fact first. Do not soften it.

> "Your response SLA compliance for P1 tickets this month was 71% against a contracted 95%. That is a significant miss. Walk me through what caused it."

Then listen. The vendor's explanation is information — about their internal capacity, their escalation process, their tooling. It helps the SDM understand whether this is a one-month anomaly or a trend that requires a more serious conversation.

After the explanation, three questions:

1. Is a UC credit owed for this month's performance?
2. What specific action is the vendor taking to prevent recurrence?
3. What does the SDM need to see next month to confirm the action worked?

All three answers go into the meeting notes and into ServiceNow as action items before the meeting closes.

---

## Section 8 — Common Vendor Management Failures

These are the patterns that allow vendor relationships to drift from managed to unmanaged — and the cost of each.

| Failure | What It Looks Like | What It Costs |
|---|---|---|
| **No UC review before contract signature** | Customer SLA committed without validating vendor can support it | First major incident exposes a gap that was always there — SDM has no remedy |
| **Escalation path not documented before first incident** | SDM scrambles to find the right vendor contact during a Sev 1 | 30–60 minutes lost finding the right person while the customer clock runs |
| **Vendor interactions not logged in ServiceNow** | Verbal updates only — nothing in the incident record | No audit trail for credit recovery — vendor denies the timeline, SDM has nothing to counter with |
| **Vendor performance not tracked monthly** | Issues only reviewed when something goes wrong | Trends are invisible — by the time a pattern is visible it has already cost the customer SLAs |
| **SDM manages vendor bridge AND customer bridge simultaneously** | IC loses control of one or both calls | Vendor escalation slows down, customer communication degrades, MTTR extends |
| **Vendor report accepted without challenge** | SDM presents vendor's own compliance numbers in customer review | Vendor's methodology may not match customer experience — SDM looks like they are managing the vendor's story, not the service |
| **Credit recovery not pursued** | Vendor breach noted, no credit claim initiated | Provider absorbs cost of customer credit without recovering from the vendor that caused it |
| **Contact list not maintained** | Escalation path documented once and never updated | Account manager has changed, executive contact is no longer at the company — discovered during a Sev 1 |
| **No post-incident debrief with vendor** | Incident closed, vendor notified it is resolved, nothing further | Root cause on vendor side is never confirmed — same failure recurs |
| **Treating all vendors the same** | Tier 1 critical path carrier gets same oversight as commodity software license | Risk is not proportional to oversight — critical path failures catch the SDM unprepared |

---

## Appendix — Vendor Management Quick Reference

### Vendor Classification Test
- If this vendor goes offline for 4 hours, does the customer SLA breach? → **Tier 1**
- If this vendor goes offline for 4 hours, does service degrade but not breach? → **Tier 2**
- If this vendor goes offline for 4 hours, is there minimal customer impact? → **Tier 3**

### UC Review Checklist (Before Contract Signature)
- [ ] Vendor response SLA supports customer response SLA
- [ ] Vendor resolution SLA supports customer resolution SLA with time for internal escalation
- [ ] Vendor coverage hours match customer coverage requirement
- [ ] Escalation path beyond support queue documented and verified
- [ ] Credit structure defined and sufficient to offset customer credit exposure
- [ ] Force majeure exemptions reviewed for unacceptable gaps

### Escalation Contact Requirements (Tier 1 Vendors)
- [ ] L1 support queue contact confirmed
- [ ] L2 support manager — named, phone, email
- [ ] L3 account manager — named, phone, email
- [ ] L4 executive contact — named, phone, email
- [ ] All contacts verified — not just copied from a website
- [ ] Reviewed and updated quarterly

### Vendor Incident Log (ServiceNow Work Notes)
- Time vendor ticket opened
- Vendor ticket number
- Name of vendor contact engaged
- Time of each vendor update — what they said, what they committed to
- Time vendor acknowledged escalation
- Time vendor confirmed resolution
- Any credit commitments made

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*When a vendor fails, the customer does not call the vendor. They call you. How prepared you are for that call was decided long before the incident started.*
