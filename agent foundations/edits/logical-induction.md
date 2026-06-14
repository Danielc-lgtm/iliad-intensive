# Logical Induction (lecture notes)

Article-class lecture notes, fully self-contained for a reader with zero background: probability/credence, Bayesian reasoning, logical omniscience, Dutch book, polynomial-time/efficient computation, prediction markets, propositional consistency, traders, exploitation are all built from examples. Project: `projects/logical-induction/main.tex`. Compiled PDF: `targets/logical-induction.pdf`.

**Title:** Logical Induction
**Subtitle:** How to be sensibly uncertain about mathematics you have not finished computing

**Abstract:** Bayesian reasoning assumes logical omniscience; logical uncertainty (not knowing the consequences of what you already know) breaks it. Logical induction weakens the Dutch-book demand: a betting market over mathematical statements (shares paying \$1 once proved), prices = probabilities, a deductive process publishing theorems over time, and rationality = no efficiently computable (polynomial-time) trader can exploit the prices. The single criterion forces convergence to coherent probabilities, timely learning of theorems before they are proved, correct statistical frequencies, respect for logical relationships, non-dogmatism, self-knowledge and self-trust. Develops the market and criterion precisely, sketches the constructive existence proof (the trading firm + Brouwer fixed point), surveys the properties, and connects to coherence theorems (the "no efficient Dutch book" generalization), Solomonoff induction, and open problems.

## Section 1: The uncertainty that more evidence cannot remove

- Empirical uncertainty (missing observations; resolved by evidence) vs logical uncertainty (missing computation; persists with full information): primality of 19,483, nth digit of pi, counting ones in "1+1+...+1 is even"
- Bayesian reasoning and credences defined from scratch; logical omniscience defined (any computation instant and free); a textbook Bayesian must already know every theorem; impossible for an embedded agent
- Why it matters for agents; plan; only probability + the idea of a program assumed

## Section 2: What we would want from a bounded reasoner

- Desideratum 1 (computable); 2 (coherent in the limit); 3 (approximately coherent along the way, the program-output example); 4 (sensible on uncrackable patterns, ~10% on nth digit of pi = 7); 5 (not dogmatic, Cromwell's law)
- The desiderata pull against each other; logical induction delivers all from one criterion

## Section 3: The betting market picture

- Betting market explained from scratch; each statement a share worth \$1 if true; price = probability via no-sure-loss
- Deductive process: a slowly-growing published list of proved theorems (Peano prover: proofs ≤ n symbols by day n); the reasoner must run ahead
- Traders: strategies (run by programs) trading on price history; we hold the market accountable only to efficiently computable / polynomial-time traders; polynomial time explained as the affordable/inaffordable dividing line

## Section 4: The logical induction criterion

- Definition 4.1 (the logical induction criterion): no efficiently computable trader exploits the market; such a market is a logical inductor
- Markets: pricing (a program's [0,1] valuation); market = sequence of daily pricings; belief states (the daily spreadsheet)
- Deductive process and worlds (complete true/false assignments, allowed to be logically wrong)
- Definition 4.2 (propositional consistency): respects and/or/not but not deeper math; checkable where full consistency is not; tightens as theorems are published
- Traders: continuous (no-jump) daily orders; efficiently computable = polynomial-time
- Definition 4.3 (exploitation): plausible appraisals $\{W(\sum_{i\le n}T_i): n, W\in\mathrm{PC}(D_n)\}$ bounded below but not above (unlimited return off limited stake); the "1+1=2 priced at 0.50 forever" example; arbitrage between statements whose "or" is provable
- The one-line intuition (any efficient pattern the prices miss is exploitable); Theorem 4.4 (existence, Garrabrant et al.): a computable logical inductor exists for every deductive process / reasonable theory

## Section 5: How such a market is built

- Single trader: continuous orders + market sets prices -> a balancing price (Brouwer fixed point, explained)
- All efficient traders at once: the trading firm runs the first n with budget $2^{-i}$; firm beats the market iff some trader does; price so the firm earns <= $2^{-n}$/day, total <= \$1; computable (brute-force price scan), finite belief state daily; impractical but existence licenses the properties

## Section 6: What the single criterion forces

- Prices settle on coherent probabilities (else buy-low/sell-high forever); provable->1, refutable->0, exclusive-exhaustive sum to 1
- Timely learning: any efficiently describable theorem sequence priced near 1 by day n regardless of proof length
- Calibration and right frequencies: uncrackable sequences get the correct base rate (nth digit of pi = 7 -> ~10%)
- Respects logical relationships: exclusive-exhaustive pairs sum to ~1 timely (even/odd digit of pi)
- Not dogmatic: never-refuted statements keep prob > 0, never-proven keep prob < 1 (the halving-prices trader)
- Self-knowledge and self-trust: prices statements about its own prices; self-trust = current probability ~ weighted average of expected future probabilities; defers to its future self without watching the reasoning (the tiling-agents link; here it's free from unexploitability where Löb blocks it)

## Section 7: Connections and open problems

- Lineage through the Dutch book (defined): coherence theorems presuppose logical omniscience; LI relaxes "no Dutch book" to "no efficient Dutch book" (no-adversary -> no-efficient-adversary), recovering coherence in the limit
- Resemblance to Solomonoff induction (experts reweighted by profit vs accuracy; LI traders can specialize); domain-independent (pixels instead of theorems)
- Two open limitations: no deciding-what-to-think-about; no logical impossibilities (eventually prices falsehoods at 0, conditioning undefined); both matter for embedded decision-making

## Sources

- *An Intuitive Guide to Garrabrant Induction* (full)
- Garrabrant, Benson-Tilsen, Critch, Soares, Taylor, *Logical Induction* (Ch 1 desiderata; Ch 3 criterion and existence theorem; Ch 4 properties skimmed)
