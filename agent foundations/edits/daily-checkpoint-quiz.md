# Agent Foundations: Daily Checkpoint (quiz answer key)

Live form (Jotform): https://form.jotform.com/261724721333048

Multiple-choice daily checkpoint per the Template's Daily Checkpoint spec. 13 single-answer questions, ungraded, optional, no name/email field. Easy for a student who followed the day, hard otherwise. Grounded in `agency-presentation.md` and `sources/Agent foundations doc.docx`.

Intro shown on the form: "A short checkpoint on today's Agent Foundations material. The questions are easy if you followed the day and hard otherwise, so they work as a quick self-check on your understanding (and as a light attendance check). You do not need to submit it, and it will not be graded. Answer from memory. Exactly one option per question is correct."

Correct answer in **bold**; options listed in the same order as the form. Source pointer after each.

**Q1.** Agent foundations tries to reason about highly capable agents in advance, rather than only studying them empirically. What is the main reason given for this?
- (a) Theory can predict the exact actions a superintelligence will take.
- **(b) At a sufficiently dangerous capability level we may have to get key safety properties right on the first critical try, with no room for trial and error.**
- (c) Empirical study of AI is always cheaper than building theory.
- (d) Highly capable agents are mathematically simpler than weak ones.
- Source: slide "Why Agent Foundations?" ((a) is the Vingean-uncertainty trap.)

**Q2.** A safety property is reflectively stable when it...
- (a) can be verified by testing the agent on many inputs.
- (b) holds for every possible agent architecture.
- **(c) stays invariant under the agent's own self-modifications (rewriting its code, building a successor, revising its world model).**
- (d) was proved using a consistent formal system.
- Source: slide "Reflective Stability".

**Q3.** Coherence theorems (money-pump / Dutch book) are described as almost vacuous as stated. Why?
- **(a) Any system at all can be cast as maximizing some utility function (even a rock on the floor), so the frame makes no predictions until you specify what the agent is coherent over.**
- (b) They have been mathematically disproven.
- (c) They apply only to agents that store a utility function internally.
- (d) They require the agent to be logically omniscient.
- Source: slide "Reasoning About Ideal Intelligence".

**Q4.** The complete class theorem sharpens coherence arguments. What does it say about a decision rule that is not dominated (Pareto-optimal across all environments)?
- (a) It must be implemented with an explicit utility function inside the agent.
- (b) It must randomize between actions.
- (c) It is automatically reflectively unstable.
- **(d) It can be represented as Bayes-optimal expected-utility maximization under some prior with full support.**
- Source: `Agent foundations doc.docx` (Consequentialist Foundations); `agency-solutions` Exercise 3. ((a) is the representational-not-mechanistic trap.)

**Q5.** Why does the day argue that accumulating resources like energy, money, or compute is favored almost regardless of an agent's terminal goal (instrumental convergence)?
- (a) Because all sufficiently capable agents share the same terminal goal.
- **(b) Because such resources are useful across a wide range of goals and buy more optionality (a wider set of reachable future states).**
- (c) Because resources are physically conserved.
- (d) Because terminal goals are inherently unstable.
- Source: slide "Why care about resources?".

**Q6.** In the contrast between Alexei (dualistic) and Emmy (embedded), which feature is characteristic of the embedded agent Emmy?
- (a) She has clean input/output channels separating her from the environment.
- (b) She is larger than the environment and can hold a full copy of it in her head.
- **(c) The environment contains her and is bigger than she is, with no crisp agent/environment boundary.**
- (d) She never has to reason about herself.
- Source: slides "Dualistic agents" and "Embedded agents". ((a), (b), (d) describe the dualistic picture.)

**Q7.** A1 wants to build a more capable successor A0. Why can't A1 just simulate A0 step by step to confirm it is safe (Vingean uncertainty)?
- (a) Because simulation is forbidden by Löb's theorem.
- **(b) Because more capable means A0 predicts or acts better, so if A1 could foresee A0's exact moves it would already be that capable.**
- (c) Because A0's source code is hidden from A1.
- (d) Because simulating A0 would violate the second law of thermodynamics.
- Source: slide "Self-Modification and Vingean Reflection".

**Q8.** If A1 and A0 share the same proof system L, self-trust becomes L proving whatever I can prove is true (for all phi, Box phi implies phi). Why is this fatal for a consistent L?
- (a) Because the statement Box phi cannot be expressed inside L.
- (b) Because consistent systems cannot reason about programs at all.
- **(c) By Löb's theorem, if L proves (Box C implies C) then L proves C; applied to a falsehood such as 2+2=5 it would force L to prove 2+2=5.**
- (d) Because the proof-search program never halts.
- Source: slide "The Löbian Obstacle".

**Q9.** A proposed workaround is for each agent to trust only a successor that uses a strictly weaker proof system. Why does this fail to give indefinite self-improvement?
- (a) Because weaker proof systems are inconsistent.
- (b) Because a stronger system can never trust a weaker one.
- (c) Because all the successors would end up identical.
- **(d) Because each successor must drop to a weaker system, so logical strength shortens at every step (a telomere) until the chain runs out of trust.**
- Source: slide "The Löbian Obstacle" (consequence for tiling agents). ((b) inverts the actual direction of trust.)

**Q10.** Which of the following is an example of logical (as opposed to empirical) uncertainty?
- (a) Whether it will rain in your city tomorrow.
- **(b) Whether the millionth digit of pi is a 7.**
- (c) Which country a stranger you just met grew up in.
- (d) Whether a fair coin you are about to flip will land heads.
- Source: slide "Embedded Subproblem: Logical Uncertainty".

**Q11.** The logical induction criterion (Garrabrant et al.) weakens the classical Dutch-book condition to which requirement?
- (a) The market must price every sentence at exactly one half.
- (b) No trader whatsoever can profit from the market.
- **(c) No efficient (polynomial-time) trader can make unbounded profit against the market.**
- (d) The market may price only sentences that have already been proved.
- Source: slide "Aside: Logical Induction". ((b) is the classical condition it weakens from.)

**Q12.** Optimization is framed as steering the world into a narrow target (local entropy reduction). By the Touchette and Lloyd bound, the extra entropy reduction a sighted agent achieves beyond a blind baseline is paid for by...
- **(a) the mutual information between the agent's observations and its actions.**
- (b) the agent's total energy budget.
- (c) the Kolmogorov complexity of the agent's source code.
- (d) the number of actions available to the agent.
- Source: slide "Optimization and Thermodynamics" (Touchette and Lloyd); `agency-solutions` Exercise 4.

**Q13.** How does descriptive agent foundations differ from the normative approach?
- (a) It derives, from first principles, how an ideally rational agent should reason.
- **(b) It asks what agents actually arising in the world look like, working bottom-up from properties of the world such as modularity, selection pressure, and resource constraints.**
- (c) It studies only superintelligences.
- (d) It avoids using mathematics.
- Source: slide "Descriptive Agent Foundations". ((a) describes the normative approach.)
