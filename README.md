# time-stamp-on-my-thesis-direction-phd

Research safe:

## FOCUS

Coherent Thesis Spine:

My core thesis problem is "planning-induced model bias under constrained belief-space dynamic programming."

formally:

Stable, contraction-preserving belief-space dynamic programming under learned causal world models to mitigate planning-induced model bias.

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
