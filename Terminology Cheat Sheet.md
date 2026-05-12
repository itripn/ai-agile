This cheat sheet is a quick reference for the vocabulary used across the
position paper and the four design specs. It is grouped by concept area
and is intended for scanning while reading the corpus, not for
sequential reading. The first section maps current Scrum/SAFe
terminology to the corpus terms; the remaining sections define corpus
terms by area. An alphabetical index at the end provides a quick lookup.
Where a corpus term reuses a familiar word in a tighter sense, the
definition flags this.

# 1. From your current vocabulary

The mapping below is approximate. Most rows are not 1:1 substitutions;
the right-hand term often carries different scope, accountability, or
lifecycle than the left-hand term. The notes column flags the most
consequential differences.

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 28%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr>
<th>If you say (Scrum/SAFe)</th>
<th>We say</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td>Story (user story)</td>
<td>Validated change</td>
<td>Sized by hypothesis, not build effort. Includes evidence-anchored
closure. Maintenance work needs a different unit type (open).</td>
</tr>
<tr>
<td>Epic</td>
<td>Outcome (aggregator)</td>
<td>Causal aggregation of validated changes serving a common business or
customer effect.</td>
</tr>
<tr>
<td>Capability</td>
<td>Long-running outcome</td>
<td>A SAFe capability is well-modeled as an outcome aggregating a stream
of validated changes over time.</td>
</tr>
<tr>
<td>Sprint</td>
<td>(no equivalent)</td>
<td>Removed at team level. Validated changes commit, gate, and close on
their own clock.</td>
</tr>
<tr>
<td>Sprint planning</td>
<td>Continuous commit</td>
<td>Per-validated-change at the commit gate; no batched commitment.</td>
</tr>
<tr>
<td>Sprint review</td>
<td>Outcome review</td>
<td>Event-driven (when validation evidence is in); monthly
backstop.</td>
</tr>
<tr>
<td>Sprint retrospective</td>
<td>Per-validated-change learning capture (+ synthesis)</td>
<td>Per closed unit; mandatory for inconclusive outcomes.</td>
</tr>
<tr>
<td>Daily standup</td>
<td>Twice-weekly synchronous sync (+ optional async)</td>
<td>Reduced frequency; continuous-flow work needs less daily
coordination.</td>
</tr>
<tr>
<td>Backlog grooming</td>
<td>Continuous unit refinement (in proposed state)</td>
<td>Happens whenever; not a calendared ceremony.</td>
</tr>
<tr>
<td>PI Planning</td>
<td>Monthly program coordination + quarterly portfolio alignment</td>
<td>The coordination function persists; the multi-week batching does
not.</td>
</tr>
<tr>
<td>System Demo</td>
<td>Outcome demo</td>
<td>Event-driven when material progress accumulates.</td>
</tr>
<tr>
<td>Inspect &amp; Adapt</td>
<td>Quarterly standards review + ongoing learning synthesis</td>
<td>Spread across continuous learning capture and quarterly standards
review.</td>
</tr>
<tr>
<td>Definition of Done</td>
<td>Production standard</td>
<td>Major upgrade: organization-owned, artifact-class-typed, versioned,
attested. Not a team checklist.</td>
</tr>
<tr>
<td>Acceptance criteria</td>
<td>Decision criteria</td>
<td>Specific to the validated change’s hypothesis; committed at commit
gate.</td>
</tr>
<tr>
<td>Product Owner</td>
<td>Validated Change Owner</td>
<td>Functional, not 1:1. POs frequently become Validated Change Owners;
many owners come from other roles. Distinct from “Owner” in the Scrum
sense.</td>
</tr>
<tr>
<td>Scrum Master</td>
<td>Scrum Master (responsibilities evolve)</td>
<td>Same title; responsibilities expand to queue health, coordination,
learning synthesis.</td>
</tr>
<tr>
<td>Release Train Engineer</td>
<td>Release Train Engineer (responsibilities evolve)</td>
<td>Same title; same responsibilities as evolved Scrum Master, applied
at program scale.</td>
</tr>
<tr>
<td>Architect</td>
<td>Standard Owner or Integration Approver</td>
<td>Architects whose work is standards governance become Standard
Owners; integration-focused architects become Integration
Approvers.</td>
</tr>
<tr>
<td>Product Manager</td>
<td>Outcome Owner (often also Validated Change Owner)</td>
<td>Multi-role; PMs often own outcomes at the aggregator level and
frequently own validated changes at the unit level.</td>
</tr>
<tr>
<td>QA / Test team</td>
<td>Approver for testing dimension</td>
<td>Reframed as approvers within the production standard’s testing
dimension.</td>
</tr>
<tr>
<td>Security team</td>
<td>Security Approver</td>
<td>Reframed as named approver role with published capacity.</td>
</tr>
<tr>
<td>Story points</td>
<td>(no direct equivalent — deliberately)</td>
<td>Validated change is sized by hypothesis scope, not build effort.
Story-point analogues are an anti-pattern.</td>
</tr>
<tr>
<td>Velocity</td>
<td>(no direct equivalent — deliberately)</td>
<td>Outcome closure rates, learning capture rates, and
finishing-standard exception rates are better signals.</td>
</tr>
</tbody>
</table>

# 2. Units of work

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 62%" />
<col style="width: 21%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Definition</th>
<th>See also</th>
</tr>
</thead>
<tbody>
<tr>
<td>Validated change</td>
<td>The primary unit. Claimed change + hypothesis + production-grade
implementation gated by production standard + validation gate + named
owner.</td>
<td>Hypothesis, Owner, Production standard</td>
</tr>
<tr>
<td>Hypothesis</td>
<td>Statement of expected effect: what changes, for whom, by when, and
how detected. Committed at commit gate.</td>
<td>Decision criteria, Validation method</td>
</tr>
<tr>
<td>Decision criteria</td>
<td>Specific evidence that triggers validated, invalidated, or
inconclusive at the closure gate. Committed at commit gate.</td>
<td>Hypothesis, Closure gate</td>
</tr>
<tr>
<td>Validation method</td>
<td>How evidence is collected (instrumentation, A/B test, telemetry
analysis, qualitative research, attested compliance check).</td>
<td>Validation window</td>
</tr>
<tr>
<td>Validation window</td>
<td>Time period over which validation evidence is collected. Set by what
the method requires, not by sprint.</td>
<td>Customer-time boundary</td>
</tr>
<tr>
<td>Rollback condition</td>
<td>Specific evidence that triggers immediate rollback. Committed at
commit gate.</td>
<td>Rollback</td>
</tr>
<tr>
<td>Outcome (record)</td>
<td>The closing record of a validated change: actual evidence + decision
(validated / invalidated / inconclusive).</td>
<td>Closure gate</td>
</tr>
<tr>
<td>Outcome (aggregator)</td>
<td>A higher-order business or customer outcome that aggregates one or
more validated changes pursued to produce it. Distinct from the
record.</td>
<td>Strategic objective</td>
</tr>
<tr>
<td>Strategic objective</td>
<td>Portfolio-level objective; outcomes aggregate to objectives.</td>
<td>Quarterly portfolio alignment</td>
</tr>
<tr>
<td>Experiment</td>
<td>Sibling unit type whose output is learning, not a shipped change.
Used to inform decisions about parent validated changes.</td>
<td>Validated change</td>
</tr>
<tr>
<td>Maintenance unit</td>
<td>Open question. Proposed lighter-weight sibling unit type for routine
operational work that lacks a user-visible hypothesis.</td>
<td>Open question</td>
</tr>
<tr>
<td>Coordination obligation</td>
<td>Explicit obligation to engage another team, approver, or
counterparty during a validated change’s lifecycle.</td>
<td>Brownfield</td>
</tr>
</tbody>
</table>

Note on “outcome”: the term has two distinct uses. The closing record of
a validated change is one; the aggregator above the validated change is
the other. Context disambiguates; flagged when ambiguous.

# 3. Lifecycle states

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr>
<th>State</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr>
<td>Proposed</td>
<td>Claim and hypothesis exist; not yet committed to. Effort to produce
should not yet be invested.</td>
</tr>
<tr>
<td>Committed</td>
<td>Accepted into work flow. Owner assigned; hypothesis, criteria, and
production standard locked.</td>
</tr>
<tr>
<td>In progress</td>
<td>Production work underway.</td>
</tr>
<tr>
<td>Production-ready</td>
<td>Implementation meets production standard; all required automated
checks and attestations recorded; awaiting deployment / rollout.</td>
</tr>
<tr>
<td>In validation</td>
<td>Deployed or rolled out; validation method collecting evidence within
the validation window.</td>
</tr>
<tr>
<td>Validated</td>
<td>Evidence confirms hypothesis. Closed positive.</td>
</tr>
<tr>
<td>Invalidated</td>
<td>Evidence disconfirms hypothesis. Closed negative; rollback / modify
/ keep-with-documentation per owner judgment.</td>
</tr>
<tr>
<td>Inconclusive</td>
<td>Evidence neither confirms nor disconfirms. Closed ambiguous;
learning capture mandatory.</td>
</tr>
<tr>
<td>Withdrawn</td>
<td>Abandoned before reaching production-ready. Legitimate; not a
failure.</td>
</tr>
</tbody>
</table>

# 4. Roles

<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 68%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr>
<th>Role</th>
<th>Definition</th>
<th>Type</th>
</tr>
</thead>
<tbody>
<tr>
<td>Producer</td>
<td>Anyone who creates an artifact (PM, designer, engineer, analyst, AI
agent under human supervision). Producer-set is wide; not gated by job
title.</td>
<td>Per-unit</td>
</tr>
<tr>
<td>Owner (Validated Change Owner)</td>
<td>Single named accountable person per validated change. Carries the
unit through its lifecycle; accepts operational consequences of the
shipped change. Distinct from Scrum Product Owner (though POs frequently
become VC Owners) and from Outcome Owner (a similar role at the
aggregator level).</td>
<td>Per-unit</td>
</tr>
<tr>
<td>Approver</td>
<td>Role-typed certifier of finishing-standard dimensions that cannot be
automated (security, compliance, accessibility, legal, brand, privacy,
etc.).</td>
<td>Persistent role + per-unit engagement</td>
</tr>
<tr>
<td>Integration Approver</td>
<td>For brownfield work, role-typed certifier that integration with
existing system is correct (platform, data, API integration
approvers).</td>
<td>Persistent role + per-unit engagement</td>
</tr>
<tr>
<td>Reviewer</td>
<td>Anyone the owner invites for judgment input. Non-authorizing. Adds
quality to the owner’s decisions.</td>
<td>Per-unit</td>
</tr>
<tr>
<td>Operator</td>
<td>Person accountable for ongoing operation of the artifact
post-rollout. Often the owner; can transfer at validation closure.</td>
<td>Per-unit; often persistent</td>
</tr>
<tr>
<td>Standard Owner</td>
<td>Owner of one or more production standards; responsible for
evolution, exceptions, and operational integrity of the standard.</td>
<td>Persistent</td>
</tr>
<tr>
<td>Scrum Master / RTE (evolved)</td>
<td>Existing titles preserved; responsibilities expand to include queue
health, coordination facilitation, dispute escalation, learning
synthesis, and cadence stewardship. Service role; not leadership.</td>
<td>Persistent</td>
</tr>
</tbody>
</table>

# 5. Gates

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 29%" />
<col style="width: 57%" />
</colgroup>
<thead>
<tr>
<th>Gate</th>
<th>Transition</th>
<th>Authorization</th>
</tr>
</thead>
<tbody>
<tr>
<td>Commit</td>
<td>Proposed → Committed</td>
<td>Owner</td>
</tr>
<tr>
<td>Production-ready</td>
<td>In progress → Production-ready</td>
<td>Automatic when production standard’s checks and attestations are
met. Cannot be overridden by individual judgment.</td>
</tr>
<tr>
<td>Validation</td>
<td>Production-ready → In validation</td>
<td>Owner (with rollout-method-specific automation)</td>
</tr>
<tr>
<td>Closure</td>
<td>In validation → Validated / Invalidated / Inconclusive</td>
<td>Owner; learning capture mandatory for inconclusive</td>
</tr>
<tr>
<td>Exception</td>
<td>Any state</td>
<td>Joint: Standard Owner + Exception Owner; documented rationale;
expiry date</td>
</tr>
</tbody>
</table>

# 6. Standards (production standards)

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr>
<td>Finishing standard</td>
<td>The codified set of requirements for a class of artifacts to be
production-grade. Organization-owned, not team-owned. Versioned and
named.</td>
</tr>
<tr>
<td>Production-grade</td>
<td>Meeting the production standard for the artifact’s class. Not
“shipping”; not “compiles”; standard satisfaction.</td>
</tr>
<tr>
<td>Artifact class</td>
<td>A category of artifact (mobile app, marketplace feature, internal
tool, regulated workflow, library, batch job, etc.). Each has its own
standard.</td>
</tr>
<tr>
<td>Dimension</td>
<td>An aspect of production-grade along which a standard specifies
requirements (tested, observable, accessible, performant, secure,
compliant, instrumented, rolled out safely, owned, documented).</td>
</tr>
<tr>
<td>Standards registry</td>
<td>Single canonical catalog of all current standards by class, with
names, versions, owners, approver roles, history, and current
exceptions.</td>
</tr>
<tr>
<td>Greenfield standard</td>
<td>Standard for a new, standalone artifact with no existing-system
integration. Typically narrower.</td>
</tr>
<tr>
<td>Brownfield standard</td>
<td>Standard for changes against an existing system. Typically stricter
on integration.</td>
</tr>
<tr>
<td>Hybrid standard</td>
<td>Standard for an artifact spanning both modes; union of relevant
requirements.</td>
</tr>
<tr>
<td>Attestation</td>
<td>The formal recorded judgment by a named approver that a standard
dimension is met. Timestamped and attached to the validated change.</td>
</tr>
<tr>
<td>Exception</td>
<td>A documented, time-bound, jointly-authorized deviation from a
standard for a specific validated change. First-class concept; not a
backdoor.</td>
</tr>
</tbody>
</table>

# 7. Cadence and ceremonies

<table>
<colgroup>
<col style="width: 22%" />
<col style="width: 77%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr>
<td>Continuous flow</td>
<td>Team-level cadence. Validated changes commit, gate, and close on
their own clock; no sprint batching.</td>
</tr>
<tr>
<td>Outcome-anchored alignment</td>
<td>Program-level cadence. Alignment is event-driven by accumulation of
validation evidence on outcomes; monthly backstop.</td>
</tr>
<tr>
<td>Customer-time boundary</td>
<td>A time boundary set by what real-world signal collection requires
(validation windows, A/B significance, observation, regulatory waiting).
The right placement for review points.</td>
</tr>
<tr>
<td>Code-production boundary</td>
<td>A time boundary set by code-production rhythm (sprint end, PI end).
The wrong placement for review points in this model.</td>
</tr>
<tr>
<td>Outcome review</td>
<td>Event-driven review of accumulated validation evidence on an
outcome; monthly backstop.</td>
</tr>
<tr>
<td>Outcome demo</td>
<td>Event-driven demonstration of material outcome progress to wider
audiences.</td>
</tr>
<tr>
<td>Per-validated-change learning capture</td>
<td>Owner-recorded capture of what was learned from a closed unit.
Mandatory for inconclusive outcomes.</td>
</tr>
<tr>
<td>Twice-weekly synchronous sync</td>
<td>15-30 minute team standing meeting; replaces daily standup.</td>
</tr>
<tr>
<td>Monthly program coordination</td>
<td>Program-level coordination ceremony; owners surface dependencies,
blockers, and standards-consultation needs.</td>
</tr>
<tr>
<td>Quarterly portfolio alignment</td>
<td>Strategic objectives, outcome alignment, funding allocation, tier-3
dispute resolution. Aligned with the funding cycle.</td>
</tr>
</tbody>
</table>

# 8. Cross-cutting concepts

<table style="width:100%;">
<colgroup>
<col style="width: 20%" />
<col style="width: 79%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr>
<td>Greenfield work</td>
<td>New, standalone artifacts without entanglement in an existing
operational system. Traditional PDLC essentially dissolves here.</td>
</tr>
<tr>
<td>Brownfield work</td>
<td>Additions to existing systems with prior commitments, dependencies,
regulatory exposure, and operational history. PDLC persists in modified
form.</td>
</tr>
<tr>
<td>Producer-set</td>
<td>The set of people (and AI agents) who can create artifacts. Wide in
this model.</td>
</tr>
<tr>
<td>Owner-set</td>
<td>The set of people who can own validated changes. Narrower; requires
authority and judgment to accept consequences.</td>
</tr>
<tr>
<td>Producer-owner disconnect</td>
<td>Failure mode where the producer cannot transfer enough operational
understanding for the owner to accept consequences. Handled by
documentation requirement and owner-refusal authority.</td>
</tr>
<tr>
<td>Capability-snapshot counterweight</td>
<td>An argument against AI-velocity claims that depends on current AI
capability gaps. Expires as models improve. Should not anchor
strategy.</td>
</tr>
<tr>
<td>Structural counterweight</td>
<td>An argument against AI-velocity claims that holds independent of AI
capability (regulation, customer-time, organizational coordination,
judgment, production standards). Durable.</td>
</tr>
</tbody>
</table>

# 9. Dispute escalation

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 40%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr>
<th>Tier</th>
<th>Between</th>
<th>Resolved by</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tier 1</td>
<td>Owner ↔︎ Approver within a single domain</td>
<td>Standard owner of the relevant standard</td>
</tr>
<tr>
<td>Tier 2</td>
<td>Owner ↔︎ Owner on coordination obligations</td>
<td>Outcome owner whose outcome both validated changes serve</td>
</tr>
<tr>
<td>Tier 3</td>
<td>Outcome owner ↔︎ Outcome owner on portfolio</td>
<td>Portfolio governance (at quarterly portfolio alignment)</td>
</tr>
</tbody>
</table>

# 10. Alphabetical index

A quick A-to-Z lookup. Section numbers in parentheses.

- Acceptance criteria → see Decision criteria (1)
- Architect → see Standard Owner or Integration Approver (1, 4)
- Artifact class (6)
- Attestation (6)
- Approver (4)
- Backlog grooming → see Continuous unit refinement (1)
- Brownfield standard (6)
- Brownfield work (8)
- Capability → see Long-running outcome (1)
- Capability-snapshot counterweight (8)
- Closure (gate) (5)
- Code-production boundary (7)
- Commit (gate) (5)
- Committed (state) (3)
- Continuous flow (7)
- Coordination obligation (2)
- Customer-time boundary (7)
- Daily standup → see Twice-weekly synchronous sync (1, 7)
- Decision criteria (2)
- Definition of Done → see Finishing standard (1, 6)
- Dimension (6)
- Epic → see Outcome (aggregator) (1)
- Exception (6)
- Exception (gate) (5)
- Experiment (2)
- Finishing standard (6)
- Flow Facilitator → see Scrum Master / RTE (evolved) (4)
- Greenfield standard (6)
- Greenfield work (8)
- Hybrid standard (6)
- Hypothesis (2)
- In progress (state) (3)
- In validation (state) (3)
- Inconclusive (state) (3)
- Inspect & Adapt → see Quarterly standards review (1)
- Integration Approver (4)
- Invalidated (state) (3)
- Long-running outcome (1)
- Maintenance unit (2)
- Monthly program coordination (7)
- Operator (4)
- Outcome (aggregator) (2)
- Outcome (record) (2)
- Outcome demo (7)
- Outcome review (7)
- Outcome-anchored alignment (7)
- Owner (4)
- Owner-set (8)
- PI Planning → see Monthly program coordination + Quarterly portfolio
  alignment (1)
- Per-validated-change learning capture (7)
- Portfolio alignment, quarterly (7)
- Producer (4)
- Producer-owner disconnect (8)
- Producer-set (8)
- Production-grade (6)
- Production-ready (gate) (5)
- Production-ready (state) (3)
- Product Manager → see Owner (1, 4)
- Product Owner → see Owner (1, 4)
- Proposed (state) (3)
- QA / Test team → see Approver (testing dimension) (1, 4)
- Quarterly portfolio alignment (7)
- Release Train Engineer (evolved) (4)
- Reviewer (4)
- Rollback condition (2)
- Scrum Master (evolved) (4)
- Security team → see Approver (security) (1, 4)
- Sprint → no equivalent (1)
- Sprint planning → see Continuous commit (1)
- Sprint retrospective → see Per-validated-change learning capture (1,
  7)
- Sprint review → see Outcome review (1, 7)
- Standard Owner (4)
- Standards registry (6)
- Story → see Validated change (1, 2)
- Story points → no direct equivalent (1)
- Strategic objective (2)
- Structural counterweight (8)
- System Demo → see Outcome demo (1, 7)
- Tier 1 / 2 / 3 dispute (9)
- Twice-weekly synchronous sync (7)
- User story → see Validated change (1, 2)
- Validated (state) (3)
- Validated change (2)
- Validation (gate) (5)
- Validation method (2)
- Validation window (2)
- Velocity → no direct equivalent (1)
- Withdrawn (state) (3)
