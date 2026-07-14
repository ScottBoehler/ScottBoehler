# Building a Service Management Function From Zero: A Practical Playbook

## Why This Exists

Most of what's written about service management assumes the function already exists — you're improving SLAs, tuning an existing ticketing tool, or fixing a broken escalation process. There's a lot less written about what to do when none of it exists yet: no ticketing system, no incident process, no CMDB, no runbooks, and no team.

That's the situation a lot of fast-growing infrastructure and technical product companies find themselves in — they've scaled the engineering and sales side hard and never built a service layer to support it. This is the playbook I'd run to fix that. It's built from 30 years managing 24x7x365 operations, incident command, and service design, compressed into a build order that works when you're starting from a blank page.

## Step Zero: Find Out What Already Exists Before You Build Anything

Before writing a single process, inventory what's already there — even informally. Most companies at this stage have *some* signal already: monitoring tools, health-check APIs, an engineering Slack channel doing the job of a help desk. Your fastest early win is almost never building new detection logic — it's wiring existing signal into a process that captures, routes, and tracks it. Don't rebuild what already works. Find out what's silently generating good data with nobody listening to it.

## Framework Foundation: What to Build First, What to Defer

ITIL gives you the full menu, but a startup doesn't need the whole menu on day one. Prioritize the practices that create immediate operational control and defer the governance-heavy ones until the function has proven its value.

**Build first (0–90 days):**
- Incident Management — the single highest-leverage practice for any company where downtime costs the customer money
- Service Desk (single point of contact) — even a one-person desk needs one defined intake channel
- Problem Management (lightweight) — track root cause so failures don't repeat undocumented
- Monitoring & Event Management — tied to whatever detection signal already exists

**Build second (90–180 days):**
- Change Enablement — lightweight approval flow, not a heavyweight CAB process
- Service Level Management — formal SLAs, once you have real incident data to base them on
- Knowledge Management — runbooks and a searchable knowledge base

**Defer (180+ days, once the function has proven value):**
- Full CMDB maturity, formal Capacity Management, a dedicated Continual Improvement practice

## Know Your Customer Populations Before You Design One Process

Don't assume one support model fits everyone. Most infrastructure companies serving both business partners and end customers actually have two distinct populations with different needs — a supply-side partner who needs operational reliability and predictable reporting, and a demand-side customer who needs fast, unambiguous incident response. Map this out explicitly before you design SLAs. A single intake process with tiered SLAs is usually the right answer — two entirely separate desks is rarely worth the staffing cost at this stage.

## If There's No Existing Provisioning/Automation Layer

Some companies already have an internal platform handling infrastructure provisioning and diagnostics — in that case, your job is wiring the service layer into what exists, not rebuilding it. If nothing exists yet, especially for physical/bare-metal infrastructure, the category of tooling you're evaluating looks different from standard SaaS ITSM:

- **Bare-metal provisioning automation** — Canonical MAAS, Tinkerbell, or Foreman to automate server imaging and configuration when a request is approved.
- **Hardware monitoring & asset tracking** — Prometheus with Node Exporter or Zabbix for health monitoring, NetBox for IPAM/DCIM asset tracking, feeding auto-generated tickets when hardware fails.

For any physical-infrastructure service desk, build the service catalog around the physical asset lifecycle, not just software requests:

- **Provisioning** — OS install, RAID configuration, network/IP assignment
- **Hardware failures** — disk, RAM, power supply, motherboard issues
- **Network & out-of-band access** — IPMI/OOB access requests, firewall rules, bandwidth adjustments
- **Decommissioning** — secure data destruction and reset before the asset returns to the available pool. Easy to overlook, but it's a real trust and compliance requirement, not an afterthought.

Map your support tiers to how much of this is automated vs. physical:

- **Tier 1 — Automated self-service**, if a provisioning API exists: request triggers imaging with no human involvement.
- **Tier 2 — Remote technical triage**: BIOS errors, network misconfiguration, kernel-level issues — resolved without anyone touching hardware.
- **Tier 3 — Physical/on-site intervention**: confirmed hardware failure requiring hands-on replacement, whether that's your own data center staff or a partner facility's team.

## Backend Vendors You'll Need — And How to Contract Them

**The core categories:**
- **ITSM / ticketing platform** — Freshservice, Zendesk, Jira Service Management, Zoho Desk, HaloITSM. Enterprise platforms like ServiceNow are usually overkill and overpriced for a company standing up its first service desk — that's a year-two conversation, not a day-one choice.
- **On-call / alerting & paging** — PagerDuty or Opsgenie. This is what turns a monitoring alert into a phone call to the right person at 3am.
- **Knowledge base / documentation** — Confluence, Notion, or GitBook. Use whatever the engineering team already runs on rather than asking people to adopt a second tool.
- **Status page / customer communication** — Atlassian Statuspage or Instatus, for transparent uptime reporting.
- **CMDB** — usually not a standalone purchase early on; most modern ITSM platforms include a lightweight CMDB module. Populate it from an existing system-of-record API rather than manual entry — manual CMDBs go stale within weeks.

**How to run the selection — same discipline as any vendor RFP, compressed for startup speed:**

1. **Define requirements before the first demo.** Ticket volume estimate, number of agents, integration needs. Walk in without a number and vendors steer you to their most expensive tier.
2. **Get three quotes minimum.** Even at startup speed, three competitive quotes is the floor for defensible pricing — and it's leverage in the negotiation itself.
3. **Ask every SaaS vendor for startup/growth-stage pricing.** Most have unpublished discount tiers for companies under a certain headcount or funding stage. Never take the list price on the website as the real price.
4. **Reference-check the vendor's stability, not just the product.** Don't compound your own company's risk profile by picking an under-funded vendor for a mission-critical function like paging or alerting.
5. **Negotiate contract term against commitment level, not just price.** Push for a 3–6 month pilot or month-to-month option before a 12-month commitment — you don't have real usage data yet, and you shouldn't lock into annual pricing for a tool that might not fit.
6. **Put SLA and support-tier terms in the contract itself.** What's the vendor's own response time if your ticketing system goes down? Get a named account manager, not just a support queue.
7. **Build in an exit.** Data export terms and a defined offboarding process, especially for the ITSM/CMDB platform — you don't want your incident history and asset data held hostage if you outgrow the tool.
8. **Set a vendor review cadence once signed.** Quarterly for the first year on anything tied to uptime or incident response — usage against ticket volume, SLA compliance from the vendor's side, and whether the pricing tier still fits.

**Framing the budget ask to leadership:** build the business case the same way you always would — cost of the tool versus cost of not having it. For a company with real technical/commercial traction and zero service tooling, the framing is simple: every hour of downtime with no formal incident tracking is lost revenue and an unmeasured customer relationship risk. Bring 2–3 vendor quotes rather than asking for an open-ended budget — gives leadership something concrete to approve instead of a hypothetical.

## Phase 1 (Days 1–30): Discovery & Assessment

- Map current support reality — how are issues reported today? Get actual volume, even if it's informal.
- Identify who currently fields issues when they happen, and how long resolution takes without a formal process.
- Confirm access to existing monitoring/diagnostic data and whether it's exposed to you as a service-layer consumer.
- Meet any partner-facing or channel teams to understand their escalation path today.
- Get a real ticket-volume estimate before buying any tooling — it drives every vendor conversation.
- Confirm reporting line and budget/headcount approval authority before you build anything that requires either.

## Phase 2 (Days 30–60): Core Process Design

- **Incident Management** — define severity levels tied to real monitoring signal, map each to a response/resolution target.
- **Escalation Matrix** — internal escalation and any external/partner-side escalation path, since some issues will be outside your direct control.
- **Change Enablement (lightweight)** — simple approval flow for anything touching production, with a documented owner and rollback requirement — not a formal CAB at this headcount.
- **SLA / OLA Draft** — draft response/resolution targets once you have real incident volume from Phase 1. Don't commit to numbers before you have data.

## Phase 3 (Days 60–90): Tooling Selection & Setup

- Run the vendor selection process above — shortlist, demo, negotiate, contract.
- Wire existing monitoring/diagnostic output into the chosen ITSM tool for auto-ticket creation — the single highest-leverage integration you can build.
- Stand up an on-call schedule, even if it's just one or two people rotating initially.
- Set up the knowledge base structure — empty shell is fine, populate as runbooks get written.

## Phase 4: CMDB & Asset Visibility

- Build a CI hierarchy that mirrors how the business already thinks about its infrastructure — don't invent a parallel structure.
- Sync inventory and health status from an existing system-of-record API on a scheduled pull or webhook, rather than manual entry.
- Tag each configuration item with ownership for accountability and to support your escalation path.

## Phase 5: Runbooks & Knowledge Base — Build These First

- The most common failure mode and its standard triage/escalation steps
- Any "unreachable / provisioning failure" scenario
- High-impact, customer-visible technical failures specific to the product
- The handoff runbook — when and how to escalate outside your direct control
- Customer-reported issue vs. platform issue — the fault-isolation runbook
- New customer/account onboarding support

## Phase 6: Staffing Model & On-Call Design

- **Tier 1** — initial triage, known-issue resolution using runbooks, hands off anything requiring deeper diagnostics.
- **Tier 2** — deeper technical triage, coordinates with engineering and any external partners on confirmed issues.
- **Tier 3** — engineering escalation for platform-level issues.
- For a lean team, a simple two-person on-call rotation is more realistic than a full 24x7 shift model until headcount is approved. An outsourced overnight/overflow vendor can buy time without burning out a small team.
- Get a headcount plan with a defined trigger point — ticket volume, revenue milestone, or a calendar date — in writing early. Otherwise "temporary" becomes permanent.

## Phase 7: Metrics, SLAs & Reporting

- MTTR, by severity and by customer population
- SLA compliance percentage, once formal SLAs are set
- Ticket volume trend and top recurring issue categories — feeds Problem Management
- Internal vs. external fault attribution, where relevant
- A simple dashboard for leadership visibility from day one — even a basic one signals the function is operating with metrics discipline, which is the credibility case you need to make in the first 90 days

## 30-60-90-180 Day Roadmap Summary

- **Days 1–30:** Discovery. Understand current state, get access to existing data, meet partner/channel teams, get a ticket volume estimate, confirm reporting line and budget authority.
- **Days 30–60:** Process design. Incident management, escalation matrix, lightweight change process, draft SLA targets.
- **Days 60–90:** Tooling. Vendor selection and contracting, monitoring integration, on-call setup, knowledge base shell.
- **Days 90–180:** Operationalize. Populate CMDB, write priority runbooks, formalize SLAs with real data, build the reporting dashboard, present the headcount case for the first hire.

---

*This playbook reflects how I'd approach standing up a service management function with nothing in place — not a template to copy line-for-line, but the build order I'd defend in front of any leadership team asking why it's sequenced this way.*
