# Consequentialist Foundations (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/consequentialist-foundations/main.tex`. Compiled PDF: `targets/consequentialist-foundations.pdf`.

**Title:** Consequentialist Foundations
**Subtitle:** Why capable agents look like expected utility maximizers, from money pumps to the complete class theorem

**Abstract:** Coherence as a foothold for reasoning about minds we have not built. Three movements: (1) the intuitive coherence argument (circular preferences make you a money pump; refusing to be pumped is consistency; extending to gambles forces probabilities and expected utility to emerge jointly); (2) the measuring-stick problem (dominated strategies are only detectable relative to a resource that plays the role of money, and identifying that resource from physics is open); (3) the rigorous complete class theorem (any admissible decision rule is Bayes-optimal for some prior, derived from pure dominance reasoning, probabilities and utilities falling out together). Closes on the representational (not mechanistic) reading and the assumptions whose failure motivates logical induction and descriptive foundations.

## Section 1: Introduction: reasoning about minds we have not built

- The prediction problem: say something reliable about a more capable system before it exists
- Robust concepts / "true names"; coherence theorems as the sturdiest example
- Slogan "coherent decisions imply consistent utilities"; the load-bearing word "behave" (representational, not a claim about internals)
- Plan and prerequisites (elementary probability)

## Section 2: Dominated strategies and circular preferences

- Pizza agent with circular preferences (onion > pineapple > mushroom > onion); the penny-per-cycle money pump; Omohundro's SF/Berkeley/San Jose taxi version
- Definition 2.1 (dominated strategy): another available strategy does strictly better, never worse
- Two emphases: coherence does not say *what* to prefer, only that preferences must be consistent; the inference runs from "avoids money pumps" to "representable by a utility function" (transitivity/acyclicity = real-valued $U$)

## Section 3: From preferences to probabilities and expected utility

### 3.1 Why there must be quantitative weights
- Refusing to start with probability or utility (Yudkowsky's inversion of the textbook order)
- Apple/orange/plum coin gamble; expected utility $0.5\,U(\text{orange}) + 0.5\,U(\text{plums}) = \texteuro 1.75$; non-EU valuations are dominable

### 3.2 Why the weights obey the laws of probability
- Sum to one: weights 0.6/0.7 on heads/tails exploited by a contract paying 0.8 apples either way
- Dutch book: mutually exclusive exhaustive prices must sum to \$1 (one more staging of the same dominance argument)
- Conditional probability forced: three tickets give $z = x\cdot y$, i.e. $P(Q\wedge R)=P(Q)P(R\mid Q)$; the $x{=}0.6,y{=}0.7,z{=}0.2$ sure-loss

### 3.3 What the coherence picture establishes, and admits
- All arguments point at the same core: behave as if probabilities + utility function + EU maximization, derived together
- Caveats (Yudkowsky's own): these are intuition pumps not professional-grade theorems (the real one is the complete class theorem); perfect coherence is uncomputable; messy internals can still look coherent

## Section 4: The measuring stick of utility

- Every dominance argument was denominated in a resource (pennies, apples, dollars)
- The triviality objection ("every system is a utility maximizer") and how a fixed resource dissolves it (pepperoni->mushroom->anchovy cycle)
- Two properties of a measuring stick: additivity across decisions; more is desirable (plus fungibility); energy/negentropy/free energy as candidates (link to thermodynamics)
- The hard open problem: recognizing a resource "in the wild" from physics alone; "what program identifies the resources in a simulated world?"; would give an objective sense of which physical systems contain embedded agents; Wentworth's resources-measure-utility argument is qualitative, not yet a theorem

## Section 5: The complete class theorem

- Motivation: a consequentialist foundation that compares consequences directly, not via hypothetical betting/payment (Demski vs Dutch-book/money-pump)

### 5.1 Setup
- Definition 5.1 (decision problem): states $\Theta$, observations $X$, actions $A$, likelihood $F(x\mid\theta)$, loss $L(\theta,a)$, decision rule $\delta:X\to A$; loss carries the measuring stick; finite $\Theta,A$
- Definition 5.2 (risk): $R(\theta,\delta)=\mathbb{E}_{x\sim F(\cdot\mid\theta)}[L(\theta,\delta(x))]$; risk profile a point in $\mathbb{R}^{|\Theta|}$

### 5.2 Dominance, admissibility, and the Bayesian rules
- Definition 5.3 (Pareto improvement; admissibility): no rule beats it everywhere weakly and somewhere strictly
- Definition 5.4 (Bayes risk; Bayes-optimality; non-dogmatic prior $\pi(\theta)>0$)

### 5.3 The theorem
- Theorem 5.5 (Bayes rules are admissible) with proof (non-dogmatism lets a single-world strict improvement survive averaging)
- Theorem 5.6 (Complete class theorem): admissible iff Bayes-optimal for some prior; separating-hyperplane proof (convex closed risk set, separate the dominating quadrant, nonnegative normal = prior)
- Two-state picture: admissible rules = lower-left frontier of the convex hull; sweeping the prior sweeps the contact point along it; "the Bayesian rules *are* the frontier"

### 5.4 What was assumed, and what was derived
- In: finite $\Theta,A$, per-state preference (loss), admissibility. Out: prior $\pi$ and EU maximization, jointly, with no probabilities assumed
- Removable assumptions: likelihood absorbed into states; mixed strategies via coins-in-worlds; VNM independence becomes a theorem; continuity relaxable (surreal utilities). Finiteness does the real work

### 5.5 A bonus: the same theorem is an argument for utilitarianism
- Reinterpret $\theta$ as people: admissibility = Pareto efficiency, prior = social weights, result = weighted sum of cardinal utilities (Harsanyi); jessicata's post-hoc-rationalization caveat

## Section 6: What the theorems do and do not say

- Representational, not mechanistic: "behaves as if" / from outside; says nothing about internals; source of robustness; tells us what more-capable systems converge toward
- Rests on a measuring stick we cannot yet locate from physics; solving it upgrades the theorems from description to a test on raw physics (handoff to descriptive agent foundations)
- Idealization real agents violate (uncomputable coherence -> logical induction; static/complete/path-independent preferences -> better selection theorems); coherence theorems as the sturdiest first foothold

## Sources

- Yudkowsky, *Coherent decisions imply consistent utilities* (Intro; Why not circular preferences?; Probabilities and expected utilities through Conditional probability; Conclusion)
- Wentworth, *The measuring stick of utility problem*
- Demski, *Complete Class: Consequentialist Foundations*
- Background: *Embedded Agency*; Dutch book and admissibility/complete-class references
