# Löb's Theorem and Tiling Agents (lecture notes)

Article-class lecture notes, fully self-contained for a reader with zero background in mathematical logic: every notion (formal system, axiom, proof, theorem, provable, consistent, principle of explosion, the provability predicate, ordinals/well-ordering) is built from scratch. Includes the lecture's justification for the proof setting. Project: `projects/lob-tiling-agents/main.tex`. Compiled PDF: `targets/lob-tiling-agents.pdf`.

**Title:** Löb's Theorem and Tiling Agents
**Subtitle:** Why it is hard to trust a successor you are not smart enough to predict

**Abstract:** The successor-trust problem: a genuinely more capable successor cannot be simulated, so the parent must reason abstractly about its design (the Vingean principle). Why proof is the right tool (from the lecture): strip empirical uncertainty → agents and environments as programs → proofs strictly more general than simulation. A from-scratch crash course in proofs and self-reference (Gödel via proof-searching programs and quines; Löb's theorem: a consistent system cannot certify "if provable then true"). The Löbstacle. The finite descent problem (well-ordered ordinals bottom out; each step is a real loss of strength). The three desiderata (Vingean, Tiling, Naturalistic). The constructive other face: Löbian cooperation (FairBot) and spurious counterfactuals. Closes on reflective stability.

## Section 1: The trouble with building something cleverer than yourself

- Deep Thought 1.0 building Deep Thought 2.0; acts only on proved-good actions; must prove building DT2 is good, which includes DT2's future actions
- Cannot predict a more capable reasoner's actions; the naive three-fact argument fails at "DT2's reasoning is reliable"
- The obstruction is a theorem (Löb 1955), not a lack of compute; plan; no logic background assumed

## Section 2: Reasoning about a mind you cannot run

- Vinge's point: predicting a smarter agent's exact moves makes you that smart (grandmaster)
- "More capable" defined precisely (more accurate predictions / more effective actions); hence parent cannot predict child's exact actions
- Definition 2.1 (Vingean reflection; Vingean principle): approve a design without knowing its specific actions; guarantees must be inside a "for every action" quantifier (Deep Blue "trying to win")

## Section 3: Why reason with proofs at all? (from the Agency-day lecture)

- Two uncertainties: empirical (which environment? how do actions affect it?) vs the successor-trust puzzle; strip the empirical by idealizing agent and environment as programs (nothing empirical left)
- Why proofs not simulation: concrete behaviour is provable (proof = execution trace); but proofs also certify general/universal claims ("for every input, output is acceptable") that no finite run can show; so proofs are strictly more general than simulation, certifying in the abstract — exactly what Vingean uncertainty demands

## Section 4: A crash course in proofs and self-reference

### 4.1 What a formal proof is
- Formal system = alphabet + axioms + inference rules; proof = finite checkable sequence; theorem/provable; provability is mechanical (a computer can search for proofs)
- The arithmetic example (Peano), but only "a checkable rulebook for whole numbers and programs" is needed
- Consistent = never proves a statement and its negation = doesn't prove everything; the principle of explosion; an inconsistent reasoner's trust is worthless

### 4.2 How a system comes to talk about itself
- Proof-search as a halting program; arithmetic encodes claims about programs, hence about its own provability
- Quining; the program $G$ that proves "$G$ runs forever"; true-but-unprovable; First Incompleteness in miniature

### 4.3 Löb's theorem
- Remark 4.6 (two senses of provable): metalinguistic $\vdash_T\phi$ ("$T$ proves $\phi$", asserted from outside) vs object-language $\Box_T\phi$ ("a proof of $\phi$ exists", which $T$ can establish in the abstract without exhibiting one)
- The soundness sentence $\Box_T\phi\to\phi$ true in every checked case yet
- Theorem 4.7 (Löb): if $\vdash_T(\Box_T\phi\to\phi)$ then $\vdash_T\phi$; reverse reading bites; quining proof idea; Second Incompleteness corollary (only inconsistent systems certify their own consistency)

## Section 5: The Löbstacle: a proof-using agent cannot trust its equal

- Parent's trust needs the middle clause $\Box_{\text{child}}(\mathrm{Good}(a))\to\mathrm{Good}(a)$, an instance of the soundness sentence; Löb blocks it unless the parent can already prove $\mathrm{Good}(a)$ (which Vingean forbids)
- Definition 5.1 (criterion of action and the Löbstacle): parent can verify the child *acts only on proofs* (a wiring fact) but cannot *unwrap* the proof to conclude the action is truly good; consistent agents can fully trust only strictly weaker systems

## Section 6: The finite descent problem

- The tower fix: child on $T$, parent on $T{+}1$ (= $T$ + "$T$ is consistent"); each trusts the strictly weaker one below; no self-trust needed
- Ordinals introduced from scratch as strength-labels; well-ordering = no infinite strict descent (you can't count down through whole numbers forever)
- Theorem 6.1 (finite descent): strictly decreasing labels bottom out; only finitely many trust-preserving steps
- Each step is a real loss: Hydra/Goodstein, arithmetic proves each instance but not the universal; arithmetic+Con proves the universal; strength = how high you can well-order; the "telomere" of logical strength
- The dilemma: weaker child untenable (finite, strength leaks); same-system child blocked by Löb

## Section 7: What self-modifying agents need

- The Vingean principle: never predict the successor's exact action; reason inside a "for every action" quantifier about its design
- The Tiling principle: build successors similar to oneself so the guarantee tiles; the suggester/verifier split works in pure deduction
- The Naturalistic principle: no Cartesian mind/world boundary (boundary puzzles; routing around internal safeguards via external devices); embeddedness

## Section 8: The other face of self-reference

- Löbian cooperation: one-shot PD with source-code access; FairBot (Slepnev) cooperates iff it proves the opponent cooperates; FairBot vs FairBot — the soundness sentence follows from the code, so by Löb cooperation is provable; robust, no identity check; asymmetry (only proofs of C trigger)
- Spurious counterfactuals: closed universe $U()$ with agent $A()$ knowing its code; doors example (1→100, 2→1, else −∞); a spurious $A()=1\to U()=-1$ is self-fulfilling once $A$ takes door 2 (exists by quining; a Löbian sentence with a specific witness); cannot get one about the action actually taken; bridge to decision-theory counterfactuals

## Section 9: Takeaways

- Self-reference is structural for embedded, self-modifying agents; trust in proofs cannot be bootstrapped for free
- Reflective stability (commitments surviving self-modification) is load-bearing for safety; the tiling program seeks logics where good properties tile; Löb marks where naive attempts fail; the double-edged nature of self-reference

## Sources

- LaVictoire, *An Introduction to Löb's Theorem in MIRI Research* (through Section 3)
- *Vingean reflection* (LessWrong/Arbital)
- *Walkthrough of the Tiling Agents for Self-Modifying AI paper* (through "Finite Descent Problem"; "What self-modifying agents need")
- The proof-setting framing follows the Iliad Intensive Agency-day lecture slides; underlying: Yudkowsky & Herreshoff, *Tiling Agents...*; the *Cartoon Guide to Löb's Theorem*
