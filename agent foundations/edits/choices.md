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
