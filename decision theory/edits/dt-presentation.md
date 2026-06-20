# Decision Theory

Title: **Decision Theory**
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/dt-presentation/main.tex` (27 slides). Add `<div>...</div>`
edit markers after any line to request a change.

---

## Title page

## Roadmap

- **Block: From classical choice to embedded counterfactuals**
  - Why decision theory matters for AI safety
  - Why it is hard: dualistic vs embedded
  - The candidates: CDT, EDT, FDT, UDT 1.0/1.1
  - A unifying lens: CDT vs EDT as intervention (chronological semimeasure) vs evidence (joint prediction)
  - The hard core: problems with UDT, the 5-and-10 problem, logical counterfactuals, Löb's theorem
  - A unifying goal: formalise decision problems as programs and ask which theory is optimal

# Section: Why decision theory?

## Why study decision theory? (for AI safety)

- **Block: Four reasons** — architecture-independent modelling; specification--optimisation split; reflective stability; multi-agent dynamics

# Section: Why is decision theory hard?

## The easy case: dualistic agents

- **Block: When the agent is cleanly separated from the world** — clean I/O, "larger than"/"outside"; action a free variable; `a* = argmax_a E[U | do(A=a)]`; vNM/Savage, complete-class theorems

## The hard case: embedded agents

- **Block: When the agent is a part of the world it reasons about** — action is just another fact; construct counterfactuals; EDT (condition) / CDT (intervene) / FDT-UDT (logical output)

# Section: Defining EDT and CDT

## Evidential decision theory: condition, don't intervene

- **Block: EDT as conditioning** — `a* = argmax_a E[U|A=a]`; conditioning treats the action as evidence about everything correlated with it; forward pointer (helps on Newcomb, misleads on the smoking lesion)

## A 60-second primer: Bayesian networks

- **Block: Encoding "what depends on what"** (own TikZ diagram: cloudy -> sprinkler, cloudy -> rain, sprinkler/rain -> wet grass) — DAG factorisation; concrete `P(C)P(S|C)P(R|C)P(W|S,R)`

## Causal decision theory: seeing vs. doing

- **Block: The do-operator** (own TikZ diagram: do(S=on) severs C -> S) — observe vs do (do = intervention, contrast with EDT's conditioning); `do(X=x)` severs arrows into X; adjustment over parents; sprinkler seeing-vs-doing; CDT `a* = argmax_a E[U|do(A=a)]`; one-line contrast `E[U|do(A=a)]` vs `E[U|A=a]`

# Section: CDT and EDT as sequential prediction

## Prerequisites: the sequential prediction setting

- **Block: Histories, environments as chronological semimeasures, and beliefs**
  - interaction: actions a_t in A, percepts e_t=(o_t,r_t); history h_{<t}
  - environment = chronological semimeasure `rho(e_{1:t} || a_{1:t})`; `||` marks actions as conditioned-on inputs, never predicted
  - chronological (no dependence on future actions); semimeasure `sum_{e_t} rho(e_{1:t}||a_{1:t}) <= rho(e_{<t}||a_{<t})`
  - Bayesian mixture `xi = sum_nu w_nu nu` (AIXI: lower-semicomputable nu, w_nu=2^{-K(nu)})
  - crux: does choosing a_t update the belief about which environment you're in? (separates CDT from EDT)

## Chronological semimeasure = CDT

- **Block: The action is an intervention, not evidence**
  - action only to the right of `||`; rho assigns no probability to actions
  - posterior updates on percepts only: `w_nu(h_{<t}) = w_nu nu(e_{<t}||a_{<t}) / xi(e_{<t}||a_{<t})`; choosing a_t does not reweight w_nu
  - value by intervening through a fixed which-world belief: `a_t = argmax_a sum_{e_t} xi(e_t || h_{<t} a)[...] = argmax_a E_xi[U || do(a)]`
  - exactly CDT: the chronological bar `||` is the do-operator on histories; Newcomb -> two-box

## Joint prediction = EDT

- **Block: Actions predicted exactly like observations**
  - model the whole history as one stream over (A x E)*; generative model = mixture over (world nu, policy pi): `P(h_{1:t}) = sum_{nu,pi} w_{nu,pi} prod_k pi(a_k|h_{<k}) nu(e_k|h_{<k}a_k)`; Solomonoff M is the universal joint predictor
  - conditioning on a_t updates the joint posterior over both policy and world: `w_{nu,pi}(h_{<t}a_t) ∝ w_{nu,pi} [...] pi(a_t|h_{<t})`; pi-factor = "what policy am I", nu correlated-in-prior = "what world am I in"
  - value by conditioning: `a_t = argmax_a E_P[U | A_t=a, h_{<t}]`
  - exactly EDT; reproduces the smoking lesion (prior correlates lesion with smoking disposition)

# Section: Where CDT and EDT fail

## Newcomb's problem: CDT two-boxes, EDT one-boxes

- **Block: The same problem splits the two rules** (+ causal-graph diagram: disposition S -> A, P; CDT cuts S->A)
  - Newcomb setup; CDT severs action from disposition -> two-boxes, gets $1,000; EDT one-boxing is evidence the box is full -> one-boxes, gets $1,000,000
  - verdict: CDT loses Newcomb (chronological-semimeasure agent two-boxes; joint-prediction agent one-boxes)

## EDT mistakes evidence for control

- **Block: The smoking lesion** — conditioning on smoking raises P(lesion); EDT abstains (symptom vs lever); scorecard CDT loses Newcomb / EDT loses smoking lesion; missing a third kind of dependence

## CDT vs. physics: the intervention is a fiction

- **Block: Does CDT really "reflect physical reality"? (following Ebtekar & Hutter)** — magic severing vs deterministic/time-reversible physics; predictor reads antecedents via ordinary physics; severing contradicts embeddedness; move the counterfactual onto the policy/computation

## Spurious counterfactuals: EDT breaks for self-aware agents

- **Block: Conditioning on a probability-zero action** — self-predicting agent gives P(A=a)=0; `E[U|A=a]` is 0/0; spurious counterfactual; foreshadows 5-and-10 / logical dependence

# Section: Functional & updateless decision theory

## Functional decision theory: choose your function's output

- **Block: "Which output of this very function would yield the best outcome?"** (intuition-first, after the FDT paper; improves on the sources FDT slides)
  - reframe what you are choosing: you run a fixed decision function; your action is its output
  - predictors who modelled it, copies running it, simulations of it all move together with its output
  - FDT asks "which output of this very decision function -- given everything that depends on it -- yields the best outcome?" and returns it; score each action a by the world where the function outputs a
  - acts as if it controls all instances of the computation at once (same logical fact)
  - Newcomb one-boxes, smoking lesion smokes; shines where embedded agents live (copies/predictors)

## Twin Prisoner's Dilemma & subjunctive dependence

- **Block: Same function, two bodies** (+ diagram: logical fact -> my action, twin's action) — Twin PD; CDT both defect ($1), FDT both cooperate ($3); subjunctive dependence (two calculators); causal dependence a special case; mere correlation is not

## Counterfactual mugging: the updateless move

- **Block: Paying in a branch you know you're not rewarded in** (+ tree diagram) — setup; updateful refuses; ex-ante worth (R-c)/2; UDT 1.0 `choice(o) = argmax_a E[U | choice(o)=a]` -> pays; updatelessness not ignorance; reflectively stable

## UDT 1.1: optimise the whole policy, not one action

- **Block: When local outputs must be coordinated** (+ diagram) — copied-agent anti-coordination; UDT 1.1 `S* in argmax_{S:O->A} E[U | choice=S]` then apply S*(o); global optimisation over branches

## The three shifts in "what am I choosing?"

- **Block: CDT/EDT -> FDT -> UDT 1.0 -> UDT 1.1 (after Kosoy's formalism)** — table (rule / object / update status / dependence) + the three shifts

# Section: Problems with UDT

## Problem 1: paying for worlds that don't exist

- **Block: Ex-ante optimality is only as good as the prior** — UDT burns real utility in the actual branch; dangerous with a mistaken prior

## Problem 2: logical updatelessness

- **Block: Which prior, when some of your uncertainty is mathematical?** — empirical vs logical uncertainty; no coherent logical prior; open

# Section: The 5-and-10 problem

## The 5-and-10 problem

- **Block: Two programs (Demski & Garrabrant)** — source code of the world `U()` (returns whatever the agent returns: 10 for 10, 5 for 5) and the agent `A()` (proof-searches for `[A()=5 -> U()=x]` and `[A()=10 -> U()=y]`, x,y in {0,5,10}; returns 5 if found with x>y, else 10)
- **Block: Why it returns $5** — let P = "[A()=5 => U()=5] and [A()=10 => U()=0]"; a proof of P makes P true (A returns 5, so A()=10 is false and the second conjunct holds vacuously); so Box P -> P is provable, Löb gives P provable, the search finds it and returns $5; spurious proof — counterfactuals over one's own action break down

# Section: A formal criterion for decision theories

## Why we want a formal optimality criterion

- **Block: Beyond case-by-case scoring** — shared program structure; one class + one optimality criterion

## Agents and worlds as programs

- **Block: The setup** (+ diagram) — agent (own + world source -> action); world (calls agent, proves about it -> utility)

## Fairness

- **Block: Judging the agent only on its behaviour** — world depends only on input/output behaviour; Newcomb/lesion/mugging/twin PD/open-source PD all fair

## What a good agent must discover

- **Block: Two demands -- which are exactly FDT/UDT turned into a spec** — coordinate across calls (UDT 1.1); subjunctive dependence / detect isomorphic subroutine (FDT)
- **Block: The open problem (and the bridge ahead)** — define class/optimality; caveats -> Deck II
