# Descriptive Agent Foundations (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/descriptive-agent-foundations/main.tex`. Compiled PDF: `targets/descriptive-agent-foundations.pdf`.

**Title:** Descriptive Agent Foundations
**Subtitle:** Selection theorems and the type signature of real agents

**Abstract:** Normative agent foundations asks what an ideal agent ought to be; descriptive foundations asks what agents actually arise in the physical world and why that structure keeps being produced. The organizing tool is the selection theorem: some optimization pressure in some environment class selects for agents with a particular type signature (world-model, goal, decision procedure). Three steps: (1) what a type signature is, and why coherence theorems are one early flawed selection theorem; (2) the type signature we actually expect (a sparse, recursive, latent-variable causal model, lazily evaluated, with goals over latents, not the textbook lookup table); (3) the wishlist of selection theorems (modularity, natural abstractions, goals over latents, subagents, mesa-optimization/search, internal modularity) and the pivotal move to broad/robust optima. Representational (coherence) vs mechanistic (selection) framing throughout.

## Section 1: Introduction: two directions on agency

- Normative (ideal agent, coherence theorems, behavior from outside) vs descriptive (start from the world; agent-free causal substrate that nonetheless produces agents)
- The descriptive goal: given any physical system, identify its goals/world-model/decision structure, and explain why such structures arise
- Bottom-up methodology; the selection theorem as the descriptive analogue of the coherence theorem; plan and prerequisites

## Section 2: The type signature of an agent

- Definition 2.1 (type signature): representation (what data structures/components), interfaces (inputs/outputs and connections), embedding (abstract structure -> low-level physical system)
- The $((A\to B)\to A)$ shorthand: model $(A\to B)$ maps actions to outcomes, agent takes a model and returns an action; which chunks of the substrate abstract into this type
- Why the three questions are exactly what alignment needs answered

## Section 3: Selection theorems

### 3.1 What a selection theorem is
- Definition 3.1 (selection theorem): something about the type signature/properties of agents selected for by a pressure (natural selection, ML training, profitability) in a broad environment class; need not mention selection; large attackable surface area

### 3.2 Coherence theorems as a (flawed) selection theorem
- Representation = utility + distribution; interfaces = bets in, EU-max action out, Bayes update; embedding = behavioral equivalence
- Too-strong assumptions (static, complete, path-independent preferences) fail for real agents; right form, wrong assumptions/conclusion; the bet that better assumptions give better type signatures (human values, inner agents, value drift)

### 3.3 Other known selection theorems
- Good Regulator / Gooder Regulator (world-models selected for); Kelly criterion (expected-log-wealth from long-run growth pressure); subagents argument (internal state -> Pareto over several utilities, not one)

### 3.4 The research program
- Forward (empirical observation -> generalize; sessile organisms lack brains) and backward (from type signature, or from selection process); incremental (apply-and-fix, as subagents came from markets; strengthen; patch; unify; minimize assumptions)
- The ambitious claim: good selection theorems get most of the way to the hardest parts of alignment

## Section 4: How we picture Bayesian agents

- Textbook (enumerate worlds, assign probabilities, update, sum EU) is only a *behavioral* spec; impossible to implement when embedded
- The world-model is a sparse causal program: Bayes net (linear not exponential), recursive reusable submodels (factorial example), "moderately sized program with a lot of recursion"
- Inference is lazy and local: message passing reaches only relevant variables (bird vs gasoline price); decisions need only differences between options, never absolute EU
- Goals attach to latent variables: clustering (bark/leaves/roots -> tree); latents need not be real (spirits) but mostly are (natural abstraction); utility inputs are latents (spouse actually happy vs appearing happy)
- Caching introduces incoherence: stale cached values violate Bellman/consistency; resolving is reflection (explains human cognitive effort and apparent non-Bayesian behavior)
- Self-modeling (agent as a node in its own model) is the least developed corner

## Section 5: What selection theorems do we expect and want

### 5.1 Broad and robust optima, not just high ones
- Broad = neighbors in parameter space also decent (selection reaches a design only through its neighbors; isolated high peaks are unreachable); robust = stays good as the environment varies (finite samples reward robustness)
- Broad/robust optima are where modularity/abstraction/explicit goals plausibly emerge; tentative "small interaction terms -> broad peak" sketch (with the candid sign-error caveat)

### 5.2 The wishlist
- Conjecture 5.x (Modularity): modular variation in the objective -> modular structure
- (Natural abstractions): convergence on shared high-level abstractions; natural abstraction hypothesis (far-propagating info is summarized)
- (Goals over latents): goals take abstract latents as inputs, not bet-able outcomes; description-length-minimization = utility-maximization hint
- (Subagent structure): goals as a set of utilities (moral insights as Pareto trades among subagents)
- (Mesa-optimization / runtime search): complex variable environments -> defer optimization to runtime = general-purpose search = agency; reframes inner optimizers as expected, not a freak failure
- (Internal architectural modularity): separate modules for world-model, goal, search
- Environment assumptions: modular variation, complexity/variability, finite sampling, abstraction availability

### 5.3 Why this matters for alignment
- Interpretability if modular with explicit components; why trained systems might have structure (breadth argument); risk register (mesa-optimizer proxy goals, alignment tractable iff latents line up, modular agents structurally capable of feigning compliance)

## Section 6: Takeaways

- Representational (complete class: any non-dominated agent *can be described* as EU max) vs mechanistic (selection theorems: what agents *are* and what pressures build them); complementary halves
- Inherits the measuring-stick problem (what is a resource, from physics) from consequentialist foundations; shares the physical bottom-up stance with optimization-and-thermodynamics; the realistic Bayesian-agent picture as a true-name hypothesis for world-models; runtime-search conjecture as a true-name hypothesis for general-purpose search; conjectures not yet theorems; candor about which assumptions to attack

## Sources

- Wentworth, *Selection Theorems: A Program For Understanding Agents* (full)
- Wentworth & Lorell, *How We Picture Bayesian Agents* (full)
- Wentworth, *What Selection Theorems Do We Expect/Want?* (full)
- Connections: consequentialist foundations (coherence, measuring stick); optimization-and-thermodynamics (optimization as entropy reduction, general-purpose search)
