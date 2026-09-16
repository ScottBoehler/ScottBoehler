# Problem Management & Root Cause Analysis Guide
### IT Operations & Managed Services | From Incident to Prevention to Continuous Improvement

**Author:** Scott Boehler — Service Delivery & Operations Leader | Six Sigma Green Belt  
**Version:** 2.0  
**Last Updated:** September 2026  
**Applies To:** IT operations teams, service delivery managers, incident commanders, and problem managers responsible for preventing recurrence of production incidents and governing the full problem management lifecycle

---

## Purpose & Scope

Resolving an incident stops the bleeding. Problem Management prevents it from happening again.

Most operations teams treat these as the same activity — they close the incident, write up what happened, and call it done. They are not the same activity. Incident Management restores service. Problem Management eliminates the conditions that caused the failure. The difference between an operations team that improves over time and one that runs the same incidents on a rotating schedule is almost always whether they have a functioning Problem Management practice — not whether they have good engineers.

This guide covers the full Problem Management lifecycle — from the moment a problem record is created through root cause analysis, known error management, permanent fix implementation, and closure. It also covers RCA methodology in depth — how to choose the right tool, how to run a session that produces actionable findings, and how to close the loop so findings drive real change.

The Six Sigma Green Belt credential informs this guide. The two decades of production incident management inform it more.

---

## Section 1 — What Problem Management Actually Is

### The ITIL Definition — In Plain Language

Problem Management is the process that manages the lifecycle of all problems. A problem is the underlying cause of one or more incidents. The goal is to identify that cause, document it, implement a permanent fix where possible, and prevent the incident from recurring.

Three terms are used precisely in this guide:

| Term | Definition |
|---|---|
| **Incident** | An unplanned interruption to a service — the symptom. Managed by Incident Management. |
| **Problem** | The underlying cause of one or more incidents — the disease. Managed by Problem Management. |
| **Known Error** | A problem where the root cause has been identified but the permanent fix has not yet been implemented. A workaround may exist. |

An incident is what the customer experiences. A problem is what the SDM investigates. A known error is what the support team manages until the fix is in place.

### Reactive vs. Proactive Problem Management

Problem Management operates in two modes. Most teams only practice the first one.

**Reactive Problem Management** — triggered by incidents. A Sev 1 or Sev 2 occurs, gets resolved, and triggers a problem record and RCA. The goal is to find the root cause and prevent recurrence.

**Proactive Problem Management** — triggered by trend analysis. The team reviews incident data, identifies patterns, and opens problem records for recurring issues before they escalate into major incidents. A team that notices three Sev 3 incidents in one month all involving the same application component does not wait for the Sev 1 — they open a problem record and investigate.

The difference between reactive and proactive Problem Management is the difference between a team that responds to fires and a team that prevents them. Both matter. Most teams only do the first.

### The Problem Manager Role

The Problem Manager is accountable for driving every open problem record to closure. In smaller organizations, the SDM fills this role. In larger organizations, it is a dedicated function. Either way, the responsibilities are the same:

- Create problem records from qualifying incidents — on time, not when convenient
- Assign root cause analysis and drive it to completion
- Maintain the Known Error Database — current and accessible
- Track action items to closure — not just to assignment
- Report problem management metrics monthly
- Identify patterns across incidents and open proactive problem records
- Ensure change requests are raised for permanent fixes and linked to the problem record

The Problem Manager does not do the RCA alone. They facilitate the process and own the outcome.

---

## Section 2 — The Problem Record Lifecycle

### When a Problem Record Is Created

| Trigger | Required | Notes |
|---|---|---|
| Sev 1 incident closed | Yes — always | No exceptions. Every Sev 1 generates a problem record. |
| Sev 2 incident closed | Yes — always | No exceptions. Every Sev 2 generates a problem record. |
| Recurring Sev 3 incidents | Yes — at SDM discretion | Three or more Sev 3 incidents with the same root cause in 30 days triggers a problem record. |
| Proactive identification | Yes — at Problem Manager discretion | Trend analysis identifies a failure pattern before a major incident occurs. |
| Sev 4 incidents | No | Not required. Reviewed if a pattern emerges. |

**The timing rule:** Problem records are created immediately after incident closure — not after the PIR, not after the RCA session, not when the Problem Manager has time. Immediately. The incident timeline and work notes are the freshest data available. Waiting lets that data degrade.

### Problem Record States

ServiceNow manages the problem record through defined states. Each state has a specific meaning and specific activities associated with it.

| State | Meaning | What Happens Here |
|---|---|---|
| **New** | Problem record created — not yet assigned | Problem Manager reviews and assigns within 24 hours |
| **Assess** | Under investigation — RCA in progress | Root cause analysis conducted. PIR scheduled and held. |
| **Root Cause Identified** | Root cause documented — fix in progress | Workaround documented in KEDB if applicable. Change request raised. |
| **Known Error** | Root cause identified — fix not yet implemented | KEDB entry active. Workaround available for support team. |
| **Resolved** | Permanent fix implemented and confirmed | Fix verified in production. KEDB entry updated or closed. |
| **Closed** | Problem closed — all action items complete | Final documentation complete. Problem record archived. |

### The Full Lifecycle

```
Sev 1/2 Incident Resolved
    |
Problem record created in ServiceNow (within 24 hrs)
    |
Problem assigned to Problem Manager
    |
PIR scheduled (Sev 1: within 48 hrs / Sev 2: within 72 hrs)
    |
RCA session conducted — root cause identified
    |
Root cause documented in Problem record
    |
    |-- Fix available --> Change request raised --> Fix implemented --> Problem resolved
    |-- Fix not ready --> Known Error in KEDB --> Workaround documented
                              |
                        Fix scheduled --> Change request raised --> Fix implemented
                              |
                        KEDB entry closed --> Problem resolved
    |
All action items confirmed closed
    |
Problem record closed
```

### Required Fields — Problem Record

The problem record must be complete enough to stand alone as an audit artifact. Six months after closure, anyone reading it should understand what happened, what caused it, what was done about it, and how the fix was confirmed.

| Field | What to Capture | Timing |
|---|---|---|
| **Problem Statement** | Specific, measurable description of the failure — not the incident title | At creation |
| **Linked Incidents** | All incident records caused by this problem | At creation |
| **Affected Services** | Systems, applications, infrastructure components involved | At creation |
| **Category** | Primary cause category — Technology, Process, People, Monitoring, Environment | At creation |
| **Assigned To** | Problem Manager — one named individual | At creation |
| **Target Resolution Date** | Based on severity and business impact | At creation |
| **Root Cause** | The specific process, system, or gap that allowed the failure | After RCA |
| **Contributing Factors** | All causes identified in the fishbone — not just the primary root cause | After RCA |
| **Timeline** | Sequence of events from detection to resolution — from work notes and monitoring data | After RCA |
| **Workaround** | Interim steps to restore service if the failure recurs before permanent fix | After RCA if applicable |
| **Permanent Fix** | What change will resolve the root cause permanently | After RCA |
| **Change Request Number** | ServiceNow CHG record linked to the permanent fix | When change raised |
| **Fix Confirmed** | Verification that the permanent fix resolved the root cause | After fix implemented |
| **Close Notes** | Final summary — what was learned, what changed | At closure |

---

## Section 3 — Known Error Database (KEDB)

### What the KEDB Is

The Known Error Database is a catalog of documented failure modes — problems where the root cause is known but the permanent fix is not yet in place. Each KEDB entry gives the support team what they need to handle a recurrence quickly — without re-investigating or escalating.

A KEDB that is current and maintained turns a 90-minute Sev 2 into a 15-minute Sev 3. A KEDB that is empty or outdated means every recurrence is investigated from scratch by a team that may not know the failure has happened before.

### What a KEDB Entry Contains

| Field | Content |
|---|---|
| **Known Error Title** | One-line description of the failure mode — what it looks like when it occurs |
| **Linked Problem Record** | ServiceNow PRB number — full audit trail |
| **Symptoms** | What the support team sees when this failure mode occurs — alerts, user reports, monitoring data |
| **Trigger Conditions** | What causes it — what must be true for this failure to happen |
| **Workaround** | Step-by-step instructions to restore service temporarily — specific enough to follow without investigation |
| **Workaround Owner** | Who is accountable for confirming the workaround still works |
| **Permanent Fix** | What will resolve this permanently |
| **Fix ETA** | When the permanent fix is expected — linked to the change request |
| **KEDB Status** | Active (fix in progress) / Resolved (fix implemented) / Closed (confirmed resolved) |

### KEDB Search From the Incident Record

The KEDB only has value if the support team uses it. Before any Sev 1 or Sev 2 investigation goes deeper than 15 minutes, the analyst checks the KEDB. If a matching entry exists, the workaround is applied. If it resolves the incident, the Problem Manager is notified and the KEDB hit is logged in the incident work notes.

A KEDB hit that resolves an incident is not a success story — it is evidence that the permanent fix has not been implemented on schedule. The Problem Manager investigates why.

### KEDB Governance

| Activity | Frequency | Owner |
|---|---|---|
| New KEDB entries created from RCA findings | Within 48 hours of PIR | Problem Manager |
| Existing entries reviewed for accuracy | Monthly | Problem Manager |
| Entries marked Resolved when fix confirmed in production | Within 24 hours of fix confirmation | Problem Manager |
| Stale entries reviewed — fix overdue | Monthly | Problem Manager + SDM |
| KEDB utilization report reviewed | Monthly | Problem Manager + SDM |

**The stale entry problem:** A KEDB entry where the fix ETA has passed and the status is still Active is a red flag. Either the fix was not implemented on schedule — which needs to be investigated — or the entry was never updated after the fix went in. Both are governance failures. Monthly KEDB review catches them before they compound.

---

## Section 4 — Why Most RCA Fails Before It Starts

Most RCA processes fail not because the team chose the wrong tool — they fail because the foundation is broken before the session begins. Three failure modes account for the majority of RCA that produces no lasting improvement.

### Failure Mode 1 — The Problem Statement Is Wrong

The most common RCA failure is a vague or symptom-level problem statement. If the problem statement is wrong, every cause identified will be wrong too — because the team is analyzing the wrong problem.

**Symptom-level problem statement:**
> "The application was slow last Tuesday."

**Problem statement that enables RCA:**
> "Between 14:32 and 16:47 on Tuesday, average API response times for the customer portal exceeded 8 seconds, affecting 340 active users and generating 47 P2 support tickets. Normal response time is under 500ms."

A good problem statement answers:
- **What** is the defect or failure — precisely, not generally?
- **When** did it start and when did it end?
- **Who** or **what** was affected — and how many?
- **What is the baseline** — what does normal look like?
- **What is the magnitude** — how far from normal were we?

If the team cannot answer all five questions before the RCA session starts, the session should be postponed until they can.

### Failure Mode 2 — The Culture Is Blameful

A blameful RCA session produces one outcome: people protect themselves. They do not share what they actually saw, they do not admit what they did not know, and they do not identify causes that implicate themselves or their team.

Blameless RCA is not about letting people off the hook. It is about recognizing that most production failures involve multiple contributing factors — a decision that seemed reasonable at the time, a process that did not catch the error, a monitoring gap that allowed the problem to grow before detection. Fixing the person solves nothing if the system that allowed the failure remains intact.

The facilitator sets the tone in the first two minutes. If the opening is "let's figure out what went wrong and who is responsible," the session will be defensive. If the opening is "let's understand what the system allowed to happen and what we change so it cannot happen again," the session will be honest.

### Failure Mode 3 — Stopping at the First Plausible Cause

The first cause that sounds reasonable is almost never the root cause. It is the proximate cause — the last thing that happened before the failure.

> "The server ran out of disk space."

That is a proximate cause. The root cause is why the server ran out of disk space when monitoring should have caught it at 80% capacity, why the alert fired but was not acknowledged, why the log rotation process had not run in 11 days, and why no one noticed until users reported a failure.

Every RCA must go at least two levels deeper than the first plausible cause. The test: if you implemented the fix identified by this cause, could this failure mode still occur through a different path? If yes, you have not reached the root cause.

---

## Section 5 — Choosing the Right RCA Tool

RCA is not one tool — it is a toolkit. Choosing the wrong tool for the problem at hand wastes time and produces incomplete findings.

### RCA Tool Decision Framework

| Situation | Best Tool | Why |
|---|---|---|
| Single, well-defined failure with a clear sequence of events | 5 Whys | Fast, focused, follows one causal chain to the root |
| Multiple possible cause categories, unknown which contributed | Fishbone Diagram | Structured brainstorming across cause categories prevents tunnel vision |
| Complex system with multiple interacting failure points | Fault Tree Analysis | Maps logical dependencies and probabilities |
| Recurring incidents — identifying which cause category to prioritize | Pareto Analysis | 80/20 principle applied to incident data |
| Post-major-incident with cross-functional team | Fishbone + 5 Whys combined | Fishbone identifies categories, 5 Whys drills into highest-priority causes |
| Problem with clear data available (error rates, volume, timing) | Pareto + scatter plot | Data-driven prioritization before qualitative RCA |

### When NOT to Use a Fishbone

The fishbone diagram is a brainstorming tool — it generates hypotheses, not confirmed root causes. Do not use it when:

- The problem statement is not yet defined — the diagram will fill up with guesses
- The team is too small or too homogeneous — you need cross-functional perspective to populate it meaningfully
- Data is available and sufficient to identify the cause directly — use the data first, brainstorm second
- The failure involves a highly complex multi-system interaction — fault tree analysis handles interdependencies better

### When NOT to Use 5 Whys

5 Whys works well for focused, linear causal chains. It breaks down when:

- Multiple independent causes contributed — a single chain of whys misses the others
- The team lacks knowledge depth to answer the whys accurately — bad answers compound into a wrong root cause
- The problem involves systemic or organizational factors — 5 Whys tends to land on individual actions rather than system failures

---

## Section 6 — The Fishbone Diagram in IT Operations

### The 6 M's Translated for IT Operations

| Traditional Category | IT Operations Translation | Examples in Production Incidents |
|---|---|---|
| **Manpower** | **People** | Insufficient staffing, skill gaps, inadequate training, alert fatigue, on-call rotation gaps |
| **Methods** | **Process** | Missing runbooks, outdated procedures, no change freeze, inadequate testing, skipped steps |
| **Machines** | **Technology** | Hardware failure, software bugs, capacity limits, deprecated dependencies, misconfiguration |
| **Materials** | **Data / Inputs** | Corrupt data, API payload errors, bad configuration files, third-party data quality |
| **Measurement** | **Monitoring & Alerting** | Monitoring gaps, alert threshold misconfiguration, no baseline defined, SLA timer misconfigured |
| **Mother Nature** | **Environment** | Network provider outages, cloud region failures, power events, security incidents outside control |
| **Management / Governance** | **Management** | Prioritization decisions, resource allocation, change approval failures, risk acceptance without mitigation |

### Building the Fishbone — IT Operations Style

**Step 1 — Write the problem statement at the head of the fish**
The specific, measurable problem statement — not a summary. If it does not fit in one sentence, it is not specific enough.

**Step 2 — Draw the backbone and ribs**
Six to seven ribs — one per category. Do not start filling in causes yet.

**Step 3 — Populate causes by category — cross-functionally**
Each rib populated by the people who actually work in that domain. Do not let one person fill in all the ribs — if the SDM fills every category, the diagram reflects one perspective, not a cross-functional analysis.

**Step 4 — Go two levels deep on each rib**

Example:
```
Technology
  └── Monitoring gap
        └── Alert threshold set too high (90% disk) — never fired at 80%
              └── No standard for threshold configuration — each team sets their own
```

The third level is where you find something you can actually fix.

**Step 5 — Mark the highest-probability causes**
Team votes or uses data to prioritize top three to five causes. These become the inputs to the 5 Whys exercise.

---

## Section 7 — 5 Whys in Practice

**Example — IT Operations context:**

```
Problem: Database server went offline during business hours — 90-minute outage

Why offline? → Disk volume reached 100% — database process crashed
Why disk full? → Log files not rotated — accumulated 23 days
Why not rotated? → Log rotation job disabled during maintenance 3 weeks ago
Why disabled? → Causing performance spike during maintenance window
Why not re-enabled? → No post-maintenance checklist — re-enabling was not a documented step

ROOT CAUSE: No post-maintenance validation checklist exists to confirm
all suspended processes are restored after a maintenance window.
```

The fix is not "re-enable the log rotation job." That fixes this instance. The fix is "create a post-maintenance validation checklist required in every maintenance change record." That prevents this class of failure.

### Where 5 Whys Breaks Down

**The chain drifts.** Each why should follow directly from the previous answer. If the team starts answering a different question, the chain has drifted and the root cause will be wrong.

**The team runs out of knowledge.** "I don't know" is information — stop, get the data, then resume.

**The chain lands on a person.** "Because [name] forgot" is not a root cause. Ask why the system allowed that person to forget.

**Multiple chains exist.** If the failure had more than one contributing cause, run 5 Whys separately for each major cause.

### Combining Fishbone and 5 Whys

1. **Fishbone** to identify all possible cause categories across the full system
2. **Prioritization** to identify the two or three most likely causes
3. **5 Whys** on each prioritized cause to drill to the actionable root cause

The fishbone prevents tunnel vision. The 5 Whys prevents surface-level fixes.

---

## Section 8 — RCA Session Facilitation Guide

### Who to Invite

**Always include:**
- Incident Commander or Service Delivery Manager — owns the problem record
- Technical Lead who worked the incident
- One engineer per affected system or service
- Problem Manager — facilitates and owns the action items

**Include when relevant:**
- Vendor or MSP representative — if third-party systems were involved
- Change Manager — if a recent change contributed
- Monitoring / NOC lead — if detection gaps were identified

**Do not include:**
- Executives — their presence changes the dynamic and produces defensive answers
- People with no knowledge of the incident — they fill silence with speculation
- More than 8 to 10 people total

### Session Structure — 90 Minutes

| Time | Activity |
|---|---|
| 0:00 – 0:10 | Facilitator opens — blameless framing, rules of engagement, timeline review |
| 0:10 – 0:20 | Problem statement confirmed |
| 0:20 – 0:50 | Fishbone population — each category populated by relevant team members |
| 0:50 – 1:00 | Cause prioritization — team votes or uses data |
| 1:00 – 1:20 | 5 Whys on top one to two causes |
| 1:20 – 1:30 | Action items — specific, named owner, due date — entered in ServiceNow before session closes |

### Opening the Session — Blameless Framing

> "The goal of this session is to understand what the system allowed to happen — not to find who to blame. Every cause we identify today is a process, a tool, a gap, or a design decision. When we name a person, we ask why the system put that person in a position to fail. The output is a Problem record with action items, not a list of names."

### Preventing HiPPO Effect

**Silent brainstorming first.** Before any discussion, each participant writes their top three suspected causes. Collect and post all causes before anyone speaks.

**Junior voices first.** When opening discussion on each rib, ask the most junior person in that domain to speak first.

**Challenge the first cause.** "Good. What else could have caused this? If that cause hadn't been present — could this still have happened?"

**Data validates, not anchors.** Use data to prioritize causes after brainstorming — not to eliminate causes before brainstorming begins.

### Closing the Session — Action Items That Actually Get Done

Before anyone leaves the room, every action item has:
1. **Specific description** — "Configure disk utilization alert to 80% on all production database servers" not "improve monitoring"
2. **Named owner** — one person, not a team
3. **Due date** — specific calendar date
4. **ServiceNow Problem Task created and linked**

---

## Section 9 — Connecting Problem Management to ServiceNow

| Action | Where in ServiceNow |
|---|---|
| Create problem record | Problem → Create New |
| Link to incident records | Problem record → Related Records → Add Relationship |
| Document root cause | Problem record → Root Cause field |
| Create Known Error | Problem record → Create Known Error button |
| Add KEDB workaround | Known Error record → Workaround field |
| Create problem task | Problem record → Related Records → Create Task |
| Link to change request | Problem record → Related Records → Add Relationship |
| Close problem record | Problem record → State → Closed + Close Notes |
| Search KEDB from incident | Incident form → Related Records → Known Errors |

Every root cause that requires a change to a system, process, or configuration generates a Change Request linked to the Problem record. The linkage in ServiceNow — Problem record → Change Request → Incident records — creates a complete audit trail. Six months later, when someone asks "what did we do about that outage in May?" the answer is one click away.

---

## Section 10 — Common Problem Management and RCA Mistakes

| Mistake | What It Looks Like | What It Costs |
|---|---|---|
| **Problem record created late** | PIR happens, findings in slides, problem record created weeks later | Timeline data lost. RCA built on memory. |
| **Stopping at proximate cause** | "Root cause: disk full. Fix: expanded disk." | Same failure recurs on a different server |
| **Blameful PIR** | Meeting minutes include names next to errors | Engineers stop attending honestly. Next PIR is less useful. |
| **RCA without cross-functional input** | SDM and one engineer fill the fishbone | Entire cause categories missed |
| **Action items without owners** | "Improve monitoring" with no name attached | Nothing happens. Same incident recurs. |
| **Problem record never linked to incidents** | Problem exists in isolation | Cannot measure repeat incident rate or trace patterns |
| **KEDB not maintained** | Root cause identified, fix in progress, no KEDB entry | Front-line team escalates every recurrence |
| **Known Error never closed after fix** | Fix deployed months ago, KEDB still Active | Support team applies workaround unnecessarily. KEDB loses credibility. |
| **Fix validated at implementation only** | Change deployed, incident drops briefly, team moves on | Root cause partially addressed. Incident recurs in six months. |
| **Proactive Problem Management never practiced** | Team only opens problems after major incidents | Patterns invisible until they become Sev 1s |

---

## Section 11 — Metrics & Continuous Improvement

| Metric | Definition | Target | Source |
|---|---|---|---|
| **PIR Completion Rate** | % of Sev 1/2 incidents with completed Problem records and documented RCA | 100% | ServiceNow Problem records linked to incidents |
| **Time to Root Cause** | Average time from incident closure to documented root cause | Trending down | ServiceNow timestamps |
| **Action Item Closure Rate** | % of Problem Tasks closed by due date | ≥90% | ServiceNow Problem Tasks |
| **Repeat Incident Rate** | % of incidents caused by a previously identified root cause | <10% | ServiceNow — incidents linked to known errors |
| **KEDB Utilization Rate** | % of recurring incidents where a KEDB entry was referenced | Trending up | ServiceNow Known Error records |
| **MTBF** | Mean Time Between Failures — average time between recurrences of the same failure mode | Trending up | Calculated from ServiceNow incident history |
| **Known Errors Past Fix ETA** | Count of KEDB entries where fix ETA passed and status still Active | Zero target | ServiceNow Known Error filter |

### Monthly Problem Management Review

Once a month the Problem Manager reviews open and recently closed Problem records with the SDM:

1. How many Sev 1 and Sev 2 incidents — how many have completed problem records?
2. How many RCA action items are open past due date — and why?
3. What patterns emerging — same cause category appearing repeatedly?
4. Is the KEDB current — stale entries, missing entries?
5. Are repeat incidents declining month over month?
6. Any proactive problem candidates — recurring Sev 3 patterns not yet in a problem record?

Pattern identification is the most valuable output of the monthly review. A single incident with a Process root cause is a problem to fix. Three incidents in one month with Process root causes is a systemic problem requiring a different level of intervention.

### The Ultimate Test

Are you running the same incidents you ran six months ago?

If yes — the Problem Management process is producing documentation, not improvement. If no — the process is working. That is the only outcome that matters.

---

## Appendix A — Quick Reference

### Problem Record Creation Triggers
- [ ] Sev 1 closed → problem record required — no exceptions
- [ ] Sev 2 closed → problem record required — no exceptions
- [ ] Three+ Sev 3 incidents same root cause in 30 days → at SDM discretion
- [ ] Proactive pattern identified → at Problem Manager discretion

### Problem Statement Checklist
- [ ] What failed — specifically?
- [ ] When did it start and end?
- [ ] Who or what was affected — how many?
- [ ] What is the baseline?
- [ ] What is the magnitude?

### RCA Tool Selection
- Single linear failure → **5 Whys**
- Multiple possible causes → **Fishbone + 5 Whys**
- Complex multi-system → **Fault Tree Analysis**
- Recurring incidents — prioritize focus → **Pareto Analysis**

### Fishbone Categories — IT Operations
People | Process | Technology | Data/Inputs | Monitoring | Environment | Management

### Action Item Requirements
- [ ] Specific description of what will be done
- [ ] Named individual owner — not a team
- [ ] Due date — specific calendar date
- [ ] Entered in ServiceNow as Problem Task before session closes

### KEDB Entry Requirements
- [ ] Symptoms — what it looks like when it occurs
- [ ] Trigger conditions — what causes it
- [ ] Workaround — step-by-step, specific enough to follow without investigation
- [ ] Permanent fix and ETA
- [ ] Linked to Problem record in ServiceNow

---

## Appendix B — RCA Documentation Template

```
PROBLEM RECORD: [PRB number]
INCIDENT(S): [INC numbers]
DATE OF INCIDENT:
SEVERITY:
DURATION: Detection to Resolution

PROBLEM STATEMENT:
[Specific, measurable — what failed, when, who affected, magnitude]

ROOT CAUSE:
[One to two sentences — the specific process, system, or gap that allowed the failure]

CONTRIBUTING FACTORS:
-
-
-

TIMELINE:
[Time] — [Event — source: work notes / monitoring]
[Time] — [Event]

WHAT WENT WELL:
-
-

WHAT NEEDS IMPROVEMENT:
-
-

ACTION ITEMS:
| # | Action | Owner | Due Date | Priority | ServiceNow Task |
|---|---|---|---|---|---|
| 1 | | | | | |
| 2 | | | | | |

KNOWN ERROR DATABASE:
Workaround documented? [Yes / No]
KEDB record number (if applicable):

PERMANENT FIX:
Change request number:
Expected implementation date:

PIR FACILITATED BY:
DATE:
```

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release as RCA Field Guide | Scott Boehler |
| 2.0 | September 2026 | Expanded to full Problem Management & RCA Guide — added Problem Management lifecycle, KEDB governance, problem record states, proactive problem management, metrics, and ServiceNow quick reference. Renamed from RCA_Field_Guide.md to Problem_Management_RCA_Guide.md | Scott Boehler |

---

*The goal of Problem Management is not to produce a document. It is to produce a system that cannot fail the same way twice. RCA finds the root cause. Problem Management ensures the fix actually gets implemented — and stays implemented.*
