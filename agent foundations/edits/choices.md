# Choices

Claude Code writes design questions and decision points here. Each is numbered
with an ID. Respond by writing your answer after the question, or in instructions.md
referencing the choice ID.

Format:
## Choice #1: [Short description]
[Question or options]

**Decision:** [You write your answer here]

---

(Choices appear below this line)

## Choice #1: Scope and depth decisions in the "Optimization and thermodynamics" lecture notes

[RESOLVED by author request 2026-06: rewrite to be much more pedagogical and self-contained, no page limit, full prose (no telegraphic constructions), include all content including the generalized heat engine and Touchette-Lloyd integrated seamlessly. Implemented in the 34-page version; superseded decisions: the 15-page length, the omission of the EP-vs-Landauer decomposition, the omission of the Ebtekar-Hutter information engine, and the compressed treatments of the coin engine and Touchette-Lloyd.]

## Choice #2: Remaining scope decisions in the expanded (34-page) version

The rewrite includes everything flagged before plus: full coin-engine treatment (designer viewpoint, example transformation, one-bath impossibility argument, two-bath calculation), full Touchette-Lloyd treatment (worked blind computation of 4.94 bits, sighted table, MI-from-actions example, provenance footnote, insufficiency examples, headphones), EP-vs-Landauer cost decomposition with both misconception corrections, the randomization/computation/measurement cost audit, the controlled-NOT Type-3 example, the bookshelf example, and the information engine (burn/eat/digest, ancilla zeros, starvation). Two things remain deliberately excluded; flag if you want either added:

1. **Logical depth** (Ebtekar-Hutter discussion section): the slow-growth law for logical depth and its connection to the arrow of time. Excluded as a tangent from the optimization theme.
2. **Full fluctuation-theorem machinery** (Ebtekar-Hutter Theorems 1 and 7, detailed bounds (45)-(46), the algorithmic Jarzynski equality in its exponential form, and the algorithmic free energy $F(x) = E(x) - k_B T \ln 2\, K(x)$): the notes state the tail-bound forms only. Excluded to keep all stated results provable or plausible at the level of rigor the notes establish; the work-capacity story is carried by the Landauer inequality and Zurek's identity instead.

**Decision:**

## Choice #3: Optimization-and-thermodynamics restructure (2026-06 edit session)

The author requested: move the generalized heat engine to an appendix and reference it when needed; epistemically calibrated language (no exaggeration for dramatic effect); move "three types of optimization" to immediately after the second law and link it to Touchette-Lloyd (specifically Type 3); note that Touchette-Lloyd makes no reversibility assumption; otherwise keep existing structure. Decisions made while implementing:

1. **Appendix placement.** The coin-engine section became `\appendix` Appendix A, placed after the Takeaways and before "Sources and further reading". All six prose references to it were reworded from "Section" to "Appendix"; cross-references resolve to "Appendix A". This supersedes the Choice #1 resolution that had it "integrated seamlessly" in the main line. *If you would prefer it placed after Sources, or kept as a numbered final section rather than a lettered appendix, say so.*
2. **Three types before Touchette-Lloyd.** New section order is §4 second law -> §5 three types -> §6 Touchette-Lloyd -> §7 subjective -> ... The "demon reframed" subsection and the end-of-§5 recap now forward-reference Touchette-Lloyd as the quantification of the Type-3 channel; §6 opens by recalling Type 3 and closes its "coin engine revisited" remark by identifying $I(X;A)$ with the Type-3 budget. The no-reversibility note was added right after the theorem statement, with a sentence on why it is consistent with the reversibility-based second law.
3. **Calibration pass scope.** I toned down clear dramatic/overclaiming phrases ("the most famous", "astonishingly small", "sharp and beautiful", "beautiful subtlety", "pleasing echo", "the satisfying one", "rotten", "exorcising", "hopelessly below", "absurd"/"absurdity", "flatly contradict", "fantastic shapes", "a striking consequence") and softened the strong "necessarily models its environment" claim to "must contain mutual information ... a necessary (not sufficient) ingredient of a world model". I deliberately left most of the document's voice and vivid-but-accurate metaphors intact rather than sanitising it wholesale. *Flag if you want a heavier or lighter calibration pass.*

**Decision:**

## Choice #4: Agency-presentation edits (2026-06 edit session)

Decisions made on the `<div>`-marked edits where intent had to be reverse-engineered:

1. **Goodhart slide.** "Remove this slide on Goodhart's law" was implemented as: drop the $U=V+X$ proxy-breakdown block, but keep the "true names" framing (it is load-bearing for the rest of the talk), retitling the frame "Robust Concepts (True Names)" with a short motivation block. *If you wanted the entire frame including the true-names list removed, say so.*
2. **Logical induction "to the end like a footnote".** Implemented as: the computational-uncertainty material (your formalism + diagram + open problems) is now the main content of the logical-uncertainty section; logical induction is condensed to a single end slide titled "Aside: Logical Induction" (criterion kept, construction removed, the Dutch-book analogy demoted to a parenthetical). *If you literally wanted a `\footnote`, or wanted logical induction cut entirely, tell me.*
3. **Decision-theory slides.** Removed from the deck and saved as a self-contained, compilable copy at `decision theory/sources/decision-theory-slides.tex` (with `bayesnet.png` copied alongside). The Conclusion's decision-theory bullet was kept but reworded to "(treated separately)" so the deck no longer claims to cover DT. *If you would rather the copy live in the `dt-presentation` project, or want the DT bullet dropped from the Conclusion entirely, say so.*
4. **Embedded-AIXI incorporation.** I folded in the conceptual content (cybernetic model; "large agent" assumptions; the embedded-agency bullets; "AIXI does not believe the universe contains AIXI agents") and kept the existing Alexei/Emmy images, which are the same canonical graphics the AIXI slides borrow. I did not extract additional images from `Embedded_AIXI.pdf`, judging them redundant with Alexei/Emmy. The embedded-agents content was split across two slides to avoid overflow.

**Decision:**

## Choice #5: Second-round updates (2026-06 edit session, follow-up)

Author follow-up: make each slide fully self-contained (assume no agent-foundations background; do not use unexplained named examples like UDT or infra-Bayesianism); remove the true-name slide entirely; in the algorithmic-thermodynamics notes, remove the Landauer's-principle and thermodynamic-costs-of-information-processing subsections and emphasise dissolving subjectivity; push to `main`. Decisions made:

1. **Self-containment.** Removed all unexplained named examples from the agency deck: the Modelling/Implementation slide no longer names AIXI, reflective oracles, UDT, infra-Bayesian physicalism, or JEPA -- each is replaced by a self-contained description (the modular-architecture idea is described in words; the JEPA name is dropped). The dualistic and embedded slides no longer name AIXI; the "large agent" and "cannot contain a copy of itself" points are stated directly. I also removed the cryptic "Measuring stick of utility problem" sidenote on the coherence slide as an unexplained pointer. *If you wanted JEPA or AIXI kept as named pointers, I can re-add them with a one-line gloss.*
2. **True-name slide.** Removed entirely. Its only downstream dependency -- the closing bullet of the Modelling/Implementation slide ("which is why we want the true names above") -- was reworded so nothing dangles.
3. **Algorithmic thermodynamics surgery.** Deleted the two subsections (Heat/temperature/Landauer; thermodynamic costs of information processing). The Maxwell's-demon and information-engine subsections were kept but de-coupled from the removed material: the demon's memory-reset is now described in informational terms (exporting K(x) bits to the environment as Type-1 waste) with no heat/joules; all cross-references into the removed sections (in §4.3, §5.3, §9, the takeaways, the plan paragraph, and the sources list) were rewritten. The section intro, the takeaways, and the plan paragraph now foreground the dissolving-subjectivity payoff. The bit-to-joule exchange rate ($\kB T\ln2$) is gone from the synthesis; the exchange rate is now stated purely informationally (one bit of steering per bit of correlation). The biased-coin appendix still discusses heat/temperature/energy analogues, which is internal to that toy world and self-contained. *Flag if you also want the information-engine subsection trimmed, or the $\kB T\ln2$ rate reinstated somewhere.*

**Decision:**
