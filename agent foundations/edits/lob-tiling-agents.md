# Löb's Theorem and Tiling Agents (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/lob-tiling-agents/main.tex`. Compiled PDF: `targets/lob-tiling-agents.pdf`.

**Title:** Löb's Theorem and Tiling Agents
**Subtitle:** The logic of trusting a successor you cannot simulate

**Abstract:** The successor-trust problem: a genuinely smarter successor cannot be simulated, so the parent must reason abstractly about its design (the Vingean principle). A self-contained crash course in self-reference (Gödel via proof-searching programs and quines; Löb's theorem: a consistent system cannot prove "if provable then true"). The Löbstacle: the parent's natural way of trusting a successor on the same system is exactly a Löbian statement, so it cannot license that trust without inconsistency, and seems forced to hand each successor a strictly weaker system. The finite descent problem kills the tower-of-theories fix (well-ordered ordinals bottom out; each step is a real loss of strength, e.g. PA vs PA+1 on the Hydra/Goodstein statement). The three desiderata (Vingean, Tiling, Naturalistic). The constructive other face: Löbian cooperation (FairBot) and spurious counterfactuals. Closes on reflective stability.

## Section 1: Introduction: the trouble with building something smarter

- Deep Thought 1.0 building Deep Thought 2.0; only acts on proved-good actions; must prove building DT2 is good, which includes DT2's future actions
- Cannot predict a stronger reasoner's actions; the naive three-fact argument (same goals, reliable, acts only on proofs) fails at "DT1 knows DT2's reasoning is reliable"
- The obstruction is a theorem (Löb 1955), not a lack of compute; plan and prerequisites

## Section 2: The Vingean principle: reasoning about a mind you cannot run

- Vinge's point: predicting a smarter agent's exact moves in detail makes you that smart (Carlsen/chess)
- Definition 2.1 (Vingean reflection; Vingean principle): approve a successor's design without knowing its specific actions
- Guarantees must be inside quantifiers (for every action, it is safe), from the design not from simulation (Deep Blue "trying to win")

## Section 3: A crash course in self-reference

### 3.1 Gödel's insight, through proof-searching programs
- Proof-search as a halting program; arithmetic can talk about its own provability
- Quines; the program $G$ that proves "$G$ runs forever"; true-but-undecidable; First Incompleteness in miniature; inconsistency loophole (explosion)

### 3.2 Löb's theorem
- Remark 3.2 (two senses of provable): metalinguistic $\vdash_T\phi$ vs object-language predicate $\Box_T\phi$ ("there is a $T$-proof of $\phi$")
- $L(\phi) = (\Box_T\phi \to \phi)$ true in all three cases (provable/disprovable/undecidable) yet
- Theorem 3.3 (Löb): if $\vdash_T(\Box_T\phi\to\phi)$ then $\vdash_T\phi$; contrapositive bite; quining proof idea; Second Incompleteness corollary (only inconsistent systems prove their own consistency); bounded version

## Section 4: The Löbstacle: a proof-based agent cannot trust its equal

- Parent's trust requires the middle clause $\Box_{\text{child}}(\mathrm{Good}(a))\to\mathrm{Good}(a)$, an instance of $L(\mathrm{Good}(a))$; Löb blocks it unless the parent can already prove $\mathrm{Good}(a)$ (which Vingean says it cannot)
- Definition 4.1 (criterion of action and the Löbstacle): boxed form (child acts only on proofs) vs desired unboxed form (unwrap the proof); passing between them is a Löbian soundness step; consistent agents can fully trust only strictly weaker systems

## Section 5: The finite descent problem

- The tower fix: child on $T$, parent on $T{+}1$ (= $T$ + Con($T$)), each trusts the strictly weaker one below; no self-trust needed
- Theorem 5.1 (finite descent): strictly decreasing ordinals are well-ordered, so the chain bottoms out after finitely many steps
- Each step is a real loss: Hydra/Goodstein, PA proves each instance but not the universal; PA+1 proves the universal; strength = how high you can well-order
- The dilemma: weaker child untenable (finite, strength leaks); same-system child blocked by Löb

## Section 6: What self-modifying agents need

- The Vingean principle: never predict the successor's exact action; reason inside quantifiers about its design
- The Tiling principle: build successors similar to oneself so the guarantee tiles; the suggester ($\Sigma$) / verifier ($\Delta$) factoring works in monotonic logic
- The Naturalistic principle: no Cartesian mind/world boundary (boundary puzzles; routing around internal safeguards via external devices); embeddedness

## Section 7: The other face of self-reference

### 7.1 Löbian cooperation
- One-shot PD with source-code access; quining cooperate-with-identical is brittle; FairBot (Slepnev) cooperates iff it proves the opponent cooperates
- FairBot vs FairBot: $L(\text{"FairBot(FairBot)=C"})$ follows from the code, so by Löb cooperation is provable; robust, no identity check needed; asymmetry (only proofs of C trigger)

### 7.2 Spurious counterfactuals
- Closed universe $U()$ with agent $A()$ knowing its code; the doors example (1→100, 2→1, else −∞)
- $A$ proves a spurious $A()=1\to U()=-1$, takes door 2, which makes the counterfactual vacuously true; self-confirming, exists by quining (Löbian with a specific witness)
- Cannot get a spurious counterfactual about the action actually taken; repair needs care about proof order; bridge to decision-theory counterfactuals

## Section 8: Takeaways

- Self-reference is structural for embedded, self-modifying agents; trust in proofs cannot be bootstrapped for free
- Reflective stability: safety properties must be invariant under self-modification; the tiling program seeks logics where good properties tile; Löb marks where naive attempts fail; the double-edged nature of self-reference

## Sources

- LaVictoire, *An Introduction to Löb's Theorem in MIRI Research* (through Section 3)
- *Vingean reflection* (LessWrong/Arbital)
- *Walkthrough of the Tiling Agents for Self-Modifying AI paper* (through "Finite Descent Problem"; "What self-modifying agents need")
- Underlying: Yudkowsky & Herreshoff, *Tiling Agents...*; the *Cartoon Guide to Löb's Theorem*
