# time-stamp-on-my-thesis-direction-phd

Here are my comments to my PhD Advisor I sent for my research directional focus:

TL;DR: Extend symbol grounding to control by introducing feasibility as an explicit layer between perception and action, and use model-based planning for constraint-consistent execution.

I think I’ve clarified the core positioning of my work and how it connects to both classical symbol grounding and current VLM/VLA approaches.

The key shift is that I’m no longer trying to build a full VLM-based controller from scratch. Instead, I treat a strong multimodal model (e.g., Gemma 4) as a fixed grounding frontend, and focus my contribution on a learned admissibility layer and model-based control on top of it.

The pipeline is:
VLM (QLoRA) → latent bridge (Mamba2 + XL memory) → learned admissible action set → model-based control (ADP / MPC)
The main idea is to explicitly decouple:

grounding (handled by the VLM),
feasibility (handled by a learned admissibility model),
control (handled by model-based planning).


Concretely, instead of learning a policy π(a|o, l), I learn an admissible set A_adm(s, l) and then perform constrained optimization:
a_t ∈ argmin_{a ∈ A_adm} Q(s, a)

This reframes offline goal-conditioned RL as learning a feasibility/verification operator over actions conditioned on grounded state, which is then combined with model-based planning (e.g., ADP/MPC with QD-style proposal generation).

Conceptually, I’ve been thinking of this as extending the classical symbol grounding problem. Traditionally, grounding focuses on mapping symbols to perceptual representations:
Symbol → Perception

Modern VLM/VLA approaches extend this to action:
Language → Representation → Action

But they still rely on implicit learning of feasibility and constraints. My view is that grounding for embodied agents is incomplete without an explicit feasibility layer, so the full structure should be:
Symbol → Perception → Feasibility → Action

In this formulation, a symbol is only “grounded” if it induces a non-empty, constraint-consistent admissible set of actions. This provides a cleaner connection between language grounding, control, and safety.

From a modeling perspective, I’ve been viewing the admissibility layer as an energy-based feasibility model. One way I’ve been instantiating this is through physically-inspired structure (i.e. I use optical light transport theory / interface constraints like total internal reflection, reaction–diffusion self-organization, and attractor-based regime structure), which provides a structured way to represent constraint propagation, repair, and feasible regions of control. In this framing, these are not separate contributions, but one possible instantiation of the admissibility energy. I also use a free-energy Gibbs formulation with symplectic (Yoshida-style) integration to encourage stable long-horizon imagination/rollouts.

For Paper 1 (NeurIPS/CoRL), I’m focusing specifically on the admissibility component and its integration into low-level model-based control, using a fixed VLM frontend. This gives a clean experimental setup where I can evaluate both on higher-level embodied tasks (VLM/VLA-style benchmarks) and smaller controlled environments (e.g., OGBench/Atari-style settings) to isolate the contribution via ablations.

I’ll share a draft this week. One open question I’d appreciate your input on:
does it make more sense to primarily use a smaller VLM (e.g., Gemma E4B) to highlight the benefit of admissibility under imperfect grounding, or should I also include results with a larger model to demonstrate robustness?

and also in the thread reply:

In my survey, I’m also connecting this framework to areas like procedural generation, ASP, and causality. I’m viewing these as structured ways to encode constraints and intervention semantics, which can strengthen the admissibility component in the grounding + control pipeline. I’m also using QD (e.g., Elite Maps) to introduce diversity within the admissible set.

The unifying perspective is that admissibility acts as a learned feasibility layer for control: it allows the system to enforce hard constraints while still optimizing over soft preferences during planning.

This naturally connects to domains like computational creativity, PCG, visual navigation, and mobile manipulation, where you need to balance strict feasibility requirements with under-specified or stylistic objectives.

Compared to approaches that rely primarily on trust regions or soft penalties, this formulation enforces constraints directly during rollout via the admissible action set. Under the standard assumptions in the model, this gives stronger feasibility guarantees within the planning loop.

I’m thinking of this overall direction as a modern formulation of language grounding for control, where language specifies constraints and preferences, and admissibility enforces them during planning.



Research safe:

## FOCUS

Below is the **clean, thesis-level formulation** that keeps your **core focus exactly as stated** while integrating the additional rigor we discussed (causal belief uncertainty, drift, amortization bias, Free-Path-Energy PD-MPC, emergent DSL, etc.).

I’ll present it in the **same structure you asked for**, but tightened to something you could literally place in a proposal or thesis introduction.

---

Formulation:

tl;dr — until I send the full drafts over the next few weeks, my main focus is Hologram and the Universe in a Bottle (UIB) survey/framework for natural language command understanding in embodied agents.

I had a pretty important breakthrough in how to position the method: the math fits much more naturally as an offline RL method than as a purely online method with heavy reward shaping. Once I stopped forcing it into the online framing, it clicked as the baseline I had been looking for.

At a high level, the direction now looks like this:

1. Hologram = the low-level control layer
learned world simulator
approximate dynamic programming
HJB / viscosity-style framing
free-energy / Gibbs connection for compositional constraints and more stable rollout-based imagination

2. Causal Deep Belief Graph scaffolding
Judea Pearl-style causal structure
DSL for counterfactual/meta-level reasoning

3. ASP admissibility layer
feasibility
reachability
repair

The broader goal is to use these pieces together to improve natural language command understanding, i.e. helping an agent understand a language command and execute it faithfully under constraints.

This broader staged thesis direction is what I’m calling Universe in a Bottle (UIB).
A big part of the insight is that this problem seems much better suited to a staged offline-first approach:
learn world simulators offline
learn value functions offline
do online control optimization on top of those learned components

That feels much closer in spirit to methods like MuZero and also aligns better with the stability issues I kept running into with fully online approaches. It also connects well with prior work I’ve done around Decision Transformer-style methods.

So for the immediate research plan, I’m no longer fighting upstream on the online framing. Instead:
Paper 1 / CoRL: Hologram as the minimal low-level offline baseline
Survey / journal paper: UIB as the broader proposed framework for command understanding
Paper 2 / AIIDE: graph edits + procedural generation + certification, likely using a more direct Decision Transformer style approach for that layer

One concise way to state the core connection is:
Imagination := rollout under a learned latent world model

That framing is turning out to be much cleaner for everything.

I’m also connecting this as general UIB solutions to different command understanding problems:
procedural generation via structured graph editing for constrained emergence
How energy based formulation enables additive compositional terms and more coherent rollouts via free energy gibbs + yoshida integration and HJB viscosity formulation connecting bellman fixed point optimization and energy based landscapes between agent and world simulator (contribution of Hologram).
causal graph discovery via curiosity for coverage
counterfactual editing for DSL meta control / communication between agent and its world model
evolutionary RL for data collection / self-play / self-improvement
I2A-style imagination during online optimization for improved sample efficiency, transfer learning negative energy reduction and dynamic adaption
Stability and how staging offline + distillation and curriculum + HRL and options can be used to achieve stable policies that can be used for online control optimization under belief constraints (i.e. operations control)

My plan now is to build this bottom-up, paper by paper, with a minimal viable research paper approach rather than trying to force the entire stack into one result at once.
So the two main priorities right now are:
Hologram as the CoRL-targeted base method
the UIB survey/framework paper

After that, I’ll push the AIIDE graph-edit paper, which should let me define the causal graph + admissibility layers more concretely, i.e. with red teaming / POSG minimax belief-flow style certification.

I also still have the curiosity / causal graph discovery direction in mind for a later ICLR-style paper, especially since it connects naturally to the DataCollector and self-play work, but I’m intentionally keeping that scoped down for now until I have proof-of-concept results.

Overall, the key shift is:
stage the system, lean into offline RL, keep the components modular, and prioritize stability.
That shift feels much cleaner both scientifically and as a long-term research direction

---

Then I revised to:

I’ve pivoted Hologram (from ATLAS) into a much cleaner formulation as an offline goal-conditioned RL method for constrained control.
At a high level:
Rollout := imagination under a learned world model

Control is formulated through an Hamiltonian-Jacobian-Bellman Viscosity (HJB) / free-energy (Gibbs) objective, which lets me compose multiple task, preference, and constraint terms cleanly for long-horizon planning under constraints

Optimization is done via approximate dynamic programming + planning, rather than actor-critic
This fits much better with the multi-objective goal conditioning work I’ve been doing. It’s also significantly more stable than the earlier reward-shaping formulation and aligns naturally with language conditioning (language → goals / constraints / preferences).
Connection to prior work is fairly direct:

model-based RL / TD-MPC-style planning / approximate dynamic programming
constrained optimal control
offline RL with learned world models
For evaluation, I’m focusing on:

OGBench (goal-conditioned / stitching)
RoboCasa365 (compositional manipulation + diversity)
D4RL / Franka Kitchen (canonical offline benchmark)
CALVIN (language-conditioned long-horizon tasks)
Metrics will center on:

task success / instruction following
constraint compliance (violation rate / safety adherence)
diversity / coverage
Plan:

Share initial results this coming week (single-seed, sanity + early comparisons)
Share a first draft within ~2 weeks
Then expand to multi-seed evaluation and ablations


I’m intentionally shifting to a more bottom-up approach (experiments → iteration → theory tightening), and time-boxing broader survey framing for now. There are additional extensions I’m thinking about (e.g., PCG, multi-agent settings), but I’m keeping the current effort tightly scoped to this formulation.

Overall this direction feels much cleaner and better aligned with both the problem and my stack. Would appreciate any early feedback once I send results.

---

# Core Problem

**Language Grounding Command Understanding for Embodied Agents**

Embodied agents must interpret semantic instructions and produce **environment states or action trajectories** that satisfy those instructions while respecting physical constraints.

Formally, given:

* observation history (o_{1:t})
* belief state (b_t)
* environment model (M)
* instruction (u)

the agent must produce behavior

[
\tau^* = \arg\max_{\tau} P(\tau \mid b_t, u)
]

where

[
\tau = (x_0,a_0,x_1,\dots,x_H)
]

is a trajectory consistent with both the environment dynamics and the instruction.

Language grounding therefore requires **integrating semantic reasoning with physical planning under uncertainty**.

---

# Two Subproblems

## 1. Language-Grounded Scene Generation

Given an instruction (u), generate a structured environment configuration (G).

[
G^* = \arg\max_G P(G \mid u)
]

Example instructions:

```text
put the red block beside the tree
place the blue block on grid position [3,5]
generate a dungeon with two rooms and a key
```

Scene generation is equivalent to **structured state synthesis conditioned on language**.

Representative benchmark:

[https://github.com/amidos2006/pcg_benchmark](https://github.com/amidos2006/pcg_benchmark)

Here the agent must produce a valid **environment state graph** consistent with semantic constraints.

---

## 2. Language-Grounded Task and Motion Planning (TAMP)

Given an instruction (u), generate a trajectory that accomplishes the task.

[
\tau^* = \arg\max_\tau P(\tau \mid u)
]

Examples:

```text
pick up the red block
avoid the gap
move around the obstacle
```

The trajectory must satisfy:

* semantic goals
* physical feasibility
* safety constraints.

This is fundamentally **planning conditioned on language**.

---

# Thesis Hypothesis

> **Stable, contraction-preserving belief-space dynamic programming under learned causal world models can mitigate planning-induced model bias for language grounding for embodied agents.**

The central idea is that **language grounding fails today primarily because planning and semantic interpretation are disconnected from belief-space reasoning over causal world models**.

---

# Fundamental Failure Modes

The thesis focuses on four failure modes that prevent reliable language grounding.

---

# 1. Causal World Model Error

Most learned world models approximate:

[
P(x_{t+1} \mid x_t,a_t)
]

but ignore the **causal structure** of the environment.

This leads to:

* poor compositional generalization
* brittle reasoning about object relations
* failure under interventions.

Solution:

Represent the environment using **causal belief graphs**

[
G_t = (V_t,E_t)
]

with nodes representing objects and edges representing relations.

---

# 2. Causal Belief Uncertainty

Embodied agents operate under partial observability.

The correct planning variable is a **belief distribution**

[
b_t = P(G_t \mid o_{1:t},a_{1:t-1})
]

However most language-conditioned agents collapse belief to a point estimate.

Ignoring belief uncertainty causes:

* incorrect grounding of objects
* misinterpretation of relations
* unsafe planning decisions.

Solution:

Perform planning directly in **belief space**.

---

# 3. Planning-Induced Model Bias (Drift)

When planning with learned world models, errors accumulate over time.

If the model error per step is (\epsilon), then the rollout error grows roughly as

[
O(H\epsilon)
]

for horizon (H).

This produces **trajectory drift**, where predicted states diverge from reality.

Drift is especially problematic for language grounding because constraints are evaluated on **incorrect predicted states**.

Solution:

Use **short-horizon model predictive control with value bootstrapping** to stabilize planning.

---

# 4. Amortization Bias

Many language-conditioned agents rely on amortized policies

[
\pi_\theta(a \mid b,u)
]

instead of explicit planning.

Amortization introduces representation bias:

[
\pi_\theta \notin \Pi^*
]

The learned policy cannot represent all optimal behaviors.

This leads to:

* poor generalization to new instructions
* failure in rare environments.

Solution:

Replace pure amortization with **planning-based decision making**.

---

# Proposed Framework

The thesis proposes a unified architecture that integrates:

1. **Causal belief graphs**
2. **Belief-space dynamic programming**
3. **Contraction-preserving PD-MPC planning**
4. **Energy-based semantic grounding**

---

# Free Path Energy Planning

The planner minimizes a **Free Path Energy functional**:

[
\mathcal F(q)
=============

-\mathbb E_q[R(\tau)]
+
\frac{1}{\beta} KL(q(\tau),|,p_0(\tau))
]

subject to

[
\tau \in \mathcal F(u)
]

where

* (R(\tau)) is expected return
* (p_0(\tau)) is a proposal trajectory prior
* (\mathcal F(u)) encodes language-derived constraints.

Language modifies the planner through:

### Soft preference energies

[
E_{pref}(u,\tau)
]

### Hard constraint barriers

[
g_{hard}(u,x_t)
]

which produce infinite energy penalties when violated.

---

# Resulting Planning Law

The optimal trajectory distribution becomes

[
q^*(\tau)
\propto
p_0(\tau)
\exp(\beta R(\tau))
\mathbf 1_{\mathcal F(u)}
]

This formulation integrates:

* planning
* uncertainty
* semantic constraints

within a single probabilistic framework.

---

# Conceptual Architecture

```text
observation
      ↓
belief inference
      ↓
causal belief graph
      ↓
latent semantic intent
      ↓
spectral task abstraction
      ↓
Free Path Energy PD-MPC
      ↓
actions or generated scenes
```

The same architecture supports both subproblems:

* **scene generation** (choosing a valid environment state)
* **task and motion planning** (choosing a valid trajectory).

---

# Thesis Contributions

The thesis contributes a unified framework for language grounding that:

1. learns **causal world models** of environments,
2. performs **belief-space dynamic programming**,
3. mitigates **planning-induced drift and amortization bias** using contraction-preserving MPC,
4. integrates language semantics as **energy-based trajectory constraints**.

---

# One-Sentence Thesis Statement

A concise statement is:

> Language grounding for embodied agents can be improved by performing contraction-preserving belief-space dynamic programming over causal world models while representing semantic instructions as energy-based constraints on trajectory distributions.

---

If you'd like, I can also show you **the most natural 3–4 paper breakdown of this thesis** (CoRL / NeurIPS / ICRA / AIIDE) that cleanly separates:

* scene generation
* TAMP
* world models
* semantic grounding.



Coherent Thesis Spine:

My core thesis problem is "planning-induced model bias under constrained belief-space dynamic programming."

formally:

Stable, contraction-preserving belief-space dynamic programming under learned causal world models to mitigate planning-induced model bias for embodied agents.

system identification -> controller repoptimization

examples with regulation -> equillibrium constraints

recoverable no bring back replay for online learning
causal do-computation

one more week after spring break

want to hear from them before spring break or research plan with minimal research project
research proposal

concept reachability + bellmann contraction state constraints invariant sets page 126 describes state constraint safe regions 
dynamic programming or optimal control problem
engineering challenge into a dynamic programming problem

simplify and relevant to problem of this course

more meaningful which methodology can be applied to this problem

i.e.

Belief-space constrained dynamic programming via learned causal world simulators.

Pillar 1 — Constrained belief-space Dynamic Programming operator

Pillar 2 — Learned causal world simulators as belief dynamics

Pillar 3 — Evolution strategies as decision-time policy improvement
(3a) with QD / MAP-Elites repertoire for priors and diversity
(3b) quasi-newton for local basin refinements

Pillar 4 — Game-theoretic formulation (Partially Observable Stochastic Game)

Supportive within experiments and pillars:
Embodiment Control
Co-creation / Mixed Initiative (showing computational creativity overlap also)
Natural language intent-alignment
Exploration strategies

Future arch:

This framework naturally extends toward population-level coevolution and open-ended multi-agent systems.

Aside for lifetime of work:

A lifetime direction must generalize across:

Robotics

Game AI

Multi-agent simulation

Human–machine teaming

Ecology / ALife

Decision theory

Your operator spine scales across all of those.

That’s a good sign.

It combines:

Partial observability

Constrained optimal control

Learned dynamics

Counterfactual reasoning

Long-horizon planning

Multi-agent extension

Each of those alone is a multi-decade field.

Combined coherently, that’s very deep.

It also scales across:

Algorithmic work (ES, QD, Newton, MPC variants)

Representation work (causal models, belief factorization)

Theoretical work (convergence, equilibrium operators)

Systems work (distributed simulation)

Application work (games, embodied agents)

Population/ecological work (coevolution)

Core community:
**Embodied Decision-Time Planning for Autonomous Agents.**

Secondary but closely related application-focused communities for me are:
	•	Mixed-Initiative Human–Machine Teaming, especially around co-creation
	•	Multi-Agent World Simulation, Self-Play, and Self-Improvement
	•	Causality, Structured Preferences, Counterfactual Reasoning, and Intent Alignment

Core thesis/dissertation problem:
**Intent-Aligned Decision-Time Planning with Learned World Models**.
especially with robotics mixed initiative and
**Intent-Aligned Imagination for Mixed-Initiative and/or Co-Creation in Interactive Worlds and Robotics**.

## Here Be Giants Simulations Alignment with Thesis/Dissertation Conceptually:
Here Be Giants World Simulators Lab
Co-Creative, Intent-Aligned World Modeling for Mixed-Initiative Human–Machine Teaming

## Validation Regimes (3)
- Safe Embodiment Planning Under Uncertainty (MBRL/MPC in our case)  
  - This is where the mobile manipulation came in.  
  - Language instruction following, safety compliance, and human-given language constraints form the Mixed-Initiative HMT setting, and this is where all the NeSy work integrates.

- Co-creation (voxel representation world generation + co-adaption with co-agent evolution)  
  - This is the mixed-initiative planning task where the goal is actual co-construction.

- Video Generation World Model Benchmarks  
  - My proposed framework can dream and improve through offline application to existing world models via self-play and self-improvement, with/without adaptive PEFT.

## Core Technical Concept
- The primary concept generally in this direction I am introducing is to use energy-based causal world modeling and imagination (MPC rollouts, Dyna style, possible I2A combination).  
- Curiosity, curriculum learning, LUPI, etc. all stack in when oriented around this unifying axis.  
- ORBIT is a first novelty towards this by treating entire segments of the rollout trajectory as a trajectory-level energy functional defined over the same offline learned dynamics path distribution, and then selecting actions by inference/reranking that optimizes this unified objective (dynamics credibility/coherence + return-to-go + any constraint/predicate terms), rather than exploiting local one-step prediction errors under selection pressure.

---

## 2026 Plan
Hi Yezhou,

I wanted to share an updated 2026 research plan that aligns each project with its “home” community and venue, and positions us strongly by year end. At this point, strong positioning really comes down to sequencing and execution, now that the core community focus is clear.

The organizing theme has strongly converged on:

Embodied Decision-Time Planning for Autonomous Agents.

That’s my true (Kungfu) Pandas  community.

Secondary but closely related application-focused communities for me are:
	•	Mixed-Initiative Human–Machine Teaming, especially around co-creation
	•	Multi-Agent World Simulation, Self-Play, and Self-Improvement
	•	Causality, Structured Preferences, Counterfactual Reasoning, and Intent Alignment

Below are four papers, each with a single primary focus and a conservative submission/backup strategy, all supporting a unified thesis direction:

Intent-Aligned Decision-Time Planning with Learned World Models.

⸻
(Dates are upcoming hard target submission deadlines with backups planned in case of community paper rejection)

1) ATLAS (primary control / embodiment paper)
I reframed the abstract to a single focus and corrected the experiment design to better match robot-learning community expectations.

Target sequence:
	•	CoRL 2026 (primary flagship)
	•	ICRA 2026 (backup)
	•	CVPR 2026 (Embodied track; final backup), emphasizing the hierarchical Q-critic visual feature and representation aspects
	•	IROS 2027 (final backup embodiment submission)

I will have the updated draft/abstract ready, with new experiments running, starting today and over the next two weeks.

⸻

2) Constraint + world generation paper (PCG / alignment / certification angle) (WIP title; draft this week)
I split out the “unique constraints” contribution into a dedicated paper: ES-based constrained optimization with multi-agent evaluation and MPC/intention guidance for world generation (self-play and self-improvement validation).

Target sequence:
	•	IEEE CoG 2026 (primary; March 15 deadline)
	•	AAMAS 2026 (backup; submit October 2026)
	•	AISTATS 2027 (final backup; submit late January / early February 2027)

⸻

3) Causal energy preferences + value-approximation scaffolding (WALRUS line)
This paper focuses on causal, energy-based preferences and value scaffolding built on an existing WALRUS world model. I’m iterating on the formulation with weekly feedback from the Bertsekas course.

Target sequence:
	•	NeurIPS 2026 (primary)
	•	ICLR 2026 (backup)
	•	CVPR Embodied track (additional backup)
	•	IROS 2027 (final backup)

⸻

4) Phase-2 reasoning module: text-only scene-graph semantic curiosity exploration for intention alignment
A separate paper on a “secondary cadence” text-only reasoning module over scene graphs, aimed at improving exploration and intention alignment (distinct from the causal energy-preference line).

Target sequence:
	•	ICLR 2026 (primary)
	•	AISTATS early 2027 (backup)
	•	IJCAI 2027 (final backup)

⸻

Survey / journal synthesis
In parallel, I’m drafting a unifying survey/journal-style synthesis oriented around Intent-Aligned Decision-Time Planning with Learned World Models, consolidating the shared framing across these efforts.

Last but not the least, we are pulling the ICML draft before submission and continuing momentum on three primary efforts this term: CoRL (ATLAS flagship), IEEE CoG (constraints and world generation), and NeurIPS (causal energy preferences and value scaffolding). We are also drafting the unifying survey in parallel.

Best,
Blake
- My hard target is to have v1 of the main experimental results and draft ready this week for team review, so we have ~1.5 weeks before the ICML abstract deadline for revisions and remaining ablations.

Note: prior also shared today with advisor so direction is locked in.

0) Data axis spanning (coverage & diversity as a first-class strategy)

Sparse tasks fail most often because the agent never sees the right states. The “data axis” approach is: engineer coverage.

Behavior diversity: mixture of policies (random + scripted + prior policy + planner rollouts) to populate replay with diverse modes.

State-space coverage objectives: novelty/coverage maximization, visit-count proxies, ensemble disagreement–driven collection.

Cross-domain / cross-embodiment data: combine data from multiple morphologies/sensors/tasks to widen support; VLAs explicitly study when/how to add cross-embodiment data.

Dataset curation pipelines: balance terminals, hard negatives, rare obstacle segments, success/failure ratio; prioritize “near-success” slices (Go-Explore style).

Domain randomization / procedural generation: widen distribution (terrain families, friction, slopes, obstacles) to reduce brittle local optima.

Active data collection: collect where uncertainty/TD-error is high (a “hardness sampling” curriculum).

1) Training staging: state-only → multimodal distillation → PEFT / final finetune

This is a high-leverage stability pattern for complex settings:

Learn control/value in low-dim state (or privileged state)

Faster learning, cleaner TD targets, fewer representation pathologies.

Distill to multimodal (images, language, audio)

Teacher: state-based policy/critic/planner

Student: vision(+language) policy/critic; distill logits, Q-values, latent plans, or action sequences.

PEFT / finetune on target modality

LoRA/adapters/prefix-tuning, low-rank heads, small policy heads on frozen backbones.

This is consistent with “multistage training paradigms” used in large world-model work (pretrain → adapt → downstream).

2) Learning from examples / data (IL, Offline RL, Offline→Online)

These are often the winning move for sparse reward.

2.1 Imitation Learning (IL)

BC (behavior cloning), DAgger, GAIL

Sequence-model IL (trajectory-conditioned policies; DT-family as “supervised RL”)

2.2 Offline RL (batch RL)

Behavior-regularized: TD3+BC, AWAC, IQL

Conservative: CQL-style pessimism

Model-based offline RL: MOPO/MOReL/COMBO-like families
(Use these when you can assemble a big replay/dataset but online exploration is painful.)

2.3 Offline → Online finetuning

Start with offline competence, then do short online finetune (often where planning + conservative value helps most).

3) Reward learning (IRL, preferences, language reward models)

When “hand reward” is the bottleneck, learn the reward.

IRL / AIRL / MaxEnt IRL: infer reward from expert occupancy.

Preference-based RL (PbRL): learn reward from pairwise comparisons (human or model-generated).

Language-derived reward: LLM/VLM critiques or classifiers as learned reward proxies (risky: reward hacking; needs verification/constraints).

4) Reward shaping & curriculum (classic levers, but formalize them)

Potential-based shaping (policy-invariant shaping).

Hierarchical / task-graph shaping: auto-derive shaping from task structure (there are papers doing this even on BipedalWalker Hardcore).

Curriculum learning

Hand curricula (difficulty ramp)

Automated curricula (goal selection, competence progress, teacher-student schedulers)

5) Structural priors / inductive bias (expanded)

You asked explicitly: language, preferences/constraints, graphs, frozen encoders, VLM/WFM, RLVR → yes, all fit here.

5.1 Frozen encoders & representation priors

Frozen CNN/ViT features; pretrained proprio encoders; contrastive SSL encoders

Use as:

observation encoder

auxiliary loss target

intrinsic reward feature space

5.2 Task-agnostic VLMs → VLAs (vision-language-action models)

Use a task-agnostic VLM backbone, then add an action head / policy interface (VLA). Recent work surveys key design choices, including cross-embodiment data scaling.

5.3 World foundation models (WFMs) / large world models

General-purpose world models that can be fine-tuned to specific physical setups is now an explicit framing (e.g., “world foundation model platform”).

Benchmarks/workshops explicitly target “world foundation models” for downstream embodied tasks.

5.4 Language intent as prior (preferences + constraints)

Preferences: scalarization / reward model prior over outcomes.

Constraints: hard/soft constraint embeddings and constraint critics.

Many generalist robot policies take language commands directly (e.g., Octo is language-conditioned).

5.5 Graphs / object-centric priors

Scene graphs, contact graphs, kinematic graphs, relational GNN dynamics → compositional generalization and better OOD structure.

5.6 RLVR as structural prior (verifiable reward channels)

RLVR = reinforcement learning with verifiable rewards: you build reward from checkable predicates (unit tests, constraint checkers, symbolic validators), which acts like a strong prior against reward hacking and can shape exploration.
In control/robotics terms: “reward = verified satisfaction of specs / constraints / success predicates,” plus dense auxiliary signals.

6) Dimensionality reduction & projection (make the problem “smaller”)

This is underrated and very practical.

Latent-state modeling: learn a compact belief state; plan/control in latent.

Bottlenecks / information constraints: force task-relevant compression.

Projections: PCA / random projections / low-rank adapters (esp. when paired with PEFT).

Manifold-aware control: learn control in a reduced subspace (often improves stability).

7) Exploration systems (beyond “just add curiosity”)

Intrinsic motivation: RND/ICM-style novelty, information gain, disagreement.

Goal-conditioned + relabeling: HER-like relabeling; goal curricula.

Skill discovery: DIAYN/VIC/APS families; then finetune with sparse reward.

Archive-based exploration: Go-Explore/quality-diversity style archives.

8) Planning + imagination/dreaming (I2A, I2A-style blending, dreaming)

This is your requested “I2A blending / imagination” bucket.

MPC planners: CEM/MPPI/CMA-ES over action sequences.

Tree search: MCTS over learned models/value.

I2A (Imagination-Augmented Agents): explicitly mixes model-free policy with learned-model rollouts interpreted by an “imagination” module.

Dreaming / imagination rollouts: generate synthetic experience from the world model; blend with real data (with uncertainty-aware filtering).

9) Stabilization & “don’t blow up” techniques (often decisive in sparse tasks)

Pessimism / conservatism in value learning (avoid OOD action exploitation).

Multi-step targets: TD(λ), Retrace/V-trace, return decomposition.

Distributional / risk-sensitive RL: quantiles, CVaR (helpful when failure penalties dominate).

Constraint / shielded RL: CMDPs, safety layers, barrier functions, action projection.

Practical “recipe stacks” (choose by what you have)
A) No demos, sparse reward, hard exploration

(Exploration + hierarchy + planning + verification)

intrinsic/disagreement exploration

landmark/options HRL

MPC/CEM planning bias

RLVR-style success/constraint verifiers

optional potential shaping as ablation

B) Demos or scripted examples available

(BC warm start → offline RL → online finetune)

BC / sequence BC

offline RL (IQL/AWAC/TD3+BC)

short online finetune + conservative critic / planner

C) Multimodal deployment required (vision+language), but state exists in sim

(State-first + distill + PEFT)

train state policy/critic/planner

distill to VLM/VLA student

PEFT finetune on target sensors/tasks

D) You want “foundation model priors”

(VLM/VLA + WFM + language intent)

VLM backbone (task-agnostic)

VLA action head

WFM for imagination / data augmentation

language preferences+constraints as priors (plus verifiers)
