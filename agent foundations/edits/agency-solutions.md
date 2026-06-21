# Agency Exercises (V2): Solutions

Article-class solution set for the exercises in `sources/Agency_exercise_V2.pdf`. Project: `projects/agency-solutions/main.tex`. Compiled PDF: `targets/agency-solutions.pdf`. Style: concise, math only, minimal prose.

**Title:** Agency Exercises (V2): Solutions
**Author:** Agent Foundations module, Iliad Intensive

Notation header: $L$ consistent formal system, $L\vdash\varphi$ provability, $K$ a fixed contradiction, $\Box P$ = "$P$ provable" = "$\mathsf{ProofSeeker}(P)$ halts"; the program/proof bridge in both directions.

## Section 1: Exercise 1 -- Gödel's second incompleteness theorem

Self-referential fact $(\star)$: $Z(Z)$ halts $\iff L\vdash G$, where $G:=\neg\mathsf{Halts}(Z(Z))$.

- **1(a)** $G$ is true. Case split on whether $Z(Z)$ halts; the halting case forces $L\vdash G$ and $L\vdash\mathsf{Halts}(Z(Z))$, contradicting consistency, so $Z(Z)$ runs forever.
- **1(b)** If $L\vdash\neg\Box K$ then $L$ inconsistent. The 1(a) argument formalizes to $L\vdash\neg\Box K\to G$; with $L\vdash\neg\Box K$ get $L\vdash G$, so $Z(Z)$ halts, so $L\vdash\mathsf{Halts}(Z(Z))$, contradiction.
- **1(c)(i)** If $L\vdash\Box P\to P$ for all $P$, then $L\vdash\neg P\Rightarrow L\vdash\neg\Box P$ (contrapositive of $\Box P\to P$).
- **1(c)(ii)** Take $P=K$: $L\vdash\neg K$ (tautology) gives $L\vdash\neg\Box K$, so by 1(b) $L$ is inconsistent (the Löbian obstacle).

## Section 2: Exercise 2 -- Löb's theorem

Properties used: (N) necessitation, (K) distribution, (4) Löb condition. Löb sentence $L\vdash\lambda\leftrightarrow(\Box\lambda\to C)$.

- **2(a)** Necessitation via ProofSeeker: a proof of $\varphi$ is found by $\mathsf{ProofSeeker}(\varphi)$, whose halting ($=\Box\varphi$) is finite and provable.
- **2(b)** Distribution via ProofSeeker: proofs of $\varphi\to\psi$ and $\varphi$ combine (concatenate + modus ponens) into a proof of $\psi$; the combining is formalizable.
- **2(c)** $L\vdash\Box\lambda\to\Box C$: apply (N) then (K) twice to the Löb sentence, and (4) to handle $\Box\Box\lambda$.
- **2(d)** Assuming $L\vdash\Box C\to C$: chain to $L\vdash\Box\lambda\to C$, use the Löb equivalence to get $L\vdash\lambda$, then (N) and modus ponens give $L\vdash C$.
- **2(e)** FairBot: from source, $L\vdash\Box B\to A$ and $L\vdash\Box A\to B$; monotonicity of $\Box$ gives $L\vdash\Box(A\wedge B)\to(A\wedge B)$; Löb with $C=A\wedge B$ yields $L\vdash A\wedge B$ (mutual cooperation).

## Section 3: Exercise 3 -- The Complete Class Theorem

Convention: higher reward better; $r(\delta)$ linear in mixing weights; $R=\operatorname{conv}\{r(a_j)\}$; $\mathrm{EU}(\delta,\pi)=\pi\cdot r(\delta)$.

- **3(a)(i)** Admissible rules put zero weight on dominated pure actions: replacing $a_j$ by a dominating rule $\delta'$ gives $r(\hat\delta)=r(\delta)+\lambda_j(r(\delta')-r(a_j))$, which dominates $\delta$ unless $\lambda_j=0$.
- **3(a)(ii)** Bayes-optimal under $\pi>0$ implies admissible: a dominating $\delta'$ would give $\mathrm{EU}(\delta',\pi)-\mathrm{EU}(\delta,\pi)\ge\pi_{i_0}(\cdots)>0$.
- **3(b)** Face $\mathcal F$ tangent directions: $\mathcal F\subseteq r(a_{i_1})+H$ with $H=\operatorname{span}\{v_l\}$, $v_l=r(a_{i_l})-r(a_{i_1})$; any displacement between two points of $\mathcal F$ lies in $H$ (coefficients sum to zero), and every $h\in H$ is realized from a relative-interior point.
- **3(c)(i)** $\pi\perp H$ makes $\mathrm{EU}(\cdot,\pi)$ constant $=c$ on $\mathcal F$.
- **3(c)(ii)** Supporting-hyperplane assumption gives $\pi\cdot r(\delta')\le c$ for all $\delta'$, so every rule on $\mathcal F$ is Bayes-optimal under $\pi$. Conclusion: admissible $\Rightarrow$ on a face $\Rightarrow$ Bayes-optimal under positive $\pi$; converse is 3(a)(ii).

## Section 4: Exercise 4 -- The Do-Divergence Theorem

Claim $D_{\mathrm{KL}}(\Pr[X]\|\Pr[X\mid\mathrm{do}(A)])\le\mathrm{MI}(A;O)$.

- Expand $D_{\mathrm{KL}}$ of the full joints: $\Pr[X\mid A,O]$ and $\Pr[O]$ cancel, leaving $\sum\Pr[a,o]\log\frac{\Pr[a\mid o]}{\Pr[a]}=\mathrm{MI}(A;O)$.
- Marginalize down to $X$ (baseline marginal $=\Pr[X\mid\mathrm{do}(A)]$); KL monotonicity under marginalization gives the bound.

## Section 5: Exercise 5 -- Channel Additivity

Channel $P[Y\mid X]=P[Y_1\mid X_1]P[Y_2\mid X_2]$.

- **5(a)** $\mathrm{MI}(X;Y)=\mathrm{MI}(X_1;Y_1)+\mathrm{MI}(X_2;Y_2)-\mathrm{MI}(Y_1;Y_2)$: expand each MI as a log-ratio over the full joint and collect (the $\frac{P[y_i\mid x_i]}{P[y_i]}$ and $\frac{P[y_1,y_2]}{P[y_1]P[y_2]}$ terms combine to $\frac{P[y_1\mid x_1]P[y_2\mid x_2]}{P[y_1,y_2]}$).
- **5(b)** $Q=P[X_1]P[X_2]$ (product of marginals): per-channel MIs unchanged, and $X_1\perp X_2$ under $Q$ forces $Y_1\perp Y_2$, so $\mathrm{MI}_Q(Y_1;Y_2)=0$; by 5(a), $\mathrm{MI}_Q(X;Y)=\mathrm{MI}_P(X;Y)+\mathrm{MI}_P(Y_1;Y_2)\ge\mathrm{MI}_P(X;Y)$.
- **5(c)** A maximizer $P^*$ exists (compactness); its marginal product $Q^*$ is also a maximizer with $X_1\perp X_2$, so a modular optimal input always exists.
