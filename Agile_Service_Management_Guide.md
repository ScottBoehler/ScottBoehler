# Agile Service Management Guide
### Adapting ITIL for DevOps Environments | Kanban for Operations | Continuous Improvement

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** August 2026  
**Applies To:** Service Delivery Managers, Operations Leaders, and IT professionals operating in organizations that run both traditional ITIL service management and modern Agile/DevOps delivery models simultaneously

---

## Purpose & Scope

Most IT organizations today are running two operating models at the same time — and they are in conflict.

The first model is ITIL-based service management. Weekly CAB meetings. Change freeze windows. SLA-driven incident response. Formal approval gates. This model was designed to protect production stability in environments where changes are infrequent and high-risk.

The second model is Agile and DevOps. Daily or hourly deployments. Continuous integration and continuous delivery. Small, frequent changes. Automated testing as the quality gate. This model was designed to accelerate software delivery in environments where speed is a competitive requirement.

When these two models collide — and in most modern enterprises they do — the Service Delivery Manager is caught in the middle. The development team wants to deploy. The CAB meets on Thursday. The release cannot wait until Thursday. The SDM either becomes the bottleneck that slows the business down or the person who waves changes through without proper review and owns the consequences when something breaks.

This guide is for the SDM who is navigating that collision. It covers what Agile and Kanban actually mean for operations leaders, where ITIL and Agile specifically conflict and why, and how to adapt each framework so both can coexist without breaking what works in either.

This is not a guide for software developers or Scrum Masters. It is a guide for operations leaders who need to understand Agile well enough to work effectively with the teams running it — and to adapt their own practices where the frameworks genuinely improve operations.

---

## Section 1 — The Problem This Document Solves

### The Traditional ITIL Model Was Built for a Different Era

ITIL was codified in an era when software releases happened quarterly or annually. A change to a production system was a significant event — weeks of planning, extensive testing, formal approval, careful implementation. The CAB existed to review those infrequent, high-stakes changes with the scrutiny they deserved.

That model worked. It still works — for organizations where changes are genuinely infrequent and the cost of a failed change is catastrophic. Financial systems processing millions of transactions. Healthcare systems managing patient records. Infrastructure changes that affect thousands of users simultaneously.

But the software development world moved. Agile methodologies — Scrum, Kanban, SAFe — changed how software is built and delivered. DevOps practices — CI/CD pipelines, infrastructure as code, automated testing — changed how software is deployed. What was once a quarterly release became a weekly release became a daily release became dozens of deployments per day.

The CAB model was not designed for dozens of deployments per day. Neither was the change freeze window, the formal risk assessment for every change, or the five-business-day submission lead time.

### The Collision Points

The friction between ITIL and Agile is not philosophical — it is operational. It shows up in specific, recurring situations that the SDM encounters in any organization running both frameworks.

**The Thursday CAB problem.** The development team needs to deploy a fix for a customer-impacting bug. The fix is tested, validated, and ready. The CAB meets Thursday. Today is Monday. The customer cannot wait four days. The SDM either convenes an emergency CAB — which was designed for actual emergencies, not routine deployments — or waves the change through without formal approval.

**The change freeze collision.** The organization institutes a change freeze for the quarter-end financial close. The development team has a sprint ending on the same day with six features ready to deploy. The sprint cannot pause because the change management calendar has a freeze.

**The velocity vs. stability tension.** The development team's performance metric is deployment frequency and feature velocity. The operations team's performance metric is SLA compliance and change success rate. These metrics pull in opposite directions. A team deploying frequently will have more change-induced incidents — statistically inevitable. An operations team minimizing change-induced incidents will push back on deployment frequency.

**The CAB as bottleneck.** In a high-velocity delivery organization, a weekly CAB that reviews every change becomes the single longest lead time in the delivery pipeline. Engineers optimize around it — which means changes accumulate, batch deployments replace continuous delivery, and the risk profile of each deployment increases as the batch size grows.

### What the SDM Needs to Do Differently

The answer is not to abandon ITIL or to abandon Agile. Both exist for good reasons. The answer is to apply each framework where it fits and adapt both where they conflict.

The SDM who understands both frameworks can:
- Design change management processes that protect production stability without blocking continuous delivery
- Apply Kanban principles to service desk operations to improve flow and reduce queue backlogs
- Run retrospectives that make the operations team better over time — not just post-incident reviews that focus on what went wrong
- Have an informed conversation with development and product leadership about what controls are non-negotiable and what can be adapted

The SDM who does not understand Agile will be overruled by development teams who do — and the controls that exist for good reasons will be removed along with the ones that were genuinely bureaucratic.

---

## Section 2 — What Agile and Kanban Actually Are (For Operations Leaders)

### Agile — The Core Principles That Matter to Operations

Agile is a set of values and principles for software development — not a specific process. The Agile Manifesto, published in 2001, established four values and twelve principles. Operations leaders do not need to memorize all twelve. The ones that matter to service management are:

**Working software over comprehensive documentation.**
In an Agile organization, the primary measure of progress is working software — not completed documentation. This conflicts with ITIL's documentation requirements for change records, PIR reports, and process artifacts. The resolution is not to abandon documentation — it is to make documentation lean and purposeful rather than comprehensive for its own sake.

**Responding to change over following a plan.**
Agile teams expect requirements and priorities to change. Plans are made to be updated, not followed rigidly. This conflicts with change freeze windows and locked implementation plans. The resolution is to design change controls that accommodate the reality of changing priorities while maintaining the protections that matter.

**Customer collaboration over contract negotiation.**
Agile teams work in close, continuous collaboration with customers or customer proxies. Feedback cycles are short — weeks, not months. This is actually aligned with good service management practice. The SDM who runs effective service reviews and acts on customer feedback quickly is operating on Agile principles whether they call it that or not.

**Individuals and interactions over processes and tools.**
Agile values human judgment and collaboration over rigid process adherence. This does not mean processes do not matter — it means processes should support the people executing them, not constrain them unnecessarily. The SDM applying this principle asks: "Is this process control protecting production stability or is it a legacy artifact that no longer serves its original purpose?"

### Scrum — What the SDM Needs to Know

Scrum is the most widely used Agile framework. Development teams running Scrum work in fixed time periods called sprints — typically two weeks. Each sprint has a planning session at the start, a review and retrospective at the end, and a daily stand-up throughout.

**What the SDM needs to understand about Scrum:**

| Scrum Concept | What It Is | Why It Matters to the SDM |
|---|---|---|
| **Sprint** | Fixed time period (typically 2 weeks) during which the team builds and delivers a defined set of work | Changes ready at sprint end create predictable deployment windows — CAB can be aligned to sprint cadence |
| **Sprint Planning** | Meeting at sprint start where team commits to what they will deliver | SDM can participate to flag high-risk changes planned for the sprint before work begins |
| **Sprint Review** | Demo of completed work at sprint end | Opportunity for SDM to see what is being deployed before it goes to production |
| **Sprint Retrospective** | Team reflection on what worked and what did not | The Agile equivalent of a PIR — the SDM can adopt this structure for operations teams |
| **Daily Stand-up** | 15-minute daily check-in — what did I do yesterday, what am I doing today, any blockers? | Model for hypercare daily stand-ups and service desk team check-ins |
| **Product Backlog** | Prioritized list of all work to be done | SDM can use backlog thinking to prioritize service improvement initiatives |
| **Definition of Done** | Team's shared standard for when work is complete | Equivalent to the SDM's go-live criteria — work is not done until it meets the definition |

### Kanban — The Operations Leader's Framework

Kanban is more directly applicable to IT operations than Scrum. It was originally developed for manufacturing — Toyota's production system — and translates naturally to service desk queue management, incident response workflows, and change management pipelines.

**The four core Kanban principles:**

**1. Visualize the workflow.**
Make all work visible. In a service desk context, this means a board where every open ticket is visible, its state is clear, and who owns it is explicit. Nothing hides in a queue that nobody can see.

**2. Limit work in progress (WIP).**
Set explicit limits on how much work can be in any given state at any time. A Tier 1 analyst who has fifteen open tickets cannot give any of them adequate attention. A WIP limit of five forces the team to finish work before starting new work — which improves quality and reduces the context-switching that kills productivity.

**3. Manage flow.**
The goal is smooth, continuous flow of work through the system — not maximum utilization of every individual. A ticket that sits in "waiting for customer" for three days is a flow problem. A team member who is 100% utilized has no capacity to handle a surge. Flow thinking optimizes the system, not the individual.

**4. Continuously improve.**
Kanban includes a regular cadence of reviewing the process and making targeted improvements. Not a big transformation — small, incremental changes based on what the data shows.

**Key Kanban metrics for operations:**

| Metric | Definition | Why It Matters |
|---|---|---|
| **Cycle Time** | Time from when work starts to when it is complete | Measures how long it actually takes to resolve an incident or fulfill a request — not the SLA target, the reality |
| **Lead Time** | Time from when work is requested to when it is complete | Includes queue wait time — tells the customer how long their experience actually is |
| **Throughput** | Number of items completed per time period | Measures team capacity — trending down signals a capacity or quality problem |
| **WIP** | Number of items actively in progress at any moment | High WIP relative to team size signals multitasking and context-switching problems |
| **Queue Age** | How long items have been waiting in queue | Tickets aging in queue are future SLA breaches |

---

## Section 3 — Where ITIL and Agile Conflict

### The Seven Specific Friction Points

These are not theoretical conflicts. They are the situations that create real operational problems in organizations running both frameworks. Naming them precisely is the first step to resolving them.

**Friction Point 1 — CAB Cadence vs. Deployment Frequency**

ITIL: Changes are reviewed at a weekly CAB meeting. Minimum 5 business days lead time for normal changes.

Agile/DevOps: Teams deploying continuously cannot wait 5 business days for every change review. A team running CI/CD may deploy dozens of times per day.

**Result:** Either the CAB becomes a bottleneck that the development team routes around — bypassing controls entirely — or the SDM spends all their time in emergency CABs convened for non-emergencies.

**Friction Point 2 — Change Documentation Requirements vs. Small Change Frequency**

ITIL: Every change requires a completed change record — implementation plan, rollback plan, risk assessment, test plan.

Agile/DevOps: A small code change that passes automated testing and is deployed via CI/CD pipeline does not need a five-field risk assessment. The automated test suite is the risk assessment.

**Result:** Either development teams fill out change records perfunctorily — treating documentation as a compliance exercise rather than a risk management tool — or they bypass the process entirely for small changes.

**Friction Point 3 — Change Freeze Windows vs. Sprint Completion**

ITIL: Change freeze windows protect critical business periods from production instability.

Agile/DevOps: Sprint cadences do not align to business calendar. A team completing a sprint during a change freeze has work ready to deploy with nowhere to deploy it.

**Result:** Work accumulates. When the freeze lifts, a large batch of changes deploys simultaneously — which is exactly the risk the freeze was designed to prevent.

**Friction Point 4 — Rollback Requirements vs. Continuous Delivery**

ITIL: Every change requires a documented rollback plan — specific steps to reverse the change if it fails.

Agile/DevOps: In a CI/CD environment, the rollback is a forward fix — the next deployment. Reverting a deployment in a microservices architecture may be impossible or more dangerous than deploying a fix.

**Result:** Rollback plans are written to satisfy the change record requirement — not because anyone intends to execute them. The control exists on paper but not in practice.

**Friction Point 5 — SLA Response Times vs. Development Team Availability**

ITIL: Sev 1 incidents require 15-minute executive notification and 4-hour resolution. On-call engineers must be available 24x7x365.

Agile/DevOps: Development teams work in sprints with defined sprint goals. An engineer pulled into a production incident during a sprint is not delivering sprint commitments.

**Result:** Either on-call coverage is inadequate because development teams resist interrupt-driven work, or sprint commitments are consistently missed because engineers are pulled into operations.

**Friction Point 6 — Problem Management Timelines vs. Sprint Velocity**

ITIL: Problem records from Sev 1 incidents should be resolved within defined timeframes. RCA findings generate action items that must be closed.

Agile/DevOps: Development teams prioritize sprint backlog items by business value. An operational stability fix that does not deliver customer-visible features competes with features for sprint capacity.

**Result:** PIR action items sit in the product backlog indefinitely — deprioritized in every sprint planning session because they do not deliver visible value. The same incident recurs.

**Friction Point 7 — Compliance and Audit Requirements vs. Agile Speed**

ITIL: In regulated environments, every production change must have a documented audit trail — approval records, implementation logs, test results.

Agile/DevOps: Automated CI/CD pipelines deploy changes without human approval steps. The pipeline IS the control — but regulators and auditors expect human approval records.

**Result:** Regulated organizations either slow down their CI/CD pipelines to insert approval gates, or they run two parallel processes — one for audit evidence and one for actual deployment — which defeats the purpose of both.

---

## Section 4 — Kanban for Service Desk Queue Management

### Applying Kanban to IT Operations

The service desk is a natural fit for Kanban. The work is visible, the states are defined, and the flow problems are the same ones Kanban was designed to solve — work piling up in queues, individuals overloaded while others are idle, tickets aging without anyone noticing.

### The Service Desk Kanban Board

A Kanban board for a service desk visualizes every active ticket in the system by its current state. In ServiceNow, this is the list view organized by state — but a physical or digital Kanban board makes the flow visible in a way a list view does not.

**Recommended columns for a service desk Kanban board:**

| Column | What Lives Here | WIP Limit |
|---|---|---|
| **New / Unacknowledged** | Tickets just created — not yet acknowledged by the team | None — but tickets here trigger SLA timers immediately |
| **Triage** | Analyst reviewing and classifying the ticket | 3–5 per analyst |
| **In Progress — Tier 1** | Actively being worked by Tier 1 | 3–5 per analyst |
| **Awaiting Customer** | Waiting for customer information or confirmation | No active work — monitor for aging |
| **Escalated — Tier 2** | Passed to Tier 2 for technical investigation | 3–5 per engineer |
| **Awaiting Vendor** | Waiting for third-party response | No active work — monitor for aging |
| **Resolved — Pending Close** | Resolution confirmed — awaiting formal closure | 24-hour maximum before closure |

### WIP Limits in Practice

A Tier 1 analyst with fifteen open tickets is not working fifteen tickets — they are context-switching between fifteen tickets and making slow progress on all of them. A WIP limit of five forces a different behavior: finish a ticket before picking up a new one.

**How to set WIP limits:**

Start with observation. For one week, track how many tickets are actively in progress per analyst at any given time. The average is the baseline. Set the WIP limit at 20% below that baseline — not so low it creates artificial constraints, but low enough to force prioritization.

Adjust over 30 days based on what the data shows. WIP limits that are too low create idle time. WIP limits that are too high have no effect. The right limit creates a slight constraint that forces the team to finish work rather than start new work.

**What happens when WIP limits are hit:**

When an analyst's WIP limit is reached, they do not pick up a new ticket. They either resolve one of their open tickets first, or they escalate a stuck ticket to remove it from their WIP. This is counterintuitive — it feels like stopping work. It is actually the opposite — it forces the team to clear blockers rather than accumulate them.

### Flow Metrics for the Service Desk

ServiceNow tracks the data needed for Kanban flow metrics. The reports need to be built — but the data is there.

**Cycle time by ticket category:**
How long does it actually take to resolve an incident, fulfill a request, or close a change? Not the SLA target — the actual cycle time. If the Sev 3 SLA target is 24 hours and the actual average cycle time is 31 hours, the SLA will be breached on average. The cycle time tells you the truth that the SLA compliance rate obscures.

**Queue age analysis:**
How old are the tickets currently sitting in each queue column? A ticket that has been in "Awaiting Customer" for six days is either about to breach SLA or has already breached. Queue age analysis surfaces these before they become escalations.

**Throughput by week:**
How many tickets did the team resolve this week compared to last week? Throughput declining while volume is stable signals a capacity or quality problem. Throughput increasing while quality metrics decline signals the team is closing tickets prematurely.

### The Daily Stand-Up — Kanban Style

A Kanban-style daily stand-up for a service desk team runs differently from a traditional status meeting. The focus is on flow — what is blocked, what is aging, what needs help — not on individual status updates.

**15-minute daily stand-up agenda:**

1. Walk the board right to left — start with tickets closest to resolution, not newest arrivals
2. Flag anything aging beyond 50% of its SLA window
3. Identify any ticket that has been in the same state for 24 hours — what is the blocker?
4. Confirm WIP limits are being respected — anyone over their limit?
5. Any tickets that need escalation or additional resources?

Walking the board right to left is deliberate. It forces the team to focus on finishing work in progress before starting new work — the core Kanban discipline.

---

## Section 5 — Agile Change Management in a DevOps Environment

### The Principle: Risk-Based Change Controls

The resolution to the ITIL vs. Agile change management conflict is not to eliminate change controls — it is to apply controls proportionally to risk. High-risk changes get full ITIL rigor. Low-risk, automated changes get lightweight controls appropriate to their risk profile.

This is not a new idea. ITIL already has this built in — the Standard Change type exists precisely for this reason. The problem is that most organizations have not designed their Standard Change Catalog to accommodate the full range of modern deployment patterns.

### Change Classification in a DevOps Environment

| Change Type | Definition | Approval Model | Review Cadence |
|---|---|---|---|
| **Automated deployment (pre-validated)** | Code change deployed via CI/CD pipeline that passes all automated tests, affects no infrastructure, and follows a defined deployment pattern | No human approval — pipeline IS the control | Post-deployment review in weekly CAB |
| **Standard change (catalog item)** | Pre-approved change type with documented procedure — no individual CAB review required | Pre-approved — implementer confirms catalog item | Quarterly catalog review |
| **Normal change (low risk)** | Planned change requiring CAB review — infrastructure, configuration, or code change outside CI/CD pipeline | Change Manager + one technical reviewer | Weekly CAB |
| **Normal change (high risk)** | Planned change with significant blast radius or complexity | Full CAB review + SDM + Security | Weekly CAB |
| **Emergency change** | Unplanned change required to restore service or address critical vulnerability | ECAB — convened within 2 hours | Post-implementation review at next CAB |

### The Pre-Approved Deployment Model

The pre-approved deployment model is how mature DevOps organizations satisfy both change management requirements and continuous delivery velocity. It works like this:

1. The development team and the SDM define the criteria for a pre-approved deployment:
   - All automated tests pass (unit, integration, end-to-end)
   - No infrastructure changes — application code only
   - Deployment follows the standard CI/CD pipeline — no manual steps
   - Deployment is to a defined set of services — not core infrastructure
   - Automatic rollback is configured — if deployment fails health checks, it rolls back automatically
   - Deployment size is bounded — no more than X services or Y lines of code in a single deployment

2. The CAB reviews and approves the pre-approved deployment model as a Standard Change — not individual deployments, the model itself.

3. Deployments that meet all criteria proceed without individual CAB review. A deployment record is created automatically in ServiceNow.

4. The CAB reviews a summary of all pre-approved deployments at the weekly meeting — not to approve them retroactively, but to identify any patterns that suggest the model needs adjustment.

**What the SDM gains:**
- Development teams deploy continuously without CAB bottleneck
- Every deployment is still recorded in ServiceNow — full audit trail exists
- High-risk changes still go through full CAB review
- The CAB focuses its time on changes that actually need scrutiny

**What the SDM gives up:**
- Individual review of every deployment — the automated controls are the review
- The ability to block a pre-approved deployment at the CAB gate — that gate no longer exists for qualifying deployments

This is a risk decision. The SDM makes it with full understanding of what is being traded.

### CI/CD Pipeline as a Change Control

In a mature DevOps environment, the CI/CD pipeline is a sophisticated control system. Understanding what it does — and what it does not do — is essential for the SDM deciding which change types can be pre-approved.

**What a CI/CD pipeline typically controls:**

| Control | What It Does | Equivalent ITIL Control |
|---|---|---|
| Automated unit tests | Verify that individual code components work as designed | Technical review of implementation plan |
| Automated integration tests | Verify that components work together correctly | System integration testing |
| Automated end-to-end tests | Verify that the full user workflow functions correctly | User acceptance testing |
| Security scanning | Identify known vulnerabilities in code or dependencies | Security review |
| Performance testing | Confirm deployment does not degrade response time | Performance impact assessment |
| Automated rollback | If deployment fails health checks, revert automatically | Rollback plan execution |
| Deployment gates | Require passing all controls before deployment proceeds | Go/No-Go checklist |

A CI/CD pipeline that includes all of these controls is a robust change management system. The SDM who understands this can make an informed argument to auditors and regulators that automated controls are at least as rigorous as manual approval gates — often more so.

**What a CI/CD pipeline does not control:**
- Business impact of the change — a technically successful deployment can still have the wrong business outcome
- Infrastructure changes — most CI/CD pipelines are designed for application code, not infrastructure
- Cumulative risk — a pipeline that approves each change in isolation does not assess the cumulative risk of forty changes deploying on the same day
- Rollback of data changes — automated rollback works for stateless application code; it does not work for database schema changes or data migrations

### Aligning CAB Cadence to Sprint Cadence

One practical adaptation that reduces friction without eliminating governance: align the CAB meeting to the end of the development sprint.

**The sprint-aligned CAB model:**

- Sprint ends Friday
- Sprint review is Friday afternoon — SDM participates or reviews output
- CAB meets Monday morning — reviews changes being deployed in the coming sprint
- Changes identified as high-risk in sprint planning are flagged early — not at CAB submission time

This model means the CAB is reviewing changes before they are built, not after they are ready to deploy. The development team gets earlier feedback on risk. The CAB gets earlier visibility into what is coming. The five-business-day submission window is satisfied naturally because the sprint review happens before the CAB.

---

## Section 6 — Retrospectives for Operations Teams

### What a Retrospective Is

A retrospective is a structured team reflection session — typically 60 to 90 minutes — where the team examines how they are working and identifies specific, actionable improvements. It is not a post-incident review. It is not a status meeting. It is a deliberate pause to look at the process — not just the output.

The retrospective format comes from Agile software development, where it is run at the end of every sprint. For operations teams, it runs on a monthly cadence — more frequent than quarterly business reviews, less frequent than daily stand-ups.

### Why Operations Teams Need Retrospectives

Post-incident reviews are reactive — they happen because something went wrong. Retrospectives are proactive — they happen on a schedule regardless of whether anything went wrong. The difference matters because the most significant operational improvements often come from examining work that went fine — and asking whether "fine" is good enough.

An operations team that only reflects when things break will optimize for fewer incidents. An operations team that reflects regularly will optimize for better ways of working — which leads to fewer incidents, but also to faster resolution, higher team satisfaction, and more consistent service quality.

### Retrospective Structure — 60 Minutes

The most widely used retrospective format asks the team to reflect on three questions:

**What went well?**
What should the team keep doing — or do more of? This is not a compliment session. It is an identification of practices that are working and should be protected when changes are made.

**What could be improved?**
What is slowing the team down, creating friction, or producing inconsistent results? This is the core of the retrospective. The team generates a list — without judgment — of everything that could be better.

**What will we do differently?**
From the improvement list, the team selects one to three items to act on before the next retrospective. Not everything — one to three. Each item has a named owner and a specific action, not a vague aspiration.

**Retrospective agenda:**

| Segment | Time | Activity |
|---|---|---|
| Set the stage | 5 min | Facilitator confirms the retrospective is blameless — we are examining the process, not the people |
| What went well | 15 min | Each team member contributes — facilitator captures on board |
| What could be improved | 20 min | Each team member contributes — facilitator captures without editing or judging |
| Dot voting | 5 min | Each team member votes for the top three improvements they want to address |
| Action item selection | 10 min | Top-voted improvements discussed — one to three selected, owner and due date assigned |
| Close | 5 min | Review action items, confirm next retrospective date |

### Retrospective Topics for Operations Teams

Beyond the standard three questions, operations retrospectives can focus on specific themes when the data suggests it:

| Theme | When to Use It | What to Examine |
|---|---|---|
| **Incident response** | After a month with high Sev 1/2 volume | What slowed resolution? What communication broke down? What would have helped? |
| **Change management** | After a month with rollbacks or change-induced incidents | What was missed in the approval process? What should have been caught earlier? |
| **Queue management** | When SLA compliance is declining | Where is the backlog building? What is causing delays? |
| **Team capacity** | When team members are consistently working beyond hours | Where is the demand spike coming from? What can be automated or eliminated? |
| **Customer feedback** | After negative CSAT scores | What did the customer experience that the team did not see? |
| **Process friction** | When the team raises process complaints repeatedly | Which process steps are adding work without adding value? |

### Connecting Retrospective Findings to Continuous Improvement

Retrospective action items are documented in ServiceNow as improvement tasks — not in a meeting notes document that gets filed and forgotten. Each action item has:

- Specific description — what will be done
- Named owner — one person
- Due date — before the next retrospective
- Link to the retrospective record — for trend tracking

At the next retrospective, the first agenda item is reviewing action items from the previous session. An action item that carries over more than once without progress is a signal — either the action is too large, the owner lacks capacity, or the team is not committed to the improvement.

The retrospective findings are summarized and included in the monthly operations review. Over time, they become the evidence of a team that is continuously improving — not just responding to incidents.

---

## Section 7 — Practical Implementation — Where to Start

### The Sequencing That Matters

Introducing Agile service management concepts into a traditional ITIL environment is not a big-bang transformation. It is a sequence of targeted changes — each one building on the last. The wrong sequence creates confusion and resistance. The right sequence creates visible wins that build momentum.

**Start here — the changes that deliver immediate value with minimal disruption:**

**Month 1 — Visualize the queue.**
Build a Kanban board for the service desk — even if it is just a ServiceNow list view organized by state with swim lanes. Make the work visible. No process changes yet — just visibility. Run the daily stand-up walking the board right to left. Track cycle time and queue age for one month.

**Month 2 — Introduce WIP limits.**
Based on one month of data, set WIP limits per analyst. Start conservative — 20% below the observed average. Run for 30 days. Measure throughput and cycle time. Adjust limits based on what the data shows.

**Month 3 — Run the first retrospective.**
Introduce the retrospective format. Keep it simple — the three questions, 60 minutes, one to three action items. The goal is not a perfect retrospective — it is a team that experiences the format and finds it useful.

**Month 4 — Review the Standard Change Catalog.**
Audit the existing Standard Change Catalog. What change types are currently going through full CAB review that could be pre-approved? Work with the development team to identify deployment patterns that qualify for pre-approved status. Build the model. Present to CAB for approval.

**Month 6 — Sprint-aligned CAB.**
If the organization runs Scrum, propose aligning the weekly CAB to the sprint cadence. Not a replacement for the CAB — a scheduling change that reduces friction by giving the CAB earlier visibility into what is being deployed.

### What Not to Change

Some things that look like friction between ITIL and Agile are not worth changing. The cost of changing them exceeds the benefit.

**Do not eliminate the CAB for high-risk changes.**
The CAB exists for a reason. Infrastructure changes, security-impacting changes, changes affecting multiple production systems — these deserve human review regardless of how frequently the organization deploys. The pre-approved model applies to low-risk, automated deployments. It does not apply to everything.

**Do not eliminate post-incident reviews.**
The Agile retrospective is not a replacement for the PIR. They serve different purposes. The PIR is reactive and specific — what caused this incident. The retrospective is proactive and systemic — how do we work better. Both belong in a mature operations environment.

**Do not abandon documentation requirements in regulated environments.**
Automated CI/CD pipelines can generate deployment records automatically. But in regulated environments, certain audit evidence requirements cannot be satisfied by automated records alone. Work with the compliance team to understand exactly what the auditors require — then design the minimum documentation that satisfies those requirements without creating unnecessary overhead.

**Do not introduce Scrum ceremonies into an operations team.**
Operations work is not sprint work. Incidents do not respect sprint boundaries. Applying Scrum's sprint structure to an operations team creates artificial constraints — sprint commitments that get blown up by the first Sev 1 incident. Kanban is the right framework for operations. Scrum is the right framework for development. Use each where it fits.

---

## Section 8 — Common Mistakes When Mixing Agile and ITIL

| Mistake | What It Looks Like | What It Costs |
|---|---|---|
| **Eliminating change controls entirely** | Development team convinces leadership that ITIL is "legacy" — CAB disbanded, all changes pre-approved | First major change-induced incident in production. Regulators or auditors flag absence of controls. SDM has no audit trail. |
| **Applying Scrum to operations teams** | Operations team runs sprints with sprint goals and backlog grooming | First Sev 1 incident blows up the sprint. Team loses confidence in the process. |
| **Pre-approving high-risk changes** | Pre-approved deployment model applied to infrastructure or security changes to avoid CAB friction | High-risk change fails in production. No human review caught it. |
| **Treating retrospectives as complaint sessions** | Retrospective becomes a list of grievances with no action items | Team loses confidence in the format. Retrospectives stop happening. |
| **WIP limits set too low** | Analysts cannot pick up new tickets while others are waiting | Throughput drops. SLA compliance declines. Team becomes frustrated with artificial constraints. |
| **Sprint-aligned CAB without development buy-in** | SDM aligns CAB to sprint cadence unilaterally | Development team ignores the alignment. Changes still submitted the day before CAB. |
| **Agile metrics replacing ITIL metrics** | Cycle time and throughput replace SLA compliance as the primary performance metrics | Customer SLA commitments are breached. Customer does not care about cycle time — they care about the contracted response time. |
| **Retrospective action items not tracked** | Action items captured in meeting notes but not in ServiceNow | Same issues raised at every retrospective. Team loses faith that anything changes. |
| **CI/CD pipeline assumed to be sufficient in regulated environment** | Automated deployment treated as equivalent to human approval for audit purposes | Audit finding. Regulator requires manual approval gates. Velocity loss is larger than if the issue had been addressed proactively. |
| **Mixing frameworks without a clear rationale** | Organization adopts Agile terminology without changing the underlying process | "We run Agile CAB" means nothing. The process is the same. The vocabulary changed. |

---

## Appendix A — Framework Comparison Quick Reference

| Dimension | Traditional ITIL | Agile/DevOps | Adapted Model |
|---|---|---|---|
| **Change frequency** | Infrequent — weekly or less | High — daily or continuous | Tiered by risk — high frequency for low-risk, full process for high-risk |
| **Approval model** | Human review — CAB | Automated — pipeline | Risk-based — automated for pre-approved, human for normal and high-risk |
| **Change lead time** | 5 business days minimum | Hours or minutes | Varies by type — 0 for pre-approved, 5 days for normal |
| **Rollback model** | Documented manual rollback plan | Automated rollback or forward fix | Automated where possible, documented where required |
| **Team structure** | Functional silos — dev, ops, support | Cross-functional — devops team owns full lifecycle | Collaboration model — shared on-call, shared incident response |
| **Improvement cadence** | Post-incident reviews — reactive | Sprint retrospectives — regular | Both — PIR for incidents, retrospective for team practices |
| **Documentation** | Comprehensive — audit-ready | Lean — just enough | Compliance-minimum — satisfies audit requirements without overhead |
| **Performance metrics** | SLA compliance, MTTR | Deployment frequency, lead time | Both — operational health and delivery velocity |

---

## Appendix B — Glossary

| Term | Definition |
|---|---|
| **Agile** | A set of values and principles for iterative, collaborative software development — not a specific process |
| **Scrum** | The most widely used Agile framework — work organized into fixed-length sprints with defined ceremonies |
| **Kanban** | A workflow management method that visualizes work, limits WIP, and optimizes flow |
| **DevOps** | A set of practices that combines software development and IT operations — emphasizing automation, continuous delivery, and shared accountability |
| **CI/CD** | Continuous Integration / Continuous Delivery — automated pipelines that build, test, and deploy software continuously |
| **WIP** | Work in Progress — the number of items actively being worked at any point in time |
| **Cycle Time** | Time from when work starts to when it is complete |
| **Lead Time** | Time from when work is requested to when it is complete — includes queue wait time |
| **Throughput** | Number of items completed per time period |
| **Sprint** | Fixed time period (typically 2 weeks) in Scrum during which the team delivers a defined set of work |
| **Retrospective** | Structured team reflection session — what went well, what could be improved, what will we do differently |
| **Pre-approved deployment** | A deployment that meets defined criteria and proceeds without individual CAB review |
| **Sprint-aligned CAB** | A CAB meeting scheduled to align with sprint cadence — providing visibility into upcoming deployments before they are built |
| **Flow** | The smooth, continuous movement of work through a system — the goal of Kanban |
| **SAFe** | Scaled Agile Framework — a framework for applying Agile practices at enterprise scale |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | August 2026 | Initial release | Scott Boehler |

---

*The goal is not to choose between ITIL and Agile. The goal is a production environment that is stable, a delivery pipeline that is fast, and an operations team that is continuously getting better. Both frameworks contribute to that goal when they are applied where they fit.*
