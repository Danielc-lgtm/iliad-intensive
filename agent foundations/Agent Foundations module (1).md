# Table of Contents

# Contributors

Daniel C wrote and taught the module. Satya Benson (Williams College) contributed to the content. The pre-reading topics, fundamental readings, exercises, lecture slides, and daily-checkpoint form are linked in the Content section below.

# Learning outcomes

**(What.)** By the end of the day, students can explain *embedded agency*: why an agent built into the world it acts on (made of the same stuff, smaller than its environment, with no clean input/output boundary, able to model and modify itself) breaks the standard dualistic picture. For each of the day’s core research directions (called 'strands') they can state the central problem and a plain-language description of a main result: the complete class theorem (consequentialist foundations), Löb’s theorem and the tiling obstacle (self-modification), the logical-induction criterion (logical uncertainty), optimization as local entropy reduction (optimization and thermodynamics), and selection theorems (descriptive agent foundations). They can describe at last one strand in mathematical detail. They can explain how each strand is an offshoot of the central threads *reflective stability* and *embedded agency*.

**(Why.)** Aligning a superintelligence is a problem we may have to get right on the first critical try, reasoning about a system more capable than anything we have observed, before it exists. That rules out pure trial and error and demands concepts that stay meaningful under extreme optimization pressure and self-modification. Agent foundations supplies (or tries to supply) those concepts, and this day gives students a map of some main research directions and how they fit together.

**(How.)** Each student goes deep on one pre-reading track beforehand. A one-hour morning lecture lays out the main threads (reflective stability and embedded agency) and previews every strand. Students then read the shared fundamental readings and, in small groups mixing different tracks, run *cross-pollination* discussions that connect their topics to embedded agency. The afternoon makes a few results rigorous through exercises.

# Prerequisites

- Comfort with elementary discrete probability (random variables, expectation, conditional probability).
- Basic formal logic (provability, quantifiers) and basic computability (programs, halting); needed for the Löb and logical-induction strands.
- Basic information theory (entropy, mutual information); needed for the optimization strand.
- No prior agent-foundations background is assumed; every term used on the day is introduced on the day or in the readings. An introductory overview of the AI alignment problem (as in the intro-alignment module) is helpful context but not required.
- Provided refresher notes cover the gaps: a *probability theory* refresher, a *formal logic* refresher, a *computability theory* refresher, and an *information theory, causality, and statistical mechanics* refresher. Point students at the one matching their weakest area before the day.

# Content

Slides: [Agent Foundations lecture slides](https://drive.google.com/file/d/11q6mvNEbDKecZHnLDBq3nEhZWJazWX8i/view?usp=sharing). Exercise sheet: [Agency exercises](https://drive.google.com/file/d/1D5rEEO0n1u6_7h-Pnkz-ccCcuhPusIwe/view?usp=sharing) (worked solutions available to instructors).

## Fast-track

To get the core in about an hour, or to catch up after missing the day:

- Read the “Morning lecture” summary below for the unifying spine (reflective stability, embedded agency, the modelling-vs-implementation split).
- Read [Embedded agency](https://www.lesswrong.com/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version) up to and including section 3.3, then section 4.1, and [Why agent foundations](https://www.lesswrong.com/posts/FWvzwCDRgcjb9sigb/why-agent-foundations-an-overly-abstract-explanation) in full.
- Pick the one strand closest to your background from “The five strands” below and read its first (most conceptual) listed reading.
- Skim the takeaways at the end of each strand summary.

## Main content

Agent foundations is not one theory but several research strands (research directions), each attacking a different facet of the same problem: how to reason about, and build, *stable* agents that are *embedded* in the world they act on. This day is organized around five such strands (consequentialist foundations; Löb’s theorem and tiling agents; logical induction; optimization and thermodynamics; descriptive agent foundations). Each student pre-reads one strand in depth before the day; the morning lecture supplies the spine that connects them; the shared fundamental readings and a small-group discussion knit them into a single picture; and an exercise session makes a few of the results rigorous.

Read top to bottom, this section runs: the unifying threads (the morning lecture), then the fundamental readings that give a bird’s-eye view, then the five strands each with its readings, then the cross-pollination discussion, the exercises, and a self-check.

### Morning lecture

*Intent: give students the through-line (the unifying spine) that ties the five pre-reading tracks together, so the rest of the day reads as one picture rather than five disconnected topics. A teacher short on time should prioritise the embedded-agency and reflective-stability framing before any individual strand preview.*

- **Why agent foundations.** We may need key safety properties to hold on the first critical try, for an agent far more capable than any we can study directly. Agent foundations looks for the properties capable agents share *in general*, so we can reason about them in advance.
- **Reflective stability.** A safety property only matters if it survives the agent’s own self-modification: a capable agent may rewrite its code, build a more capable successor, or revise its world model. A property is *reflectively stable* if it is invariant under all of these. Working assumption: under enough optimization pressure, a property persists only if there is some reason it must. Reflective stability is the thread running through every strand.
- **Robust concepts (“true names”).** Goodhart’s law says a proxy that becomes a target stops measuring what we want. So a theory of agency must be built from concepts that do not break under optimization, the “true names” of optimization, goals, world models, and embeddedness.
- **Two pathways of impact (following C. Wyeth).** *Modelling*: build an abstract mathematical model of an idealised capable agent and use it to show why a given alignment proposal would fail. *Implementation*: develop a theory far enough to build and inspect an actual system, often favouring a modular architecture (a separate, inspectable world model, planner, and goal) so each part can be checked.
- **Dualistic vs embedded agents.** The standard picture (an agent with clean I/O, “larger than” and “outside” its environment, holding a full world model in its head) is dualistic. A real agent is *embedded*: part of the world, made of the same pieces, smaller than its environment, with no crisp boundary, and able to be copied, modified, or to model itself. Embeddedness is what makes self-improvement, multi-agent reasoning about copies, and self-reference unavoidable, and it is what the rest of the day is about.

### Fundamental reading

*Intent: a shared bird’s-eye view that ties the five tracks to embedded agency, so the mixed-group discussion has common ground. Everyone reads these on the day (skimming beforehand is fine).*

- [Embedded agency](https://www.lesswrong.com/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version): read up to and including section 3.3, then section 4.1. The canonical statement of the embedded-agency problem cluster (the Alexei/Emmy framing the lecture uses).
- [Why agent foundations](https://www.lesswrong.com/posts/FWvzwCDRgcjb9sigb/why-agent-foundations-an-overly-abstract-explanation): read entirely. Why this abstract, theory-first approach is worth pursuing.
- [Reflectively consistent degree of freedom](https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom): read entirely. The precise notion behind a property an agent would not self-modify away, which is the day’s recurring theme of reflective stability.
- [General purpose search](https://www.lesswrong.com/posts/6mysMAqvo9giHC4iX/what-s-general-purpose-search-and-why-might-we-expect-to-see): read entirely. Why a capable mind plausibly contains a retargetable search process.

### The five strands (pre-reading tracks)

*The five strands are different facets of one problem, embedded agency; each student pre-reads one. Every summary below is self-contained at the conceptual level and ends with that strand’s readings (start with the first listed, which is the most conceptual). The morning lecture previews all five; the cross-pollination discussion connects them.*

**1. Consequentialist foundations.** If an agent’s preferences are cyclic, an adversary can money-pump it through trades that each look acceptable but leave it strictly worse off. So any agent that reliably avoids such dominated strategies behaves *as if* it maximizes a utility function. The **complete class theorem** sharpens this: any decision rule that is not dominated (Pareto-optimal across environments) is Bayes-optimal under some prior with full support. This is *representational*, not mechanistic: it says a capable, non-self-defeating agent looks like a Bayesian expected-utility maximizer from the outside, without saying it has a utility function inside, and without telling us *which* utility function (the hard part). *Takeaway: coherence gives a reflectively-stable target (a dominated strategy is one a rational agent would self-modify away from), but it under-determines the agent’s actual goals.* *Readings:* [Coherent decisions imply consistent utilities](https://www.lesswrong.com/s/SgomvxZ3cJWy2SBCu/p/RQpNHSiWaXTvDxt6R) (Introduction; “Why not circular preferences?”; “Probabilities and expected utilities” through “Conditional probability”; Conclusion); [The measuring stick of utility](https://www.lesswrong.com/posts/73pTioGZKNcfQmvGF/the-measuring-stick-of-utility-problem); [Complete class: consequentialist foundations](https://www.lesswrong.com/posts/sZuw6SGfmZHvcAAEP/complete-class-consequentialist-foundations).

**2. Löb’s theorem and tiling agents.** A capable agent may build a successor more capable than itself. By *Vingean reflection*, it cannot verify the successor by simulating it (if it could predict the successor’s exact moves, it would be that capable already), so it must reason abstractly about the successor’s *design*. The natural strategy (“trust the successor because it only takes actions it has proved safe”) needs the parent to trust the successor’s proofs. **Löb’s theorem** blocks this: if a consistent system `L` can prove “if `L` proves `C` then `C`”, then `L` already proves `C`. A consistent system cannot vouch for its own proofs in the abstract, only for a strictly weaker system’s. So a naive chain of self-improvements uses an ever-weaker proof system (a “telomere” of logical strength that runs out), the *finite descent problem*. The tiling-agents programme studies whether this obstacle can be overcome. *Takeaway: self-trust under self-modification is not free; it runs straight into a logical wall.* *Readings:* [Introduction to Löb’s theorem](https://intelligence.org/files/lob-notes-IAFF.pdf) (up to and including section 3); [Vingean reflection](https://www.lesswrong.com/w/vingean-reflection); [Walkthrough of the tiling agents paper](https://www.lesswrong.com/posts/QGrX3qK3qxQYK9D4C/walkthrough-of-the-tiling-agents-for-self-modifying-ai-paper) (start through “Finite Descent Problem”, then “What self-modifying agents need”).

**3. Logical induction.** Standard Bayesian reasoning assumes *logical omniscience*: the agent instantly knows all consequences of its beliefs. A bounded agent cannot (it may know a program’s source yet not its output, or the axioms yet not whether a number is prime). **Logical induction** (Garrabrant et al.) handles this by picturing a market that prices logical sentences in \[0,1\]; the *logical-induction criterion* requires only that no efficient (polynomial-time) trader can exploit the market for unbounded profit, a computable weakening of the Dutch-book argument. That single condition yields convergence and coherence in the limit, timely learning of statistical patterns (it prices “the nth digit of pi is 7” near 1/10 without computing it), and *self-trust* (current credence equals a weighted average of expected future credences). *Takeaway: a principled model of how a bounded agent should hold probabilities over facts it has not yet computed.* *Readings:* [An intuitive guide to Garrabrant induction](https://www.lesswrong.com/posts/y5GftLezdozEHdXkL/an-intuitive-guide-to-garrabrant-induction); [Logical induction](https://arxiv.org/pdf/1609.03543) (chapters 1 and 3; skim chapter 4).

**4. Optimization and thermodynamics.** A powerful agent reliably steers the world into a narrow region of outcomes, ones extremely unlikely under any random process. This is *local entropy reduction*: concentrating probability mass from a broad initial distribution onto a narrow target. Even a pure predictor has an objective reason to attend to optimizers: naming what an optimizer steers toward predicts the outcome cheaply and robustly, where modelling the initial conditions would be expensive and chaos-fragile. Steering is bounded by information: the **Touchette-Lloyd** inequality says the entropy reduction a sighted agent achieves over a blind baseline is at most the mutual information between its observations and actions ($`\Delta H \leq \Delta H_{\text{blind}}^{\max} + I(X;A)`$). *Algorithmic thermodynamics* (Ebtekar and Hutter) replaces ensemble entropy with Kolmogorov complexity, giving laws for individual states and making an embedded agent’s knowledge an endogenous physical quantity (algorithmic mutual information between memory and environment), which is exactly its budget for optimization. *Takeaway: optimization is physically constrained, and “knowing more” formally means “being able to optimize more.”* *Readings:* the self-contained note [Optimization and thermodynamics](https://drive.google.com/file/d/1uJ3a_mVCDdCI1-kW5Ha2PyZ5otTtu-dO/view?usp=sharing) (read entirely; appendix optional) is the primary reading; its underlying sources are [The ground of optimization](https://www.lesswrong.com/posts/znfkdCoHMANwqc2WE/the-ground-of-optimization-1) (up to and including “Relationship to Garrabrant and Demski’s Embedded Agency”), [Generalized heat engine](https://www.lesswrong.com/posts/uKWXktrR7KpbgZAs4/generalized-heat-engine), and [Algorithmic thermodynamics and three types of optimization](https://www.lesswrong.com/posts/CJRxQiTKEzior7jGq/algorithmic-thermodynamics-and-three-types-of-optimization).

**5. Descriptive agent foundations.** *Normative* agent foundations asks what an ideal agent should look like; *descriptive* asks what agents actually arising in the world (bacteria, neural networks, future AI) look like, and aims to read off their goals, world model, and decision structure from the outside. It works bottom-up from properties of the world (modularity, selection pressures, computational limits). **Selection theorems** aim to prove results of the form “any system selected to achieve goal G in environment E must contain structure approximately isomorphic to X”, giving mechanistic rather than merely representational accounts of agency. A key example: the world’s *modularity* (it decomposes into sparsely-interacting subsystems) is what makes both world-modelling (Bayesian networks propagate updates locally) and planning (general-purpose search can pursue decoupled subgoals) tractable. *Takeaway: the complementary direction to coherence: not “non-dominated agents can be described as maximizers” but “what pressures make agent-like structure actually arise.”* *Readings:* [Selection theorems: a program for understanding agents](https://www.lesswrong.com/posts/G2Lne2Fi7Qra5Lbuf/selection-theorems-a-program-for-understanding-agents); [How we picture Bayesian agents](https://www.lesswrong.com/posts/TiBsZ9beNqDHEvXt4/how-we-picture-bayesian-agents); [What selection theorems do we expect/want](https://www.lesswrong.com/posts/RuDD3aQWLDSb4eTXP/what-selection-theorems-do-we-expect-want).

### Cross-pollination discussion

*Intent: each student knows one strand deeply; the discussion makes them build the connections between strands, which is where the unified picture of embedded agency actually lives. Groups mix tracks so no one can answer alone.*

On the day, students who pre-read different strands meet in small mixed groups and work to connect their topics into one picture of embedded agency: how a logical inductor’s trust in its future self relates to a tiling agent’s trust in its successor, how the coherence account of goals relates to the thermodynamic one, how the representational view of agency (coherence) relates to the mechanistic one (selection theorems). The specific discussion prompts used are listed in the teaching guide.

### Exercise session

*Intent: turn a few of the day’s headline results from slogans into things students have actually proved. Problems are self-contained and build through lemmas to a main theorem. Suggest students start with the exercise matching their pre-reading track, then branch out; pairs or small groups work well.*

Five exercises (full statements in the [exercise sheet](https://drive.google.com/file/d/1D5rEEO0n1u6_7h-Pnkz-ccCcuhPusIwe/view?usp=sharing); worked solutions available to instructors), grouped by topic:

*Logical uncertainty and self-reference.*

- **Exercise 1: Gödel’s second incompleteness theorem** (difficulty 4/5, importance 4/5). Via a self-referential program: a Gödel sentence is true, a consistent system cannot prove its own consistency, and this is exactly the Löbian obstacle to self-trust. Parts (a) true Gödel sentence, (b) no self-consistency proof, (c) the obstacle.
- **Exercise 2: Löb’s theorem** (difficulty 3/5, importance 5/5). The three provability properties (necessitation, distribution, the Löb condition), a full proof of the theorem, and an application: FairBot programs cooperate by Löb’s theorem. Parts (a-b) properties, (c-d) the proof, (e) FairBot.

*Coherence and consequentialism.*

- **Exercise 3: The complete class theorem** (difficulty 3/5, importance 5/5). The equivalence between non-dominated strategies and Bayesian expected-utility maximization, via a geometric argument over the convex set of attainable reward vectors. Parts (a) admissibility, (b) faces and difference vectors, (c) constructing the rationalizing prior.

*Descriptive agent foundations.*

- **Exercise 4: The do-divergence theorem** (difficulty 2/5, importance 4/5). Formalizes optimization as outcome concentration and proves that how far an agent can steer outcomes (a KL divergence from the unsteered baseline) is bounded by the mutual information between its observations and actions. The single-step backbone of the Touchette-Lloyd picture.
- **Exercise 5: Channel additivity** (difficulty 3/5, importance 3/5). Optimal input distributions over independent channels: mutual information decomposes across channels, independence improves throughput, and an optimal policy need not coordinate across a modular environment (connecting modularity to tractable optimization).

### Daily checkpoint

*Intent: a quick understanding-and-attendance check, easy for someone who followed the day and hard otherwise. Align answers with the learning outcomes.*

The live form used on the day: <https://form.jotform.com/261724721333048>. The questions below are a self-contained version; answers at the end of this section.

1.  What does it mean for a safety property to be *reflectively stable*? (a) It holds on the training distribution. (b) It is invariant under the agent’s self-modification and successor-building. (c) It can be expressed in formal logic. (d) It maximizes expected utility.
2.  The complete class theorem tells us that a non-dominated agent: (a) has an explicit utility function in its code; (b) can be *described* as maximizing expected utility under some prior; (c) is conscious; (d) must use causal decision theory.
3.  Why can’t a consistent agent simply trust its own proofs “in the abstract” to license self-modification? (a) Proofs are too slow. (b) Löb’s theorem: provable self-trust collapses into proving everything. (c) It lacks enough memory. (d) Gödel sentences are false.
4.  The logical-induction criterion requires that: (a) no trader at all can exploit the market; (b) no *efficiently computable* trader can exploit the market for unbounded profit; (c) prices equal frequencies; (d) the agent is logically omniscient.
5.  “Optimization is local entropy reduction” plus Touchette-Lloyd implies: (a) entropy never decreases anywhere; (b) steering beyond a blind baseline is bounded by the agent’s mutual information with what it steers; (c) optimization is impossible; (d) entropy is subjective.
6.  Selection theorems aim to show that: (a) any non-dominated strategy can be described as EU maximization; (b) systems selected to achieve a goal in an environment must contain certain agent-like structure; (c) evolution is optimal; (d) all agents are Bayesian.

*Answers: 1(b), 2(b), 3(b), 4(b), 5(b), 6(b).*

## Learn more

The readings for each strand are linked under that strand in the Main content above. Beyond them:

**Algorithmic thermodynamics (Ebtekar).** [Foundations of algorithmic thermodynamics](https://arxiv.org/abs/2308.06927); [Modelling the arrows of time with causal multibaker maps](https://www.mdpi.com/1099-4300/26/9/776); [Long-time derivation of the Boltzmann equation from hard-sphere dynamics](https://arxiv.org/abs/2408.07818).

**Embedded and universal AI (Wyeth).** [Limit-computable grains of truth](https://arxiv.org/pdf/2508.16245); [Embeddedness failures in universal artificial intelligence](https://arxiv.org/pdf/2505.17882); [Value under ignorance](https://arxiv.org/pdf/2512.17086).

**Other directions.** [Introduction to the infra-Bayesianism sequence](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence) (non-realizable environments); [The learning-theoretic agenda](https://www.lesswrong.com/posts/ZwshvqiqCvXPsZEct/the-learning-theoretic-agenda-status-2023); [Optimization at a distance](https://www.lesswrong.com/posts/d2n74bwham8motxyX/optimization-at-a-distance); the [hard problem of corrigibility](https://www.lesswrong.com/w/hard-problem-of-corrigibility) and a [critique of the corrigibility basin of attraction](https://www.lesswrong.com/posts/oLbpfPkdtcknABvvw/the-corrigibility-basin-of-attraction-is-a-misleading-gloss); the original [tiling agents draft](https://intelligence.org/files/TilingAgentsDraft.pdf); and background notes on [admissibility and the complete class theorem](https://www2.stat.duke.edu/~pdh10/Teaching/581/LectureNotes/admiss.pdf) and the [Dutch book argument](https://www.stat.berkeley.edu/~census/dutchdef.pdf).

**Research frontier.** The *agent structure problem* (whether strong optimization provably entails an internal world model), embedded variants of AIXI, and resource-theoretic accounts of instrumental convergence.

# Teaching guide

The day mixes a single framing lecture with self-directed reading, structured discussion, and exercises. Students should already have read their one chosen pre-reading track.

## Time schedule

- 10:00–11:00 Morning lecture (the unifying spine; preview each strand).
- 11:00–12:30 Fundamental reading (90 min; the four shared readings).
- 12:30–13:30 Lunch.
- 13:30–15:30 Cross-pollination discussion (120 min; mixed-track small groups).
- 15:30–15:45 Break.
- 15:45–17:45 Exercise session (120 min).
- 17:45–18:00 Daily checkpoint and feedback form.

(Reading plus discussion totals 3.5 hours; lecture 1 hour; exercises 2 hours. Adjust the reading/discussion split toward discussion if the room is engaged.)

## Required materials

- Projector and laptop for the slides.
- Printed (or linked) fundamental readings and the five pre-reading track sheets.
- Printed exercise sheets and the solutions set (for the teacher, and to hand out after).
- Whiteboard for the discussion block.
- One or more instructors/TAs to float between the cross-pollination discussion groups and seed stuck groups.
- The four prerequisite refresher notes, shared with students a few days ahead.

## Morning lecture

Walk the slides. Protect the spine over the strand previews: open with “first critical try” and reflective stability, establish the dualistic-vs-embedded contrast (the Alexei/Emmy framing), then preview the five strands as *facets of embedded agency* rather than as a list. **TN:** the previews only need to plant the question each strand answers; depth comes from the students’ own pre-reading and the discussion, so do not over-explain any one strand here. Leave 10 minutes for questions.

## Fundamental reading

Students read the four shared readings (skimming beforehand is encouraged). **TN:** tell students to read for *connections to their own track*, not for full coverage; the connections are the raw material for the discussion. Embedded agency is the anchor; the other three each sharpen one thread (why this approach, reflective stability, general-purpose search).

## Cross-pollination discussion

Form groups of 4-6 that deliberately mix pre-reading tracks (ideally one student per track per group). **TN:** the failure mode is a student who read a topic answering for everyone. Run it as: each member first explains their own track’s core idea to the group in two minutes, then the group works a cross-pollination prompt together. Let each group pick the prompts that span the tracks present; float between groups and seed a stuck group with one concrete sub-question (for example, “does a logical inductor’s self-trust give a tiling agent what it needs?”). Close with each group sharing one connection they found.

Suggested prompts (groups can go beyond them):

1.  **Logical induction × Löb’s theorem and tiling agents.** A logical inductor’s self-trust (current credence is a weighted average of expected future credences) versus the tiling agent’s need to trust a successor without inspecting its actions. How do the two notions of self-trust relate?
2.  **Consequentialist foundations × optimization and thermodynamics.** Coherence describes goal pursuit as expected-utility maximization; the thermodynamic picture describes it as moving uncertainty around to produce low-entropy outcomes. How do these two pictures of goal-directed behaviour relate? Can thermodynamics offer a “measuring stick of utility”?
3.  **Logical induction × consequentialist foundations.** The Dutch-book argument behind coherence presupposes logical omniscience (computing expected utilities needs the logical consequences of one’s beliefs). How does logical uncertainty interact with the foundations of coherence?
4.  **Optimization and thermodynamics × descriptive agent foundations.** Thermodynamics constrains what optimization is physically possible; selection theorems ask what agent type-signatures get selected for. What constraints might thermodynamics impose on the selection environment?
5.  **Consequentialist foundations × descriptive agent foundations.** The complete class theorem is representational (“can be described as a maximizer”); descriptive foundations is mechanistic (“what agents actually are, and what makes them arise”). How do the representational and mechanistic views relate?
6.  **Consequentialist foundations × logical induction.** Coherence assumes the agent can price any bet correctly; the logical-induction criterion is the “no efficient Dutch book” analogue. How does logical uncertainty reshape coherence arguments?

## Exercise session

Hand out the exercise sheet. **TN:** suggest students start with the exercise matching their pre-reading track (Löb/Gödel for the logic tracks, complete class for consequentialist foundations, do-divergence/channel additivity for optimization and descriptive), then move on; Exercises 2 and 3 are the highest-importance and best for a mixed room. The exercises build through lemmas, so a stuck student usually needs the previous part re-read, not the answer. Release solutions at the end. **TN, Exercise 2(e):** the FairBot part is the payoff (Löbian cooperation), and it directly seeds the Decision Theory day’s tournament; flag the connection.

## Daily checkpoint

Run the six-question checkpoint (above) as a quick individual quiz, then read out the answers. It doubles as an attendance check and tees up the feedback form.

# Notes for future iterations

- Notes about delivery:
    - Slides were too dense/heavy, with too much informtion in too small of a font
    - Morning lecture was too long and information-heavy
    - Needs more examples
    - Tie more directly to other parts of the intensive, for example coherence arguments have been mentioned before.
- Notes about format:
    - Some students did not value doing prereadings that overlapped with lectures
    - Since students had just learned one sub-topic for the first time, the cross-pollinisation prompts were far too complicated and the group discussions served better just for students to get some increased exposure across topics.
    - Use less niche field-specific terms or at least define them before they are used
- General cautions:
    - This topic attracts even more skepticism of credibility of authors (and lesswrong) than most of AI safety
    - Inferential distance to audience increases as audience is increasingly selected from the general (not AI safety) math/physics population.
    - Something to consider, is it worthwile to help participants develop an appreciation for agent foundations by challenging them about the theories of change of other alignment agendas? This strategy shows some success in small groups and one-on-ones but I am reluctant to apply it during lecture where it might come across as uncessarily defensive.
- Plan for future rewrite: instead of aiming to teach each subtopic to every participant which has proven to be too ambitious, make the primary goal to make the case for the overarching frame of agent foundations, and to allow them to go deeper in one subtopic of their choosing in order to appreciate the amount of mathematical substance that agent foundations can actually have.
- In general, we must make the assumptions more explicit:
    - Defining intelligence, agency, alignment etc in rigourous terms might be possible at all
    - Presupposing super intelligence
    - Defining intellience as being to do with steering the world
    - In the limit, agents will act rationally / be coherent
    - Alignment needs to be solved on a first critical try
