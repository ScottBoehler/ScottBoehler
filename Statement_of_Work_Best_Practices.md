# Statement of Work Best Practices Guide
### Enterprise IT & Managed Services | SOW Design, Review & Execution

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** Enterprise IT services, managed services, cloud, contact center, and network SOWs

---

## Purpose & Scope

A Statement of Work is where a deal becomes a commitment. Everything that happens in delivery — the disputes, the cost overruns, the customer escalations, the finger-pointing — traces back to what was or wasn't in the SOW. Get it right before anyone signs and you have a foundation for a successful engagement. Get it wrong and you are managing the fallout from day one.

This guide covers how to structure, write, and review an enterprise SOW. It is written from the perspective of someone who has been on both sides — designing solutions that go into SOWs and owning the delivery once they are signed. Both perspectives matter. A solution architect who has never delivered against an SOW will over-promise. A delivery manager who has never written one will under-scope. The best SOWs are written by people who understand both.

---

## Section 1 — What a Statement of Work Is and Isn't

### What It Is

A Statement of Work is a legally binding document that defines the specific services, deliverables, timelines, and responsibilities for a particular engagement between a provider and a customer. It sits underneath a Master Services Agreement (MSA) and gives the MSA commercial and legal terms something to apply to.

The SOW answers four questions:

- **What** is being delivered?
- **How** will it be delivered?
- **When** will it be delivered?
- **Who** is responsible for what?

If the SOW cannot answer all four questions clearly, it is not ready to be signed.

### What It Isn't

**It is not a proposal.** A proposal is a sales document designed to win a deal. An SOW is an operational document designed to define a commitment. Proposals use aspirational language — SOWs use precise language. The moment proposal language makes it into an SOW, you have a problem.

**It is not a contract.** The MSA is the contract. The SOW references the MSA and is governed by it. Changes to the SOW do not change the MSA, and vice versa.

**It is not a requirements document.** Requirements documents capture what the customer wants. An SOW defines what the provider is committing to deliver. These are related but not the same. A requirement that is not in the SOW scope is not being delivered — regardless of how many times it appeared in a requirements document.

### The MSA / SOW / Change Order Hierarchy

Understanding the hierarchy prevents most SOW disputes before they start.

```
Master Services Agreement (MSA)
└── Governs the overall relationship, commercial terms, liability, IP
    └── Statement of Work (SOW)
        └── Defines specific engagement scope, deliverables, timelines
            └── Change Order / Complex Service Request
                └── Modifies SOW scope, cost, or timeline for specific changes
```

Anything not in the SOW that the customer wants delivered goes through a Change Order or Complex Service Request — not an informal email, not a verbal agreement, not a slide deck from a sales call. If it is not documented and signed, it does not exist.

---

## Section 2 — Core SOW Structure

Every enterprise SOW should follow a consistent structure. Deviating from it without good reason creates gaps that surface in delivery. Here is the standard structure and what belongs in each section.

### 2.1 Introduction

**Background** — How did we get here? Brief context on the customer's current state, what problem they are trying to solve, and why this engagement exists. Two to three paragraphs maximum. This is not a sales pitch — it is context that helps anyone reading the SOW understand what the engagement is trying to accomplish.

**Purpose** — What does this SOW specifically cover? Phase 1 only? A specific business unit? A defined geography? State it explicitly. If there are future phases, name them and confirm they are out of scope for this SOW.

### 2.2 Statement of Requirements

What the customer needs the solution to do. This section captures requirements before the solution is described — the what before the how. Requirements should be numbered and tracked through the rest of the document to confirm they are addressed in the solution.

Each requirement should be:
- **Specific** — not "the solution should be reliable" but "the solution will have 99.9% availability measured monthly"
- **Measurable** — if you cannot measure compliance with the requirement, it will be disputed
- **Attributed** — who owns verifying this requirement is met — provider, customer, or third party?

### 2.3 Solution

How the provider will meet the stated requirements. Architecture overview, components, integrations, platform dependencies. This section describes what is being built or delivered — not how the project will be managed.

Critical rule: every requirement in Section 2 must be traceable to a response in Section 3. If a requirement is out of scope for this engagement, say so explicitly here — do not leave it unaddressed. Unaddressed requirements become disputes.

### 2.4 Project Delivery

How the solution will be implemented. Scope, team structure, milestones, testing approach, training, migration plan, go-live criteria. This section covers the delivery of the solution, not the solution itself.

### 2.5 Service

What ongoing service the provider will deliver once the solution is live. Incident management, escalation paths, reporting, self-service capabilities, SLAs and KPIs. This is where the operational commitment lives.

### 2.6 Caveats, Obligations and Dependencies

What the provider is assuming to be true, what the customer must do to enable delivery, and what third parties are involved. This section protects both parties — and is the most commonly underwritten section in any SOW.

---

## Section 3 — Defining Scope

Scope is the most important section of any SOW. Every delivery dispute, every cost overrun, every escalation that starts with "we thought that was included" traces back to scope that was not defined clearly enough.

### The Golden Rule of Scope

**State what is in scope. State what is out of scope. Leave nothing to assumption.**

If the customer believes something is included and the provider believes it is not, the SOW is the referee. If the SOW is silent on the item, both parties will argue their interpretation and somebody loses. Write the SOW so that argument never has to happen.

### In-Scope vs. Out-of-Scope

Every SOW should have an explicit out-of-scope section. Not just a list of what is included — a list of what is specifically excluded. Examples:

| In Scope | Out of Scope |
|---|---|
| Migration of defined business units in Phase 1 | Migration of any business unit not named in Phase 1 |
| Integration with named systems (CRM, SSO) | Integration with any system not named in this SOW |
| Standard platform training for defined user roles | Custom training development or additional training instances |
| Support during agreed business hours | Support outside agreed hours unless separately contracted |
| New platform configuration | Migration of historical data from legacy systems |

If it is not on the in-scope list, it is out of scope. If there is any doubt about whether something is in or out, put it on the out-of-scope list explicitly.

### Phased Delivery and Future Scope

When an engagement is delivered in phases — which most large enterprise engagements are — the SOW must be explicit about what is Phase 1 and what is future.

Best practice:
- Name future phases explicitly and state they are out of scope for this SOW
- Define the process for scoping future phases (typically a Complex Service Request or a new SOW)
- Do not include detailed requirements for future phases in the current SOW — it creates implied commitments

### The Complex Service Request Process

Every SOW should define how changes to scope are handled after signing. The most common mechanism is a Complex Service Request (CSR) or Change Order process.

A CSR process should define:
- What triggers a CSR — any scope addition, design change, or commercial impact
- Who can initiate a CSR — authorized contacts on both sides
- What a CSR must include — description of change, impact on timeline, impact on cost
- Required approvals before work begins
- SLA for provider to respond to a CSR request

**Critical rule:** No work outside the SOW scope begins without an approved CSR. Not based on a verbal agreement. Not based on an email. Not based on a slide deck. If work is performed outside approved scope without a CSR, the provider has no basis for billing it and the customer has no obligation to pay for it.

---

## Section 4 — Service Requirements

The service section of an SOW defines what happens after the solution goes live. This is where the ongoing operational commitment lives — and where the most commercially significant commitments are made.

### Incident Management

The SOW should define the incident management model clearly:

- **Support model** — dedicated team, shared service, or hybrid? Named contacts or queue-based?
- **Coverage hours** — 24x7x365, business hours, follow-the-sun?
- **Single Point of Contact (SPOC)** — who does the customer call when something breaks?
- **Resolver groups** — how does the SPOC engage technical resolver teams?
- **Third-party coordination** — when third parties are involved, who owns the vendor bridge?

### Escalation and Major Incident Management

- How does a standard incident become a major incident?
- Who is the Major Incident Manager?
- What are the executive notification requirements?
- How are bridge calls managed?
- What is the post-incident review process?

### Reporting

Define what reports the customer will receive, at what frequency, and through what channel. Common reporting commitments:

| Report | Frequency | Delivery Method |
|---|---|---|
| Incident summary report | Monthly | Email / Portal |
| SLA compliance report | Monthly | Email / Portal |
| Major incident report | Within 5 days of resolution | Email |
| Service review meeting | Quarterly | Live presentation |
| Capacity and performance report | Quarterly | Email |

Reporting commitments that are not in the SOW are not required. Customers will ask for reports that were discussed during the sales process but never formalized. If it is not in the SOW, it goes through the CSR process.

### Self-Service

If the customer has access to a self-service portal — for creating tickets, viewing reports, requesting standard changes — define the scope of that access explicitly. What can they do themselves? What requires provider involvement? What roles have what permissions?

### SLAs and KPIs

Every SLA in the service section must be:
- **Specific** — exact metric, exact target, exact measurement period
- **Measurable** — objective data source defined (not "as agreed" or "to be determined")
- **Remedied** — consequence of missing the SLA defined before signing

Common SLA structure in an SOW:

| SLA | Target | Measurement | Remedy |
|---|---|---|---|
| Platform availability | 99.9% monthly | Platform monitoring uptime log | Service credit per breach tier |
| P1 incident response | 15 minutes | ServiceNow acknowledgment timestamp | Service credit |
| P1 incident resolution | 4 hours | ServiceNow resolution timestamp | Service credit |
| Monthly reporting delivery | By 5th of following month | Report delivery date | Noted in service review |

---

## Section 5 — Project Delivery Requirements

The project section covers how the solution gets from SOW signature to go-live. This section is where delivery risk lives.

### Project Scope

Define what the project will deliver — not the solution itself, but the project activities required to deliver it:

- Solution design and architecture finalization
- Platform build and configuration
- Integration development and testing
- System Integration Testing (SIT) and User Acceptance Testing (UAT)
- Training delivery
- Migration execution
- Go-live support
- Hypercare period post-go-live

State explicitly what is not a project activity. Customer responsibilities during the project must be named here — not in the caveats section.

### Milestones

Milestones mark meaningful points in the delivery — not just calendar dates. A good milestone is:
- **Verifiable** — both parties can confirm it has been reached
- **Binary** — either it is complete or it is not
- **Consequential** — missing it has a defined impact on the schedule or commercials

Typical enterprise delivery milestones:

| Milestone | Description |
|---|---|
| SOW Signature | Engagement authorized to begin |
| Kick-off Complete | Project team mobilized, plan confirmed |
| Design Sign-off | Solution design approved by both parties |
| Build Complete | Platform configured per approved design |
| SIT Complete | Provider testing complete, defects resolved |
| UAT Complete | Customer validation complete, sign-off received |
| Migration Complete | Data and services migrated per plan |
| Go-Live | Service live in production |
| Hypercare Complete | Transition to steady-state service |

### Testing

Define who does what testing — and what constitutes a passed test.

- **SIT (System Integration Testing)** — provider-led, tests that the solution works as designed
- **UAT (User Acceptance Testing)** — customer-led, tests that the solution works for the business
- **Defect management** — how are defects raised, prioritized, and resolved?
- **Go-live criteria** — what must be true before the solution goes live? P1 defects outstanding = no go-live?

The go-live criteria must be agreed before testing begins — not negotiated after defects are found.

### Training

Specify:
- Who gets trained (roles, not names)
- What they get trained on
- How many instances of each course
- Delivery format (instructor-led, on-demand, documentation)
- What additional training costs

Training that is not specified in the SOW is not included. If the customer wants more training than the SOW includes, that is a CSR.

### Migration

Migration is where most enterprise delivery engagements run into trouble. The SOW must define:

- What is being migrated (systems, data, numbers, configurations)
- What is not being migrated (legacy data, archived recordings, historical reports)
- Migration approach (big bang vs. phased cutover)
- Rollback criteria — if migration fails, what triggers a rollback and who makes that call?
- Customer responsibilities during migration — this must be explicit

### Hypercare

Define a hypercare period immediately after go-live — typically 2 to 4 weeks — during which the provider maintains elevated support. Define:
- What "elevated support" means (response times, dedicated resource, daily check-ins)
- When hypercare ends and steady-state service begins
- What triggers an extension of hypercare

---

## Section 6 — Caveats, Obligations and Dependencies

This is the section nobody reads carefully enough — until something goes wrong. Caveats, obligations, and dependencies define the conditions under which the provider can deliver what the SOW commits to. If those conditions are not met, the provider's commitments are affected.

### Caveats

A caveat is a condition or limitation that affects delivery. Common examples:

- Solution is based on information provided by the customer as of a specific date — changes to requirements after that date go through the CSR process
- Delivery timelines assume customer approvals within defined windows — delays in customer approval extend delivery dates proportionally
- Availability SLAs exclude downtime caused by factors outside the provider's control (customer network, third-party services, force majeure)
- Platform features are subject to the vendor's roadmap and may vary — the SOW commits to the feature set available at time of delivery
- SLAs do not apply during agreed maintenance windows

Write caveats in plain language. Legal language that nobody reads is not a protection — it is just a document that both parties will dispute later.

### Customer Obligations

The customer has obligations too. These must be named explicitly — not implied. Common customer obligations:

- Provide named technical and business contacts with decision-making authority
- Respond to provider requests for information within defined timeframes (typically 2-5 business days)
- Provide access to systems, environments, and facilities required for delivery
- Conduct UAT and provide sign-off within agreed windows
- Ensure required third-party vendors are engaged and available
- Provide network connectivity and access that meets defined specifications
- Designate trained administrators before go-live

If a customer obligation is not met and delivery is impacted, the provider needs the SOW to document that the obligation existed. Without it, the provider owns the delay.

### Third-Party Dependencies

Name every third party whose performance affects delivery. For each one, define:

- What they are providing
- Who manages the relationship — provider or customer?
- What the dependency is — if they do not deliver X by Y, what happens to the project?
- Who is accountable if the third party fails to deliver?

Third-party risk that is not documented becomes provider risk by default in most customer conversations.

---

## Section 7 — Common SOW Mistakes

These are the mistakes that create the most pain in delivery. They are predictable, preventable, and still happen on almost every engagement.

| Mistake | Why It Happens | What It Costs |
|---|---|---|
| **Proposal language in the SOW** | SOW drafted by copying from the proposal deck | Aspirational claims become contractual commitments — impossible to deliver against |
| **Scope defined only as in-scope** | No out-of-scope section | Customer assumes everything not explicitly excluded is included — every conversation becomes a negotiation |
| **Requirements not traced to solution** | Rushed SOW development | Customer requirements appear in the SOW but no solution response is defined — discovered in delivery |
| **Customer obligations not named** | Assumed the customer knows their responsibilities | Delivery delays caused by customer inaction become provider's problem |
| **SLAs without measurement definitions** | "We'll figure it out" mentality | Every SLA miss becomes a dispute about whether it was actually a miss |
| **No go-live criteria** | Assumed go-live decision was obvious | Customer refuses to go live citing issues that were never defined as blockers |
| **Future scope included in detail** | Sales team trying to show vision | Detailed future scope creates implied commitments for phases not yet contracted |
| **Third-party dependencies not named** | Assumed everyone knows who the vendors are | Provider held accountable for delays caused by vendors they do not control |
| **No CSR process defined** | Assumed scope changes would be handled informally | Every scope conversation becomes a dispute — no agreed process to resolve it |
| **Hypercare not defined** | Assumed steady-state starts at go-live | Customer expects elevated support that was never contracted — provider team moves to next engagement |

---

## Section 8 — SOW Review Checklist

Use this checklist before any SOW is signed. If any item is not confirmed, the SOW is not ready.

### Scope
- [ ] In-scope deliverables are listed specifically — not described in general terms
- [ ] Out-of-scope items are listed explicitly — not left to assumption
- [ ] Future phases are named and confirmed out of scope for this SOW
- [ ] CSR / Change Order process is defined
- [ ] Phase boundaries are clear — what ends Phase 1 and what triggers future phases

### Requirements
- [ ] Every requirement is specific and measurable
- [ ] Every requirement in Section 2 has a response in Section 3
- [ ] Requirements that are out of scope are explicitly stated as such
- [ ] No requirement is left unaddressed

### Solution
- [ ] Solution description matches what was technically validated — not what was proposed
- [ ] All named integrations have been technically confirmed as feasible
- [ ] Platform limitations or dependencies are documented
- [ ] Architecture has been reviewed by the delivery team — not just the sales team

### Project Delivery
- [ ] Milestones are verifiable and binary
- [ ] Go-live criteria are defined and agreed by both parties
- [ ] Testing responsibilities are split clearly between provider and customer
- [ ] Training scope is specific — roles, course titles, number of instances
- [ ] Migration scope is explicit — what is migrated and what is not
- [ ] Hypercare period is defined with start, end, and exit criteria
- [ ] Customer obligations are listed specifically

### Service
- [ ] Support model is defined — coverage hours, SPOC, resolver path
- [ ] Every SLA has a target, measurement method, and remedy
- [ ] Reporting commitments are listed with frequency and delivery method
- [ ] Escalation and major incident process is referenced or defined

### Caveats and Dependencies
- [ ] All assumptions are documented as caveats
- [ ] Customer obligations are listed — not implied
- [ ] All third-party dependencies are named with accountability defined
- [ ] SLA exclusions are documented — maintenance windows, customer-caused events, force majeure

### Commercial
- [ ] Pricing matches the solution and project scope — no scope has been added since commercials were agreed
- [ ] Out-of-scope pricing mechanism is defined (rate card, CSR process)
- [ ] Credit and remedy structure is documented for each SLA

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*A deal that closes on a weak SOW is not a win — it is a delayed loss. The time you save rushing the SOW is the time you will spend managing the fallout in delivery.*
