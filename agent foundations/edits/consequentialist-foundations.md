# Consequentialist Foundations (lecture notes)

Article-class lecture notes, fully self-contained for a reader with zero background in decision theory or agent foundations: every term (preference, utility function, probability, expected utility, Dutch book, dominated strategy, Pareto, prior, convex/separating hyperplane) is built from a concrete example before being named. Project: `projects/consequentialist-foundations/main.tex`. Compiled PDF: `targets/consequentialist-foundations.pdf`.

**Title:** Consequentialist Foundations
**Subtitle:** Why anything that pursues goals well comes to look like an expected utility maximizer

**Abstract:** Coherence theorems as forced, general facts about effective goal-pursuit, for a reader not already on board with agent foundations. Three movements: (1) the intuitive version (circular preferences make you a money pump; avoiding the drain is a consistency requirement; gambles force probabilities and expected utility to emerge jointly); (2) the hidden assumption (being "drained" only makes sense relative to a resource playing the role of money, and identifying that resource from physics is open); (3) the rigorous version, the complete class theorem (any undominated rule is Bayes-optimal for some prior, from pure dominance reasoning, probabilities and utilities falling out together). Closes on the representational (not mechanistic) reading and the idealizations whose failure motivates logical induction and descriptive foundations.

## Section 1: The problem: saying something about a mind before it exists

- Building a capable goal-pursuer we cannot experiment on; we want properties forced by effective goal-pursuit, whatever the internals
- Modest in one direction (won't say *what* it wants), surprising in another (the structure is specific: utility function + probability distribution + expected-utility maximization)
- The load-bearing word "behaves" = summarized from outside (the thrown-rock/least-action analogy); strength and limit of that
- Plan and prerequisites (simple arithmetic only)

## Section 2: Circular wanting, and how it drains you

- Pizza system with circular preferences (onion > pineapple > mushroom > onion); the penny-per-cycle money pump; Omohundro's Bay-area-taxi version
- Definition 2.1 (dominated; dominated strategy): another available course does at least as well everywhere and strictly better somewhere
- Two emphases: coherence does not say *what* to want, only that wants must be loop-free; the inference runs from "not drainable" to "encodable by an assigned-number ranking"
- Definition 2.5 (utility function): real number per outcome, higher = more preferred; capturable iff loop-free

## Section 3: Choosing under uncertainty, and where probabilities come from

- Gambles; the textbook order inverted (refuse to start with probabilities or utilities; extract both from the no-draining demand)

### 3.1 Why there must be numerical weights at all
- Apple/orange/plum coin gamble; expected utility (defined plainly) $0.5\,U(\text{orange}) + 0.5\,U(\text{plums}) = \text{€}1.75$; non-blend scorings are drainable

### 3.2 Why the weights have to behave like probabilities
- Sum to one: weights 0.6/0.7 exploited by a contract paying 0.8 apples either way
- Dutch book (defined from scratch): mutually exclusive exhaustive ticket prices must sum to \$1
- Conditional probability forced: three tickets give $z = x\cdot y$, i.e. $P(Q\wedge R)=P(Q)P(R\mid Q)$; the $x{=}0.6,y{=}0.7,z{=}0.2$ sure-loss

### 3.3 What the intuitive picture shows, and what it admits
- All arguments converge: behave as if utility function + probability distribution + EU maximization, derived together; "Bayesian" defined
- Caveats: intuition pumps not professional-grade theorems (the rigorous one is the complete class theorem); perfect coherence uncomputable; messy internals can still look coherent

## Section 4: The hidden ruler: what counts as a resource?

- Every drain was booked in a currency (pennies, apples, dollars)
- The "every system is a utility maximizer" triviality and how a fixed resource dissolves it (pepperoni->mushroom->anchovy cycle)
- Two properties of a measuring stick: adds across decisions; more is better (plus fungibility); energy/free energy as candidates (thermodynamics link)
- The open problem: identify resources "in the wild" from physics alone; would give a non-circular sense of which physical systems contain agents; Wentworth's resources-measure-utility argument is qualitative, not a theorem

## Section 5: The rigorous version: the complete class theorem

- Motivation: compare consequences directly, no bookies/money pumps (Demski)

### 5.1 The pieces of a decision problem
- Definition 5.1 (decision problem): states $\Theta$, observations $X$, actions $A$, likelihood $F(x\mid\theta)$, loss $L(\theta,a)$ (lower=better, a flipped utility), decision rule $\delta:X\to A$; loss carries the measuring stick; finite $\Theta,A$
- Definition 5.2 (risk): $R(\theta,\delta)=\sum_x F(x\mid\theta)L(\theta,\delta(x))$; risk profile a point with one axis per state

### 5.2 Not being dominated, made precise
- Definition 5.3 (Pareto improvement; admissibility): at least as low risk everywhere, strictly lower somewhere
- Definition 5.4 (Bayes risk; Bayes-optimality; non-dogmatic prior): prior = weights summing to one; Bayes-optimal = an EU maximizer in disguise

### 5.3 The theorem
- Theorem 5.5 (Bayes-optimal => admissible) with full proof (positivity lets a one-state strict gain survive averaging)
- Theorem 5.6 (complete class): admissible iff Bayes-optimal for some prior; separating-hyperplane proof, with convexity and the separating-hyperplane theorem explained from scratch (achievable risk set convex+closed; separate the dominating corner; nonnegative normal, rescaled = prior)
- Two-state picture: admissible rules = lower-left frontier; sweeping the prior sweeps the tangent contact point; the EU maximizers *are* the frontier

### 5.4 What went in, and what came out
- In: finite $\Theta,A$, per-state loss, admissibility. Out: prior + EU maximization, jointly, no beliefs assumed
- Removable assumptions: likelihood absorbed into states; randomization via coins-in-worlds; VNM independence becomes a consequence. Finiteness does the real work

### 5.5 A bonus: the same theorem argues for a kind of utilitarianism
- Reinterpret $\theta$ as people: admissibility = social efficiency, prior = weights, result = weighted sum of welfare (Harsanyi); jessicata's "describable-as vs mechanically-does" caveat

## Section 6: What these theorems do and do not say

- Representational, not mechanistic: "behaves as if" from outside; says nothing about internals; source of robustness; the target more-capable systems drift toward
- Lean on a ruler we cannot yet find from physics; solving it upgrades the theorems from description to a test on raw physics (handoff to descriptive foundations)
- Idealizations real systems break (uncomputable coherence -> logical induction; complete/fixed/path-independent preferences -> better selection theorems); the sturdiest first foothold

## Sources

- Yudkowsky, *Coherent decisions imply consistent utilities* (Intro; Why not circular preferences?; Probabilities and expected utilities through Conditional probability; Conclusion)
- Wentworth, *The measuring stick of utility problem*
- Demski, *Complete Class: Consequentialist Foundations*
