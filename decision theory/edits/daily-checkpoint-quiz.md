# Decision Theory: Daily Checkpoint (quiz answer key)

Live form (Jotform): https://form.jotform.com/261725016620045

Multiple-choice daily checkpoint per the Template's Daily Checkpoint spec. 13 single-answer questions, ungraded, optional, no name/email field. Easy for a student who followed the day, hard otherwise. Grounded in `dt-presentation.md` (Deck I) and `sources/Decision theory day.docx`.

Intro shown on the form: "A short checkpoint on today's Decision Theory material. The questions are easy if you followed the day and hard otherwise, so they work as a quick self-check on your understanding (and as a light attendance check). You do not need to submit it, and it will not be graded. Answer from memory. Exactly one option per question is correct."

Correct answer in **bold**; options listed in the same order as the form. Source pointer after each.

**Q1.** For a dualistic agent, optimization is just pick the action that maximizes expected utility. Why is this harder for an embedded agent?
- (a) Embedded agents have no utility function.
- **(b) For an embedded agent the action is just another fact about the world, so what would happen if I acted differently is not given and counterfactuals must be constructed.**
- (c) Embedded agents cannot compute expected values.
- (d) Embedded agents always have more actions to choose from.
- Source: slide "The hard case: embedded agents".

**Q2.** EDT and CDT differ in how they treat the agent's action. Which description is correct?
- **(a) EDT conditions on the action (treats it as evidence); CDT intervenes on it (the do-operator).**
- (b) EDT intervenes on the action; CDT conditions on it.
- (c) Both condition on the action; they differ only in the prior.
- (d) Both intervene on the action; they differ only in the utility function.
- Source: slides "Evidential decision theory" and "Causal decision theory".

**Q3.** In a Bayesian network, the intervention do(X=x) differs from observing X=x because it...
- (a) adds new arrows pointing out of X.
- (b) conditions on all of X's descendants.
- **(c) severs the arrows into X (cutting it off from its causes) and then sets X equal to x.**
- (d) is just another name for conditioning on X equals x.
- Source: slide "Causal decision theory: seeing vs. doing".

**Q4.** On Newcomb's problem, how do the two rules come apart?
- (a) CDT one-boxes; EDT two-boxes.
- **(b) CDT two-boxes; EDT one-boxes.**
- (c) Both one-box.
- (d) Both two-box.
- Source: slide "Newcomb's problem: CDT two-boxes, EDT one-boxes".

**Q5.** The smoking lesion is the case that tells against EDT. Why does EDT give the intuitively wrong verdict (abstain)?
- (a) Because smoking directly causes the lesion.
- (b) Because the lesion has no effect on anything in the problem.
- **(c) Because conditioning on smoking raises the probability of the lesion, even though smoking is only correlated with (a symptom of) it rather than a cause of cancer; EDT mistakes that evidence for control.**
- (d) Because EDT cannot represent the problem at all.
- Source: slide "EDT mistakes evidence for control".

**Q6.** In the sequential-prediction framing, which identification does the deck make?
- (a) CDT is the joint predictor over action-and-percept streams; EDT is the chronological semimeasure.
- **(b) CDT is the chronological semimeasure (the action sits to the right of the double-bar, as an intervention); EDT is the joint predictor that conditions on the action.**
- (c) Both CDT and EDT correspond to the same predictor.
- (d) Neither can be written as a predictor.
- Source: slides "Chronological semimeasure = CDT" and "Joint prediction = EDT".

**Q7.** Functional decision theory reframes what you are choosing. On FDT, you are choosing...
- (a) the action directly, severed from its causes.
- (b) a prior over which environment you are in.
- (c) the policy of a strictly weaker successor agent.
- **(d) the output of the fixed decision function you run, scored by the world in which the function gives that output (so predictors, copies, and simulations of it move together).**
- Source: slide "Functional decision theory: choose your function's output".

**Q8.** In the twin prisoner's dilemma (two copies of one decision procedure), how do CDT and FDT differ, and why?
- (a) CDT cooperates and FDT defects, because of a causal link between the twins.
- (b) Both cooperate, for the same reason.
- **(c) CDT has both twins defect; FDT has both cooperate, because the twins' actions share a subjunctive (logical) dependence on the same function that CDT ignores.**
- (d) FDT defects because the twins are physically connected.
- Source: slide "Twin Prisoner's Dilemma & subjunctive dependence".

**Q9.** In counterfactual mugging, why does a UDT agent pay in the branch where it receives nothing?
- (a) Because it is unsure whether it actually lost the coin flip.
- **(b) Because the paying policy has higher ex-ante expected value (before seeing the coin), and UDT optimizes the policy it would have committed to rather than updating on the observed branch.**
- (c) Because paying causally increases its own reward.
- (d) Because Löb's theorem forces it to pay.
- Source: slide "Counterfactual mugging: the updateless move". ((a) is the updatelessness-is-not-ignorance trap.)

**Q10.** What does UDT 1.1 add over UDT 1.0?
- (a) It updates on its observations before acting.
- **(b) It optimizes over the whole policy (a map from observations to actions) instead of one action at a time, so outputs in different branches can be coordinated.**
- (c) It throws away the prior.
- (d) It replaces logical reasoning with causal intervention.
- Source: slide "UDT 1.1: optimise the whole policy, not one action".

**Q11.** A central worry about UDT is that it can pay for worlds that don't exist. What is the concern?
- **(a) Because it optimizes ex-ante expected utility under the prior, a mistaken prior can make it burn real utility in the actual branch for the sake of branches that never occur.**
- (b) UDT is uncomputable.
- (c) UDT always defects in games.
- (d) UDT ignores the prior completely.
- Source: slide "Problem 1: paying for worlds that don't exist".

**Q12.** In the 5-and-10 problem, a proof-searching agent that should obviously take the 10 dollars can end up taking the 5 dollars. What goes wrong?
- (a) The agent miscalculates that 10 is greater than 5.
- (b) The world's source code is hidden from the agent.
- (c) The agent is not permitted to output 10.
- **(d) A spurious self-referential proof: via Löb's theorem the agent proves something like if A returns 5 then utility is 5, and if A returns 10 then utility is 0, so its search certifies the 5 dollars; counterfactuals over one's own action break down.**
- Source: slide "The 5-and-10 problem"; `agency-solutions` Exercise 1/2 (Löb).

**Q13.** Toward a formal optimality criterion, decision problems are written as programs (a world that calls the agent). A problem counts as fair when...
- (a) the world hands out rewards at random.
- (b) the agent and the world are guaranteed to share the same prior.
- **(c) the world depends only on the agent's input/output behaviour, not on its internal source code beyond that behaviour.**
- (d) the world is forbidden from ever simulating the agent.
- Source: slide "Fairness".
