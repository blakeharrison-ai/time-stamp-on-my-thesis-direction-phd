Told my research group openly:

Connection to my general research direction:
Open-Ended Embodied Imitation Learning

(Open-Ended Embodied Learning + Embodied/Robot Imitation Learning)
-----------------------------------

I treat policy optimization as generalized policy iteration (or value iteration in restricted/fixed-policy settings) over an explicit, structured representation, using MBRL to learn emergent action-conditioned latent dynamics from interaction. The broader objective is to learn object-relational, causal/action-effect, and capability structure that can be retained, edited, and dynamically recomposed online. In particular, I am interested in conceptual blending over reusable object–relation–action and capability components: composing compatible pieces of previously acquired structure into candidate capabilities for novel situations, evaluating those compositions and their counterfactual consequences under learned dynamics and value/energy functions, and explicitly verifying their admissibility and feasibility.

Online I use approximate dynamic programming and MPC over an energy-value landscape.
Policy improvement is evolutionary rather than gradient-following:
quality-diversity archives (e.g., QD MAP-Elites with CMA-ES emitters) over
continuous plan parameters, so improvement maintains a diverse frontier of
verified solutions instead of a single descent path. The state substrate
is evolving object-centric and factorized graphs -- factor-graph beliefs and typed scene graphs operating as state-dependent memory (as GNN+transformer representations) -- a learned but construct-constrained memory whose structure can still evolve and emerge. On top of that substrate I learn action-conditioned latent dynamics from interaction (MBRL), supporting counterfactual prediction and the induction and evaluation of structured components -- typed preconditions/effects, options, subgoals, and capabilities over object hierarchical structure i.e. parts, objects, assemblies, affordances, factors (in the factor graph sense) alongside factorization yielding features that are relevant for agent-model--model-world (AMW) improvement. So that the world model (EOG-WAM) can be edited and dynamically recomposed online.

The critical discipline is propose-authorize separation: learned modules only propose and rank, a fixed symbolic layer e.g., ASP (clingo) admissibility plus deterministic numeric feasibility bounds or learned verifier performs admissibility.

This also provides for hybrid simulation (explicit math formulations + learned) in the loop and secondary cadence updates; and externalized simulators like CuRobo, CuMotion, GTSAM (for slam) can operate cleanly in the closed loop under open world partial observability and uncertainty.

Embodied Imitation Learning is the pillar I use explicitly for learning the representation from demonstrations, RLVR or self play, open-ended learning (ACL, UED, intrinsic motivation (the curiosity stuff), co-evolution, etc.) is used to improve the agent for generalization and preparation for adaptation online.

How that instantiates in this pilot
-----------------------------------

Offline embodied imitation on expert demonstrations trains a
procedure-conditioned policy/value model over a causal decision
transformer fused with GTrXL and Mamba-2 memory. The value head regresses a constraint-aware quality-to-go — task return minus a violation/boundary cost-to-go -- a deliberately supervised proxy for the full ADP loop, chosen so the pilot's estimand (does the learned value representation respond correctly at known constraint boundaries?) stays clean and falsifiable. Optimization then moves online in the same propose/verify shape: a deficit-weighted curriculum proposes scenes in weak capability cells; rollouts pass through the ASP verifier and a return-quantile filter
(ReST / expert-iteration style), so only verified, high-quality behavior
is ever imitated; and self-play distillation PEFT-adapts the oracle
reviewer against the verifier's labels. Hard constraints run as a 16-predicate ASP program (clingo, with a deterministic cross-check that
fails closed), layered with real-time integer programming that sets LP
feasibility bounds: the LP relaxation certifies what is geometrically
achievable, the symbolic layer what is procedurally admissible, and their
gap is the formal signal that a learned behavior has been strategically
invalidated. Cosmos3-Nano fills the WAM slot (Cosmos-H-Surgical is the
drop-in oracle id), and cuRobo attaches through the sim-in-the-loop margin
oracle. Receding-horizon MPC under learned dynamics is the FRONTIER core's role; wiring this policy into that loop is the next step — today the
pilot's online stage is verifier-filtered adaptation with early stopping
and best-policy restoration.[4:44 PM]---



Yep, getting some lunch and then generating input video with overlays.



For my research direction I told my PhD advisor:

Hi Yezhou,

I’ll be sharing my ICLR draft with results this week, but I wanted to give you a brief update on the broader direction I think I’ve now converged on.

I think the concept I want to anchor my research around moving forward is Open-Ended Agent--World Co-Evolution through Continual Model--World Editing for Embodied Intelligence (working name). My first paper focuses on mobile manipulation, using RoboCasa and Isaac Lab with Cosmos Policy/CuRobo and UED alternatives, including their corresponding benchmarks and ablations.

POET provides a strong precedent for open-ended co-evolution of environments and agents, while unsupervised and open-ended environment design give me a concrete first testbed for the curriculum-allocation problem. This also seems like a natural continuation from Oak and from offline-pretrained world models toward continual online world-model adaptation and MPC.

I have also been moving toward language-grounded Neurosymbolic Object-Graph World Action Models (NeSOG-WAMs) as the common MBRL/MPC substrate for this direction. The goal is to support agents that continually acquire, retain, and compose capabilities while both their internal models and shared executable worlds can be continually edited and extended, including targeted unlearning when knowledge or capabilities must be removed.

More broadly, I am interested in robust generalization under structural, task, instruction, and dynamics shifts; online adaptation and partial identification; persistent model--world causal admissibility; open-ended capability acquisition and composition; and extended memory and retrieval. Recent work on generalist agents and generative interactive worlds makes this intersection increasingly compelling.

I think the survey can consolidate this direction by connecting open-ended learning and co-evolution, continual model editing and unlearning, hybrid/generative world simulation, embodied robot learning, mixed-initiative and co-creative world editing, imagination augmentation, computational creativity, procedural world generation, and multi-agent emergence around the common problem of persistent agent--world co-evolution.

I see UED, intrinsic motivation, curriculum allocation, self-play/co-play and self-improvement, continual learning, MBRL/MPC, causality, RLVR/IRL, imitation learning, and evolutionary/QD methods primarily as methodological tools within this broader program rather than separate research directions. The main downstream domains I see are mobile manipulation and navigation, UxVs and autonomous vehicles, digital twins, and game/simulation AI.

For the first C³RAFT-X paper, the immediate contribution is much narrower: a UED/curriculum-allocation method for improving robust generalization under distribution shifts in embodied mobile manipulation and navigation.

Going to need to put together clear visuals and references to existing literature intro I think for the slides.

Also relevant: https://cirl.lcsr.jhu.edu/research/hmm/datasets/jigsaws_release/ and https://github.com/NVIDIA-Medtech/Cosmos-H-Surgical. I have a partial PoC demo, but am working on getting my paper drafted / results ready for Friday’s presentation. Will post the demo tomorrow along with slides. If we go the simulation-generation route, my approach could also use language instructions to condition the generation.

# time-stamp-on-my-thesis-direction-phd
Title: C³RAFT-X: Causal Experience Valuation for Recomposable Capability-Frontier Expansion via Approximate Dynamic Programming
Lead author: Blake Harrison
Abstract: Open-ended embodied imitation learning (OE-EIL) for open-world autonomous mobile robotics asks how to allocate offline demonstrations and online interactions for continual learning in World Action Models (WAMs) with persistent, editable, quality-diverse capabilities for language-grounded adaptation and robust generalization under out-of-distribution (OOD) shifts. Existing embodied OEL curricula commonly prioritize regret, progress, novelty, learnability, task relationships, causal alignment, or related proxies. We instead ask whether valuing prospective acquisitions by their delayed causal effect on retained executable-capability frontier expansion improves creative recomposition and compositional OOD generalization. We introduce \textbf{\mbox{C\textsuperscript{3}RAFT-X}}, a finite-horizon approximate dynamic programming (ADP) framework with receding-horizon allocation. Its \emph{retention-weighted interventional capability-frontier advantage} measures the candidate-versus-matched-substitute effect on fixed-reference Pareto hypervolume after $H$ learning steps under adaptive continuation, crediting acquisition, localized revision, retention, and strict zero-update recomposition. \emph{Capability-component niches} bind object--relational preconditions and effects to executable options and subgoals, while Neurosymbolic Energy--Object-Graph WAMs support conceptual blending under four-way grounding of natural-language semantics, structural causal predictions, symbolic admissibility, and abductive feasibility. Counterfactual learner rollouts amortize checkpoint-fork valuation and calibrate against fractal-seeded, meta-conditioned co-play multi-rollouts. Under matched training and scoring budgets, C\textsuperscript{3}RAFT-X improves retained frontier expansion, zero-update creative recomposition, and compositional OOD generalization across long-horizon language-conditioned mobile manipulation and navigation evaluations using RoboCasa365, ManiSkill-HAB, and Isaac Lab Mimic, with complementary ablations using Newton Physics, EnvPool, and Procgen.
Target venue: ICLR

— 
Title: Open-Ended Embodied Imitation Learning: An Offline-to-Online Approximate Dynamic Programming Perspective
Lead author: Blake Harrison Abstract: Open-Ended Embodied Imitation Learning (OE-EIL) for open-world autonomous mobile manipulation and navigation systems---which we introduce as the continual acquisition, composition, editing, unlearning, generalization, and adaptation of executable capabilities from multimodal demonstrations, logs, and experience, toward online-adaptable, admissible behavior, robust OOD generalization, continual capability recomposition, and self-improving, self-reflexive open-world embodied systems---synthesizes literatures spanning open-ended embodied learning, robot imitation learning, and world action modeling. Unlike fixed-task imitation, OE-EIL asks how capabilities persist and expand as worlds, tasks, dynamics, embodiments, instructions, constraints, and preferences change. Partial observability hides state; demonstrations only partially identify goals/rewards and may underdetermine values, dynamics, and skill decompositions. We formalize OE-EIL through offline-to-online approximate dynamic programming, unifying value learning, model-based reinforcement learning, and model predictive control (MPC). Demonstrations and experience from humans, agents, planners, simulators, and environments inform goals, admissibility, preferences, rewards, values, dynamics, capabilities, and representations; World Foundation Models can supply generative priors; parameter-efficient post-training can yield action-conditioned World Action Models (WAMs); MPC closes the prediction--planning--execution loop; and online learning closes adaptation--data acquisition, with simulation and reasoning in the loop. We connect imitation learning with inverse, offline, hierarchical, model-based, and reinforcement learning with verifiable rewards (RLVR), latent actions, neural-filter adapters, inverse graphics, and hybrid simulation. Intrinsic motivation drives exploration; curricula allocate tasks/demonstrations/subgoals; unsupervised environment design generates worlds; quality-diversity maintains repertoires; computational creativity enables combinational, exploratory, and transformational expansion and conceptual blending; and evolutionary RL, self-/co-play distillation, self organization and emergence (e.g. multiagent emergence, adaptive complex systems, synergetics, reaction-diffusion / pattern forming dynamics) around repertoire learning and interactions drive co-adaptation and co-editing. We organize these connections through a reference architecture---language-grounded Neurosymbolic Energy-Object-Graph WAMs (NEOG-WAMs)---integrating abductive learning and ASP; multiscale causal-physical, knowledge, Bayesian/factor, and streaming graphs; object-centric, energy-based, flow, causal, and Decision-Transformer models; spatial graph structures; and affordance--option--capability and part--object--assembly hierarchies for admissibility, reasoning, MPC, editing, and unlearning. Evaluation spans capability-frontier expansion, compositional retention/OOD transfer, uncertainty, safety, adherence, and embodied domains. Finally, we propose agent--model--world co-evolution through continual model--world editing (AMW-MWE). We cover the specific domains of mobile manipulation, UxV navigation (especially humanoid, underwater and aerial), autonomous vehicle systems, and related game AI and procedural world generation. We further explore the domains of autonomous mobile agent safe model editing, mixed-initiative (including co-creative) human-robot settings, and self organizing multiagent AMW-MWE mobile systems. Target venue: CSUR Journal Survey (Oct. target submission, with feedback revisions Dec. latest) —  




Title: Universe in a Bottle: Verifiable Joint Editing of Multiagent Co-Evolving Neurosymbolic Object-Graph World Model---Hybrid World Simulator Pairs
Lead Author: Blake Harrison
Abstract: Neurosymbolic Object-Graph World Action Models (NeSOG-WAMs) are strongly amiable to co-evolve with the hybrid simulators that train them under self-/co-play and improvement—explicit physics and neurosymbolic domain, implementation and generator programs coupled with learned generation under scaled verifiable-reward, proxy policies or direct value loops: a universe in a bottle. Yet editing and unlearning target artifact—the simulator re-teaches what the model removes, the model regenerates what the simulator removes—and address weights or beliefs, not the generative source both compile from; while single-artifact verifiers ignore the closed loop. We introduce Universe in a Bottle (UIB) which the pair itself are considered the joint-edit object under executable-capability value and transformational creativity progression objectives under language-grounded shared editable factorized object-graph meta (OGM) structure. Self supervised multi-agent language games evolve an emergent interaction language that is bound by OGM, whose co-evolved addressable meta-grammar that generates and adapts verified worlds and coupled model-based agents. The grammar is further made intelligible by PeFT latent bridge adaption to a common multimodal embedding space and made answer set program (ASP) compliant through a learned resolver. OGM itself includes addressable primitives, causal preconditions, and compositions. Deductive programs can thus be written adapting the shared configuration of the world and agents. Both members recompile from the edited graph: revision rewrites productions; removal deletes them along with their generative descendents, provenance bounding collateral through recursive lexical analysis. Von Neumann meta classes are further assigned to aggregate groupings based on spectral similarity for addressable class level organizations. Online a universal meta-adaptive controller chooses among, revising, regenerating, and unlearning, deferring transient inconsistency to downstream neural-symbolic MPC that integrates a non-linear kernel projection of the ASP program to fuzzy logic resolve likely adaptive ideal hyper parameter set membership. Open-ended online meta adaptive verification is closed loop: a deductive solver adversarial red-team verifies post-edit rollouts on secondary cadence. Across diverse embodied tasks (navigation, manipulation and automated resource planning) MiniHack, Crafter, IsaacLab-FORGE/Behavior, MineDojo, RoboCasa365, Maniskill-Hab and CARLA; partially observable complex tasks over long-horizons, UIB sustains generation validity, resists relearning attacks that defeat unilateral editing, unlearning, and fine-tuning, and preserves retained executable-capabilities over long horizon multi-step tasks under shifting natural-language instruction, constraints and context—establishing joint editability as a measurable property of model—simulator pairs.
Target Venue: CVPR
—

Title: CAST-MPC: Executable Options and Certified Capability Editing & Retraction under Partially Identified Neurosymbolic 4D Causal Scene Graphs
Lead author: Blake Harrison
Abstract: Neurosymbolic Object-Graph World Action Models (NeSOG-WAMs) give embodied agents language-grounded options, yet expanding options across instances requires knowing which remain admissible under partially identified structure and dynamics. Offline-to-online control penalizes unfamiliarity, not admissibility — dynamic feasibility, constraint-validity, reachability, recoverability — transfer aligns correlated appearance and latent dynamics, not invariant causal structure. We introduce CAST-MPC, a 4D causal-physical scene-graph WAM, transfers admissibility evidence only across causally probed invariant structure child subgraphs inherit from shared parents, enrolling verified options on children and hypothetical compositions of capability-bearing parts, executing only when closed-loop trajectories are admissible under every credible graph–mechanism hypothesis. From RGB-D, language, interaction, bidirectional counterfactual imagination induces credible graph–mechanism hypotheses — object-factorized scene-graph program mixtures instantiating hybrid finite-element–graph-neural simulation — and forward re-simulation reweights them. Newtonian re-simulation verifies dynamic feasibility and answer-set programs constraint-validity, while interventional probes verify invariance of the inherited object–affordance hierarchy — relational structure, features, topology; executable capabilities composed from skills, knowledge, options. Partial optimal transport aligns verified structure across siblings with per-plan provenance; offline, a normalizing flow learns belief-conditioned HJB-viscosity values; online, a learned abduction head predicts membership in the calibrated admissible transport mass, whose density proxies transfer trust-region support, weighting reachable tubes gating Gibbs-energy scenario-tree tube-MPC. Edit contracts invert these flows, propagating revocation through capability cones to re-verification — enrollment and retraction, one transport, forward and inverse. Across Isaac Lab, ManiSkill-HAB, LIBERO, and Infinigen-Articulated, CAST-MPC enrolls options zero-shot, improves task- and instruction-shift generalization, reduces unsafe, irrecoverable executions, and enables recomposition-robust, transfer-preserving retraction.
Target venue: ICML 
—

Title: Neurosymbolic Graph Field Grammars: Learning to Compositional Blend, Explore and Transform Multi-Domain Design Spaces for Procedural 4D Worlds
Lead Author: Blake Harrison
Abstract: Graph grammars are widely used to design large-scale interactive worlds for media and simulation, yet when multiple domains are combined they are often done so in ways that collapse quality-diverse contributions from either. This limits quality-diverse coverage and prevents the grammar itself from adapting as worlds evolve in a transformational creative manner. We introduce Graph Field Grammars (GfG), a semi- and self-supervised neurosymbolic object-graph blending framework that learns a field over typed spatiotemporal graph-rewrite events, with hierarchical latent field-theoretic creation, interaction, and deletion operators for inverse procedural modeling of 4D worlds for blending that are assigned meta object class compositions online through bidirectional procedural generation---reconstruction. GfG operationalizes computational creativity through three coupled processes: blending aligns and recombines motifs across source grammars; exploration uses quality-diversity MPC-based search to discover high-value derivations within the current grammar; and transformation adds, removes, or retypes symbols, productions, and constraints to make previously unreachable world families generable. GfG learns and revises grammars through self-play, self-improvement, and co-creative emergent multi-agent interaction, while a neurosymbolic verifier enforces local geometric and semantic constraints and global topological, physical, temporal, and natural-language context, task constraints, goals and subgoal decomposition descriptions in a hybrid simulator. On the PCG Benchmark and a procedural 4D-world suite implemented in Blender Geometry Nodes and Infinigen, GfG improves valid multi-design-space coverage, controllability, cross-grammar motif retention, and language-conditioned constraint satisfaction over classical and learned graph grammars, Graph and RL based PCG, and quality-diversity baselines. Moreover, GfG further supports local grammar editing and subtree-level revision without retraining from scratch, enabling procedural 4D worlds to blend, explore, and transform multi-design spaces adaptively and dynamically online.
Target Venue: SIGGRAPH (backup IROS)

—

Title: TuRTLE-MEM: Provenance-Closed Voxel Memory Editing and Trajectory Unlearning for Open-Ended Neurosymbolic Graph-based Visual Navigation and Embodied MPC
Lead Author: Blake Harrison
Abstract: Lifelong open-ended robots accumulate unbounded memory that must persist, adapt, and stay editable as maps drift, sensors wear, and objects and instructions change. Object-centric and growing representations rarely address streaming scale, locality precision, or stale-information rollup. We introduce KALEDO-MEM, which folds memory editing and trajectory unlearning into the model predictive control (MPC) loop, adapting residual fidelity and rollup aggregation over a robot's lifetime. A versioned observation–value–action 4D causal scene graph–spatio-temporal action graph (4DSG-STAG), with age-weighted message passing, spans object-indexed multi-SDF voxels and tetrahedrons based on locality, a sparser multi-TSDF interactive layer, and a far-field sparse GNN. Edits block stale retrieval, retract descendant support, and recompute dependent factors; deletion contracts purge descendants; an audit transformer memory logs every edit's factor-graph membership. A compositional energy functional drives differentiable MPC ranking, with learned language-preference and constraint-kernel projections gating cross-layer self-attention, while periodic boosted-ensemble interventional probing resolves contradictions by lead vote. Across OmniGibson/BEHAVIOR-1K, SUMO–OpenStreetMap–CARLA, HoloOcean, nuPlan, Isaac Lab, ManiSkill-HAB, MineDojo stress tests, and OpenStreetMap edits, KALEDO-MEM limits task drift, improves long-horizon compositional reasoning under distribution shift over scene-graph, map-maintenance, replay, editing/unlearning, and streaming SLAM/VSLAM baselines, and better retrieves and retains executable capabilities out-of-distribution on navigation, mobile manipulation, and real2sim2real drone navigation under changing language-conditioned instructions.
Target Venue: IROS (CoRL backup) - revising better title and use World Foundation Model RLVR distillation to NeSOG-WAM and more fundamental memory contribution over graphs (integrating local voxels and global graph) and for multiagents


Title: Placeholder for IEEE CoG Bi-Directional ProcGen paper for improved grounding and admissible MPC
Lead Author: Blake Harrison 
Abstract: ..
Target Venue: IEEE CoG

—

Title: His long term STLDrive work revised
Lead Author: Varun Jammul
Second Author: Blake Harrison
Abstract: his innovations on his long term paper with baselines/world action model + imitation learning I design and setup on autonomous driving
Target Venue: CVPR
NOTE: inspiration was found from Maryland GAMMA group concerning potential red teaming innovation


—

Title: His long term STLDrive work revised
Lead Author: Varun Jammul
Second Author: Blake Harrison
Abstract: his innovations on his long term paper with baselines/world action model + imitation learning I design and setup on autonomous driving
Target Venue: CVPR
NOTE: inspiration was found from Maryland GAMMA group concerning potential red teaming innovation


—

These next two need combined into 
Title: Placeholder for Open-Ended Editing NeSy Multiagent Digital Twin NeSOG-WAM for online adaptive hybrid world sim control Extension work
Lead Author: Blake Harrison 
Abstract: ..
Target Venue: CoRL

Told my advisor:

Hi Yezhou,

I am simplifying my C³RAFT-X paper this weekend around capability-niche advantage and plan to share an updated draft with results this week.

I am also reworking my survey around a single concept that now unifies the papers. The current title is:

Autonomous Robotics: Robust Generalization through Open-Ended Embodied Learning and Model Editing of Neurosymbolic Object-Graph World Action Models — An Approximate Dynamic Programming Perspective

I am introducing NeSOG-WAMs (Neurosymbolic Object-Graph World Action Models) as the organizing model family. I am narrowing the primary robotics domains to mobile manipulation, visual navigation, autonomous vehicles, and UxV autonomy (aerial, underwater, and ground), with Game AI as an additional domain for open-ended learning and procedural world generation.

The core research problems are open-ended capability acquisition; adaptive composition and blending of behaviors, options, affordances, higher-level capabilities, and structured knowledge; and model editing/unlearning for robust and admissible generalization in embodied MBRL/MPC. I am treating adversarial robustness as an extension of the broader robust-generalization problem rather than a separate thesis direction.

Supporting concepts include open-ended curriculum and experience generation (ACL, UED, intrinsic motivation, quality-diversity, computational creativity, imagination, and self/co-play/self-improvement, developmental robotics); continual and multi-agent adaptation (meta-adaptation, co-evolution, composition, and self-organization); and hybrid world simulation and co-creation (procedural generation and mixed-initiative methods).

Best,
Blake

and labmate:

I think my new survey title clearly states my core problem:

Autonomous Robotics: Robust Generalization through Open-Ended Embodied Learning and Model Editing of Neurosymbolic Object-Graph World Action Models — An Approximate Dynamic Programming Perspective

Domains:
(Mobile Manipulation, Visual Navigation, Autonomous Vehicles, UxVs and Game AI for open-ended learning and procedural world generation aspects)

I also changed the subgroup name to APG Robotics & World Models Subgroup to bring in more interest.
—

Title: Hyper-GWLA: Partial-Identification-Aware Hypergraph-Latent Energy Factorization for Inverse World-Language-Action Models

Lead author: Blake Harrison

Abstract: Video world models power embodied planning and control, yet photorealism is not physics: implicit latents entangle credit assignment and encode no mechanism surviving intervention under feasibility or validity constraints, compounding in open-ended autocurricula demanding feasible, reachable, valid goals. We thus introduce Hyper-IWS, a hybrid inverse world simulation that combines tetrahedron splatting with a hypergraph object-construction hierarchy of energy basins mixed via cross-attention. Differentiable inverse rendering and inverse physics reconcile offline video with interactive interventional probing, reconstruction, and transform generation, updating what forward simulation and rendering should do during learning regimes. Inspired by realtime volume rendering, ray casting tetrahedron traversal yields exact segment stratification and sample-matched barycentric probes for scattering and transmittance extinction gradients. Finite video partially identifies dynamics, so an inverse energy landscape retains certified compatible basins with interval-valued flat directions, and decision-equivalence grounding exploits sub-tolerance combinations for online identification. When no basin fits belief below admissible thresholds, typed adequacy alarms certify class failure, not parameter error -- residuals localizing to geometry, dynamics, causal, or agent channels trigger ontology expansion, admitted only after type-checking, compilation, execution, and executor verification. Fine tuned via offline dreaming, deployed with differentiable Model Predictive Control (MPC) that leverages differentiable world simulation during online planning under uncertainty, Hyper-IWS improves long-horizon planning on a variety of embodied tasks including ManiSkill-HAB, Carla and IsaacLab under object-dynamics generalization, and extends to language-conditioned LIBERO; micro-basin recombination generalizes under partial occlusion and partial task acquisition. We further show reduction of imagination hallucination through extended horizon stress tests on Isaac Lab Newton and a path to reintegration back into the video generation process, showing generative generalization, as neural guidance through distillation on WorldScore, and show inverse procedural-program identification from rendered video via Infinigen-Sim.

Target venue: CVPR

—-


NOTE to self, I shared concept generally with lab mate (Arpit) considering admissibility as transport mass. I mentioned I had paper I was working on and trust he isn't doing same work but may have spoken too loud and others in area may have heard. Masters students seem to scalp ideas. Hoping they respect in progress work though for ICRA.

my first paper concept:
Offline-to-online embodied control must generalize beyond offline support under distribution shift, partial observability, and long horizons. Existing methods construct behavior-proximity trust regions before assessing feasibility, constraints, reachability, and recoverability -- conflating novelty with inadmissibility, misidentifying the transported admissible support, and forcing online generate-and-test filtering. Instead, we observe that causal mechanisms are invariant across domains, and model sibling domains and tasks as interventional configurations of a shared learned structural causal world model (SCWM). Causal Admissibility via Structural Transport (CAST) defines admissibility as SCWM-constrained optimal-transport mass between sibling transition occupancies; this support -- not behavior-policy density -- forms the online trust region. CAST-MPC learns object-centric latent dynamics with an SCWM represented as a parameterized dynamic Bayesian factor graph. Under local constraints, decentralized agents self-organize to select symmetry-breaking interventions, generating quality-diverse admissible rollouts through self-play and co-play. Online during infinite receding-horizon planning, CAST-MPC instantiates Gibbs-energy MPPI over the transported admissible support. An amortized inverse causal dynamics predictor abduces exogenous experience transport mass membership -- accepting, repairing infeasible suffixes and rejecting unsupported rollouts in a single forward pass, without costly online deductive solving or post-hoc verification. Under unseen environment and task distribution shift, and partial observability across embodied simulators: IsaacLab, RoboCasa365, MetaWorld+, and OGBench, CAST-MPC reduces constraint violations, improves instruction following by and disturbance-recovery success, and task performance over strong baselines.

I am studying identification and correspondence in open-ended learning
offline-to-online and in addition to UED, coverage and causal admissibility as identification mechanisms I am also exploring:

https://gmail.app.goo.gl/?link=https://mail.google.com&isi=422689480&ibi=com.google.Gmail&ct=sp-stn-b-1&mt=8&pt=9008&cid=6382299652459406484&_fpb=COoGEJIDGgVlbi1VUw==&_cpt=cpit&_iumenbl=1&_iumchkactval=1&_plt=596&_uit=1003&_cpb=1&_fpb=COoGEJIDGgVlbi1VUw==&_cpt=cpit&_iumenbl=



One key major difference is that my method keeps domain constraints constant while generatively grows the frontier online adaptively under admissibility constraints (that are also updated on slower cadence online) during online rollout optimization.

My first paper concept is: Admissibility-Gated Object-Centric Frontier Discovery and Open-Ended Autocurriculum Growth

I came up with the concept from novelty frontier exploration and how PCG always requires second pass and my prior work looking into Neurosymbolic ASP (e.g. NeurASP) and the concept of defining a domain clearly but learning the components and related admissibility (I got this from Bertsekas course); and I got the local-to-global composition from free energy-gibbs formulation of physics "least action principle". I got the one step ADP approach with discounted return formulation and CCM metric flow based learning concept looking deeply into bellman fixed point contraction. Reachability, feasibility, validity and recovery I got from concepts related to APD rollouts. Receding horizon MPC is a book I have and nature extension of ADP to n=k horizons in realtime online. CEM and MPP are the natural implementations of this in continuous spaces. I got evo strategies and evo algorithms integration with flow methods from my work with Kevin Luck and also it is standard in search based procedural content generation. The idea of generating worlds and using that in imagination to co-evolve worlds and agents came from my initial research into how to effectively use symmetry (really now symmetry breaking and correspondence), in our affordance and object centric learning of options and related object factorization (My DARPA risers early concept), and how to abstract features into generalizable components. However, I used ChatGPT to better understand which field I most aligned with given my world model, imagination, etc. focus for my survey and from related works I realized I am in "openendedness" specifically "embodied openendedness". This makes a lot of since being years ago I actually posted the XLand and generally followed this idea of improved curriculum and generalization (task and domain) over the last decade+. Now I understand the field and it makes finding gaps much easier and community notation simpler. 

Generally, I am using LLMs only for information retrieval (e.g. intial surveying space but then looking at references and forward citations and community discussions on thought leaders from there), polishing my writing, generation of math (not formulation and in general I form my own math first and would have it try and match community standards but I know them well enough now), not I use it only to check that my math is "sound, valid, complete, and ideal bounded (or boundable)", and to help with lemma derivations. I don't use it to suggest any components in general but I may use it to say "hey could attention work here like this" as pre-experiment validation. I also ask it to look for any gaps in my logic. Other than that I primarily use wolfram alpha to actually check my math and logic. I also ask it for frontier methods for fixed non-contribution areas to stay up to date on latest, as well as scanning conference/latest works myself. Other than that what I code is AI + me hybrid, where I code alongside it and give language instructions or my method math formulation to generate code. In this case I check all my solutions both manually and with wolfram alpha. I also use "White Mamba" the open source MIT license framework I broke off from my company "Black Mamba" stack that uses a bunch of standard components I build or incorporated from different RL frameworks. I design all of my experiments without AI but have it generate custom visualizations per my explicit direction (mostly code I tweak and modify). I also use it to help me rapidly iterate and setup experiments (per my express configuration) in gymnasium format modified for my actual hypothesis testing. For open-endedness a grand open problem is actually how to benchmark it. So what I do is what Kevin Luck taught me. Take existing environment and modify it for your experiments. I use the LLMs for that. Other than that I am creative and have plenty of cool ideas. Great day to be able to rapidly code them.

My second paper is in "Math Representation Models". When building my own game engine and procedural generation systems for my game company I came across the concept of thinking like an architect and using grammars to procedurally generate worlds. I then found infinigen I linked to the group for all to use. I take the concept to the idea of "Procedural Imagination" whereby I first construct a procedural graph and then generate it. Then I do grammar grounding through self play. (grammar here being math formula understanding of topology (in the compute geometry sense), and interactions. So for me it is basically the mathmatical expression of the relationships described clearly and the graph construction in all my papers is inductive (few graph construction methods seem to be); this is inverse reconstruction. I don't do reconstruction. I generate the world and then cheat. I learn the exact math I used to build it and then generalize to similar clusters as a form of semi-supervised learning. That way I can use general math to generate general cool things I can then consider for future auto curricula work.

I also see admissibility as local-to-global composition (I got the term composition from chatgpt but I was calling it local-to-global coherence prior). The idea is not only composition of hierarchies but in my definition local rules that self organize into global admissibility defined by ASP or language in general. Or possibly even itself constract language emergent. That is an area of multiagent systems I am beginning to look more into now.

Made firm commitment to advisor:

Going bottom up + survey I have come to realize I am working on embodied openendedness. I read POET and the most recent ACCEL papers on autocurriculum and have a better grounding there.

The question I have been trying to answer is this:
Instead of what emergence asks (e.g. emergent procedural imagination): How is global structure able to emerge from local self organization (composition e.g. symmetry breaking, flocking, unique unforeseen complex higher order combinations of local rules, etc.)?

I have been trying to solve:
How does global structure emerge from local self organization without violating global constraints or limiting the coverage of emergence (especially online and dynamic OOD)?



I think however, I figured out how to respond in turn to the question now.

I compiled all of my strongest concepts into 3 potential publications (and from there I am rewriting everything bottom up):


SOLA-MPC (cooler named CoCa-MPC) | a new autocurricula/UED style method for ICRA that directly solves the question using my system, which includes abductive learning + MPC and multiagent counterfactual imagination for emergence
Contractual Active-Matter Frontier Memory for Open-Ended Embodied Exploration | my long time coming intrinsic motivation work for ICLR
UIB: Universe in a Bottle | It is math representation models using inverse procedural generation and then meta adaption via procedural imagination as heavy hitting paper for WACV or CVPR


My WIP CSUR survey: From Objects to Worlds: Object-Centric Interactive World Simulators for Open-Ended Embodied Agents

Just wanted to give you heads up so you weren't blindsided these are works results I am bringing for July + hard targets. I also have been in communication with Varun and both him and Josh are waiting to give feedback. Chitta also was interested in #1 (he told me to send him draft after the whole free Gibbs energy concept become something) and Ben Zhou as new reasoning faculty may be interested as well. I think lots of folks will be interested in these but I need to write up clean and make sure the experiments are solid. (edited) 
Blake Harrison  [11:45 AM]
I'll share draft / results for #1 next week and am pushing to have full drafts for 1 and 2 by July meet alongside survey draft and hopefully early improvement results for #3 also by then.


The follow up thrice papers are:

1. Extending SOLA-MPC to belief flow formulation and extended use
2. Combining these two papers as single application meta adaptive co-evolution paper (online better agents + better worlds). Got this idea from how Genie3 + SIMA2 showed strong improvements in complex spaces via dreaming
3. I have a concept of Factions and complex agent self organizations for IEEE CoG paper.

Computational biology/chemistry is naturally on my radar using a "Periodic table" of grammars predefined with lose coupling similar to HTNs + GOAP using ASP. These are more structural adaptions of the principled concept. I am also exploring electrodynamics in principle, reaction-diffusion, hodges decomposition, etc. as self organization / symmetry correspondence and breaking mechanisms as well as improved curiosity/novelty mechanisms for improved frontier graph construction. The real area I want to dive deeper into though is curriculum generation and adaptive learning online through self play and self improvement. I believe that is how we can get to truly self reflexive systems and emergence that is safe/preference and constraint aligned and interesting (i.e. more diverse and dense in terms of diversity and online adaptive procedural worlds that are long horizon physically consistent).

Right — the top-level research direction and three subdirections are:
Top Research Direction
Online Adaptive Embodied AI Open-Endedness
Object-centric world simulators, embodied agents, admissibility mechanisms, memory systems, language/grammar grounding, and multiagent social structures adapt online to expand robust embodied competence beyond behavioral support.
Concrete SOLA-MPC spine:
world simulators propose
→ intrinsic motivation / memory prioritizes
→ admissibility certificates authorize
→ MPC executes
→ frontier ledger updates support
→ agents, worlds, grammars, and simulators improve online
Three Subdirections
1. Object-Centric Interactive World Simulators, Coevolution, Self-Play, and Self-Improvement
Worlds, agents, object ontologies, affordances, relations, interventions, and simulators co-evolve through object-centric procedural imagination, self-play, and online self-improvement.
Includes:
object discovery
object ontology formation
affordance learning
scene graphs / object graphs
relation graphs
interactive world simulators
procedural world generation
world-agent coevolution
multiagent emergence
self-play
simulator self-improvement
emergent object societies
social communication contract emergence
VLM/VLA grounding
game AI / robotics / PCG simulators
Core question:
How do object-centric simulators generate new worlds, tasks, relations, affordances, interventions, agents, and social/communication structures that co-evolve with embodied learners?

2. Admissible Open-Ended Frontier Discovery, Autocurricula, UED, and Procedural Imagination
POET / PAIRED / ACCEL-style environment and task generation, reframed around admissible frontier growth rather than only novelty, regret, or learning progress.
Includes:
UED
POET
PAIRED
ACCEL
PLR
minimal criterion learning
quality diversity
novelty search
procedural imagination
graph grammars
WFC
L-systems
ASP-constrained generation
grammar grounding
language grounding
certificate-gated curricula
support-growth frontier
online frontier ledger
offline-to-online MPC
Core question:
Which generated worlds, tasks, relations, interventions, plans, and communication/grammar structures are admissible enough to enter the autocurriculum or MPC control loop?
Key claim:
Admissibility is the minimal criterion for open-ended embodied frontier growth.

3. Intrinsic Motivation, Curiosity, Memory Retrieval, and Self-Organizing Representations for Robust Embodied Generalization
Intrinsic motivation and memory decide which admissible frontiers are interesting, useful, novel, learnable, recoverable, worth revisiting, or worth rejecting.
Includes:
intrinsic motivation
curiosity
learning progress
novelty
uncertainty
memory retrieval
frontier memory
episodic memory
rejection memory
support buffer
graph memory
GTrXL / Transformer-XL
Mamba / SSM retention
retrieval-augmented memory
self-organization
symmetry breaking
correspondence learning
local-to-global composition
Hodge decomposition
energy-based formulations
field / electrodynamics correspondence
grammar and language grounding
multiagent communication memory
social contract memory
Core question:
How do embodied agents prioritize, remember, retrieve, repair, and generalize from admissible frontier experiences over long online deployment?
One-Sentence Synthesis
My research studies Online Adaptive Embodied AI Open-Endedness: object-centric world simulators generate evolving worlds, tasks, agents, relations, affordances, interventions, grammars, and social communication contracts; admissibility-gated frontier discovery decides what may enter the autocurriculum or MPC loop; and intrinsic motivation plus frontier memory drives robust embodied generalization through self-organizing, local-to-global representations.






I have studied SSM (Mamba 2) + GTxRL and other transformer architectures as a history log memory but feel extended forms of memory (e.g. transformer + neural turing machines NTMs), in conjunction with admissible emergence is going to yield ever expansive semi-autonomous systems.




My second

AANd I finally understand my research direction / community now..

Open Ended Learning for Object-Centric Embodied Agents using Interactive World Generators


Question:
Can open-ended learning + memory + imagination make language-guided long horizon embodied model predictive control (planning) robust to OOD?

Thesis statement:

Here is my final direction I told my PhD advisor:

I realized this week that I have been maximizing systems when I need to think in terms of core claims, clear gaps, and minimal contributions with maximal yield — claims I can defend with references, empirical evidence, or math.

My current view is that CoCa-MPC is best positioned for RA-L → ICRA. I am narrowing it around one core problem gap: behavioral support does not entail admissibility, and admissibility does not entail behavioral support, especially under OOD/distribution shift. My plan is to build the paper around a single proof of that gap plus a small robotics simulation experiment this weekend, then share it with Josh for a first round of revision.

I also realized that what I was calling language-guided co-creation is more of an application domain than the core technical identity of the work. My actual communities are model-based RL/MPC — especially the offline RL or evolutionary-algorithms-to-online ADP/MPC line — open-endedness, and embodied AI / robot learning, specifically embodied open-endedness.
The thesis-level question I am converging on is:
Can certified semantic imagination enable vision-and-language grounded embodied agents to achieve robust, diverse, constraint-respecting long-horizon generalization under OOD/distribution shift, while mitigating negative transfer, hallucinated futures, and compounding model error?
By certified semantic imagination, I mean causally grounded, admissibility-gated, language-guided world-model planning sourced by open-ended semantic frontier generation — including semantic autocurricula, multiagent emergence, co-evolution through world-model/agent self-play and self-improvement, curiosity, and self-organization within imagination and offline blending — recomposed from structured memory, and committed to action through robust MPC (planning).

This is the single axis that I think everything I am working on fits under. I can measure it through custom modified embodied simulators, VLA/VLM+MPC benchmarks — including OOD benchmark performance, negative-transfer measures, safety compliance, language-command following, hallucination rate, compounding model-error effects, and long-horizon success — and PCG-style settings where constraints and diversity are clear empirical wins.

It can also be framed two ways: first, as improved agents through learned world-simulator imagination plus memory; second, as hybrid learned/externalized world simulators for validating existing VLA/VLM+MPC agents. I have the ICLR, WACV Round 2, AIIDE, RA-L → ICRA, and CSUR survey narratives updating along this line.

I am also changing my workflow to a quick single-claim + proof + experiment iteration mode, so I should be able to show convergence more regularly and quickly. This week I am sharing the narrowed CoCa-MPC version with Josh, and after I get his revisions I will share it with you.


----
These were prior concepts or mechanisms supporting this leading up to it:

Language ground and symbol grounding also

Subject: Research framing: embodied open-endedness, world simulation, and VLM/VLA evaluation

Hi Professor [Name],

I wanted to share a clearer framing for the survey paper and the WACV / AIIDE / ICLR line of work.

The umbrella term I am converging on is open-endedness, with the more specific sub-area being embodied open-endedness. The concepts I have been circling around — automatic curricula, co-evolution, curiosity, imagination, memory, world models, and learned/hybrid simulators — all fit more cleanly under that framing.

My current thesis is that world simulators can serve two connected roles for embodied AI and foundation models:

1. Evaluation: build hybrid learned evaluation environments for VLMs / VLAs, similar in spirit to MineDojo, but focused more directly on modern embodied foundation models. The goal would be to expose long-horizon planning failures, hallucination, weak grounding, constraint violations, and robustness gaps.
2. Improvement: use world simulation inside imagination / dreaming / memory-augmented learning loops. This connects to Dyna-style methods, active inference / imagination-based learning, curiosity-driven exploration, and model-predictive or ADP-style online optimization. The longer-term direction is to use these mechanisms to generate better latent exploration, better imagined rollouts, and eventually more reliable constraint-aware behavior.

The practical reason this direction feels unusually strong for me is that it also aligns with what I am building professionally through Here Be Giants. The company is effectively a world simulation company: generating large-scale synthetic environments and production-grade simulation assets, with overlap between training simulators, embodied AI environments, game-engine infrastructure, and VFX tooling. I am already doing a scaled production version of this work through my own AA-scale engine work and Unreal-based simulation pipeline. That gives me a concrete systems substrate rather than only a conceptual research direction.

This also clarified something important for me methodologically. I have been thinking too much in terms of maximal systems. I now understand the research process more cleanly as making minimal, testable claims, identifying precise gaps, and validating each step empirically, mathematically, or through prior work. So instead of trying to prove the entire world-simulation vision at once, I want to decompose it into smaller claims that can support a coherent PhD trajectory and a series of publishable papers.

My rough mapping is:

* Survey paper: open-endedness / embodied open-endedness taxonomy.
* WACV: hybrid learned evaluation for VLMs / VLAs and long-horizon embodied failure modes.
* AIIDE: procedural / simulated world generation as an open-ended curriculum and evaluation substrate.
* ICLR: imagination, memory, world simulation, and control/planning as a learning architecture.

I spoke with Josh and am aiming to get first early empirical results out this week. After one polish pass, I will send you the WACV draft. I think the first round may still be possible, but the second round is the safer target.

Best,
Blake

Model-based RL → vision-language-grounded MPC → extended to multi-agent teams via compositional causal world models and composable admissibility constraints. Validated in game AI (composition at team scale), dyadic human-machine teaming on mobile manipulation/navigation (admissibility with an uncontrolled teammate), and procedural content generation (isolating the composition property).

Compositionality, Emergence, and Self-Organization within Safe RL (offline-to-online, MPC-based constrained MARL/MAP).
My methodological stance is that in multiagent planning and MARL the right simplification is structural, not reductive: rather than simplify away partial observability, non-stationarity, long horizons, distribution shift, or strategic interaction, I seek the local mechanisms that make global coordination composable — a compositional analogue of scaling laws, in which complexity grows gracefully with the number of agents, tasks, and environments. Concretely, the thesis — the hypothesis I am currently working toward — is:

In multiagent embodied systems, staying within the support of training behavior is neither necessary nor sufficient for a team to act admissibly under distribution shift and over long horizons. I argue that admissibility must instead be engineered compositionally, and I introduce local interaction mechanisms — topological belief graphs, relational fields, emergent grammars, and self-organization rules — that serve as local admissibility contracts and, under explicit decomposability and bounded-interaction assumptions, compose into team-level admissibility through an inductive, parameter-shared construction whose cost grows gracefully with the number of agents. The distinction is load-bearing: emergence constructs the grammar and causal relations in which contracts are framed — induced from counterfactual imagination during self-play — and shapes the conduct within the certified set, but emergence only ever proposes; the verifier certifies each contract against fixed domain rules, and compositionality assembles the certified contracts into the team guarantee — so a team can discover its constraints emergently yet never acts outside a composed, verifier-carried admissibility. The agents I design are trained by self-play and model-based self-improvement through imagined rollouts in a learned world model — from which the inductive causal graph and a symbolic intervention grammar are themselves constructed by counterfactual imagination and grounded both in fixed domain semantics, for soundness, and in vision-and-language, so that perceptual evidence and human commands map into the same admissibility grammar — and they move from offline reinforcement learning to online model-predictive control, carrying that emergent, grounded graph-and-grammar into receding-horizon planning alongside the behavior policy, so that admissibility is maintained by planning over contract-compatible futures beyond the empirical data rather than by staying within it. I engage strategic interaction structurally rather than reductively — certifying admissibility robustly against a bounded set of teammate behaviors not ours to constrain, rather than presuming a shared objective — while strategic exploitation and co-adaptation remain scoped future work. I validate this on embodied multiagent teams across three domains — game AI, vision-and-language embodied mobile manipulation, and procedural generation — testing whether admissibility and composition hold as teams scale; human-machine teaming is the multiagent extension configuration in which the uncontrolled teammate is a human who acts and instructs through language, and procedural generation isolates the composition property itself.
More technical version:

A team of embodied agents behaves admissibly when its joint belief-conditioned trajectory remains within a specified set of acceptable team-level outcomes — including task satisfaction, natural language or communicated commands, constrained belief flow, intent alignment, and safety specifications — throughout an extended horizon and under distribution shift. This thesis argues that confinement to the support of the training-behavior distribution is neither necessary nor sufficient for admissibility so defined: agents may satisfy the specification while acting outside that support, and may violate it while remaining within it. I therefore treat admissibility as a property to be constructed rather than inherited from data coverage, and derive sufficient conditions under which the local admissibility of individual agents, composed through a small set of local interaction mechanisms — topological belief graphs, relational fields, emergent grammars, and self-organization rules — implies global team admissibility under explicit decomposability and bounded-interaction assumptions. To realize these conditions, each engineered agent is trained by self-play and model-based self-improvement, using imagined rollouts in a learned world model to evaluate contract-compatible futures beyond the empirical support, and transitions from offline reinforcement learning to online, receding-horizon model-predictive control; admissibility is thus maintained by planning over trajectories that extend beyond the data while satisfying local admissibility contracts, rather than by remaining within the data. I evaluate the resulting teams on game AI and on multi-robot navigation and manipulation, extend the analysis to human-machine co-creation — where admissibility must be maintained, or violations detected, under an exogenous teammate the framework does not directly constrain — and isolate the composition property in a controlled procedural-generation setting that removes embodiment and perception confounds.

Told my advisor:

Just FYI — I'm framing the work around multi-agent Human–Machine Teaming, since it seems to be the strongest long-term research direction and gives the experiments a clearer organizing structure.

Going back through my partial drafts from the past couple of years, I've consolidated them under a single organizing idea — team admissibility — that threads through intent alignment, safety, and vision-and-language multiagent cooperation, now connecting around ten works (I have specific gap and proposed framework they all focus on concerning admissibility but it's easier to share with the drafts). My immediate focus is one paper at a time, starting with the WACV work and the CSUR survey. WACV Round 1 is my ideal near-term target (the Round 1 deadline looks to be around mid-July), with Round 2 in the early fall as a backup, depending on results and collaborator feedback.

Mostly just focused on experiments and refining those drafts now over summer through next spring (there are 5+the survey). Plan on sending out drafts to collaborators as experiments are there and they are ready for feedback. (edited) 
Blake Harrison  [6:05 PM]
It looks like the lineage I’ve followed is model-based RL → vision-language-grounded MPC, so my cleanest baselines are VLAs (the paradigm) and in-family world-model MPC like VLMPC and GWM-MPC (the real contribution comparison), with VLM ablations as motivation. My method is VLM + world-model MPC, with the compositional-causal world model and composable admissibility as the novelty. Framing it this way keeps a much cleaner community narrative and grounds my terminology in a single community.
Blake Harrison  [6:17 PM]
VLM pretrained or Peft tuned + my novelty* + MPC. Not generic:

Vision-language-grounded world-model MPC for embodied agents, using self-organized local-to-global admissibility constraints to improve robust long-horizon planning under distribution shift.

I use multiagent dreaming to emerge a grammar that connects to general ASP framing so that grounding is done via dreaming (imagination during self play). That's the paper I have been working on all term. The framing was really difficult to get right.

Composition (local-to-global) constraint adherence, self organization (eg electrodynamics, multiagent, swarms), admissibility (viability, feasibility, reachability, repair) = better intent alignment (NL command following) + safety measured via VLA benchmarks like RoboCasa, with VLM/component ablations, hard constraints via PCG tests (like Sudoku and Minecraft benchmarks), and narrative framing is easy to explain HMT dyadic (dynamic and adaptive new human commands or interactions with single agent) and future work extends clean to multiagent (what I meant by belief flow POSG extensions). That's the path I have been trying to fit.

Makes sense the community like Sergey Levine moved from Offline RL -> VLAs. VLM+MPC just become a thing. So I have a clean history of methods to visualize in my survey also.

Anyways just wanted to give you high level before sharing my experiment results soon and how it connects to survey. (edited)

\documentclass[10pt,letterpaper]{article}

% Generic Overleaf / pdfLaTeX-compatible preamble.
% Compile with: pdflatex main.tex
\usepackage[margin=0.95in,top=1.05in,bottom=0.85in]{geometry}
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage{lmodern}
\usepackage{microtype}
\usepackage{graphicx}
\usepackage{array}
\usepackage{booktabs}
\usepackage{longtable}
\usepackage{makecell}
\usepackage{enumitem}
\usepackage{xcolor}
\usepackage{xurl}
\usepackage[hidelinks]{hyperref}
\usepackage{tikz}
\usetikzlibrary{arrows.meta,calc,fit,positioning,backgrounds}
\usepackage{titlesec}
\usepackage{fancyhdr}
\usepackage{ragged2e}
\usepackage{etoolbox}

% Better line breaking for long URLs and dense prose.
\Urlmuskip=0mu plus 2mu
\emergencystretch=3em
\hypersetup{
  pdftitle={Biggest Cross-Cutting Problems in Multiagent Human-Machine Teaming, Co-Creation, HRI, and Multiagent Systems},
  pdfauthor={ChatGPT Deep Research},
  pdfcreator={LaTeX conversion}
}

\pagestyle{fancy}
\fancyhf{}
\renewcommand{\headrulewidth}{0pt}
\cfoot{\thepage}

\setlength{\parindent}{0pt}
\setlength{\parskip}{0.60em}
\setlist[itemize]{leftmargin=1.4em,itemsep=0.15em,topsep=0.25em}
\setlength{\tabcolsep}{3.5pt}
\renewcommand{\arraystretch}{1.28}
\sloppy

\titleformat{\section}{\Large\bfseries}{}{0pt}{}
\titleformat{\subsection}{\normalsize\bfseries}{}{0pt}{}
\titlespacing*{\section}{0pt}{1.05em}{0.42em}
\titlespacing*{\subsection}{0pt}{0.9em}{0.25em}

\newcommand{\sourcemark}[1]{%
  \textsuperscript{\tikz[baseline=(m.base)]\node[fill=black!8,circle,inner sep=1.25pt,font=\tiny] (m) {#1};}%
}

\newcommand{\sourceitem}[2]{%
  \par\noindent\sourcemark{#1}\hspace{0.45em}{\footnotesize\url{#2}}\par\vspace{0.30em}
}

\newcommand{\docmark}{%
  \begin{tikzpicture}[x=1em,y=1em,baseline=-0.45em,line width=0.115em,line cap=round,line join=round]
    \foreach \a in {0,60,...,300}{%
      \begin{scope}[rotate=\a]
        \draw (0,0) .. controls (0.55,0.05) and (0.83,0.38) .. (0.82,0.78)
              .. controls (0.80,1.08) and (0.53,1.28) .. (0.25,1.31);
      \end{scope}%
    }
  \end{tikzpicture}%
}

\newcommand{\problempara}[3]{%
  \par\noindent\textbf{#1. #2.} #3\par
}

\begin{document}

{\Large\bfseries \docmark\hspace{0.55em}ChatGPT}\par\vspace{0.75em}

{\fontsize{19.7}{25}\selectfont\bfseries Biggest Cross-Cutting Problems in Multiagent\\[0.25em]
Human--Machine Teaming, Co-Creation, HRI, and\\[0.25em]
Multiagent Systems\par}

\section*{Thesis General Direction}

In multiagent embodied systems, behavioral support is neither necessary nor sufficient for admissibility under distribution shift and extended horizons. This thesis develops constructive admissibility mechanisms — topological belief graphs, relational fields, emergent grammars, and local self-organization rules — that constrain learned behavior so local interactions compose into globally admissible team behavior.

Documenting Red Teaming verification and repair, reachibility, feasibility and repair so I remember to integrate

\section*{Executive summary}

Across human--machine teaming, co-creation, human--robot interaction, and multiagent systems, the hardest problems are no longer best described as isolated model-accuracy problems. The field has increasingly reframed them as \emph{coordination and governance problems in sociotechnical systems}: agents must coordinate under uncertainty, maintain common ground with humans and unfamiliar partners, fail safely, remain supervisable, and operate within workable legal and organizational structures. That shift is visible in the move from ``machine behaviour'' and ``cooperative AI'' research agendas to lifecycle risk-management frameworks and new teamwork benchmarks (Rahwan et al., 2019; Dafoe et al., 2021; National Academies, 2022; NIST, 2024). \sourcemark{1}

My ranking below prioritizes problems by cross-domain harm potential and by the size of the gap between deployment speed and research maturity. The top eight are: safety assurance; common ground and intent alignment; robust coordination in open teams; trust calibration and controllability; human agency, workload, and skill retention; evaluation and reproducibility; accountability/privacy/IP governance; and bias, value pluralism, and vulnerable-user harms. In co-creation specifically, the evidence is especially clear that AI can increase average output quality while narrowing diversity and weakening creative agency when humans are reduced to editors rather than genuine collaborators (Doshi and Hauser, 2024; McGuire et al., 2024). Meanwhile, MARL/HMT benchmarking work shows that claimed progress is often fragile, poorly standardized, or insufficiently ecological (Bettini et al., 2024; Poelitz et al., 2026; Wang et al., 2026). \sourcemark{2}

A practical conclusion follows. The next wave of research should optimize less for isolated task success and more for \emph{team complementarity under uncertainty}: explicit goal and intent representations, human-interpretable inter-agent communication, compositional safety cases with runtime monitoring, adaptive autonomy that preserves human capability, and benchmarks that measure teamwork processes, not only outputs. Regulatory work is also converging on this lifecycle view, through NIST's cross-sector profile, the EU AI Act timeline, U.S. accountability guidance, and copyright/privacy guidance for generative systems. \sourcemark{3}

\section*{Framing the problem space}

I treat HMT broadly as interdependent work by one or more humans and one or more AI agents or robots toward shared goals; because the application domain is unspecified, the analysis emphasizes cross-domain problems that recur in transport, healthcare, industrial robotics, public-sector decision support, and creative workflows. The same families of failure become more severe in safety-critical settings, where human oversight, safety culture, privacy, and liability cannot be treated as afterthoughts, as illustrated by the Tempe ADS fatality, healthcare/social-robot privacy concerns, and updated robot-safety standards. \sourcemark{4}

\clearpage
\section*{Prioritized cross-cutting problems}

\problempara{1}{Safety assurance and graceful failure}{\textbf{Definition:} the inability to guarantee safe behavior when humans, robots, and software agents interact under distribution shift, sensor error, adversarial conditions, or degraded human attention. \textbf{Why it matters:} in HRI and HMT, failures can become physical injury or death; in general MAS, latent coordination failures scale with the number of interacting components. \textbf{Key subproblems:} runtime monitoring, safe handoff, compositional verification for learned components, cyber-physical security, and standards for open/shared workspaces. \textbf{Real-world impact:} the Uber Tempe ADS crash combined failed pedestrian classification, a design that precluded emergency braking, inattentive human oversight, and inadequate safety culture; newer A3/ISO robot-safety work now treats cybersecurity vulnerabilities as physical safety hazards and highlights gaps for humanoids and dynamically stable robots. \textbf{Open gaps and directions:} compositional assurance cases for team behavior, runtime ``safety shields,'' interaction-failure scenario libraries, and standards tailored to open human-shared environments. \textbf{Representative refs:} NTSB (2020), National Academies (2022), Kouvaros et al. (2024), Garg et al. (2024), A3/ISO (2025--2026). \sourcemark{5}}

\problempara{2}{Common ground, shared mental models, and intent alignment}{\textbf{Definition:} failures to maintain shared beliefs, assumptions, goals, capabilities, and situational awareness across humans and agents. \textbf{Why it matters:} high-performing teamwork depends less on raw intelligence than on whether partners can coordinate, repair misunderstandings, and anticipate each other. \textbf{Key subproblems:} referential grounding, intent communication, shared displays, bi-directional explanations, role-aware information presentation, and explicit goal articulation. \textbf{Real-world impact:} the National Academies note that ad hoc teams often differ in training, terminology, timelines, and authority, degrading cohesion and trust; recent work on language-grounded MARL and common-ground benchmarking shows that current systems still diverge from human collaborative norms. \textbf{Open gaps and directions:} shared-state representations, repair-aware interfaces, human-readable agent protocols, and benchmarks that directly test common ground rather than only task completion. \textbf{Representative refs:} National Academies (2022), Endsley (2023), Bansal et al. (2024), Li et al. (2024), Poelitz et al. (2026). \sourcemark{6}}

\problempara{3}{Robust coordination and generalization in open teams}{\textbf{Definition:} the inability of agents trained in fixed settings to coordinate with novel teammates, changing team sizes, partial observability, and limited communication. \textbf{Why it matters:} real deployments are open systems, not closed training populations; agents must work with unfamiliar humans, third-party robots, or other organizations' agents. \textbf{Key subproblems:} ad hoc teamwork, partner modeling, non-stationarity, sparse credit assignment, emergent conventions, zero-shot coordination, and distribution shift across social situations. \textbf{Real-world impact:} NAHT explicitly uses autonomous-driving and heterogeneous-team examples to show why classical ``all agents under one controller'' assumptions break down; Melting Pot and SMACv2 likewise show that older benchmarks can overstate progress and under-test closed-loop social generalization. \textbf{Open gaps and directions:} open-team training curricula, diverse partner generation, uncertainty-aware teammate models, and standardized large-scale ad hoc teamwork infrastructure. \textbf{Representative refs:} Dafoe et al. (2021), Leibo et al. (2021), Ellis et al. (2023), Wang et al. (2024), Wang et al. (2026). \sourcemark{7}}

\problempara{4}{Trust calibration, transparency, and controllability}{\textbf{Definition:} humans over-rely, under-rely, or misunderstand agents because interfaces do not properly communicate confidence, intent, limits, or control boundaries. \textbf{Why it matters:} the goal is not maximum trust, but well-calibrated trust and meaningful control. \textbf{Key subproblems:} prospective versus retrospective explanations, mode awareness, adjustable autonomy, trust repair, dependence versus trust, and the side effects of anthropomorphism. \textbf{Real-world impact:} transparency/explainability are identified as mechanisms for improving situation awareness and performance, yet recent experiments show design effects can be counterintuitive: lower-explainability teammates were sometimes perceived as more trustworthy or competent, and proactive robot behavior can improve efficiency while also creating expectation-management problems. \textbf{Open gaps and directions:} uncertainty communication, longitudinal trust measures, adaptive explanation, and interfaces that expose both capability and authority boundaries. \textbf{Representative refs:} National Academies (2022), Endsley (2023), Hauptman et al. (2024), Jamshad et al. (2024). \sourcemark{8}}

\problempara{5}{Human agency, workload, skill retention, and role design}{\textbf{Definition:} poor task allocation can trap humans in brittle roles---passive monitor, answer-checker, exception handler, or post-hoc editor---causing overload, boredom, deskilling, or reduced ownership. \textbf{Why it matters:} teaming quality depends on whether humans remain capable, attentive, and willing to intervene. \textbf{Key subproblems:} level of automation, timing of control transfer, routine-versus-failure workload, cognitive offloading, authorship/ownership in co-creation, and training requirements. \textbf{Real-world impact:} HMT literature identifies skill retention and resilience as open gaps; workload changes under autonomy failure are substantial; in co-creation, people are less creative when placed in an editor role than when they genuinely co-create; and GenAI studies report that higher confidence in GenAI is associated with less critical thinking. \textbf{Open gaps and directions:} adaptive autonomy that preserves skill, participatory role design, mode-switches keyed to cognitive state, and co-creative interfaces that preserve self-efficacy and authorship. \textbf{Representative refs:} National Academies (2022), Xu et al. (2023), McGuire et al. (2024), Lee et al. (2025), Doshi and Hauser (2024). \sourcemark{9}}

\problempara{6}{Evaluation, benchmarking, and reproducibility}{\textbf{Definition:} the field lacks stable, comparable, ecologically valid ways to measure team quality across technical, human, and governance dimensions. \textbf{Why it matters:} weak evaluation hides coordination failures and slows cumulative science. \textbf{Key subproblems:} output-centric metrics, poor reporting standards, solved or gameable benchmarks, low ecological validity, and missing measures for teamwork process, common ground, workload, or governance quality. \textbf{Real-world impact:} BenchMARL explicitly describes a reproducibility crisis in MARL; SMACv2 was created because SMAC no longer required sufficiently rich closed-loop policies; NASA's HATTB and the 2026 common-ground benchmark both exist because field-relevant HMT evaluation remains underdeveloped; and co-creation work argues that current evaluations overemphasize artifact quality while under-measuring interaction quality and mental models. \textbf{Open gaps and directions:} multi-level scorecards combining task performance, teamwork process, safety, user outcomes, and auditability; long-horizon field studies; standardized ad hoc teammate sets; and benchmarks that include repair and failure handling. \textbf{Representative refs:} Bettini et al. (2024), Ellis et al. (2023), NASA (2024), Gmeiner et al. (2024), Poelitz et al. (2026), Wang et al. (2026). \sourcemark{10}}

\problempara{7}{Accountability, liability, privacy, IP, and governance ambiguity}{\textbf{Definition:} even when systems work technically, it often remains unclear who is responsible for harms, what disclosures are owed, how incidents should be audited, and how data, privacy, and authorship rights should be handled. \textbf{Why it matters:} this is where otherwise promising systems stall in deployment. \textbf{Key subproblems:} provenance, incident disclosure, auditability, allocation of responsibility between developer/deployer/operator, consent-credit-compensation for training data, and privacy in embodied systems. \textbf{Real-world impact:} NIST's GenAI profile centers lifecycle governance, provenance, testing, and incident disclosure; NTIA recommends independent evaluations for high-risk systems; the EU AI Act is now in phased application; and the U.S. Copyright Office has concluded that GenAI outputs are copyrightable only where a human author determines sufficient expressive elements. Creative-worker interviews also show persistent gaps around consent, credit, and compensation. \textbf{Open gaps and directions:} role-responsibility matrices, deployment logs and provenance, privacy-by-design in robots, audit-friendly interfaces, and domain-specific contracting/oversight practices. \textbf{Representative refs:} NIST (2024), NTIA (2024), European Commission (2024--2026), U.S. Copyright Office (2024--2025), Kyi et al. (2025), Jayaraman et al. (2024). \sourcemark{11}}

\problempara{8}{Bias, value pluralism, and vulnerable-user harms}{\textbf{Definition:} team outputs can encode stereotypes, paternalism, moral framing errors, or manipulative personalization, and these harms can be amplified through human--AI feedback loops. \textbf{Why it matters:} ``human in the loop'' does not reliably remove bias; sometimes it redistributes or legitimizes it. \textbf{Key subproblems:} selective adherence to biased advice, value conflicts across cultures and contexts, feedback-loop amplification, anthropomorphism, harms to children/older adults/patients, and participatory evaluation. \textbf{Real-world impact:} UNESCO's ethics framework centers human rights, fairness, and oversight; public-sector experiments show selective adherence when advice aligns with stereotypes; newer work shows AI feedback loops can alter human perceptual interpretations; and HRI studies in healthcare and eldercare highlight privacy, autonomy, and dependency concerns for vulnerable populations. \textbf{Open gaps and directions:} team-level fairness tests rather than model-only fairness tests, participatory design with affected communities, dynamic harm audits, and safeguards against manipulative or dependency-forming robot behavior. \textbf{Representative refs:} UNESCO (2021), National Academies (2022), Alon-Barkat and Busuioc (2023), Glickman et al. (2025), Jayaraman et al. (2024), Hung et al. (2025). \sourcemark{12}}

\section*{Domain and stakeholder mapping}

The matrix below is a synthesis of the literature above. ``H'' means high salience; ``M'' means meaningful but usually secondary. In co-creation, the ``user'' and ``operator'' are often the same person, but I keep them separate for consistency. \sourcemark{13}

{\footnotesize
\begin{longtable}{@{}p{0.26\linewidth}>{\centering\arraybackslash}p{0.06\linewidth}>{\centering\arraybackslash}p{0.072\linewidth}>{\centering\arraybackslash}p{0.052\linewidth}>{\centering\arraybackslash}p{0.083\linewidth}>{\centering\arraybackslash}p{0.064\linewidth}>{\centering\arraybackslash}p{0.079\linewidth}>{\centering\arraybackslash}p{0.075\linewidth}>{\centering\arraybackslash}p{0.083\linewidth}@{}}
\toprule
Problem & HMT & \makecell{Co-\\creation} & HRI & \makecell{General\\multiagent} & Users & Operators & Designers & Regulators \\
\midrule
\endfirsthead
\toprule
Problem & HMT & \makecell{Co-\\creation} & HRI & \makecell{General\\multiagent} & Users & Operators & Designers & Regulators \\
\midrule
\endhead
Safety assurance & H & M & H & H & H & H & H & H \\
\midrule
Common ground and intent alignment & H & H & H & H & H & H & H & M \\
\midrule
Open-team coordination and generalization & H & M & H & H & M & H & H & M \\
\midrule
Trust calibration and controllability & H & H & H & M & H & H & H & M \\
\midrule
Agency, workload, and skill retention & H & H & H & M & H & H & H & M \\
\midrule
Evaluation and reproducibility & H & H & H & H & M & M & H & M \\
\midrule
Governance, privacy, IP, and liability & H & H & H & H & H & H & H & H \\
\midrule
Bias, values, and vulnerable-user harms & H & H & H & H & H & M & H & H \\
\bottomrule
\end{longtable}
}

\section*{Recent milestones and problem interdependencies}

The timeline shows how the field moved from accident- and sociology-driven warning signs toward specific benchmarks, standards, and governance instruments. The milestones are representative rather than exhaustive. \sourcemark{14}

\begin{center}
\resizebox{\linewidth}{!}{%
\begin{tikzpicture}[font=\sffamily\scriptsize,>=Stealth]
  \node[font=\sffamily\bfseries\small] at (8.0,4.85) {Milestones shaping HMT, co-creation, HRI, and multiagent systems};
  \draw[->,line width=0.8pt] (-0.35,3.65) -- (16.55,3.65);
  \foreach \x/\yr/\txt in {
    0/2018/{Uber ADS crash in\\Tempe exposes\\handoff, oversight,\\and safety-culture\\failures},
    2/2019/{Rahwan et al.\\formalize ``machine\\behaviour''},
    4/2021/{Dafoe et al. argue\\for Cooperative AI\\and common\\ground},
    6/2022/{National Academies\\consolidate HMT\\research needs},
    8/2023/{SMACv2 highlights\\benchmark\\insufficiency for\\closed-loop MARL\\coordination},
    10/2024/{BenchMARL targets\\reproducibility;\\LangGround\\targets\\human-interpretable\\agent\\communication},
    12/2024/{NIST GenAI Profile\\and U.S.\\accountability\\guidance push\\lifecycle risk\\management},
    14/2025/{USCO AI copyright\\reports and revised\\robot-safety\\standards sharpen\\governance\\questions},
    16/2026/{Common-ground\\benchmark and\\JaxAHT target\\human-AI\\collaboration and\\ad hoc teamwork\\evaluation}
  }{
    \node[fill=black!25,minimum width=1.28cm,minimum height=0.43cm,font=\sffamily\bfseries\tiny] at (\x,4.1) {\yr};
    \draw[densely dotted,black!60] (\x,3.92) -- (\x,2.64);
    \node[draw=black!28,fill=black!10,align=center,text width=1.72cm,inner sep=2.6pt,minimum height=1.2cm,font=\sffamily\tiny] at (\x,1.95) {\txt};
  }
\end{tikzpicture}%
}
\end{center}

These problems are tightly coupled. Weak benchmarking hides coordination failures; hidden failures distort trust; distorted trust worsens over- or under-reliance; poor role design accelerates deskilling; and governance ambiguity reduces incident learning and constrains deployment. This interaction pattern is one reason the field needs joint technical--human--organizational research rather than isolated algorithmic fixes. \sourcemark{15}

\begin{center}
\resizebox{0.92\linewidth}{!}{%
\begin{tikzpicture}[
  font=\sffamily\scriptsize,
  >=Stealth,
  box/.style={draw=black!28,fill=white,align=center,text width=2.95cm,minimum height=0.78cm,inner sep=3pt},
  arr/.style={->,line width=0.65pt,black!75}
]
  \node[box] (open) at (0,4.20) {Open-world coordination\\limits};
  \node[box] (cg) at (0,3.05) {Common-ground failures};
  \node[box] (handoff) at (0,1.88) {Poor handoffs and mode\\confusion};

  \node[box] (bias) at (6.15,5.15) {Bias, privacy, IP, and\\liability issues};
  \node[box] (legit) at (3.95,4.20) {Low legitimacy and\\constrained deployment};
  \node[box] (bench) at (3.95,3.00) {Weak benchmarks and\\low reproducibility};
  \node[box] (hidden) at (3.95,1.90) {Hidden capability gaps};
  \node[box] (trust) at (3.95,0.76) {Trust miscalibration};
  \node[box] (rely) at (3.95,-0.38) {Over- or under-reliance};

  \node[box] (role) at (7.90,3.05) {Poor role design};
  \node[box,text width=3.15cm] (work) at (7.90,1.88) {Workload imbalance\\and deskilling};
  \node[box,text width=3.15cm] (safety) at (7.05,-1.45) {Safety and performance\\failures};

  \draw[arr] (open) -- (cg);
  \draw[arr] (cg) -- (handoff);
  \draw[arr] (legit) -- (bench);
  \draw[arr] (bench) -- (hidden);
  \draw[arr] (hidden) -- (trust);
  \draw[arr] (trust) -- (rely);
  \draw[arr] (role) -- (work);
  \draw[arr] (bias.west) to[out=200,in=72] (legit.north);
  \draw[arr] (handoff.south) to[out=-76,in=185] (trust.west);
  \draw[arr] (work.south) to[out=-72,in=0] (trust.east);
  \draw[arr] (rely.south) to[out=-90,in=195] (safety.west);
  \draw[arr] (bias.east) to[out=-10,in=85] (safety.north east);

  \begin{scope}[on background layer]
    \node[draw=black!22,rounded corners=2pt,fit=(open)(cg)(handoff)(bias)(legit)(bench)(hidden)(trust)(rely)(role)(work)(safety),inner sep=7mm] {};
  \end{scope}
\end{tikzpicture}%
}
\end{center}

\section*{Selected primary-source URLs}

A compact list of primary or official sources discussed above, with URLs included in code format.

\begin{itemize}
\item Rahwan et al. (2019), \emph{Machine behaviour} --- \url{https://www.nature.com/articles/s41586-019-1138-y}
\item Dafoe et al. (2021), \emph{Cooperative AI: machines must learn to find common ground} --- \url{https://doi.org/10.1038/d41586-021-01170-0}
\item National Academies (2022), \emph{Human-AI Teaming: State-of-the-Art and Research Needs} --- \url{https://doi.org/10.17226/26355}
\item NTSB, \emph{Collision Between Vehicle Controlled by Developmental Automated Driving System and Pedestrian} --- \url{https://www.ntsb.gov/investigations/Pages/HWY18MH010.aspx}
\item NIST (2024), \emph{Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile} --- \url{https://doi.org/10.6028/NIST.AI.600-1}
\item NTIA (2024), \emph{Artificial Intelligence Accountability Policy Report} --- \url{https://www.ntia.gov/sites/default/files/publications/ntia-ai-report-final.pdf}
\item Bettini et al. (2024), \emph{BenchMARL} --- \url{https://www.jmlr.org/papers/v25/23-1612.html}
\item Li et al. (2024), \emph{Language Grounded Multi-agent Reinforcement Learning with Human-interpretable Communication} --- \url{https://proceedings.neurips.cc/paper_files/paper/2024/file/a06e129e01e0d2ef853e9ff67b911360-Paper-Conference.pdf}
\item Wang et al. (2024), \emph{N-Agent Ad Hoc Teamwork} --- \url{https://arxiv.org/abs/2404.10740}
\item McGuire et al. (2024), \emph{Establishing the importance of co-creation and self-efficacy in creative collaboration with artificial intelligence} --- \url{https://doi.org/10.1038/s41598-024-69423-2}
\item U.S. Copyright Office, \emph{Copyright and Artificial Intelligence} --- \url{https://www.copyright.gov/ai/}
\item European Commission, \emph{AI Act} --- \url{https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai}
\item Poelitz et al. (2026), \emph{A Benchmark to Assess Common Ground in Human-AI Collaboration} --- \url{https://arxiv.org/abs/2602.21337}
\item Wang et al. (2026), \emph{JaxAHT} --- \url{https://openreview.net/pdf?id=DkZ2IEBpH1}
\item A3, \emph{ANSI/A3 R15.06-2025} --- \url{https://www.automate.org/robotics/standards/robot-standard-r15-06-2025-available-purchase}
\item UNESCO, \emph{Recommendation on the Ethics of Artificial Intelligence} --- \url{https://www.unesco.org/en/ethics-ai/en/recommendation-ethics}
\end{itemize}

\bigskip
\hrule
\bigskip

\sourceitem{1}{https://www.nature.com/articles/s41586-019-1138-y}
\sourceitem{2}{https://www.science.org/doi/10.1126/sciadv.adn5290}
\sourceitem{3}{https://arxiv.org/abs/2409.17348}
\sourceitem{4}{https://academic.oup.com/pnasnexus/article/5/3/pgag030/8490283}
\sourceitem{5,14}{https://www.ntsb.gov/investigations/Pages/HWY18MH010.aspx}
\sourceitem{6}{https://www.nationalacademies.org/read/26355/chapter/6}
\sourceitem{7}{https://pubmed.ncbi.nlm.nih.gov/33947992/}
\sourceitem{8}{https://www.nationalacademies.org/read/26355/chapter/7}
\sourceitem{9,15}{https://www.nationalacademies.org/read/26355/chapter/8}
\sourceitem{10}{https://www.jmlr.org/papers/volume25/23-1612/23-1612.pdf}
\sourceitem{11}{https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence}
\sourceitem{12}{https://www.unesco.org/en/ethics-ai/en/recommendation-ethics}
\sourceitem{13}{https://www.nationalacademies.org/read/26355}

\end{document}

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
