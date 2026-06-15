# Decision Theory II: Reflective Oracles, Open-Source Games, and Commitment Races

Title: **Decision Theory II** -- Reflective Oracles, Open-Source Games, and Commitment Races
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/reflective_oracles_commitment_races/main.tex` (20 slides).
Add `<div>...</div>` edit markers after any line to request a change.

The reflective-AIXI section paraphrases and credits Cole Wyeth's *Embedded Agency* slides.

---

## Title page

## Where we are: agents that model each other

- **Block: Two foundational obstacles to mutual modelling**
  - Deck I ended at fair computational worlds (agent and world are programs modelling each other)
  - (1) Can a Bayesian agent represent agents like itself? (reflective oracles)
  - (2) When agents read each other's code, how do they cooperate without conflict? (open-source games, commitment races, SPI)
  - Reflective oracles solve mutual modelling semantically; open-source games solve it syntactically; both then face commitment

# Section: Self-modelling failures & AIXI  (following C. Wyeth)

## Large agents vs. embedded agents

- **Block: The cybernetic picture and its hidden assumptions**
  - Cybernetic model: learn a model, plan to a goal
  - Hidden assumptions: agent "larger than" the world, agent "outside" the world (1 => 2)
  - Embedded reality: agent is part of the world; can be copied/modified; other equally powerful agents exist
  - Can we reason when the agent is smaller than its environment?

## AIXI: the ideal large agent

- **Block: Optimal planning against a universal mixture**
  - History-based RL
  - AIXI: optimal for computable environments; Bayesian mixture over all programs (Solomonoff prior, weight ~ 2^-length)
  - One-line idea: try every program-world, weight by simplicity, act to maximise expected reward
  - Gold standard of the idealised dualistic agent

## AIXI cannot model itself

- **Block: "AIXI does not believe the universe contains AIXI"**
  - Joint history prediction does not transfer cleanly to RL; may not converge
  - AIXI's environment is lower semi-computable, but AIXI's own policy is not; no self-copy in its hypothesis class
  - Self-modelling failure (Wyeth--Hutter): prediction of selected bits can fail (infinitely-often doubt); normalising patches some

## The grain of truth problem

- **Block: Bayesian agents that are never "infinitely surprised"**
  - Agents modelling each other must be the "same size"; AIXI cannot learn an environment containing other AIXIs
  - Grain of truth: prior assigns positive probability to the truth (truth absolutely continuous w.r.t. the agent's beliefs)
  - Naive constructions hang (mutual calls do not halt); need same-size prediction without hanging

## Reflective oracles

- **Block: Self-reference without paradox, via randomisation** (+ diagram: machine T <-> oracle O <-> machine T')
  - Reflective oracle O answers "is P(T outputs 1) > p?" for machines that may call O
  - Liar machine handled by randomising on borderline cases (true probability equals threshold)
  - Reflective-oracle-computable strategies closed under mutual modelling; reflective AIXI has the grain of truth
  - Consequences: Nash-equilibrium convergence; acausal coordination in the PD; failures vanish
  - Bridge: semantic (oracle) vs syntactic (read the code) mutual modelling

# Section: Open-source game theory

## A 60-second refresher on game theory

- **Block: Nash, and the Prisoner's Dilemma** (+ 2x2 PD payoff matrix)
  - Normal-form game; Nash equilibrium (no profitable unilateral deviation)
  - PD: (C,C) beats (D,D) for both, but D dominates; unique Nash (D,D)
  - Root cause: payoff depends on the joint action but you cannot condition on the other's choice

## Löbian cooperation: FairBot

- **Block: When players can read each other's code**
  - Open-source/program game (Tennenholtz): submit a program taking the opponent's source code -> action
  - FairBot: cooperate iff it can prove the opponent cooperates
  - FairBot vs FairBot: by Löb's theorem both prove mutual cooperation and cooperate (Box(Box C -> C) -> Box C)
  - Unexploitable: cooperates with CooperateBot, defects against DefectBot; never the sucker
  - Caveat: proof-based FairBot is brittle (syntactic, may not terminate)

## Robust cooperation by simulation: epsilon-grounded bots

- **Block: Replacing proofs with simulation (Oesterheld)**
  - epsilon-grounded FairBot: prob epsilon cooperate unconditionally; else run opponent on your code and copy
  - Terminates: each level grounds with prob epsilon, recursion halts a.s.
  - Two of them cooperate (a.s.); a Nash equilibrium; robust (behaviour, not syntax)
  - epsilon-grounded pi-Bot and generalisations (arXiv:2412.14570)

## What open-source game theory is really doing

- **Block: Conditional commitment**
  - Two desiderata: cooperate with your own copy; unexploitability
  - Ordinary game theory fails on mutual uncertainty (cannot condition)
  - Open-source game = conditional commitment: "I commit to X conditional on you committing to Y"
  - Conditional part = unexploitable; commitment part = legible cooperation; FairBot is exactly this

# Section: Commitment races

## The commitment races problem

- **Block: Why consequentialists race to commit (Kokotajlo)**
  - Consequentialist = bully and coward; whoever commits first controls the later committer
  - A race to commit before thinking/learning; thinking longer leaks information
  - Catastrophe modes: incompatible commitments lock in (Chicken crash); wasteful racing (arms race)

## Moving first in logical time; and s-risks

- **Block: Why this is a safety priority**
  - "First" = logical time (who effectively decides first under mutual prediction)
  - s-risks: threats are the worst commitments; races can lock in carrying out catastrophic threats
  - A theory that avoids commitment races is a genuine safety goal

## Influencer vs. responder

- **Block: The first-mover's advantage, and the race it triggers** (+ Pareto-frontier diagram: influencer's pick)
  - Responder: run opponent, observe action, best-respond
  - Influencer: assume opponent is a responder; pick the frontier point best for you, worst for them
  - "The best response is not the best response"; everyone wants to be the influencer -> a race

## The generalized commitment race: entanglement

- **Block: Why agents are not incentivised to make Pareto improvements**
  - You optimise against a distribution over the opponent's possible programs, including counterfactual ones
  - Cannot just maximise against the actual program; incentive entangled with counterfactual programs
  - Punishing = forgoing utility against the actual program to gain against counterfactual ones
  - Entanglement is the obstacle to Pareto improvements; the generalized commitment race

# Section: Safe Pareto improvements

## Safe Pareto improvements (SPI)

- **Block: Improving on a default that risks conflict**
  - Setup (Oesterheld--Conitzer; DiGiovanni--Clifton--Macé, arXiv:2403.05103): delegate to representatives; default = play the game
  - SPI: a re-instruction guaranteed to make every player weakly better off, no probabilistic assumptions
  - Example: strip the destructive outcome from a Chicken-style game
  - Clean guarantee (at least your lowest payoff in any efficient outcome) -- under a strong assumption

## The assumption SPI relies on -- and the cheating problem

- **Block: Participation independence**
  - Participation independence: representatives play the transformed game the same as the default
  - Cheating problem: knowing SPI removes conflict cost, an agent submits a more hawkish default
  - Anticipating this, the opponent's incentive to offer SPI is undermined; SPI can defeat itself

## Entanglement-free SPI: the idea

- **Block: Make the improvement with an entanglement-free program**
  - Diagnosis: entanglement disincentivises Pareto improvements
  - Renegotiation program; sequential structure: exchange and update on the actual renegotiation program first
  - Update on the actual program => no entanglement => no incentive to punish/reject improvements
  - Renegotiation may only Pareto-improve: cannot make the opponent worse off (no influencer exploitation, even moving first); conditions on defaults to detect cheating (drops participation independence)
  - Full action space retained; renegotiation only adds the Pareto-improve option

## Entanglement-free SPI: the protocol

- **Block: A clean formalism** + diagram of the 4-stage protocol
  - Open-source game: A = A1 x A2, u_i: A -> R, programs p_i: P_{-i} -> A_i, joint action (p1(p2), p2(p1))
  - Renegotiation function rn_i: RN_{-i} x A -> C(A), proposes Pareto-improvements on a, conditional on opponent's rn
  - Entanglement-free renegotiation program en_i: P_{-i} -> RN_i (reads opponent's default program)
  - Intersection I = rn_1(rn_2,a) cap rn_2(rn_1,a); final outcome sel(I); choice of sel adds no coordination problem (DiGiovanni)

## Why first-mover is safe here -- and what we trade away

- **Block: Resolving the race without creating a new one**
  - The first move can only Pareto-improve, so it cannot exploit; no new commitment race
  - Solves the cheating problem and drops participation independence (renegotiation conditions on defaults)
  - Trade-off: dropping the assumption forfeits the original SPI's clean minimum-payoff bound
