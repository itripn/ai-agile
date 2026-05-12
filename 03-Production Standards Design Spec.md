# Executive summary

This document specifies a production standards model for AI-assisted
product development. It is the second of four follow-on artifacts
proposed by the position paper AI-Assisted Velocity and the Limits of
Modern PDLC/SDLC and is the direct companion to the Unit-of-Work design
spec. The two are co-designed: the validated change references a
production standard, and a production standard binds the validated
change’s transition to production-ready. (The practice of operating
production standards organization-wide is sometimes called finishing
discipline; the two terms refer to the same thing in this corpus.)

The recommended model has three central properties. First, production
standards are organization-owned, not team-owned: the standard travels
with the artifact regardless of who produced it or which team it was
produced inside. Second, standards are artifact-class-typed: different
artifact classes (mobile app, marketplace feature, internal tool,
regulated workflow, library, etc.) have different standards, and each is
named, versioned, and owned. Third, standards are enforceable
independent of producer role: where automation can enforce, it does;
where attestation is required, the approvers are named and the
attestation is part of the standard.

The remainder of this document specifies the principles, the
production-grade dimensions, the producer-agnostic enforcement model,
the governance model, the greenfield-and-brownfield treatment, the hooks
to the unit-of-work spec, and example standards for two artifact
classes. Open questions are flagged at the end.

# 1. Problem context

The position paper concluded that finishing discipline scales as
production cheapens, not the other way around. When a single
non-engineer with AI assistance can produce, integrate, and ship a
production-grade artifact in days, the question of what “done” means
intensifies. The traditional model — definition-of-done as a team-owned
checklist enforced through team-owned ceremonies — fails in three ways.

It is producer-coupled. The team’s checklist binds the team’s
developers. It does not bind a UX designer producing in their own
workflow, an analyst producing in theirs, or an AI tool producing
autonomously under any role’s supervision. Production-grade artifacts
can now arrive from anywhere; the standard cannot live only inside one
producer’s habitual workflow.

It is folkloric, not codified. Most team definitions of done are tribal
knowledge maintained by the team’s senior members. They survive turnover
badly and they are not legible to producers outside the team. When the
producer set widens, folkloric standards stop functioning.

It is uniform within a team and varied across teams. The same artifact
class — say, a customer-facing mobile feature — may have meaningfully
different production standards in different teams. This was tolerable
when teams were narrow and stable; it is not tolerable when
production-grade artifacts cross team boundaries routinely.

A replacement model must solve all three: producer-agnostic, codified,
and consistent within an artifact class regardless of which team or
producer ships the artifact.

# 2. Principles

Six principles guide the model.

1.  **The standard binds the artifact, not the producer.** Whoever
    produces the artifact is responsible for meeting the standard. The
    standard does not change based on the producer’s role. AI tooling is
    co-designed to help producers meet the standard, not to lower the
    standard.

2.  **Standards are class-typed.** Artifact classes (mobile app,
    marketplace feature, internal tool, library, regulated workflow,
    batch job, customer email, etc.) each have their own standard. The
    standards differ because the production-grade requirements differ —
    a mobile app standard is not an internal-tool standard.

3.  **Standards are codified.** They live in writing in a single
    registry, with named owners and explicit versions. They are not
    tribal knowledge. They are versioned because they evolve, and the
    version applicable to a given validated change is the version
    current at commit time.

4.  **Enforcement is automated where possible, attested where not.**
    Automated checks (CI, security scans, accessibility scans,
    performance budgets) gate transitions wherever they can. Where the
    requirement cannot be automated — regulatory attestation, legal
    review, brand approval — the requirement is itself part of the
    standard, with named approvers and explicit response-time
    expectations.

5.  **Exceptions are first-class, time-bound, and rare.** Exceptions to
    a standard exist; they are not bugs. They are explicit, documented,
    owned, and have an expiry date by which they must be either resolved
    or renewed. An organization with no exceptions is hiding them; an
    organization with many is failing to evolve standards or producers.

6.  **Standards evolve with capability and with experience.** As AI
    tooling improves, the cost of meeting parts of the standard falls;
    as production runs reveal new failure modes, the standard
    incorporates them. A defined change process keeps evolution
    principled rather than ad hoc.

# 3. The dimensions of production-grade

Each production standard specifies, for its artifact class, requirements
across a defined set of dimensions. The dimensions below are the
proposed canonical set; not every dimension applies to every artifact
class, but each dimension is considered for each class and either
specified or explicitly marked not applicable.

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 81%" />
</colgroup>
<thead>
<tr>
<th>Dimension</th>
<th>What the standard specifies</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tested</td>
<td>Required test types and coverage targets at each level (unit,
integration, contract, end-to-end).</td>
</tr>
<tr>
<td>Observable</td>
<td>Required metrics, logs, traces, and dashboards needed to detect
problems and measure outcome.</td>
</tr>
<tr>
<td>Accessible</td>
<td>Required accessibility standard (WCAG level, platform-specific
equivalents) and verification method.</td>
</tr>
<tr>
<td>Performant</td>
<td>Required performance budgets (latency P50/P95/P99, throughput,
resource consumption) and verification method.</td>
</tr>
<tr>
<td>Secure</td>
<td>Required security baseline: authentication, authorization, secrets
handling, data protection, threat model where applicable.</td>
</tr>
<tr>
<td>Compliant</td>
<td>Required regulatory and policy compliance (PCI, HIPAA, SOX, GDPR,
accessibility law, financial-services frameworks, internal policy).</td>
</tr>
<tr>
<td>Instrumented</td>
<td>Required emission of the data needed for the parent validated
change’s validation method.</td>
</tr>
<tr>
<td>Rolled out safely</td>
<td>Required rollout method (canary, ramp, A/B, staged) and rollback
path.</td>
</tr>
<tr>
<td>Owned</td>
<td>Required named accountable owner for operational consequences.</td>
</tr>
<tr>
<td>Documented</td>
<td>Required operational documentation: how to operate, how to debug,
how to roll back, how to escalate.</td>
</tr>
</tbody>
</table>

For each dimension, the standard specifies (a) the requirement, (b) how
it is verified, (c) who attests if attestation is required, and (d) the
disposition for non-applicability if it does not apply to the class.

# 4. Producer-agnostic enforcement

The model’s central property is that the standard binds the artifact
regardless of producer. Three enforcement modes operate together.

**Automated checks.** Wherever a requirement can be expressed as an
automated test (CI gates, security scans, accessibility scans,
performance regression checks, contract tests, dependency vulnerability
scans), it is. Automated checks run in a producer-independent pipeline;
the producer cannot bypass them by being in a non-engineering workflow.
This is the strongest enforcement mode and is preferred wherever
possible. AI tooling is increasingly capable of producing artifacts that
pass these checks on first attempt; the model assumes this trajectory
continues and is co-designed for it.

**Required attestations.** Where a requirement cannot be automated, the
standard specifies a **named approver role** (not a person — the role
outlives any individual). The approver is responsible for the
production-grade judgment that the requirement is met. Examples:
regulatory attestation by compliance officers, security review by
security engineers, legal review by counsel, brand review by brand
owners. The attestation is a formal artifact — recorded, timestamped,
attached to the validated change — not a handshake.

**Required engagement before commit.** For artifact classes with
non-trivial coordination requirements (most brownfield work, all
regulated work), the standard requires that the relevant approvers and
coordination partners be engaged *before* the validated change moves
from proposed to committed. This prevents the common failure mode in
which a producer ships a near-complete artifact only to discover it
cannot pass attestation as built. The engagement is itself part of the
unit’s coordination obligations.

A producer who cannot personally satisfy a dimension (a UX designer who
cannot personally attest to SOC 2 compliance, for example) does not
lower the standard; they engage the named approver and complete the
attestation through the standard process. This is a feature of the
model, not a friction point: it makes producer-set expansion safe rather
than disruptive.

# 5. Governance

The model requires sustained governance to remain useful.

**Standards registry.** A single canonical registry catalogs all current
standards by artifact class. Each entry includes the standard’s name,
version, owner role, approver roles by dimension, history of changes,
and current exceptions. The registry is the source of truth; standards
referenced from a validated change resolve to an exact version in the
registry.

**Standard owners.** Each standard has a single named owner role (e.g.,
“Mobile Platform Standard Owner,” “Marketplace Feature Standard Owner”).
The owner is responsible for the standard’s evolution, exceptions, and
operational integrity. Owners change over time; the role persists.

**Change process.** Changes to a standard go through a defined change
process: an open RFC posted to the standards registry, a comment window
of defined length, and the owner’s decision. Substantive changes require
the owner to consult relevant approvers and a sample of recent producers
operating against the standard. Trivial changes (typo, clarification)
follow a lighter process.

**Versioning.** Standards are versioned semantically: major version
bumps for changes that increase requirements; minor for clarifications
and additions that do not increase requirements; patch for typos and
editorial fixes. A validated change committed against version 5.1 is
held to version 5.1 throughout its lifecycle, even if 5.2 ships during
production. This provides stability for in-flight work while allowing
evolution.

**Exceptions.** Exceptions are recorded against a specific standard and
a specific validated change. Each exception has a stated reason, a named
owner, and an expiry date. At expiry, the exception is either resolved
(the validated change now meets the standard) or renewed (with
rationale). An exception that has been renewed three times is escalated
to the standard owner for consideration of standard evolution.
Exceptions are visible in the registry and in any validated-change view
that references the standard.

**Standard cadence.** Each standard is reviewed by its owner at least
quarterly. Reviews consider: changes in producer practice (especially
what AI tooling now reliably produces); changes in operational reality
(incident analysis, customer impact); changes in regulatory landscape;
cumulative exception patterns. Reviews are recorded; the absence of a
recent review is itself a warning signal.

# 6. Greenfield and brownfield treatment

Many artifact classes have both a greenfield variant and a brownfield
variant of the standard, because the requirements differ.

**Greenfield standards** are typically narrower because there is no
existing system to integrate against. A greenfield mobile app standard,
for example, does not require backwards compatibility with an existing
release train, integration with an existing observability stack, or
coordination with platform teams whose contracts pre-exist. It does
require all the production-grade dimensions for the new artifact in
isolation.

**Brownfield standards** are typically stricter, but the additional
strictness is concentrated in the integration dimensions: existing tests
must continue to pass, existing performance budgets must hold, existing
observability must remain coherent, and existing operational practices
must be respected. The producer must engage the relevant existing-system
owners as part of coordination obligations.

**Hybrid standards** apply when an artifact has both new and integrating
components — a new standalone application that consumes an existing
service, for example. The hybrid standard is the union of the relevant
requirements; coordination obligations cover both modes.

Whether a given artifact class needs separate greenfield and brownfield
variants is an artifact-class judgment. Some classes (internal scratch
tools) may not need both; some (customer-facing features in regulated
domains) need both and benefit from explicit treatment.

# 7. Hooks to the unit-of-work spec

The two specs are co-designed; this section enumerates the binding
points.

**At commit time** (Proposed → Committed in the validated change
lifecycle), the validated change references a specific production
standard and version from the registry. The reference is part of the
unit’s attributes and is fixed at commit. The standard’s coordination
requirements are added to the unit’s coordination obligations. The
standard’s required approvers are notified.

**At production-ready transition** (In progress → Production-ready), the
standard’s automated checks must pass and the standard’s required
attestations must be recorded. This is a hard gate enforced by tooling,
not a soft checklist confirmed by the producer. The validated change
cannot transition to production-ready without the standard’s gates
green.

**At validation gate** (In validation →
Validated/Invalidated/Inconclusive), the standard’s instrumentation
requirements must have produced the data the validation method requires.
A validated change cannot close on evidence the standard’s
instrumentation did not enable.

**At rollback** (any time after In validation), the standard’s required
rollback path is exercised. The rollback path is part of the standard,
not part of the unit’s bespoke planning.

**For exceptions**, exceptions to the standard are recorded against the
validated change in the standards registry. The exception is visible in
the unit’s attributes. The exception’s expiry date is a tracking
obligation on the unit’s owner.

The combined effect is that the validated change becomes the *carrier*
of the production standard’s requirements through the unit’s lifecycle,
and the production standard becomes the *vocabulary* in which the
validated change’s production-readiness is expressed.

# 8. Example standards

Two illustrative examples, one greenfield mobile app and one brownfield
marketplace feature.

## 8.1 Mobile-greenfield-standard v3.2 (illustrative)

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 48%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr>
<th>Dimension</th>
<th>Requirement</th>
<th>Verification</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tested</td>
<td>Unit-test coverage ≥ 70% on business logic; UI smoke tests for
primary flows; one full happy-path E2E.</td>
<td>CI; cannot transition to production-ready without green.</td>
</tr>
<tr>
<td>Observable</td>
<td>Crash reporting integrated; minimum metric set (DAU, session length,
primary flow completion); dashboard exists.</td>
<td>Automated detection of crash-reporting integration; dashboard
registered in catalog.</td>
</tr>
<tr>
<td>Accessible</td>
<td>WCAG 2.1 AA for in-app text and controls; platform-specific
accessibility checks (iOS Accessibility Inspector, Android Accessibility
Scanner) clean.</td>
<td>Automated scan in CI.</td>
</tr>
<tr>
<td>Performant</td>
<td>App cold-start under 3.0 s on reference low-end device; primary flow
under 1.5 s P95.</td>
<td>Automated perf test in CI.</td>
</tr>
<tr>
<td>Secure</td>
<td>No hardcoded secrets; certificate pinning for backend calls; OWASP
MASVS L1 baseline.</td>
<td>Static analysis in CI; manual security review only for auth-handling
apps.</td>
</tr>
<tr>
<td>Compliant</td>
<td>App Store / Play Store policy compliance; ATT disclosures present;
privacy policy linked; age rating accurate.</td>
<td>Manual checklist; legal review of privacy policy by counsel
approver.</td>
</tr>
<tr>
<td>Instrumented</td>
<td>Events specified by parent validated change’s validation method are
emitted and visible in catalog.</td>
<td>Automated event-catalog check.</td>
</tr>
<tr>
<td>Rolled out safely</td>
<td>Phased rollout via App Store / Play Store; rollback by store
rollback or version pinning.</td>
<td>Documented in operational runbook.</td>
</tr>
<tr>
<td>Owned</td>
<td>Named owner recorded in app metadata.</td>
<td>Manual; checked at production-ready transition.</td>
</tr>
<tr>
<td>Documented</td>
<td>Operational runbook in repo; covers crash response, rollback,
escalation.</td>
<td>Manual; checked at production-ready transition.</td>
</tr>
</tbody>
</table>

## 8.2 Marketplace-feature-standard v5.1 (illustrative)

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 54%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr>
<th>Dimension</th>
<th>Requirement</th>
<th>Verification</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tested</td>
<td>Unit, integration, and contract tests as applicable; existing e2e
suite passes; new e2e for primary flow.</td>
<td>CI.</td>
</tr>
<tr>
<td>Observable</td>
<td>Metrics for new feature surface published to existing observability
stack; dashboard added; alerting configured for guardrail metrics.</td>
<td>Automated dashboard and alert presence checks.</td>
</tr>
<tr>
<td>Accessible</td>
<td>WCAG 2.1 AA; uses approved accessible component library.</td>
<td>Automated scan; component-use check.</td>
</tr>
<tr>
<td>Performant</td>
<td>No P95 latency degradation &gt; 5% on touched home-screen endpoints;
CPU and memory budgets hold.</td>
<td>Load test in CI; production canary observation.</td>
</tr>
<tr>
<td>Secure</td>
<td>Threat-model addendum reviewed by security approver for any new data
flows; OAuth and authz changes reviewed; no new PII categories without
DPO sign-off.</td>
<td>Attestation by security engineer approver; DPO attestation if
PII.</td>
</tr>
<tr>
<td>Compliant</td>
<td>Existing compliance posture preserved; any change to data handling
reviewed by compliance approver.</td>
<td>Compliance approver sign-off.</td>
</tr>
<tr>
<td>Instrumented</td>
<td>A/B framework integration; primary metric and guardrail metrics
emitting; experiment registered with experimentation team.</td>
<td>Automated check of experiment registry.</td>
</tr>
<tr>
<td>Rolled out safely</td>
<td>Behind feature flag; phased ramp through experimentation framework;
rollback via flag.</td>
<td>Automated flag-presence check.</td>
</tr>
<tr>
<td>Owned</td>
<td>Named owner recorded in feature metadata; on-call rotation covers
feature.</td>
<td>Manual at production-ready transition.</td>
</tr>
<tr>
<td>Documented</td>
<td>Operational runbook updated; incident-response section includes the
feature; rollback steps documented.</td>
<td>Manual at production-ready transition.</td>
</tr>
</tbody>
</table>

These are illustrative, not normative. Real standards for a given
organization will differ in specifics; the structure is the point.

# 9. Open questions

Five questions are flagged for the next iteration.

**Standards bootstrapping.** The model assumes a standards registry
already exists. In practice, organizations will need to bootstrap one.
The recommendation is to start with three to five standards covering the
most common artifact classes and accept that everything else will
operate under a default catch-all standard until it is specified. The
bootstrapping process needs its own treatment.

**Standards evolution velocity.** Quarterly review may be too infrequent
in a period when AI capability is changing what producers can do month
over month. A faster review cadence may be needed initially, with the
understanding that standards stability matters too — a standard that
changes constantly is not a standard.

**Cross-class artifacts.** Some artifacts span multiple artifact classes
(a mobile app that includes a regulated payment flow, for example). The
union-of-standards approach is proposed but needs operational testing.
Conflict resolution between standards that disagree is unspecified.

**Approver capacity.** Standards that require named approvers create a
dependency on those approvers’ capacity. If every brownfield validated
change requires security attestation, the security team becomes a
bottleneck. The model needs a treatment of how approver capacity is
sized, queued, and prioritized.

**Relationship to existing quality and compliance functions.** Most
organizations have existing QA, security, compliance, and accessibility
functions. The production standards model both depends on those
functions (as approvers) and partially supersedes their team-by-team
enforcement. The reorganization that may follow is out of scope here but
is on the critical path for adoption.

These are the largest known unresolved questions. Smaller questions are
noted inline above.
