# Decision Theory

Title: **Decision Theory**
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/dt-presentation/main.tex` (28 slides). Add `<div>...</div>`
edit markers after any line to request a change.

---

## Title page

## Roadmap

- **Block: From classical choice to embedded counterfactuals**
  - Why decision theory matters for AI safety (modelling, specification, reflective stability, multi-agent conflict)
  - Why it is hard: optimisation is solved for *dualistic* agents but not for *embedded* ones
  - The candidates: CDT, EDT, FDT, UDT 1.0/1.1
  - A unifying lens: CDT vs EDT as two readings of an action in sequential (AIXI-style) prediction — intervention (chronological semimeasure) vs evidence (joint prediction)
  - The hard core: problems with UDT, the 5-and-10 problem, logical counterfactuals, Löb's theorem
  - A unifying goal: formalise decision problems as programs and ask which theory is *optimal*

# Section: Why decision theory?

## Why study decision theory? (for AI safety)

- **Block: Four reasons** — architecture-independent modelling; specification--optimisation split; reflective stability; multi-agent dynamics

# Section: Why is decision theory hard?

## The easy case: dualistic agents

- **Block: When the agent is cleanly separated from the world** — clean I/O, "larger than"/"outside"; action a free variable; `a* = argmax_a E[U | do(A=a)]`; vNM/Savage, complete-class theorems; economics/stats/RL

## The hard case: embedded agents

- **Block: When the agent is a part of the world it reasons about** — agent is a piece of the world (copied/predicted/read); "which action I take" is just another fact; the central difficulty is constructing counterfactuals; EDT (condition) / CDT (intervene) / FDT-UDT (logical output)

# Section: Causal decision theory

## A 60-second primer: Bayesian networks

- **Block: Encoding "what depends on what"** (own TikZ diagram: cloudy -> sprinkler, cloudy -> rain, sprinkler/rain -> wet grass)
  - DAG; factorisation `P = prod P(X_i | Pa(X_i))`; independence of non-descendants given parents
  - Concrete factorisation for the graph: `P(C) P(S|C) P(R|C) P(W|S,R)`

## Causal decision theory: seeing vs. doing

- **Block: The do-operator** (own TikZ diagram: do(S=on) severs the C -> S arrow)
  - observe vs do; `do(X=x)` severs arrows into X; adjustment over parents `P(Y|do(x)) = sum_z P(Y|x,z)P(z)`
  - sprinkler seeing-vs-doing; CDT: `a* = argmax_a E[U | do(A=a)]`

## CDT on Newcomb's problem

- **Block: Two-boxing, and why** (+ causal-graph diagram: disposition S -> A, P; CDT cuts S->A)
  - Newcomb; do(A) severs action from disposition; two-boxing dominates; predictably worse; discards prediction's dependence

## CDT vs. physics: the intervention is a fiction

- **Block: Does CDT really "reflect physical reality"? (following Ebtekar & Hutter)** — magic severing vs deterministic/time-reversible physics; predictor reads antecedents via ordinary physics; severing contradicts embeddedness; move the counterfactual onto the policy/computation

# Section: Evidential decision theory

## Evidential decision theory: condition, don't intervene

- **Block: EDT as conditioning** — `a* = argmax_a E[U | A=a]`; one-boxes Newcomb; `E[U|do(A=a)]` vs `E[U|A=a]`

## EDT mistakes evidence for control

- **Block: The smoking lesion** — conditioning on smoking raises P(lesion); EDT abstains (symptom vs lever); scorecard CDT/EDT each half-right

## Spurious counterfactuals: EDT breaks for self-aware agents

- **Block: Conditioning on a probability-zero action** — self-predicting agent gives P(A=a)=0; `E[U|A=a]` is 0/0; spurious counterfactual; foreshadows 5-and-10 / logical dependence

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
  - action appears only to the right of `||`; rho assigns no probability to actions
  - posterior updates on percepts only: `w_nu(h_{<t}) = w_nu nu(e_{<t}||a_{<t}) / xi(e_{<t}||a_{<t})`; choosing a_t does not reweight w_nu
  - value by intervening through a fixed which-world belief: `a_t = argmax_a sum_{e_t} xi(e_t || h_{<t} a) [r_t + ...] = argmax_a E_xi[U || do(a)]`
  - exactly CDT: the chronological bar `||` is the do-operator on histories; Newcomb -> two-box

## Joint prediction = EDT

- **Block: Actions predicted exactly like observations**
  - model the whole history as one stream over (A x E)*; generative model = mixture over (world nu, policy pi): `P(h_{1:t}) = sum_{nu,pi} w_{nu,pi} prod_k pi(a_k|h_{<k}) nu(e_k|h_{<k}a_k)`; Solomonoff M is the universal joint predictor
  - conditioning on a_t updates the joint posterior over both policy and world: `w_{nu,pi}(h_{<t}a_t) ∝ w_{nu,pi} [...] pi(a_t|h_{<t})`; pi-factor = "what policy am I", nu correlated-in-prior = "what world am I in"
  - value by conditioning: `a_t = argmax_a E_P[U | A_t=a, h_{<t}]`
  - exactly EDT; reproduces the smoking lesion (prior correlates lesion with smoking disposition)

# Section: Functional & updateless decision theory

## Functional decision theory: intervene on the function

- **Block: The three rules side by side (Yudkowsky & Soares 2017)**
  - `EDT(P,x) = argmax_a E[V | Obs=x, Act=a]`
  - `CDT(P,G,x) = argmax_a E[V | do(Act=a), Obs=x]`
  - `FDT(P,G,x) = argmax_a E[V | do(fdt(P,G,x)=a)]` (boxed)
  - only change from CDT is which node you intervene on: physical act (Peirce's token) vs the logical function node (the type)
  - Newcomb one-boxes, smoking lesion smokes; caveat: counterpossibles (counter-to-logic antecedents) still open

## Twin Prisoner's Dilemma & subjunctive dependence

- **Block: Same function, two bodies** (+ diagram: logical fact -> my action, twin's action)
  - Twin PD; CDT both defect ($1), FDT both cooperate ($3)
  - Subjunctive dependence (Y&S): two systems computing the same function are logically tied (two calculators evaluating 6288+1048); causal dependence a special case; mere correlation (both pink) is not

## Counterfactual mugging: the updateless move

- **Block: Paying in a branch you know you're not rewarded in** (+ tree diagram: coin -> tails reward / heads cost, one policy spans both)
  - Setup; updateful refuses; ex-ante policy worth (R-c)/2 > 0
  - UDT 1.0 formula: `choice(o) = argmax_a E[U | choice(o)=a]` (drop the updateful O=o conditioning) -> pays
  - updatelessness not ignorance; reflectively stable

## UDT 1.1: optimise the whole policy, not one action

- **Block: When local outputs must be coordinated** (+ diagram: one global policy -> obs 1 / obs 2, coordinated)
  - Copied-agent anti-coordination; "if Alg(1)=A then Alg(2)?" wrong type
  - UDT 1.1 formula: `S* in argmax_{S:O->A} E[U | choice=S]`, then apply S*(o); UDT 1.0 instead fixes a single output
  - global optimisation over branches

## The three shifts in "what am I choosing?"

- **Block: CDT/EDT -> FDT -> UDT 1.0 -> UDT 1.1 (after Kosoy's formalism)** — table (rule / object / update status / dependence) + the three shifts

# Section: Problems with UDT

## Problem 1: paying for worlds that don't exist

- **Block: Ex-ante optimality is only as good as the prior** — UDT burns real utility in the actual branch; dangerous with a mistaken prior; "best from the prior" when the prior includes non-actual worlds

## Problem 2: logical updatelessness

- **Block: Which prior, when some of your uncertainty is mathematical?** — empirical vs logical uncertainty; "don't update" unclear logically; no coherent logical prior; open

# Section: The 5-and-10 problem

## The 5-and-10 problem

- **Block: The simplest decision, made hard by self-knowledge (Demski & Garrabrant)**
  - $5 vs $10; embedded framing (deterministic world pays the number; agent chooses by proof search)
  - deep issue: knowing your own behaviour makes it hard to reason about behaving differently; the other action is ruled out by logic (impossible antecedent)
  - the trap: once it can prove it takes $5, "(A=$10)=>U=$0" is vacuously true; self-fulfilling spurious counterfactual
  - fault is too much self-knowledge, not bad logic

## Spurious proofs and Löb's theorem

- **Block: Why a naive proof-searcher is genuinely unsafe**
  - Löb (formula + intuition): `if |- (Box P -> P) then |- P`; equivalently `|- Box(Box P -> P) -> Box P`; can't prove own consistency (Gödel II)
  - the spurious proof: S = "(A=$10)=>U=$0"; agent built so proving S -> takes $5; then Box S -> S, so by Löb |- S
  - moral: needs extra structure (playing chicken with the universe); counterpossibles open; same obstacle blocks successor-trust (reflective stability)

# Section: A formal criterion for decision theories

## Why we want a formal optimality criterion

- **Block: Beyond case-by-case scoring** — shared program structure; case-by-case judging; one class + one optimality criterion

## Agents and worlds as programs

- **Block: The setup** (+ diagram: Agent <-> World) — agent (own + world source -> action); world (calls agent on many inputs, proves about it -> utility); high utility across all worlds

## Fairness

- **Block: Judging the agent only on its behaviour** — no source-code punishment; world depends only on input/output behaviour; Newcomb/lesion/mugging/twin PD/open-source PD all fair

## What a good agent must discover

- **Block: Two demands -- which are exactly FDT/UDT turned into a spec** — coordinate across calls (UDT 1.1); subjunctive dependence / detect isomorphic subroutine (FDT)
- **Block: The open problem (and the bridge ahead)** — define class/optimality, show theories differ; caveats -> Deck II
