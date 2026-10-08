I shared this with team for Fall 2026 / Early Spring 2027 team doc of my work

I shared also with team on open slack channel:
I told team on slack channel update:

I found a solid alternative that seems reliable, which I’m using as my primary baseline and architectural bridge to derive my contribution from DIMA (https://arxiv.org/abs/2505.20922). The line traces nice from Dreamer to MAMBA through MARIE to DIMA.

For the visual world model side, I’m using NVIDIA γ-World (research.nvidia.com/labs/sil/projects/gamma-world) as a contemporary multi-agent visual-generation comparison, alongside the Cosmos transfer/foundation-model stack. (edited)

I found my primary baseline that fits 3/4 of my drafts!.. Should have their paper results by tomorrow (Sept 24) then deriving my (one by one mechanisms) contribution and evaluating different aspects

Baseline Choice: https://icml.cc/virtual/2026/poster/61713 (using this as primary baseline)
Other baselines: https://openreview.net/forum?id=xT8BEgXmVc, ObjectZero, MAZero, etc. (MuZero, TD-MPC2/Newt, Flow-Actor-Critic, Diffusion Sheaves, Dreamer lines also)
Open-Ended paper UED/Autocurricula extension paper connection: https://arxiv.org/abs/2303.03376
Interactive video world gen connection: https://research.nvidia.com/labs/sil/projects/gamma-world/, https://arxiv.org/abs/2608.08600
Video Gen Architectures: https://huggingface.co/Lightricks/LTX-2.3, (wann 2.2) https://wan.video/research-and-open-source
FACTS (state-state memory) https://proceedings.iclr.cc/paper_files/paper/2025/hash/ac58b418745b3e5f10c80110c963969f-Abstract-Conference.html?utm_source=chatgpt.com, Graph Transformer / Graph-Mamba 

I found solid alternative that seems reliable and well written I am using instead as my primary baseline bridge: https://arxiv.org/pdf/2406.15836 and for visual generation experiment: https://research.nvidia.com/labs/sil/projects/gamma-world/

also found inspiration from: https://arxiv.org/html/2602.10982v1
also https://link.springer.com/article/10.1007/s11634-013-0134-6

 I found my primary baseline that fits 3/4 of my drafts!..
Title: Universe in a Bottle: Exact Revision-Persistent Programmable Neuro-Symbolic Multi-Agent Visual World Models
Lead Author: Blake Harrison
Abstract: We introduce Universe in a Bottle (UIB), a programmable neuro-symbolic (NeSy) multi-agent visual world model for continual joint-revision persistence and out-of-distribution (OOD) compositional generalization in open-world embodied teams. UIB combines versioned, exact-edit state-space memory with closed-loop interventional retrieval, decoupling continually learned hierarchical object-centric stochastic latent evidence from deterministic revisable symbolic semantics and meta-utility that guides its organization without rewriting or relearning retained latents. A many-to-one abductive mapping grounds language-defined Answer Set Programming (ASP) priors in visual dynamics and counterfactual signatures of quality-diverse capabilities and supporting knowledge. ASP contracts support exact Add, Split, Merge, Migrate, and Selective Unlearn-to-($\bot$) operations, with verified local-to-global polygraphic rewriting propagating revisions across shared team representations. An inductive temporal scene–factor graph transformer composes mixture-of-experts (MoE) dynamics, while predicate-conditioned cellular sheaves impose Hodge compatibility energies shaping a Gibbs–Boltzmann free-energy landscape linking language-grounded semantics and causal latent dynamics. NeSy MoE approximate dynamic programming retrieval unifies offline and off-policy model-based multi-agent reinforcement learning with symbolically admissible differentiable latent MPC and adaptive options for long-horizon capability recomposition. Across OG-MARL, RoboCasa, and Isaac Lab, UIB improves joint-revision persistence, skill transfer, language-preference and causal-constraint adherence, and OOD team compositional generalization over programmable and multi-agent visual world model baselines under matched training and adaptation budgets.
Target Venue: CVPR 




Title: Trustworthy Semantic–Causal Programmable Multi-Agent World Models for Open-World Embodied Multi-Agent and Human–AI Teams: A Survey
Subtitle: A Neuro-Symbolic Causal Meta-Utility Value, Compositional Game Theoretic, and Object-Centric Approximate Dynamic Programming Perspective 
Lead author: Blake Harrison
Abstract: Open-world embodied multi-agent systems and human–AI teams must continually acquire, revise, and recombine capabilities and constituent knowledge under diverse adversarial out-of-distribution (OOD) shifts. Yet predictive accuracy alone does not establish causal transfer, preserve collective competence after revision, or justify safe execution of novel behavior, as is character defining in the open wild. This survey examines trustworthy semantic–causal world models through a unified taxonomy of representations, evidence, capability learning, coordination, and assurance. We synthesize object-centric graph, transformer and set representations, neuro-symbolic language grounding and causal reasoning, continual and open-ended learning, model editing and selective unlearning, and world model-agent co-adaptation – compositional, evolutionary and partially observable games – self-/co- play and self improvement, computational creativity and procedural imagination and worlds, hybrid world simulation, world value and world action models, and mixed initiative, adversarial agents and red-teaming and co-creation human–AI collaboration. Throughout, we distinguish partial observability from partial identification of mechanisms and human preferences. An approximate dynamic programming perspective connects meta-utility value learning, model-based multi-agent reinforcement learning, and local–global model predictive control, informed by demonstrations, interaction, generative priors, and hybrid simulation. We relate imitation learning, inverse reinforcement learning, and direct value learning to passive observation and active perception, examining how visual experience, symbolic knowledge, and natural language support semantic–causal grounding. Two complementary questions guide our analysis: how to value the delayed causal effects of acquisition, editing, and selective unlearning on retention and recomposition; and how acquiring and transferring admissibility evidence can support safe expansion of capabilities and knowledge while respecting human preferences and constraints. We examine autocurricula, unsupervised environment design, quality-diversity, self- and co-play, self-improvement, and self-organization alongside meta-contract adaptation, interventional validation, counterfactual evaluation, uncertainty calibration, formal verification, and human oversight. A reference architecture relates these mechanisms while distinguishing empirical performance from conditional safety guarantees. Evaluation addresses retained capability and knowledge growth, compositional generalization, constraint adherence, joint safety and recovery, safe co-adaptation and emergence, preference satisfaction, and self-reflexivity assessed through calibrated self-assessment, failure diagnosis, and correction. We cover multi-agent, mixed-initiative, and co-creative human–AI settings across mobile manipulation, humanoid, aerial, rover and underwater UxV robotics, logistics, autonomous vehicles, and interactive games and procedural world simulation. Finally, we identify open problems in causal abstraction, compositional assurance, and human-directed agent–model–world co-evolution.
Target venue: CSUR Journal Survey (End of Oct. target review, with feedback revisions Dec. latest)
—

Title: C³META: Learning to Expand Capability Frontiers for Open-Ended Compositional Generalization in Programmable Multi-Agent World Models
Lead author: Blake Harrison
Abstract: Open-world robot teams must generalize capabilities to unseen objects, tasks, and teammates under out-of-distribution (OOD) shifts. Yet multi-agent autocurricula optimize tasks, environments, or learning progress, while generative value learning (GVL) values observed trajectories and multi-agent world-action models predict joint-action consequences rather than the effects of capability interventions on future team competence. We introduce C$^3$META, a programmable meta-utility multi-agent world-action model (PMU-MAWAM) and simulative GVL autocurriculum extending predictive action modeling from environmental actions to capability-repertoire interventions. C$^3$META values these interventions by their expected delayed counterfactual Team Pareto-hypervolume (TPH) gain under future recomposition. An object-centric Bayesian inductive graph-transformer represents hierarchical object–agent–world structure as compositional Gibbs–Boltzmann energy basins in stratified fiber geometry, while language-grounded Answer Set Programming (ASP) provides revisable multi-shot rollout dynamics. Counterfactual evolutionary co-play revises conceptual blends and bidirectional cross-attention memory for capability recomposition, while combinatorial, exploratory, and transformational (C$^3$) objectives select candidates by predicted TPH expansion. Mixed-integer abstract approximate dynamic programming selects TPH-expanding options and subgoals while minimizing the shortest abstract path defined by known ASP dynamics in offline or off-policy online MuZero unplugged-style multi-agent extended formulation. Resulting TPH advantages prioritize simulated experience for approximate value iteration, which learns capability-frontier continuation values conditioned on preferences, constraints, context, and goals specified in natural language and grounded into ASP through contractive fixed-point updates, closing the loop between construction, valuation, revision, and adaptive search. Under matched budgets, C$^3$META improves OOD capability compositional generalization while preserving quality-diversity, retention, team recomposition, natural-language constraint following, and in-distribution performance.
Target venue: ICML

Title: CAST-MPC: Safe Explainable Programmable Multi-Agent Visual World Models under Partial Identification
Lead author: Blake Harrison
Abstract: Safe open-ended multi-agent capabilities emergence requires resolving uncertain admissibility without excluding safe discoveries or permitting inadmissible joint execution. We hypothesize that acquiring and causally transferring admissibility evidence beyond observed behavioral coverage, through interventional discovery of invariant mechanisms in shared-parent object–relation–affordance–option hierarchies, expands retained executable capabilities without relaxing safety requirements. Existing safe RL and MPC methods lack support for interventional discovery of invariant parent object centric structures, let alone in multi-agent joint editing continual learning and adaptation settings. We introduce CAST-MPC, a trustworthy neuro-symbolic semantic–causal world action model post-training framework that jointly learns team capabilities and transferable admissibility evidence through continual online learning under partial identification. Robot and human–AI teams are modeled as partially observed cooperative stochastic games with joint option policies and coupled safety constraints. Natural-language-grounded, machine-checkable meta-contracts specify admissibility; multi-shot Answer Set Programming encodes hierarchical task networks over options grounded in object relations and affordances. Causal meta-utility values guide discovery and planning through expected effects on retention, task performance, and human preference satisfaction. Competitive synergetics couples cooperative discovery with interventional red-teaming to acquire and challenge evidence in checkpointed imagination-augmented rollouts. Von Neumann–inspired meta-class aggregates organize typed mechanisms and evidence provenance. Partial optimal transport aligns intervention-supported invariant subgraphs for evidence transfer under explicit identification and confounding assumptions, with provenance enabling retraction. Partial Markov categories formalize abductive conditioning and admissible joint-continuation probability mass to guide exploration; hybrid causal–physical simulation tests feasibility. Approximate dynamic programming connects model-based multi-agent reinforcement learning with local–global model predictive control (MPC), using evolutionary–flow-based Hamilton–Jacobi–Bellman value approximation for continuous team control over semantic continuous fractal algebraic topology. Scenario-tree tube MPC gates joint execution through certificates for hard safety contracts across retained hypotheses under model-coverage and disturbance assumptions, with verified recovery. Updates undergo retention checks and recertification. Planned matched-budget sequential evaluations assess retained capability growth, generalization across tasks and teammates, preference satisfaction, unsafe joint executions, and retraction robustness.
Target venue: ICML 

Title: Graph Field Grammars: Explainable Self-Improving Programmable Multi-Agent World Models for Continual Co-Creative 4D Generation
Lead Author: Blake Harrison 
Abstract: Graph grammars are widely used to design large-scale interactive worlds for media and simulation, yet when multiple domains are combined they are often done so in ways that collapse quality-diverse contributions from either. This limits quality-diverse coverage and prevents the grammar itself from adapting as worlds evolve in a transformational creative manner. We introduce Graph Field Grammars (GfG), a semi- and self-supervised neurosymbolic object-graph transformational conceptual blending framework that learns a field over typed spatiotemporal graph-rewrite events, with hierarchical latent field-theoretic creation, interaction, and deletion operators for inverse procedural modeling of 4D worlds for blending that are assigned meta object class compositions online through bidirectional procedural generation---reconstruction. GfG operationalizes computational creativity through three coupled processes: blending aligns and recombines motifs across source grammars; exploration uses quality-diversity MPC-based search to discover high-value derivations within the current grammar; and transformation adds, removes, or retypes symbols, productions, and constraints to make previously unreachable world families generable. GfG learns and revises grammars through self-play, self-improvement, and co-creative emergent multi-agent interaction, while a neurosymbolic verifier enforces local geometric and semantic constraints and global topological, physical, temporal, and natural-language context, task constraints, goals and subgoal decomposition descriptions in a hybrid simulator. On the PCG Benchmark and a procedural 4D-world suite implemented in Blender Geometry Nodes and Infinigen, GfG improves valid multi-design-space coverage, controllability, cross-grammar motif retention, and language-conditioned constraint satisfaction over classical and learned graph grammars, Graph and RL based PCG, and quality-diversity baselines. Moreover, GfG further supports local grammar editing and subtree-level revision without retraining from scratch, enabling procedural 4D worlds to blend, explore, and transform multi-design spaces adaptively and dynamically online. 
Target Venue: IROS

 




- - -
(Below not yet active preview for next term)

Title: FACTIONS
Lead Author: Blake Harrison 
Abstract: Co-creative math representation models procedural imagination + cellular automaton paper concerning multiagent active matter self organization meta contract emergence study for procedural generation
Target Venue: IEEE CoG


Placeholder for my compositional meta value self explainability + trustworthy compositional robot imitation learning + self/co-play and self improvement co-adaptation with social meta contracts paper
Lead Author: Blake Harrison
Abstract: Placeholder for my self explainability paper for multi-agent systems for IROS
Target Venue: IROS

Placeholder for my new recurrent state-space memory (transformer + neural differentiable computer hybrid that works ideal with my symbolic state-space memory concept) and retrieval paper for multiagent mobile robotics and supports cellular automata
Lead Author: Blake Harrison
Abstract: Placeholder for my self explainability paper for multi-agent systems for IROS
Target Venue: CoRL


Placeholder follow up human-AI paper
Lead Author: Blake Harrison
Abstract: Placeholder for my self explainability paper for multi-agent systems for CoRL.. one will be on multi-agent continual co-adaptation emergent memory retrieval and meta adaptation through meta social contracts
Target Venue: CoRL

Evaluation benchmark for complex multiagent world models using video games and RLVR
Lead Author: Blake Harrison
Abstract: This is revision of my prior ongoing project with masters students, this year we will complete
Target Venue: NeurIPS Main conference (workshop backup)

