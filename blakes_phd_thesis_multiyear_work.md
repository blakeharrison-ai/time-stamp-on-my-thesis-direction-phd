I told my teammate:

Blake Harrison  [8:47 PM]
@chuan166 I missed part of the conversation.. I suggested TD-MPC2 because I thought priyank had trained myopic rollouts not accounting for infinite discounted horizon, telescoping or a terminal cost-to-go approximator. I have had a lot of success using MPC but I do approximate dynamic programming value learning independently and then use that over latent-space MPC (MPPI or CEM).. in that case you can use any time of generator (I go what I am calling our "value-transformer" as simplified Decision-Transformer style generator) integrated into inverse multi-agent MBRL loop.. that works really well.

You can also go for flow actor critic, diffusion actor critic, evolutionary algorithms (I go for these to separate behavioral quality diversity), approximate value iteration with approximate EM formulation, continuous HJB viscocity fixed point contraction, primal dual fixed point contraction, etc. the point is you do some kind of value learning and then you use that in continuous latent-space over rollout. (edited) 
9 repliesPriyank Patel  [8:54 PM]
Thanks for sharing this Blake, like you mentioned currently I am training the model to just predict the next latent state. I haven't considered the approach you mentioned above but will look into it!
Blake Harrison  [8:54 PM]
oh yeah nope
Chi-Yao Huang  [8:56 PM]
Here is a misunderstanding. Currently, we care more about the performance of WM rather than planner. Bad planning performance does not mean WM learn in a bad way. Any kind of planners are fine. The point is how to make sure our WM learn the thing we want.
Blake Harrison  [8:57 PM]
right.. but if you are doing planning during WM latent dynamics learning that impacts it
Chi-Yao Huang  [8:59 PM]
So we not only care the latent dynamic. We care what we want to learn. In Priyank's case, we care if WM learn medium, which any planner cannot show that.
Blake Harrison  [9:00 PM]
You mean apart from value function
[9:00 PM]just the latent transition dynamics
Chi-Yao Huang  [9:02 PM]
You can say that. We are not only focus on latent transition but something else in latent space. In Priyank's case, he want the latent transition AND transition in the medium. In my case, I want the latent transition AND transition in the spatial-aware way.
Blake Harrison  [9:33 PM]
Makes sense. In my case, I want latent transitions AND symbolic–causal action grounding, so embodied teammates can communicate through shared semantic meanings, track versioned joint revisions exactly, and support programmable, safe, constrained emergence.

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

I shared formally in group shared research progress doc:

Title: Universe in a Bottle: Joint Revision Persistence in Programmable Multimodal Neuro-Symbolic Multi-Agent World Models
Lead Author: Blake Harrison
Abstract: Open-world embodied teams require multimodal multi-agent world models that continually learn and revise shared knowledge for open-ended compositional generalization under out-of-distribution shifts. Yet latent adaptation can revive obsolete interpretations or degrade protected capabilities and their supporting knowledge, undermining exact, jointly consistent symbolic revisions. We introduce Universe in a Bottle (UIB), a programmable multimodal neuro-symbolic multi-agent world action model coupling symbolically guided continual learning of vision--language latent dynamics with independently revisable object-centric semantics and meta-utility through versioned symbolic state-space memory within a closed-loop programmable hybrid simulation. Multi-shot Answer Set Programming governs contract-checked local-to-global polygraphic recursive rewriting across capability and knowledge dependencies, committing shared versions after finite verification of declared symbolic contracts. Mixture-of-experts approximate dynamic programming retrieval combines our value decision-transformer-based offline and off-policy online multi-agent inverse reinforcement learning of meta-utility value with evolutionary quality-diverse counterfactual imagination to enhance latent action grounding. Within this formulation, continuous latent-space multi-agent model predictive control generates diffusion-forced, symbolically admissible rollouts in a Gibbs--Boltzmann free-energy landscape of multimodal latent dynamics, where predicate-conditioned cellular sheaf compatibility energies shape basins and abductive probability mass. During revisions, noncommutative entropic optimal transport over density operators on complex Hilbert space uses current sheaf-energy costs to reorganize latent beliefs through many-to-one grounding into revised symbolic basins. Under matched training budgets, UIB outperforms programmable memory and multi-agent multimodal world model baselines in joint-revision persistence, multi-task transfer, and out-of-distribution compositional generalization of team capabilities while preserving protected capabilities and supporting knowledge.
Target Venue: CVPR


Title: Trustworthy, Programmable Multimodal Neuro-Symbolic Multi-Agent World Models for Open-Ended Embodied Teams: A Survey
Subtitle: A Compositional Game-Theoretic, and Offline-to-Continual-Online Approximate Dynamic Programming Perspective 
Lead author: Blake Harrison
Abstract: Open-world embodied multi-agent systems and human–AI teams must continually acquire, revise, and recombine shared knowledge and capabilities through open-ended learning under out-of-distribution shifts in tasks, partners, and environments. Predictive accuracy alone does not establish causal transfer, preserve collective competence after revision, or justify safe execution of newly composed behavior. This survey organizes programmable neuro-symbolic multi-agent world models (PNS-MAWMs) through a taxonomy of multimodal grounding, representation, continual revision, valuation, coordination, and assurance. We examine how learned latent transitions can be coupled to neuro-symbolic causal action grounding, enabling agents to communicate through shared semantic meanings and preserve version-consistent symbolic joint revisions during continued adaptation and recursive rewriting. We trace world foundation model post-training into world action models that integrate prediction with action generation, planning, and control, and compare multi-agent organization with mixture-of-experts (MoE) architectures. A compositional game-theoretic perspective examines capability and team recomposition in cooperative, competitive, and mixed-initiative interactions. An approximate dynamic programming perspective connects offline imitation and inverse reinforcement learning with continual online utility and value learning, model-based multi-agent reinforcement learning, and local–global model predictive control. Two questions guide our synthesis: how to value the delayed effects of acquisition, editing, and selective unlearning on retention and team recomposition, and what transferable evidence supports safe, constrained open-ended capability emergence under natural-language human preferences and constraints. We relate object-centric and relational graph and cellular representations, hybrid simulation, and revisable symbolic interfaces for knowledge, mechanisms, objectives, and constraints to autocurricula, unsupervised environment design, intrinsic motivation, self-play and co-play, generative and simulative generative meta-utility value learning, computational creativity, related procedural generation, team self organization and language games, and quality-diversity capabilities frontier expansion, structural interventional and counterfactual imagination, and human-guided co-creation. Throughout, we distinguish partial observability from partial identification of mechanisms and preferences, and empirical performance from conditional safety guarantees. A reference architecture and evaluation framework address joint-revision persistence, compositional generalization, uncertainty calibration and self-assessment, interventional validation, adversarial testing, constraint adherence, recovery, and human oversight across robotics, autonomous systems, and interactive simulated worlds. We identify open problems in causal semantics abstraction, multi-agent memory and retrieval architectures, safe, constrained compositional generalization, human-directed agent–model–world co-evolution, multi-agent mixture-of-experts and safe, hybrid simulation constrained multi-agent civilizations emergence.
Target venue: CSUR Journal Survey (End of Nov. target review, with feedback revisions Dec. latest)

Title: C³META: Learning to Expand Capability Frontiers for Open-Ended Compositional Generalization in Programmable Multi-Agent World Models
Lead author: Blake Harrison
Abstract: Open-world embodied teams require continual capability expansion for compositional generalization to unseen objects, tasks, and teammates, yet task-progress valuation and joint-action prediction do not directly quantify the delayed effects of capability interventions on long-horizon team competence. We introduce C³META, an open-ended post-training autocurriculum for learning programmable multi-agent world action models, coupling inverse multi-agent reinforcement learning of meta-utility with simulative generative value learning to optimize expected delayed counterfactual expansion of team capability Pareto hypervolume (TPH). Quality-diverse computational creativity combines combinatorial, exploratory, and transformational objectives with counterfactual evolutionary meta co-play, revising conceptual blends and bidirectional cross-attention memory to construct candidate capability interventions ranked by predicted TPH expansion. An object-centric Bayesian inductive factor-graph transformer represents hierarchical object–agent–world structure as multiscale compositional Gibbs–Boltzmann energy basins in stratified fiber geometry, while language-grounded multi-shot Answer Set Programming (ASP) contracts condition and filter revisable rollouts. Mixed-integer abstract multi-agent approximate dynamic programming selects TPH-expanding options and subgoals before minimizing admissible abstract path costs, while offline and off-policy online learning fits joint dynamics from TPH-prioritized simulated experience, expands joint-action search trees, and backs up feasibility-checked latent-space rollout values to refine policy and continuation-value targets within closed-system hybrid simulation with warp-level GPU parallelism. Under matched budgets across fixed and mobile manipulation, navigation, and routing tasks with human–robot and multi-agent embodied teams, C³META improves in- and out-of-distribution capability compositional generalization, multi-task skill transfer, and natural-language instruction, preference, and constraint following, while enhancing behavioral quality-diversity compared with open-ended autocurriculum and unsupervised environment design baselines.
Target venue: ICML

Title: Cellular Graph Field Grammars: Neuro-Symbolic Multi-Agent World Model Belief Flows for Emergent Programmable AI Civilizations as Mixture-of-Experts
Lead Author: Blake Harrison
Abstract: Open-world embodied agent societies require continual collective capability expansion, yet coherent interaction, role specialization, and cultural transmission do not establish how organizational changes produce sustained progress toward AI civilizations. We introduce Cellular Graph Field Grammars (CGfG), programmable neuro-symbolic multi-agent world action models that learn executable social–physical emergent grammars for open-ended collective learning through contract-constrained recursive rewriting of hierarchical object-centric scene graphs, representing societies as evolving mixtures of specialized experts. Building on versioned symbolic state-space memory, neural cellular updates route guarded production proposals among specialized experts over object–agent–institution subgraphs, while vision-and-language-grounded multi-shot Answer Set Programming couples dialogue, joint option execution, and revisable collective rules. Forward closed-loop hybrid simulation executes recursive productions to predict organizational consequences, while backward abductive reconstruction infers candidate derivations from observed joint trajectories, enabling agents to propose and learn role assignments, coordination protocols, and institutional productions through co-play and joint agent-world co-editing. Quality-diverse evolutionary latent-space approximate dynamic programming uses counterfactual shadow traces to learn meta-utility for combinatorial blending, exploratory search, and transformational grammar revisions by delayed gains in retained collective competence, committing shared updates only after finite symbolic-contract verification and protected-capability replay. Training and planning matched-budget many-agent Minecraft and hybrid societal simulations compare concurrent agent architectures, fixed institutions, and language-mediated coordination under resource shifts, population turnover, and sequential institutional revisions, measuring collective production, retained capability growth, behavior-grounded specialization, cultural transmission fidelity, rule compliance, and revision persistence.
Target Venue: ICML

Title: CAST-MPC: Safe, Explainable, Emergent Programmable Neuro-Symbolic Multi-Agent Multimodal World Action Models under Certified Partial Identification
Lead author: Blake Harrison
Abstract: Open-world embodied teams must expand capabilities while resolving uncertain admissibility, yet admissibility judgments based on limited behavioral coverage can exclude safe recomposition through coverage mode collapse or underconstrain and permit catastrophic unsafe joint execution. We introduce CAST-MPC, certified safe programmable multi-agent visual world action models that continually acquires, transfers, and retracts admissibility evidence across shared-parent object–relation––goal–option–value hierarchies under partial identification without using behavioral support density as a proxy for admissibility or feasibility. Vision-and-language grounded meta-contracts specify coupled team constraints as multi-shot Answer Set Programming, that conditions hierarchical option latent-space scenario-tree tube rollouts. Cooperative discovery and interventional red-teaming acquire and challenge invariant mechanisms, while partial optimal transport proposes typed subgraph alignments for evidence transfer licensed by intervention support and explicit identification and confounding assumptions. Checkpointed provenance traces each transfer to its supporting evidence and retracts dependent authorizations when mechanisms or assumptions change. Latent-space multi-agent approximate dynamic programming optimizes discovery through expected retention, meta-utility value, and preference satisfaction under local-global certification as abductive probability mass inclusion. Planned matched-budget sequential fixed and mobile manipulation and navigation experiments compare safe learning and planning baselines with intervention, multi-task transfer, and provenance ablations on held-out object–task–teammate compositions under adversarial agent and disturbance attacks. Evaluations measure retained executable capability growth, safe discovery yield, false exclusion, preference satisfaction, unsafe joint execution, and retraction robustness under confounding and out-of-distribution mechanism shifts.
Target venue: IROS 


- - -

(Below not yet active preview for next term planned but only the self explainability method and FACTIONS are started)

Title: FACTIONS
Lead Author: Blake Harrison 
Abstract:  
- contribution co-creative imitation learning new intrinsic motivation search paper over symbolic programmable computational creativity latent-spaces leverage new QED more stable reformulation with recent research progress

Question: does self supervised pretraining dwarf emergent capabilities vs direct grounding as bottom up (with a plan) vs top down (capture of derivative concepts)
Target Venue: IROS


Placeholder for robot imitation learning + imitation IRL with relative RLVR social meta for loosen and solve simpler problems compositionally and then re-contract to hard problem for improved compositional meta-utility value learning through RLHF for composition capabilities and related knowledge for generalizable skills transfer in open-ended acquisition settings
Lead Author: Blake Harrison
Abstract:
- contribution new RLHF formulation that can take compositional aspects of existing simulators or video and recompose new capabilities (that result in new emergent skills) further exploring our simulative generative value-transformer approach with evolutionary quality-diverse value through learning through hybrid simulation and multimodal action latent space grounding
Target Venue: CoRL

Placeholder follow up self explainable human-AI paper for multi-agent multimodal world models under continuous revision
Lead Author: Blake Harrison
Abstract: 
- contribution new explainable co-evolving memory architecture and closed-system you can interact with through natural-language

Placeholder for my self explainability paper for multi-agent systems for CoRL.. one will be on multi-agent continual co-adaptation emergent memory retrieval and meta adaptation through meta social contracts emergent dialog using imitation learning (IRL direct meta-utility value) but with explainable interfaces 
Target Venue: CoRL

Title: Mixture-of-Experts Multi-Agent Ensemble Memory for Foundation Model Compression and Distributed Expertise Focus
Lead Author: Blake Harrison
Abstract: - contribution ontological decomposition of latent components of existing world foundation model and LLMs into traceable latent ensemble boosted tree architecture memory for capabilities concept explicit retrieval and blending as distributed multi-agent mixture-of-experts (there is proof multi-agent is mixture-of-experts but not the other way)
Target Venue: NeurIPS
