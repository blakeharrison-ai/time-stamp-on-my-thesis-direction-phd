# time-stamp-on-my-thesis-direction-phd
message of my thesis direction to my (Blake Harrison) PhD Advisor (Dr. YZ Yang):

I’ve been reflecting on LeCun’s recent discussion of world models and EBMs. I agree with his framing that EBMs are a strong substrate for modeling dynamics, but I see the most powerful direction as integrating EBMs with RL to form the substrate for Structural Causal Models (SCMs). My goal is to identify the right semantic layer—something with the precision of a predicate calculus that allows counterfactuals, constraints, and compositional reasoning. That’s the focus of Paper 2.

Paper 1 now simplifies beautifully: its mechanism is a spring-style energy constraint that enforces coherence around clean priors—both mathematically and intuitively clearer.

When I say interactive world models, I mean systems that:
– represent p(s_{t+1}\mid s_t,a_t) consistently,
– respond to interventions/counterfactuals,
– integrate sensory feedback and causal structure, and
– generalize across agents and contexts while preserving internal coherence.

EBMs then provide the energy landscape unifying these properties—robust, uncertainty-bounded, and composable policies that could, in principle, approach physical precision once scalability issues are solved.

For the semantic layer, I’m evaluating ASP + HTN + ANML, which seems to combine causal expressiveness, hierarchical planning, and mature temporal-resource modeling.

subthread comment on this slack message declaration as well:

The simulator is the physical execution layer of your EBM world model:
it instantiates the environment p(s_{t+1}\!\mid\!s_t,a_t), while ASP → HTN → ANML supply structured, causal, and temporal directives.
The EBM + RL + SCM substrate bridges them—turning symbolic intent into physically realized, energy-consistent dynamics and feeding the resulting data back into causal reasoning and policy learning.
The entry concept of this for generalization/safety is what I am working to achieve in the second paper. (edited) 
