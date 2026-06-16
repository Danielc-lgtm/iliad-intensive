# Decision Theory II: Reflective Oracles, Open-Source Games, and Commitment Races

Title: **Decision Theory II** -- Reflective Oracles, Open-Source Games, and Commitment Races
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/reflective_oracles_commitment_races/main.tex` (31 slides).
Add `<div>...</div>` edit markers after any line to request a change.

The reflective-AIXI section mirrors Cole Wyeth's *Embedded Agency* slides in detail; its
diagrams are recreated in TikZ (cybernetic/embedded-agent figures after the LessWrong
Embedded Agency sequence). Formulas after Hutter and Wyeth & Hutter (arXiv:2505.17882).

---

## Title page

## Where we are: agents that model each other

- **Block: Two foundational obstacles to mutual modelling** — fair computational worlds; (1) can a Bayesian agent represent agents like itself? (reflective oracles); (2) cooperation without conflict (open-source games, commitment races, SPI); semantic vs syntactic mutual modelling

# Section: Self-modelling failures & AIXI  (mirrors C. Wyeth's Embedded Agency slides; diagrams recreated)

## The cybernetic model and large agents

- **Block: Learn a model, then plan with it** (+ TikZ: cybernetic loop, agent with dashed boundary <-> environment, action / percept,reward)
  - cybernetic model: learn a model, plan to a goal
  - two assumptions: (1) agent "larger than" the environment (mind holds a full copy); (2) agent "outside" it; 1 => 2; model-based RL assumes 2

## The actual situation: embedded agency

- **Block: The agent is a part of the world** (+ TikZ: agent + incomplete model inside the environment box)
  - agent is a special part of the environment; may be modified/destroyed/copied between steps; other equally powerful agents may exist, mutually reasoning
  - safety relevance: reward hacking, shutdown problem, user identification
  - can we reason when the agent is smaller than its environment?

## History-based reinforcement learning

- **Block: The general framework** (+ TikZ: Agent <-> Environment loop with actions a_n / percepts o_n, rewards r_n; interaction timeline)
  - model a general class of tasks as history-based RL; percepts e_n=(o_n,r_n); history a_1 o_1 r_1 a_2 o_2 r_2 ...

## AIXI

- **Block: The optimal history-based agent for computable environments [Hut00]**
  - plans optimally against a Bayesian mixture of all programs (Solomonoff prior, weight 2^{-l(q)})
  - one-line formula: `a_k := argmax_{a_k} sum_{o_k r_k} ... max_{a_m} sum_{o_m r_m} [r_k + ... + r_m] sum_{q: U(q,a_{1:m})=e_{1:m}} 2^{-l(q)}`

## Joint history prediction: the idea

- **Block: Predict the whole tape, actions included** (+ TikZ: joint-history tape, env-state boxes with nested agent-state, over time)
  - jointly predict the entire history; `a_1 e_1 a_2 e_2 ... = h ~ rho`; cybernetic special case `rho = mu^pi`

## Joint history prediction: Solomonoff's mixture

- **Block: From pure prediction to a joint belief**
  - Solomonoff `M(x) = sum_{p: U(p)=x*} 2^{-l(p)}`; Hutter extends to decisions
  - joint AIXI belief `xi^U(e_{1:t} || a_{1:t}) = prod_{i=1}^t M(e_i | h_{<i} a_i)`; why not use this for the joint distribution?

## Joint history prediction: why it breaks for RL

- **Block: Joint prediction does not transfer cleanly**
  - doesn't transfer to RL; may not converge under the cybernetic assumption
  - uncomputable odd bits destroy Solomonoff prediction on computable even bits: 11 00 00 11 11 11 11 ...
  - uncomputable actions break percept prediction; normalising M patches this

## Semimeasure loss

- **Block: The missing probability mass** (+ TikZ: bar M(0|x) | gap | M(1|x), reallocation)
  - semimeasure `nu(x) >= sum_a nu(xa)`; multiple ways to complete/normalise; the reallocated gap = semimeasure loss

## Prediction of selected bits

- **Block: The semimeasure loss can be large infinitely often**
  - large infinitely often [Lattimore--Hutter--Gavane]
  - Theorem 7 (adversarial non-convergence of xi^U) [Wyeth--Hutter]: exists e=a in B^inf with `xi^U(e_{1:t} || a_{1:t}) = xi^U(a_{1:t} || a_{1:t}) -> 0`
  - reward always matched the action bit yet AIXI infinitely often doubts; caution: maybe not on-policy; fails when M normalised

## AIXI is much "larger" than its environment

- **Block: The agent is not in its own hypothesis class** (+ TikZ: hypothesis class M not containing AIXI's policy)
  - environment lower semicomputable (Sigma^0_1); AIXI's policy is not — higher in the arithmetical hierarchy (... Delta^0_n subset Sigma^0_n,Pi^0_n subset Delta^0_{n+1} ...)
  - "AIXI does not believe the universe contains AIXI agents"

# Section: The grain of truth problem & reflective oracles

## Modeling multi-player games

- **Block: Mutual modelling needs same-size agents** (+ TikZ: two agents each modelling a small copy of the other, "same size")
  - agents modelling each other must be "same size"; AIXI can't learn the env contains other AIXIs; multiplayer != being-inside-the-environment

## The grain of truth problem

- **Block: Correctly-specified subjective models**
  - never "infinitely surprised" by a positive-probability event; given class of games G, strategies P, beliefs xi_i
  - grain of truth: each optimal policy pi*_{xi_i} in P; each belief `xi_i >> sigma^pi` for all sigma in G, pi in P^n; >> = absolute continuity (truth a.c. w.r.t. belief; Blackwell--Dubins merging)

## Solution with reflective oracles (I): the construction

- **Block: Precise access to others, without hanging** (+ TikZ: machine T <-> oracle O <-> machine T')
  - fails for AIXI; naive `lambda_T(x_t | x_{<t}) = P[T(x_{<t})=x_t]` but policies hang
  - reflective oracle O gives precise access to the RHS: `lambda^O_T(x_t | x_{<t}) = P[T^O(x_{<t})=x_t]`; randomise at the threshold (no hang, no liar paradox); exists (Fallenstein--Taylor--Christiano); builds reflective AIXI with the grain of truth

## Solution with reflective oracles (II): results

- **Block: What reflective oracles buy** — dualistic multiplayer: Nash-equilibrium convergence and Thompson-sampling optimality [Leike--Taylor--Fallenstein; Wyeth et al.]; with policy correlations (joint prediction): acausal coordination in the PD [Meulemans et al.]; semimeasure loss eliminated and selected-bits prediction succeeds

## Solution with reflective oracles (III): self-modelling

- **Block: Using the self-model -- and its limits** — exploit the self-model to avoid planning; reason about self-modifications; hard to prove optimality; `a_1 e_1 a_2 e_2 ... ~ xi^O`, `pi_S(h_{<t}) in argmax_{a_t} xi^O(sum_{i=t}^inf gamma_i r_i | h_{<t} a_t)`; bridge: semantic (oracle) vs syntactic (read the code)

# Section: Open-source game theory

## A 60-second refresher on game theory

- **Block: Nash, and the Prisoner's Dilemma** (+ 2x2 PD payoff matrix) — normal-form game; Nash; PD unique Nash (D,D) though (C,C) better; cannot condition on the other's choice

## Löbian cooperation: FairBot

- **Block: When players can read each other's code** — open-source/program game (Tennenholtz); FairBot; FairBot vs FairBot cooperate by Löb (Box(Box C -> C) -> Box C); unexploitable; brittle

## Robust cooperation by simulation: epsilon-grounded bots

- **Block: Replacing proofs with simulation (Oesterheld)** — prob epsilon cooperate unconditionally, else simulate and copy; terminates a.s.; Nash equilibrium; robust; arXiv:2412.14570

## What open-source game theory is really doing

- **Block: Conditional commitment** — desiderata (cooperate with copy; unexploitability); mutual uncertainty; "I commit to X conditional on you committing to Y"; conditional = unexploitable, commitment = legible; FairBot is exactly this

# Section: Commitment races

## The commitment races problem

- **Block: Why consequentialists race to commit (Kokotajlo)** — bully and coward; first committer controls later; race to commit before learning; catastrophe modes (incompatible lock-in; wasteful racing)

## Moving first in logical time; and s-risks

- **Block: Why this is a safety priority** — logical time; threats and s-risks; avoiding commitment races is a safety goal

## Influencer vs. responder

- **Block: The first-mover's advantage, and the race it triggers** (+ Pareto-frontier diagram: influencer's pick) — responder (best response); influencer (assume opponent responds; pick frontier point best for you); "the best response is not the best response" -> a race

## The generalized commitment race: entanglement

- **Block: Why agents are not incentivised to make Pareto improvements** — optimise against a distribution over counterfactual opponent programs; punishing = forgoing utility against the actual program; entanglement is the obstacle; persists with full conditional commitment

# Section: Safe Pareto improvements

## Safe Pareto improvements (SPI)

- **Block: Improving on a default that risks conflict** — delegate to representatives; SPI = guaranteed weak Pareto improvement; Chicken example; bound = Pareto Meet Minimum (PMM), tight, under a strong assumption (Oesterheld--Conitzer; DiGiovanni--Clifton--Macé, arXiv:2403.05103)

## Why an SPI guarantees a floor: the Pareto Meet Minimum

- **Block: The shape of the renegotiation set controls exploitation** (+ Pareto-frontier diagram: A best for me, A' best for opp, floor = u_1(A')) — point A best for me; include up to A; beyond A enables exploitation; floor = opponent's A-point = your lowest efficient payoff = PMM (tight)

## The assumption SPI relies on -- and the cheating problem

- **Block: Participation independence** — representatives play the SPI game the same as default; cheating problem (hawkish defaults when conflict is cheap); SPI can defeat itself

## Entanglement-free SPI: the idea

- **Block: Make the improvement with an entanglement-free program** — renegotiation program; exchange and update on the actual one first; no entanglement; may only Pareto-improve (no influencer exploitation; conditions on defaults to catch cheating, drops participation independence); full action space retained

## Entanglement-free SPI: the protocol

- **Block: A clean formalism** + 4-stage protocol diagram — open-source game A=A1xA2, programs p_i; renegotiation function rn_i: RN_{-i} x A -> C(A); entanglement-free renegotiation program en_i: P_{-i} -> RN_i; intersection I = rn_1(rn_2,a) cap rn_2(rn_1,a); sel(I) final (sel adds no coordination problem, DiGiovanni)

## Why first-mover is safe here -- and what we trade away

- **Block: Resolving the race without creating a new one** — first move can only Pareto-improve, cannot exploit; solves cheating + drops participation independence; no new commitment race
  - trade-off (no tight PMM): renegotiation conditions on defaults -> incentive gradient (more cooperative default => more improvement); may withhold improvement, so the agreed set is no longer "up-to-A" and the tight PMM floor is lost
