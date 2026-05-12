# Executive summary

This document specifies a role taxonomy and a gating model for
AI-assisted product development. It is the third of four follow-on
artifacts from *AI-Assisted Velocity and the Limits of Modern PDLC/SDLC*
and depends on the Unit-of-Work design spec (which defines the validated
change) and the Production Standards design spec (which defines
production-grade standards) as foundational vocabulary.

The recommended model has three central roles — **Producer**, **Owner**,
and **Approver** — supported by three secondary roles — **Integration
Approver**, **Reviewer**, and **Operator** — and one cross-cutting
governance role from the Production Standards spec, the **Standard
Owner**. The producer set is deliberately wide: anyone with the means
and judgment to create an artifact may produce, including non-engineers
using AI tooling and AI agents working under human supervision. The
owner set is narrow: each validated change has exactly one named owner
accountable for operational consequences. The approver set is role-typed
(security approver, compliance approver, accessibility approver, etc.),
with named individuals filling each role on a defined-capacity basis.

The gating model defines five gates in the validated change lifecycle:
**commit**, **production-ready**, **validation**, **closure**, and
**exception**. Each gate has explicit authorization rules.
Production-ready and exception gates are the most consequential:
production-ready cannot be overridden by individual judgment (it is
automated and attested); exception gates require joint standard-owner
and exception-owner authorization with expiry. Disputes follow a tiered
escalation path that resolves most cases within the model rather than
escalating to leadership.

The remainder of this document specifies the model in detail, including
authorization patterns, approver capacity, the producer-owner disconnect
that AI-assisted production introduces, dispute resolution, examples,
migration considerations, and open questions.

# 1. Problem context

The position paper observed that current PDLC/SDLC roles assume the
developer is the only legitimate producer of working artifacts and that
the team is the natural unit of finishing discipline. AI-assisted
production breaks both assumptions. Producers now include any role with
judgment to use AI tooling — product managers, designers, analysts,
domain experts, and AI agents operating under human supervision.
Finishing discipline must travel with the artifact regardless of who or
where it was produced.

The role and gating model that follows resolves three specific problems.

The first is **authority without accountability.** When anyone can
produce a production-grade artifact, anyone can also produce a
production-grade problem. Without a named accountable person per change,
the organization absorbs the consequences silently and the producers
face no learning signal. The model resolves this with a
single-named-owner rule per validated change.

The second is **gating by role rather than by judgment.** Traditional
models gate by job title — only developers commit code, only QA approves
releases, only architects review designs. When the producer set widens,
role-based gating becomes either an arbitrary blocker (a designer cannot
commit production-grade code because they are not a developer, even
though their code meets the standard) or it dissolves entirely (anyone
can ship anything because there is no role-based gate). Both failure
modes are common; the model proposes gating by *standard satisfaction*
and *attestation*, not by role.

The third is **specialist judgment under producer-set expansion.** Some
judgments cannot be made by the producer regardless of how capable the
AI tooling is — regulatory attestation, security review, brand approval,
legal review. The model resolves this by making approvers first-class
roles with defined capacity, queueing, and authorization scope, and by
requiring engagement *before* commit rather than discovery at
production-ready.

# 2. Evaluation criteria

Ten criteria are used to evaluate candidate role and gating models.

1.  **Producer-set wide.** Anyone with means and judgment can produce;
    production is not gated by job title.
2.  **Accountable.** Each unit has exactly one named owner accountable
    for operational consequences.
3.  **Specialist judgment available.** Where specialist judgment is
    required (security, regulatory, brand, legal, accessibility), it is
    named, available, and binding within scope.
4.  **No bottleneck on a single role.** No single role becomes the
    universal critical path for normal work.
5.  **Regulator-compatible.** The model accommodates legal attestation
    requirements (SOX, HIPAA, PCI, GDPR, financial services oversight,
    etc.) without reshaping for each regulation.
6.  **Clear authority at each gate.** It is unambiguous who authorizes
    each transition; ambiguity is the most common source of process
    drift.
7.  **Disputes resolvable in-model.** Normal disputes resolve within the
    model’s escalation tiers; only abnormal cases reach leadership.
8.  **Adoptable from current state.** Existing roles map to new roles
    (or to functions) without requiring a clean-room reorg.
9.  **Producer-finisher disconnect handled.** AI-assisted production
    introduces a new failure mode — the producer who cannot transfer
    enough understanding for the owner to accept consequences. The model
    handles it explicitly.
10. **Greenfield + brownfield compatible.** The model accommodates both
    modes by parameterization.

# 3. Candidate models canvassed

Six candidate role and gating models are evaluated. Brief descriptions
follow; the comparative scoring is in Section 4.

**Status quo Agile (PO, dev team, Scrum Master).** The Product Owner
authors stories; the development team produces; QA validates; the Scrum
Master facilitates process. Non-developer producers are not native to
this model and accommodate as exceptions.

**SAFe role topology (RTE, Product Manager, Product Owner, Architects,
Scrum Masters, STE).** A larger and more specialized set of roles built
around the program-increment cadence. Specialist roles (architect,
security, etc.) are accommodated as program-level functions but are not
native gates on individual units of work.

**Producer-only model.** The producer of an artifact is also its owner
and its authorizer. No separate gating; trust the producer. Radical
simplification; fails accountability and specialist-judgment criteria.

**Producer/Owner split.** Anyone produces; a named owner authorizes the
unit through its lifecycle. Producer and owner can be the same person or
different. This is partial; it does not handle specialist judgment.

**Producer/Owner/Approver triad** (the recommended model). Builds on the
producer/owner split by adding role-typed approvers whose authorization
is required for specific dimensions of the production standard.

**Functional gate model.** All work routes through fixed functional
gates — every change goes through security review, accessibility review,
performance review, compliance review, etc. Heavy on specialist judgment
but creates universal bottlenecks and is incompatible with continuous
flow.

A summary of the canvass follows.

In the table below, *Scrum* is the status-quo Agile model; *SAFe* is the
SAFe role topology; *Prod-only* is the producer-only model; *P/O* is the
producer-owner split; *P/O/A* is the recommended producer/owner/approver
triad; *Func gate* is the functional gate model.

<table style="width:100%;">
<colgroup>
<col style="width: 32%" />
<col style="width: 9%" />
<col style="width: 8%" />
<col style="width: 13%" />
<col style="width: 8%" />
<col style="width: 11%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr>
<th>Criterion</th>
<th>Scrum</th>
<th>SAFe</th>
<th>Prod-only</th>
<th>P/O</th>
<th><strong>P/O/A</strong></th>
<th>Func gate</th>
</tr>
</thead>
<tbody>
<tr>
<td>Producer-set wide</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Accountable</td>
<td>Weak</td>
<td>Weak</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Weak</td>
</tr>
<tr>
<td>Specialist judgment</td>
<td>Weak</td>
<td>Yes</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>No single-role bottleneck</td>
<td>Yes</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>Regulator-compatible</td>
<td>Weak</td>
<td>Yes</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Clear authority per gate</td>
<td>Weak</td>
<td>Med</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Disputes in-model</td>
<td>Weak</td>
<td>Med</td>
<td>N/A</td>
<td>Weak</td>
<td>Yes</td>
<td>Weak</td>
</tr>
<tr>
<td>Adoptable</td>
<td>Easy</td>
<td>Med</td>
<td>Easy</td>
<td>Easy</td>
<td>Medium</td>
<td>Hard</td>
</tr>
<tr>
<td>Producer-finisher handled</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>Part.</td>
<td>Yes</td>
<td>Partial</td>
</tr>
<tr>
<td>GF + BF compatible</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
</tbody>
</table>

# 4. Recommendation

The recommended model is the **Producer/Owner/Approver triad** with
**Integration Approver**, **Reviewer**, and **Operator** as supporting
roles and **Standard Owner** as cross-cutting governance.

The recommendation rests on three observations.

First, only the triad model scores well on all ten criteria. The
producer-only and producer/owner models fail specialist judgment and
regulator compatibility; the status quo and SAFe models fail
producer-set width; the functional-gate model creates universal
bottlenecks. The triad covers the requirement set without introducing
new bottlenecks because attestation is dimension-typed and parallel
rather than serial through a single function.

Second, the triad is co-designed with the validated change and the
production standard. The producer creates the artifact; the owner takes
accountability for the validated change; the approvers certify the
dimensions of the production standard that cannot be automated. Each
role has a clear contract with the units it touches.

Third, the triad handles the producer-owner disconnect explicitly. When
a non-engineer or AI agent produces an artifact and a different person
is the owner, the model requires that the producer transfer enough
understanding for the owner to accept operational consequences. This is
operationalized through the production standard’s documentation
requirements and through the owner’s authority to refuse commit if the
transfer is insufficient.

# 5. The role taxonomy

Seven roles are specified. Three are central; three are supporting; one
is cross-cutting governance.

## 5.1 Central roles

**Producer.** Anyone — product manager, designer, engineer, analyst,
domain expert, AI agent operating under human supervision — who creates
an artifact. The producer set is deliberately wide and is not gated by
job title. A producer is a per-unit role: the same person may be a
producer on one unit and not on another. AI agents may be producers; the
human supervising the agent shares responsibility for the agent’s output
as if they had produced it personally.

**Owner** (also: **Validated Change Owner** or **Accountable Owner**
when disambiguation is needed). A single named person per validated
change, accountable for the unit’s lifecycle and for the operational
consequences of the shipped change. The owner is a per-unit role and a
job-title-agnostic function: in practice, owners are often product
managers, engineering leads, or designers, but any person with
sufficient organizational authority and judgment may own a unit. The
owner is not necessarily the producer; the owner is not necessarily the
operator post-rollout. The owner is necessarily named and singular.
Note: this is distinct from the Scrum Product Owner role, though the two
often overlap in practice — Product Owners frequently become Validated
Change Owners. Distinct also from the **Outcome Owner** at the
aggregator level (a similar pattern of named accountability, but for
outcomes rather than units of work).

**Approver.** A role-typed (not person-typed) certifier of one or more
dimensions of the production standard that cannot be fully automated.
Approvers are filled by named individuals on a defined-capacity basis.
Examples by dimension:

- **Security approver** — security engineer credentialed to attest to
  threat-model adequacy.
- **Compliance approver** — compliance officer credentialed for the
  relevant regulatory framework.
- **Accessibility approver** — accessibility specialist credentialed for
  the applicable WCAG level or platform standard.
- **Legal approver** — counsel for terms, privacy, and regulatory legal
  review.
- **Brand approver** — brand owner for naming, voice, visual identity.
- **Privacy approver** — DPO or privacy officer for data-handling
  judgment.

The list is illustrative; each production standard names the approver
roles it requires for its dimensions.

## 5.2 Supporting roles

**Integration Approver.** For brownfield validated changes, a role-typed
certifier that the integration with existing system constraints is
correct. Examples include platform integration approvers (for shared
infrastructure), data integration approvers (for shared data flows), and
API integration approvers (for shared contracts). Integration Approvers
often overlap with approvers for the same dimension; the distinction is
that approvers certify against a written standard, while integration
approvers certify against existing system reality, which is often less
documented.

**Reviewer.** Anyone the owner invites for judgment input on a validated
change. Reviewer feedback is recorded but is not authorizing. Reviewers
are common in design, code, and architecture review settings. Their role
is to add quality to the owner’s decisions, not to gate the unit.

**Operator.** The named person accountable for ongoing operation of the
artifact post-rollout: incident response, performance monitoring,
dependency management, deprecation. The operator is often the owner, but
ownership may transfer at validation closure to a designated operator
(for example, a feature shipped by a product team may transfer
operational ownership to a platform team that owns its long-term
maintenance). The transfer is explicit and is part of the validated
change’s outcome record.

## 5.3 Cross-cutting role

**Standard Owner.** Defined in the Production Standards design spec. The
standard owner is responsible for the evolution of one or more
production standards and is the authority for exceptions to those
standards. Standard owners are referenced here for completeness; their
full specification lives in the Production Standards document.

# 6. The gating model

The validated change lifecycle has five gates. Each gate has explicit
authorization rules and a defined transition contract.

## 6.1 Commit gate (Proposed → Committed)

**Conditions to pass.**

- Owner is named.
- Hypothesis, validation method, decision criteria, and rollback
  condition are stated.
- Finishing standard (and version) is referenced.
- All approvers required by the production standard have been notified
  and have acknowledged engagement (acknowledgment of availability; not
  approval).
- All coordination obligations have been identified and the relevant
  counterparties notified.

**Authorization.** Owner. The owner takes the commitment.

**Notes.** The commit gate is the most consequential planning act in the
model. After commit, the hypothesis and decision criteria are the
contract for the rest of the lifecycle. Changes to either after commit
are themselves a small process: documented, justified, and acknowledged
by the affected approvers.

## 6.2 Production-ready gate (In progress → Production-ready)

**Conditions to pass.**

- All automated checks defined by the production standard pass.
- All required attestations defined by the production standard are
  recorded.
- All coordination obligations are met (counterparties have confirmed
  integration as needed).

**Authorization.** Automatic when conditions met; cannot be overridden
by individual judgment, including the owner’s. If a condition cannot be
met as the standard requires, an exception (Section 7) is the only path
forward.

**Notes.** The production-ready gate is the primary place where the
trust between the model and the organization lives. The discipline of
not allowing override is what makes the model trustworthy at scale; an
organization that routinely overrides production-ready transitions is
not running this model.

## 6.3 Validation gate (Production-ready → In validation)

**Conditions to pass.**

- Rollout method specified by the production standard is initiated
  (canary, ramp, A/B, staged).
- Instrumentation specified by the validation method is confirmed live
  and emitting.

**Authorization.** Owner, with rollout-method-specific automation. For
example, an A/B test enrollment is initiated by the owner but executed
by the experimentation platform; a staged rollout is initiated by the
owner but executed by the deployment platform.

## 6.4 Closure gate (In validation → Validated/Invalidated/Inconclusive)

**Conditions to pass.**

- Validation window has elapsed (or rollback was triggered earlier — see
  Section 7).
- Evidence has been collected per the validation method.
- Decision has been reached against the committed criteria.
- For inconclusive: learning capture has been recorded.

**Authorization.** Owner. The owner records the outcome and closes the
unit. For invalidated outcomes, the owner additionally records whether
the change is rolled back, modified, or kept with explicit documentation
of the disconfirmation.

## 6.5 Exception gate (any state)

**Conditions to pass.**

- Documented rationale for the exception.
- Named exception owner accountable for resolution.
- Expiry date by which the exception must be resolved or renewed.

**Authorization.** Standard owner of the standard being excepted,
jointly with the exception owner. Two named authorities; not one.

**Notes.** Exceptions are first-class; they are not a backdoor. An
exception is a public, time-bound deviation that is visible in the
standards registry and on the affected validated change. Repeated
exceptions of the same type indicate that the standard needs to evolve.

# 7. Authorization patterns

Six authorization patterns recur across the model and are documented
here for reference.

**Producer authorization is implicit.** A producer authorizes their own
work by producing it. There is no producer-specific gate.

**Owner authorization is the central authority for the unit.** The owner
authorizes commit, validation, and closure. The owner does not authorize
production-ready (which is automatic when conditions are met) or
exceptions (which require joint authorization with a standard owner).

**Approver authorization is gate-specific and binding within scope.** An
approver authorizes a single dimension of the production standard for a
single unit. Their authorization is binding within their dimension; they
do not authorize the unit as a whole.

**Standard owner authorization governs standards and exceptions.**
Standard owners authorize changes to standards (per the Production
Standards spec) and exceptions to standards (per Section 6.5).

**Joint authorization for exceptions.** Exceptions require both standard
owner and exception owner authorization. This is the only place in the
model where two named authorities are required for a single transition.

**Rollback authorization is a fast path.** The owner may trigger
rollback at any time after the validation gate without further
authorization. The rollback condition specified at commit is the basis
for the action; if the condition is met, the owner is expected to act.
Rollback returns the unit to in-progress (if the owner intends to
revise) or to withdrawn (if not).

# 8. Approver capacity and queueing

Named approver roles introduce a real risk: if every brownfield
validated change requires security attestation and the security team’s
attestation capacity is small, the security team becomes a bottleneck.
The model handles this with three mechanisms.

**Published capacity.** Each approver role publishes its current
capacity: typical response time, current queue length, current
concurrent load. Producers and owners can see this when planning.

**Visible queue.** When attestation is requested, the request enters a
visible queue scoped to the approver role. The queue is ordered by
parent outcome priority; ties are broken by request time.

**Capacity sizing as an organizational decision.** The model does not
specify how much approver capacity an organization should fund. It only
specifies that the capacity exists, is visible, and is queue-managed.
Capacity sizing is an organizational design decision that the cadence
spec (the fourth artifact) addresses at the portfolio level.

When an approver role’s queue depth exceeds a defined threshold for a
sustained period, an escalation is triggered to the standard owner of
the standards that role attests to. The standard owner has three
options: increase approver capacity (organizational change), narrow the
standard (so fewer units require attestation), or accept elevated cycle
time (a deliberate trade-off, recorded).

# 9. The producer-owner disconnect

AI-assisted production introduces a failure mode that traditional roles
did not have to handle: the producer can create a working artifact that
the owner does not understand well enough to accept operational
consequences for. This is the **producer-owner disconnect.**

The model handles it through three mechanisms.

**Documentation as a finishing requirement.** The production standard
requires operational documentation sufficient for someone other than the
producer to operate the artifact. This is a hard requirement at the
production-ready gate. AI tooling is increasingly capable of producing
this documentation alongside the artifact; producers are responsible for
ensuring it is produced and accurate.

**Owner refusal is a legitimate action.** If the owner does not
understand the artifact well enough to accept consequences, the owner
refuses to commit (or refuses to authorize the validation gate). This is
not a failure of the producer; it is a normal use of authority. The unit
returns to the producer for additional documentation, simplification, or
transfer.

**Producer-on-call.** For complex artifacts where ownership transfer is
partial, the model supports a producer-on-call arrangement: the producer
remains available for a defined period (typically through the validation
window) to support the owner if questions arise. The arrangement is
recorded on the validated change.

The combined effect is to make production by non-traditional producers
safe rather than risky. The producer-set widens; the owner-set does not
lose accountability; the artifact is operable by people other than the
producer.

# 10. Dispute resolution

Disputes within the model resolve through three escalation tiers. Most
disputes resolve in tier 1; only abnormal cases reach tier 3.

**Tier 1: between owner and approver within a single domain.** Resolved
by the standard owner of the relevant standard. Example: the owner
believes the security approver’s requirements exceed the standard; the
security standard’s owner adjudicates whether the approver’s
interpretation is correct or whether the standard itself needs
clarification.

**Tier 2: between owners on coordination obligations.** Resolved by the
outcome owner whose outcome both validated changes are children of.
Example: two teams’ validated changes both want to ship in the same
release window with conflicting feature-flag dependencies; the outcome
owner adjudicates priority and sequencing.

**Tier 3: between outcome owners on portfolio priorities.** Resolved by
portfolio governance, which is defined in the cadence spec (the fourth
artifact). This is the leadership-attention path; well-functioning
organizations should see only a small number of tier-3 disputes per
cycle.

All dispute outcomes are recorded with rationale. Pattern detection
drives standard evolution: if the same tier-1 dispute recurs, the
standard owner is expected to evolve the standard to remove the
ambiguity that produced the disputes.

# 11. Examples

Two illustrative examples, parallel to the ones in the unit-of-work
spec.

**Greenfield example: standalone iOS event-check-in app.**

- **Producer.** UX designer B (with AI assistance).
- **Owner.** Product manager A.
- **Approvers.** Legal approver (privacy policy review), brand approver
  (icon and naming), accessibility approver (automated scan results
  review).
- **Integration Approver.** None (greenfield).
- **Reviewers.** Two designers from peer teams; one engineer for
  spot-check of the AI-generated code.
- **Operator.** UX designer B remains operator for first 60 days;
  transfers to the small-tools operations team thereafter.

The owner (PM A) authorizes commit after approvers acknowledge
engagement. Production-ready is automatic when the
mobile-greenfield-standard’s automated checks pass and the three
attestations are recorded. Validation gate is the App Store release.
Closure happens at 60 days against the committed decision criteria.

**Brownfield example: marketplace home-screen “recently viewed”
carousel.**

- **Producer.** Engineering team D.
- **Owner.** Product manager C.
- **Approvers.** Security approver (data-flow review), compliance
  approver (PII handling review), accessibility approver (component-use
  check).
- **Integration Approvers.** Platform integration approver (shared
  infrastructure), recommendations integration approver (consumer of new
  event types), experimentation integration approver (A/B framework
  integration).
- **Reviewers.** SRE team (latency budget review, non-blocking
  advisory).
- **Operator.** Engineering team D’s on-call rotation.

The owner (PM C) authorizes commit after approvers and integration
approvers acknowledge engagement. Production-ready requires the
marketplace-feature-standard’s automated checks plus three attestations
and three integration approver confirmations. Validation gate is A/B
test enrollment. Closure happens at 14 days against the committed
decision criteria.

# 12. Migration considerations

The transition from current role models to this one should be
evolutionary and function-first rather than title-first.

**Existing PO/Scrum-Master/dev-team teams.** Product owners frequently
become Validated Change Owners (or Outcome Owners for those operating at
the aggregator level); Scrum Masters keep their title and take on the
evolved process-facilitation responsibilities specified in the cadence
spec (queue health, coordination, learning synthesis); developers
frequently become producers and, for some, approvers or integration
approvers in their domain.

**Existing SAFe teams.** Release Train Engineers frequently become
coordination facilitators at the outcome or portfolio level (cadence
spec); architects frequently become integration approvers or standard
owners; product managers frequently become outcome owners; product
owners frequently become validated-change owners.

**Existing functional teams (security, compliance, accessibility, legal,
brand).** These become the approver roles. The function-team-as-approver
is the natural mapping; what changes is the *model of engagement* — from
“submit a request and wait” to “named approver engaged at commit, on a
published capacity.” This is a meaningful change and is one of the
larger adoption challenges.

**Resist 1:1 title mapping.** Job titles are not the unit of change. The
unit of change is the function someone performs on a given validated
change. Many people will perform multiple roles across multiple units.
Title changes are an organizational convenience, not a model
requirement.

**Adoption sequencing.** A reasonable sequence: introduce the validated
change unit first (so units exist that need owners); introduce ownership
next (so the named-owner discipline takes hold); introduce attestation
third (which requires standards to exist and approver capacity to be
funded); introduce integration approvers last (these emerge naturally
once attestation is established).

# 13. Open questions

Five questions are flagged for the next iteration.

**Process facilitation.** This spec defers the process-facilitation
function to the cadence spec, which keeps the existing Scrum Master and
Release Train Engineer titles and lets their responsibilities evolve to
include queue health, coordination, escalation, and learning synthesis.
This is intentional: introducing a new title for a role that already
exists telegraphs disruption without delivering conceptual lift.

**AI agent supervision.** The model treats AI agents as producers under
human supervision. The supervision relationship needs
operationalization: who is the supervising human for an agent acting on
an analyst’s behalf, what is their authority over the agent’s outputs,
and how does responsibility allocate when an agent’s output causes
operational harm. This is a near-term question.

**Approver capacity funding.** The model assumes approver capacity is
funded; reality is that approver roles are typically funded out of
cost-center budgets that are not easily flexed. The funding model needs
treatment, possibly via a chargeback or service-level approach.

**Multi-approver coordination for complex units.** Some validated
changes touch many dimensions and require many approver engagements. The
coordination of multi-approver reviews (parallel vs sequential,
dependencies between dimensions) is unspecified.

**Cross-organizational attestation.** When a validated change crosses
organizational boundaries (a partner team’s standard, a vendor-provided
service), the approver chain extends beyond the organization. The model
is silent on this case.

These are the largest known unresolved questions. Smaller questions are
noted inline above.
