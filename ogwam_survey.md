# Object-Graph World Action Model Learning for Embodied Planning and Control: An Approximate Dynamic Programming Perspective

**FULL SURVEY BLUEPRINT (v2.0)** — supersedes `og-wam-csur-blueprint.md` (kept as the skeleton record). Calibrated against the closest-neighbor survey: Hou et al., *World Model for Robot Learning: A Comprehensive Survey* (arXiv:2605.00080, Apr 2026), hereafter **[NTU-WM]**.

---

## PART A — FRONT MATTER (LOCKED)

- **Title:** Object-Graph World Action Model Learning for Embodied Planning and Control: An Approximate Dynamic Programming Perspective
- **Abstract:** FINAL v2 (LaTeX, in the v1 file §1; unchanged). All body sections below exist to discharge its promises.
- **Venue:** ACM Computing Surveys. **Body budget:** ~42 pages. **References:** 280–350. **arXiv first**, living repo + project page from day one (mirror [NTU-WM]'s repo/page convention: `Awesome-OG-WAM` + GitHub Pages).
- **Keywords/CCS:** as in v1 file.
- **Inclusion criterion (print in §1):** a work enters iff (a) it learns/uses a predictive model of environment dynamics AND (b) at least one tuple quantity is learned from, computed by, or defined over that model or an object/graph state space.
- **Freeze policy:** coverage freeze at submission minus 1 month, stated in a footnote; post-freeze works go to the repo only.

## PART B — WHAT THE REFERENCE SURVEY TEACHES (adopt / extend / differ)

**Adopt (conventions that visibly work in [NTU-WM]):**
1. **Fig. 1 organization diagram** on p.2–3: per-section iconized map of the survey. We do the same, with the tuple heads as the visual spine.
2. **Fig. 2 temporal-evolution diagram**: dated waves (2023.1→2026.3) in two branches. Ours: upper branch = object/graph world models (2016→2026: Interaction Networks → NRI/GNS → slot dynamics → language-conditioned slot WMs); lower branch = decision-quantity coupling (Dyna/MuZero/TD-MPC → Cosmos Policy/DreamZero → WM-as-simulator/evaluator → co-evolution). Caption caveat, verbatim spirit: "dominant directions, not sequential replacements."
3. **Checkbox comparison tables** (their Tables 1–4): ✓ / – / ✗ attribute matrices with representative-work rows. Our master taxonomy adopts this exact legibility convention.
4. **Per-section rhetoric:** "problem setting and scope" openers; "Taken together…" closing synthesis paragraphs; equations introduced early per section; explicit "our survey differs from prior surveys in three respects" paragraph in §1.
5. **Two-level narrative device** (their §4.1): first-level paradigm → second-level co-evolution. We reuse it in our post-training and simulator subsections.
6. **First-class Benchmarks & Datasets section** with a layered evaluation framework and dataset attribute tables.
7. **Explicit epistemic hedges** where evidence is suggestive ("open empirical question") — reviewer-proofing we should mirror.

**Extend (their formalism, generalized by ours):** [NTU-WM] §3.1 presents policy, passive WM, controllable WM, and IDM as marginals/conditionals of one joint p(o_{t+1:t+k}, a_{t+1:t+k} | o_t, l). Our §2 subsumes this: augment the joint with rewards, costs, and goals; their four queries plus value, cost, admissibility, and policy heads all become **queries of a decision-augmented joint**, and ADP is the calculus for composing those queries into planning and control. This is our formal contribution stated in the reference's own vocabulary — the single most important positioning move in the paper.

**Differ (the gap, now documentable):** [NTU-WM] states its concrete focus is "predominantly visual world models" and treats symbolic/predicate/object-relation world models and structure-aware generation as complementary side threads (their §3.6, §5.4). It has no value/cost/admissibility treatment beyond noting Cosmos Policy's value outputs and RISE's progress-value head; no factored-MDP theory; no open-endedness; no ADP unification; navigation/driving but no PCG/design/co-creation. Table T-DIFF row 1 writes itself — and their scope sentences are citable evidence that the object-graph decision-oriented union is unoccupied.

## PART C — GLOBAL APPARATUS

**Figures (full specs):**
- **F1 (p.1–2) Organization + pipeline:** WFM → post-training → WAM with the seven heads fanning out; object-graph plane beneath; section numbers annotated on regions ([NTU-WM] Fig. 1 style).
- **F2 Temporal evolution, two branches** (spec in Part B.2).
- **F3 Action-role spectrum:** action-free WM → action-conditioned WM → joint WAM → VLA; place Genie / Cosmos-Predict, DreamDojo / DreamZero, Cosmos Policy, MuZero, TD-MPC2 / RT-2, OpenVLA, π0.
- **F4 Queries of the decision-augmented joint:** one joint blob; arrows to eight query boxes (their four + our value/cost/admissibility/goal-conditioned-policy), each labeled with its ADP role.
- **F5 The MPC template:** base policy = π̂, simulator = p̂, terminal cost = V̂, stage cost = r̂/ĉ, action masking = α̂; Bertsekas lookahead diagram instantiated with tuple heads.
- **F6 Architectural paradigms for head exposure** (mirrors [NTU-WM] Fig. 3/4): decoupled | single-backbone | MoE/MoT | latent-internalized — reinterpreted as *which heads each paradigm exposes and where*.
- **F7 Taxonomy trellis** (five axes).
- **F8 Sparse-cell heatmap:** state-structure × decision-head coverage density from T-MASTER; the empty object-graph × {V̂, ĉ, α̂} × RL-from-WFM region visually undeniable.

**Tables (schemas):**
- **T-NOTE** notation; **T-DEF** definitions box (world model / video generation model [NTU-WM eq.1–2] / WAM-narrow / WAM-tuple / OG-WAM / VLA).
- **T-QUERY:** Query | factorization of the joint | tuple head(s) | ADP primitive | representative works. Rows: policy, passive WM, controllable WM, IDM, value query, cost/constraint query, admissibility query, evaluator query.
- **T-SUB (§3):** substrate × supervision × exposed heads (✓/–/✗ over 7 heads) × domain.
- **T-ARCH (§4):** paradigm (IDM-style / single-backbone / MoE-MoT / unified-VLA / latent-WM / simulator / evaluator) × representative works × heads exposed × inference-time active heads × backbone × coupling ([NTU-WM] Table 1 schema + our head columns).
- **T-MASTER (§8, 2 pages):** rows = method families §3–§7; columns = 7 head checkboxes | state structure (pixel/latent/slot/graph/symbolic) | learning signal | lifecycle stage | ADP primitive | domain.
- **T-DIFF:** prior surveys ([NTU-WM]; the 2606.00113 manipulation-WM survey; VLA surveys — embodied-manipulation, action-tokenization, efficient-VLA; object-centric WM reviews; GNN-simulator reviews; open-endedness surveys; MPC–RL syntheses) × covers × lacks.
- **T-BENCH (§10):** benchmark × layer (open-loop / closed-loop / diagnostics / decision-quantity) × what it measures × graph-readiness.
- **T-DATA (§10):** dataset attribute matrix ([NTU-WM] Table 3/4 convention): X-Emb | actions | 3D/multi-view | language | contact/physics | **object/graph annotations** (our added column).

---

## PART D — SECTION-BY-SECTION FULL PLAN
(Format per section: Budget | Purpose | Subsections with paragraph-level content | Anchors | ADP sentence | Owns | Risk)

### §1 Introduction — 3 pp
Six-paragraph draft from v1 stands (¶1 opening already synced to abstract v2). **Add, per [NTU-WM] convention:** (a) a bulleted 4-item contributions list (C1 tuple formalization subsuming [NTU-WM]'s four queries; C2 substrates reorganized by decision-readiness; C3 post-training as approximate policy iteration with the architectural-paradigm × head-exposure account; C4 checkbox taxonomy exposing the sparse cell + open-problem program); (b) a "differs from prior surveys in three respects" paragraph naming [NTU-WM] directly: finer decision-quantity resolution, object/graph structural resolution, and a single formal lens; (c) F1, F2 placed here. **Risk:** low. **Owns:** F1, F2.

### §2 Background & Formalism — 4.5 pp
- **2.1 MDPs, factored MDPs, OO-MDPs:** Boutilier/Guestrin decomposition boxed result; Diuk OO-MDPs; relational RL; schema networks. The formal payoff sentence: on object-graph states, values/costs/admissibility decompose over local scopes.
- **2.2 ADP primitives:** Bellman operators; VI/PI; rollout + policy improvement property; multistep lookahead; MPC-as-lookahead; AlphaZero/MPC identification (Bertsekas 2020/2022).
- **2.3 The decision-augmented joint and its queries (NEW, the Part-B "extend" move):** start from [NTU-WM] eq. (4)–(8); augment with (r, c, g); derive T-QUERY; one display equation for the augmented joint; note their l-as-high-level-action convention and unify it with our g (language goals ⊂ G, so instruction-conditioning = goal-head conditioning).
- **2.4 The WAM tuple:** camera-ready head-definition block (already drafted, v1 §2.3 insert) + T-DEF + F3.
- **2.5 Association / intervention / counterfactual:** two paragraphs; do(·) becomes substantive only under confounded offline logs (→ §6).
**Owns:** T-NOTE, T-DEF, T-QUERY, F3, F4. **Risk:** low; write first.

### §3 Substrates: Object-Centric and Graph World Models — 5.5 pp
Purpose: the mature "where is the field" literatures, reorganized by decision-readiness; running observation = these expose p̂ with structure but almost no decision heads.
- **3.1 Slot-based scene decomposition & dynamics:** AIR→MONet/IODINE/GENESIS→Slot Attention; SAVi/SAVi++/STEVE/SlotDiffusion; C-SWM, OP3, SlotFormer; FOCUS; closing exhibit: language-conditioned slot rollouts (Jeong et al., ICLR'25) as nearest-existing OG-WAM.
- **3.2 Graph-network simulators:** Interaction Networks, NRI, GNS, MeshGraphNets; contact-rich GNN models.
- **3.3 Symbolic/relational ancestors and planner-facing WMs:** factored/OO-MDP model learning; schema networks; TAMP; the [NTU-WM]-cited predicate/operator world-model line (Silver 2021; Shah 2025; Liang 2025c/2026; Athalye 2026) — folded in as the symbolic limit of OG-WAMs, upgrading what [NTU-WM] treats as a side note into a first-class substrate.
- **3.4 Video-to-structure intermediates (NEW, from the reference):** AVDC dense correspondences; VidBot 3D hand trajectories; Object-centric 3D Motion Fields; NovaFlow actionable 3D object flow; TesserAct 4D RGB-D-normal WMs; Mask2IV interaction-trajectory conditioning. Thesis: the video-WM community is *already* extracting object-graph structure as an execution interface — evidence the substrates are converging on our cell from the pixel side.
- **3.5 Transformers as graph machines:** attention = message passing; object tokens; structure-biased transformers; substrate-agnosticism hedge quoting [NTU-WM]'s "open empirical question" stance.
- **3.6 3D/geometric consistency:** PAIWorld; OBEYED-VLA; geometry as admissibility's perceptual substrate.
**Owns:** T-SUB. **ADP sentence:** substrates learn the transition kernel only; every decision quantity is external. **Risk:** low-medium; write first.

### §4 From World Foundation Models to WAMs: Post-Training as Approximate Policy Iteration — 7 pp (churn section; write last)
- **4.1 WFM pretraining:** Cosmos platform / Predict 2.5; Genie 2/3 + Genie Envisioner; V-JEPA 2/2.1; DreamDojo (latent-action pretraining, human video); WoW (interaction-trained physical intuition); Vid2World (video-diffusion → interactive WM); WHAM/Muse; GigaWorld-0 (data engine); UnifoLM-WMA-0.
- **4.2 Action conditioning:** Cosmos action-control; IRASim frame-level action conditioning; EnerVerse-AC; Ctrl-World action-faithful multi-view rollout; Interactive World Simulator; MiraBench's AdaLN recipe; EVA's inverse-dynamics-reward executability alignment.
- **4.3 Architectural paradigms × head exposure (reframes [NTU-WM] §3 through the tuple):** IDM-style decoupled (UniPi, VidMan, Vidar, Gen2Act, VPP, Video2Act, MimicVideo, TC-IDM, LVP, Say-Dream-ACT); single-backbone joint (UVA, UWA, VideoVLA, VideoPolicy, UD-VLA, GigaWorld-Policy; **Cosmos Policy as the value-head existence proof** — actions, future states, AND values as latent frames, direct-policy vs planning modes; **DreamZero** chunk-wise joint denoising); MoE/MoT (GE-Act, Motus, LingBot-VA, BagelVLA, DiT4DiT, Fast-WAM's "co-training may beat inference-time imagination" finding, LDA-1B, FRAPPE); unified VLA (GR-1, UP-VLA, WorldVLA, DreamVLA, UniVLA, CoWVLA, F1, InternVLA-A1, HALO, TriVLA); latent-internalized (FLARE, VLA-JEPA, JEPA-VLA, WoG, DIAL). One paragraph per paradigm + T-ARCH; the analytical payoff is the *heads-exposed* column, which [NTU-WM] does not track.
- **4.4 Language grounding of dynamics:** Dynalang, LanGWM, language-guided WMs, instruction-conditioned slot rollouts; g enters the tuple here.
- **4.5 Alignment-style post-training of dynamics:** ABot-PhysWorld DPO with decoupled discriminators; preference optimization applied to p̂ itself; ĉ head emergence.
- **4.6 RL/RLVR with the model in the loop — two-level narrative:** Level 1, WM as environment (UniSim, World-Env, VLA-RFT, DiWA, World4RL, WorldGym/World-Gymnast, PlayWorld, RehearseVLA, WMPO, ProphRL, RISE progress-value head, GigaBrain-0.5M); Level 2, co-evolution (World-VLA-Loop, VLAW, WoVR — simulator reliability as the bottleneck; keyframe-initialized rollouts). RLVR = policy iteration with verifiable/world-model-supplied reward.
- **4.7 WM as evaluator/verifier:** GPC deployment-time lookahead; IRASim value-ranked trajectories; World-in-World closed-loop plan revision; DreamPlan preference pairs from rollouts; WorldEval, Veo/Gemini policy evaluation, WorldArena; CoVer-VLA verification scaling; MPC-in-latent (TD-MPC2, LeWorldModel).
**ADP Rosetta row per family** (SFT=policy approximation; DPO/RLHF=improvement vs learned preference; RLVR=PI under verifiable reward; WM-as-critic=approximate policy evaluation; WM-as-env=simulation-based PI; distillation=policy-space projection; evaluator=lookahead/rollout). **Owns:** T-ARCH, F6. **Risk:** HIGH churn.

### §5 Decision Quantities over Object Graphs — 5.5 pp
Head-by-head (r̂/ĉ; V̂/Q̂ with Guestrin factored decomposition meeting GNN value functions; α̂ admissibility & physical feasibility — CMDPs, shielding, contact/support/reachability predicates, physics-alignment link, flag as largest importance-vs-literature gap; affordances as typed admissible-action edges — Gibson, Khetarpal; options/hierarchy/parts — subgraph-indexed skills, articulated objects, capability libraries; preferences/constraints; language→graph grounding — referring expressions→nodes, instructions→goal graphs; the YZ-lineage subsection, written deep). Per-head anchor works + ADP role. **Risk:** low-medium; write first alongside §3.

### §6 Lifecycle: Offline Logs to Online Hybrid Simulation — 4 pp
6.1 offline logs & confounding (do(·) cashes out; causal RL; OPE); 6.2 imagination training (Dyna, Dreamer v1–3, MBPO short-rollout error control); 6.3 decision-time hybrid simulation (PETS/PlaNet/TD-MPC2; rollout-and-verify; F5 template instantiated); 6.4 human-in-the-loop & apprenticeship (DAgger, ALOE intervention loops, teleop-through-WM per DreamDojo); 6.5 forward pointer to §10 evaluation layers. **Owns:** F5.

### §7 Open-Endedness — 3 pp
Scope rule printed first (objective/curriculum computed from the model or defined over the graph). 7.1 model-derived intrinsic rewards (ICM, Plan2Explore, RND, empowerment) — the WAM *manufactures* components of r̂; 7.2 skill discovery → subgraph-indexed options; 7.3 QD + computational-creativity bridge (novelty search, MAP-Elites, graph-edit-distance novelty); 7.4 UED as typed graph edits (POET, PAIRED=robust DP, ACCEL, XLand); 7.5 multi-agent emergence (agents-as-nodes, hide-and-seek). **Risk:** low; the scope rule is the shield.

### §8 Synthesis: Master Taxonomy and the Sparse Cell — 2.5 pp
T-MASTER (2 pp) + three reading observations + the sparse-cell paragraph naming nearest occupants honestly (language-guided slot WMs; Cosmos Policy's value frames; RISE's progress value; geometry-grounded VLAs; symbolic planner-facing WMs) and why each stops short. **Owns:** T-MASTER, F7, F8.

### §9 Applications and the Belief-Flow Preview — 2.5 pp
Seven domains keyed to exercised heads (manipulation; visual navigation — Pathdreamer, NWM, VISTA/v2, SparseVideoNav, EgoWM reframed by which heads they expose; mobile manipulation; interactive PCG; assisted design; mixed-initiative co-creation; multi-agent simulation). **Scope discipline:** autonomous driving = one adjacency paragraph deferring to [NTU-WM] §6.2 (it is not in our abstract; do not creep). 9.8 belief-flow preview (flows over agent-indexed graph states; I-POMDP lineage; belief-MDP VI with flow-parameterized updates; marked outlook).

### §10 Benchmarks, Datasets, and Evaluation — 2.5 pp (modeled on [NTU-WM] §7, extended one layer)
- **10.1 Four-layer evaluation framework:** L1 open-loop predictive quality (RBench, EWMBench, DreamGen Bench, EVA-Bench); L2 closed-loop decision utility (WorldArena, WorldEval, WorldGym, World-in-World); L3 physical-consistency/controllability/executability diagnostics (WorldSimBench, WoW-World-Eval, MiraBench action-conditioned reliability, WM-ABench atomic capabilities); **L4 decision-quantity diagnostics (our extension):** value calibration, cost/constraint fidelity, admissibility precision-recall, graph-state prediction accuracy — mostly nonexistent → feeds Open Problem 8.
- **10.2 Datasets** T-DATA with the added object/graph-annotation column: robot corpora (OXE, DROID, BridgeData V2, AgiBot World, RoboMIND 2.0, RH20T/-P, RoboTwin 2.0, UMI family); human/ego priors (Ego4D-style, DreamDojo-HV, UniHand, DexWild, EgoMimic, Action100M); object-centric/physics suites (CLEVRER, Physion, CATER, Kubric/MOVi); scene-graph environments (AI2-THOR/ProcTHOR, Habitat, BEHAVIOR). Honest observation: no existing corpus pairs foundation-scale video with graph-state + decision-quantity annotation.
**Owns:** T-BENCH, T-DATA.

### §11 Open Problems: Toward OG-WAMs — 3 pp
The v1 eight, plus reference-informed upgrades: P1 pixel→graph transfer of WFM priors (latent-action bridges; video-to-structure intermediates of §3.4 as the on-ramp); P2 admissibility/feasibility heads on graphs; P3 factored value/cost at foundation scale; P4 confounding-aware offline→online; P5 subgraph skills & capability allocation; P6 EBM/flow graph dynamics; P7 open-ended graph curricula; P8 L4 benchmarks & reporting standards; **P9 (new) reliability and co-evolution for graph simulators** — the WoVR/VLAW lesson transposed: graph-rollout hallucination corrupts evaluation signals; co-evolve p̂ with π̂.

### §12 Conclusion — 0.5 pp. Question shift → tuple → factored leverage → sparse cell → one forward sentence.

---

## PART E — WRITING OPERATIONS

- **Order:** §2 → §3 → §5 → §7 → §6 → §10 → §8 → §9 → §11 → §4 (churn-last) → §1 polish → §12. Abstract untouched.
- **Cadence target:** stable sections drafted in 6–8 weeks; §4 + T-MASTER in weeks 8–12; internal red-team pass against the reviewer pre-emptions (v1 list + one new: "how is this not [NTU-WM] plus graphs?" → answer = T-QUERY, T-MASTER head columns, §5, §7, L4, ADP throughout — the tuple is the paper); arXiv at week 14; CSUR submission after 2-week cooldown edit.
- **Repo structure mirrors T-MASTER columns** so the living list and the taxonomy stay one artifact.
- **Consistency rules:** every section ends "Taken together…" + one-sentence ADP mapping; every method mention carries its heads-exposed tag on first appearance; [NTU-WM] cited generously and framed as the complementary policy-centric/video-centric account — ally, not rival.
