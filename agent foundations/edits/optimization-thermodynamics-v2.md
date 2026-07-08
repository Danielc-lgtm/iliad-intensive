# Optimization and Thermodynamics, Version 2 (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/optimization-thermodynamics-v2/main.tex`. Compiled PDF: `targets/optimization-thermodynamics-v2.pdf`.

**This is V2:** same section structure, theorems, equations, and worked examples as V1, but the prose of every section (Introduction, toolkit, second law, three types, subjective entropy, algorithmic thermodynamics, embedded agency, both appendices) was rewritten in the crisp, intuition-first, signposted, example-led style of the new Section 3, made fully em-dash-free, and run through a critical-correctness pass. The one substantive content change versus V1 is the corrected prediction argument in §3.4 (see that bullet); a redundant footnote in §4.3 was also de-duplicated. V1 (`projects/optimization-thermodynamics/`) is the prior version, with the same §3.4 correction applied.

**V2 editorial pass (style only, substance and structure unchanged):** a harshest-critic pass per `CLAUDE.md` removed residual LLM-prose tells, with no change to any claim, theorem, equation, example, or section ordering. Cut filler frames and inflated topic sentences ("worth flagging/stating/seeing/knowing/internalizing/spelling out", "deserves a careful telling", "most importantly for what follows", "Crucially", "each of independent interest", "it pays to see", "The real payoff", "the answer turns out to") in favor of direct statement. The document was already em-dash-free; this pass tightened the signposting prose around the existing content.

**V2 register pass (prose rewritten toward the source posts' register; substance and structure held constant):** the expository prose was rewritten to read like the LessWrong/AF posts the notes are built on (Wentworth's *Generalized Heat Engine*, Daniel C & Ebtekar's *Algorithmic thermodynamics and three types of optimization*, Harwood & Altair, Flint), calibrated against those posts directly. Moves: lead with the concrete, more direct second-person ("you"/"we"), shorter declaratives interleaved with longer unpacking sentences, fewer balanced/ornate academic constructions, math introduced through plain-language statements. Rewrote the Introduction in full, the §2 openers (toolkit, coding interpretation, codelength caveat), all of §3 (the optimization core: everyday notions, attractors, entropy reduction, the prediction argument, the objectivity argument), the §4.2 framing, and the section openers of §5, §6, §8. The source-derived sections (coin-world Appendix A, Touchette--Lloyd Appendix B, the Maxwell's demon tellings) were already in this register and were left essentially as-is. No claim, theorem, equation, example, number, or section ordering changed; kept em-dash-free and contraction-free (matching the existing text). Recompiled cleanly (31 pages).

**Thesis-register rewrite (2026-07, current state):** per author request, the prose of the entire document was dramatically rewritten so that its writing style is indistinguishable from the author's MSc thesis (`sources/Chiang Sung En-Thesis.pdf`: formal academic "we" voice, long participially-elaborated sentences, heavy signposting, rhetorical-question motivation, bold nominal run-in headers, didactic closures, sparing unspaced em-dashes, American -ize spelling), superseding the earlier LessWrong-register pass described above. Section and subsection titles were renominalized in thesis style (reflected in the headings below); §9's bulleted takeaways became "Summary and conclusions" prose. All theorems, equations, numbers, labels, examples, footnotes, and the section structure are unchanged; the one prose-in-math change is the guessing-game `\text` gloss ("you matched..." -> "the submitted string matches..."). Compiles cleanly at 35 pages. See choices.md Choice #11 for the recorded decisions.

**Title:** Optimization and Thermodynamics (Version 2, revised exposition)
**Subtitle:** From convergent attractors to algorithmic entropy: the thermodynamic cost of optimization for embedded agents (renominalized in the thesis-register pass; formerly "...and what physics charges an embedded agent for steering the world")

**Abstract:** Three-stage development: (1) an optimizer made precise as the *cause* of a convergent attractor (a physical thing whose presence drives the system it acts on, from a broad range of initial conditions and despite perturbations, into a narrow target -- conditioning on the optimizer collapses one's uncertainty about where that system ends up), with the argument that even a pure predictor has an objective, information-theoretic reason to attend to optimizers, so optimization is observer-independent; translated into local entropy reduction in the system acted on; (2) physical constraints: second law from reversibility, then the three types of optimization under information conservation; (3) the subjectivity problem of Gibbs-Shannon entropy and its resolution by algorithmic thermodynamics (Ebtekar-Hutter), ending with knowledge as an endogenous physical resource (algorithmic mutual information as the budget for optimization). The generalized heat engine of biased coins (Appendix A) and the Touchette-Lloyd theorem quantifying the third type (Appendix B) are developed as self-contained appendices and referenced from the main text.

## Section 1: Introduction: the role of thermodynamics in agent foundations

- Robust concepts ("true names"); the descriptive direction for the true name of optimization
- Reason 1 in full prose: optimization is local entropy reduction (stochastic thermodynamics holds far from equilibrium and constrains optimization processes)
- Reason 2 in full prose: embedded agents pay for knowledge in physical currency (dualistic vs embedded agents; knowledge must be physically encoded)
- Translation value for physics readers; self-containedness promise for non-physics readers; plan paragraph (updated: §3 now characterizes the optimizer as the *cause* of a convergent attractor and argues observer-independence; Touchette-Lloyd and the coin world are flagged as appendices); prerequisites (elementary discrete probability only)

## Section 2: Theoretical foundations: probability, entropy, and information

### 2.1 Random variables and notation
### 2.2 Entropy

- Definition 2.1 (Shannon entropy); Example 2.2 calibrating entropy: fair coin 1 bit, deterministic 0, uniform n-bit strings n bits, biased coin $h(p)$ with $h(0.2) \approx 0.72$ and $h(0.1) \approx 0.47$ (foreshadowing the coin engine)

### 2.3 The coding interpretation

- Source coding theorem informally; Example 2.3: the (1/2, 1/4, 1/8, 1/8) code with mean length 1.75 = entropy
- Definition 2.4 (Shannon codelength / stochastic entropy / surprisal); explicit warning that "entropy of an individual outcome" is undefined without a distribution (crux of Section 6)

### 2.4 Joint and conditional entropy, and mutual information

- Conditional entropy, chain rule with coding reading; Definition 2.6 (mutual information); Example 2.7 calibrating MI (two coin flips vs first flip: 1 bit)

### 2.5 Divergence and two fundamental inequalities

- KL divergence with coding reading (works for unnormalized references)
- Lemma 2.9 (log-sum inequality) with proof via Jensen; Gibbs' inequality; nonnegativity of MI; data processing deferred to Section 4

## Section 3: Characterizing optimization

*(Rewritten per author request from `sources/fixed_aim.txt`: Flint's optimizing-system definition, the three-axes comparison, and Yudkowsky's optimization-power measure were removed from the body -- they survive only as references -- and replaced with the convergent-attractor characterization plus the prediction/observer-independence argument. The order now is: define the optimizer behaviorally, quantify it as entropy reduction, motivate it via efficient prediction, then draw the objectivity conclusion. William James's "fixed aim / varying means" is absorbed but, per request, not cited.)*

### 3.1 Two notions of optimization and their relationship

- CS optimization (minimizing an objective, e.g. gradient descent to $\sqrt2$) vs engineering optimization (improving an artifact to fit a purpose); the question that links them: what property makes a physical process an optimization process?

### 3.2 Optimizers and convergent attractors

- **Two things kept apart (the central ontology):** the *system being optimized* (whose configuration we care about, could end up many ways) vs the *optimizer* (a separate physical thing whose presence drives that system to a narrow target). The optimizer is **not** the attractor and not the funnelling; it is the **cause** of the funnelling. Operational characterization: an optimizer is a physical thing such that, once you condition on its being there, your uncertainty about where the optimized system ends up is small
- Running example is a **courier delivering to a fixed address**: the *package* is the optimized system (its location could be anywhere), the *courier* is the optimizer; left to itself the package goes nowhere, the courier drives it to the address, *making the address a convergent attractor for the package* (the attractor is a feature of the package's behavior; the courier is what creates it). Genuinely hard to predict exactly, and steered by real agents (couriers, delivery robots, navigation systems)
- The two load-bearing features: a broad range of initial conditions (start anywhere in the city, all driven to the destination); robustness to perturbation (a coasting satellite has nothing steering it and optimizes nothing; the courier reroutes around a closed road and still arrives)
- One omission flagged: calling something an optimizer says nothing about goals/preferences/representations (courier, feedback circuit, chess engine, organism, optimization algorithm, house-builders are all optimizers in the same sense -- a structural fact about their *effect on the world*, not a mental attribute)

### 3.3 Optimization as entropy reduction

- $X$ = where the optimized system starts, $Y$ = where it ends; broad initial set = large $H(X)$; then **condition on the optimizer's presence** -- it drives the system to the narrow target whatever it started from, so $H(Y)$ is small; $\Delta H = H(X) - H(Y)$ is the entropy reduction the optimizer produces in that system; robustness is what lets $H(X)$ stay large while convergence still operates; large $\Delta H$ = reliably reaching a target the system's own unaided dynamics would essentially never hit (the opening slogan made precise)
- Remark 3.x: what the translation drops (the direction/goal); Wentworth's decomposition of EU maximization into entropy minimization + distribution-matching ("utility maximization = description length minimization"); physics constrains the first part only

### 3.4 The predictive value of optimizers (the efficient-prediction argument, made fully explicit)

- Setup: an agent who wants only to predict; claim: optimizers are, information-theoretically, the most economical things to know about
- Ordinary case (no optimizer): you must know $X$ in detail ($\approx H(X)$ bits, enormous) and integrate the dynamics; the forecast *degrades* over time as chaos amplifies any error in $X$
- Optimizer case, two changes both in your favour: (1) the initial condition is no longer needed (the optimizer drives every start to $T$, so uncertainty in $X$ does not propagate to $Y$); (2) **naming the target *is* the forecast** (intuitive framing): the laborious route is to pin down the exact start and follow the dynamics (hopeless and chaos-fragile for anything large); the optimizer lets you skip all that and just say "it ends at the target", a small and sturdy thing to know. Stated carefully (saving of effort, not a free lunch): saying "it ends at the target" *is* the forecast -- no extra knowledge conjured; the win is that knowing where a process is *headed* is cheap and stable, whereas reconstructing where it *started* (the only alternative route) is vast and fragile
- Courier illustration: track every vehicle, traffic light, and car and integrate forward (a hopeless, chaotic tangle) vs learn "the courier is delivering to 14 Elm Street" (a handful of bits, confident prediction, no traffic modelled)
- Robustness sharpens it: the forecast "ends in $T$" survives unforeseen perturbations, so you are spared the cost of modelling perturbations too; a pure predictor should scan for optimizers and track what they steer toward

### 3.5 The observer-independence of optimization

- The objection at its strongest (web-grounded): intelligence/optimization is observer-relative -- a system counts as intelligent only on tasks *we* care about. Formal backbone: the **No Free Lunch theorems** (no optimizer beats blind search averaged over all problems, so competence is always relative to a problem class reflecting the observer's interests). Philosophical sibling: **Dennett's intentional stance** (agency as a predictive stance an observer adopts, so "has goals" depends on the observer)
- The answer: we agree the significance of optimizers is grounded in predictive value (§3.4), but deny that value is observer-relative -- "is something here driving this system into a narrow target?" is a question about the system and the things acting on it, and the predictive leverage a known optimizer provides (a short, accurate description of where the system is headed) is the same for every predictor whatever its goals; the bare aim of prediction already singles out optimizers, so the reason to care is observer-*independent*
- Caveats kept precise: this does not contradict No Free Lunch (a different claim, about average competence across all problems); the optimizer's target is itself a property of the system, not imposed from outside; whose-standards-judge-success never enters
- Closing transition: optimizer = the *cause* of a convergent attractor (§3.2), measure = entropy it removes from the optimized system (§3.3), any predictor has an objective reason to track optimizers (§3.4-§3.5); optimization is *local* entropy reduction, and *global* entropy reduction is impossible -> Section 4
- References for §3.5 added to the bibliography: Wolpert-Macready (No Free Lunch, 1997) and Dennett (The Intentional Stance, 1987)

## Section 4: Reversibility and the second law

### 4.1 The reversibility of microscopic physics (phase space, bijective dynamics, Liouville's theorem in words, unitary QM)
### 4.2 The incompatibility of global funneling with reversibility (the central bookkeeping principle, displayed quote); §4.3 second-sentence pointer now reads "Section 5 and Appendix B"
### 4.3 Coarse-graining and the emergence of probability

- Cells, transition probabilities P(y,x) as volume fractions, randomness as shadow of unresolved detail
- Markov assumption discussed honestly; multibaker maps; the falling-vase arrow-of-time story (forward local statistics vs backward retrodiction)
- Liouville implies stationary volume measure; equal cells imply doubly stochastic P (derivation spelled out); footnote on the general unequal-volume ($\pi$-relative) formalism

### 4.4 The second law of thermodynamics

- Theorem 4.1 with two-step proof: data processing inequality for KL via log-sum, then counting-measure specialization
- Discussion: ingredient list is Markov + double stochasticity = reversibility; "second law follows from reversibility of physics"

### 4.5 The scope and limitations of the second law (subsystems may decrease; ensemble vs trajectory; fixed P vs observing agents -- the cost of which is now "the subject of Appendix B"; the exogenous mu foreshadowed). Closing transition leads into the three-types bookkeeping question; the coin-world toy model is pointed to as Appendix A.

## Section 5: Three types of optimization under information conservation

*(Immediately follows the second law. Sets up the bookkeeping question "when a subsystem's entropy falls, where does it go?", and links the third type to the Touchette-Lloyd theorem, now in Appendix B.)*

### 5.1 The bookkeeping problem (agent A, subsystem S, environment E; exhaustive classification)
### 5.2 Type 1: transfer of entropy into the environment as waste heat (refrigerator, builders; coin-world conditional swaps referenced to Appendix A; agent as broker)
### 5.3 Type 2: absorption of entropy into the agent's memory through measurement

- Maxwell's demon told in full; the two-histories reversibility argument for why the memory must fill
- Memory as exhaustible buffer; clearing memory ultimately exports the stored entropy to the environment as Type-1 waste (exact bookkeeping deferred to the demon section, §7.4)

### 5.4 Type 3: expenditure of pre-existing mutual information

- Full joint-entropy derivation: erasing the subsystem's copy of $I(S_t;A_t)$ leaves joint entropy exactly unchanged
- Example 5.x (controlled-NOT): one-bit worked instance with complete bookkeeping

### 5.5 A reinterpretation of Maxwell's demon, and a synthesis of the three channels (copy step = Type 2 purchase, control step = Type 3 expenditure). The forward link is now to Appendix B: how much steering per bit of mutual information is exactly the question the Touchette-Lloyd theorem answers, and the section ends by posing it and quoting the bound (one bit of reduction beyond the blind baseline per bit of mutual information).

## Section 6: Limitations of subjective entropy

### 6.1 Entropy as a measure of optimization capacity (demon's free memory; the question of objectivity)
### 6.2 The exogenous status of the reference distribution

- Codelength is a property of (state, distribution) pairs; mu as exogenous knowledge
- The three conditions for mu to be a useful summary: simplicity, concentration, typicality; equilibrium lives inside this regime

### 6.3 Three failure modes of the ensemble formalism

- Failure of simplicity: point mass on intricate state, knowledge booked at zero cost
- Failure of concentration: robot battery coin-flip, H(mu) describes no actual state
- Failure of typicality: patterned gas configuration, work underestimated, clever machine falsely branded a second-law violator

### 6.4 The demon's capacity as the central case for agent foundations (observer-relative capacity problem; classical macrovariables unsuited to memories; memory states are stable and meaningful, not thermalizing; agent-relevant states are exactly the failure cases)

## Section 7: Algorithmic thermodynamics

*(The section's emphasis is on dissolving the subjectivity problem: K(x) is an objective property of the individual state, the three failure modes of Section 6 are resolved, and the demon's objective-vs-subjective entropy wedge locates rather than banishes subjectivity.)*

### 7.1 Kolmogorov complexity

- Definition 7.1: K(x), K(x|y), algorithmic mutual information; footnote on self-delimiting programs (Kraft inequality) and chain-rule fine print
- Calibrating examples: million zeros, digits of pi, quantum-random bits, particles in a corner; "low entropy is compressibility"
- Algorithmic MI calibration; the additive-constant notations

### 7.2 Justification of $K$ as an entropy measure

- Machine-dependence physically negligible (12 GiB interpreter < 10^-12 J/K; 1 bit = k_B ln 2 ≈ 9.57e-24 J/K)
- Agreement with Shannon: $K(x|\mu) \le \log 1/\mu(x)$ for all x, near-tight for typical samples, Zurek's identity $H(\mu) = \langle K(X|\mu)\rangle$; Boltzmann macrostates as the uniform-set case; the bookshelf example; cheapest simple description wins
- The three failure modes of Section 6 resolved one by one
- Uncomputability as load-bearing: upper semicomputability; Chaitin's incompleteness in one line; the perpetual-motion argument against any computable entropy (find-certified-complex-state, then compute-copy-uncompute erasure)

### 7.3 The algorithmic second law

- Theorem 7.2 (informal Levin/Ebtekar-Hutter): w.p. > 1-δ, $K(X_s) - K(X_t) \le^+ K(t-s) + \log(1/\delta)$
- Per-trajectory, no initial distribution; both allowance terms explained with magnitudes (kilobit fluctuations ≈ 10^-20 J/K; Poincare recurrence priced by K(t-s); simply specified times)
- Corollary 7.3: deterministic simple dynamics cannot change K; entropy production requires randomness; random-bijection picture

### 7.4 An exact analysis of Maxwell's demon

- Full measurement then erasure: $(0,x) \to (x,x) \to (x,0)$ with all K's $=^+$ K(x); erasure permitted because a copy exists; last-copy clearing forbidden (not injective or not simply describable); to reset memory the demon must export K(x) bits to the environment as Type-1 waste (stated in informational terms, no heat/joules)
- Partial measurement: $(0,x) \to (m(x),x) \to (m(x),y)$; full chain-rule derivation of Equation (3), boxed: $K(x) - K(y) \le^+ I(m(x):x)$; attainable with equality when correlation fully and reversibly spent
- Term-by-term comparison with Theorem B.1 (Touchette-Lloyd, now Appendix B): ensemble vs single-shot versions; rigorous form of Type 3
- Objective entropy K(x) vs subjective entropy K(x|m(x)); optimization power as the wedge; subjectivity located, not banished -- the core dissolving-subjectivity payoff

## Section 8: Knowledge as a physical resource: optimization for embedded agents

### 8.1 From exogenous to endogenous knowledge

- The two frameworks side by side; no ledger exists; knowledge = $I(a:s) =^+ K(s) - K(s|a)$, an objective relation between pieces of matter; subjective beliefs implemented, not eliminated; K(s|a) as the environment's entropy as that agent finds it
- **"Knowing more is being able to do more," made precise** -- leads with the common intuition and formalizes it by composing two bridges, with the implication stated up front:
  - *Beliefs → mutual information* (Shannon coding): if memory $a$ encodes a computable belief $q$ (recovered by an $O(1)$ program), the Shannon codeword of the true $s$ under $q$ gives $K(s\mid a) \le^+ \log 1/q(s)$, hence $I(a:s) \ge^+ K(s) - \log 1/q(s)$ -- more probability on the truth = more mutual information
  - *Mutual information → optimization* (algorithmic Touchette-Lloyd, Appendix B): the agent can squeeze up to $I(a:s)$ bits out of the environment, attainably
  - *Composed:* achievable optimization $\ge^+ K(s) - \log 1/q(s)$, so "more probability on the truth ⇒ more optimization" -- the individual-state form of Touchette-Lloyd (Appendix B) and the rigorous Type-3 channel (Section 5)
- Bayesian learning read physically: updating raises $q(s)$ ⇒ codelength and residual $K(s\mid a)$ fall ⇒ $I(a:s)$ and reachable optimization rise; certainty limit $K(s\mid a) =^+ 0$, $I(a:s) =^+ K(s)$
- Two further properties: Type-3 consumptiveness; perishability (decay of stale correlation, from the algorithmic second law)
- The slogan: knowledge about the world = capacity to optimize the world beyond blind baselines, at a fixed (informational) exchange rate

### 8.2 Refinements of the three channels via universal computation

- Type 1: compress waste before thermalization; Type 2: memory bill is K(x) not raw transcript; Type 3: simple worlds cheap to know via computation alone
- The duality: K(s) = minimal Type-2 memory = minimal Type-3 knowledge

### 8.3 Dissolution of the apparent subjectivity

- Demon's capacity objective (free memory via description complexity of contents; compressible recoverable, incompressible irreducible)
- Whose physics the changing beliefs belong to: our update = physical change in our brains = acquired algorithmic MI, itself spendable; "every ledger is somebody's memory"

### 8.4 Thermodynamic implications for optimizing systems

*(Retitled from "Back to optimizing systems"; Flint's three-axes thermodynamic readings removed.) Key payoff: funneling beyond the blind baseline forces internal mutual information -- a necessary (not sufficient) ingredient of a world model, the thermodynamic seed of the selection-theorems program. Tied explicitly to the §3.5 observer-independence point: the presence of a world model, like the presence of an optimizer, is an objective fact certified by the entropy removed, not attributed by an observer.*

## Section 9: Summary and conclusions

- Summary prose (thesis-register paragraphs, formerly bullets) covering the full arc: optimizer as the *cause* of a convergent attractor (conditioning on it makes your uncertainty about where the system ends up small; calling it an optimizer needs no claim about its internals or goals); the observer-independence/efficient-prediction bullet (the target is a short, robust description of the outcome, so it forecasts for a tiny fraction of the bits the initial-condition route would need; answers the "intelligence is task-relative" worry); second law from reversibility; the three types; Touchette-Lloyd (now Appendix B); subjective-entropy failures; algorithmic thermodynamics results; endogenous knowledge. The coin-world lessons are carried in Appendix A.

## Appendix A: A thermodynamics of biased coins: the generalized heat engine

*(Referenced from elsewhere in the notes wherever a concrete blind-policy example helps -- the blind baseline of Appendix B and the Type-1 channel of Section 5. Opens with a short note on its role and that it can be read any time after Section 4.)*

### A.1 The designer's viewpoint (refrigerator designer; uncertainty moved not reduced; machines observing while running are inside the formalism; transfers to embedded AIs)
### A.2 Specification of the model: coins, transformations, and conservation laws

- Cold pool p=0.1 (0.47 bits/coin), hot pool p=0.2 (0.72 bits/coin); heads = energy
- Three rules: reversibility, heads conservation, no peeking
- Wentworth's conditional-swap example transformation analyzed (reads one part, acts on another, reversible, conservative)

### A.3 Work extraction as a compression problem (work coins; invertibility forces H(X')=H(X); certainty here requires uncertainty there)
### A.4 The impossibility of work extraction from a single heat bath

- The 0.72n bits / 0.36n heads vs 0.2n heads contradiction in full
- General maxentropic-subject-to-constraint argument; negentropy defined; type-2 perpetual motion impossible

### A.5 Work extraction from two heat baths at different temperatures

- Joint state not maxentropic; the explicit equation $(2n-w)\,h((0.3n-w)/(2n-w)) = 1.19n$; solution w ≈ 0.011n; Carnot caveat (marginal vs total conversion)

### A.6 Lessons from the toy world (four lessons in prose; everything was blind; the bridge question "what if it could look?" pointing to Appendix B)

## Appendix B: The informational cost of steering: the Touchette-Lloyd theorem

*(Moved here from the main body per author request, with all references updated from "Section" to "Appendix"; the one internal reference to the deleted ball-in-valley example was reworded to a self-contained description.)*

### B.1 From optimization to modeling: the motivating question (recalls the Type-3 channel of Section 5 and asks how many bits of steering each bit of mutual information buys; selection theorems; agent structure problem; footnote with full provenance: Touchette-Lloyd 2004 Theorem 10, 2000 paper, Lloyd 1989, good regulator + internal model principle comparison)
### B.2 The formal setup: environments, actions, and policies (X, A, Y; policy and dynamics)
### B.3 Blind and sighted policies

- Definition B.1; blind includes deterministic and privately randomized rules; the coin engine (Appendix A) = blind policies
- Naive conjecture refuted (a contracting dynamics, e.g. a ball settling in a valley, reduces entropy unaided); definition of blind baseline $\Delta H^{max}_{blind}$ over all initial distributions and blind action distributions

### B.4 A worked example: the guessing game under blind play

- The 5-bit game with f(x,a); why a=00000 is the wasted move (output exactly uniform)
- Full computation for a=11111: P(00000)=1/16, P(11111)=0, others 1/32, H(Y) = 4.94 bits
- Non-uniform initial distributions remark

### B.5 The guessing game under sighted play (k observed bits strategy; full table of H(Y) and ΔH for k=0..5)
### B.6 Mutual information as a measure of sightedness (inferring 2 bits of X from observing A=10111; H(X|A)=3; I=2; estimable from joint statistics)
### B.7 Statement of the theorem

- Theorem B.1 (Touchette-Lloyd): $\Delta H \le \Delta H^{max}_{blind} + I(X;A)$
- **No reversibility assumption:** the theorem is a purely information-theoretic (data-processing) inequality holding for arbitrary dynamics, reversible or not -- and why this is consistent with the rest (the second law needed reversibility to forbid global entropy reduction; Touchette-Lloyd needs none to bound steering beyond the blind baseline)
- Contrapositive selection-theorem reading; "anyone who beats 4.94 bits must have peeked"

### B.8 Limitations of the theorem

- Information can fail to help (action-independent dynamics) or be squandered (bitwise-NOT policy: 5 bits MI, zero reduction, worse than blind)
- Example B.3: noise-cancelling headphones (earplugs as blind policy exploiting fixed structure; active cancellation as sighted; music playing as entropy-increasing choice)
- Remark B.4: the coin engine (Appendix A) and the theorem as two halves of one picture; explicit identification of $I(X;A)$ with the Type-3 channel of Section 5

## Sources and further reading

- Flint (2020) and Yudkowsky (2008): now further-reading references only (the optimizing-system and optimization-power treatments are no longer expounded in the body); Wolpert-Macready (No Free Lunch, 1997) and Dennett (The Intentional Stance, 1987) added as the sources for the observer-relative view §3.5 states and answers; Wentworth (2020, + Utility Maximization = Description Length Minimization 2021); Harwood & Altair (2025, now grounding Appendix B) + Touchette & Lloyd (2004, 2000) + Lloyd (1989); Daniel C & Ebtekar (2025, the central organizing source, now also grounding §3); Ebtekar & Hutter (Phys. Rev. E 2025, arXiv:2308.06927)
- Pointer to the Agent Foundations slide deck for the broader module context
