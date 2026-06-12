# Optimization and Thermodynamics (lecture notes)

Article-class lecture notes, ~15 pages. Project: `projects/optimization-thermodynamics/main.tex`. Compiled PDF: `targets/optimization-thermodynamics.pdf`.

**Title:** Optimization and Thermodynamics
**Subtitle:** From convergent attractors to algorithmic entropy, and what physics charges an embedded agent for steering the world

**Abstract:** Three-stage development: (1) optimization made precise as optimizing systems (Flint) and translated into local entropy reduction; (2) physical constraints: second law from reversibility, Touchette-Lloyd bound, three types of optimization under information conservation; (3) the subjectivity problem of Gibbs-Shannon entropy and its resolution by algorithmic thermodynamics (Ebtekar-Hutter), ending with knowledge as an endogenous physical resource (algorithmic mutual information as the budget for optimization).

## Section 1: Orientation: why thermodynamics belongs in agent foundations

- Agent foundations seeks robust concepts ("true names"); these notes target the true name of optimization, from the descriptive direction
- Two reasons thermodynamics enters: optimization is local entropy reduction (second law, fluctuation theorems, erasure costs constrain it); embedded agents pay for knowledge in physical currency (knowledge = physically encoded memory)
- Value for physics-background readers is translation, not new results
- Plan paragraph (roadmap of sections); prerequisites: basic discrete probability only

## Section 2: Information-theoretic language

- Definition 2.1: Shannon entropy, Shannon codelength $\log 1/\mu(x)$, conditional entropy, mutual information, KL divergence
- Lemma 2.2: log-sum inequality (used to prove the second law)

## Section 3: Optimization as a physical phenomenon

### 3.1 Optimizing systems

- Definition 3.1 (Flint): optimizing system = tends from broad basin of attraction to small target configuration set, despite perturbations
- Example 3.2: computing sqrt(2) by gradient descent (robust to debugger overwriting the estimate mid-run)
- Example 3.3: ball in valley (weak optimizing system) vs billiard balls (not one)
- Example 3.4: building a house (sealed-chamber version)
- Three axes: robustness (basin rim, "death"), duality (engine vs object; tree as non-dualistic), retargetability (microscopic perturbation redirects target; signature of agent-like structure)

### 3.2 From improbability to entropy

- Yudkowsky: optimization power as improbability of outcome (top $2^{-k}$ fraction = $k$ bits)
- Translation: initial configuration $X$, final $Y$, entropy reduction $\Delta H = H(X) - H(Y)$; broad basin = large $H(X)$, narrow target = small $H(Y)$
- Remark 3.5: $\Delta H$ drops the goal direction; EU maximization decomposes into entropy reduction + distribution shifting (these notes cover the first part)

## Section 4: Reversibility and the second law

### 4.1 The funneling picture is globally impossible

- Microdynamics are bijective; funneling is many-to-one; quoted claim: optimization lives in coarse-grained subsystem descriptions and the squeezed-out information must go somewhere

### 4.2 Coarse-graining and the second law

- Markovian coarse-graining of phase space; $P(y,x)$ = fraction of cell $x$ flowing to $y$; Markov property as source of the arrow of time; footnote: Liouville measure stationary, equal cells give doubly stochastic $P$
- Theorem 4.1 (second law for doubly stochastic chains): $H(Y) \ge H(X)$, proved via log-sum/data-processing with counting measure
- Remark 4.2: second law does not forbid subsystem entropy reduction; it imposes bookkeeping; statistical not absolute

### 4.3 A fully explicit toy world: the coin engine

- Wentworth's setup: cold pool ($p=0.1$, 0.47 bits/coin), hot pool ($p=0.2$, 0.72 bits/coin); heads = energy
- Three rules: reversibility, heads conservation, designer viewpoint (choose transformation without looking; machine's own observations are internal reversible transformations; transfers to embedded AIs)
- Work extraction = compression problem; no work from single pool (maxentropic-subject-to-constraint cannot be compressed: 0.36n heads needed vs 0.2n available); two pools at different temperatures yield $w \approx 0.011n$
- Remark 4.3: uncertainty is moved, not destroyed; optimization as compression; negentropy (gap to constrained maxent) is the fuel

## Section 5: Steering costs information: the Touchette-Lloyd theorem

### 5.1 Setup

- Environment $X \to Y$ under dynamics $P(Y|X,A)$; policy $P(A|X)$; blind ($I(X;A)=0$) vs sighted policies
- $\Delta H^{max}_{blind}$ = best blind entropy reduction over all initial distributions (need not be zero)
- Theorem 5.2 (Touchette-Lloyd): $\Delta H \le \Delta H^{max}_{blind} + I(X;A)$
- Selection-theorem reading: observed entropy reduction beyond blind baseline implies that many bits of mutual information (optimization implies modeling)

### 5.2 A worked example: the guessing game

- 5-bit string game with $f(x,a) = 00000$ if $a=x$ else $x$; blind optimum 4.94 bits; table of $H(Y)$ vs bits observed (4.94 / 4.85 / 4.63 / 4.11 / 2.83 / 0)
- Example 5.3: noise-cancelling headphones vs earplugs
- Remark 5.4: mutual information necessary but not sufficient (bitwise-NOT policy has 5 bits, zero reduction)

## Section 6: Three types of optimization under information conservation

- Universe decomposed into agent $A$, subsystem $S$, environment $E$; $H(S)$ falls, joint entropy cannot
- Type 1: dump waste heat into environment (refrigerator, builder)
- Type 2: measurement, absorb entropy into agent's memory; Maxwell's demon; reversibility forces the memory record (two-histories argument)
- Type 3: spend pre-existing mutual information; derivation: erase the copy of $I(S_t;A_t)$ inside $S$, joint entropy exactly unchanged, no waste heat
- Demon reframed as copy step (buy correlation) + control step (spend it); parallel with Touchette-Lloyd flagged, made rigorous in Section 8.4
- Summary list of the three channels

## Section 7: The trouble with subjective entropy

### 7.1 Entropy is supposed to measure capacity to optimize

- Demon's free memory (size minus stored entropy) = remaining optimization capacity; should be objective

### 7.2 But the standard definitions are relative to a subjective ensemble

- Stochastic entropy $\hat H(x,\mu) = \log 1/\mu(x)$ requires exogenous $\mu$; Gibbs-Shannon = its mean; footnote: general $\pi$ version
- Equilibrium = the regime where $\mu$ is a useful summary: (1) simple, (2) concentrating, (3) $x$ typical; then all entropies agree
- Three failure modes keyed to the three conditions: point mass on complex state (knowledge cost unaccounted); robot battery coin-flip (no concentration, mean work misleading); atypical compressible state (work underestimated, apparent second-law violation)
- Demon puzzle: does our belief change the demon's capacity? Standard formulation makes capacity observer-relative
- For agent foundations this is the central case: memories, records, computations lack natural ensembles

## Section 8: Algorithmic thermodynamics

### 8.1 Kolmogorov complexity in five minutes

- $K(x)$ = shortest program length; $K(x|y)$; algorithmic mutual information $I(x:y)$; footnote on self-delimiting programs and chain-rule fine print
- $K$ as optimal lossless compression; concentrated particles = low $K$; "low entropy" = "compressible" per individual state
- Notation $\stackrel{+}{<}$ etc. for additive constants
- Three facts: (1) machine-dependence physically negligible (12 GiB interpreter $< 10^{-12}$ J/K; 1 bit $= k_B \ln 2$); (2) agreement with Shannon picture where it applies ($K(x|\mu) \le \log 1/\mu(x)$, Zurek's relation $H(\mu) = \langle K(X|\mu)\rangle$; resolves the three failure modes); (3) uncomputability is a feature (computable entropy admits a perpetual-motion program: find-and-erase argument)

### 8.2 The algorithmic second law

- Theorem 8.2 (informal Levin/Ebtekar-Hutter): w.p. $> 1-\delta$, $K(X_s) - K(X_t) \stackrel{+}{<} K(t-s) + \log(1/\delta)$
- Interpretation of both allowance terms: chance fluctuations ($\delta = 2^{-1000}$ costs a kilobit) and Poincare recurrence ($K(t-s)$)
- Holds per trajectory, no exogenous initial distribution
- Deterministic case: $K(f(x)) \stackrel{+}{=} K(x)$; entropy production requires randomness

### 8.3 Work, heat, and Landauer's principle

- Algorithmic free energy $F(x) = E(x) - k_B T \ln 2 \cdot K(x)$; work bound; slogan: $K$ gives actual capacity from a state, $H(\mu)$ the prior-knowledge mean (resolves robot battery)
- Algorithmic Landauer: $\Delta K + Q/(k_B T \ln 2) \stackrel{+}{>} -\log(1/\delta)$; erasure = reduction in description complexity; digits-of-pi corollary (uncompute instead of dissipate); incompressible data costs heat to clear

### 8.4 Maxwell's demon, exactly

- Full measurement then erasure: $(0,x) \mapsto (x,x) \mapsto (x,0)$, all $K$'s equal up to constants; erasure permitted because a copy exists; last-copy erasure $(x,0) \mapsto (0,0)$ forbidden (not injective or not simply describable); clearing memory costs $k_B T \ln 2 \cdot K(x)$ heat (Szilard recovered)
- Partial measurement: $(0,x) \mapsto (m(x),x) \mapsto (m(x),y)$ gives Equation (1): $K(x) - K(y) \stackrel{+}{<} I(m(x):x)$, attainable with equality when the correlation is fully reversibly spent
- Equation (1) = single-shot algorithmic counterpart of Touchette-Lloyd and rigorous form of Type 3; subjective entropy $K(x|m(x))$ vs objective $K(x)$

## Section 9: Knowledge as a physical resource: optimization for embedded agents

### 9.1 From exogenous to endogenous knowledge

- Gibbs-Shannon $\mu$ lives in the modeler's ledger; embedded agency: no such ledger exists
- Agent's knowledge of environment = algorithmic mutual information $I(a:s)$ between memory state and environment state; objective relation between physical states
- $I(a:s)$ is the steering budget (by Eq. (1)), spendable bit for bit; "knowing more lets you do more" as a theorem of physics

### 9.2 The three types, sharpened by universal computation

- Type 1: compress waste before releasing it (must precede thermalization)
- Type 2: memory cost is $K(x)$, not raw measurement length
- Type 3: budget is algorithmic mutual information; simple rooms are cheap to know
- Duality: $K(x)$ = minimal memory for Type 2 = minimal knowledge for Type 3

### 9.3 Dissolving the subjectivity, and the demon's objective capacity

- Demon's capacity = free memory = total minus description complexity of contents; compressible contents recoverable, incompressible irreducibly occupied; observer-independent
- The subjective appearance mislocated something real: our belief update is physically represented in our brains = we gained algorithmic mutual information with the demon's memory, itself spendable via Type 3; every ledger is somebody's memory

### 9.4 Back to optimizing systems

- An optimizing system's funneling requires one of the three balancing channels; beating the blind baseline implies containing mutual information with the steered system (thermodynamic root of selection theorems)
- Robustness/duality/retargetability reread physically: funneling capacity, localized ledger, compactly encoded target

## Section 10: Takeaways

- Seven summary bullets: optimizing systems and entropy reduction; second law from reversibility; three balancing channels; Touchette-Lloyd ensemble + algorithmic single-state bounds; subjectivity failure of Gibbs-Shannon; algorithmic thermodynamics fixes (objective per-state entropy, second law with priced fluctuations, Landauer, $K$-determined work capacity); knowledge as endogenous consumable resource

## Sources and further reading

- Flint, The ground of optimization (2020); Yudkowsky, Measuring optimization power (2008); Wentworth, Generalized heat engine (2020); Harwood & Altair, Touchette-Lloyd post (2025) + Touchette & Lloyd, Physica A (2004); Daniel C & Ebtekar, Algorithmic thermodynamics and three types of optimization (2025); Ebtekar & Hutter, Foundations of algorithmic thermodynamics, Phys. Rev. E (2025, arXiv:2308.06927)
- Pointer to the Agent Foundations slide deck for broader context
