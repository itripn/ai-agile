# Executive summary

This paper argues, then stress-tests, the claim that the product and
software development lifecycles refined over the past two decades — 
Agile in its various flavors, SAFe at scale, sprint-based delivery, 
story-pointestimation, the linear discovery-to-release pipeline — were 
calibratedfor a world that AI-assisted work has begun to dismantle. Two 
structural changes underwrite that claim. First, the marginal cost of 
producing a working production-grade first cut of almost any artifact — 
code, mock, schema, test, document, prototype — has collapsed toward zero, 
and the trajectory is steep enough that “production-grade” should be assumed
to be the near-term norm rather than an aspiration. Second, the set of
people who can produce that first cut has expanded well beyond
developers to include product managers, designers, analysts, and domain
experts. Together these shift several of the constraints that current
frameworks were designed to manage, and the shift is accelerating, not
stabilizing.

I assert this claim is directionally correct and arriving on a timescale
of months, not years. The case for sprint-based batching, story-point
estimation, role-as-gate workflows, and handoff-driven coordination is
collapsing. The case for coordination at scale, regulatory and
accountability gates, judgment about what to build, finishing
discipline, funding cadence, and the social rituals that hold
organizations together is not collapsing — and several of these become
*more* important, not less, as production cheapens. The implication is
not abandonment of PDLC/SDLC, but a deliberate redesign around the
bottlenecks that remain genuinely structural rather than the ones AI
assistance is in the process of removing. The remainder of this paper
lays out the mechanics that support the thesis, the structural
counterweights worth taking seriously, the qualified position the paper
arrives at, and four follow-on artifacts proposed for subsequent
treatment.

# 1. Framing

Before arguing whether current frameworks are ill-equipped, it is worth
being precise about the change they are presumed to be ill-equipped for.
“AI-assisted teams” in this paper means teams in which most contributors
— not only engineers — use general-purpose AI tooling to produce a
working first cut of artifacts they would historically have specified,
requested, or waited for. “Velocity” means the cycle time from a posed
question or proposed change to a validated answer or shipped change, not
raw output. With those terms held still, the question becomes: do
frameworks designed when artifact production was scarce, expensive, and
concentrated in one role still serve teams in which production is cheap,
fast, and broadly distributed?

The thoughtful answer requires us to remember what those frameworks were
optimizing for in the first place. Agile was a response to the failures
of large-batch waterfall planning under conditions of high requirement
uncertainty. SAFe was a response to the failure of grass-roots Agile to
coordinate across hundreds of teams with shared dependencies, regulatory
exposure, and finite funding. Story points were a response to the
unreliability of time-based estimates under conditions where engineering
effort dominated cycle time. Sprints were a response to the cost of
replanning when planning itself was expensive. Each of these is a real
solution to a real problem. The question is not whether they were ever
right — they were — but whether the problem each solves is still the
operative problem.

A note on capability assumptions before proceeding. This paper treats
AI-assisted production capability as a moving target on a steep curve.
Where the argument depends on a present-day capability claim, that claim
is flagged as a snapshot. Where the argument depends on something
structural — accountability, regulation, organizational coordination,
judgment, customer-time — it is treated as durable. The reader is asked
to extrapolate the trajectory aggressively rather than conservatively:
the operating assumption is that within a year, a single non-engineer
working with general-purpose AI tooling can produce, integrate, and ship
a production-grade artifact in domains where the surrounding system
permits it. That assumption is doing meaningful work in the analysis
below.

# 2. The thesis

Stated plainly: the frameworks of the past decade were calibrated
against constraints that AI-assisted work has loosened, and the
calibration is now beginning to act as a tax. The constraints that have
loosened are the cost and concentration of artifact production. The
activities those frameworks structure most heavily — estimation,
planning, decomposition, role-bounded handoff — were the activities
whose value was greatest when production was the bottleneck. As
production ceases to be the bottleneck for an expanding range of work,
the value of those activities falls relative to their cost. What
replaces the bottleneck is not nothing — it is integration, validation,
judgment, and rollout — but those new bottlenecks are not what current
frameworks are organized around.

This is the thesis worth defending and stress-testing.

# 3. The mechanics: why the thesis is plausible

Five structural arguments support the thesis. None is decisive on its
own, but together they describe a coherent shift.

First, **the cost of a first cut has collapsed.** What used to take a
week of engineering — a working prototype, a schema, a test harness, a
deployment script — now takes hours and increasingly minutes. The
frameworks of the past decade were built around estimation, batching,
and prioritization rituals whose core purpose was to allocate scarce
production capacity. When production capacity ceases to be scarce for a
growing class of work, the rationale for those rituals weakens.

Second, **the producer set has widened.** A product manager can now
stand up a working prototype to interrogate a hypothesis without filing
a ticket. A designer can produce a working component, not a Figma frame.
An analyst can build a queryable data product, not a request to data
engineering. This is not a marginal change. It changes who can start
work, which dissolves the assumption — embedded in nearly every
framework — that “build” begins with a developer claiming a story.

Third, **the discover-design-build-validate cycle compresses unevenly.**
Production accelerates dramatically; integration, validation, and
rollout do not, at least not at the same rate. The traditional pipeline
assumed roughly proportional stages and was structured to keep them
flowing. When one stage collapses to near-zero while others remain
expensive, pipeline thinking misallocates attention. Work piles up at
the new bottleneck, which is not where current frameworks place their
gates or ceremonies.

Fourth, **estimation degrades.** Story points were a proxy for
engineering effort against relatively constant developer throughput.
When the actual production effort for a given artifact varies by an
order of magnitude depending on whether AI tooling can produce it
cleanly on the first attempt, points lose their predictive value.
Velocity-as-points-per-sprint becomes a metric measuring something that
no longer matters — and worse, it begins to incentivize work that AI
assists well, regardless of whether that work is the most valuable.

Fifth, **handoffs become latency.** Frameworks structure handoffs
because handoffs were once coordination. PM specifies, design designs,
dev builds, QA validates: each handoff was a synchronization point that
allowed specialists to work in parallel on different things. When one
person can move through all four functions in a single session, the
handoff stops coordinating and starts queuing. Sprint cadence, ticket
flow, and pull-request workflows all assume that handoffs are valuable.
Increasingly they are not — they are where the cycle time goes.

# 4. The stress test: structural counterweights worth taking seriously

A thesis worth defending is worth attacking with the strongest available
counterweights. The temptation in any AI-vs-process argument is to lean
on capability gaps that exist today — what the model “still can’t do.”
Those counterweights have a known expiration date and should not anchor
a multi-quarter strategy. The counterweights below are deliberately
chosen because they would hold even if AI capability advances at the
steepest credible trajectory. They are the parts of the argument the
original thesis must contend with seriously.

First, **accountability and attestation are organizational, not
technical.** Regulatory frameworks — SOX, PCI, HIPAA, GDPR, FDA
validation, financial services oversight, SOC 2, accessibility law —
require *humans* to attest. The signature, the auditor’s opinion, the
credentialed reviewer’s sign-off: these are demanded by regulators, not
by capability gaps. Even if an AI produces a flawless threat model or
compliance package, a named human attests for the auditor. That floor
moves on regulatory time, which is years, not on model release time,
which is months. For any organization operating in a regulated domain,
this is durable structural friction that no model release dissolves.

Second, **customer-time and physical-world rollout have hard floors.**
Canary observation windows need real user traffic over real time to
surface long-tail behavior. A/B tests need statistical significance,
which requires user-volume × time. Some regulatory frameworks impose
mandatory waiting periods. Hardware and supply-chain dependencies move
at their own pace. AI doesn’t make 50,000 users hit a service faster
than they hit it, and it doesn’t shorten the half-life of a bad rollout.
Any framework reimagining must place its gates at customer-time
boundaries, not at code-production boundaries.

Third, **organizational coordination is invariant under model
improvement.** Conway’s law, dependency surface area, funding cycles,
the cognitive load of cross-team alignment — none of these are
code-generation problems. A team of twenty AI-augmented engineers
shipping ten times faster does not reduce the cost of coordinating with
the fourteen other teams whose services they depend on or whose
contracts they consume. In some ways it raises that cost, because the
coordination window shrinks while the rate of change accelerates.
SAFe-style portfolio mechanisms exist largely to manage this, and the
management problem does not go away when the producers get faster — it
intensifies.

Fourth, **the judgment of what to build inverts in importance.** When
generating a candidate solution costs essentially nothing, the
discipline of choosing well becomes the differentiator. The ratio of “we
could build this” to “we should build this” inverts dramatically, and
organizations that lose discipline at that gate ship faster in the wrong
direction. AI helps with analysis, comparison, and even strategic
synthesis, but it does not substitute for organizational judgment about
strategy, ethics, brand, customer relationships, or competitive
positioning. This is one of the few PDLC functions whose value goes up
rather than down as production cheapens.

Fifth, and most consequential for the solutioning work that follows,
**finishing discipline scales as production cheapens.** When a single
non-engineer with AI assistance can produce, integrate, and ship a
production-grade artifact in days, the question of what “done” means
intensifies, not relaxes. “Done” must encompass tested, observable,
accessible, performant, secure, compliant, instrumented, rolled out
safely, with a rollback path and a named accountable owner — and it must
do so for artifacts produced by any role, not just by engineers
operating inside a team’s existing finishing apparatus. AI assists with
every one of these dimensions and the assistance improves quickly, but
the *codified definition* of finishing — the standard against which
production-grade is measured — must live in the organization regardless
of who or what produced the artifact. Frameworks that treat
definition-of-done as a team-level checklist are not equipped for a
world in which production-grade artifacts arrive from anywhere.

Frameworks are also social technology — standups, demos, retros, and
reviews carry belonging, accountability, and shared sense-making, not
only coordination — and that function persists independent of production
speed. This is real but secondary to the five structural counterweights
above; it bears mention rather than full treatment here.

# 5. A qualified conclusion

Weighing the mechanics and the structural counterweights, the position
this paper arrives at is the following.

The thesis is correct that the current frameworks were calibrated
against a constraint set that is dissolving on a timescale of months,
not years. The cost of producing a production-grade first cut has
collapsed for a rapidly expanding class of work, and the producer set
has widened beyond developers in a way no current framework
accommodates. The discomfort many practitioners report when applying
SAFe-style structure to AI-assisted teams is not a failure of the
practitioners — it is a real signal that the framework is solving a
problem that is in active dissolution. Sprint-based batching as the
primary planning unit, story-point estimation as a forecasting tool,
role-as-gate workflows that assume a developer is the only legitimate
producer, and the linear discovery-to-build pipeline are all losing
their structural rationale. They should be expected to evolve
substantially or be replaced.

To be clear, this paper is not a call to abandon PDLC/SDLC wholesale.
The five structural counterweights identified above — accountability and
attestation, customer-time floors, organizational coordination, judgment
of what to build, and finishing discipline — are likely not capability
gaps that close as models improve. They are functions of regulation,
physics, organizational structure, judgment, and codified standards.
Several of them become *more* important as production cheapens, not
less. When generating a candidate solution costs nothing, the discipline
to choose well, to validate honestly, to attest accurately, and to
integrate safely is what carries the load. Frameworks that codify that
discipline are not the obstacle; they are what is left worth keeping,
and worth strengthening.

There is one further distinction the position depends on. The collapse
of the production constraint is not uniform across all contexts. In
greenfield work — a new, standalone application without entanglement in
an existing operational system — a large portion of the traditional PDLC
essentially dissolves. A single non-engineer working with AI tooling can
plausibly conceive, build, integrate, and ship a production-grade
artifact on a vastly reduced timescale, and the implication for that
mode of work is that frameworks designed for multi-role multi-week
production cycles are not adapting; they are becoming irrelevant. In
brownfield work — additions to existing systems with prior commitments,
shared dependencies, regulatory exposure, and operational history —
traditional PDLC partially persists, but its persistence is no longer
about allocating scarce production capacity. It is about coordinating
between AI-augmented producers and the rest of the organization, and
about enforcing finishing discipline against the existing system’s
constraints. The greenfield/brownfield gap is real today and is closing
quickly: practitioners are already observing AI-assisted non-engineers
making well-executed fixes inside long-lived applications. The gap
should be expected to compress further on the same timescale as the
underlying capability trajectory. The real framing is that brownfield is
following greenfield, not stable in opposition to it.

The correct conclusion, then, is **neither “the frameworks are obsolete”
nor “the frameworks are fine and the discomfort is adoption-pace
anxiety.”** It is that the frameworks need to be redesigned around a
different bottleneck topology and a different producer topology, with
the redesign calibrated to the trajectory rather than to today’s
snapshot. The next section proposes the four artifacts that follow.

# 6. Implications and proposed follow-on work

If this position is accepted in roughly the form above, four solutioning
artifacts naturally follow, and this paper proposes them as the next
deliverables for discussion. They are presented in the order this paper
recommends tackling them.

The first is a **reimagined unit of work**. The user story was a unit
calibrated to engineering effort against scarce, concentrated production
capacity. A more relevant unit for AI-assisted teams is likely something
closer to an experiment, an outcome hypothesis, or a validated change —
a unit whose lifecycle includes the production of a candidate solution
as a near-trivial step rather than the central one, and whose definition
of done emphasizes integration, validation, accountability, and learning
rather than completion of a build. The unit should also be expressive
enough to describe both greenfield work (where the unit may span what
was historically several stories) and brownfield work (where the unit
must additionally encode coordination obligations to other teams).
Without a defensible primary unit, the other three artifacts lack a
foundation to build on.

The second is a **production standards** model. Traditional
definition-of-done was a team-level checklist enforced through
ceremonies the team owned. In a world where production-grade artifacts
can be produced by any role, with or without that team’s involvement,
the standard for what production-grade means must move from team-owned
ritual to organization-owned standard. The artifact should specify, for
each meaningful artifact class, what production-grade means: the
testing, observability, accessibility, security, compliance,
performance, instrumentation, rollout, rollback, and accountable-owner
conditions that an artifact must satisfy regardless of who produced it.
The standard must be enforceable independent of producer role, and it
must be co-designed with the AI tooling that increasingly assists
producers in meeting it. This artifact is placed second because it is
the one most directly responsible for distinguishing useful velocity
from harmful velocity, and because both the unit-of-work and
role-and-gating artifacts depend on a coherent production standard to
refer to.

The third is a **revised role and gating model**. If anyone can produce
a production-grade first cut, the question becomes who can authorize,
who can attest, who can integrate against existing system constraints,
and who is accountable for the operational consequences. Roles do not
disappear — they reconfigure away from exclusive production rights and
toward judgment, attestation, integration, and accountable ownership.
The gating model needs to make this explicit, particularly for regulated
work where attestation is a legal requirement and not merely an
organizational preference. The model also needs to handle the case in
which the producer is a non-traditional role, without treating it as an
exception to be tolerated.

The fourth is a **modified cadence**. Sprint-based batching loses much
of its rationale when planning is cheap and producing is fast. A
defensible alternative is continuous flow at the team level with
periodic alignment rituals at the program and portfolio level —
preserving the coordination functions of SAFe-style cadence without
paying its batching costs. The cadence design must take seriously the
customer-time and physical-rollout floors identified above: faster
production does not shorten observation windows or
statistical-significance windows, **and the cadence should place its
review points at customer-time boundaries, not at code-production
boundaries**. The exact cadence is an empirical design question, but the
design space is worth exploring deliberately rather than letting it
emerge through neglect.

Each artifact deserves its own treatment, and the four together are
intended to be a coherent successor to the team-level and
portfolio-level mechanics of current PDLC/SDLC, not a set of point edits
to it.


---

*Part of [ai-agile](https://github.com/itripn/ai-agile) by Ron Forrester. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
