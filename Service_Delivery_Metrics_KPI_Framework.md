# Service Delivery Metrics & KPI Framework
### Enterprise IT Operations | Comprehensive Performance Management

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** All IT service delivery operations — incident management, change management, problem management, and customer-facing service performance

---

## Purpose & Scope

Metrics exist for one reason — to tell you whether the operation is working before the customer tells you it isn't. This framework defines the key performance indicators (KPIs) that matter across incident management, SLA compliance, team performance, customer satisfaction, and executive reporting.

Every metric in this framework is measurable, reportable from ServiceNow, and tied directly to operational outcomes. Metrics that cannot drive a decision or an action have no place in this framework.

---

## Section 1 — Incident Management Metrics

These are the core operational metrics. They measure how fast the team detects, acknowledges, and resolves issues — and how consistently they perform against defined targets.

### Primary Incident Metrics

| Metric | Definition | How It Is Measured | Target |
|---|---|---|---|
| **MTTA** (Mean Time to Acknowledge) | Average time from incident detection to acknowledgment in ServiceNow | ServiceNow SLA module — detection timestamp to acknowledgment timestamp | Sev 1: ≤5 min / Sev 2: ≤10 min / Sev 3: ≤30 min |
| **MTTR** (Mean Time to Resolve) | Average time from incident detection to resolution and ServiceNow closure | ServiceNow SLA module — detection timestamp to resolved timestamp | Sev 1: ≤4 hrs / Sev 2: ≤8 hrs / Sev 3: ≤24 hrs |
| **MTTD** (Mean Time to Detect) | Average time from actual failure to detection by monitoring or user report | Alert timestamp vs. estimated failure time from RCA | Trending down — indicates improving monitoring coverage |
| **SLA Compliance Rate** | Percentage of incidents resolved within target MTTR by severity | ServiceNow reporting — incidents resolved within SLA / total incidents | ≥95% overall |
| **Incident Volume by Severity** | Total incident count broken down by Sev 1 / Sev 2 / Sev 3 / Sev 4 | ServiceNow incident reports — filtered by priority | Trending flat or down — spikes require investigation |
| **Repeat Incident Rate** | Percentage of incidents caused by a previously identified root cause | Incidents linked to known errors in ServiceNow KEDB / total incidents | <10% — high rate signals problem management failure |
| **Escalation Rate** | Percentage of incidents requiring Level 3 or Level 4 escalation | Incidents with escalation flag / total incidents | Trending down month over month |
| **Bridge Call Duration** | Average length of Sev 1 and Sev 2 bridge calls from open to close | Bridge call log timestamps | Trending down — indicates improving resolution efficiency |

### Incident Trend Analysis

Raw numbers are not enough. Trend direction matters more than any single data point. Track each metric month over month and ask three questions:

1. Is the trend moving in the right direction?
2. If not — what changed?
3. What specific action will reverse the trend?

A MTTR that is above target but improving month over month is a different conversation than one that is above target and flat for three consecutive months.

---

## Section 2 — SLA Compliance Metrics

SLA compliance is the metric customers actually care about. Everything else is internal. These metrics measure performance against the commitments made to customers.

| Metric | Definition | Target |
|---|---|---|
| **Overall SLA Compliance Rate** | Percentage of all incidents resolved within contracted SLA windows | ≥95% |
| **Sev 1 SLA Compliance** | Percentage of Sev 1 incidents resolved within contracted target | ≥98% — Sev 1 breaches have direct customer and contract implications |
| **SLA Breach Count** | Number of incidents where resolution exceeded the contracted SLA window | Zero is the target — every breach requires documented explanation |
| **SLA Breach Root Cause** | Classification of why each SLA breach occurred | Tracked by category: staffing, vendor delay, complexity, process failure |
| **Near-Miss Rate** | Percentage of incidents resolved within the final 10% of the SLA window | Trending down — near-misses are future breaches |
| **Customer Notification Compliance** | Percentage of incidents where executive notification was sent within the required window | 100% — missed notifications are a separate contractual obligation |
| **SLA Credit Exposure** | Total financial value of SLA credits owed based on breach thresholds | Tracked monthly — patterns drive contract renegotiation or operational investment |

### SLA Breach Response Protocol

Every SLA breach is documented in ServiceNow and triggers a mandatory review:

1. Breach identified — ServiceNow SLA module flags automatically at expiration
2. Change Manager or SDM notified immediately
3. Root cause documented within 24 hours — what caused the breach?
4. Customer notification sent — breach acknowledged, remediation explained
5. Corrective action identified — what prevents recurrence?
6. Breach report added to monthly operations review

SLA breaches are never closed in ServiceNow without a documented root cause and corrective action.

---

## Section 3 — Team Performance Metrics

Operational metrics measure the process. Team performance metrics measure the people executing it. Both matter.

| Metric | Definition | Target |
|---|---|---|
| **First Contact Resolution (FCR)** | Percentage of Sev 3 and Sev 4 incidents resolved without escalation | ≥80% — low FCR signals skill gaps or poor knowledge base |
| **Queue Backlog** | Number of open incidents beyond target resolution time | Zero backlog target — growing backlog signals capacity or prioritization problem |
| **On-Call Response Compliance** | Percentage of on-call pages acknowledged within SLA window | 100% — missed pages are a systemic risk |
| **Knowledge Base Contribution Rate** | Number of new or updated knowledge articles per month per team | Trending up — healthy teams build and maintain their own knowledge base |
| **PIR Action Item Closure Rate** | Percentage of post-incident review action items closed by due date | ≥90% — open action items signal execution gaps |
| **Change Success Rate** | Percentage of changes implemented without incident or rollback | ≥95% |
| **Training Completion Rate** | Percentage of team members current on required certifications and training | 100% — gaps are flagged monthly |

### Coaching & Development Tracking

Team performance metrics are not used to rank individuals against each other. They are used to identify where coaching, training, or process improvement is needed. A team member with low FCR is a coaching conversation — not a performance warning. A team with low FCR across the board is a process or tooling conversation.

Individual performance data is reviewed by the team lead monthly in 1:1 sessions. Aggregate team data is reviewed in monthly operations reviews.

---

## Section 4 — Customer Satisfaction Metrics

Internal metrics tell you how the operation is running. Customer satisfaction metrics tell you whether the customer agrees.

| Metric | Definition | Collection Method | Target |
|---|---|---|---|
| **Customer Satisfaction Score (CSAT)** | Customer rating of individual incident handling | Post-incident survey sent automatically from ServiceNow on closure | ≥4.0 / 5.0 |
| **Net Promoter Score (NPS)** | Customer likelihood to recommend the service | Quarterly survey — sent outside of ServiceNow | ≥30 |
| **Customer Retention Rate** | Percentage of customers renewing contracts | Tracked by account management | ≥90% |
| **Escalation Frequency by Customer** | Number of customer-initiated escalations per account per quarter | Tracked in ServiceNow — escalation flag on incident record | Zero target — any customer-initiated escalation triggers account review |
| **Executive Sponsor Satisfaction** | Satisfaction rating from customer executive contacts | Quarterly executive business review (EBR) feedback | Tracked qualitatively — negative feedback triggers action plan |

### CSAT Follow-Up Protocol

Any CSAT score below 3.0 triggers a mandatory follow-up:

1. Service Delivery Manager reviews the incident record within 24 hours
2. Customer contact reached within 48 hours — understand what went wrong
3. Findings documented in ServiceNow account notes
4. Corrective action identified and tracked
5. Follow-up CSAT issued after corrective action is implemented

Low CSAT scores that are not followed up are a bigger risk than the low score itself. Silence signals indifference.

---

## Section 5 — Executive Reporting Metrics

Executives do not need every metric — they need the metrics that tell them whether the operation is healthy, whether customers are at risk, and whether resources are allocated correctly.

### Monthly Executive Dashboard — Key Metrics

| Category | Metric | This Month | Last Month | Trend |
|---|---|---|---|---|
| **Incidents** | Total Sev 1 + Sev 2 count | | | ↑ ↓ → |
| **Incidents** | Sev 1 MTTR average | | | ↑ ↓ → |
| **SLA** | Overall SLA compliance rate | | | ↑ ↓ → |
| **SLA** | SLA breach count | | | ↑ ↓ → |
| **Changes** | Change success rate | | | ↑ ↓ → |
| **Changes** | Emergency change rate | | | ↑ ↓ → |
| **Customer** | CSAT average | | | ↑ ↓ → |
| **Customer** | Customer-initiated escalations | | | ↑ ↓ → |
| **Risk** | Open PIR action items past due | | | ↑ ↓ → |
| **Risk** | Repeat incident rate | | | ↑ ↓ → |

### Executive Reporting Principles

- **Lead with the exceptions.** Executives do not need to hear what is working — they need to know what is at risk and what is being done about it.
- **One slide per category.** Incident slide, SLA slide, change slide, customer slide. No more than four slides for a monthly operations review.
- **Every red metric has an owner and an action.** Do not present a problem without a plan.
- **Trend over snapshot.** A metric that is below target but improving tells a different story than one that is below target and declining. Show both the number and the direction.

---

## Section 6 — ServiceNow Reporting Reference

All metrics in this framework are generated from ServiceNow reporting. No manual spreadsheets — if it cannot be pulled from ServiceNow, it is not a metric.

| Report | Location in ServiceNow | Frequency |
|---|---|---|
| Incident volume by severity | Reports → Incident Reports → Volume by Priority | Weekly / Monthly |
| MTTA and MTTR by severity | Reports → SLA Reports → Resolution Time by Priority | Weekly / Monthly |
| SLA compliance rate | Reports → SLA Reports → SLA Compliance Dashboard | Weekly / Monthly |
| SLA breach log | Reports → SLA Reports → Breached SLAs | Weekly |
| Change success rate | Reports → Change Reports → Implementation Outcome | Monthly |
| Emergency change rate | Reports → Change Reports → Change Type Distribution | Monthly |
| CSAT scores | Reports → Survey Reports → CSAT by Incident | Monthly |
| PIR action item status | Reports → Problem Reports → Open Action Items | Weekly |
| Knowledge base contribution | Reports → Knowledge Reports → Article Activity | Monthly |

---

## Section 7 — Monthly Operations Review Structure

Metrics without a review cadence are decoration. This is the agenda for the monthly operations review — 60 minutes, every month, no exceptions.

1. **Incident review** (15 min) — Volume, MTTR, SLA compliance, repeat incident rate
2. **SLA review** (10 min) — Compliance rate, breach log, near-miss rate, credit exposure
3. **Change review** (10 min) — Success rate, emergency change rate, rollback count
4. **Customer review** (10 min) — CSAT, escalations, retention risk accounts
5. **PIR action item review** (10 min) — What is open, what is overdue, who owns what
6. **Next month priorities** (5 min) — What needs to improve, what resources are needed

Every metric that is red or trending wrong gets a named owner and a due date before the meeting closes. No metric leaves the room without an action.

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*A metric nobody acts on is not a metric — it is a number. Build the dashboard you will actually use to run the operation, not the one that looks impressive in a slide deck.*
