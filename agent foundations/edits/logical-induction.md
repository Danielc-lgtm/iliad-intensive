# Logical Induction (lecture notes)

Article-class lecture notes, fully pedagogical and self-contained. Project: `projects/logical-induction/main.tex`. Compiled PDF: `targets/logical-induction.pdf`.

**Title:** Logical Induction
**Subtitle:** Reasoning under logical uncertainty, via a market no efficient trader can beat

**Abstract:** Bayesian reasoning assumes logical omniscience; logical uncertainty (not knowing the consequences of what you already know) breaks it. Logical induction weakens the Dutch book demand: a prediction market over logical sentences (shares paying \$1 if proved), prices = probabilities, a deductive process revealing theorems over time, and rationality = no efficiently computable (poly-time) trader can exploit the prices. The single criterion forces convergence to coherent probabilities, timely learning of theorems before they are proved, correct statistical frequencies, respect for logical relationships, non-dogmatism, introspection and self-trust. Develops the market and criterion precisely, sketches the constructive existence proof (the trading firm), surveys the properties, and connects to coherence theorems (the "no efficient Dutch book" generalization), Solomonoff induction, and the open problems.

## Section 1: Introduction: the uncertainty that more data cannot fix

- Empirical vs logical uncertainty; the latter persists with no missing data (source code without output; primality of 19,483; nth digit of pi; counting ones in "1+1+...+1 is even")
- Bayes builds in logical omniscience (any computation at no cost); a textbook Bayesian must already know every theorem; impossible for an embedded agent
- Why it matters for agent foundations; plan and prerequisites (probability, poly-time)

## Section 2: What we want from a bounded reasoner

- Desideratum 1 (computable approximability); 2 (coherence in the limit); 3 (approximate coherence at finite times, the prg(7)=0/1 example); 4 (learning statistical patterns, ~10% on nth digit of pi = 7); 5 (calibration); 6 (non-dogmatism / Cromwell's law extended to logic)
- The desiderata pull against each other; logical induction delivers all from one criterion

## Section 3: The market picture

- Each sentence a share worth \$1 if true; market maker quotes prices = probabilities (0.75 = 75% credence)
- Deductive process: slow source of verified theorems (Peano prover: all proofs of <= n symbols by day n); the reasoner must outpace it
- Traders: algorithms watching price history and trading; we hold the market accountable only to efficiently computable (poly-time) traders

## Section 4: The logical induction criterion

- Definition 4.1 (the logical induction criterion): no efficiently computable trader exploits the market; such a market is a logical inductor
- Markets: valuation $V:\mathcal S\to[0,1]$; pricing (computable rational); market = computable sequence of pricings; belief states (finite support, the daily spreadsheet)
- Deductive processes ($D_n$ nested finite sets) and worlds (truth assignments $W:\mathcal S\to\mathbb B$, not necessarily consistent)
- Definition 4.2 (propositional consistency): respects Boolean structure; checkable where full consistency is not; $\mathrm{PC}(D)$; the deductive process weeds out p.c.-but-impossible worlds
- Traders: trading strategy = affine combination of shares with continuous (expressible-feature) coefficients; efficiently computable = poly-time
- Definition 4.3 (exploitation): plausible valuations $\{W(\sum_{i\le n}T_i(P)): n, W\in\mathrm{PC}(D_n)\}$ bounded below but not above (unbounded return off bounded investment); the "1+1=2 priced at 0.50 forever" example; arbitrage between sentences whose disjunction is provable
- The one-line intuition (any poly-time pattern the prices miss is exploitable); Theorem 4.4 (existence, Garrabrant et al.): a computable logical inductor exists for every deductive process / recursively axiomatizable theory

## Section 5: How the market is built

- Single trader: continuous demand + market sets prices -> a price leaving the trader indifferent (Brouwer fixed point for many traders)
- All efficient traders at once: the trading firm runs the first n poly-time strategies with budget $2^{-i}$; firm exploits iff some trader does; price so the firm earns <= $2^{-n}$/day, total <= \$1; computable (brute-force rational search), finite belief state daily; impractical but existence licenses the properties

## Section 6: What falls out of the criterion

- Convergence and coherence: prices converge (else buy-low/sell-high forever); limit is a coherent probability distribution (provable->1, refutable->0, exclusive-exhaustive sum to 1)
- Timely learning: any efficiently computable sequence of theorems gets ~prob 1 by day n regardless of proof length; faster on sparse subsequences
- Calibration and statistical patterns: pseudorandom sequences get correct limiting frequency (nth digit of pi = 7 -> ~10%)
- Learning logical relationships: exclusive-exhaustive pairs sum to ~1 timely (even/odd digit of pi)
- Non-dogmatism: never-disproven sentences keep prob > 0, never-proven keep prob < 1 (the halving-prices trader); may sit at wrong extremes on finite days
- Introspection and self-trust: prices sentences about its own prices; self-trust (Sec 4.12) = current credence ~ weighted average of expected future credences; defers to its future self without witnessing the reasoning (the cross-pollination link to tiling agents; here it falls out of unexploitability where Löb blocks it)

## Section 7: Connections and open problems

- Lineage through the Dutch book: coherence theorems presuppose logical omniscience; LI relaxes "no Dutch book" to "no efficient Dutch book" (parallel to no-adversary -> no-efficient-adversary), recovering coherence in the limit
- Resemblance to Solomonoff induction (experts reweighted by profit vs accuracy; LI traders can specialize); domain-independent (pixels instead of theorems)
- Two open limitations: no decision-directed thinking (cannot focus computation on the question that matters); no logical counterpossibilities (eventually assigns prob 0 to falsehoods, conditioning undefined); both matter for embedded decision theory

## Sources

- *An Intuitive Guide to Garrabrant Induction* (full)
- Garrabrant, Benson-Tilsen, Critch, Soares, Taylor, *Logical Induction* (Ch 1 desiderata; Ch 3 criterion and main theorem; Ch 4 properties skimmed)
- Connections: consequentialist foundations (Dutch book); self-trust (Sec 4.12) and tiling agents
