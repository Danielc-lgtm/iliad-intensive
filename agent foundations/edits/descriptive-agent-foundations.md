# Descriptive Agent Foundations (lecture notes)

Article-class lecture notes, fully self-contained for a reader who has never met functional programming, Bayes nets / Pearlean causality, dynamic programming, or type signatures: causal diagrams, recursion, message passing, lazy evaluation, latent variables, caching, the Bellman equation, and the (A→B)→A type are each built from a concrete example. Project: `projects/descriptive-agent-foundations/main.tex`. Compiled PDF: `targets/descriptive-agent-foundations.pdf`.

**Title:** Descriptive Agent Foundations
**Subtitle:** What real agents are made of, and why those structures keep getting built

**Abstract:** Normative agent foundations asks what an ideal agent ought to be; descriptive foundations asks what agents actually arise in the physical world and why that machinery keeps being produced. The organizing tool is the selection theorem (a pressure selects for a particular type signature). Three steps: (1) what a type signature is, and why coherence theorems are one flawed selection theorem; (2) a precise, from-scratch picture of the structure a real embedded agent has (a self-referential web of causes around hidden summary variables, lazily evaluated, with goals over the hidden variables); (3) the wish list of selection theorems and the pivotal move to reachable (broad/robust) optima. Representational (coherence) vs mechanistic (selection) framing throughout.

## Section 1: Two ways to ask what an agent is

- Normative (ideal agent, coherence theorems, behavior from outside) vs descriptive (start from the world; an agent-free causal substrate that nonetheless produces agents)
- The descriptive goal: locate any system's goals/world-picture/decision structure, and explain why such structures arise
- Bottom-up methodology; the selection theorem as the descriptive analogue of the coherence theorem; plan; only probability-as-belief assumed

## Section 2: What is "the structure" of an agent?

- Type signature built by analogy to a recipe/function (what goes in, what comes out)
- Definition 2.1 (type signature): representation (what parts, stored as what), interfaces (inputs/outputs and connections), embedding (abstract -> low-level physical system)
- The (A→B)→A shorthand unpacked from scratch: "A to B" = a model (action -> outcome); an agent takes a model and returns an action; which regions of the substrate round off into this type
- Why the three questions are exactly what alignment needs answered

## Section 3: Selection theorems

### 3.1 What a selection theorem is
- Definition 3.1 (selection theorem): something about the type signature/properties selected for by a pressure (natural selection, ML training, market competition) in a broad environment class; need not mention selection; large attackable surface area

### 3.2 The coherence theorems as a (flawed) selection theorem
- Representation = utility + distribution; interfaces = bets in, EU-max action out, Bayes update; embedding = behavioral
- Too-strong assumptions (fixed, complete, path-independent preferences) fail for real agents; right form, wrong assumptions/conclusion; the bet that better assumptions give better type signatures

### 3.3 Other selection theorems we already have
- Good Regulator / Gooder Regulator (world-models selected for); Kelly criterion (expected-log-wealth from long-run growth); subagents argument (internal state -> a committee of utilities)

### 3.4 The research program
- Forward (observation -> generalize; sessile organisms lack brains) and backward (from structure, or from pressure); incremental (apply-and-fix, as subagents came from markets; strengthen; patch; unify; minimize assumptions)
- The ambitious claim: good selection theorems get most of the way to the hardest parts of safety

## Section 4: How we picture a real agent

- The textbook image (enumerate all worlds, assign probabilities, update, sum) is only a *behavioral* spec; impossible to implement when embedded

### 4.1 A web of causes, not a table of worlds
- Causal diagram / Bayes net explained from scratch (variables as dots, arrows = direct influence); stores local dependencies, grows linearly not exponentially (road map vs every route)
- Recursive submodels: the factorial self-referential rule encodes an unbounded diagram with a finite description; world-model = a moderately-sized self-referential program

### 4.2 Updates that travel only where they matter
- Message passing explained from scratch (updates ripple along arrows like a rumor); messages shrink to nothing over long weak chains; the bird-vs-gasoline example (stop early; leave most of the model untouched)

### 4.3 Choosing without computing everything
- Never compute an absolute expected utility; compute the *difference* between options; the difference is zero across nearly all the world (lamb vs burrito leaves your career and distant nations unchanged), so it dies out and only the few differing things are queried

### 4.4 Goals attached to hidden quantities
- Latent variable defined from scratch (a hidden quantity posited to explain observed correlations); the tree example (bark/leaves/roots -> "tree"); latents need not be real (spirits) but mostly are (natural abstraction); goals' inputs are latents (spouse *actually* happy vs *looks* happy)

### 4.5 Reusing stored answers, and the price of doing so
- Caching / dynamic programming explained from scratch; the Bellman equation as a consistency condition (value here = best step + value there); stale caches go inconsistent; repair needs propagation = thinking/reflection (explains human cognitive effort and apparent non-Bayesian quirks)
- The assembled hypothesis; self-representation as the least developed corner

## Section 5: What selection theorems we want, and what selection can reach

### 5.1 Reachable optima, not merely high ones
- Broad = neighbors in design space also decent (selection reaches a design only through its neighbors; isolated high peaks unreachable by mutation/gradient steps); robust = stays good as the environment varies (finite samples reward robustness)
- Broad/robust optima are where modularity/abstraction/explicit goals emerge; tentative "weak interactions -> broad peak" sketch (with the candid sign-error caveat)

### 5.2 The wish list
- Conjecture (Modularity): modular variation in the objective -> modular structure
- (Natural abstractions): convergence on shared high-level summaries; natural-abstraction hypothesis (far-relevant info is compressed)
- (Goals over hidden variables): goals take latents as inputs, not bet-able outcomes
- (A committee of goals): goals as a set of utilities (moral insights as multi-party Pareto trades)
- (Optimizers inside optimizers): complex variable environments -> defer optimization to runtime = general-purpose search = agency; reframes mesa-optimizers as expected, not a malfunction
- (Separate modules): distinct parts for world-model, goal, search
- Environment assumptions: modular variation, complexity/variability, finite sampling, abstraction availability

### 5.3 Why this matters for AI safety
- Interpretability if modular with explicit parts; why trained systems might have structure (reachability); risk register (mesa-optimizer proxy goals, alignment tractable iff hidden variables line up, modular agents structurally able to feign compliance)

## Section 6: Takeaways

- Representational (complete class: any undominated agent *can be described* as EU max) vs mechanistic (selection theorems: what agents *are* and what builds them); complementary halves
- Inherits the measuring-stick problem from consequentialist foundations; shares the physical bottom-up stance with optimization-and-thermodynamics; the real-agent picture as a true-name hypothesis for world-models; runtime-search conjecture as a true-name hypothesis for general-purpose search; conjectures not yet theorems; candor about which assumptions to attack

## Sources

- Wentworth, *Selection Theorems: A Program For Understanding Agents* (full)
- Wentworth & Lorell, *How We Picture Bayesian Agents* (full)
- Wentworth, *What Selection Theorems Do We Expect/Want?* (full)
