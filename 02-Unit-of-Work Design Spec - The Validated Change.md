# Executive summary

This document specifies a primary unit of work for AI-assisted product
development. It is the first of four follow-on artifacts proposed by the
position paper *AI-Assisted Velocity and the Limits of Modern
PDLC/SDLC*, and is intended to be developed in parallel with its
companion, the Production Standards design spec.

The recommended unit is **the validated change**: a unit consisting of a
claimed change to system or user behavior, a hypothesis about its
effect, a production-grade implementation that meets the applicable
production standard, a validation gate that produces evidence, and a
single named accountable owner. The validated change replaces the user
story as the primary unit of planning, tracking, and completion. It is
producer-agnostic, outcome-anchored, verifiable, compatible with both
greenfield and brownfield work, and explicitly designed to integrate
with a codified production standard rather than a team-level checklist.

The remainder of this document evaluates candidate units against a
consistent set of criteria, defends the recommendation, and specifies
the validated change operationally — its definition, attributes,
lifecycle, relationships, sizing, examples, and migration considerations
from current units. Open questions are flagged at the end.

# 1. Problem context

The position paper concluded that the user story, sized by engineering
effort against scarce production capacity, is no longer a coherent
primary unit when production capacity is no longer scarce and the
producer set is no longer restricted to engineers. Three specific
failures recur:

The user story is **producer-coupled**. Its standard form (“As a
\[role\] I want \[feature\] so that \[benefit\]”) is structured for a
developer to consume from a backlog. Non-engineer producers using AI
tooling do not need the framing and do not benefit from it.

The user story is **activity-anchored**. Its definition of done is “the
work described is built and accepted.” It does not natively encode
whether the change had the claimed effect on users or the system. In a
world where producing the change is cheap and the question of whether it
worked is the expensive part, this is the wrong anchor.

The user story is **standard-naive**. Its definition of done lives in
the team that owns it, and the team’s checklist is the standard. When a
non-engineer producer ships an artifact in a different role’s workflow,
the team’s checklist does not bind them. There is no organization-level
standard for what production-grade means.

A replacement unit must repair all three of these without losing what
worked: small enough to flow continuously, large enough to be
meaningful, decomposable, aggregable, learnable.

# 2. Evaluation criteria

Twelve criteria are used to evaluate candidate units. They are listed in
roughly decreasing weight.

1.  **Production-cost insensitive.** The unit stays coherent when the
    cost of producing the artifact approaches zero. Units sized by build
    effort fail this criterion.

2.  **Producer-agnostic.** The unit can be authored, owned, and
    progressed by any role with the necessary judgment, not only by
    developers.

3.  **Outcome-anchored.** The unit is defined by its intended effect on
    users or the system, not by the activity of producing an artifact.

4.  **Verifiable.** The unit has a defensible “done” condition tied to
    evidence, not to the producer’s claim that the work is complete.

5.  **Accountable.** The unit has a single named person accountable for
    the operational consequences, not just for the build.

6.  **Greenfield-and-brownfield compatible.** The unit works for both
    new standalone artifacts and changes inside long-lived systems with
    prior commitments.

7.  **Continuous-flow compatible.** The unit does not require sprint
    batching to function as a planning or tracking primitive.

8.  **Aggregatable upward.** Multiple units can be rolled up into
    higher-order business or strategic units (outcomes, objectives,
    themes).

9.  **Decomposable downward.** A unit too large to commit can be split
    into smaller units of the same kind, or into supporting units.

10. **Adoptable.** Existing teams can learn and use the unit without
    retraining that exceeds the value gained.

11. **Pathology-resistant.** The unit does not reproduce the
    dysfunctions of story-point estimation, velocity-as-throughput, or
    activity-counted “productivity.”

12. **Standard-coherent.** The unit has a natural place to reference the
    production standard its artifacts must meet.

# 3. Candidate units canvassed

Nine candidates are evaluated. Brief descriptions follow; the
comparative scoring is presented after.

**The user story** is the status quo and is included for completeness.
As discussed in Section 1, it fails the production-cost-insensitivity,
producer-agnostic, outcome-anchored, accountable, and standard-coherent
criteria.

**The experiment** is a unit borrowed from Lean Startup and
continuous-discovery practice. Its central property is that the output
is *learning*, not a shipped artifact. It scores well on production-cost
insensitivity, producer-agnostic, outcome-anchored, and
pathology-resistant, but poorly on accountability for operational
consequences and on aggregation upward into business outcomes — an
experiment is naturally a child of an outcome, not a peer of one.

**The outcome hypothesis** is a unit that pairs a desired customer or
business outcome with a hypothesis about how a specific change will
produce it. It scores well across most criteria but is awkward to
decompose downward — the hypothesis is naturally the size of the bet,
not the size of the change.

**The validated change** is the synthesis this document recommends. It
pairs a claimed change to system or user behavior with a hypothesis
about its effect, a production-grade implementation requirement, and a
validation gate. It is detailed in Section 5.

**The opportunity** (in the Teresa Torres / continuous-discovery sense)
is a problem-space unit: a discovered customer or business opportunity
to be addressed. It is essential at the discovery stage and is
recommended as a *parent* unit in the recommended model, but it is too
problem-space to serve as the primary planning and execution unit.

**The capability** (in the SAFe sense) is a long-lived, large-grained
unit naming a persistent capability of the system. It works at the
portfolio level but is too large and too persistent to serve as the
primary execution unit.

**The bet** (in the Shape Up sense) is a fixed-time, variable-scope
commitment. It scores well on accountability and pathology-resistance
but assumes time-boxing as the primary tradeoff lever, which is in
tension with continuous-flow planning.

**The job-to-be-done** is a user-goal unit independent of any specific
solution. It is a useful framing concept and a parent for opportunities,
but it is too solution-agnostic to serve as the primary execution unit.

**The thin vertical slice** is a small end-to-end deployable change. It
scores well on continuous flow and on adoptability, but it inherits the
user story’s activity-anchoring and producer-coupling: a thin vertical
slice is “built and deployed,” not “built, deployed, and validated.”

A summary of the canvass for the five most directly competitive
candidates is below. Criteria are rows; candidates are columns. The
validated change (column 4) is the recommended unit; its column scores
well on all twelve criteria and is the only one that does. The remaining
four candidates (capability, bet, JTBD, thin vertical slice) are not
tabulated because their narrative descriptions above already establish
that each fails one or more high-weight criteria categorically —
capability fails continuous-flow; bet fails continuous-flow and is hard
to adopt; JTBD fails outcome-anchoring and verifiability; thin vertical
slice replicates the user story’s producer-coupling and
activity-anchoring.

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 8%" />
<col style="width: 14%" />
<col style="width: 15%" />
<col style="width: 18%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr>
<th>Criterion</th>
<th>Story</th>
<th>Experiment</th>
<th>Outcome hyp.</th>
<th>Validated change</th>
<th>Opportunity</th>
</tr>
</thead>
<tbody>
<tr>
<td>Prod-cost insensitive</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Producer-agnostic</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Outcome-anchored</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Partial</td>
</tr>
<tr>
<td>Verifiable</td>
<td>Weak</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Hard</td>
</tr>
<tr>
<td>Accountable</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
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
</tr>
<tr>
<td>Continuous flow</td>
<td>Weak</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Aggregable upward</td>
<td>Yes</td>
<td>Hard</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Decomposable downward</td>
<td>Yes</td>
<td>Yes</td>
<td>Hard</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Adoptable</td>
<td>Easy</td>
<td>Medium</td>
<td>Medium</td>
<td>Medium</td>
<td>Medium</td>
</tr>
<tr>
<td>Pathology-resistant</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>DoD-coherent</td>
<td>Weak</td>
<td>Hard</td>
<td>Medium</td>
<td>Strong</td>
<td>No</td>
</tr>
</tbody>
</table>

# 4. Recommendation

The recommended primary unit is **the validated change.**

The recommendation rests on four observations from the canvass.

First, the validated change is the only candidate that scores well on
all twelve criteria. The closest alternatives — the outcome hypothesis
and the experiment — each fail one or two criteria the validated change
passes. The outcome hypothesis is hard to decompose downward; the
experiment is hard to aggregate upward and weak on operational
accountability.

Second, the validated change preserves what was useful about the user
story (small enough to flow, decomposable, learnable) while repairing
what was broken (producer coupling, activity anchoring, finishing
naivety). It is a successor, not a foreign import.

Third, the validated change has a natural place for the production
standard to bind. Every validated change references the production
standard its artifacts must meet at commit time, and the standard’s
automated checks and attestation requirements gate the transition from
in-progress to production-ready. This coupling makes the two artifacts
(this spec and the Production Standards spec) genuinely co-designed
rather than independent.

Fourth, the validated change handles the greenfield/brownfield
distinction the position paper insisted on. A greenfield validated
change is typically scoped as a complete user-facing capability with a
greenfield production standard; a brownfield validated change is
typically scoped as a change against an existing system surface with a
brownfield production standard that is stricter on integration and
coordination obligations. The same unit accommodates both modes by
parameterization, not by separate types.

The remainder of this document specifies the validated change
operationally.

# 5. The validated change, specified

## 5.1 Definition

A **validated change** is a unit of work consisting of:

1.  A **claimed change** to system or user behavior.
2.  A **hypothesis** about the change’s effect, including for whom, by
    when, and how the effect will be detected.
3.  A **production-grade implementation** of the change that meets the
    applicable production standard.
4.  A **validation gate** at which evidence is collected and a decision
    (validated, invalidated, inconclusive) is recorded.
5.  A **single named accountable owner** who carries the unit through
    its lifecycle and is responsible for the operational consequences of
    the shipped change.

The unit is producer-agnostic: the owner need not be the producer. The
owner may be a product manager, a designer, an engineer, an analyst, or
any role with sufficient authority and judgment to commit the unit and
accept its consequences. The producer may be a single person (with or
without AI assistance) or a team.

## 5.2 Attributes

Each validated change carries the following attributes.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Attribute</th>
<th style="text-align: left;">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">ID</td>
<td style="text-align: left;">Unique identifier.</td>
</tr>
<tr>
<td style="text-align: left;">Title</td>
<td style="text-align: left;">A statement of the claimed change in one
sentence.</td>
</tr>
<tr>
<td style="text-align: left;">Hypothesis</td>
<td style="text-align: left;">What is expected to happen, for whom, by
when, and how it will be detected.</td>
</tr>
<tr>
<td style="text-align: left;">Change type</td>
<td style="text-align: left;">Greenfield, brownfield, or hybrid.</td>
</tr>
<tr>
<td style="text-align: left;">Surface area</td>
<td style="text-align: left;">The systems, teams, and customer segments
touched by the change.</td>
</tr>
<tr>
<td style="text-align: left;">Owner</td>
<td style="text-align: left;">The single named accountable person.</td>
</tr>
<tr>
<td style="text-align: left;">Producer(s)</td>
<td style="text-align: left;">The person, role, team, or AI-assisted
producer responsible for production. May be different from owner.</td>
</tr>
<tr>
<td style="text-align: left;">Finishing-standard reference</td>
<td style="text-align: left;">The specific production standard (and
version) the implementation must meet, by reference to the standards
registry.</td>
</tr>
<tr>
<td style="text-align: left;">Coordination obligations</td>
<td style="text-align: left;">Other teams and stakeholders that must be
engaged before, during, or after the change.</td>
</tr>
<tr>
<td style="text-align: left;">Validation method</td>
<td style="text-align: left;">How evidence will be collected
(instrumentation, A/B test, qualitative research, telemetry analysis,
attested compliance check, etc.).</td>
</tr>
<tr>
<td style="text-align: left;">Validation window</td>
<td style="text-align: left;">The time period over which evidence will
be collected.</td>
</tr>
<tr>
<td style="text-align: left;">Decision criteria</td>
<td style="text-align: left;">The specific evidence that will trigger
validated, invalidated, or inconclusive.</td>
</tr>
<tr>
<td style="text-align: left;">Rollback condition</td>
<td style="text-align: left;">The specific evidence that will trigger an
immediate rollback.</td>
</tr>
<tr>
<td style="text-align: left;">Outcome</td>
<td style="text-align: left;">Filled at close: the actual evidence and
decision.</td>
</tr>
</tbody>
</table>

The hypothesis, decision criteria, and rollback condition are committed
*before* production begins. They are part of what makes the unit
verifiable rather than activity-anchored.

## 5.3 Lifecycle

A validated change progresses through a defined set of states.

**Proposed.** The claim and hypothesis exist; the unit is not yet
committed to. Discussion, refinement, and decomposition happen here.
Effort to produce the change should not yet be invested.

**Committed.** The unit has been accepted into the work flow. Owner is
assigned. Hypothesis, production standard, validation method, decision
criteria, and rollback condition are all set and are the contract for
the rest of the lifecycle.

**In progress.** Production work is underway. The producer (whoever they
are) is producing the implementation against the production standard.
The owner is accountable for the unit moving forward.

**Production-ready.** The implementation meets the production standard.
All gates the standard requires (automated checks, attestations,
security reviews where applicable) have passed. The change is ready to
be deployed or rolled out, but is not yet collecting validation
evidence.

**In validation.** The change is deployed (or rolled out, or otherwise
live) and the validation method is collecting evidence. The validation
window is running.

**Validated.** Evidence collected during the validation window meets the
decision criteria for confirming the hypothesis. The unit is closed
positive. The change remains in production; the outcome is recorded.

**Invalidated.** Evidence collected during the validation window meets
the decision criteria for disconfirming the hypothesis. The unit is
closed negative. The change is rolled back, modified, or kept with
explicit documentation of the disconfirmation, depending on the rollback
condition and the owner’s judgment. The outcome is recorded.

**Inconclusive.** Evidence collected during the validation window
neither confirms nor disconfirms the hypothesis. The unit is closed
ambiguous. A learning-capture step is mandatory: the owner records what
the inconclusive result implies and what would be needed to make a
future validated change of similar type more conclusive.

**Withdrawn.** The unit is abandoned before reaching production-ready.
Reasons are recorded. Withdrawal is a legitimate outcome; it is not a
failure of the unit, only a decision not to pursue.

A unit may be **rolled back** at any point after entering “in
validation” if the rollback condition is met. Rollback is not a separate
terminal state; it triggers a transition back to “in progress” (if the
owner intends to revise) or to “withdrawn” (if not).

## 5.4 Relationships

A validated change exists within a relationship graph of larger and
smaller units.

**Upward.** Validated changes aggregate into **outcomes**: higher-order
customer, business, or operational outcomes that the organization is
pursuing. An outcome is the natural parent of one or more validated
changes that are hypothesized to produce it. Outcomes themselves
aggregate into **strategic objectives** or **themes** at the portfolio
level. The aggregation is not arithmetic — outcomes are not the sum of
their validated changes — but is causal: validated changes are the bets
the organization is making about how to produce the outcome.

**Sideways.** Validated changes can have **coordination dependencies**
on other validated changes (and on other teams’ work). These are
explicit obligations recorded in the coordination-obligations attribute.
They are not parent-child relationships; they are peer-to-peer.

**Downward.** A validated change can be **decomposed** when it is too
large to commit credibly. Two decomposition patterns are supported:

- **Decomposition into smaller validated changes.** When a single
  hypothesis is too broad, it can be split into several narrower
  hypotheses, each its own validated change. The parent validated change
  becomes a *grouping* and is closed when its children are.
- **Decomposition into supporting experiments.** When a hypothesis is
  too uncertain to commit to building the full change, it can be
  preceded by one or more **experiments** — smaller units whose output
  is learning, not a shipped change. An experiment’s output informs the
  decision to commit, modify, or withdraw the parent validated change.
  Experiments are a sibling unit type, not a state of the validated
  change.

##  5.5 Sizing

The validated change is sized by **hypothesis scope**, not by build
effort. Specifically:

- The right size is the smallest unit that supports a credible
  hypothesis with a defensible validation window.
- A unit too large to fit a credible validation window — for example,
  “improve the entire checkout funnel” — should be decomposed into
  smaller validated changes with their own hypotheses.
- A unit so small that it cannot support any meaningful hypothesis — for
  example, “change a button color” — should either be merged with
  related changes into one larger validated change, or processed under a
  separate **maintenance unit** type (see Section 7, open questions).

Anti-patterns to avoid:

- **Sizing by AI-token consumption or developer-days.** This re-imports
  the production-cost coupling the unit is designed to remove.
- **Sizing by sprint fit.** The validated change is continuous-flow
  native; sprint fit is irrelevant.
- **Sizing by team capacity.** Capacity-based sizing prioritizes
  utilization over outcome.

##  5.6 Greenfield and brownfield handling

The validated change accommodates both modes by parameterization, not by
separate unit types.

**Greenfield validated changes** are typically scoped as a complete
user-facing capability or standalone application. Their
production-standard reference points to the applicable greenfield
standard (which is typically narrower because there is no existing
system to integrate with). Coordination obligations are typically light.
The change-type attribute is set to *greenfield*.

**Brownfield validated changes** are typically scoped as a change
against an existing system surface. Their production-standard reference
points to the applicable brownfield standard (which is typically
stricter on integration: existing tests must continue to pass,
observability must remain intact, latency budgets must hold, etc.).
Coordination obligations are typically explicit and non-trivial. The
change-type attribute is set to *brownfield*.

**Hybrid validated changes** include components of both — a new
standalone artifact that consumes existing services, for example. The
production-standard reference may point to multiple standards, and the
union of their requirements applies. The change-type attribute is set to
*hybrid*.

##  5.7 Definition-of-done hooks

The validated change defers most of “done” to the Production Standards
spec. Specifically:

- The transition from **in progress** to **production-ready** is gated
  by the production standard referenced at commit time. The standard’s
  automated checks must pass and any required attestations must be
  recorded. This is a hard gate, not a soft checklist.
- The transition from **in validation** to **validated / invalidated /
  inconclusive** is gated by the validation method and decision criteria
  committed at the start. Evidence must be produced; it is not enough to
  claim the change worked.
- The validated change cannot be marked done in the validated,
  invalidated, or inconclusive states without an outcome recorded. The
  outcome is the artifact that the unit’s value compounds into for
  future organizational learning.

The combination of finishing-standard-gated production and
evidence-gated validation is what distinguishes the validated change
from its predecessors. It is not enough to ship; it is not enough to
claim impact; both must be evidenced.

# 6. Examples

Two illustrative examples, one greenfield and one brownfield.

**Greenfield example.**

> **Title.** A standalone iOS event-check-in app for small organizers.
>
> **Hypothesis.** Within 60 days of launch, at least 50 distinct event
> organizers will have used the app to check in attendees at a real
> event of 25 or more attendees, and at least 70% of those organizers
> will use it for a second event.
>
> **Change type.** Greenfield. **Surface area.** New iOS application; no
> existing system integration. **Owner.** Product manager A.
> **Producer(s).** UX designer B, working with AI tooling.
> **Finishing-standard reference.** Mobile-greenfield-standard v3.2.
> **Coordination obligations.** Legal review of privacy disclosures;
> brand review of icon and naming. **Validation method.** App Store
> install telemetry, in-app event-creation telemetry, retention cohort
> analysis. **Validation window.** 60 days from public availability.
> **Decision criteria.** ≥50 distinct organizers + ≥70% second-event
> usage = validated. &lt;25 organizers OR &lt;40% second-event usage =
> invalidated. Anything in between = inconclusive. **Rollback
> condition.** Any P1 security disclosure or App Store removal during
> the validation window.

This is a single validated change. The producer is a non-engineer. The
production standard is referenced explicitly and is the gate for
production-ready. The hypothesis is committed before production begins.

**Brownfield example.**

> **Title.** Add a “recently viewed” carousel to the marketplace home
> screen.
>
> **Hypothesis.** A 5% or greater lift in session-to-purchase conversion
> rate among users who see the carousel, sustained over a 14-day
> measurement window, with no degradation in P95 home-screen latency or
> in any core marketplace KPI.
>
> **Change type.** Brownfield. **Surface area.** Marketplace home screen
> on iOS and Android; recommendation service; events pipeline.
> **Owner.** Product manager C. **Producer(s).** Engineering team D.
> **Finishing-standard reference.** Marketplace-feature-standard v5.1.
> **Coordination obligations.** Recommendations team (consumer of new
> event types); SRE team (latency budget review); experimentation team
> (A/B framework integration). **Validation method.** A/B test at 50/50
> with 10% holdout; primary metric = session-to-purchase conversion;
> guardrails = P95 home latency, top-line GMV, error rate. **Validation
> window.** 14 days at full ramp. **Decision criteria.** ≥5% lift on
> primary metric with 95% confidence and no statistically significant
> degradation on guardrails = validated. Negative or flat primary metric
> = invalidated. Positive but below 5% or with guardrail concerns =
> inconclusive. **Rollback condition.** Any guardrail crosses its
> threshold for two consecutive hours during ramp; any P1 incident
> attributed to the change.

This is also a single validated change, but the brownfield standard
binds it to existing system constraints, the coordination obligations
are non-trivial, and rollback is feature-flag-based and instantaneous.

# 7. Migration considerations

The transition from current units (user stories, epics, OKRs,
capabilities) to validated changes should be evolutionary, not a mass
relabeling.

**For new work.** New work should be authored as validated changes from
the point of adoption. The friction of writing the hypothesis and
decision criteria upfront is the practice the unit is designed to
instill; teams that skip this are not adopting the unit, only renaming
the old one.

**For existing user stories.** In-flight stories should be allowed to
complete in their current form. New stories that would have been opened
against existing epics should be re-stated as validated changes if the
epic represents an outcome (which is common but not universal).

**For existing OKRs.** Existing OKRs that are well-formed objectives can
become outcomes that aggregate validated changes. OKRs that conflate
objective and key results should be split: the objective becomes the
outcome; the key results become decision criteria on the validated
changes that produce it.

**For SAFe capabilities.** Capabilities are typically too large to be
validated changes. They are best treated as long-running outcomes that
aggregate streams of validated changes. The capability remains; what
changes is what its constituent units look like.

**For sprint-bound teams.** Teams operating in sprints can adopt
validated changes within the sprint cadence as a transitional state,
then evolve to continuous flow as comfort grows. The unit does not
require continuous flow to function; it only does not require sprints
either.

The expected adoption curve is months, not weeks, and the value comes
from the practice of writing hypotheses and decision criteria, not from
the relabeling.

# 8. Open questions

Five questions are flagged for the next iteration.

**Maintenance work.** Bug fixes, dependency upgrades, and routine
operational work do not naturally have hypotheses about user-visible
effect. A separate **maintenance unit** type is probably needed, with
its own lighter-weight definition (no hypothesis required, but the
production standard and accountable owner do apply). This document
leaves the maintenance unit unspecified pending a follow-up.

**Exploratory research.** Pure research with no committed change to ship
is a candidate for the **experiment** sibling unit type mentioned in
Section 5.4. The boundary between an experiment and a validated change
at the proposed state is fuzzy and should be tightened.

**Multi-quarter outcomes.** Outcomes that span a quarter or more
aggregate many validated changes over time. The aggregation pattern
(which changes are children of which outcomes, and how the outcome’s
status reflects the children’s outcomes) needs more specification,
particularly for portfolio-level reporting.

**Reporting and rollups.** This spec defines the unit but not the
reporting model. How validated changes roll up into outcome dashboards,
how outcomes roll up into portfolio views, and how the inconclusive
state is treated in aggregate metrics all need specification.

**Tooling.** Existing work-tracking tools (Jira, Linear, etc.) do not
natively model the hypothesis, decision criteria, validation window, or
outcome attributes. Adoption will require either custom field
configuration or a different tool. The tooling decision is out of scope
for this spec but is on the critical path for adoption.

These are the largest known unresolved questions. Smaller open questions
are noted inline above.


---

*Part of [ai-agile](https://github.com/itripn/ai-agile) by Ron Forrester. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
