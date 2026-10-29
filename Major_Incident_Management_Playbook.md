# Major Incident Management Playbook
### IT Operations & Managed Services | Running the Incident — Not Just Attending It

**Author:** Scott Boehler — Service Delivery & Operations Leader | Six Sigma Green Belt  
**Version:** 1.0  
**Last Updated:** October 2026  
**Applies To:** Major Incident Managers, incident commanders, service delivery managers, and on-call leaders responsible for restoring service during Severity 1 and Severity 2 events

---

## Purpose & Scope

The [Incident Management Runbook](https://github.com/ScottBoehler/ScottBoehler/blob/main/Incident_Management_Runbook.md) defines the framework: severity matrix, role definitions, bridge protocol, communication templates, and escalation paths. This playbook covers something different — how the Major Incident Manager (MIM) actually runs the event from the moment the page fires to the moment the bridge closes.

A framework tells you what a Sev 1 is. A playbook tells you what to do in minute four when the engineers are arguing, the executive is asking for an ETA you do not have, and nobody has told the customer anything yet.

The central idea is simple: **a major incident has two jobs running in parallel.** One job is restoring service. The other is managing everyone who is not restoring service. Engineers are good at the first. The MIM exists to own the second — and to make sure the first is never starved of focus, information, or decisions.

This playbook assumes the framework in the Incident Management Runbook. It does not repeat it. Where a section depends on a runbook definition, it says so.

---

## Section 1 — What the Major Incident Manager Actually Does

### The MIM Is Not the Fixer

The most common failure in major incident management is a MIM who is also the best technical person on the bridge, and who therefore dives into the problem. The moment the MIM starts troubleshooting, nobody is managing the incident.

| The MIM Does | The MIM Does Not |
|---|---|
| Declares, owns, and closes the incident | Run commands or touch systems |
| Assigns workstreams and owners | Debate root cause on the bridge |
| Forces decisions and records them | Make technical decisions the Technical Lead owns |
| Controls the bridge and the clock | Let the loudest voice set direction |
| Owns all communication cadence | Delegate communication to "whoever has time" |
| Escalates early, on process, without apology | Wait until the situation is undeniable to escalate |
| Hands off cleanly to Problem Management | Treat restoration as the end of the job |

### The Three Questions

At any moment during a major incident, the MIM should be able to answer three questions in under ten seconds:

1. **What is the customer impact right now?** Not what is broken — what can customers or the business not do.
2. **What is the current action, who owns it, and when do we hear back?** If any of those three is missing, the action does not exist.
3. **When is the next stakeholder update, and who is writing it?**

If you cannot answer all three, stop and fix that before doing anything else.

### Calm Is a Deliverable

Tone on the bridge is contagious. A MIM who sounds rushed produces a rushed bridge. Speak slower than the situation feels. Use short sentences. Assign by name, never to the room. "Dana, you own the database failover check, report back at 14:20" is a command. "Can someone look at the database?" is a wish.

---

## Section 2 — The Declaration Decision

### When to Declare

Declare a major incident when **any** of these are true — severity criteria are defined in the Incident Management Runbook; this is the judgment layer on top:

- A revenue-generating or customer-facing service is down or materially degraded
- A regulatory, safety, or contractual obligation is at risk
- Multiple customers or business units are affected and the count is growing
- Initial responders cannot identify cause or workaround within their normal window
- Executive or customer awareness is already likely, or will be within the hour

### The Over-Declaration Rule

**When in doubt, declare.** Downgrading a Sev 1 to a Sev 2 costs a few minutes of mild embarrassment. Failing to declare costs an hour of uncoordinated effort and a customer who heard about the outage before you told them.

The only discipline required is that a downgrade is also a decision: state it on the bridge, record the reason, and notify the people who were notified of the original declaration.

### Declaration Is Not Diagnosis

You do not need to know what is wrong to declare. You need to know that something material is wrong. Declare first, diagnose second. Teams that wait for a confirmed cause before declaring will always declare late.

---

## Section 3 — The First 15 Minutes

The first fifteen minutes determine whether the next four hours are controlled or chaotic. The sequence below is deliberately rigid.

| Minute | Action | Owner |
|---|---|---|
| 0–2 | Acknowledge the page. Open the major incident record. Declare severity. | MIM |
| 2–4 | Open the bridge. Page the Technical Lead and required SMEs. Announce who is the MIM. | MIM |
| 4–6 | State the known facts, the customer impact, and the ground rules on the bridge. | MIM |
| 6–8 | Assign the first workstreams by name, each with a report-back time. | MIM |
| 8–10 | Appoint a scribe. Start the running timeline. | MIM / Scribe |
| 10–12 | Confirm what changed in the last 24 hours (changes, deployments, vendor events, maintenance). | Technical Lead |
| 12–15 | Send the initial stakeholder notification. Set the next update time. | Communications Lead |

### The Opening Script

Say this, in your own words, within the first five minutes of opening the bridge:

> "This is [name], I am the Major Incident Manager for this event. Here is what we know: [facts only]. Customer impact is [impact]. We are not yet certain of cause. Ground rules: one person speaks at a time, I will assign actions by name, and if you have an idea, say your name and your idea. Do not troubleshoot on the bridge in parallel — work in your assigned stream and report back at the time I give you. Next update to stakeholders is at [time]."

The ground rules are not courtesy. They are the mechanism that makes a thirty-person bridge function.

### Facts, Not Theories

During the first fifteen minutes, the bridge fills with theories. "It's probably the load balancer." "I bet it's DNS." Theories are useful as hypotheses to assign and test. They are harmful as statements of fact.

The MIM's job is to convert every theory into one of two things: a **test** with an owner and a report-back time, or a **parked item** on the record. A theory that is neither tested nor parked will quietly become the team's belief.

### What Changed?

Most major incidents are caused by change. In the first fifteen minutes, ask:

- Any deployment, configuration change, or patch in the last 24–72 hours?
- Any vendor or carrier maintenance or incident?
- Any certificate, license, or credential expiry?
- Any capacity or traffic anomaly — a marketing event, a batch job, a customer onboarding?
- Any recent change to a dependency two layers away from the failing service?

If a recent change is plausible, the Change Manager joins the bridge. Rolling back a suspect change is nearly always faster than finding out why it failed.

---

## Section 4 — Running the Bridge

### Structure the Bridge Into Workstreams

A single bridge conversation does not scale beyond about six active participants. Split the work:

| Workstream | Purpose | Lead |
|---|---|---|
| **Restoration** | Find and apply the fastest path to service recovery | Technical Lead |
| **Investigation** | Establish cause — only if it does not slow restoration | Senior SME |
| **Communications** | Stakeholder and customer updates | Communications Lead |
| **Business Impact** | Quantify and track what is affected | Service Owner / Business Rep |
| **Vendor / Third Party** | Engage and track external parties | Vendor Manager |

Workstreams report to the MIM at agreed intervals. Workstream leads who need to work deeply break out to a side channel and return at the stated time. The main bridge stays clear for decisions.

### Restoration Before Root Cause

This is the rule that most separates experienced MIMs from inexperienced ones: **the goal of the bridge is restoring service, not understanding it.**

If a restart, failover, rollback, or workaround restores service, do it — then preserve evidence first where you can (logs, memory state, configuration snapshots), and understand it later in the RCA. Teams that insist on finding the cause before acting extend outages in the name of thoroughness.

The exception is when the proposed workaround carries its own risk of data loss or wider impact. In that case, the decision goes to the Technical Lead and, where needed, the Service Owner — and the MIM records who decided and why.

### Decision Discipline

Every decision made on the bridge gets stated aloud and written to the timeline in this form:

> **Decision:** [what] | **Decided by:** [name] | **Time:** [time] | **Reason:** [why] | **Risk accepted:** [what could go wrong]

This has three effects: it forces clarity, it protects the people who made a call under pressure, and it makes the post-incident review factual rather than a matter of recollection.

### Managing the Bridge Itself

| Situation | MIM Response |
|---|---|
| Two people talking over each other | Name one: "Priya first, then Marcus." |
| Technical argument without resolution | "Two options on the table. Priya, Marcus — take ten minutes in a side channel, return with a recommendation at 15:10." |
| Senior executive joins and starts directing | Brief them in two sentences, ask them to route requests through you, offer a private line for questions. |
| Someone on the bridge is not contributing | Release them. "Thanks, Sam — you're released. We'll page you if we need you." Fewer people means a faster bridge. |
| Silence after a question | Do not fill it. Wait. Then assign: "Dana, take that one." |
| The bridge goes quiet for ten minutes | Check in by name. Quiet bridges either mean focused work or stalled work — you need to know which. |
| Blame begins | "We'll cover cause in the review. Right now: what is the next action?" |

### The HiPPO Problem

The Highest Paid Person's Opinion will arrive on the bridge sooner or later. Directors and VPs usually want one of two things: reassurance that someone is in control, or a decision they can influence. Give them the first freely. For the second, route their input through the MIM so it enters the process as an input, not an order.

A senior leader overriding the Technical Lead is the single most dangerous bridge dynamic. Manage it early, privately, and respectfully: "I want to make sure we get your input in the right place. Can I take that to the Technical Lead as a recommendation?"

---

## Section 5 — Communication Strategy

Message templates live in the Incident Management Runbook. This section covers the strategy those templates serve.

### Communicate on a Clock, Not on News

Stakeholders do not need good news; they need predictability. Set the update cadence at the start and keep it even when there is nothing new to say.

| Severity | Initial Notice | Update Cadence |
|---|---|---|
| Sev 1 | Within 15 minutes of declaration | Every 30 minutes |
| Sev 2 | Within 30 minutes of declaration | Every 60 minutes |

An update that says "no change, next update at 15:30" is a good update. Silence is what makes executives call the bridge.

### One Voice

All outbound communication goes through one person — the Communications Lead, authored under MIM direction. Engineers do not email executives. The MIM does not draft customer notices while also managing the bridge. Two people sending different versions of the facts is how organizations lose credibility during an outage.

### Audience Matters

| Audience | What They Need | What To Leave Out |
|---|---|---|
| **Executives** | Business impact, ETA or confidence level, decisions needed from them | Technical detail, speculation |
| **Customers** | What is affected, what to do, when the next update comes | Internal cause, blame, anything legally sensitive |
| **Service Desk / Support** | Talking points, known symptoms, workaround, how to log tickets | Anything they cannot say to a customer |
| **Technical Teams** | Current state, who owns what, what is needed | Executive-level reassurance |
| **Business Operations** | Workaround and expected duration so they can plan | Root cause theories |

### Writing an Honest ETA

The ETA is the hardest sentence in any update. Rules:

- **Never give an ETA you cannot support.** A missed ETA damages trust more than "unknown."
- **Give a time for the next update instead.** "We do not have a restoration time yet. We will update at 15:30."
- **When you do give an ETA, state confidence.** "We expect restoration by 16:00. Confidence is moderate — dependent on the vendor patch."
- **Revise early.** The moment you know the ETA will slip, say so. Nobody has ever been angry at an early warning.

### Language to Avoid

| Avoid | Use Instead |
|---|---|
| "We think it's probably…" | "We have not confirmed the cause. Current hypothesis is…" |
| "It should be fixed soon." | "Next update at 15:30." |
| "The vendor is slow to respond." | "We have an open case with [vendor], case number X, last contact at Y." |
| "Someone made a bad change." | "A change deployed at 09:40 is under review as a contributing factor." |
| "Everything is under control." | State the facts. Let the facts reassure. |

### The Customer Communication Trap

For a managed services provider, customer communication during a major incident is a contractual and relational event as much as an operational one. Before the first customer notice:

- Confirm what the contract requires: notification window, format, named contacts
- Confirm what has been verified versus assumed
- Have the customer's Service Owner or account lead review where the relationship warrants it
- Never describe cause externally until it is confirmed

---

## Section 6 — Escalation in Practice

Escalation levels and triggers are defined in the Incident Management Runbook. The practical lesson is about *timing and framing*.

### Escalate on Time, Not on Embarrassment

Most escalation delays have the same cause: the responsible person hopes the next ten minutes will fix it, and does not want to ask for help. Build the discipline the other way around. Escalation on a time trigger is **process**, not failure.

### The Time-Box Rule

Assign every workstream a time box. When it expires without progress, escalate — automatically, without debate:

> "Restoration workstream has run 30 minutes on database recovery with no result. Escalating to the vendor's senior engineering line and bringing in the Infrastructure Director."

### How to Escalate to a Vendor

Vendors prioritize the customer who gives them what they need in the first call. Have ready:

- Account, contract, and support case numbers
- Business impact in one sentence, with a start time
- What has been tried and the result of each attempt
- A technical contact on your side with authority to act
- A named person who will remain on the call until resolved

State your severity and your expectations explicitly: "This is a Severity 1. We need a senior engineer on this bridge within fifteen minutes."

### Escalating Upward

When informing leadership, bring three things: the facts, the options, and the ask.

> "Payments have been degraded since 14:10; roughly 40% of transactions are failing. We have two options — fail over to the secondary site, which carries about twenty minutes of risk to in-flight transactions, or wait for the vendor patch, ETA unknown. I recommend failover. I need your approval to proceed."

Leaders do not want to be surprised and do not want to be handed a problem without a recommendation.

---

## Section 7 — Long-Running Incidents

An incident that passes the four-hour mark is a different animal. People are tired, judgment degrades, and the tendency to stop questioning assumptions grows.

### Rotate the Roles

No single person should hold a major incident role for more than four to six hours. Plan the handover before it is needed.

### The Handover Brief

When handing over the MIM role, the outgoing MIM provides, in writing and verbally:

1. Current customer impact and trend
2. Timeline of key events and decisions
3. What has been tried and ruled out
4. Active workstreams, owners, and report-back times
5. Open decisions and who needs to make them
6. Stakeholder communication status — last sent, next due
7. Vendor and escalation status
8. Any commitments made (ETAs, customer promises)

The incoming MIM states the handover on the bridge so everyone knows who is in command.

### Fresh Eyes

At the three-hour mark, ask a structured question: **"What assumption have we not questioned?"** Bring in someone who joined late or has not been on the bridge. Long incidents often turn on an assumption made in the first twenty minutes that nobody revisited.

### Look After People

- Make sure people eat and rest. Say so aloud.
- Release people who are no longer needed, and tell them when you may call them back.
- Do not keep a bridge full of silent observers "just in case."
- Plan for the next shift's staffing before the current one is exhausted.

---

## Section 8 — Recovery, Closure, and Handoff

### Restored Is Not Resolved

Declare **service restored** when customer impact ends. Do not close the incident at that moment. Before closing:

- [ ] Service validated by the business or customer, not only by monitoring
- [ ] Monitoring confirms stability for an agreed observation period
- [ ] Any temporary workaround is documented and its owner named
- [ ] Backlogged transactions, queues, and data reconciliation are accounted for
- [ ] Resolution notification sent to all original recipients
- [ ] Evidence preserved — logs, timelines, configuration snapshots
- [ ] Bridge closed, with a statement on the bridge confirming it

### The Handoff to Problem Management

Closing the incident starts the next process. Before the bridge disbands, confirm:

- A problem record is opened and linked to the major incident
- A named owner exists for the post-incident review
- The review is scheduled within the standard window (see the Incident Management Runbook)
- Workarounds are in the Known Error Database where applicable
- Any emergency changes made during the incident are logged for retrospective review

Without this handoff, the same incident returns under a new number. The [Problem Management & RCA Guide](https://github.com/ScottBoehler/ScottBoehler/blob/main/Problem_Management_RCA_Guide.md) covers what happens next.

### The Post-Incident Review — The MIM's Part

The MIM's contribution to the review is the timeline, the decision log, and an honest assessment of the *response* — separate from the cause. Questions the MIM should bring:

- How long from first symptom to detection? To declaration? To the right people on the bridge?
- Which decisions were slow, and why?
- Did communication cadence hold?
- Did escalation happen on time?
- What did we lack — a runbook, access, a contact, a tool?

Response improvements are often cheaper and faster to deliver than root cause fixes, and they pay off on every future incident.

---

## Section 9 — Scenario Playbook

Short patterns for common major incident types. Each starts from the same first fifteen minutes in Section 3.

| Scenario | First Moves | Watch For |
|---|---|---|
| **Total application outage** | Confirm scope with an external check. Recent change review. Prepare rollback. | Teams debugging while a rollback would restore service in minutes |
| **Partial degradation** | Quantify — what percentage, which users, which function. Check dependencies and capacity. | Under-declaring because "it's not fully down" |
| **Network or carrier failure** | Open carrier case immediately in parallel. Identify path or site. Evaluate failover. | Assuming the carrier will volunteer information |
| **Security-related incident** | Engage Security lead *before* acting. Preserve evidence. Restrict communication to need-to-know. | Restoring service in a way that destroys evidence |
| **Third-party or SaaS outage** | Confirm via vendor status and an independent check. Activate workaround. Communicate dependencies to customers. | Spending hours on internal investigation of an external fault |
| **Data integrity issue** | Stop further writes if possible. Define scope of affected data. Involve business owners. | Restoring service before understanding what is corrupted |
| **Failed change** | Roll back first. Engage the change owner. Preserve the change record. | Pushing forward with a fix on top of a failed change |
| **Cascading failure across services** | Establish dependency map. Fix the root dependency, not the loudest symptom. | Multiple teams each chasing their own alert |
| **After-hours event** | Verify on-call coverage and reachability. Confirm bridge access. Plan the shift handover early. | Single points of knowledge sitting with people who are asleep |

---

## Section 10 — Common Failures

| # | Failure | What It Looks Like | Prevention |
|---|---|---|---|
| 1 | **MIM becomes the troubleshooter** | The MIM is typing commands; nobody is running the bridge | Strict role separation; MIM never touches systems |
| 2 | **Late declaration** | "Let's give it another ten minutes" three times | Declare on criteria; downgrade later if wrong |
| 3 | **Theories treated as facts** | Team converges on a cause nobody tested | Every theory becomes a test or a parked item |
| 4 | **Cause before restoration** | Rollback delayed to "understand it first" | Restore first; preserve evidence; investigate later |
| 5 | **Silent stakeholders** | Executives phone the bridge for status | Fixed cadence, honored even with no news |
| 6 | **Multiple voices externally** | Customer receives conflicting messages | One Communications Lead, one approved source |
| 7 | **Unsupported ETAs** | Three missed ETAs; credibility gone | Give next-update time, not guesses |
| 8 | **Overcrowded bridge** | Forty attendees, six contributing | Release people; use workstreams and side channels |
| 9 | **Late escalation** | Vendor engaged after two hours | Time-boxed workstreams with automatic escalation |
| 10 | **No handover on long incidents** | Exhausted MIM on hour nine, repeating old theories | Rotate roles; written handover brief |
| 11 | **Closure without handoff** | Same incident returns next month | Problem record and review owner confirmed before closing |
| 12 | **Blame on the bridge** | Engineers stop volunteering information | Reframe immediately; cause belongs to the review |

---

## Section 11 — Metrics

Core incident metrics are defined in the Incident Management Runbook. For major incident *response* quality, add:

| Metric | Why It Matters |
|---|---|
| **Time to detect** (failure start to alert or report) | Measures monitoring quality |
| **Time to declare** (detect to major incident declared) | Measures judgment and discipline |
| **Time to assemble** (declare to correct people on bridge) | Measures on-call and contact quality |
| **Time to initial communication** | Measures communications readiness |
| **Update cadence adherence** (% of updates on time) | Measures predictability |
| **Time to restore** | Headline measure of impact |
| **Escalations triggered by time-box vs. by crisis** | Measures how proactive escalation is |
| **PIR completed within standard** | Measures follow-through |
| **Repeat major incidents (same cause)** | Measures problem management effectiveness |

Review these monthly. A reducing time to declare and time to assemble are better indicators of a maturing practice than a falling incident count.

---

## Appendix A — MIM Quick Reference Card

**Declare:** When in doubt, declare. Declare first; diagnose second.

**Minute 0–15:** Open record → open bridge → say who you are → state facts and impact → assign by name → appoint scribe → ask "what changed?" → send first notice → set next update time.

**Every few minutes, ask yourself:**
1. What is the customer impact right now?
2. Who owns the current action, and when do we hear back?
3. When is the next update, and who is writing it?

**Rules:**
- Restore before you understand.
- Facts, not theories.
- Assign by name, with a time.
- Time-box every workstream, then escalate.
- One voice outward.
- Never give an ETA you cannot support.
- Rotate roles after four to six hours.
- Close only after the handoff.

---

## Appendix B — Major Incident Timeline Template

| Time | Event / Action / Decision | Owner | Source |
|---|---|---|---|
| | First symptom / alert | | |
| | Major incident declared (severity) | MIM | |
| | Bridge opened | MIM | |
| | Technical Lead engaged | | |
| | Initial notification sent | Comms Lead | |
| | Decision: [what, who, why, risk accepted] | | |
| | Escalation: [to whom, why] | | |
| | Vendor engaged — case # | | |
| | Workaround or fix applied | | |
| | Service restored | | |
| | Validation complete | | |
| | Resolution notification sent | Comms Lead | |
| | Bridge closed | MIM | |
| | Problem record opened — # | MIM | |
| | PIR scheduled — date | | |

---

## Appendix C — Handover Brief Template

**Incident #:** ___  **Severity:** ___  **Duration so far:** ___  
**Outgoing MIM:** ___  **Incoming MIM:** ___  **Time of handover:** ___

1. **Current customer impact and trend:**
2. **Key events and decisions to date:**
3. **Tried and ruled out:**
4. **Active workstreams** (owner / next report-back):
5. **Open decisions** (what / who decides):
6. **Communication status** (last sent / next due):
7. **Vendor and escalation status:**
8. **Commitments made (ETAs, customer promises):**

---

## Change Log

| Version | Date | Changes |
|---|---|---|
| 1.0 | October 2026 | Initial release |

---

*Restoring service is the job. Running the incident is how you do it.*
