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

## Choice #6: Third-round updates (2026-06 edit session, follow-up 2)

Author follow-up: remove the information engine; in "From exogenous to endogenous knowledge", make the algorithmic-mutual-information argument rigorous via Shannon coding (belief update $\to$ higher probability on the true environment $\to$ short codelength bounds $K(s\mid a)$ $\to$ higher $I(a:s)$ $\to$ more optimization, linking to Touchette-Lloyd). Decisions:

1. **Information engine removed** (the last subsection of §8); §8 now ends with the demon, which is also the dissolving-subjectivity payoff. All four references to it (plan paragraph, §9.4 retargetability, the appendix's role note, the Ebtekar-Hutter source annotation) were rewritten. The now-unreferenced `sec:cointeach` label in the appendix is harmless and left in place.
2. **Rigorous endogenous-knowledge derivation.** Added a "Making the link precise" block to §9.1 with the exact chain: assuming the memory $a$ encodes a computable belief $q$ (recovered from $a$ by an $O(1)$ program), the Shannon-codeword bound gives $K(s\mid a)\plt\log 1/q(s)$, hence $I(a:s)\pgt K(s)-\log 1/q(s)$; updating toward the truth raises $q(s)$, shrinks the codelength and the residual $K(s\mid a)$, and raises $I(a:s)$; the algorithmic Touchette-Lloyd bound then converts this into achievable optimization. The one modeling assumption is that the agent's memory *is* (an $O(1)$-encoding of) its belief distribution; everything else is the established codelength bound (§2.3 / §8.2) and the algorithmic TL bound. *If you would rather not assume "memory encodes a computable distribution" and instead want the argument stated for an arbitrary record, the bound weakens to the generic $I(a:s)$ definition; tell me if you prefer that framing.*

**Decision:**

## Choice #7: Fourth-round updates (2026-06 edit session, follow-up 3)

Author follow-up: shorten Flint's *ground of optimization* (use it as a basis for "optimization as entropy reduction", not the centre) and do the same in §9.4; emphasise "knowing more $\to$ more optimization" earlier by combining the belief$\to$MI and MI$\to$optimization bridges and stating the implication up front; in the agency deck, add a concise bullet-form version of the Shannon-codelength justification, combined with the optimization-and-thermodynamics slides. Decisions:

1. **Shortened §3.2/§3.3.** Removed the separate gradient-descent and house *example* boxes (folded into two sentences) and condensed the three-axes subsection from three paragraphs to one. Kept Definition 3.1, the ball-in-valley example box (cross-referenced from §6), and the label `sec:axes`. The unused `ex:sqrt2`/`ex:house` labels were dropped. §3.5 (optimization as entropy reduction) remains the centre.
2. **Shortened §9.4** similarly: the three-axes mapping is now a brief tail; the section leads with the world-model entailment.
3. **Reframed §9.1** so the "Making the link precise" block opens with the common intuition, explicitly composes the two bridges into a single inequality, and states the headline implication ("more probability on the truth $\Rightarrow$ more optimization") up front rather than at the end.
4. **New agency slide** "Optimization and Thermodynamics: why knowing more formally means optimizing more" -- four concise bullets giving the belief$\to$MI Shannon bound and the MI$\to$optimization (Touchette-Lloyd) step, placed with the other optimization-and-thermodynamics slides. Compiles with no overflow (deck now 26 slides).

**Decision:**

## Choice #10: Courier example, dropped optimizer/optimized point, and a V2 full rewrite with critical pass (2026-06 edit session, follow-up 7)

Author asks: (1) replace the thermostat/temperature example (temperature equilibrates and is not hard to predict) with one that is genuinely hard to predict exactly yet steerable by real agents; (2) drop the explicit "we don't separate optimizer vs optimized" point (the distinction is left implicit); (3) create a V2 that rewrites the rest of the document in the new Section-3 style, then do a harsh critical-correctness pass; put both versions in projects/ and targets/ (new one = V2). Decisions:

1. **New running example: a courier delivering to a fixed address.** Used in §3.2 and §3.4 of both V1 and V2. It satisfies both criteria: the route/where-it-is is genuinely hard to predict (chaotic traffic), and real agents steer it (couriers, delivery robots, navigation systems). The thermostat was removed from §3.2's list of optimizers too (replaced by a chess engine etc.). The satellite-vs-courier contrast now carries "restoring tendency present vs absent"; the ball-in-valley was dropped from §3.2 (it still appears once in Appendix B as a passive contracting-dynamics example, which is appropriate there).
2. **Dropped the optimizer/optimized sentence** in §3.2 ("Two omissions" -> "One omission"), keeping only the no-goals/no-mentalism point.
3. **V2 created** at `projects/optimization-thermodynamics-v2/` (PDF `targets/optimization-thermodynamics-v2.pdf`, mirror `edits/optimization-thermodynamics-v2.md`). The prose of the Introduction and Section 4 was substantially rewritten (long paragraphs broken into short, signposted, intuition-first ones); Sections 6 and 7 had their longest motivating paragraphs tightened; the whole document was made em-dash-free (parentheses/colons). Sections 2, 5, 8, 9 and both appendices were already in the target style (example-led, crisp) and were kept, receiving only the global corrections below. Title carries a "Version 2 (revised exposition)" line. V2 is 31 pages, V1 32; both compile with zero undefined references and no warnings.
4. **Critical pass found a genuine conceptual error in §3.4 (the prediction argument), fixed in BOTH V1 and V2.** The original claimed, via `I(O;Y) = H_0 - H(Y|O)`, that you "predict many bits of the future per bit learned" (ratio > 1). That violates `I(O;Y) <= H(O)`: an observation never removes more uncertainty about Y than its own information content -- there is no free lunch. Rewrote §3.4 to make the correct, still-strong claim: it is about *comparative cost*. The optimizer's target is a short, robust description of the macroscopic outcome (cost ~ the target's description length), versus the initial-condition model (cost ~ H(X), and chaos-fragile); the win is `ell(T) << H(X)`, not "more bits out than in." Added an explicit "no free lunch" sentence. Propagated to §3.5 (removed the dangling `I(O;Y)` reference), the takeaways bullet, and both markdown mirrors.
5. **Minor V2 polish:** de-duplicated a repeated sentence in the §4.3 footnote on unequal cell volumes. (Left as-is in V1 to keep V1 minimal.)

*Open: V1 still contains two pre-existing em-dashes (house style); I left V1's broader prose untouched since V2 is the clean rewrite. Say if you want V1 also made dash-free, or want any section of V2 rewritten more (or less) aggressively.*

**Decision:**

## Choice #9: Replace Flint/Yudkowsky intro with the convergent-attractor + prediction argument; Touchette-Lloyd to an appendix (2026-06 edit session, follow-up 6)

Author request (from `sources/fixed_aim.txt`): remove the content of Flint's *ground of optimization* (which includes Yudkowsky's optimization-power definition) from the body, keep them only as references, and replace them with the conceptual argument in `fixed_aim.txt` (optimizer as convergent attractor; optimization as entropy reduction; why a pure predictor should attend to optimizers; optimization as observer-independent). Also: move the Touchette-Lloyd theorem to an appendix and update all references. Decisions made:

1. **Section 3 rewrite.** Replaced the "Optimizing systems", "Three axes", and "Measuring optimization in bits" subsections with: §3.2 *Optimizers as convergent attractors* (control-theory framing, thermostat/ball/satellite examples, broad initial conditions + robustness, whole-system view with no optimizer/optimized split and no goal-talk -- this absorbs the useful parts of Flint without naming him or his definitional apparatus); §3.3 *Optimization as entropy reduction* (kept, with the Flint "basin" wording and the Yudkowsky paragraph removed; `rem:translation`/Wentworth kept); §3.4 *Why a predictor should attend to optimizers* (the efficient-prediction argument, made fully explicit: define $O$, $I(O;Y)=H_0-H(Y\mid O)$ large vs description-length of $O$ small, contrast with the $H(X)$/chaos route, thermostat illustration, robustness point); §3.5 *Optimization is an objective feature, not observer-relative*.
2. **Observer-relative view.** Per the request to "search the web for the accurate description", §3.5 states the view via the No Free Lunch theorems (competence relative to a problem class reflecting the observer's interests) and Dennett's intentional stance (agency as a predictive stance an observer adopts), then contrasts: the convergent-attractor question and its predictive value $I(O;Y)$ are observer-independent, so a pure predictor singles out optimizers without fixing any tasks. Kept brief (two short paragraphs) per request. Both added to the reference list.
3. **William James not cited.** Per request, the "fixed aim / varying means" source is absorbed conceptually but not cited; no James reference was added.
4. **Flint/Yudkowsky as references only.** Both kept in "Sources and further reading", reframed as further reading (no in-body exposition, no dangling "source for Section X" claims). *If you would rather drop the Yudkowsky entry entirely (the instruction only explicitly required keeping Flint "as reference"), say so.*
5. **Touchette-Lloyd to Appendix B.** The whole §6 block was moved verbatim (with one internal `Example~\ref{ex:ball}` reference reworded, since that example was deleted) to a new Appendix B, after the coin-engine Appendix A and before "Sources and further reading". All body references updated: `Section~\ref{sec:tl}` -> `Appendix~\ref{sec:tl}` (plan, §4.2 transition, §4.5, §5 end, §5.5 demon-reframe, §9.1, the coin appendix's forward pointer), `Section~\ref{sec:tlcaveats}` -> `Appendix~\ref{sec:tlcaveats}` (§8.2, §9.4); `Theorem~\ref{thm:tl}` references kept (the theorem renumbers to B.1 automatically) with an added "(Appendix~\ref{sec:tl})" pointer at the two main-body uses. The abstract and plan note that the theorem is now developed in an appendix. *If you would prefer Touchette-Lloyd as Appendix A (before the coins), or restored to the main line, say so.*
6. **§9.4 "Back to optimizers".** Retitled from "Back to optimizing systems"; the Flint three-axes thermodynamic readings were removed; the section now leads with the world-model entailment and ties it to the §3.5 observer-independence point.

**Decision:**

## Choice #8: Sixth-round update (2026-06 edit session, follow-up 5)

Author follow-up: revert the previous commit (the recast of optimization as "steering into narrow regions" plus the document-wide de-flowering pass), returning the optimization-and-thermodynamics notes to the previous version; then, on that base, modify only the "Knowledge as a physical resource" section (Section 9) for more clarity and simpler phrasing. Done as follows:

1. **Revert.** Restored `projects/optimization-thermodynamics/main.tex`, its mirror, and this file to the previous commit (`77f0be9`) via `git checkout`, so the Flint/Yudkowsky material and the original prose are back. The Agency deck was untouched by the reverted commit, so it was left as-is. No history was rewritten and no force-push was used; the revert is a normal commit on top of the reverted one.
2. **Section 9 clarity pass.** Rewrote all four subsections of Section 9 (from exogenous to endogenous knowledge; the three types sharpened; dissolving the subjectivity; back to optimizing systems) with shorter sentences and plainer wording. The structure, the Shannon-coding derivation, every equation, and all cross-references are unchanged; the diff against the previous version is confined to Section 9 (a single hunk). The Flint three-axes content in Section 9.4 was kept (consistent with the reverted base), only clarified.

**Decision:**
