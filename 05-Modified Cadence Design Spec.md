# Executive summary

This document specifies a cadence model for AI-assisted product
development. It is the fourth and final follow-on artifact from
*AI-Assisted Velocity and the Limits of Modern PDLC/SDLC* and depends on
the validated change (Unit-of-Work spec), the production standard
(Finishing-Discipline spec), and the producer-owner-approver model
(Role-and-Gating spec) as foundational vocabulary.

The recommended model is **continuous flow at the team level with
outcome-anchored alignment at the program level and quarterly alignment
at the portfolio level.** Sprints are removed as the team-level batching
mechanism: validated changes commit continuously, gate continuously, and
close continuously. Calendar-driven program ceremonies (sprint planning,
sprint review, retrospective, PI planning, system demo,
inspect-and-adapt) are replaced or repurposed. The funding cadence and
the regulatory cadences are preserved because they are organizationally
exogenous. Social rituals for belonging and shared sense-making are
preserved at adjusted cadences because they are not throughput devices
but cohesion devices.

The model places review points at **customer-time boundaries**
(validation windows, A/B significance windows, regulatory waiting
periods) rather than at code-production boundaries, on the principle
that the production rate is no longer the binding constraint and that
aligning ceremonies to it confuses activity with progress. The **Scrum
Master** and **Release Train Engineer** roles are kept by name and let
the function evolve: under the new cadence they take on queue health,
coordination, escalation, and learning synthesis.

The remainder of this document specifies the cadence at each level, the
preserved and replaced elements from current frameworks, the Scrum
Master / RTE role, two illustrative cadences, migration considerations,
and open questions.

# 1. Problem context

Current PDLC/SDLC cadence is largely sprint-derived. At team level,
two-week sprints structure planning, commitment, daily synchronization,
review, and retrospection. At program level, SAFe-style program
increments aggregate sprints into 8-to-12-week cycles with their own
planning, demonstration, and improvement ceremonies. The cadence was
calibrated for two conditions: production capacity was the binding
constraint, and replanning was expensive. Both conditions are
dissolving.

When production capacity is no longer the binding constraint, the
rationale for batching weakens. Sprints amortize planning overhead by
committing a sprint’s worth of work at planning time; if planning is
itself fast, the amortization no longer pays. Continuous commitment
becomes feasible, and continuous commitment is more responsive to the
validation evidence that the unit-of-work spec puts at the center.

When the validated change is the unit, the natural review cadence is
*outcome-anchored* rather than calendar-anchored. Outcomes have their
own clock — it ticks when validated changes close, when validation
evidence accumulates, when hypotheses are confirmed or disconfirmed.
Asking an outcome to demonstrate progress every two weeks regardless of
whether validation evidence is in is a category error.

Three specific failures recur with current cadence under AI-assisted
production.

The first is **ceremony-as-progress.** When production is fast,
sprint-based ceremonies risk becoming a record of activity rather than
of outcome. Velocity-as-points-per-sprint, story closure rates, and
story-completion-by-sprint-end all measure things that are no longer
expensive and no longer signal value.

The second is **calendar-driven review of customer-time work.** A
two-week sprint review of a feature whose validation window is six weeks
reviews the wrong thing — it reviews shipped activity, not validated
outcomes. The signal arrives later than the ceremony.

The third is **batching as a coordination tax.** Sprint-aligned
coordination across teams forces teams whose natural rhythms differ to
synchronize at sprint boundaries, which is rarely the cheapest
coordination point and is often the most expensive.

# 2. Evaluation criteria

Ten criteria are used to evaluate candidate cadence models.

1.  **Compatible with continuous-flow validated changes.** The cadence
    does not require artificial batching of work into time-bound
    increments.
2.  **Customer-time review placement.** Review and demonstration happen
    when validation evidence is in, not on a fixed calendar.
3.  **Preserves coordination at scale.** The cadence supports
    coordination across many teams without requiring sprint-aligned
    synchronization.
4.  **Preserves funding cadence.** Funding decisions still happen on the
    organization’s funding rhythm (typically quarterly).
5.  **Preserves social rituals for belonging.** The cadence retains
    predictable rhythms for team cohesion, public commitment, and shared
    context.
6.  **Adoptable from current state.** Existing teams can transition
    without losing functioning practices in the gap.
7.  **Avoids ceremony bloat.** The number of recurring ceremonies is
    bounded; new ceremonies are added only when they replace something
    or solve something specific.
8.  **Compatible with multi-team coordination.** Coordination
    obligations between validated changes (per the unit-of-work spec)
    are accommodated by the cadence.
9.  **Supports learning capture.** Inconclusive validation outcomes (per
    the unit-of-work spec) trigger learning capture; the cadence ensures
    the learning is integrated, not lost.
10. **Compatible with regulator and audit cycles.** Mandatory external
    cycles (regulatory submissions, audits, attestations) fit naturally.

# 3. Candidate cadences canvassed

Five candidates are evaluated.

**Sprint-based (Scrum).** Fixed-time batches at team level; ceremonies
on each cycle. The status quo for many teams. Fails customer-time review
placement and is in tension with continuous-flow validated changes.

**SAFe PI cadence.** Sprints at team level plus 8-to-12-week program
increments at program level. More elaborate ceremony stack. Fails
customer-time review placement at both levels and forces multi-team
synchronization at sprint boundaries.

**Kanban.** Continuous flow with WIP limits. Minimal calendar ceremony.
Compatible with continuous-flow validated changes but weak on
customer-time review placement (no defined review point) and weak on
social ritual.

**Shape Up.** Fixed 6-week cycles plus 2-week cooldown. Cycles are
commitments; bets are placed at cycle boundaries. Compatible with some
continuous-flow ideas but still time-batched. Weak on multi-team
coordination.

**Continuous flow with outcome-anchored alignment** (the recommended
model). Continuous flow at team level; outcome-anchored review and demo
at program level; quarterly alignment at portfolio level. Calendar
ceremonies are minimized at team and program level and preserved only
where they serve cohesion or external requirements.

A summary of the canvass:

<table>
<colgroup>
<col style="width: 35%" />
<col style="width: 9%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 13%" />
<col style="width: 17%" />
</colgroup>
<thead>
<tr>
<th>Criterion</th>
<th>Scrum</th>
<th>SAFe PI</th>
<th>Kanban</th>
<th>Shape Up</th>
<th><strong>Cont. + outc.</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td>Continuous-flow compatible</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Partial</td>
<td>Yes</td>
</tr>
<tr>
<td>Customer-time review</td>
<td>No</td>
<td>No</td>
<td>Weak</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>Coordination at scale</td>
<td>Weak</td>
<td>Yes</td>
<td>Weak</td>
<td>Weak</td>
<td>Yes</td>
</tr>
<tr>
<td>Funding-cadence preserved</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Social rituals preserved</td>
<td>Yes</td>
<td>Yes</td>
<td>Weak</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Adoptable</td>
<td>N/A</td>
<td>N/A</td>
<td>Medium</td>
<td>Hard</td>
<td>Medium</td>
</tr>
<tr>
<td>Avoids ceremony bloat</td>
<td>Weak</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Multi-team coordination</td>
<td>Weak</td>
<td>Yes</td>
<td>Weak</td>
<td>Weak</td>
<td>Yes</td>
</tr>
<tr>
<td>Learning capture</td>
<td>Weak</td>
<td>Medium</td>
<td>Weak</td>
<td>Medium</td>
<td>Yes</td>
</tr>
<tr>
<td>Regulator/audit compatible</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
</tbody>
</table>

# 4. Recommendation

The recommended cadence is **continuous flow at the team level with
outcome-anchored alignment at the program level and quarterly alignment
at the portfolio level.**

The recommendation rests on three observations.

First, only this cadence model scores well on the customer-time review
placement criterion, which is the one criterion that is structural
rather than convenient. Sprints, PIs, and Shape Up cycles all anchor
reviews to code-production rhythms. Kanban omits the review point; this
model places it at the customer-time boundary the validation window
defines.

Second, the model preserves coordination at scale through
outcome-anchored alignment rather than through sprint-aligned
synchronization. Teams whose natural rhythms differ no longer have to
synchronize at artificial calendar boundaries; they coordinate at
outcome boundaries (where their work actually intersects) and at
portfolio boundaries (where strategy and funding actually require).

Third, the model is adoptable. It preserves what current frameworks do
well (funding cadence, social rituals, multi-team coordination at the
right level) and replaces only what current frameworks do poorly (sprint
batching, calendar-driven review, ceremony bloat). The migration is
incremental rather than wholesale.

# 5. The cadence at each level

The model operates at four levels: team, outcome, program, and
portfolio. Each level has a defined cadence, defined ceremonies, and
defined participants.

## 5.1 Team level

**Default cadence.** Continuous. Validated changes commit, progress,
gate, and close on their own clock.

**Defined ceremonies.**

- **Daily async sync (optional).** A short written status from each
  owner of in-flight validated changes. Typically a paragraph; reads in
  five minutes for a team. Optional: teams may choose to skip if
  blockers are routinely surfaced through other channels.
- **Twice-weekly synchronous sync (15-30 minutes).** A standing meeting
  where blockers are surfaced and dependencies are discussed. Replaces
  daily standup. The reduced frequency reflects that continuous-flow
  work needs less daily coordination than batched sprint work.
- **Ad-hoc rapid response.** Owners may call ad-hoc syncs for blocked
  validated changes. The Scrum Master / RTE (Section 7) helps
  coordinate.

**Defined non-ceremonies.**

- **No sprint planning.** Commitment is per-validated-change at the
  commit gate; there is no batched commitment.
- **No sprint review.** Review is outcome-anchored at the program level
  (Section 5.3).
- **No retrospective.** Retrospection is per-closed-validated-change in
  the form of learning capture (mandatory for inconclusive outcomes) and
  is synthesized periodically by the Scrum Master / RTE.

## 5.2 Outcome level

**Default cadence.** Event-driven, with a periodic backstop. Outcome
reviews happen when material validation evidence has accumulated,
typically monthly but variable based on outcome velocity.

**Defined ceremonies.**

- **Outcome review.** When material validation evidence has accumulated,
  the outcome owner convenes a review with the relevant owners,
  approvers, and stakeholders. Agenda: what validated changes have
  closed, what evidence they produced, what the outcome’s status is,
  what the next set of validated changes target, what the open questions
  are. Outcome reviews are not demonstrations of activity; they are
  honest reckonings with evidence.
- **Outcome demo.** When an outcome’s progress is material enough to be
  demonstrated to wider audiences (other teams, leadership, customers),
  the outcome owner runs a demo. Outcome demos are voluntary and
  event-driven, not calendared.
- **Per-validated-change learning capture.** Owned by the validated
  change’s owner; mandatory for inconclusive outcomes. The capture
  records what was learned, what would be done differently, what the
  inconclusive evidence implies for future similar changes. Captures are
  filed against the parent outcome and are synthesized at outcome
  reviews.

## 5.3 Program level

The “program level” in this model is a coordination layer above outcomes
— typically a related set of outcomes serving a common business area,
customer segment, or strategic theme.

**Default cadence.** Monthly, with event-driven additions.

**Defined ceremonies.**

- **Monthly program coordination.** A standing meeting at which outcome
  owners surface coordination obligations, dependencies, and blockers
  across outcomes. Replaces SAFe PI planning’s coordination function
  with a lighter, higher-frequency cadence. Replaces the
  Inspect-and-Adapt’s coordination function with the per-outcome
  learning capture and synthesis.
- **Cross-team dispute resolution.** Tier-2 disputes (Role-and-Gating
  spec, Section 10) are typically resolved at the program level. The
  monthly program coordination is the default forum; ad-hoc escalations
  are also supported.
- **Standards consultation.** Standard owners (Finishing-Discipline
  spec) consult with program-level participants on proposed standards
  changes that materially affect work in this program. This is not a
  separate ceremony; it is a recurring agenda item.

**Defined non-ceremonies.**

- **No PI planning.** Replaced by monthly coordination plus quarterly
  portfolio alignment.
- **No system demo.** Replaced by outcome demos when material.
- **No Inspect-and-Adapt.** Replaced by per-validated-change learning
  capture, monthly synthesis, and quarterly standards review.

## 5.4 Portfolio level

**Default cadence.** Quarterly, aligned with the organization’s funding
cycle.

**Defined ceremonies.**

- **Quarterly portfolio alignment.** The forum at which strategic
  objectives are set or refreshed, outcomes are aligned to objectives,
  funding is allocated, and tier-3 disputes (Role-and-Gating spec) are
  resolved. This is the portfolio-governance function.
- **Annual strategy.** At least once per year, a strategy-setting cycle
  establishes or refreshes the strategic objectives that outcomes serve.
  Some organizations run this annually; some semi-annually; the model
  accommodates either.
- **Standards review.** Per the finishing-discipline spec, each standard
  is reviewed quarterly by its standard owner. The reviews are not a
  portfolio ceremony per se but happen on the same cadence and inform
  portfolio decisions about approver capacity and standards investment.

# 6. Customer-time review placement

A central principle of the model is that review points sit at
customer-time boundaries, not at code-production boundaries. This is
operationalized as follows.

- **Validation windows are committed at the validated change commit
  gate.** They are set by what the validation method actually requires
  (A/B significance, observation period, regulatory waiting), not by
  sprint boundary.
- **Outcome reviews trigger when material validation evidence is in.**
  This is event-driven, with a monthly backstop to ensure outcomes do
  not go reviewed for more than one month. The backstop exists to
  surface stalled outcomes; it is not the primary trigger.
- **Outcome demos run when an outcome has material progress to
  demonstrate**. They are not calendared.
- **Quarterly portfolio alignment is calendared because funding is
  calendared.** This is an exception that the model accepts because the
  funding cadence is exogenous.

The contrast with sprint-based cadence is that the calendar serves only
the things that are themselves calendar-bound (funding, regulator
submissions, annual strategy). Everything else runs on the clock of the
work it reviews.

# 7. The Scrum Master / RTE role, evolved

The role-and-gating spec deferred a process-facilitation role to this
document. The role exists; the deliberate choice is to keep the existing
names — **Scrum Master** at team level and **Release Train Engineer** at
program level — and let the function evolve rather than introduce a new
title. The titles are widely understood, the people in them already
exist, and renaming them telegraphs disruption that is not necessary.
What changes is the responsibility set, not the role name.

In the recommended model, the evolved Scrum Master and RTE
responsibilities include:

- **Queue health.** Monitors the queues of approver capacity (per
  Role-and-Gating spec, Section 8); surfaces sustained queue-depth
  issues to standard owners.
- **Coordination facilitation.** Helps owners surface and resolve
  coordination obligations across validated changes; facilitates the
  monthly program coordination ceremony.
- **Dispute escalation.** Helps tier-1 disputes find their standard
  owner; helps tier-2 disputes find their outcome owner; surfaces tier-3
  disputes to the portfolio.
- **Learning synthesis.** Reads per-validated-change learning captures
  across the team or program; identifies patterns; surfaces patterns to
  standard owners (so standards can evolve) and to portfolio (so
  strategic implications can be considered).
- **Cadence stewardship.** Watches for cadence drift — ceremonies that
  have lost their function, ceremonies that should have been added,
  ceremonies that have grown to consume more time than they return.

Scrum-Master-style coverage typically operates at the team level;
RTE-style coverage at the program level. At smaller scale, the role can
be fractional (a person spending part of their time on it); at larger
scale, it can be a dedicated role with deputies. It is not a leadership
role; it is a service role.

# 8. What is preserved, modified, and replaced

The following table summarizes the cadence elements from current
frameworks and how they are treated in the recommended model.

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 19%" />
<col style="width: 53%" />
</colgroup>
<thead>
<tr>
<th>Current element</th>
<th>Treatment</th>
<th>Replacement / modification</th>
</tr>
</thead>
<tbody>
<tr>
<td>Sprint (team batching)</td>
<td>Replaced</td>
<td>Continuous flow of validated changes</td>
</tr>
<tr>
<td>Sprint planning</td>
<td>Replaced</td>
<td>Continuous commit per validated change</td>
</tr>
<tr>
<td>Sprint review</td>
<td>Replaced</td>
<td>Outcome review (event-driven, monthly backstop)</td>
</tr>
<tr>
<td>Sprint retrospective</td>
<td>Replaced</td>
<td>Per-validated-change learning capture + synthesis by Scrum Master /
RTE</td>
</tr>
<tr>
<td>Daily standup</td>
<td>Modified</td>
<td>Optional async daily + twice-weekly synchronous sync</td>
</tr>
<tr>
<td>Backlog grooming</td>
<td>Replaced</td>
<td>Continuous unit-level refinement in proposed state</td>
</tr>
<tr>
<td>PI planning (8-12 wk batching)</td>
<td>Replaced</td>
<td>Monthly program coordination + qtrly portfolio alignment</td>
</tr>
<tr>
<td>System demo</td>
<td>Replaced</td>
<td>Outcome demo (event-driven)</td>
</tr>
<tr>
<td>Inspect-and-Adapt</td>
<td>Replaced</td>
<td>Quarterly standards review + ongoing learning synthesis</td>
</tr>
<tr>
<td>Quarterly funding cycle</td>
<td>Preserved</td>
<td>Aligned to portfolio quarterly alignment</td>
</tr>
<tr>
<td>Annual strategy</td>
<td>Preserved</td>
<td>Annual or semi-annual; sets objectives that outcomes serve</td>
</tr>
<tr>
<td>Regulator / audit cycles</td>
<td>Preserved</td>
<td>External; treated as exogenous</td>
</tr>
<tr>
<td>Standards review (per PS spec)</td>
<td>Preserved</td>
<td>Quarterly per Production Standards spec</td>
</tr>
<tr>
<td>Scrum Master / RTE</td>
<td>Preserved (evolved)</td>
<td>Same titles; expanded responsibilities</td>
</tr>
</tbody>
</table>

# 9. Examples

Two illustrative cadences.

**A small product team running a single outcome.**

- **Team level.** Continuous flow. Twice-weekly Tuesday/Friday 20-minute
  sync. Async daily-status optional and informally used.
- **Outcome level.** Outcome review every 3-4 weeks (when validation
  evidence accumulates from closed validated changes) or monthly at
  minimum.
- **Program level.** N/A; the team is small enough to coordinate
  directly with adjacent teams.
- **Portfolio level.** Participates in the organization’s quarterly
  portfolio alignment.

A typical week for the team contains: continuous validated-change work;
two 20-minute syncs; ad-hoc reviewer engagement; about one
outcome-related conversation per week (review, demo, or learning
capture).

**A multi-team program shipping outcomes across several customer-facing
surfaces.**

- **Team level (each team).** As above.
- **Outcome level.** Each outcome owner runs reviews monthly
  (event-driven within month). Cross-outcome demos when material.
- **Program level.** Monthly two-hour program coordination at which
  outcome owners surface coordination, dispute, and
  standards-consultation needs. Scrum Master / RTE runs the meeting and
  tracks follow-ups.
- **Portfolio level.** Quarterly half-day portfolio alignment at which
  the program’s outcomes are aligned to strategic objectives, funding is
  confirmed, and tier-3 disputes are resolved.

A typical month for the program contains: continuous team-level work;
weekly team syncs; ~4 outcome reviews across the program (one per
outcome on average); one program coordination meeting; ad-hoc
cross-outcome demos as warranted. Quarterly: one portfolio alignment;
one standards-review cycle per relevant standard.

# 10. Migration considerations

The transition from current cadence to this model is incremental and
team-by-team rather than wholesale.

**Start with continuous commit at the team level.** A team can begin
committing validated changes continuously while still running sprints;
the sprint container becomes vestigial as commitment migrates out of
sprint planning. Once continuous commitment is established, sprint
planning naturally falls away.

**Replace sprint review with outcome review next.** Once validated
changes are committing continuously and producing validation evidence,
outcome reviews become more useful than sprint reviews. The Scrum Master
/ RTE (or the closest existing role) helps establish the cadence.

**Replace retrospectives with learning capture next.**
Per-validated-change learning capture is most valuable for inconclusive
outcomes. As inconclusive outcomes accumulate, the synthesis becomes the
team’s retrospection.

**Modify standup last.** Daily standup is the most habit-rooted ceremony
and the change is socially sensitive. Move to optional async daily +
twice-weekly sync only after the team is comfortable with
continuous-flow work; doing it earlier risks losing coordination before
the new cadence has compensated.

**At program level, reduce PI planning gradually.** A first step is to
shorten PI planning and to repurpose half its time for outcome-anchored
alignment. Over two or three cycles, the planning component shrinks and
the alignment component takes over. PI planning eventually goes away;
quarterly portfolio alignment takes its place.

**Resist the temptation to delete ceremonies en masse.** Ceremonies
serve functions; deleting them without replacement removes the function
as well as the ceremony. Always identify the function being served
before removing or modifying a ceremony.

# 11. Open questions

Five questions are flagged for the next iteration.

**Cadence at very large scale.** This model has been designed with
single programs (multiple teams; one or two layers of outcome
aggregation) in mind. Organizations with many programs, multi-program
coordination needs, and centralized portfolio governance will need
additional layers. The model accommodates additional layers by recursion
(programs aggregate into portfolios; portfolios aggregate into
programs-of-programs), but the operational details of the higher levels
are unspecified.

**Asynchronous-first vs synchronous-first defaults.** The model is
moderately synchronous (twice-weekly syncs, monthly program
coordination, quarterly portfolio alignment). Some organizations operate
asynchronous-first; the cadence accommodates this but the asynchronous
protocols are unspecified.

**Regulated-domain cadence.** Regulated work has additional cycles
(audit prep, regulator submission windows, attestation refresh) that
interact with the cadence in ways this spec does not detail. Regulated
programs likely need additional ceremonies aligned to the regulator’s
calendar.

**Cadence for purely operational work.** Maintenance, dependency
upgrades, incident remediation, security patching — work that does not
fit the validated-change shape — may need its own cadence treatment. The
unit-of-work spec flagged this as an open question (the maintenance unit
type); the cadence implications follow.

**Portfolio governance composition.** This spec refers to “portfolio
governance” as the body that resolves tier-3 disputes and conducts
quarterly alignment. The composition, authority, and decision protocols
of that body are organization-specific and out of scope here, but they
are on the critical path for adoption.

These are the largest known unresolved questions. Smaller questions are
noted inline above.


---

*Part of [ai-agile](https://github.com/itripn/ai-agile) by Ron Forrester. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
