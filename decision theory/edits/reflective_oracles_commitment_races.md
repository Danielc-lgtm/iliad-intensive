# Decision Theory II: Reflective Oracles, Open-Source Games, and Commitment Races

Title: **Decision Theory II** -- Reflective Oracles, Open-Source Games, and Commitment Races
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/reflective_oracles_commitment_races/main.tex` (22 slides).
Add `<div>...</div>` edit markers after any line to request a change.

The reflective-AIXI section paraphrases and credits Cole Wyeth's *Embedded Agency* slides
(formulas after Hutter and Wyeth & Hutter, arXiv:2505.17882).

---

## Title page

## Where we are: agents that model each other

- **Block: Two foundational obstacles to mutual modelling** — fair computational worlds; (1) can a Bayesian agent represent agents like itself? (reflective oracles); (2) cooperation without conflict (open-source games, commitment races, SPI); semantic vs syntactic mutual modelling

# Section: Self-modelling failures & AIXI  (following C. Wyeth)

## Large agents vs. embedded agents

- **Block: The cybernetic picture and its hidden assumptions** — learn a model + plan; "larger than" and "outside" (1 => 2); embedded reality; smaller-than-environment

## AIXI: the ideal large agent

- **Block: Optimal planning against a universal mixture (Hutter)**
  - history-based RL; actions a_t, percepts e_t=(o_t,r_t), history h_{<t}
  - universal mixture: `xi(e_{1:m} || a_{1:m}) = sum_{nu in M} w_nu nu(e_{1:m} || a_{1:m})`, `w_nu = 2^{-K(nu)}`
  - AIXI expectimax: `a_t = argmax_{a_t} sum_{e_t} ... max_{a_m} sum_{e_m} (sum_{k=t}^m r_k) xi(e_{t:m} || h_{<t} a_{t:m})`
  - try every program-world, weight by simplicity, maximise expected reward; ideal dualistic agent

## Joint prediction, semimeasures, and selected bits

- **Block: Going beyond the cybernetic split -- and where it breaks**
  - jointly predict actions+percepts; Solomonoff `M(x) = sum_{p: U(p)=x*} 2^{-l(p)}`; cybernetic assumption = condition on actions
  - semimeasure: `nu(x) >= sum_a nu(xa)` (probability can leak)
  - selected-bits failure (Lattimore--Hutter--Gavane; Wyeth--Hutter): exists omega with omega_{2n}=omega_{2n-1} yet `liminf_n M(omega_{2n} | omega_{1:2n-1}) < 1`; AIXI infinitely often doubts a perfect pattern; normalising closes the semimeasure gap

## AIXI cannot model itself

- **Block: "AIXI does not believe the universe contains AIXI"** — environment lower semicomputable but AIXI's policy is not; no self-copy in M; Cartesian dualist (fixed policy, from outside); cannot represent an equally powerful agent

## The grain of truth problem

- **Block: Bayesian agents that are never "infinitely surprised"** — same-size modelling; grain of truth: truth mu absolutely continuous w.r.t. belief xi (`mu << xi`, i.e. `xi(x)=0 => mu(x)=0`); Blackwell--Dubins merging; naive constructions hang

## Reflective oracles

- **Block: Self-reference without paradox, via randomisation** (+ diagram: machine T <-> oracle O <-> machine T')
  - reflective oracle: `O(T,p) = 1 if P[T^O()=1] > p, 0 if < p` (either if =p); exists (Fallenstein--Taylor--Christiano)
  - liar machine contradicts a deterministic oracle; randomising at =p breaks the diagonalisation
  - closed under mutual modelling -> reflective AIXI has the grain of truth; Nash convergence; acausal coordination in the PD
  - bridge: semantic (oracle) vs syntactic (read the code)

# Section: Open-source game theory

## A 60-second refresher on game theory

- **Block: Nash, and the Prisoner's Dilemma** (+ 2x2 PD payoff matrix) — normal-form game; Nash; PD unique Nash (D,D) though (C,C) better; cannot condition on the other's choice

## Löbian cooperation: FairBot

- **Block: When players can read each other's code** — open-source/program game (Tennenholtz); FairBot (cooperate iff prove opponent cooperates); FairBot vs FairBot cooperate by Löb (Box(Box C -> C) -> Box C); unexploitable; brittle (syntactic, may not terminate)

## Robust cooperation by simulation: epsilon-grounded bots

- **Block: Replacing proofs with simulation (Oesterheld)** — prob epsilon cooperate unconditionally, else simulate and copy; terminates a.s.; Nash equilibrium; robust (behaviour not syntax); arXiv:2412.14570

## What open-source game theory is really doing

- **Block: Conditional commitment** — desiderata (cooperate with copy; unexploitability); mutual uncertainty; "I commit to X conditional on you committing to Y"; conditional = unexploitable, commitment = legible; FairBot is exactly this

# Section: Commitment races

## The commitment races problem

- **Block: Why consequentialists race to commit (Kokotajlo)** — bully and coward; first committer controls later; race to commit before learning; catastrophe modes (incompatible lock-in; wasteful racing)

## Moving first in logical time; and s-risks

- **Block: Why this is a safety priority** — logical time; threats and s-risks (astronomical suffering); avoiding commitment races is a safety goal

## Influencer vs. responder

- **Block: The first-mover's advantage, and the race it triggers** (+ Pareto-frontier diagram: influencer's pick) — responder (best response); influencer (assume opponent responds; pick frontier point best for you); "the best response is not the best response" -> a race

## The generalized commitment race: entanglement

- **Block: Why agents are not incentivised to make Pareto improvements** — optimise against a distribution over counterfactual opponent programs; punishing = forgoing utility against the actual program; entanglement is the obstacle; persists with full conditional commitment

# Section: Safe Pareto improvements

## Safe Pareto improvements (SPI)

- **Block: Improving on a default that risks conflict** — delegate to representatives (default = play the game); SPI = guaranteed weak Pareto improvement, no probabilistic assumptions; Chicken example; bound = Pareto Meet Minimum (PMM), tight, under a strong assumption (Oesterheld--Conitzer; DiGiovanni--Clifton--Macé, arXiv:2403.05103)

## Why an SPI guarantees a floor: the Pareto Meet Minimum

- **Block: The shape of the renegotiation set controls exploitation** (+ Pareto-frontier diagram: A best for me, A' best for opp, floor = u_1(A'))
  - renegotiation set = accepted Pareto-improvements; on the frontier, better-for-opponent = worse-for-me
  - point A best for me; include points up to A (pushing opponent below A can't help me); beyond A enables exploitation
  - so sets stop at each player's A; worst agreed outcome = opponent's A-point = your lowest efficient payoff = PMM (tight)

## The assumption SPI relies on -- and the cheating problem

- **Block: Participation independence** — representatives play the SPI game the same as default; cheating problem (hawkish defaults when conflict is cheap); SPI can defeat itself (entanglement reappearing)

## Entanglement-free SPI: the idea

- **Block: Make the improvement with an entanglement-free program** — renegotiation program; exchange and update on the actual one first; no entanglement; may only Pareto-improve (no influencer exploitation; conditions on defaults to catch cheating, drops participation independence); full action space retained

## Entanglement-free SPI: the protocol

- **Block: A clean formalism** + 4-stage protocol diagram
  - open-source game: A=A1xA2, u_i, programs p_i: P_{-i}->A_i, joint action (p1(p2),p2(p1))
  - renegotiation function rn_i: RN_{-i} x A -> C(A) (Pareto-improvements on a, conditional on opponent's rn)
  - entanglement-free renegotiation program en_i: P_{-i} -> RN_i (reads opponent's default)
  - intersection I = rn_1(rn_2,a) cap rn_2(rn_1,a); sel(I) final; sel adds no coordination problem (DiGiovanni)

## Why first-mover is safe here -- and what we trade away

- **Block: Resolving the race without creating a new one** — first move can only Pareto-improve, cannot exploit; solves cheating + drops participation independence; no new commitment race
  - trade-off (no tight PMM): renegotiation conditions on defaults -> incentive gradient (more cooperative default => more improvement); may withhold improvement, so the agreed set is no longer "up-to-A" and the tight PMM floor is lost
