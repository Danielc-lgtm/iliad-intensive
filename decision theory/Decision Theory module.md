# Table of Contents

# Contributors

Daniel C and Satya Benson (Williams College) wrote and taught the module. Satya Benson created and ran the Open-Source Prisoner’s Dilemma Tournament. The lecture slides, reading list, and tournament handout are linked in the Content section below.

# Learning outcomes

**(What.)** By the end of the day, students can explain why decision theory is hard for an *embedded* agent (its action is just another fact about the world, so counterfactuals must be constructed, not read off) and can state the four main theories and what each gets right and wrong: CDT (intervene), EDT (condition), FDT (choose your decision function’s output), and UDT 1.0/1.1 (act on the policy you would have committed to in advance). They can work the canonical problems (Newcomb, smoking lesion, counterfactual mugging, twin prisoner’s dilemma) and say which theory each one separates. They understand the multi-agent layer: open-source game theory and Löbian cooperation (FairBot), commitment races, and safe Pareto improvements. They apply all of this by designing and submitting a bot to the open-source Prisoner’s Dilemma tournament.

**(Why.)** To make a superintelligence safe we will likely prove safety properties under assumptions about *how the agent decides*. Decision theory is a *reflectively-consistent degree of freedom*: unlike a mistaken factual belief, a bad decision theory is not automatically corrected as an agent gets smarter, so a load-bearing assumption (“the agent is CDT”) can silently fail if the agent self-modifies. The multi-agent failures (commitment races, conflict, exploitable cooperation) are direct AI-safety concerns, and safe Pareto improvements are one of the few constructive tools against them.

**(How.)** A morning lecture builds the theories in order (CDT/EDT to FDT to UDT), motivated by the problems that break each one. A two-hour reading and discussion block has students wrestle with the primary sources and a transparency-and-cooperation prompt. An afternoon lecture moves to the multi-agent setting (open-source game theory, commitment races, safe Pareto improvements). The day ends with a programming tournament that operationalizes program equilibrium and Löbian cooperation.

# Prerequisites

- Basic probability and expected value; comfort reading pseudocode.
- Helpful but not required: Löb’s theorem (covered on the Agent Foundations day; it underlies FairBot and the tournament’s cooperation results) and a first acquaintance with Bayesian networks and the causal do-operator (re-introduced briefly in the lecture).
- No prior decision-theory background assumed; Newcomb’s problem and the rest are introduced from scratch.

# Content

Slides: Deck I (Decision Theory: CDT to UDT) and Deck II (Open-Source Game Theory, Commitment Races, and Safe Pareto Improvements), linked from the [Decision Theory session page](https://iliad.au.pe/sessions/decision-theory/participant-guide.html). Tournament handout: [Open-Source Prisoner’s Dilemma Tournament](https://iliad.au.pe/sessions/decision-theory/handout.html).

## Fast-track

To get the core in about an hour, or to catch up after missing the day:

- Read “The four decision theories” and “The multi-agent layer” below.
- Read the [FDT paper](https://arxiv.org/abs/1710.05060) (at least chapters 1-3) for the FDT/UDT picture, and skim [Towards a new decision theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory).
- Read the tournament handout and write a one-paragraph bot (even “cooperate only if the opponent provably cooperates with me” is enough to engage with the ideas).

## Main content

The day has four sub-modules: the **morning lecture** (single-agent decision theory), the **reading and discussion** block, the **afternoon lecture** (multi-agent decision theory), and the **tournament**, closing with a **daily checkpoint**.

### Morning lecture

*Intent: build the four decision theories (CDT, EDT, FDT, UDT) in the order forced by the problems that break each one, so students see each theory as the fix for the previous one’s failure rather than as an arbitrary option. Protect the CDT-vs-EDT contrast and the FDT reframing above the formal asides.*

**Why decision theory, and why it is hard.** For a *dualistic* agent cleanly separated from the world, the action is a free variable and the rule is just `a* = argmax_a E[U | do(A=a)]`. For an *embedded* agent the action is itself a fact about the world (predictors may have modelled it, copies may share it), so “what happens if I act differently” is a counterfactual that must be *constructed*. The decision theories differ in how they construct it.

**EDT and CDT: condition vs intervene.**

- *Evidential decision theory* conditions on the action as evidence: `a* = argmax_a E[U | A=a]`. This treats the action as news about everything correlated with it.
- *Causal decision theory* intervenes: `a* = argmax_a E[U | do(A=a)]`, severing the arrows *into* the action in a causal (Bayesian-network) model, so the action is news about its effects only.
- They split on the canonical cases. On **Newcomb’s problem** (a predictor fills a box based on your disposition), EDT one-boxes and wins \$1,000,000; CDT two-boxes (the prediction is already made) and wins \$1,000. On the **smoking lesion** (a common cause produces both a disposition to smoke and the disease), EDT wrongly abstains (smoking is bad *evidence* though not a *cause*); CDT correctly smokes. Neither rule handles both, which points to a third kind of dependence.
- *(Aside, for the mathematically inclined.)* The two rules drop out of two ways to model the agent’s interaction history: CDT is a chronological-semimeasure predictor (actions are conditioned-on inputs, never predicted, exactly the do-operator), while EDT is a joint predictor over actions and observations (conditioning on an action updates beliefs about which world and which policy you are). The slides develop this; it can be skipped without loss.

**FDT: choose your function’s output.** Functional decision theory reframes *what you are choosing*. You run a fixed decision function; your action is its output, and everything that depends on that function (predictors who modelled it, copies running it, simulations of it) moves together with the output. FDT asks “which output of this decision function, given everything that depends on it, yields the best outcome?” It one-boxes on Newcomb and smokes on the smoking lesion. Its signature case is the **twin prisoner’s dilemma**: two copies of the same agent share the same logical output (*subjunctive dependence*), so FDT cooperates (each gets \$3) where CDT defects (each gets \$1). Causal dependence is a special case of subjunctive dependence; mere correlation (the lesion) is not.

**UDT: act on the policy you would have committed to.**

- *UDT 1.0* chooses each action as the one a prior-stage self would have committed to: `choice(o) = argmax_a E[U | choice(o)=a]`. On **counterfactual mugging** (a coin you have already seen land the wrong way, where paying in this branch is what makes paying profitable across branches), the updateful agent refuses and the updateless agent pays, because ex ante paying is worth `(R-c)/2`. Updatelessness is not ignorance; it is refusing to update away a commitment that is good in expectation, which makes it reflectively stable.
- *UDT 1.1* optimizes the whole *policy* (a map from observations to actions) rather than each action separately, then applies it: `S* in argmax_{S:O->A} E[U | choice=S]`. This is needed when copies must coordinate their actions across branches, which per-observation optimization can get wrong.

**Where this is heading.** The shift across CDT/EDT to FDT to UDT 1.0 to UDT 1.1 is a shift in *what you are choosing*: an action, then a function’s output, then an output you do not update away, then a whole policy. Two hard problems remain: UDT pays real utility in the actual branch and is only as good as its prior, and *logical updatelessness* (what is the right “prior” when some uncertainty is mathematical?) has no clean answer. The **5-and-10 problem** shows the deeper trouble: a naive proof-searching agent can be driven by a spurious Löbian proof to take the worse action, because counterfactuals over one’s own action break down. The frontier goal is to formalize decision problems as programs and ask which theory is *optimal* over a well-defined class of “fair” problems (where the world depends only on the agent’s input/output behaviour); the two demands such a criterion forces (coordinate across calls; detect an isomorphic copy of yourself) are exactly UDT 1.1 and FDT turned into a specification.

### Reading and discussion

*Intent: the primary sources are where FDT and UDT were worked out and argued over; the block has students confront the actual arguments and one open multi-agent question, so the afternoon lecture lands on prepared ground.*

Readings (arranged roughly chronologically; the FDT paper is the primary reference):

- [Functional decision theory: a new theory of instrumental rationality](https://arxiv.org/abs/1710.05060) (chapters 1-5).
- [Towards a new decision theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory).
- [Updateless decision theory](https://www.lesswrong.com/w/updateless-decision-theory).
- [Conceptual problems with UDT and policy selection](https://www.lesswrong.com/posts/9sYzoRnmqmxZm4Whf/conceptual-problems-with-udt-and-policy-selection).
- [Pitfalls of building UDT agents](https://www.lesswrong.com/posts/y3zTP6sixGjAkz7xE/pitfalls-of-building-udt-agents).

Discussion prompt (transparency and cooperation): consider two agents A1 and A2 whose code, preferences, and decision algorithms become perfectly transparent to each other at time T (state your interpretation of “transparent” where it matters). Under these conditions, when might A1 and A2 end up in a *Pareto-inefficient* outcome? Where inefficiency looks plausible but a non-obvious argument rules it out, give that argument. (This prompt is the bridge to the afternoon: it is exactly the open-source-game-theory setting.) Supporting afternoon readings: [When would AGIs engage in conflict?](https://www.lesswrong.com/posts/cLDcKgvM6KxBhqhGq/when-would-agis-engage-in-conflict) and [Individually incentivized safe Pareto improvements in open-source bargaining](https://www.lesswrong.com/posts/uGfDx9es2pnYWaWJr/individually-incentivized-safe-pareto-improvements-in-open).

### Afternoon lecture

*Intent: move from one agent against the world to the multi-agent layer (agents reasoning about each other’s code), and show both the cooperation it unlocks (FairBot) and the new failure it creates (commitment races), then the constructive response (safe Pareto improvements). This is the conceptual setup the tournament makes concrete.*

**Open-source game theory.** When players can read each other’s source code, cooperation becomes possible without repetition or prior trust. **FairBot** cooperates if and only if it can prove its opponent cooperates with it; two FairBots cooperate by Löb’s theorem (from `□(□C -> C) -> □C`). It is unexploitable but brittle (it relies on a proof system and exact source). **Epsilon-grounded bots** (Oesterheld) replace proofs with simulation: cooperate unconditionally with small probability epsilon, else simulate the opponent and copy its move; this terminates almost surely, is a Nash equilibrium, and is robust. The unifying idea is *conditional commitment*: “I commit to X conditional on you committing to Y.” Conditional makes it unexploitable; commitment makes it legible. FairBot is exactly this.

**Commitment races.** Among consequentialists who can commit, there is an incentive to commit *first*: the first mover can pick the point on the bargaining frontier best for itself and leave the responder to best-respond. So “the best response is not the best response”, and agents race to commit before they even finish learning, risking incompatible lock-in or wasteful conflict (including threats and s-risks). Moving first “in logical time” is a genuine safety concern, which makes *avoiding* commitment races a safety goal. The deeper obstacle is *entanglement*: each agent optimizes against a distribution over the *counterfactual* programs the other might submit, so punishing a Pareto improvement means forgoing utility against the opponent’s *actual* program; the incentive to make improvements is entangled with those counterfactuals, and this persists even with full conditional commitment.

**Safe Pareto improvements (SPI).** An SPI modifies the agents’ default (conflict-prone) strategies so that *every* player is guaranteed at least as well off regardless of the opponent, a guaranteed weak Pareto improvement (Oesterheld-Conitzer; DiGiovanni-Clifton-Macé). In the open-source/program setting, each player individually prefers to use renegotiation-based SPIs, and the guaranteed floor is the *Pareto Meet Minimum* (your lowest efficient payoff), which is tight under a *participation-independence* assumption. That assumption can fail (agents may become hawkish when conflict is cheap), the “cheating” problem. *Entanglement-free SPI* (a research-frontier idea) restructures the interaction into two stages (exchange renegotiation programs, update on the actual one, then submit defaults), which breaks the entanglement and drops participation independence, at the cost of the tight floor. Teach the standard SPI result in full; present entanglement-free SPI briefly as the current frontier.

### The tournament

*Intent: make program equilibrium and Löbian cooperation concrete by having students design bots for the open-source Prisoner’s Dilemma tournament that read each other’s code, then watch which decision-theoretic ideas actually win. The grade is on the idea embodied, not leaderboard placement.*

Full rules are in the [tournament handout](https://iliad.au.pe/sessions/decision-theory/handout.html); the structure is summarized here so the day can be run from this document.

**The game.** The one-shot Prisoner’s Dilemma, with the twist that your program can read the opponent’s program before deciding (source is open). Payoffs (you, them): mutual cooperation `(C,C)` gives 3 each; mutual defection `(D,D)` gives 1 each; defecting against a cooperator gives 5 to the defector and 0 to the cooperated. This satisfies `T > R > P > S` (5 \> 3 \> 1 \> 0) and `2R > T + S` (6 \> 5).

**Two leagues.**

- *League A (one-shot, open source).* Bots see the opponent’s source and decide once. This is the program-equilibrium / Löbian-cooperation setting.
- *League B (iterated, history only).* Bots see the move history over a hidden number of rounds (around 100-200) and cannot read source. This is the classic reciprocity setting (Tit-for-Tat and relatives).

**Submitting a bot.** A submission may be in any form (real Python, pseudocode, or a careful English description) plus a short design rationale explaining the decision-theoretic approach; an LLM compiles it into the canonical `Agent` class:

    class Agent:
        def move_oneshot(self, opp) -> Move:                  # League A
        def move_iterated(self, my_hist, opp_hist, t) -> Move: # League B

In League A a bot may query: `opp.move_against(SELF)` (the opponent’s move against you), `opp.move_against(DEFECT_BOT)`, `opp.move_against(COOP_BOT)`, and `opp.source` (the opponent’s canonical source). League B provides only the two history lists and the round index `t`.

**How circular queries resolve.** Two source-reading bots can each ask “what does the other do against me?”, which is circular. Rather than simulate the recursion, the engine treats every “what does the opponent do against X?” query as a *provability* question and computes the fixed point directly, the same Löbian move that lets two FairBots cooperate. When no stable resolution exists, it applies a *no-wishful-thinking* rule: if cooperation cannot be established, default to D.

**Reference bots.** League A: CooperateBot, DefectBot, FairBot, PrudentBot, CliqueBot, RandomBot. League B: AllC, AllD, Random, TitForTat, GrimTrigger, GenerousTitForTat, Pavlov, TitForTwoTats. These seed the field and give students targets to beat or cooperate with.

**Scoring.** Round-robin: every bot plays every other bot, including a copy of itself, and ranking is by total points accumulated across all matchups (not head-to-head wins). League B matches add about 2% move-flip noise and a randomized hidden length, so brittle strategies are penalized.

**What good looks like.** A strong submission embodies a clear decision-theoretic concept (commitment, transparency, the limits of self-reference, functional decision theory) and explains it, rather than chasing the leaderboard. The standout lesson is usually that FairBot-style conditional cooperation beats both naive cooperation (exploited) and naive defection (misses mutual cooperation) in League A, while robustness to noise dominates in League B.

### Daily checkpoint

*Intent: a quick understanding-and-attendance check, easy for someone who followed the day and hard otherwise.*

Answers at the end of this section.

1.  On Newcomb’s problem, CDT and EDT differ because: (a) they use different payoffs; (b) CDT severs the action from the disposition the predictor read and two-boxes, while EDT treats one-boxing as evidence the box is full; (c) EDT cannot do arithmetic; (d) CDT is updateless.
2.  The smoking lesion is a problem for: (a) CDT; (b) EDT, which mistakes evidence for control; (c) FDT; (d) nobody.
3.  In the twin prisoner’s dilemma, FDT cooperates because: (a) it is altruistic; (b) both copies share the same logical output (subjunctive dependence), so the choice controls both; (c) the game is iterated; (d) it fears punishment.
4.  Two FairBots cooperate by: (a) simulation to fixed depth; (b) Löb’s theorem applied to “I cooperate if I can prove you cooperate with me”; (c) a binding contract; (d) random chance.
5.  A commitment race arises because: (a) communication is slow; (b) the first agent to commit can pick the frontier point best for itself, so each rushes to commit before learning; (c) commitments are illegal; (d) agents are irrational.
6.  A safe Pareto improvement guarantees: (a) the best possible outcome; (b) every player is at least as well off as the default, regardless of the opponent; (c) cooperation in every game; (d) a Nash equilibrium.

*Answers: 1(b), 2(b), 3(b), 4(b), 5(b), 6(b).*

## Learn more

**Single-agent decision theory.** The reading list above, plus the [FDT paper](https://arxiv.org/abs/1710.05060) for the full treatment; on the CDT-vs-EDT-as-prediction view, the chronological-semimeasure framing follows the algorithmic-thermodynamics line (Ebtekar and Hutter). The 5-and-10 problem and logical counterfactuals are developed in the MIRI decision-theory literature (Demski and Garrabrant).

**Multi-agent and open-source game theory.** The [annotated program-equilibrium bibliography](https://www.andrew.cmu.edu/user/coesterh/AnnotatedProgEqBibliography.html) (Oesterheld); the [epsilon-grounded FairBot paper](https://arxiv.org/abs/2412.14570); [When would AGIs engage in conflict?](https://www.lesswrong.com/posts/cLDcKgvM6KxBhqhGq/when-would-agis-engage-in-conflict); the safe-Pareto-improvement papers (Oesterheld-Conitzer; [DiGiovanni-Clifton-Macé](https://arxiv.org/abs/2403.05103)). Andrew Critch’s work on cooperative and uncooperative institution design is a good, pedagogically simple source for further exercises.

**Frontier.** Logical updatelessness and logical time; UDT 2 and policy-selection fixes; bargaining and notions of fairness (the Nash bargaining solution and the “zoo” of coalitional structures); entanglement-free safe Pareto improvements; reflective oracles and program equilibrium as a single picture.

# Teaching guide

The day alternates lecture, reading-and-discussion, lecture, and a programming tournament. The tournament is the capstone, so introduce it early enough that students can think about bots through lunch.

## Time schedule

- 10:00–11:00 Morning lecture (CDT/EDT to FDT to UDT).
- 11:00–13:00 Reading and discussion (120 min; primary sources and the transparency prompt).
- 13:00–14:00 Lunch (announce the tournament and the bot brief here so students can mull it over).
- 14:00–15:00 Afternoon lecture (open-source game theory, commitment races, safe Pareto improvements).
- 15:00–16:00 Open-source Prisoner’s Dilemma tournament (finalize bots, run, reveal leaderboard, debrief).
- 16:00–16:15 Daily checkpoint and feedback form.

(Lecture plus discussion totals 3 hours in the morning; the afternoon is a 1-hour lecture and a 1-hour tournament. If the room writes bots quickly, spend the saved time on the tournament debrief, which is where the decision-theoretic lessons land.)

## Required materials

- Projector and laptop for the two slide decks.
- The tournament engine (compiles submissions into the `Agent` class, runs the round-robin, computes the fixed-point League A queries, and produces the leaderboard) and a machine to run it on.
- A TA or instructor comfortable operating the engine (compiling submissions, running the round-robin, surfacing the leaderboard) during the tournament session.
- Laptops for students to draft bots, or paper (submissions can be plain English).
- The tournament handout, shared at the start of the day.
- Whiteboard for the discussion block.

## Morning lecture

Walk Deck I. Build the theories in problem-driven order: motivate each theory with the case that breaks the previous one (Newcomb forces past CDT’s two-boxing intuition, the smoking lesion forces past EDT, the twin PD forces FDT, counterfactual mugging forces updatelessness). **TN:** keep the chronological-semimeasure-vs-joint-prediction aside optional; it is elegant but costs time and is not needed for the tournament. **TN:** the 5-and-10 slide is the one to slow down on, because it is the bridge to “decision theory is genuinely unsolved” and motivates the fair-problems criterion.

## Reading and discussion

Run the discussion in small groups on the transparency prompt (in the Main content “Reading and discussion” section) after the readings. **TN:** the prompt is deliberately the open-source-game-theory setting in disguise; do not resolve it, let groups discover that transparency enables both cooperation (you can verify the other will cooperate) and new conflict (you can verify a threat is real). Surface a few group answers, then carry the unresolved tension into the afternoon lecture. As on the Agent Foundations day, in a room where some students have read everything, have them help their group rediscover the point rather than announce it.

## Afternoon lecture

Walk Deck II. **TN:** the throughline is one move repeated: conditional commitment unlocks cooperation (FairBot), then the same power to commit creates the commitment race, then safe Pareto improvements are the constructive response. Teach the standard SPI floor (Pareto Meet Minimum) carefully; present entanglement-free SPI as a brief frontier pointer, not a full derivation. End by handing straight into the tournament: the bots students are about to write are exactly the conditional-commitment programs the lecture described.

## The tournament

Announce the format and payoffs before lunch so students arrive with bot ideas; collect submissions (Python, pseudocode, or English plus a one-paragraph rationale) at the start of the session and have the engine compile them. **TN:** the single most valuable teaching moment is the reveal and debrief, not the run. Walk the leaderboard and ask *why* each top bot did well: FairBot-style conditional cooperators avoid being exploited by DefectBot while still cooperating with each other; CliqueBot-style “cooperate only with exact copies of me” looks clever but fails to cooperate with non-identical cooperators; naive CooperateBot gets exploited. In League B, connect the winner’s robustness to the 2% noise (this is why GrimTrigger is fragile and generous strategies recover). **TN:** require the design rationale and grade on the decision-theoretic idea embodied, not the score, or students optimize the leaderboard and miss the point. The no-wishful-thinking default (cooperation must be *established*, else defect) is itself a teachable instance of why self-reference needs grounding.

## Daily checkpoint

Run the six-question checkpoint (above) as a quick individual quiz, then read out the answers, and close with the feedback form.

# Notes for future iterations

- Tournament:
    - Tournament was well-liked, but probably the tournament needed to be introduced earlier in the day so that students had more time to think.
- Checkpoint:
    - Answers need to be randomized more.
- Notes about delivery:
    - Slides were too dense/heavy, with too much informtion in too small of a font
- Notes about content:
    - Students found the decision theory introduction very difficult to understand. It seems important to be upfront about the fact that decision theories only disagree in certain narrow (but important) circumstances, and emphasise that with a deterministic algorithim like an LLM, it is easy to run these experiments (twin prisnors dilemma, Newcomb's, smoking liasion, etc) and the (unbelivable) nature of the particular examples we give (e.g. clones or perfect predictors) is more of mnemonic device or for helping humans imagine what it is like. 
    - A major criticism is the perceived relevance of the topic. It seems a pragmatic way to convince students that decision theory is an important thing to think about is to explain that an LLM instance is an agent that needs to use functional decision theory in order to coordinate with other instances of itself. It is important to convey to students that a decision theory is the remaining free variable determining how an agent acts in some important edge cases once you have already specified that it is an expected utility maximiser with a given utility function.
    - Safe pareto improvements talk is very well received (although still maybe not well enough motivated; participants still seemed receptive to being more convinced about the importance of SPI in one-on-ones.) Probably still needed a bit of motivation to explain why this counts as agent foundations work that is important for the future (perhaps a lecturer could make the argument that safe pareto improvement is an illustartion that agent foundations has the power to be useful even in a world where we don't have AGI.)

