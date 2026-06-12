# Optimization and Thermodynamics (lecture notes)

Article-class lecture notes, 34 pages, fully pedagogical and self-contained. Project: `projects/optimization-thermodynamics/main.tex`. Compiled PDF: `targets/optimization-thermodynamics.pdf`.

**Title:** Optimization and Thermodynamics
**Subtitle:** From convergent attractors to algorithmic entropy, and what physics charges an embedded agent for steering the world

**Abstract:** Three-stage development: (1) optimization made precise as optimizing systems (Flint) and translated into local entropy reduction; (2) physical constraints: second law from reversibility, the generalized heat engine of biased coins, the Touchette-Lloyd theorem, three types of optimization under information conservation; (3) the subjectivity problem of Gibbs-Shannon entropy and its resolution by algorithmic thermodynamics (Ebtekar-Hutter), ending with knowledge as an endogenous physical resource (algorithmic mutual information as the budget for optimization).

## Section 1: Introduction: why thermodynamics belongs in agent foundations

- Robust concepts ("true names"); the descriptive direction for the true name of optimization
- Reason 1 in full prose: optimization is local entropy reduction (stochastic thermodynamics holds far from equilibrium and constrains optimization processes)
- Reason 2 in full prose: embedded agents pay for knowledge in physical currency (dualistic vs embedded agents; knowledge must be physically encoded)
- Translation value for physics readers; self-containedness promise for non-physics readers; plan paragraph; prerequisites (elementary discrete probability only)

## Section 2: A self-contained toolkit: probability, entropy, information

### 2.1 Random variables and notation
### 2.2 Entropy

- Definition 2.1 (Shannon entropy); Example 2.2 calibrating entropy: fair coin 1 bit, deterministic 0, uniform n-bit strings n bits, biased coin $h(p)$ with $h(0.2) \approx 0.72$ and $h(0.1) \approx 0.47$ (foreshadowing the coin engine)

### 2.3 The coding interpretation

- Source coding theorem informally; Example 2.3: the (1/2, 1/4, 1/8, 1/8) code with mean length 1.75 = entropy
- Definition 2.4 (Shannon codelength / stochastic entropy / surprisal); explicit warning that "entropy of an individual outcome" is undefined without a distribution (crux of Section 8)

### 2.4 Joint and conditional entropy, and mutual information

- Conditional entropy, chain rule with coding reading; Definition 2.6 (mutual information); Example 2.7 calibrating MI (two coin flips vs first flip: 1 bit)

### 2.5 Divergence and two workhorse inequalities

- KL divergence with coding reading (works for unnormalized references)
- Lemma 2.9 (log-sum inequality) with proof via Jensen; Gibbs' inequality; nonnegativity of MI; data processing deferred to Section 4

## Section 3: What is optimization?

### 3.1 Two everyday notions, and the question that links them (CS vs engineering optimization)
### 3.2 Optimizing systems

- Definition 3.1 (optimizing system, Flint): basin of attraction, target configurations, robustness to perturbation
- Example 3.2: computing sqrt(2) by gradient descent, with the debugger-overwrite experiment in full
- Example 3.3: ball in valley (weak but genuine) vs billiard balls and satellite (non-examples)
- Example 3.4: building a house in a sealed chamber
- Death of an optimizing system = perturbation past the basin rim; tree and forest fire; existential catastrophe in this vocabulary

### 3.3 Three axes for comparing optimizing systems

- Robustness (self-driving car example), duality (robot+vase vs tree; optimization does not require an agent), retargetability (compact target representation as agent signature)

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

### 4.5 What the second law does and does not forbid (subsystems may decrease; ensemble vs trajectory; fixed P vs observing agents; the exogenous mu foreshadowed)

## Section 5: A thermodynamics of biased coins: the generalized heat engine

### 5.1 The designer's viewpoint (refrigerator designer; uncertainty moved not reduced; machines observing while running are inside the formalism; transfers to embedded AIs)
### 5.2 The setup: coins, transformations, and two conservation laws

- Cold pool p=0.1 (0.47 bits/coin), hot pool p=0.2 (0.72 bits/coin); heads = energy
- Three rules: reversibility, heads conservation, no peeking
- Wentworth's conditional-swap example transformation analyzed (reads one part, acts on another, reversible, conservative)

### 5.3 Extracting work is a compression problem (work coins; invertibility forces H(X')=H(X); certainty here requires uncertainty there)
### 5.4 No work from a single heat bath

- The 0.72n bits / 0.36n heads vs 0.2n heads contradiction in full
- General maxentropic-subject-to-constraint argument; negentropy defined; type-2 perpetual motion impossible

### 5.5 Work from two heat baths at different temperatures

- Joint state not maxentropic; the explicit equation $(2n-w)\,h((0.3n-w)/(2n-w)) = 1.19n$; solution w ≈ 0.011n; Carnot caveat (marginal vs total conversion)

### 5.6 What the toy world teaches (four lessons in prose; everything was blind; the bridge question "what if it could look?")

## Section 6: Steering costs information: the Touchette-Lloyd theorem

### 6.1 From optimization to modeling: the question (selection theorems; agent structure problem; Wentworth's "bits of optimization per bit of observation"; footnote with full provenance: Touchette-Lloyd 2004 Theorem 10, 2000 paper, Lloyd 1989, good regulator + internal model principle comparison)
### 6.2 The setup: environments, actions, policies (X, A, Y; policy and dynamics)
### 6.3 Blind and sighted policies

- Definition 6.1; blind includes deterministic and privately randomized rules; coin engine = blind policies
- Naive conjecture refuted (contracting dynamics reduce entropy unaided); definition of blind baseline $\Delta H^{max}_{blind}$ over all initial distributions and blind action distributions

### 6.4 A worked example: the guessing game, played blind

- The 5-bit game with f(x,a); why a=00000 is the wasted move (output exactly uniform)
- Full computation for a=11111: P(00000)=1/16, P(11111)=0, others 1/32, H(Y) = 4.94 bits
- Non-uniform initial distributions remark

### 6.5 The same game, played sighted (k observed bits strategy; full table of H(Y) and ΔH for k=0..5)
### 6.6 Mutual information measures sightedness (inferring 2 bits of X from observing A=10111; H(X|A)=3; I=2; estimable from joint statistics)
### 6.7 The theorem

- Theorem 6.2 (Touchette-Lloyd): $\Delta H \le \Delta H^{max}_{blind} + I(X;A)$
- Contrapositive selection-theorem reading; "anyone who beats 4.94 bits must have peeked"

### 6.8 What the theorem does not say

- Information can fail to help (action-independent dynamics) or be squandered (bitwise-NOT policy: 5 bits MI, zero reduction, worse than blind)
- Example 6.3: noise-cancelling headphones (earplugs as blind policy exploiting fixed structure; active cancellation as sighted; music playing as entropy-increasing choice)
- Remark 6.4: the coin engine and the theorem as two halves of one picture

## Section 7: Three types of optimization under information conservation

### 7.1 The bookkeeping problem (agent A, subsystem S, environment E; exhaustive classification)
### 7.2 Type 1: dump waste heat into the environment (refrigerator, builders, conditional swaps; agent as broker)
### 7.3 Type 2: absorb the entropy into the agent's memory (measurement)

- Maxwell's demon told in full; the two-histories reversibility argument for why the memory must fill
- Memory as exhaustible buffer; clearing memory converts Type 2 to Type 1 (Landauer foreshadowed)

### 7.4 Type 3: spend mutual information you already have

- Full joint-entropy derivation: erasing the subsystem's copy of $I(S_t;A_t)$ leaves joint entropy exactly unchanged
- Example 7.1 (controlled-NOT): one-bit worked instance with complete bookkeeping

### 7.5 The demon reframed, and the recap (copy step = Type 2 purchase, control step = Type 3 expenditure; Touchette-Lloyd as the ledger of the control step; the three channels compose in cycles)

## Section 8: The trouble with subjective entropy

### 8.1 Entropy is supposed to measure the capacity to optimize (demon's free memory; the question of objectivity)
### 8.2 The exogenous distribution

- Codelength is a property of (state, distribution) pairs; mu as exogenous knowledge
- The three conditions for mu to be a useful summary: simplicity, concentration, typicality; equilibrium lives inside this regime

### 8.3 Three ways the ensemble picture fails

- Failure of simplicity: point mass on intricate state, knowledge booked at zero cost
- Failure of concentration: robot battery coin-flip, H(mu) describes no actual state
- Failure of typicality: patterned gas configuration, work underestimated, clever machine falsely branded a second-law violator

### 8.4 The demon's capacity, and why this is the central case for agent foundations (observer-relative capacity absurdity; classical macrovariables unsuited to memories; memory states are stable and meaningful, not thermalizing; agent-relevant states are exactly the failure cases)

## Section 9: Algorithmic thermodynamics

### 9.1 Kolmogorov complexity

- Definition 9.1: K(x), K(x|y), algorithmic mutual information; footnote on self-delimiting programs (Kraft inequality) and chain-rule fine print
- Calibrating examples: million zeros, digits of pi, quantum-random bits, particles in a corner; "low entropy is compressibility"
- Algorithmic MI calibration; the additive-constant notations

### 9.2 Why K deserves to be called entropy

- Machine-dependence physically negligible (12 GiB interpreter < 10^-12 J/K; 1 bit = k_B ln 2 ≈ 9.57e-24 J/K)
- Agreement with Shannon: $K(x|\mu) \le \log 1/\mu(x)$ for all x, near-tight for typical samples, Zurek's identity $H(\mu) = \langle K(X|\mu)\rangle$; Boltzmann macrostates as the uniform-set case; the bookshelf example; cheapest simple description wins
- The three failure modes of Section 8 resolved one by one
- Uncomputability as load-bearing: upper semicomputability; Chaitin's incompleteness in one line; the perpetual-motion argument against any computable entropy (find-certified-complex-state, then compute-copy-uncompute erasure)

### 9.3 The algorithmic second law

- Theorem 9.2 (informal Levin/Ebtekar-Hutter): w.p. > 1-δ, $K(X_s) - K(X_t) \le^+ K(t-s) + \log(1/\delta)$
- Per-trajectory, no initial distribution; both allowance terms explained with magnitudes (kilobit fluctuations ≈ 10^-20 J/K; Poincare recurrence priced by K(t-s); simply specified times)
- Corollary 9.3: deterministic simple dynamics cannot change K; entropy production requires randomness; random-bijection picture

### 9.4 Heat, temperature, and Landauer's principle

- Heat reservoir, Boltzmann entropy B(E), temperature as marginal exchange rate (k_B T ln 2 joules per bit); footnote tying to unequal-volume coarse-graining
- Equation (2), algorithmic Landauer: $\Delta K + Q/(k_B T \ln 2) \ge^+ -\log(1/\delta)$; erasure as complexity reduction, observer-free
- Landauer cost vs EP cost decomposition; misconception 1 (logical irreversibility need not cost heat: uniform-overwrite example); misconception 2 (Landauer costs cancel long-run; energy bill = EP cost; reversible computing)

### 9.5 The thermodynamic costs of information processing

- Randomization (negative Landauer cost; reversible harvest from reservoir vs careless scavenging)
- Computation (deterministic outputs are pseudo-entropy; uncompute vs thermalize; structure destroyed by mixing)
- Measurement (reversible copy, undoable; discarded mutual information is entropy production; the K(x,y) three-term decomposition)
- Unifying principle: negentropy exchanged, hidden, or stored as correlation; all costs are EP costs at machinery/information mismatches

### 9.6 Maxwell's demon, exactly

- Full measurement then erasure: $(0,x) \to (x,x) \to (x,0)$ with all K's $=^+$ K(x); erasure permitted because a copy exists; last-copy clearing forbidden (not injective or not simply describable); the Landauer bill for memory reset; Szilard as a two-line calculation
- Partial measurement: $(0,x) \to (m(x),x) \to (m(x),y)$; full chain-rule derivation of Equation (3), boxed: $K(x) - K(y) \le^+ I(m(x):x)$; attainable with equality when correlation fully and reversibly spent
- Term-by-term comparison with Theorem 6.2: ensemble vs single-shot versions; rigorous form of Type 3
- Objective entropy K(x) vs subjective entropy K(x|m(x)); optimization power as the wedge; subjectivity located, not banished

### 9.7 An information engine: compressible strings as fuel

- Negentropy = compressibility m - K(z); memory with zero-padding reserve; fixed compressor with worst-case blowup c
- Burn / eat / digest cycle; zeros as ancilla bits embedding irreversible operations reversibly (overwrites, error correction, repair); demon's blank memory as ancilla
- Organism/genome illustration (the YummyAlphabetSoup cycle in prose); starvation on incompressible fuel
- The inversion: coin engine needed ensemble knowledge at design time, information engine needs no distributional assumptions

## Section 10: Knowledge as a physical resource: optimization for embedded agents

### 10.1 From exogenous to endogenous knowledge

- The two frameworks side by side; no ledger exists; knowledge = $I(a:s) =^+ K(s) - K(s|a)$, an objective relation between pieces of matter
- Subjective beliefs implemented, not eliminated; K(s|a) as the environment's entropy as that agent finds it
- Three directions certifying the resource claim: algorithmic Touchette-Lloyd (attainable budget), Type-3 consumptiveness, perishability (decay of stale correlation)
- The slogan: knowledge about the world = capacity to optimize the world beyond blind baselines, as a theorem with fixed exchange rates

### 10.2 The three types, sharpened by universal computation

- Type 1: compress waste before thermalization; Type 2: memory bill is K(x) not raw transcript; Type 3: simple worlds cheap to know via computation alone
- The duality: K(s) = minimal Type-2 memory = minimal Type-3 knowledge

### 10.3 Dissolving the subjectivity

- Demon's capacity objective (free memory via description complexity of contents; compressible recoverable, incompressible irreducible)
- Whose physics the changing beliefs belong to: our update = physical change in our brains = acquired algorithmic MI, itself spendable; "every ledger is somebody's memory"

### 10.4 Back to optimizing systems

- Funneling requires the three channels; robustness = entropy-disposal capacity; beating the blind baseline forces internal mutual information (selection-theorem root: world models as conserved-quantity requirement); duality = localized bookkeeping; retargetability = compact rewritable target records

## Section 11: Takeaways

- Eight summary bullets covering the full arc (optimizing systems, second law from reversibility, coin-world lessons, Touchette-Lloyd, three types, subjective entropy failures, algorithmic thermodynamics results, endogenous knowledge)

## Sources and further reading

- Flint (2020), Yudkowsky (2008), Wentworth (2020, + Utility Maximization = Description Length Minimization 2021), Harwood & Altair (2025) + Touchette & Lloyd (2004, 2000) + Lloyd (1989), Daniel C & Ebtekar (2025), Ebtekar & Hutter (Phys. Rev. E 2025, arXiv:2308.06927), each annotated with which sections it grounds
- Pointer to the Agent Foundations slide deck for the broader module context
