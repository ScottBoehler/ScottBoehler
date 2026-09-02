# Service Transition & New Customer Onboarding Playbook
### Enterprise IT Operations | From Signed Contract to Steady-State Service

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** August 2026  
**Applies To:** Service Delivery Managers, Operations Leaders, and Implementation Teams responsible for transitioning new customers from contract signature to steady-state managed service delivery

---

## Purpose & Scope

A signed contract is not a delivered service. Everything that happens between the signature and the first steady-state service review — the kickoff, the knowledge transfer, the tooling configuration, the go-live, the hypercare period — determines whether the customer relationship starts on solid ground or starts with a deficit the SDM spends the next year recovering from.

Most onboarding failures are not technical. The technical implementation team delivers what they were asked to deliver. The failures happen in the gaps — unclear scope, incomplete knowledge transfer, SLAs that were never properly baselined, escalation paths that were never agreed, and a customer who expected something different from what was delivered.

The Service Delivery Manager owns the transition. Not the project manager, not the implementation team, not the account executive who closed the deal. The SDM is accountable for the customer's experience from the day the contract is signed to the day steady-state service is confirmed. Everything in this playbook reflects that accountability.

This playbook is organized around four phases — Pre-Transition, Active Transition, Go-Live, and Steady-State Handoff. Each phase has defined activities, owners, and exit criteria. Nothing moves to the next phase without the SDM confirming the exit criteria are met.

---

## Section 1 — Purpose & Philosophy

### What Service Transition Actually Is

Service transition is the process of moving a customer from their current state — self-managed IT, a previous provider, or a legacy internal team — to a new managed service model. It is not just a technical migration. It is a complete transfer of operational accountability — processes, tooling, knowledge, relationships, and commitments.

A technical migration moves data, configurations, and systems. A service transition moves the operating model. Both have to happen. The SDM owns the second one.

### Why Most Onboardings Fail

The same failure patterns appear in onboarding engagements regardless of the customer, the technology, or the team. Knowing them before the transition starts is the difference between managing them and being surprised by them.

**Failure Pattern 1 — The SDM shows up after the implementation.**
When the SDM is not involved until the technical implementation is complete, everything that matters to service delivery — SLA design, escalation paths, support model, customer expectations — has already been decided by people who will not own it in steady state. The SDM inherits commitments they did not make and a customer who was told something different from what the SDM is prepared to deliver.

**Failure Pattern 2 — Knowledge transfer is treated as documentation.**
The previous provider or internal team produces a stack of documents and calls it knowledge transfer. Documents are not knowledge. Knowledge transfer is a structured process of understanding how the environment actually operates — not how it was designed to operate. The gap between the two is where the first incidents come from.

**Failure Pattern 3 — Go-live is treated as the finish line.**
The implementation team declares success at go-live and moves to the next engagement. The SDM is left with a customer in a new environment, a support team that has never handled a production incident in this environment, and no hypercare structure to catch the failures that always come in the first 30 days.

**Failure Pattern 4 — SLAs are committed to before the baseline is established.**
The contract includes SLA commitments based on what was sold — not what the environment can actually support. When the first SLA breach happens in week two, the SDM has no baseline to reference and no data to support a conversation about what is reasonable.

**Failure Pattern 5 — The customer's definition of success was never documented.**
What does "successfully onboarded" mean to this customer? If that question was never asked and answered in writing before the transition started, the SDM and the customer will have different answers at the end of it.

### The SDM's Role in Transition

The SDM is not the project manager — that role manages tasks, timelines, and resources. The SDM is not the technical lead — that role executes the implementation. The SDM is the accountable owner of the customer relationship and the service commitment.

In practice, that means:

- The SDM is involved from day one — not day thirty
- The SDM owns the customer communication — not the project manager, not the account executive
- The SDM sets the go/no-go criteria and makes the go/no-go call
- The SDM signs off at every phase gate — not just at the end
- The SDM owns the escalation path if anything goes wrong during transition
- The SDM defines what success looks like and confirms it with the customer before the transition starts

---

## Section 2 — The Four Phases of Service Transition

Every service transition follows four phases regardless of the size, complexity, or technology involved. The names may differ by organization — the structure does not.

```
Phase 1: Pre-Transition        Phase 2: Active Transition
[Contract Signed] ──────────► [Kickoff Complete] ──────────►

Phase 3: Go-Live               Phase 4: Steady-State
[Build Complete] ────────────► [Go-Live] ──────────────────► [90-Day Mark]
```

### Phase Summary

| Phase | Duration | SDM Focus | Exit Criteria |
|---|---|---|---|
| **Pre-Transition** | 2–4 weeks | Establish foundation — scope, team, SLAs, tooling, customer expectations | Transition Readiness Checklist confirmed green |
| **Active Transition** | 4–12 weeks (varies by complexity) | Govern the build — knowledge transfer, process design, tooling configuration, training | Go/No-Go criteria met — all checklist items green |
| **Go-Live** | Day 1 + Hypercare period (typically 30 days) | Own the support model — daily stand-ups, incident response, customer communication | Hypercare exit criteria met — SDM signs off |
| **Steady-State** | First 90 days post-hypercare | Establish the rhythm — first service review, SLA baseline, relationship health | First quarterly business review complete |

### Phase Gate Rules

**Rule 1:** The SDM signs off at every phase gate. Not the project manager. Not the implementation lead. The SDM.

**Rule 2:** Phase gates are binary. The criteria are met or they are not. "Mostly done" is not a phase gate pass. If criteria are not met, the timeline extends — not the criteria.

**Rule 3:** The customer confirms readiness at each gate that requires their participation. A gate the provider passes unilaterally — without customer confirmation — is not a gate. It is a risk.

**Rule 4:** Every gate has a documented sign-off. The SDM's sign-off is recorded in ServiceNow as a milestone. When something goes wrong six months later, the audit trail shows what was confirmed and when.

---

## Section 3 — Pre-Transition — Getting Ready

### What Happens Here

Pre-transition is the foundation phase. Nothing built in Active Transition will be stable if the foundation is wrong. The SDM's job in this phase is to make sure everyone — the provider team, the customer team, and any third parties involved — starts from the same understanding of what is being built and why.

### 3.1 Transition Kickoff

The kickoff meeting is the first formal interaction between the provider team and the customer team as an operational unit. It is not a sales meeting — the deal is closed. It is not a project status meeting — the project has not started. It is a structured conversation that establishes the working relationship and confirms the foundation.

**Kickoff agenda — 90 minutes:**

| Segment | Time | Owner | Content |
|---|---|---|---|
| Introductions | 10 min | SDM | Provider team and customer team — names, roles, and accountability |
| Transition overview | 15 min | SDM | Four phases, timeline, key milestones, what the customer can expect at each phase |
| Scope confirmation | 20 min | SDM | What is in scope, what is out of scope, what goes through the change process — confirmed with customer |
| Customer success definition | 15 min | SDM | What does successfully onboarded mean to the customer? Documented and confirmed. |
| Roles and RACI | 10 min | SDM | Who does what — provider side and customer side. Named contacts, not team names. |
| Communication plan | 10 min | SDM | How will the teams communicate during transition? Frequency, channel, escalation path. |
| Open questions | 10 min | All | Anything not covered — documented and assigned |

**The most important question in the kickoff:**
"What does success look like to you at the end of this transition?"

Ask it directly. Write down the answer. Confirm it back. This answer becomes the definition of done for the entire engagement — and it is almost always different from what the provider assumed.

### 3.2 Stakeholder Mapping

Before the transition starts, map every stakeholder on both sides. Not just the project contacts — every person whose approval, cooperation, or sign-off is required to complete the transition successfully.

| Stakeholder | Organization | Role in Transition | Decision Authority | Communication Preference |
|---|---|---|---|---|
| [Name] | [Provider / Customer] | [Role] | [Approve / Inform / Consult] | [Email / Phone / Meeting] |

**Common stakeholders missed during mapping:**
- Customer's IT security team — often needs to approve new tooling or access methods
- Customer's finance or procurement team — purchase orders, invoicing contacts
- Customer's end users — the people who will actually use the new support model
- Third-party vendors whose systems are in scope — they have their own timelines and dependencies
- Customer's legal or compliance team — if regulated data is involved

### 3.3 RACI Establishment

The RACI is built at kickoff and confirmed with the customer before Active Transition begins. It covers the full transition — not just the technical implementation.

See Section 7 for the complete RACI template.

**Critical RACI rules:**
- Every activity has exactly one Accountable — not a team, one named person
- The SDM is Accountable for all service delivery activities — not just the ones that go well
- Customer responsibilities are explicitly named — not implied
- The RACI is a living document — updated when roles change, not at the end of the transition

### 3.4 Baseline Documentation

Before anything changes, document the current state. This is the rollback reference — if something goes wrong during transition, this is what the customer returns to.

**Baseline documentation requirements:**

| Area | What to Document | Owner | Format |
|---|---|---|---|
| Current support model | How is the customer currently getting IT support? Who do they call? What are the hours? | SDM | Written summary |
| Current SLA performance | What is the current incident volume, resolution time, and SLA compliance? | SDM / Customer | Data export |
| Current tooling | What ITSM platform, monitoring tools, and communication channels are currently in use? | Technical Lead | Inventory |
| Current escalation path | Who does the customer escalate to today when things go wrong? | SDM | Written summary |
| Known issues | What recurring problems or known issues exist in the current environment? | Technical Lead / Customer | Issue log |
| Customer contacts | Who are all the customer contacts — IT, business, executive — and what are their roles? | SDM | Contact directory |

**Rule:** No Active Transition begins without baseline documentation complete. You cannot measure improvement from a baseline you never established.

### 3.5 SLA Confirmation

The SLA commitments in the contract were agreed during the sales process. Before Active Transition begins, the SDM confirms that those commitments are achievable given the actual environment.

**SLA confirmation checklist:**

- [ ] Review contracted SLA commitments — every metric, every target
- [ ] Confirm the baseline environment can support the committed targets
- [ ] Confirm the support model — coverage hours, team structure — matches the SLA requirements
- [ ] Confirm the tooling — ServiceNow SLA timers, monitoring alerts — is configured to measure the right things
- [ ] Identify any SLA commitments that are at risk given the baseline environment
- [ ] If gaps are identified — escalate to account management before transition starts, not after first breach

**If the SLA is not achievable:**
Raise it before the transition starts. A conversation about SLA feasibility before go-live is uncomfortable. A conversation about SLA credits after three months of breaches is much worse.

### 3.6 Tooling Setup

All tooling required to support the new service model must be configured and tested before Active Transition begins. The tools are not configured during transition — they are ready when transition starts.

**Tooling setup checklist:**

| Tool | Setup Required | Owner | Confirmed Ready |
|---|---|---|---|
| ServiceNow — customer account | Account created, SLA timers configured, assignment groups set up | ServiceNow Admin | [ ] |
| ServiceNow — customer portal access | Customer contacts provisioned with appropriate access | ServiceNow Admin | [ ] |
| Monitoring integration | Monitoring alerts routing to ServiceNow incident records | Technical Lead | [ ] |
| On-call schedule | On-call rotation configured for this customer | SDM | [ ] |
| Communication channels | Bridge call details, escalation contacts, customer distribution lists | SDM | [ ] |
| Reporting | Customer-facing reports configured and scheduled | SDM | [ ] |

### 3.7 Pre-Transition Exit Criteria — Phase Gate 1

The SDM confirms all of the following before Active Transition begins. If any item is not confirmed, Pre-Transition continues.

- [ ] Kickoff meeting complete — all attendees confirmed, notes distributed
- [ ] Customer's definition of success documented and confirmed
- [ ] Stakeholder map complete — all required contacts identified on both sides
- [ ] RACI confirmed with customer
- [ ] Baseline documentation complete
- [ ] SLA commitments confirmed achievable — or escalation initiated
- [ ] All tooling set up and tested
- [ ] Transition timeline confirmed — key milestones agreed by both parties
- [ ] Communication plan confirmed — frequency, channel, escalation path
- [ ] Customer-side responsibilities confirmed and accepted

---

## Section 4 — Active Transition — The Build

### What Happens Here

Active Transition is where the new service model is built. The technical implementation team executes. The SDM governs — ensuring that what is being built matches what was committed, that risks are identified and managed before they become incidents, and that the customer is informed throughout.

The SDM's job in this phase is not to do the technical work. It is to make sure the technical work is being done correctly and that nothing is being built that will create a problem in steady state.

### 4.1 Knowledge Transfer

Knowledge transfer is the most underestimated activity in any service transition. Documentation is not knowledge transfer. A handoff meeting is not knowledge transfer. Knowledge transfer is a structured process of understanding how the environment actually operates — the undocumented dependencies, the workarounds that have been in place for years, the systems that are more fragile than they look, and the customer contacts who know where the bodies are buried.

**Knowledge transfer structure:**

| Session | Topic | Who Provides | Who Receives | Documentation Output |
|---|---|---|---|---|
| Environment overview | Architecture, key systems, dependencies | Previous provider / customer IT team | Provider technical team + SDM | Architecture diagram |
| Known issues | Recurring problems, workarounds, fragile systems | Previous provider / customer IT team | Provider technical team | Known issues log → KEDB |
| Escalation history | What has escalated to the customer's executives and why | Customer IT lead | SDM | Escalation history summary |
| Customer preferences | How the customer likes to be communicated with, what they care about, what frustrates them | Customer IT lead | SDM | Customer profile |
| Vendor relationships | Third-party vendors, carrier relationships, support contracts | Customer IT lead | SDM | Vendor directory |
| Access and credentials | System access, credentials, security requirements | Customer IT lead | Technical Lead | Access inventory |

**The questions that surface the real knowledge:**
- "What breaks most often and why?"
- "What is the one thing we should never change without being very careful?"
- "Who on the customer side will escalate to their executive if something goes wrong?"
- "What did the previous provider get wrong that we should not repeat?"
- "What workarounds are currently in place that we should know about?"

The answers to these questions are more valuable than any technical documentation.

### 4.2 Process Documentation

During Active Transition, the processes that will govern steady-state service are documented. These are not copied from a generic template — they are designed specifically for this customer's environment and confirmed with the customer before go-live.

**Processes documented during Active Transition:**

| Process | Content | Confirmed With |
|---|---|---|
| Incident Management | Severity classification for this customer, escalation path, bridge call protocol, executive notification contacts | Customer IT lead |
| Change Management | Change classification, blackout periods specific to this customer, CAB participation if applicable | Customer IT lead |
| Service Request | Request catalog items specific to this customer, fulfillment SLAs, approval requirements | Customer IT lead |
| Escalation | When the customer escalates, who they call, what the SDM does when they receive an escalation | Customer executive contact |
| Reporting | What reports the customer receives, at what frequency, in what format | Customer IT lead |

### 4.3 ServiceNow Configuration

Every customer-specific ServiceNow configuration is completed and tested during Active Transition — not at go-live.

**Customer-specific ServiceNow configuration:**

| Configuration Item | Description | Tested | Sign-Off |
|---|---|---|---|
| Customer account | Account record, contacts, escalation preferences | [ ] | [ ] |
| SLA definitions | One SLA per priority — response and resolution | [ ] | [ ] |
| SLA breach notifications | Automated alerts at 75% and 100% of each SLA window | [ ] | [ ] |
| Assignment groups | Support teams mapped to this customer | [ ] | [ ] |
| On-call schedule | On-call rotation configured and tested | [ ] | [ ] |
| Monitoring integration | Alerts from customer monitoring routing to incidents | [ ] | [ ] |
| Customer portal | Customer contacts can submit tickets and check status | [ ] | [ ] |
| Reporting | Customer-facing reports scheduled and tested | [ ] | [ ] |
| KEDB entries | Known issues from knowledge transfer documented | [ ] | [ ] |

**Testing rule:** Every configuration item is tested with a simulated incident, change, or request before go-live. Configurations that have not been tested in a realistic scenario have not been validated.

### 4.4 Team Training

The support team that will own this customer in steady state must be trained before go-live. Training is not optional and it is not a one-hour briefing. It covers the customer's environment, their processes, their escalation preferences, and the ServiceNow configuration specific to this account.

**Training content:**

- Customer overview — who they are, what they do, why they matter
- Environment architecture — key systems, dependencies, known fragile points
- Incident classification for this customer — what is a Sev 1 vs. Sev 2 in this environment
- Escalation path — who to call when things go wrong, in what order
- Customer communication preferences — how the customer wants to be kept informed
- ServiceNow walkthrough — this customer's account, SLA timers, escalation rules
- Known issues and workarounds — from the KEDB entries built during knowledge transfer
- First call simulation — practice handling a simulated Sev 1 incident for this customer

**Training sign-off:** Every team member who will be on-call for this customer at go-live signs off on training completion. No team member handles a live incident for this customer before training is complete.

### 4.5 Active Transition Exit Criteria — Phase Gate 2

The SDM confirms all of the following before Go-Live is scheduled. If any item is not confirmed, Active Transition continues.

- [ ] Knowledge transfer complete — all sessions conducted, documentation produced
- [ ] All processes documented and confirmed with customer
- [ ] ServiceNow configuration complete and tested for all configuration items
- [ ] KEDB populated with all known issues from knowledge transfer
- [ ] All team members trained and signed off
- [ ] Go/No-Go criteria defined and agreed with customer
- [ ] Go-live date confirmed — customer and provider both committed
- [ ] Hypercare structure defined — duration, daily stand-up cadence, escalation path
- [ ] Customer communication for go-live prepared — announcement, new support contact details, portal instructions
- [ ] Rollback plan confirmed — if go-live fails, what happens?

---

## Section 5 — Go-Live — The Handoff

### What Happens Here

Go-live is the moment operational accountability transfers to the new service model. It is not the end of the transition — it is the beginning of the most sensitive phase. The first 30 days after go-live are where the gaps in knowledge transfer, process design, and tooling configuration surface as real incidents with real customer impact.

The SDM's job at go-live is to own the transition moment, communicate it clearly, and have a hypercare structure in place that catches the inevitable issues before they become escalations.

### 5.1 Go/No-Go Decision

The Go/No-Go decision is made by the SDM — not the project manager, not the implementation lead, not the customer. The SDM makes this call based on the Phase Gate 2 checklist. If the criteria are not met, go-live is postponed. The SDM communicates the postponement and the reason to the customer.

**Go/No-Go criteria — minimum requirements:**

- [ ] All Phase Gate 2 criteria confirmed complete
- [ ] All critical ServiceNow configurations tested — no open defects
- [ ] All team members trained — no untrained staff on go-live day support rotation
- [ ] Rollback plan confirmed and all parties know their role
- [ ] Customer IT lead has confirmed readiness
- [ ] Go-live communication sent to all affected users
- [ ] SDM and on-call support confirmed available for go-live day and 48 hours after
- [ ] Hypercare bridge call details distributed to all parties

**If any item is red at the Go/No-Go checkpoint:** Go-live does not happen. The SDM states this clearly — not apologetically, not with excessive explanation. "We are not ready to go live today. Here is what still needs to be done and when we will be ready." Then execute against that timeline.

### 5.2 Day One Support Model

Go-live day requires elevated support — not the steady-state model. Day one is not business as usual.

**Day one support structure:**

| Role | Responsibility | Coverage |
|---|---|---|
| SDM | On-call — available for any escalation or customer contact | Full business hours + on-call after hours |
| Senior Engineer | On standby — available to join any incident bridge within 15 minutes | Full business hours |
| Service Desk Lead | Monitoring queue — elevated response to all tickets from this customer | Full business hours |
| Customer IT Lead | On-site or available by phone — confirms issues as they arise | Full business hours |

**Day one monitoring checklist — SDM checks every 2 hours:**
- ServiceNow queue — any open tickets? What is the status?
- Monitoring alerts — anything firing that has not generated a ticket?
- Customer portal — any submissions that have not been acknowledged?
- On-call team — all team members aware they are on elevated support?

### 5.3 Go-Live Communication

The SDM owns all go-live communications. Three communications go out — before, at, and after.

**Pre-go-live (T-24 hours):**
> "Tomorrow, [date], your IT support transitions to [provider]. Effective [time], please contact support through [new method — portal URL, phone number]. Your new Service Delivery Manager is [SDM name] — [contact details]. If you experience any issues during the transition, contact [SDM direct line] immediately."

**At go-live (T-0):**
> "The transition is live as of [time]. Your IT support is now managed by [provider]. Submit requests and report issues at [portal URL] or call [support number]. We are monitoring closely during the first 30 days — contact [SDM name] directly at [contact] if you have any concerns."

**End of day one:**
> "Day one is complete. [X] tickets were handled today — [X] resolved, [X] in progress. No SLA breaches. [Or: one SLA breach — root cause and corrective action below.] We will provide a daily summary for the first week. Your next update will be [time tomorrow]."

### 5.4 Hypercare Structure

Hypercare is the elevated support period immediately following go-live. It is typically 30 days — adjusted based on environment complexity. During hypercare, the SDM maintains direct involvement in every significant incident and reviews the operation daily.

**Hypercare duration guidance:**

| Environment Complexity | Recommended Hypercare Duration |
|---|---|
| Simple — single site, standard tooling, low incident volume | 2 weeks |
| Moderate — multiple sites or systems, moderate complexity | 30 days |
| Complex — enterprise environment, multiple integrations, high volume | 45–60 days |

**Daily hypercare stand-up — 15 minutes:**

| Agenda Item | Content |
|---|---|
| Ticket volume | How many tickets were opened and closed in the last 24 hours? |
| SLA compliance | Any SLA breaches or near-misses? |
| Open incidents | Any incidents open more than 24 hours? What is the status? |
| Customer feedback | Any customer contacts outside the ticketing system — calls, emails, complaints? |
| Monitoring alerts | Any alerts that did not generate tickets? Why? |
| Action items | Any items from previous stand-up that are not yet resolved? |

**Hypercare escalation path:**
During hypercare, the escalation path is tighter than steady state. Any Sev 2 or above — the SDM is notified within 15 minutes. Any customer contact outside the ticketing system — the SDM is notified immediately.

### 5.5 Hypercare Exit Criteria — Phase Gate 3

The SDM confirms all of the following before declaring hypercare complete and transitioning to steady state. If criteria are not met, hypercare is extended.

- [ ] No open Sev 1 or Sev 2 incidents
- [ ] SLA compliance rate at or above contracted target for the past 14 days
- [ ] All known issues from knowledge transfer have been addressed or have documented workarounds in KEDB
- [ ] Support team is handling incidents independently — SDM not required on every call
- [ ] Customer IT lead confirms satisfaction with current support model
- [ ] No outstanding action items from go-live or hypercare incidents without owners and due dates
- [ ] First monthly service review scheduled
- [ ] Steady-state on-call schedule confirmed — hypercare elevated coverage ends

---

## Section 6 — Steady-State Handoff — The First 90 Days

### What Happens Here

Steady state is not the end of the SDM's onboarding work — it is the beginning of the ongoing relationship. The first 90 days of steady state establish the patterns, the expectations, and the trust that determine whether this customer stays for three years or becomes a churn risk.

### 6.1 First Service Review

The first monthly service review happens within 30 days of hypercare close. It is the first time the SDM presents formal performance data to the customer under the new service model.

**First service review — what is different:**

- The baseline is being established — the SDM presents the data and confirms with the customer that the measurement methodology matches their expectations
- Historical comparison may be limited — the SDM acknowledges this directly rather than presenting incomplete comparisons
- Hypercare findings are reviewed — what was found, what was fixed, what is still in progress
- The customer's definition of success from the kickoff is revisited — are we on track?

**What not to do in the first service review:**
Do not present the first month's data as a victory lap if the hypercare period had significant issues. The customer lived through it — they know. Present the data honestly, acknowledge the hypercare issues, and state specifically what was done about each one.

### 6.2 SLA Baseline Establishment

The first 90 days establish the actual performance baseline for this customer's environment. The contracted SLA commitments are the target — the baseline is the reality. If the baseline is below target, the SDM has 90 days to identify the gap, find the root cause, and close it before it becomes a pattern.

**SLA baseline documentation:**

| Metric | Contracted Target | Month 1 Actual | Month 2 Actual | Month 3 Actual | Trend |
|---|---|---|---|---|---|
| Sev 1 MTTR | | | | | |
| Sev 2 MTTR | | | | | |
| SLA Compliance Rate | | | | | |
| Incident Volume | | | | | |
| FCR Rate | | | | | |

If month three is not at target — escalate. Do not wait for the quarterly business review. A negative trend in month three is a pattern. A pattern that is not addressed becomes a relationship problem.

### 6.3 KEDB Population from Transition Findings

Every issue surfaced during knowledge transfer, active transition, and hypercare that does not have a permanent fix is documented in the KEDB. The first 90 days of steady state is when the KEDB proves its value — the support team references known errors during triage instead of re-investigating issues that were already identified during transition.

**KEDB review at 90 days:**
- How many KEDB entries were created during transition?
- How many have been referenced during steady-state incident triage?
- How many still have no permanent fix — and what is the plan?
- Have any new recurring issues emerged that should be added?

### 6.4 Relationship Health Check

At the 90-day mark, the SDM conducts a relationship health check with the customer's primary IT contact and, where appropriate, the customer's executive sponsor.

**Health check questions — customer IT contact:**
- How would you rate the responsiveness of our support team on a scale of 1 to 5?
- Is the communication frequency and format working for you?
- Are there any recurring issues that we have not addressed?
- Is there anything about the transition that did not go as you expected?
- What is the one thing we could do differently that would make the biggest difference?

**Health check questions — executive sponsor:**
- Do you have confidence in the service model we have established?
- Are there any business changes on the horizon that we should be planning for?
- Is the relationship meeting your expectations at this stage?

The answers to these questions are documented and reviewed by the SDM. Any negative feedback generates an action item — with a named owner and a due date — before the conversation ends.

### 6.5 First Quarterly Business Review

The first QBR happens at the 90-day steady-state mark — approximately four to five months after contract signature. It is the first opportunity to present strategic value, not just operational performance.

**First QBR agenda additions beyond standard QBR:**
- Transition retrospective — what went well, what was challenging, what was learned
- 90-day performance summary — trend data since go-live
- Roadmap preview — what improvements are planned for the next quarter
- Customer success revisit — the definition of success from kickoff — has it been achieved?

---

## Section 7 — RACI Template

### Transition RACI by Phase

**R = Responsible | A = Accountable | C = Consulted | I = Informed**

| Activity | SDM | Technical Lead | Service Desk Lead | Customer IT Lead | Customer Executive | Project Manager |
|---|---|---|---|---|---|---|
| **PRE-TRANSITION** | | | | | | |
| Transition kickoff facilitation | A/R | C | I | C | I | C |
| Stakeholder mapping | A/R | C | C | C | I | C |
| RACI development | A/R | C | C | C | I | R |
| Baseline documentation | A | R | C | C | I | C |
| SLA confirmation | A/R | C | I | C | C | I |
| Tooling setup | A | R | C | I | I | C |
| Phase Gate 1 sign-off | A/R | C | I | C | I | C |
| **ACTIVE TRANSITION** | | | | | | |
| Knowledge transfer facilitation | A/R | C | I | R | I | C |
| Process documentation | A/R | R | C | C | I | C |
| ServiceNow configuration | A | R | C | I | I | I |
| Team training | A/R | R | C | I | I | C |
| Customer communication | A/R | I | I | C | I | C |
| Phase Gate 2 sign-off | A/R | C | I | C | I | C |
| **GO-LIVE** | | | | | | |
| Go/No-Go decision | A/R | C | I | C | I | C |
| Day one monitoring | A/R | C | R | C | I | I |
| Go-live communication | A/R | I | I | C | I | C |
| Hypercare stand-ups | A/R | C | R | C | I | I |
| Incident response (hypercare) | A | R | R | C | I | I |
| Phase Gate 3 sign-off | A/R | C | C | C | I | I |
| **STEADY STATE** | | | | | | |
| First service review | A/R | C | C | C | I | I |
| SLA baseline documentation | A/R | C | R | C | I | I |
| KEDB review | A | C | R | C | I | I |
| Relationship health check | A/R | I | I | R | R | I |
| First QBR | A/R | C | C | C | R | I |

### Customer RACI — Customer Obligations

These are the activities the customer is accountable for during transition. These are documented in the SOW and confirmed at kickoff — not discovered when they are missed.

| Customer Obligation | Owner | Phase | Consequence If Missed |
|---|---|---|---|
| Provide named technical contact with decision authority | Customer IT Lead | Pre-Transition | Transition timeline extends |
| Participate in knowledge transfer sessions | Customer IT Lead + Team | Active Transition | Knowledge gaps surface as incidents post-go-live |
| Provide access to systems and environments | Customer IT Lead | Active Transition | Configuration and testing delayed |
| Complete UAT and provide sign-off | Customer IT Lead | Active Transition | Go-live delayed — Phase Gate 2 blocked |
| Communicate transition to end users | Customer IT Lead | Pre-Go-Live | End users unaware of new support process — contact volumes spike incorrectly |
| Participate in go-live day monitoring | Customer IT Lead | Go-Live | SDM lacks on-site visibility during highest-risk period |
| Attend hypercare stand-ups | Customer IT Lead | Hypercare | Issues go unidentified — escalation risk increases |
| Respond to SDM health check | Customer IT Lead + Executive | Steady State | Relationship health is unmeasured |

---

## Section 8 — Transition Risk Register

Every transition carries risk. The risks are predictable. Managing them before they materialize is the SDM's job. Discovering them after they become incidents is not risk management — it is incident response with a preventable root cause.

### Standard Transition Risks

| Risk | Probability | Impact | Mitigation | Owner |
|---|---|---|---|---|
| **Scope creep** — customer requests items not in the SOW during transition | High | High | SOW scope confirmed at kickoff. Change request process established for any additions. | SDM |
| **Knowledge transfer incomplete** — previous provider disengages before transfer is complete | Medium | High | Knowledge transfer sessions scheduled and confirmed before previous provider exit date. Escalation to customer executive if sessions are missed. | SDM |
| **Customer stakeholder unavailability** — key customer contacts unavailable during critical transition activities | Medium | High | Named backup contacts identified at kickoff for every critical role. | SDM |
| **SLA misalignment** — contracted SLA not achievable in the actual environment | Medium | High | SLA confirmation completed in Pre-Transition. Escalation to account management before transition starts if gap identified. | SDM |
| **Tooling delays** — ServiceNow or other tooling not ready at Active Transition start | Low | High | Tooling setup checklist confirmed before Pre-Transition gate closes. | Technical Lead |
| **Go-live incidents** — production issues in first 48 hours post-go-live | High | Medium | Hypercare structure in place. Day one elevated support confirmed. Rollback plan ready. | SDM |
| **Team training gaps** — support team not trained on customer environment before go-live | Low | High | Training sign-off required before Phase Gate 2 closes. | SDM |
| **Customer expectation mismatch** — customer expected something different from what was delivered | Medium | High | Customer definition of success documented at kickoff. Revisited at each phase gate. | SDM |
| **Third-party dependency delay** — vendor or carrier required for transition is not available on schedule | Medium | Medium | Third-party dependencies identified and confirmed in Pre-Transition. Escalation path established. | Technical Lead / SDM |
| **Hypercare exit too early** — pressure to close hypercare before environment is stable | Medium | High | Hypercare exit criteria are binary — met or not met. SDM holds the gate regardless of pressure. | SDM |

### Risk Escalation Threshold

Any risk that moves from Medium to High probability during the transition is escalated to the SDM's manager and the customer's IT lead immediately. Not at the next status meeting. Immediately.

A risk that was identified and escalated before it materialized is a well-managed transition. A risk that was known and not escalated is a management failure.

---

## Section 9 — Transition Checklist

This is the master checklist for the entire transition. The SDM owns it. It is updated at every phase gate and reviewed at every weekly status meeting.

### Phase Gate 1 — Pre-Transition Complete

- [ ] Kickoff meeting conducted — notes distributed to all parties
- [ ] Customer definition of success documented and confirmed
- [ ] Stakeholder map complete — named contacts on both sides
- [ ] RACI confirmed with customer
- [ ] Baseline documentation complete — current state captured
- [ ] SLA commitments confirmed achievable — or escalation initiated
- [ ] All tooling set up and tested
- [ ] Transition timeline confirmed — milestones agreed
- [ ] Communication plan confirmed
- [ ] Customer-side obligations confirmed and accepted
- **SDM Sign-off:** _________________ Date: _______

### Phase Gate 2 — Active Transition Complete

- [ ] All knowledge transfer sessions complete — documentation produced
- [ ] All processes documented and confirmed with customer
- [ ] ServiceNow configuration complete and tested
- [ ] KEDB populated with all known issues from knowledge transfer
- [ ] All team members trained and signed off
- [ ] Go/No-Go criteria defined and agreed
- [ ] Go-live date confirmed — both parties committed
- [ ] Hypercare structure defined — duration, cadence, escalation path
- [ ] Go-live communications prepared
- [ ] Rollback plan confirmed
- **SDM Sign-off:** _________________ Date: _______

### Go-Live — Day One

- [ ] Go/No-Go decision made — criteria confirmed green
- [ ] Go-live communications sent
- [ ] Elevated support team confirmed available
- [ ] ServiceNow monitoring active
- [ ] Customer IT lead confirmed available
- [ ] Rollback resources on standby
- [ ] End-of-day summary sent to customer
- **SDM Sign-off:** _________________ Date: _______

### Phase Gate 3 — Hypercare Complete

- [ ] No open Sev 1 or Sev 2 incidents
- [ ] SLA compliance at or above target for 14 consecutive days
- [ ] All known issues addressed or in KEDB with workaround
- [ ] Support team handling incidents independently
- [ ] Customer IT lead confirms satisfaction
- [ ] No outstanding action items without owners and due dates
- [ ] First monthly service review scheduled
- [ ] Steady-state on-call schedule confirmed
- **SDM Sign-off:** _________________ Date: _______

### 90-Day Steady-State Checkpoint

- [ ] Three months of SLA performance data compiled
- [ ] SLA baseline documented — trend direction confirmed
- [ ] KEDB reviewed — utilization rate confirmed
- [ ] Relationship health check completed with customer IT lead
- [ ] Relationship health check completed with customer executive (if applicable)
- [ ] Any negative feedback has a documented action item with owner and due date
- [ ] First QBR scheduled and agenda confirmed
- **SDM Sign-off:** _________________ Date: _______

---

## Section 10 — Common Onboarding Failures

These are the failures that appear in every post-mortem of a troubled customer relationship. They are not surprises. They are patterns. Knowing them before the transition starts is the advantage.

| Failure | What It Looks Like | What It Costs | How to Prevent It |
|---|---|---|---|
| **SDM not involved until implementation is complete** | SDM inherits commitments they did not make and a customer who was told something different | First 90 days spent correcting misaligned expectations instead of delivering service | SDM involvement starts at contract signature — not at go-live |
| **Knowledge transfer treated as documentation** | Stack of documents handed over, called complete | First incidents re-investigated from scratch — MTTR is double what it should be | Structured knowledge transfer sessions with specific questions — not document handoffs |
| **Customer obligations not confirmed** | Customer IT lead unavailable for knowledge transfer sessions | Active Transition extends — knowledge gaps surface as post-go-live incidents | Customer obligations confirmed in writing at kickoff — escalate immediately when missed |
| **Go-live treated as the finish line** | Implementation team moves to next engagement at go-live | Hypercare is unstructured — first incidents escalate directly to customer executive | Hypercare structure defined before go-live — SDM owns it |
| **SLA not baselined before commitment** | First SLA report shows 78% compliance against a 95% target | Customer demands credits, relationship starts in deficit | SLA confirmation completed in Pre-Transition — gaps escalated before contract signs |
| **Scope not confirmed at kickoff** | Customer asks for items not in the SOW during Active Transition | SDM either delivers out-of-scope work for free or has a difficult conversation mid-transition | SOW scope confirmed line by line at kickoff — change request process activated immediately for additions |
| **Customer definition of success never asked** | Provider delivers what was contracted — customer is still dissatisfied | Churn at first renewal | Ask the question at kickoff — document the answer — revisit at every phase gate |
| **Hypercare closed under pressure** | Account team wants to close hypercare to free up resources | Environment instability continues into steady state — incidents increase | Hypercare exit criteria are binary — SDM holds the gate |
| **First service review skipped or delayed** | No formal review in first 30 days of steady state | Baseline never established — performance trends invisible | First service review scheduled before hypercare closes |
| **No rollback plan** | Go-live fails and nobody knows what to do | Extended outage — customer escalates to executive on day one | Rollback plan defined and tested before Phase Gate 2 closes |

---

## Appendix — Transition Quick Reference

### Phase Gates Summary
| Gate | Phase Closes | SDM Confirms | Customer Confirms |
|---|---|---|---|
| Gate 1 | Pre-Transition | All foundation items complete | Obligations accepted, timeline agreed |
| Gate 2 | Active Transition | Build complete, go-live ready | UAT sign-off, go-live date confirmed |
| Gate 3 | Hypercare | Environment stable, team independent | Satisfaction confirmed |
| 90-Day | Steady State | Baseline established, relationship healthy | Health check complete |

### First Call Rule
The SDM is reachable directly — not through a queue — for the first 30 days post-go-live. Every customer escalation during that window goes to the SDM first.

### The One Question That Matters Most
*"What does success look like to you at the end of this transition?"*

Ask it at kickoff. Write down the answer. Confirm it at every phase gate. If the answer changes — that is a scope conversation, not a delivery failure.

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | August 2026 | Initial release | Scott Boehler |

---

*A transition that ends at go-live is not a transition — it is an implementation. The SDM's job is not done until the customer is in steady state, the baseline is established, and the relationship is healthy. Everything before that is setup.*
