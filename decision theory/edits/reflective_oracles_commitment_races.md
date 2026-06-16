# Decision Theory II: Open-Source Game Theory, Commitment Races, and Safe Pareto Improvements

Title: **Decision Theory II** -- Open-Source Game Theory, Commitment Races, and Safe Pareto Improvements
Author: Daniel C
Date: (placeholder)

Markdown mirror of `projects/reflective_oracles_commitment_races/main.tex` (16 slides).
Add `<div>...</div>` edit markers after any line to request a change.

(The reflective-oracle / embedded-AIXI material was removed; this deck now covers only
open-source game theory, commitment races, and safe Pareto improvements.)

---

## Title page

## Where we are: agents that read each other's code

- **Block: Cooperation and conflict between embedded agents** — fair computational worlds; the strategic question (cooperate without conflict, without being exploitable); the thread: open-source game theory, commitment races, safe Pareto improvements

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
