# time-stamp-on-my-thesis-direction-phd
Question:
Can open-ended learning + memory + imagination make language-guided long horizon embodied model predictive control (planning) robust to OOD?

Thesis statement:

Here is my final direction I told my PhD advisor:

I realized this week that I have been maximizing systems when I need to think in terms of core claims, clear gaps, and minimal contributions with maximal yield — claims I can defend with references, empirical evidence, or math.

My current view is that CoCa-MPC is best positioned for RA-L → ICRA. I am narrowing it around one core problem gap: behavioral support does not entail admissibility, and admissibility does not entail behavioral support, especially under OOD/distribution shift. My plan is to build the paper around a single proof of that gap plus a small robotics simulation experiment this weekend, then share it with Josh for a first round of revision.

I also realized that what I was calling language-guided co-creation is more of an application domain than the core technical identity of the work. My actual communities are model-based RL/MPC — especially the offline RL or evolutionary-algorithms-to-online ADP/MPC line — open-endedness, and embodied AI / robot learning, specifically embodied open-endedness.
The thesis-level question I am converging on is:
Can certified semantic imagination enable language-guided embodied agents to achieve robust, diverse, constraint-respecting long-horizon generalization under OOD/distribution shift, while mitigating negative transfer, hallucinated futures, and compounding model error?
By certified semantic imagination, I mean causally grounded, admissibility-gated, language-guided world-model planning sourced by open-ended semantic frontier generation — including semantic autocurricula, multiagent emergence, co-evolution through world-model/agent self-play and self-improvement, curiosity, and self-organization within imagination and offline blending — recomposed from structured memory, and committed to action through robust MPC (planning).

This is the single axis that I think everything I am working on fits under. I can measure it through modified embodied simulators, VLA/VLM+MPC benchmarks — including OOD benchmark performance, negative-transfer measures, safety compliance, language-command following, hallucination rate, compounding model-error effects, and long-horizon success — and PCG-style settings where constraints and diversity are clear empirical wins.

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
