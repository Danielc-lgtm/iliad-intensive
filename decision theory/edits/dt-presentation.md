# Decision Theory Presentation

(Title page only -- content to be added.)

Title: **Decision Theory**
Author: Daniel C
Date: (placeholder)





Rough sketch (cover all following points, reverse engineer what I meant, heavily search online to gather full background context, write it in a way for maximal self-containedness, extreme clarity, and well motivated motivations)



Motivation for decision theory:

- Modelling and reason about how superintelligent agents will behave even if we don't understand details of its architectures

- Implementation: Guide implementation for how to make decisions in an optimal way (Problem decomposition: Figure out a specification of a goal that we want to optimize, then optimize for it correctly. Decision theory is about the second part, without the second part the specification would not be sufficient for alignment, as the AI might optimize it in a wrong way)

- Reflective stability: We want to study safety properties that are reflective stable (because we need safety properties to remain invariant under self-modification, check agency presentation slides), decision theory is a natural, simple setting to study these questions (Would an agent with decision theory A want to "self-modify" to decision theory B, or construct a successor with decision theory B)

- Multi-agent dynamics: Decision theory problems often get tricky when it involves strategic interactions/mutual modelling between different agents.  We want to find the sort of decision theory so that we can design agents that can successfully cooperate with other superintelligent agents and avoid conflict outcomes, without being exploitable



Why is decision theory hard:

- Base this part on the decision theory slides in sources, the bit about how decision theory in dualistic case is easy, but embedded is hard because you have to construct counterfactuals. But improve this for more well-motivatedness and clarity

- For "dualistic case is easy" part, explain and link that the "dualistic case" is basically the existing framework on EU maximization, complete class theorems etc, which have good applications in economics/RL. But we want a theory that works 

Causal decision theory

- Also follow the decision theory slides. But with the following improvements: More self contained introduction to bayesian networks and interventions. Afterwards mention that internvention is contradictory with embeddedness or physics (sever connection with upstream variables). In particular, heavily read and incorporate the arrow_of_time_presentation from agent foundations/sources to explain the conflict between causal decision theory and physics

- Make good diagrams

Evidential decision theory:

- Formally define evidential decision theory as conditioning

- Explain the problem of spurious counterfactuals, use "Decision_Theory_CDT_to_UDT_1_1 (1)" from sources as inspiration



Functional decision theory and the updateless decision theory:

- For this,  combine the structure between the decision theory slides and Decision_Theory_CDT_to_UDT_1_1 (1). Make use of paradoxes. For UDT make sure you emphasize the aspects that are emphasized in the decision theory slides

- For UDT make sure that you make diagrams that emphasize the idea of different branches of possibility that correspond to different observations, and you want to "coordinate" across all those different branches. Doing a kind of "global optimization" instead of "local optimization"

(In general, just augment the slides with the decision_theory_cdt_to_udt doc in an appropriate way)



Problems with updateless decision theory:

- UDT would sacrifice utility in the actual world in exchange for utility in hypothetical worlds that doesn't exist (do a deep search to understand what I mean, explain in a clarifying way)

- Logical updatelessness (search online to understand what it is)





5 and 10 problem

- Explain the 5 and 10 problem in an extremely clarifying but self-contained way, emphasize the problem of logical counterfactuals: The agent has access to its own source code and can prove things about its own source code, so it can prove things about its own actions, so it does not have a well defined notion of "what would happen if I had taken a different action"

- Link back to embedded agency: The agent's action is just another fact about the world

- Have a self-contained introduction to Lob's theorem as well

- [Embedded Agency (full-text version) — LessWrong](https://www.lesswrong.com/s/Rm6oQRJJmhGCcLvxh/p/i3BTagvt3HbPMx6PN)





Formalization of decision theory problem:

- A framework on formalizing and judging decision theory. (Use moderate formalism to make this more precise), use diagrams appropriately

- Both agents and the world are represented as programs, with the following properties:
  
  - Agent has access to the world's source code as well as its own source code, returns an action
  
  - The world can make function calls on the agent (where we think of agent as a function from some input -> Action) and can search for proofs about the agent's input output behavior, return a utility
  
  - Fairness (search for what fairness means in decision theory): We don't feed the agent's source code to the world directly because we don't want worlds that are "unfair" in the sense of "if the agent's source code is written in python, then punish the agent". The agent should only be judged on its input output behavior

- We would like to design an agent that performs well (the optimal mapping to actions such that utility (returned by the world) is high for almost all worlds)

- What the agent has to account for:
  
  - Coordinate across different function calls: If the world does multiple function calls on the agent (basically testing "what would the agent do in some counterfactual situation?"), then the agent has to discover that, and make sure that the counterfactual behavior is "coordinated" to ensure optimal utility
  
  - Subjunctive dependence: Suppose that the world calls a subroutine A where the subroutine A is isomorphic to the agent itself (e.g. same algorithm with a different implementaiton). Per functional decision theory the agent should treat its own action as if it is also controlling the output of subroutine A (since subroutine is essentially a copy). So the agent has to discover that the world ccontains something which is isomorphic to itself
  
  - Here is a description I wrote, use it to improve motivation: Many of the central puzzles in decision theory — Newcomb's problem, counterfactual mugging, the five-and-ten problem, open-source game theory — share a common structure: the agent and the environment are both programs that may inspect each other's source code, simulate each other's input-output behaviour, or contain subroutines that are algorithmically isomorphic to one another. Yet these problems are typically presented as standalone thought experiments, and the existing decision theories (CDT, EDT, FDT, UDT) are evaluated by checking their prescriptions case by case rather than against a unified optimality criterion over a well-defined problem class. The substantive question is whether one can formalise a class of computational environments rich enough to encompass all of these problems simultaneously, together with a criterion of optimality against which any candidate decision theory can be measured. The formalism would need to capture at least three features: fairness (the environment's payoffs depend only on the agent's policy or input-output behaviour, not on implementation details unrelated to its outputs), counterfactual querying (the environment may call the agent as a subroutine under different observations to determine its counterfactual actions, so the agent must coordinate across these calls), and subjunctive dependence (the environment may contain a subroutine whose algorithm is isomorphic to the agent's own, so the agent must recognise this and treat its decision as controlling the subroutine's output as well). A concrete starting point would be to define such a problem class, prove that the known decision theories differ in their performance on it, and determine whether any of them (or a modification) is optimal across all fair problems in the class.
