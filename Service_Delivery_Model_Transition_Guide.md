# Moving Support Work Between Delivery Models: A Practical Guide

## Why This Exists

The [Greenfield Service Desk Playbook](Greenfield_Service_Desk_Playbook.md) covers building service management from a blank page. This is the companion for what comes after: the service exists, it works well enough, and someone asks whether a queue should stay with the core team, move to a specialist group, go to an outside partner, or be handled by automation.

Most of what gets written about this is either a sales pitch for one model or a project plan with no judgment in it. Transitions that go badly tend to go badly for the same few reasons: the decision was made on a spreadsheet, nobody defined "working" before the move, and the team that handed the work off was gone by the time the problems showed up.

This is the approach I'd follow. It's built from experience running 24x7x365 operations and service transitions, and it's a way of thinking rather than a template to copy line for line. I haven't led every kind of move described here, and I've tried not to write as if I had. Where the guide gives a rule, it's because the logic holds regardless of the model.

## Step Zero: Find Out Why the Work Is Moving

Before scoring anything, get the real reason in writing. It's almost always one of three: **cost, coverage, or growth.** Occasionally it's quality or risk. The reason matters because it decides what "success" means. A move made for coverage hours is not judged the same way as a move made to cut cost, and a move made for cost that quietly damages customer experience is a loss even if the invoice goes down.

If the stated reason and the real reason differ, you will find out at the worst possible moment. Ask early, and ask directly.

## Decide What Should Move (and What Shouldn't)

Not every queue is a candidate. Score each one on plain questions:

| Question | Why it matters |
|---|---|
| How much volume, and how steady is it? | Steady, high-volume work is easier to hand off than spiky work. |
| How repeatable is the resolution? | If a written procedure solves it, someone else can run it. If it takes judgment, be careful. |
| What is the customer or regulatory risk of a mistake? | High-risk work moves last, or stays. |
| How good is the documentation today? | If the knowledge lives in two people's heads, fix that before anything moves. |
| What does it cost now, fully loaded? | Include management time, rework and escalations, not just headcount. |
| What happens to the work that doesn't move? | A queue that loses its easy tickets keeps the hard ones. Check the team can still carry it. |

**Warning:** The last question is the one that gets skipped. Moving the repeatable work out of a team leaves the remaining work harder, slower and more stressful, and the team's numbers will look worse even if nothing else changed. Decide ahead of time how that gets measured fairly.

Keep the recommendation separate from the decision. Your job is to bring options, data and a clear view. Leadership makes the call. Write down what you recommended and why, because you will want that record later, whichever way the decision goes.

## Delivery Models, in Plain Terms

- **Core team.** Best for work that needs product knowledge and judgment.
- **Specialist team.** Best for complex or high-risk categories that deserve dedicated expertise.
- **Outside partner.** Best for high-volume, well-documented work, and for coverage hours you cannot staff yourself.
- **Automation or AI-assisted.** Best for narrow, repeatable requests. Test it on a slice before relying on it.
- **Pilot or incubation.** A small group that handles new or unclear work until it is understood well enough to place.

No model is better in general. The question is which one fits this work today, and it should be asked again as the work changes.

## Set the Measures Before You Move Anything

Write these down before the transition starts:

- **Customer.** Satisfaction, resolution time, repeat contacts.
- **Quality.** Accuracy of resolution, audit or QA score.
- **Capacity.** Backlog, response time, coverage hours.
- **Cost.** Cost per contact, plus the cost of managing the new arrangement.
- **People.** Attrition, absence, and how the team describes the change when asked.

Capture the baseline now. If you wait until after the move, you cannot tell whether it helped or just changed. A one-page template is in Appendix A.

**Warning:** Don't let the baseline be a single number pulled from a good week. Use enough history to show normal variation, and note any unusual events inside it. Otherwise the first bad week after the move gets blamed on the move.

## Readiness Criteria

A date is not a readiness criterion. Before work moves, confirm:

- Procedures and knowledge articles are written, current, and tested by someone who did not write them.
- The receiving team has been trained and has handled real cases with supervision.
- Escalation paths and contacts are named, not implied.
- Tools and access are in place and working, including for people who join later.
- Quality checks are defined, and someone owns them.
- Workforce planning covers volume, seasonality and ramp.
- Customer communication is prepared, including what changes for them and what doesn't.
- A rollback plan exists, and the trigger for using it is written down.

A scorecard version of this is in Appendix B. If the answer to any item is "we'll sort that out after go-live," it isn't ready.

## Run It in Stages

A sensible order:

1. **Scope and baseline.** What moves, what doesn't, and what the numbers are today.
2. **Knowledge transfer.** Documents first, then shadowing, then reverse shadowing.
3. **Supervised ramp.** The receiving team handles a growing share while the original team stays close.
4. **Cutover.** Only when the readiness criteria are met.
5. **Stabilization.** A defined period of closer measurement and a named owner for problems.
6. **Handoff.** Normal governance takes over, and the transition is closed formally.

**Warning:** Do not release the original team until stabilization is finished. The most expensive knowledge in the operation walks out the door on the day people are told they are no longer needed.

## Looking After the Team

A transition is a change to people's jobs, and it gets handled as if it were only a change to a process. Three groups are affected, and each needs a plan.

**The team handing the work off.**
- Tell them early, and tell them the truth, including what you don't yet know. People fill silence with the worst version.
- Be clear about what their role becomes. If you can't say yet, say when you will be able to.
- Ask them to help build the knowledge transfer, and recognize that you are asking them to document themselves out of a task. That needs to be acknowledged, not ignored.

**The team receiving the work.**
- Don't hand over work without the context behind it. Rules without reasons produce bad judgment calls.
- Protect their ramp. Pressure to hit full volume quickly is how quality problems start.
- Give them a direct line to the original team during stabilization.

**The team that keeps the harder work.**
- See the earlier warning about the remaining queue. Adjust targets and expectations to match what is actually left.

**Warning:** Watch for the point where the original team stops volunteering information. That is usually the sign that trust has broken, and it's far cheaper to repair early.

## Customers and Stakeholders

Customers shouldn't find out the delivery model changed because something went wrong. Decide what they need to know, when, and from whom. In most cases, the right message is short: what is changing, what is not, who to contact, and how to raise a concern.

Keep stakeholders informed on a fixed schedule through stabilization, even when there is nothing new. The same applies to internal leadership: bad news that arrives early is manageable, and the same news that arrives late looks like a cover-up.

## Stabilization: Judge Whether It Works

Launch is not success. For a set period after the move, review the measures from the baseline weekly. Decide in advance:

- What result counts as stable.
- What result triggers a fix.
- What result triggers a rollback.

Be willing to change the plan if the data says the original assumptions were wrong. That is a good outcome, not a failure. Writing the triggers down beforehand matters because, in the moment, everyone will want to explain why the numbers are fine.

## Governing a Partner After the Move

Moving the work does not move the accountability. Keep:

- A written scope and service levels the partner can actually measure.
- A regular service review with real numbers, not a slide of good news. (See the [Service Review & Executive Business Review Guide](Service_Review_EBR_Guide.md).)
- A single owner on your side for the relationship.
- Clear ownership for every handoff point, so issues do not fall into the gap between teams.
- A way to see quality directly, through sampling or audit, not only through the partner's reporting.
- An exit path: what happens to the knowledge, the tooling and the data if the arrangement ends. Agree it while the relationship is good. The [Vendor Management & Third-Party Performance Framework](Vendor_Management_Framework.md) covers the governance side in more detail.

## Using AI and Automation Without Fooling Yourself

- Start with one narrow category and measure it against the human baseline.
- Check accuracy, not just speed.
- Keep a human path for anything the tool is unsure about, and make it easy for the customer to reach.
- Track what the tool saves and what it adds, including review time and customer frustration.
- Recheck the results after a few months, because the first results are rarely the lasting ones.

**Warning:** Deflection is not resolution. A customer who gives up has not been helped. Measure whether the problem was solved, not whether a ticket was avoided.

## Common Mistakes

- Moving a queue because it is expensive without checking why it is expensive.
- Taking the stated reason for the move at face value.
- Treating documentation as something to finish after the move.
- Skipping the baseline, then arguing about results.
- Using a single good week as the baseline.
- Letting the original team disperse before the new one is stable.
- Ignoring what happens to the work that stays behind.
- Telling the team late, or only after customers have heard.
- Judging success by launch date.
- Assuming the partner's report is the whole picture.
- Having no exit path, and discovering the dependency when it matters.

## Summary Checklist

- [ ] Reason for the move confirmed in writing
- [ ] Work scored and a recommendation written down
- [ ] Impact on remaining work assessed
- [ ] Baseline measures captured over enough history
- [ ] Success, fix and rollback triggers defined
- [ ] Documentation written and tested by someone new
- [ ] Receiving team trained and supervised
- [ ] Escalation paths named
- [ ] Team and customer communication planned
- [ ] Cutover based on criteria, not a date
- [ ] Stabilization period with a named owner
- [ ] Formal handoff to normal governance
- [ ] Exit path agreed where a partner is involved
- [ ] Lessons written down for the next move

---

## Appendix A: Baseline Measures (One Page)

Fill this in before anything moves. Use real history and note the period it covers.

**Queue / work category:** ______________________  
**Current delivery model:** ______________________  
**Proposed delivery model:** ______________________  
**Reason for the move (cost / coverage / growth / other):** ______________________  
**Baseline period:** ______ to ______  **Unusual events in that period:** ______________________

| Area | Measure | Baseline | Source | Target / acceptable range | Rollback trigger |
|---|---|---|---|---|---|
| Customer | Satisfaction | | | | |
| Customer | Time to resolve | | | | |
| Customer | Repeat contacts | | | | |
| Quality | Resolution accuracy / QA score | | | | |
| Capacity | Backlog | | | | |
| Capacity | Response time | | | | |
| Capacity | Coverage hours | | | | |
| Cost | Cost per contact (fully loaded) | | | | |
| Cost | Cost of managing the new arrangement | | | | |
| People | Attrition / absence | | | | |

**Owner of this baseline:** ______________________  **Date agreed:** ______

## Appendix B: Readiness Scorecard

Score each item **Ready / Partial / Not ready**. Any "Not ready" holds the cutover. Any "Partial" needs a named owner and a date.

| # | Criterion | Status | Owner | Evidence |
|---|---|---|---|---|
| 1 | Procedures and articles current, tested by someone who did not write them | | | |
| 2 | Receiving team trained and has handled real cases under supervision | | | |
| 3 | Escalation paths and contacts named | | | |
| 4 | Tools and access working | | | |
| 5 | Quality checks defined and owned | | | |
| 6 | Workforce plan covers volume, seasonality and ramp | | | |
| 7 | Customer and stakeholder communication ready | | | |
| 8 | Team communication delivered | | | |
| 9 | Rollback plan and trigger written down | | | |
| 10 | Stabilization owner and review schedule named | | | |

**Decision:** Proceed / Hold   **Decided by:** ______________   **Date:** ______

---

*This guide describes how I'd approach moving support work between delivery models. It's an approach to defend and adapt, not a record of results, and every situation will change some of the details.*
