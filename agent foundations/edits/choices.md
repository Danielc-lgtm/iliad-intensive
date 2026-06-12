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

Created `projects/optimization-thermodynamics/` (15 pages, article class, theorem/definition/example environments modeled on the decision theory CDT-to-UDT document). Several judgment calls; flag any you want changed:

1. **Included with proof:** the second law for doubly stochastic Markov chains (via log-sum inequality), the Type 3 bookkeeping derivation, and the partial-measurement demon bound $K(x)-K(y) \stackrel{+}{<} I(m(x):x)$ (derived from the algorithmic second law plus chain rule, following Ebtekar-Hutter eq. 68). These are short and carry the conceptual weight.
2. **Stated without proof, simplified:** Levin randomness conservation / algorithmic second law (stated informally for equal-volume cells with the $K(t-s) + \log(1/\delta)$ allowance; the $\tilde P$-conditioning is relegated to remarks), algorithmic free energy / work bound, and algorithmic Landauer. Full fluctuation-inequality machinery (Theorems 1, 7, detailed bounds (45)-(46), Jarzynski form) omitted as overwhelming for the format.
3. **Omitted entirely:** Gacs' general $S_\pi(x) = K(x) + \log\pi(x)$ appears only in footnotes (main text fixes equal-volume cells so $S = K$); multibaker maps mentioned in one sentence; logical depth, EP-vs-Landauer cost decomposition, and the information engine of Ebtekar-Hutter section V.D dropped (the Wentworth coin engine covers the same intuition earlier and more simply).
4. **The Touchette-Lloyd connection** is presented twice deliberately: ensemble version (Theorem, Shannon MI) in its own section, and the algorithmic single-shot counterpart inside the demon analysis, explicitly flagged as the rigorous form of Type 3. This seemed like the most precise way to honor "mutual info is the resource for optimization" without conflating Shannon and algorithmic MI.
5. **Authorship line** reads "Lecture notes, Agent Foundations module / Iliad Intensive" (no personal author), matching the unsigned style of the decision theory baseline.

**Decision:**
