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

Title: Universe in a Bottle: Neuro-Symbolic Revision-Persistent Programmable Multi-Agent Visual World Models
Lead Author: Blake Harrison
Abstract: Open-world embodied teams require multi-agent visual world models that continually learn and revise shared knowledge for open-ended compositional generalization under out-of-distribution shifts. Yet, latent adaptation can revive obsolete interpretations or degrade protected capabilities and their supporting knowledge, undermining exact, jointly consistent symbolic revisions. We introduce Universe in a Bottle (UIB), a programmable model coupling symbolically guided continual learning of multimodal vision–language latent dynamics with independently revisable object-centric semantics and meta-utility through versioned symbolic state-space memory within a closed-loop programmable hybrid simulation. Multi-shot Answer Set Programming governs contract-checked local-to-global polygraphic rewriting across capability and knowledge dependencies, committing shared versions after finite verification of symbolic contracts. Mixture-of-experts approximate dynamic programming retrieval combines offline and off-policy multi-agent inverse reinforcement learning of meta-utility value with evolutionary quality-diverse counterfactual imagination. Within this formulation, continuous, latent-space multi-agent model predictive control generates diffusion-forced, symbolically admissible rollouts in a Gibbs–Boltzmann free-energy landscape of multimodal latent dynamics, where predicate-conditioned cellular sheaf compatibility energies shape basins and abductive probability mass. During revisions, noncommutative entropic optimal transport over density operators on complex Hilbert space uses current sheaf-energy costs to reorganize latent beliefs through many-to-one grounding into symbolic basins. Under matched training budgets, UIB outperforms programmable memory and multi-agent visual world model baselines in joint-revision persistence, multi-task transfer, and out-of-distribution compositional generalization of team capabilities while preserving protected capabilities and supporting knowledge.
Target Venue: CVPR


Title: Trustworthy Programmable Multi-Agent World Models for Continual Open-Ended Embodied Team Neuro-Symbolic Hybrid Simulation: A Survey
Subtitle: A Compositional Game Theoretic and Approximate Dynamic Programming Perspective 
Lead author: Blake Harrison
Abstract: Open-world embodied multi-agent systems and human–AI teams must continually acquire, revise, and recombine capabilities and constituent knowledge under diverse adversarial out-of-distribution (OOD) shifts. Yet predictive accuracy alone does not establish causal transfer, preserve collective competence after revision, or justify safe execution of novel behavior, as is character defining in the open wild. This survey examines trustworthy semantic–causal world models through a unified taxonomy of representations, evidence, capability learning, coordination, and assurance. We synthesize object-centric graph, transformer and set representations, neuro-symbolic language grounding and causal reasoning, continual and open-ended learning, model editing and selective unlearning, and world model-agent co-adaptation – compositional, evolutionary and partially observable games – self-/co- play and self improvement, computational creativity and procedural imagination and worlds, hybrid world simulation, world value and world action models, and mixed initiative, adversarial agents and red-teaming and co-creation human–AI collaboration. Throughout, we distinguish partial observability from partial identification of mechanisms and human preferences. An approximate dynamic programming perspective connects meta-utility value learning, model-based multi-agent reinforcement learning, and local–global model predictive control, informed by demonstrations, interaction, generative priors, and hybrid simulation. We relate imitation learning, inverse reinforcement learning, and direct value learning to passive observation and active perception, examining how visual experience, symbolic knowledge, and natural language support semantic–causal grounding. Two complementary questions guide our analysis: how to value the delayed causal effects of acquisition, editing, and selective unlearning on retention and recomposition; and how acquiring and transferring admissibility evidence can support safe expansion of capabilities and knowledge while respecting human preferences and constraints. We examine autocurricula, unsupervised environment design, quality-diversity, self- and co-play, self-improvement, and self-organization alongside meta-contract adaptation, interventional validation, counterfactual evaluation, uncertainty calibration, formal verification, and human oversight. A reference architecture relates these mechanisms while distinguishing empirical performance from conditional safety guarantees. Evaluation addresses retained capability and knowledge growth, compositional generalization, constraint adherence, joint safety and recovery, safe co-adaptation and emergence, preference satisfaction, and self-reflexivity assessed through calibrated self-assessment, failure diagnosis, and correction. We cover multi-agent, mixed-initiative, and co-creative human–AI settings across mobile manipulation, humanoid, aerial, rover and underwater UxV robotics, logistics, autonomous vehicles, and interactive games and procedural world simulation. Finally, we identify open problems in causal abstraction, compositional assurance, and human-directed agent–model–world co-evolution.
Target venue: CSUR Journal Survey (End of Oct. target review, with feedback revisions Dec. latest)
—

Title: C³META: Learning to Expand Capability Frontiers for Open-Ended Compositional Generalization in Programmable Multi-Agent World Models
Lead author: Blake Harrison
Abstract: Open-world embodied teams require continual capability expansion for compositional generalization to unseen objects, tasks, and teammates, yet task-progress valuation and joint-action prediction do not directly quantify the delayed effects of capability interventions on long-horizon team competence. We introduce C³META, an open-ended post-training autocurriculum for learning programmable multi-agent world action models, coupling inverse multi-agent reinforcement learning of meta-utility with simulative generative value learning to optimize expected delayed counterfactual expansion of team capability Pareto hypervolume (TPH). Quality-diverse computational creativity combines combinatorial, exploratory, and transformational objectives with counterfactual evolutionary meta co-play, revising conceptual blends and bidirectional cross-attention memory to construct candidate capability interventions ranked by predicted TPH expansion. An object-centric Bayesian inductive factor-graph transformer represents hierarchical object–agent–world structure as multiscale compositional Gibbs–Boltzmann energy basins in stratified fiber geometry, while language-grounded multi-shot Answer Set Programming (ASP) contracts condition and filter revisable rollouts. Mixed-integer abstract multi-agent approximate dynamic programming selects TPH-expanding options and subgoals before minimizing admissible abstract path costs, while offline and off-policy online learning fits joint dynamics from TPH-prioritized simulated experience, expands joint-action search trees, and backs up feasibility-checked latent-space rollout values to refine policy and continuation-value targets within closed-system hybrid simulation with warp-level GPU parallelism. Under matched budgets across fixed and mobile manipulation, navigation, and routing tasks with human–robot and multi-agent embodied teams, C³META improves in- and out-of-distribution capability compositional generalization, multi-task skill transfer, and natural-language instruction, preference, and constraint following, while enhancing behavioral quality-diversity compared with open-ended autocurriculum and unsupervised environment design baselines.
Target venue: ICML

(still working out the “safe, constrained computational creativity emergence” math on this one deriving from: https://arxiv.org/pdf/2610.03715 - should have coherent by this weekend)
Title: Cellular Graph Field Grammars: Programmable Multi-Agent World Model Belief Flows for Emergent AI Civilizations as Mixture-of-Experts Lead Author: Blake Harrison
Abstract: Open-world embodied agent societies require continual collective capability expansion, yet coherent interaction, role specialization, and cultural transmission do not establish how organizational changes produce sustained progress toward AI civilizations. We introduce Cellular Graph Field Grammars (CGfG), programmable neuro-symbolic multi-agent world action models that learn executable social–physical emergent grammars for open-ended collective learning through contract-constrained recursive rewriting of hierarchical object-centric scene graphs, representing societies as evolving mixtures of specialized experts. Building on versioned symbolic state-space memory, neural cellular updates route guarded production proposals among specialized experts over object–agent–institution subgraphs, while vision-and-language-grounded multi-shot Answer Set Programming couples dialogue, joint option execution, and revisable collective rules. Forward closed-loop hybrid simulation executes recursive productions to predict organizational consequences, while backward abductive reconstruction infers candidate derivations from observed joint trajectories, enabling agents to propose and learn role assignments, coordination protocols, and institutional productions through co-play and joint agent-world co-editing. Quality-diverse evolutionary latent-space approximate dynamic programming uses counterfactual shadow traces to learn meta-utility for combinatorial blending, exploratory search, and transformational grammar revisions by delayed gains in retained collective competence, committing shared updates only after finite symbolic-contract verification and protected-capability replay. Planned matched-budget many-agent Minecraft and hybrid societal simulations compare concurrent agent architectures, fixed institutions, and language-mediated coordination under resource shifts, population turnover, and sequential institutional revisions, measuring collective production, retained capability growth, behavior-grounded specialization, cultural transmission fidelity, rule compliance, and revision persistence.
Target Venue: ICML


Title: CAST-MPC: Safe Explainable Programmable Multi-Agent Visual World Models under Certified Partial Identification
Lead author: Blake Harrison
Abstract: Open-world embodied teams must expand capabilities while resolving uncertain admissibility, yet admissibility judgments based on limited behavioral coverage can exclude safe recomposition through coverage mode collapse or underconstrain and permit catastrophic unsafe joint execution. We introduce CAST-MPC, certified safe programmable multi-agent visual world action models that continually acquires, transfers, and retracts admissibility evidence across shared-parent object–relation––goal–option–value hierarchies under partial identification without using behavioral support density as a proxy for admissibility or feasibility. Vision-and-language grounded meta-contracts specify coupled team constraints as multi-shot Answer Set Programming, that conditions hierarchical option latent-space scenario-tree tube rollouts. Cooperative discovery and interventional red-teaming acquire and challenge invariant mechanisms, while partial optimal transport proposes typed subgraph alignments for evidence transfer licensed by intervention support and explicit identification and confounding assumptions. Checkpointed provenance traces each transfer to its supporting evidence and retracts dependent authorizations when mechanisms or assumptions change. Latent-space approximate dynamic programming optimizes discovery through expected retention, meta-utility value, and preference satisfaction under local-global certification as abductive probability mass inclusion. Planned matched-budget sequential fixed and mobile manipulation and navigation experiments compare safe learning and planning baselines with intervention, multi-task transfer, and provenance ablations on held-out object–task–teammate compositions under adversarial agent and disturbance attacks. Evaluations measure retained executable capability growth, safe discovery yield, false exclusion, preference satisfaction, unsafe joint execution, and retraction robustness under confounding and out-of-distribution mechanism shifts.
Target venue: IROS 


- - -

(Below not yet active preview for next term)

Title: FACTIONS
Lead Author: Blake Harrison 
Abstract:  
- contribution new intrinsic motivation search paper over symbolic programmable computational creativity latent-spaces

Co-creative math representation models procedural imagination + cellular automaton paper concerning multiagent active matter self organization meta contract emergence study for procedural generation through cellular sheaf grammar optimal transport
Target Venue: IEEE CoG


Placeholder for robot imitation learning + imitation IRL with relative RLVR social meta for loosen and solve simpler problems compositionally and then re-contract to hard problem for improved compositional meta-utility value learning through RLHF
Lead Author: Blake Harrison
Abstract:
- contribution new RLHF formulation that can take compositional aspects of existing simulators or video and recompose new capabilities (that result in new emergent skills)
Target Venue: CoRL

Placeholder follow up explainable human-AI paper
Lead Author: Blake Harrison
Abstract: 
- contribution new explainable co-evolving memory architecture and closed-system you can interact with through natural-language

Placeholder for my self explainability paper for multi-agent systems for CoRL.. one will be on multi-agent continual co-adaptation emergent memory retrieval and meta adaptation through meta social contracts emergent dialog using imitation learning (IRL direct meta-utility value) but with explainable interfaces 
Target Venue: CoRL

Title: Mixture-of-Experts Multi-Agent Ensemble Memory for Foundation Model Compression and Distributed Expertise Focus
Lead Author: Blake Harrison
Abstract: - contribution ontological decomposition of latent components of existing world foundation model and LLMs into traceable latent ensemble boosted tree architecture memory for capabilities concept explicit retrieval and blending as distributed multi-agent mixture-of-experts (there is proof multi-agent is mixture-of-experts but not the other way)
Target Venue: NeurIPS Main conference
