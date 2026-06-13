# Optimization and Thermodynamics (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/optimization-thermodynamics/main.tex`. Compiled PDF: `targets/optimization-thermodynamics.pdf`.

**Title:** Optimization and Thermodynamics
**Subtitle:** From convergent attractors to algorithmic entropy, and what physics charges an embedded agent for steering the world

**Abstract:** Three-stage development: (1) optimization made precise as optimizing systems (Flint) and translated into local entropy reduction; (2) physical constraints: second law from reversibility, then the three types of optimization under information conservation, then the Touchette-Lloyd theorem (which quantifies the third type); (3) the subjectivity problem of Gibbs-Shannon entropy and its resolution by algorithmic thermodynamics (Ebtekar-Hutter), ending with knowledge as an endogenous physical resource (algorithmic mutual information as the budget for optimization). The generalized heat engine of biased coins is developed as a self-contained appendix and referenced from the main text.

## Section 1: Introduction: why thermodynamics belongs in agent foundations

- Robust concepts ("true names"); the descriptive direction for the true name of optimization
- Reason 1 in full prose: optimization is local entropy reduction (stochastic thermodynamics holds far from equilibrium and constrains optimization processes)
- Reason 2 in full prose: embedded agents pay for knowledge in physical currency (dualistic vs embedded agents; knowledge must be physically encoded)
- Translation value for physics readers; self-containedness promise for non-physics readers; plan paragraph (updated to the new section order, with the coin world flagged as an appendix); prerequisites (elementary discrete probability only)

## Section 2: A self-contained toolkit: probability, entropy, information

### 2.1 Random variables and notation
### 2.2 Entropy

- Definition 2.1 (Shannon entropy); Example 2.2 calibrating entropy: fair coin 1 bit, deterministic 0, uniform n-bit strings n bits, biased coin $h(p)$ with $h(0.2) \approx 0.72$ and $h(0.1) \approx 0.47$ (foreshadowing the coin engine)

### 2.3 The coding interpretation

- Source coding theorem informally; Example 2.3: the (1/2, 1/4, 1/8, 1/8) code with mean length 1.75 = entropy
- Definition 2.4 (Shannon codelength / stochastic entropy / surprisal); explicit warning that "entropy of an individual outcome" is undefined without a distribution (crux of Section 7)

### 2.4 Joint and conditional entropy, and mutual information

- Conditional entropy, chain rule with coding reading; Definition 2.6 (mutual information); Example 2.7 calibrating MI (two coin flips vs first flip: 1 bit)

### 2.5 Divergence and two workhorse inequalities

- KL divergence with coding reading (works for unnormalized references)
- Lemma 2.9 (log-sum inequality) with proof via Jensen; Gibbs' inequality; nonnegativity of MI; data processing deferred to Section 4

## Section 3: What is optimization?

### 3.1 Two everyday notions, and the question that links them (CS vs engineering optimization)
### 3.2 Optimizing systems

*(Shortened per author request: Flint's material is now a compact intuition-builder for "optimization as entropy reduction" (§3.5), not the centre.)*

- Definition 3.1 (optimizing system, Flint): basin of attraction, target configurations, robustness to perturbation
- Gradient-descent-computing-sqrt(2) with the debugger-overwrite illustration, plus the sealed-chamber house, compressed to a couple of sentences (the separate sqrt2/house example boxes were removed)
- Example 3.2 (ball in valley): weak but genuine optimizing system; billiards/satellite as non-examples (kept as the one example box, since it is cross-referenced from §6)
- Death of an optimizing system = perturbation past the basin rim; tree and forest fire; existential catastrophe in this vocabulary

### 3.3 Three axes for comparing optimizing systems

- Condensed to one paragraph: robustness (self-driving car), duality (robot+vase vs tree; optimization does not require an agent), retargetability (compact target representation as agent signature)

### 3.4 Measuring optimization in bits

- Yudkowsky's proposal in full prose: rank configurations by preference, ask what fraction would be at least as good at random; fraction $2^{-k}$ = k bits of optimization power
- Flint vs Yudkowsky: whole closed systems vs patch+mind; robustness vs improbability; complementary readings

### 3.5 Optimization as entropy reduction

- $\Delta H = H(X) - H(Y)$; broad basin = large H(X), narrow target = small H(Y)
- Remark 3.5: what the translation drops (the goal); Wentworth's decomposition of EU maximization into entropy minimization + distribution shifting

## Section 4: Reversibility and the second law

### 4.1 Microscopic physics is reversible (phase space, bijective dynamics, Liouville's theorem in words, unitary QM)
### 4.2 Why the funneling picture cannot hold globally (the central bookkeeping principle, displayed quote)
### 4.3 Coarse-graining: where probability enters a deterministic world

- Cells, transition probabilities P(y,x) as volume fractions, randomness as shadow of unresolved detail
- Markov assumption discussed honestly; multibaker maps; the falling-vase arrow-of-time story (forward local statistics vs backward retrodiction)
- Liouville implies stationary volume measure; equal cells imply doubly stochastic P (derivation spelled out); footnote on the general unequal-volume ($\pi$-relative) formalism

### 4.4 The second law of thermodynamics

- Theorem 4.1 with two-step proof: data processing inequality for KL via log-sum, then counting-measure specialization
- Discussion: ingredient list is Markov + double stochasticity = reversibility; "second law follows from reversibility of physics"

### 4.5 What the second law does and does not forbid (subsystems may decrease; ensemble vs trajectory; fixed P vs observing agents; the exogenous mu foreshadowed). Closing transition now leads into the three-types bookkeeping question; the coin-world toy model is pointed to as Appendix A.

## Section 5: Three types of optimization under information conservation

*(Moved to immediately follow the second law. Sets up the bookkeeping question "when a subsystem's entropy falls, where does it go?", and links to the Touchette-Lloyd theorem of Section 6 -- specifically that the third type is what Touchette-Lloyd quantifies.)*

### 5.1 The bookkeeping problem (agent A, subsystem S, environment E; exhaustive classification)
### 5.2 Type 1: dump waste heat into the environment (refrigerator, builders; coin-world conditional swaps referenced to Appendix A; agent as broker)
### 5.3 Type 2: absorb the entropy into the agent's memory (measurement)

- Maxwell's demon told in full; the two-histories reversibility argument for why the memory must fill
- Memory as exhaustible buffer; clearing memory ultimately exports the stored entropy to the environment as Type-1 waste (exact bookkeeping deferred to the demon section, §8.4)

### 5.4 Type 3: spend mutual information you already have

- Full joint-entropy derivation: erasing the subsystem's copy of $I(S_t;A_t)$ leaves joint entropy exactly unchanged
- Example 5.x (controlled-NOT): one-bit worked instance with complete bookkeeping

### 5.5 The demon reframed, and the recap (copy step = Type 2 purchase, control step = Type 3 expenditure). The forward link is now explicit: how much steering per bit of mutual information is exactly the question the Touchette-Lloyd theorem of Section 6 answers, and the section ends by posing it.

## Section 6: Steering costs information: the Touchette-Lloyd theorem

### 6.1 From optimization to modeling: the question (now opens by recalling the Type-3 channel of Section 5 and asking how many bits of steering each bit of mutual information buys; selection theorems; agent structure problem; footnote with full provenance: Touchette-Lloyd 2004 Theorem 10, 2000 paper, Lloyd 1989, good regulator + internal model principle comparison)
### 6.2 The setup: environments, actions, policies (X, A, Y; policy and dynamics)
### 6.3 Blind and sighted policies

- Definition 6.1; blind includes deterministic and privately randomized rules; the coin engine (Appendix A) = blind policies
- Naive conjecture refuted (contracting dynamics reduce entropy unaided); definition of blind baseline $\Delta H^{max}_{blind}$ over all initial distributions and blind action distributions

### 6.4 A worked example: the guessing game, played blind

- The 5-bit game with f(x,a); why a=00000 is the wasted move (output exactly uniform)
- Full computation for a=11111: P(00000)=1/16, P(11111)=0, others 1/32, H(Y) = 4.94 bits
- Non-uniform initial distributions remark

### 6.5 The same game, played sighted (k observed bits strategy; full table of H(Y) and ΔH for k=0..5)
### 6.6 Mutual information measures sightedness (inferring 2 bits of X from observing A=10111; H(X|A)=3; I=2; estimable from joint statistics)
### 6.7 The theorem

- Theorem 6.2 (Touchette-Lloyd): $\Delta H \le \Delta H^{max}_{blind} + I(X;A)$
- **No reversibility assumption:** explicit note that the theorem is a purely information-theoretic (data-processing) inequality holding for arbitrary dynamics, reversible or not -- and why this is consistent with the rest (the second law needed reversibility to forbid global entropy reduction; Touchette-Lloyd needs none to bound steering beyond the blind baseline)
- Contrapositive selection-theorem reading; "anyone who beats 4.94 bits must have peeked"

### 6.8 What the theorem does not say

- Information can fail to help (action-independent dynamics) or be squandered (bitwise-NOT policy: 5 bits MI, zero reduction, worse than blind)
- Example 6.3: noise-cancelling headphones (earplugs as blind policy exploiting fixed structure; active cancellation as sighted; music playing as entropy-increasing choice)
- Remark 6.4: the coin engine (Appendix A) and the theorem as two halves of one picture; explicit identification of $I(X;A)$ with the Type-3 channel of Section 5

## Section 7: The trouble with subjective entropy

### 7.1 Entropy is supposed to measure the capacity to optimize (demon's free memory; the question of objectivity)
### 7.2 The exogenous distribution

- Codelength is a property of (state, distribution) pairs; mu as exogenous knowledge
- The three conditions for mu to be a useful summary: simplicity, concentration, typicality; equilibrium lives inside this regime

### 7.3 Three ways the ensemble picture fails

- Failure of simplicity: point mass on intricate state, knowledge booked at zero cost
- Failure of concentration: robot battery coin-flip, H(mu) describes no actual state
- Failure of typicality: patterned gas configuration, work underestimated, clever machine falsely branded a second-law violator

### 7.4 The demon's capacity, and why this is the central case for agent foundations (observer-relative capacity problem; classical macrovariables unsuited to memories; memory states are stable and meaningful, not thermalizing; agent-relevant states are exactly the failure cases)

## Section 8: Algorithmic thermodynamics

*(The Landauer's-principle subsection and the thermodynamic-costs-of-information-processing subsection were removed per author request. The section's emphasis is now squarely on dissolving the subjectivity problem: K(x) is an objective property of the individual state, the three failure modes of Section 7 are resolved, and the demon's objective-vs-subjective entropy wedge locates rather than banishes subjectivity. The §8 intro and the takeaways now foreground this.)*

### 8.1 Kolmogorov complexity

- Definition 8.1: K(x), K(x|y), algorithmic mutual information; footnote on self-delimiting programs (Kraft inequality) and chain-rule fine print
- Calibrating examples: million zeros, digits of pi, quantum-random bits, particles in a corner; "low entropy is compressibility"
- Algorithmic MI calibration; the additive-constant notations

### 8.2 Why K deserves to be called entropy

- Machine-dependence physically negligible (12 GiB interpreter < 10^-12 J/K; 1 bit = k_B ln 2 ≈ 9.57e-24 J/K)
- Agreement with Shannon: $K(x|\mu) \le \log 1/\mu(x)$ for all x, near-tight for typical samples, Zurek's identity $H(\mu) = \langle K(X|\mu)\rangle$; Boltzmann macrostates as the uniform-set case; the bookshelf example; cheapest simple description wins
- The three failure modes of Section 7 resolved one by one
- Uncomputability as load-bearing: upper semicomputability; Chaitin's incompleteness in one line; the perpetual-motion argument against any computable entropy (find-certified-complex-state, then compute-copy-uncompute erasure)

### 8.3 The algorithmic second law

- Theorem 8.2 (informal Levin/Ebtekar-Hutter): w.p. > 1-δ, $K(X_s) - K(X_t) \le^+ K(t-s) + \log(1/\delta)$
- Per-trajectory, no initial distribution; both allowance terms explained with magnitudes (kilobit fluctuations ≈ 10^-20 J/K; Poincare recurrence priced by K(t-s); simply specified times)
- Corollary 8.3: deterministic simple dynamics cannot change K; entropy production requires randomness; random-bijection picture

### 8.4 Maxwell's demon, exactly

- Full measurement then erasure: $(0,x) \to (x,x) \to (x,0)$ with all K's $=^+$ K(x); erasure permitted because a copy exists; last-copy clearing forbidden (not injective or not simply describable); to reset memory the demon must export K(x) bits to the environment as Type-1 waste (stated in informational terms, no heat/joules)
- Partial measurement: $(0,x) \to (m(x),x) \to (m(x),y)$; full chain-rule derivation of Equation (3), boxed: $K(x) - K(y) \le^+ I(m(x):x)$; attainable with equality when correlation fully and reversibly spent
- Term-by-term comparison with Theorem 6.2: ensemble vs single-shot versions; rigorous form of Type 3
- Objective entropy K(x) vs subjective entropy K(x|m(x)); optimization power as the wedge; subjectivity located, not banished -- the core dissolving-subjectivity payoff

*(The information-engine subsection was removed per author request; §8 now ends with the demon.)*

## Section 9: Knowledge as a physical resource: optimization for embedded agents

### 9.1 From exogenous to endogenous knowledge

- The two frameworks side by side; no ledger exists; knowledge = $I(a:s) =^+ K(s) - K(s|a)$, an objective relation between pieces of matter; subjective beliefs implemented, not eliminated; K(s|a) as the environment's entropy as that agent finds it
- **"Knowing more is being able to do more," made precise** -- leads with the common intuition and formalizes it by composing two bridges, with the implication stated up front (not deferred to the end):
  - *Beliefs → mutual information* (Shannon coding): if memory $a$ encodes a computable belief $q$ (recovered by an $O(1)$ program), the Shannon codeword of the true $s$ under $q$ gives $K(s\mid a) \le^+ \log 1/q(s)$, hence $I(a:s) \ge^+ K(s) - \log 1/q(s)$ -- more probability on the truth = more mutual information
  - *Mutual information → optimization* (algorithmic Touchette-Lloyd): the agent can squeeze up to $I(a:s)$ bits out of the environment, attainably
  - *Composed:* achievable optimization $\ge^+ K(s) - \log 1/q(s)$, so "more probability on the truth ⇒ more optimization" -- the individual-state form of Touchette-Lloyd (Section 6) and the rigorous Type-3 channel (Section 5)
- Bayesian learning read physically: updating raises $q(s)$ ⇒ codelength and residual $K(s\mid a)$ fall ⇒ $I(a:s)$ and reachable optimization rise; certainty limit $K(s\mid a) =^+ 0$, $I(a:s) =^+ K(s)$
- Two further properties: Type-3 consumptiveness; perishability (decay of stale correlation, from the algorithmic second law)
- The slogan: knowledge about the world = capacity to optimize the world beyond blind baselines, at a fixed (informational) exchange rate

### 9.2 The three types, sharpened by universal computation

- Type 1: compress waste before thermalization; Type 2: memory bill is K(x) not raw transcript; Type 3: simple worlds cheap to know via computation alone
- The duality: K(s) = minimal Type-2 memory = minimal Type-3 knowledge

### 9.3 Dissolving the subjectivity

- Demon's capacity objective (free memory via description complexity of contents; compressible recoverable, incompressible irreducible)
- Whose physics the changing beliefs belong to: our update = physical change in our brains = acquired algorithmic MI, itself spendable; "every ledger is somebody's memory"

### 9.4 Back to optimizing systems

- Shortened per author request (Flint's axes de-centred). Key payoff: funneling beyond the blind baseline forces internal mutual information -- a necessary (not sufficient) ingredient of a world model, the thermodynamic seed of the selection-theorems program. Flint's three axes then get brief thermodynamic readings: robustness = entropy-disposal capacity; duality = localized bookkeeping; retargetability = compact rewritable target record

## Section 10: Takeaways

- Eight summary bullets covering the full arc (optimizing systems, second law from reversibility, the three types, Touchette-Lloyd, subjective entropy failures, algorithmic thermodynamics results, endogenous knowledge; the coin-world lessons now carried in Appendix A)

## Appendix A: A thermodynamics of biased coins: the generalized heat engine

*(Moved to an appendix per author request; referenced from the main text wherever a concrete blind-policy example helps -- the blind baseline of Section 6 and the Type-1 channel of Section 5. Opens with a short note on its role and that it can be read any time after Section 4.)*

### A.1 The designer's viewpoint (refrigerator designer; uncertainty moved not reduced; machines observing while running are inside the formalism; transfers to embedded AIs)
### A.2 The setup: coins, transformations, and two conservation laws

- Cold pool p=0.1 (0.47 bits/coin), hot pool p=0.2 (0.72 bits/coin); heads = energy
- Three rules: reversibility, heads conservation, no peeking
- Wentworth's conditional-swap example transformation analyzed (reads one part, acts on another, reversible, conservative)

### A.3 Extracting work is a compression problem (work coins; invertibility forces H(X')=H(X); certainty here requires uncertainty there)
### A.4 No work from a single heat bath

- The 0.72n bits / 0.36n heads vs 0.2n heads contradiction in full
- General maxentropic-subject-to-constraint argument; negentropy defined; type-2 perpetual motion impossible

### A.5 Work from two heat baths at different temperatures

- Joint state not maxentropic; the explicit equation $(2n-w)\,h((0.3n-w)/(2n-w)) = 1.19n$; solution w ≈ 0.011n; Carnot caveat (marginal vs total conversion)

### A.6 What the toy world teaches (four lessons in prose; everything was blind; the bridge question "what if it could look?" pointing to Section 6)

## Sources and further reading

- Flint (2020), Yudkowsky (2008), Wentworth (2020, + Utility Maximization = Description Length Minimization 2021), Harwood & Altair (2025) + Touchette & Lloyd (2004, 2000) + Lloyd (1989), Daniel C & Ebtekar (2025), Ebtekar & Hutter (Phys. Rev. E 2025, arXiv:2308.06927), each annotated with which sections it grounds (the Wentworth coin-engine reference now points to Appendix A)
- Pointer to the Agent Foundations slide deck for the broader module context
