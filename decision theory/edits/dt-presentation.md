# Decision Theory

Title: **Decision Theory**
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/dt-presentation/main.tex` (26 slides). Add `<div>...</div>`
edit markers after any line to request a change.

---

## Title page

## Roadmap

- **Block: From classical choice to embedded counterfactuals**
  - Why decision theory matters for AI safety (modelling, specification, reflective stability, multi-agent conflict)
  - Why it is hard: optimisation is solved for *dualistic* agents but not for *embedded* ones, where the agent must *construct* counterfactuals
  - The candidates: CDT, EDT, FDT, UDT 1.0/1.1 -- each a different recipe for the counterfactual
  - The hard core: problems with UDT, the 5-and-10 problem, logical counterfactuals, Löb's theorem
  - A unifying goal: formalise decision problems as programs and ask which theory is *optimal* across all "fair" problems

# Section: Why decision theory?

## Why study decision theory? (for AI safety)

- **Block: Four reasons**
  - Architecture-independent modelling: reason about behaviour without knowing the build
  - Implementation / specification--optimisation split: decision theory is part (2); a perfect spec is not sufficient if counterfactuals are constructed wrongly
  - Reflective stability: would an agent with theory A self-modify into theory B? (link to Agent Foundations deck)
  - Multi-agent dynamics: cooperate with other superintelligences and avoid conflict, without being exploitable

# Section: Why is decision theory hard?

## The easy case: dualistic agents

- **Block: When the agent is cleanly separated from the world**
  - Clean input/output channels; agent "larger than" and "outside" the world
  - Action is a free variable; optimisation solved: `a* = argmax_a E[U | do(A=a)]`
  - Mature framework: vNM/Savage axioms, Bayesian updating, complete-class theorems
  - Underpins economics, statistics, RL

## The hard case: embedded agents

- **Block: When the agent is a part of the world it reasons about**
  - Agent is a piece of the world; can be copied, predicted, simulated, read
  - "Which action I take" is just another fact; no ready-made "what if I acted differently"
  - The central difficulty: constructing counterfactuals
  - EDT (condition), CDT (intervene), FDT/UDT (logical output of the decision procedure)

# Section: Causal decision theory

## A 60-second primer: Bayesian networks

- **Block: Encoding "what depends on what"**
  - DAG; joint factorises as product of `P(X_i | Pa(X_i))`
  - Each variable independent of non-descendants given its parents
  - [image: bayesnet.png]

## Causal decision theory: seeing vs. doing

- **Block: The do-operator**
  - Observing X=x (evidence) vs doing X=x (intervention)
  - `do(X=x)`: sever arrows into X, fix X=x, propagate; adjustment over parents `Pa(X)`
  - Barometer/storm confounder example
  - CDT: `a* = argmax_a E[U | do(A=a)]`

## CDT on Newcomb's problem

- **Block: Two-boxing, and why** (+ causal-graph diagram: disposition S -> action A, prediction P; A,P -> U; CDT cuts S->A)
  - Newcomb setup; do(A) severs action from disposition, box contents fixed, two-boxing dominates
  - Predictably: two-boxers get $1,000, one-boxers get $1,000,000
  - CDT wins the battle, loses the war; discards the prediction's dependence on the agent

## CDT vs. physics: the intervention is a fiction

- **Block: Does CDT really "reflect physical reality"? (following Ebtekar & Hutter)**
  - do(A) holds the past fixed and magically sets the action -- what licenses cutting it from its causes?
  - In deterministic, time-reversible physics, the action has antecedents; a predictor reading them is ordinary physics
  - Severing incoming arrows contradicts embeddedness; throws away real correlations
  - Pressures moving the counterfactual onto the policy/computation

# Section: Evidential decision theory

## Evidential decision theory: condition, don't intervene

- **Block: EDT as conditioning**
  - `a* = argmax_a E[U | A=a]`; evaluate by the news the action brings
  - Newcomb: one-boxing is strong evidence the box is full; EDT one-boxes and gets the million
  - Contrast: `E[U | do(A=a)]` (CDT) vs `E[U | A=a]` (EDT)

## EDT mistakes evidence for control

- **Block: The smoking lesion**
  - Lesion causes cancer and the urge to smoke; smoking harmless, benefit b
  - EDT abstains (smoking is bad news) though abstaining does not reduce cancer: symptom vs lever
  - Scorecard: CDT loses Newcomb, EDT loses smoking lesion; missing a third kind of dependence

## Spurious counterfactuals: EDT breaks for self-aware agents

- **Block: Conditioning on a probability-zero action**
  - A self-aware agent can predict its own action; the un-taken action has P=0
  - `E[U | A=a]` becomes 0/0 -- undefined; un-taken action can be assigned any value (spurious counterfactual)
  - Foreshadows the 5-and-10 problem and the need for logical dependence

# Section: Functional & updateless decision theory

## Functional decision theory: choose the algorithm's output

- **Block: Identify with the computation, not the body**
  - You are an implementation of a decision computation; predictors/copies are other implementations
  - FDT counterfactual: "this algorithm, on this input, outputs a"; everything logically downstream changes
  - Newcomb (one-box, right reason) and smoking lesion (smoke) both handled correctly
  - Slogan: physically different (CDT) / evidence (EDT) / decision computation different (FDT)

## Twin Prisoner's Dilemma & subjunctive dependence

- **Block: Same function, two bodies** (+ diagram: logical fact -> my action, twin's action)
  - Twin PD; CDT both defect ($1 each); FDT both cooperate ($3 each)
  - Subjunctive dependence: two systems depend on one logical fact; FDT controls all instances at once

## Counterfactual mugging: the updateless move

- **Block: Paying in a branch you know you're not rewarded in** (+ tree diagram: coin -> tails reward / heads cost, one policy spans both)
  - Setup; updateful refuses ($100 cost only); ex-ante policy "pay if asked" worth (R-c)/2 > 0
  - UDT pays: evaluate against the prior, don't delete the branch your policy controls
  - Updatelessness is not ignorance; reflective stability (nothing to self-modify)

## UDT 1.1: optimise the whole policy, not one action

- **Block: When local outputs must be coordinated** (+ diagram: one global policy -> obs 1 / obs 2, coordinated)
  - Copied-agent anti-coordination; local "if Alg(1)=A then Alg(2)?" is the wrong type
  - UDT 1.1 (Wei Dai): choose the whole policy `pi*`, then apply to the actual observation
  - Global optimisation over branches, not local optimisation

## The three shifts in "what am I choosing?"

- **Block: CDT/EDT -> FDT -> UDT 1.0 -> UDT 1.1 (after Kosoy's formalism)**
  - Table: rule / object chosen / update status / dependence used
  - Shift 1 (FDT): physical act -> algorithm output
  - Shift 2 (UDT 1.0): posterior -> prior
  - Shift 3 (UDT 1.1): single output -> whole policy

# Section: Problems with UDT

## Problem 1: paying for worlds that don't exist

- **Block: Ex-ante optimality is only as good as the prior**
  - UDT burns real utility in the actual branch (pays $100 in heads for a tails-world it knows didn't happen)
  - Bad when the prior misjudges which worlds are possible: a real, exploitable tax for fake benefits
  - Is "best from the prior" the right notion of rational?

## Problem 2: logical updatelessness

- **Block: Which prior, when some of your uncertainty is mathematical?**
  - Uncertainty is also logical (own source code, digits of pi, halting)
  - "Don't update" is clear empirically, unclear logically: thinking longer = learning = looks like updating
  - Logical updatelessness; no coherent "logical prior"; open problem, needs logical uncertainty

# Section: The 5-and-10 problem

## The 5-and-10 problem

- **Block: The simplest decision, made impossible by self-knowledge**
  - Take $5 or $10; obviously $10
  - Embedded agent can prove facts about its own action
  - Naive proof-based agent: prove "(A=5)=>U=x", "(A=10)=>U=y", take higher
  - Trap: un-taken action makes "(A=10)=>U=0" vacuously true -- a spurious counterfactual -> takes $5

## A self-contained look at Löb's theorem

- **Block: When "provable" is allowed to behave like "true"**
  - Box P = "P is provable"; distinguish the sentence Box P from the metafact "the system proves P"
  - Löb: if |- (Box P -> P) then |- P; equivalently |- Box(Box P -> P) -> Box P
  - Curry-style intuition
  - Special case P = false: a consistent system cannot prove its own consistency (Gödel II)

## Why Löb makes the spurious proof available

- **Block: The self-fulfilling proof**
  - S = ((A=10) => U=0); the agent built so proving S leads it to take $5
  - Box S -> S provable, so by Löb |- S; agent takes $5
  - A naive proof search is not safe; logical counterfactuals (counterpossibles) remain open
  - Embedded-agency moral; the same Löbian obstacle hits successor-trust / reflective stability

# Section: A formal criterion for decision theories

## Why we want a formal optimality criterion

- **Block: Beyond case-by-case scoring**
  - Newcomb, mugging, 5-and-10, twin PD, open-source games share structure (programs inspecting/simulating each other)
  - Theories judged case-by-case rather than against one standard
  - Substantive question: one class of environments + one optimality criterion

## Agents and worlds as programs

- **Block: The setup** (+ diagram: Agent <-> World, world queries agent and proves about it)
  - Agent: program with own + world source code -> action
  - World: program that may call the agent on many inputs and search for proofs about it -> utility
  - Goal: high utility across (almost) all worlds

## Fairness

- **Block: Judging the agent only on its behaviour**
  - Without it, worlds could punish source code; criterion vacuous
  - Fairness: world depends on the agent only through input/output behaviour (its policy)
  - Newcomb, smoking lesion, mugging, twin PD, open-source PD are all fair

## What a good agent must discover

- **Block: Two demands -- which are exactly FDT/UDT turned into a spec**
  - Coordinate across function calls (= UDT 1.1's policy view)
  - Subjunctive dependence: detect a subroutine isomorphic to itself (= FDT)
- **Block: The open problem (and the bridge ahead)**
  - Define the class, define optimality, show theories differ, ask whether any is optimal
  - Caveats: logical counterfactuals, logical uncertainty, what counts as a policy, multi-agent fairness/bargaining -> Deck II
