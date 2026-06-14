# Löb's Theorem and Tiling Agents (lecture notes)

Article-class lecture notes, fully self-contained for a reader with zero background in mathematical logic: every notion (formal system, axiom, proof, theorem, provable, consistent, principle of explosion, the provability predicate, ordinals/well-ordering) is built from scratch. Includes the lecture's justification for the proof setting. Project: `projects/lob-tiling-agents/main.tex`. Compiled PDF: `targets/lob-tiling-agents.pdf`.

**Title:** Löb's Theorem and Tiling Agents
**Subtitle:** Why it is hard to trust a successor you are not smart enough to predict

**Abstract:** The successor-trust problem: a genuinely more capable successor cannot be simulated, so the parent must reason abstractly about its design (the Vingean principle). Why proof is the right tool (from the lecture + exercise sheet): strip empirical uncertainty = hand the agent its environment's source code (+ both are programs); the only residue is what the code does, a logical question; proofs are strictly more general than simulation. A from-scratch crash course built around the ProofSeeker program: the program/proof bridge; provable ($L\vdash P$) vs provably-provable ($L\vdash\Box P$); Gödel; Löb's theorem with full proof via the derivability conditions, the Löb/Curry sentence, Tarski, and what Löb adds beyond Gödel. The Löbstacle. The finite descent problem. The three desiderata. The constructive other face: FairBot and spurious counterfactuals. Closes on reflective stability. Tone follows "An Introduction to Löb's Theorem" and the Agency exercise sheet V2.

## Section 1: The trouble with building something cleverer than yourself

- Deep Thought 1.0 building Deep Thought 2.0; acts only on proved-good actions; must prove building DT2 is good, which includes DT2's future actions
- Cannot predict a more capable reasoner's actions; the naive three-fact argument fails at "DT2's reasoning is reliable"
- The obstruction is a theorem (Löb 1955), not a lack of compute; plan; no logic background assumed

## Section 2: Reasoning about a mind you cannot run

- Vinge's point: predicting a smarter agent's exact moves makes you that smart (grandmaster)
- "More capable" defined precisely (more accurate predictions / more effective actions); hence parent cannot predict child's exact actions
- Definition 2.1 (Vingean reflection; Vingean principle): approve a design without knowing its specific actions; guarantees must be inside a "for every action" quantifier (Deep Blue "trying to win")

## Section 3: Why reason with proofs at all? (from the Agency lecture + exercise sheet)

- Two uncertainties: empirical (which environment am I in? how do my actions affect it?) vs the successor-trust puzzle
- **Stripping the empirical uncertainty = handing the agent its environment's source code**: removing uncertainty about which environment I'm in means the agent *knows* the environment; with the environment idealized as a program, that means the agent holds the environment's source code (and its own). Nothing empirical is left; the only residue is what the code does when run (a logical/computational question). This is the spurious-counterfactual setting ($U()$ with $A()$ knowing $U$'s code)
- Why proofs not simulation (via the program/proof bridge): concrete behaviour is provable (proof = execution trace); but proofs also certify universal claims ("for every input, output is acceptable") no finite run can show; so proofs are strictly more general than simulation — exactly what Vingean uncertainty demands

## Section 4: A crash course in proofs and self-reference

### 4.1 Formal systems, programs, and the bridge between them
- Formal system $L$ = alphabet + axioms + inference rules; proof = finite checkable sequence; $L\vdash P$ = P provable; consistency $L\not\vdash K$ (K = "0=1"); principle of explosion; an inconsistent reasoner's trust is worthless
- The bridge: programs→L (if M halts in 17 steps, L proves it); L→programs: $\mathrm{ProofSeeker}(P)$ := "try every string; halt iff a valid L-proof of P" — halts iff P is provable. L can talk about its own provability via this program

### 4.2 Provable, versus provably provable
- $L\vdash P$ = a concrete proof of P in hand vs $L\vdash\Box P$ = L has proved "a proof exists" (= ProofSeeker(P) halts), a claim about the program, not a certificate for P
- Two routes to proving $\Box P$: trace the execution (yields a direct proof of P, in hand) vs reason abstractly about the program (knows a proof is "out there" but not in hand). The gap L cannot close in general

### 4.3 Gödel: a true statement no proof can reach
- The self-referencing program $Z(A)$ := "search for an L-proof that $A(A)$ runs forever"; $G$ = "$Z(Z)$ runs forever" is true but unprovable (First Incompleteness); sharper than halting-undecidability; Second Incompleteness (L can't prove $\neg\Box K$ = its own consistency)

### 4.4 Löb's theorem
- The soundness sentence $\Box C\to C$ true from outside, yet
- Theorem 4.x (Löb): if $L\vdash(\Box C\to C)$ then $L\vdash C$
- Proof via the three derivability conditions explained through ProofSeeker — Necessitation ($L\vdash\varphi\Rightarrow L\vdash\Box\varphi$), Distribution ($\Box(\varphi\to\psi)\to(\Box\varphi\to\Box\psi)$, the proof-transforming-function analogy), the Löb condition ($\Box\varphi\to\Box\Box\varphi$) — plus the self-referential Löb sentence $\lambda\leftrightarrow(\Box\lambda\to C)$ and the derivation
- The Curry / Santa Claus paradox ("if this sentence is true then C") and Tarski (L has no truth predicate, only the provability predicate $\Box$); liar→Gödel, Curry→Löb
- What Löb adds beyond Gödel: not just no self-consistency proof, but no case-by-case self-trust; L never trusts a proof until it witnesses it; Second Incompleteness as the case $C=K$; bounded-proof version

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
