## Roth's Theorem — The First Density Theorem

If van der Waerden says any coloring of $\mathbb{N}$ forces a 3-term AP, Roth says you don't even need to color everything. A single set occupying positive fraction of integers already forces a 3-term AP.

First time density, not partition, forces arithmetic order — $k=3$ case of Szemerédi, analytic heart that later powers Green-Tao.

> **Roth's Theorem 1953:** Any subset of $\mathbb{N}$ with positive upper density contains a non-trivial 3-term AP.

Proved by Klaus Roth — Fields Medal 1958 — launched modern additive combinatorics.

### Formal Statement

**Upper density:**

$$\displaystyle \bar d(A)=\limsup_{N\to\infty}\dfrac{\left|A\cap[1,N]\right|}{N}$$

Fraction of $\left\{1,\dots,N\right\}$ belonging to $A$, taken $\limsup$ — best infinitely often.

If $\displaystyle \bar d(A)=\delta>0$ then exists $a,d$ with $d\neq0$ and $\displaystyle a,\;a+d,\;a+2d\in A$ three equally spaced numbers inside $A$, non-trivial $d\neq0$.

Note $\bar d$ uses $\limsup$, not limit — allows sets like numbers starting with $1$, density oscillates $10\%$ to $55\%$, still $\bar d>0$ so Roth applies.

**Quantitative finite form:**

Let

$$\displaystyle r_{3}(N)=\max\left\{\left|A\right|:A\subset[1,N],\;A\text{ contains no non-trivial }3\text{-AP}\right\}$$

Largest AP-free size.

Roth proved:

$$\displaystyle r_{3}(N)=O\!\left(\dfrac{N}{\log\log N}\right)$$

Because $\displaystyle\dfrac{1}{\log\log N}\to0$, we have $\displaystyle\frac{r_{3}(N)}{N}\to0$.

Consequence: Fix $\delta>0$. For large $N$,

$$\displaystyle \delta N > C\cdot\dfrac{N}{\log\log N}\ge r_{3}(N)$$

since $\displaystyle\dfrac{1}{\log\log N}\to0$. So any $A\subset[1,N]$ with $\left|A\right|\ge\delta N$ must contain $3$-AP.

Take $A\subset\mathbb{N}$ with $\bar d(A)=\delta>0$ — then infinitely many $N$ with $\left|A\cap[1,N]\right|\ge\tfrac{\delta}{2}N$. For large such $N$, $\left|A\cap[1,N]\right|>r_{3}(N)$ → contains $3$-AP. So infinite set with positive upper density contains $3$-AP — actually infinitely many.

Question since: how fast does $\displaystyle \dfrac{r_{3}(N)}{N}\to0$?

Roth gave $\displaystyle O\!\left(\tfrac{1}{\log\log N}\right)$. Behrend gives lower bound $\displaystyle\Omega\!\left(\exp\!\left(-C\sqrt{\log N}\right)\right)=\dfrac{1}{\exp\!\left(C\sqrt{\log N}\right)}$. Gap huge: $\exp(-C\sqrt{\log N})$ decays slower than any $\left(\log N\right)^{-c}$? Actually faster than $\left(\log\log N\right)^{-1}$? Let's compare: $\exp(C\sqrt{\log N})\gg\log\log N$ for large $N$, so Behrend upper on density $\displaystyle\frac{r_{3}(N)}{N}\ge\frac{1}{\exp(C\sqrt{\log N})}$ much larger than Roth's $\dfrac{1}{\log\log N}$? No, $\dfrac{1}{\exp(\sqrt{\log N})}\ll\dfrac{1}{\log\log N}$ eventually — so Roth upper bound far from Behrend lower bound. Closing gap is $70$-year program culminating in Bloom-Sisask $\displaystyle\frac{1}{(\log N)^{1+c}}$.

In van der Waerden language: $W(2,3)=9$ says $2$-coloring of $\left[1,9\right]$ forces monochrome $3$-AP. Roth says you don't need to color all numbers — single color class of density $\delta>0$ already forces $3$-AP inside itself. Density version strictly stronger than coloring version for $k=3$.

### Why It's Hard: Naive Count Fails

Let $A\subset[1,N]$, $\left|A\right|=\delta N$. Count $3$-APs including trivial $d=0$:

$$\displaystyle T_{3}(A)=\sum_{x,d}1_{A}(x)1_{A}(x+d)1_{A}(x+2d)=N^{2}\sum_{r}\left|\widehat{1_{A}}(r)\right|^{2}\widehat{1_{A}}(-2r)$$

Fourier identity.

**What is $T_{3}$?** $\displaystyle T_{3}$ counts pairs $\left(x,d\right)$ with $x,x+d,x+2d\in A$. For each $a=x$, $d$ arbitrary $\left(-N\le d\le N\right)$, includes $d=0$ gives $N$ trivial APs $a,a,a$. Nontrivial when $d\neq0$. $N^{2}$ choices $\left(x,d\right)$ total.

**If $A$ random density $\delta$:** Choose each $n\in[1,N]$ independently with probability $\delta$. Then $\displaystyle\mathbb{E}\left[1_{A}(x)1_{A}(x+d)1_{A}(x+2d)\right]=\delta^{3}$ for $d\neq0$ distinct points. So

$$\displaystyle \mathbb{E}\left[T_{3}(A)\right]\approx\delta^{3}N^{2}$$

Many — $N^{2}$ vs $N$ — so random set expects $\approx\delta^{3}N^{2}$ progressions, e.g., $\delta=\tfrac{1}{10}$, $N=10^{6}$ expects $10^{12}\cdot10^{-3}=10^{9}$ $3$-APs. So random dense set has many APs.

**Why naive expectation not proof?** Structured set could conspire to cancel.

Example: evens only — still many APs, not counterexample. Need set where Fourier phases cancel to make $T_{3}$ small despite large $\delta$.

Write balanced function:

$$\displaystyle f=1_{A}-\delta1_{[1,N]}$$

mean zero, $\displaystyle\widehat{f}(0)=0$.

Expand:

$$\displaystyle T_{3}(A)=\sum_{x,d}\left(\delta+f(x)\right)\left(\delta+f(x+d)\right)\left(\delta+f(x+2d)\right)$$

Main term $\displaystyle\delta^{3}\sum_{x,d}1=\delta^{3}N^{2}$.

Cross terms involve $\displaystyle\sum_{r\neq0}\left|\widehat{f}(r)\right|^{2}\widehat{f}(-2r)$ etc. So

$$\displaystyle T_{3}(A)=\delta^{3}N^{2}+ N^{2}\sum_{r\neq0}\left|\widehat{1_{A}}(r)\right|^{2}\widehat{1_{A}}(-2r)+\text{lower}$$

If $A$ has no nontrivial $3$-AP, then $T_{3}(A)=N$ trivial only — essentially $0$ compared to $\delta^{3}N^{2}$. So sum over $r\neq0$ must be $\approx-\delta^{3}N^{2}$ to cancel main term.

Hence some $\left|\widehat{f}(r)\right|$ must be large — cannot have all $\left|\widehat{f}(r)\right|$ small.

Formally:

$$\displaystyle \exists r\neq0:\;\left|\widehat{f}(r)\right|\gg\delta^{2}$$

with $\displaystyle\widehat{f}(r)=\dfrac{1}{N}\sum_{x=1}^{N}f(x)e^{-2\pi i r x/N}$.

**Plain meaning:** Large Fourier coefficient at frequency $r$ means $A$ correlates with linear phase $\displaystyle e^{2\pi i r x/N}$ — wave with period $\displaystyle N/r$.

$$\displaystyle \left|\sum_{x\in A}e^{2\pi i r x/N}\right|\gg\delta^{2}N$$

Random set has $\displaystyle\left|\sum_{x\in A}e^{2\pi i r x/N}\right|\approx\sqrt{\delta N}\ll\delta^{2}N$ — flat spectrum, all frequencies small $O(\sqrt{N})$.

No $3$-APs forces spike: some $r\neq0$ where sum large — bias. $A$ prefers regions where phase $\approx1$, avoids where $\approx-1$.

Think: sprinkle dots randomly on circle — no direction stands out. If dots cluster in arc, Fourier at corresponding frequency spikes.

So strategy: no APs $\implies$ bias $\implies$ denser on subprogression $\implies$ iterate — Roth density increment.

This is why Fourier needed — counting alone $\delta^{3}N^{2}$ heuristic says many APs, but need to rule out conspiratorial cancellation. Fourier converts cancellation into structural bias that can be exploited.

### The Proof: Density Increment via Fourier — Plain Terms

Three ideas now standard:

**Idea 1: Fourier bias.**

Let $f=1_A-\delta1_{[1,N]}$ balanced function — mean zero, positive where $A$ denser than average, negative where sparser.

If $A$ has no nontrivial 3-AP, then $T_3(A)\approx0$ ignoring trivial $N$ APs with $d=0$, but main term from average $\delta$ contributes $\delta^3 N^2$. To cancel $\delta^3 N^2$ to near 0, some Fourier coefficient must be large:

$$\exists r\neq0:\;|\hat f(r)|\gg\delta^2.$$

Large Fourier coefficient means $A$ correlates with linear phase $e^{2\pi i r x/N}$ — wave. $A$ prefers places where wave phase near 1, avoids where phase -1. Not uniform — clusters in arithmetic sense, e.g., prefers certain residues mod $q$.

Analogy: If you sprinkle dots randomly on circle, no direction stands out. If Fourier spike, dots cluster in some arc — bias.

**Idea 2: From bias to density increment.**

Large Fourier coefficient implies $A$ significantly denser on some long arithmetic progression $P\subset[1,N]$ length $N'\ge N^c$.

Precisely: exists $P$, $|P|\ge N^{c}$ with

$$\dfrac{|A\cap P|}{|P|}\ge\delta + c'\delta^2$$

Gain $\Omega(\delta^2)$ density by restricting to $P$.

Why? $e^{\tfrac{2\pi i r x}{N}}$ roughly constant on progression with step $q$ where $\dfrac{r q}{N}$ small mod 1. Pigeonhole over $q$ — Dirichlet. Densest subprogression where phase near 1 must have higher density.

Intuition: If $A$ clusters mod $q$, look at densest residue class mod $q$ — it has higher density than average. If $A$ clusters on intervals, look at densest interval.

**Idea 3: Iterate to contradiction.**

Now repeat. $A_1=A\cap P$, rescaled to $[1,N']$. Has density $\delta_1\ge\delta+c'\delta^2$ and still no 3-AP — subset of AP-free set still AP-free.

Apply again: get $P_2$, density $\delta_2\ge\delta_1+c'\delta_1^2$, etc.

Density increases by at least $\Omega(\delta^2)$ each step, so after $O\left(\dfrac{1}{\delta}\right)$ steps density would exceed 1 — impossible, since density $\le1$.

Therefore process must stop because we found 3-AP before that.

$O\left(\dfrac{1}{\delta}\right)$ steps, each shrinking $N$ to about $\sqrt N$ (or $N^c$), yields $N$ must be at least $\exp\left(\exp\left(O\left(\dfrac{1}{\delta}\right)\right)\right)$ to run that many steps, giving $r_3(N)\ll \dfrac{N}{\log\log N}$.

This density increment strategy — if no pattern, then denser on substructure, iterate — is template for Szemerédi, Gowers, Green-Tao.

Same meta-theorem: disorder budget finite. Budget = $\dfrac{1}{\delta}$. Each step without pattern spends budget by increasing density. Cannot increase forever.

### How Large Can AP-Free Set Be? Bounds War

Let $r_{3}(N)$ be max size of $3$-AP-free subset of $$ — no $a, a+d, a+2d$ with $d\neq0$ inside.[1][N]

Roth proved $\displaystyle\frac{r_{3}(N)}{N}\to0$. Question: how fast?

**Lower bound — Behrend 1946: how to avoid**

Construction:

1. Cube $\left\{0,\dots,m-1\right\}^{d}$.
2. Sphere layer $\displaystyle S_{R}= \left\{ x : \sum_{i=1}^{d} x_{i}^{2}=R \right\}$.
3. No $3$-AP on sphere: if $x+z=2y$ and $\left\|x\right\|_{2}^{2}=\left\|z\right\|_{2}^{2}=\left\|y\right\|_{2}^{2}=R$, then $\left\|\tfrac{x+z}{2}\right\|_{2}<R$ unless $x=z$ by strict convexity. So distinct $x,y,z$ in AP cannot all lie on same sphere.
4. Choose densest $R$ — $\displaystyle\left|S_{R}\right|\ge \dfrac{m^{d}}{d m^{2}}$.
5. Map to integers $\displaystyle n = \sum_{i=1}^{d} x_{i} (2m)^{i-1}$ base $2m$ — no carries, so $x+z=2y \iff n_{x}+n_{z}=2n_{y}$. AP-free in cube $\implies$ AP-free in $\mathbb{Z}$.

Optimizing $\displaystyle d\approx\sqrt{\log N}$ gives:

$$\displaystyle r_{3}(N)\ge N\cdot\exp\!\left(-C\sqrt{\log N}\right)=\dfrac{N}{\exp\!\left(C\sqrt{\log N}\right)} $$

So $\displaystyle r_{3}(N)=N^{1-o(1)}$ — almost linear. For $N=10^{6}$, $\displaystyle\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}\approx\tfrac{N}{50}$ — still $2\%$, no $3$-AP.

Elkin 2008:

$$\displaystyle r_{3}(N)\ge N\cdot\dfrac{\log^{1/4}N}{\exp\!\left(C\sqrt{\log N}\right)} $$

extra $\log^{1/4}N$ from better sphere packing.

**Upper bounds — $70$ years pushing $\log\log$ down to $\log$:**

- **Roth 1953:**

$$\displaystyle r_{3}(N)\ll\dfrac{N}{\log\log N}$$

One large Fourier coefficient $\left|\widehat{f}(r)\right|\gg\delta^{2}$ gives increment $\displaystyle\delta\to\delta+c'\delta^{2}$ on $P$, $\left|P\right|\ge N^{c}$. After $\displaystyle O\!\left(\tfrac{1}{\delta}\right)$ steps density $>1$.

- **Szemerédi & Heath-Brown:**

$$\displaystyle r_{3}(N)\ll\dfrac{N}{\left(\log N\right)^{c}}$$

for some small $c>0$ — Bohr sets $\displaystyle B(S,\rho)=\left\{x:\left\|\dfrac{rx}{N}\right\|<\rho\;\forall r\in S\right\}$ instead of progressions.

- **Bourgain 1999-2008:**

$$\displaystyle r_{3}(N)\ll N\cdot\dfrac{\sqrt{\log\log N}}{\sqrt{\log N}} \quad\text{and}\quad N\cdot\dfrac{\left(\log\log N\right)^{2}}{\left(\log N\right)^{2/3}}$$

refined restriction, almost-periodicity.

- **Sanders 2011:**

$$\displaystyle r_{3}(N)\ll N\cdot\dfrac{\left(\log\log N\right)^{5}}{\log N}$$

almost $\displaystyle\frac{N}{\log N}$ — Croot-Sisask lemma.

- **Bloom & Sisask 2020 breakthrough:**

$$\displaystyle r_{3}(N)\ll\dfrac{N}{\left(\log N\right)^{1+c}} \qquad c>0$$

Broke $\displaystyle\frac{N}{\log N}$ barrier.

Why new? Old: one large coefficient $\implies$ increment $\displaystyle\delta\to\delta+\Omega\!\left(\delta^{2}\right)$. Need $\displaystyle O\!\left(\tfrac{1}{\delta}\right)$ steps.

New: many large coefficients, large spectrum $\displaystyle\Delta_{\eta}(f)=\left\{r:\left|\widehat{f}(r)\right|\ge\eta\right\}$ has additive structure — $\Delta+\Delta$ small. Spectral boosting uses $\displaystyle\left\langle 1_{A}*1_{A}, f\right\rangle$ to boost $\eta$. Almost-periodicity: exists measure $\mu$ on Bohr set with $\displaystyle\left\|1_{A}* \mu - 1_{A}\right\|_{2}$ small, so density increment $\displaystyle\delta\to\delta+\Omega\!\left(\delta\right)$ on much larger Bohr set — loses only $\exp\!\left(-O\!\left(\tfrac{1}{\delta}\right)\right)$ not $N^{c}$.

So $\displaystyle O\!\left(\log\tfrac{1}{\delta}\right)$ steps $\implies$ $\displaystyle\left(\log N\right)^{1+c}$.

**Why $\displaystyle\frac{N}{\log N}$ threshold matters for Erdős:**

Erdős conjecture: $\displaystyle\sum_{a\in A}\tfrac{1}{a}=\infty\implies A$ contains $3$-AP.

If $\displaystyle\left|A\cap[1,N]\right|\approx\dfrac{N}{\log N}$ then $\displaystyle\sum_{a\le N}\tfrac{1}{a}\sim\int^{N}\dfrac{d\left|A\cap[1,t]\right|}{t}\sim\dfrac{\log N}{\log N}\to\infty$ diverges — harmonic $\displaystyle\sum\tfrac{1}{n\log n}$ diverges.

If $\displaystyle\left|A\cap[1,N]\right|\ll\dfrac{N}{\left(\log N\right)^{1+c}}$ then $\displaystyle\sum\tfrac{1}{a}\ll\sum\dfrac{1}{n\left(\log n\right)^{1+c}}<\infty$ — integral $\displaystyle\int^{\infty}\dfrac{dx}{x\left(\log x\right)^{1+c}}=\dfrac{1}{c\left(\log x\right)^{c}}<\infty$.

Hence Bloom-Sisask: any $3$-AP-free $A$ has $\displaystyle\sum\tfrac{1}{a}<\infty$, so divergent reciprocal sum forces $3$-AP — $k=3$ case of Erdős.

For $k\ge4$, best lower bound still $\displaystyle\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}$, best upper $\displaystyle\frac{N}{\left(\log N\right)^{c}}$ — huge gap, requires $\displaystyle U^{k}$ norms, nilsequences, far beyond.

### Why Bloom-Sisask Matters: Erdős $3,000 Conjecture

Erdős offered prizes:

> **Erdős Conjecture on APs:** If $A\subset\mathbb{N}$ satisfies $\displaystyle\sum_{a\in A}\dfrac{1}{a}=\infty$, then $A$ contains $k$-term APs for every $k$.

Divergent reciprocal sum means not too sparse. Primes satisfy since $\displaystyle\sum\dfrac{1}{p}=\infty$ harmonic over primes diverges like $\log\log N$.

Connection to $r_3(N)$:

If $r_3(N)\approx \dfrac{N}{\log\log N}$, set can be 3-AP-free and still have divergent reciprocal sum, because $\displaystyle\sum \dfrac{1}{(\tfrac{N}{\log\log N})^{-1}}$ diverges? Let's see: size of AP-free set at $N$ about $\dfrac{N}{\log\log N}$ → density $\dfrac{N}{\log\log N}$ → sum of reciprocals $\displaystyle\sum \dfrac{1}{a}$ about $\displaystyle\int \dfrac{dN}{N\log\log N}$? Actually integral of density $\dfrac{dN}{N}$? For set with $|A\cap[1,N]|\sim \dfrac{N}{\log\log N}$, sum $\displaystyle\sum_{a\le N}\dfrac{1}{a}\sim\int^N \left(\tfrac{1}{t}\right) d|A\cap[1,t]|\sim\dfrac{\log N}{\log\log N}\to\infty$ diverges. So Roth bound says nothing about Erdős.

If $r_3(N)\ll \dfrac{N}{(\log N)^{1+c}}$, then any 3-AP-free $A$ has $\displaystyle\sum \dfrac{1}{a}<\infty$ because $\displaystyle\sum N^{-1}(\log N)^{-1-c}$ converges — integral test: $\displaystyle\int \dfrac{dx}{x(\log x)^{1+c}}$ converges for $c>0$.

Bloom-Sisask therefore proved:

> **$k=3$ case of Erdős conjecture true.** Any set with divergent reciprocal sum contains 3-term AP.

First unconditional progress on Erdős for any $k\ge3$. $\dfrac{N}{\log N}$ was psychological barrier — exactly threshold where harmonic series switches from divergence to convergence.

For $k\ge4$, Erdős conjecture remains wide open. Even $k=4$ would require $r_4(N)\ll \dfrac{N}{(\log N)^{1+c}}$, far beyond current technology — best $r_4(N)$ bounds still $\dfrac{N}{(\log N)^c}$.

### From Roth to Szemerédi to Green-Tao

- **Roth $k=3$:** Fourier + density increment. Needs one large Fourier coefficient — linear phase $\displaystyle e^{2\pi i r x/N}$.
- **Szemerédi $k\ge4$, 1975:** Roth Fourier fails — $4$-APs need quadratic Fourier. Szemerédi used pure combinatorics, invented Regularity Lemma — partitions graph into random-like pieces. Vastly more complex.
- **Gowers $k\ge4$, 2001:** Extended Roth analytic approach by inventing higher-order Fourier analysis and Gowers uniformity norms $\displaystyle U^{k}$. Set with no $4$-AP must correlate with quadratic phase $\displaystyle e^{2\pi i\left(\alpha n^{2}+\beta n\right)}$, not just linear. Won Fields Medal.
- **Green-Tao 2004:** Needed Gowers $\displaystyle U^{3}$ norm and relative version to handle primes — relative Szemerédi inside pseudorandom majorant.

**Why Roth fails for $k\ge4$:**

Count $4$-APs:

$$\displaystyle T_{4}(A)=\sum_{x,d}1_{A}(x)1_{A}(x+d)1_{A}(x+2d)1_{A}(x+3d)=N^{2}\sum_{r,s}\widehat{1_{A}}(r)\widehat{1_{A}}(s)\widehat{1_{A}}(-2r-s)\widehat{1_{A}}(r+2s)$$

Four linear phases not enough — quadratic phases $\displaystyle e^{2\pi i\alpha x^{2}}$ are uniform in $\displaystyle U^{2}$ — all linear Fourier coefficients $\displaystyle\left|\widehat{f}(r)\right|$ small — but still cause many $4$-APs to be missing or overcounted.

Example: $A=\left\{x:\left\| \alpha x^{2}\right\|<\delta\right\}$ — level set of quadratic phase. Then $\displaystyle\left|\widehat{1_{A}}(r)\right|=o(N)$ for all $r\neq0$ — Fourier uniform, looks random to Roth — but $\displaystyle\left\|1_{A}\right\|_{U^{3}}$ large — contains many $4$-APs structure.

So need higher-order uniformity.

**Szemerédi 1975:**

Proved for all $k$,

$$\displaystyle \bar d(A)>0\implies A\text{ contains }k\text{-AP}$$

Equivalently $\displaystyle r_{k}(N)=o(N)$.

Method: Purely combinatorial, no Fourier. Invented Szemerédi Regularity Lemma — any graph can be partitioned into $\displaystyle O_{\epsilon}(1)$ pieces where between pieces edges random-like $\displaystyle\left|e(X,Y)-\delta|X||Y|\right|<\epsilon|X||Y|$.

Used to build hypergraph regularity for $k$-AP hypergraph. Proof enormous — $N(\delta,k)$ tower of exponentials of height $O(1/\delta)$ — $\displaystyle\exp^{(O(1/\delta))}(1)$.

Gives no explicit good bound, but qualitative.

**Gowers 2001 — Fourier revived:**

Invented Gowers uniformity norms:

$$\displaystyle \left\|f\right\|_{U^{2}}^{4}=\mathbb{E}_{x,h_{1},h_{2}}f(x)\overline{f(x+h_{1})f(x+h_{2})}f(x+h_{1}+h_{2})$$

$$\displaystyle \left\|f\right\|_{U^{3}}^{8}=\mathbb{E}_{x,h_{1},h_{2},h_{3}}\prod_{\omega\in\{0,1\}^{3}}C^{|\omega|}f(x+\omega\cdot h)$$

In general $\displaystyle\left\|f\right\|_{U^{k}}$ measures correlation with degree $\displaystyle(k-1)$ polynomial phases.

- $\displaystyle\left\|f\right\|_{U^{2}}$ small $\iff$ all $\displaystyle\left|\widehat{f}(r)\right|$ small — linear uniform.
- $\displaystyle\left\|f\right\|_{U^{3}}$ small $\iff$ no correlation with quadratic phases $\displaystyle e^{2\pi i(\alpha n^{2}+\beta n)}$.

**Inverse theorem:** If $\displaystyle\left\|f\right\|_{U^{k}}\ge\eta$, then $\displaystyle f$ correlates with $(k-1)$-step nilsequence — generalized polynomial phase on nilmanifold.

For $k=3$, nilsequence = linear phase $\displaystyle e^{2\pi i r x/N}$ — Roth.

For $k=4$, nilsequence = quadratic phase $\displaystyle e^{2\pi i(\alpha x^{2}+\beta x)}$ plus bracket polynomials — Gowers.

Proof then: If $A$ no $k$-AP, balanced $f$ has large $\displaystyle U^{k-1}$ norm → correlates with nilsequence → density increment on Bohr-nil Bohr set → iterate. Gives

$$\displaystyle r_{k}(N)\ll\dfrac{N}{\left(\log\log N\right)^{c_{k}}}$$

with explicit $c_{k}=2^{-2^{k+9}}$ — first reasonable bound since Szemerédi.

Fields Medal 1998? Actually 1998? No, Gowers Fields 1998 for earlier, but this work core.

**Green-Tao 2004 — relative version:**

Need Roth/Gowers for primes density $0$. Primes $\displaystyle\pi(N)\sim\dfrac{N}{\log N}$ — $\displaystyle\delta(N)=\tfrac{1}{\log N}\to0$, so Szemerédi not apply.

Idea: find pseudorandom majorant $\displaystyle\nu$ with

1. $\displaystyle 0\le c\cdot1_{prime}\le\nu$,
2. $\displaystyle\mathbb{E}\nu=1+o(1)$,
3. $\displaystyle\left\|\nu-1\right\|_{U^{k-1}}=o(1)$ — $\nu$ looks like $1$ for $k$-AP counts.

Then prove **relative Szemerédi:** If $\displaystyle0\le f\le\nu$ and $\displaystyle\mathbb{E}f\ge\delta>0$, then $f$ contains $\displaystyle\ge c(\delta,k)N^{2}$ $k$-APs.

Ingredients: generalized von Neumann — if $\displaystyle\left\|f\right\|_{U^{k-1}}$ small relative to $\nu$, $k$-AP count $\approx\delta^{k}N^{2}$; dense model theorem — any $0\le f\le\nu$ has model $\displaystyle\tilde f$ with $0\le\tilde f\le1$ and $\displaystyle\left\|f-\tilde f\right\|_{U^{k-1}}=o(1)$; then apply Gowers inverse to $\tilde f$.

For primes, after $W$-trick $W=\prod_{p\le w}p$, define

$$\displaystyle \tilde f(n)=\dfrac{\phi(W)}{W}\log N\cdot1_{prime}(Wn+1)$$

mean $\approx1$, bounded by Selberg sieve $\displaystyle\nu$, so relative Szemerédi gives $k$-APs in $Wn+1$ primes → $k$-APs in primes.

Thus Roth seed:

> **If no pattern, then bias, then denser substructure, iterate**

universal template.

In Ramsey terms: $\displaystyle r_{3}(N)$ inverse of $\displaystyle W(2,3)$ in density form. $\displaystyle W(2,3)=9$ says $2$-coloring of $\displaystyle[1,9]$ forces monochrome $3$-AP. Roth says even one color class of positive density $\displaystyle\delta>0$ forces it — no need to color rest. Bridge from pigeonhole coloring to analytic density, without it Szemerédi and Green-Tao would not exist.

## Behrend's Construction — The Limit of How Far You Can Avoid Order

If Roth's theorem says "dense sets must contain a 3-term AP," Behrend's construction says "you can be _almost_ dense and still avoid one." It is the ultimate counterexample — the lower bound that sandwiches $r_3(N)$ and proves Roth's theorem cannot be improved too far.

Let
$$r_3(N) = \max\{|A|: A\subset\{1,\dots,N\},\, A\text{ contains no }a,a+d,a+2d\text{ with }d\neq0\}.$$

- Roth gives upper bound: $r_3(N)$ cannot be too big, otherwise 3-AP forced.
- Behrend gives lower bound: $r_3(N)$ can be at least this big while still AP-free.

Together:
$$N \cdot \exp(-C\sqrt{\log N}) \le r_3(N) \le \dfrac{N}{(\log N)^{1+c}}$$

For 62 years Behrend's lower bound was unbeaten. It shattered the pre-1946 intuition that AP-free sets must be polynomially small.

### The Intuition Before Behrend: Power-Law Conjecture

Erdős and Turán in the 1930s conjectured that any 3-AP-free set must be tiny, like $N^{0.9}$ or $N^{1-\epsilon}$ or even $N / (\log N)^C$ — a power-law saving over $N$.

Why they thought this: The easy greedy construction — take numbers with no digit 2 in base 3, the Stanley sequence — gives $N^{\log_2 3} \approx N^{0.63}$ and is 3-AP-free. That looks polynomial.

Behrend in 1946 destroyed this. He showed you can keep $N^{1-o(1)}$ numbers — $N$ divided by something growing slower than any $N^{\epsilon}$ — and still avoid 3-APs.

Compare as $N$ grows:

| $N$        | Power law guess $N^{0.9}$ | Behrend $N \cdot \exp(-\sqrt{\log N})$ | Density                                                    |
| :--------- | :------------------------ | :------------------------------------- | :--------------------------------------------------------- |
| $10^4$     | 3,981                     | ~1,800                                 | 18%                                                        |
| $10^{10}$  | $10^9$                    | $3.1\times10^8$                        | 3.1%                                                       |
| $10^{20}$  | $10^{18}$                 | $6.7\times10^{17}$                     | 6.7%                                                       |
| $10^{100}$ | $10^{90}$                 | $3.8\times10^{95}$                     | $10^{-5}$ fraction, but $10^5$ times larger than $N^{0.9}$ |

$\exp(-\sqrt{\log N})$ decays to $0$ slower than any $N^{-\epsilon} = \exp(-\epsilon\log N)$, because $\sqrt{\log N} \ll \epsilon \log N$. So Behrend sets are eventually _vastly_ larger than any power-law bound. Erdős-Turán power-law conjecture was false.

### The Construction: Spheres Have No 3-Term Lines

Behrend's genius was to use geometry.

**Key geometric fact:** A straight line can intersect a sphere in at most 2 points. If you have three distinct collinear points $x,y,z$ with $y$ midpoint of $x$ and $z$, they cannot all lie on the same sphere centered at origin, because then $\|x\|^2 = \|y\|^2 = \|z\|^2$ and $\|y\|^2 = \|(x+z)/2\|^2 < (\|x\|^2+\|z\|^2)/2$ by strict convexity of $L^2$ norm unless $x=z$.

So a sphere is 3-AP-free.

**Step 1: Grid in high dimensions.**

Fix $d$ and $m$. Consider the grid
$$G = \{0,1,\dots,m-1\}^d \subset \mathbb{Z}^d$$
Size $|G| = m^d$.

For $x\in G$, define $S(x) = \displaystyle\sum_{i=1}^d x_i^2 = \|x\|^2$, which ranges from $0$ to $d(m-1)^2$.

There are only $d m^2$ possible values of $S$, but $m^d$ points. By pigeonhole, some radius $R$ contains many points:

$$\exists R: |\{x\in G: \|x\|^2 = R\}| \ge \dfrac{m^d}{d m^2} = \dfrac{m^{d-2}}{d}$$

This set $T_R$ lies on a sphere and thus has no 3-term AP in $\mathbb{Z}^d$ — because if $x+z=2y$, then $x,y,z$ collinear with $y$ midpoint, impossible on sphere.

**Step 2: Map to integers without creating APs.**

Encode $x = (x_1,\dots,x_d)$ as a base-$(2m)$ number:
$$\phi(x) = \displaystyle\sum_{i=1}^d x_i (2m)^{i-1}$$

Base $2m$ is larger than $2(m-1)$, so addition in $\mathbb{Z}^d$ has no carries when adding two such numbers: $\phi(x)+\phi(z) = 2\phi(y)$ iff $x+z=2y$ coordinate-wise. Since $T_R$ has no solution to $x+z=2y$ with $x\neq z$, $\phi(T_R)$ has no 3-term AP in integers.

So $A = \phi(T_R) \subset [0, (2m)^d)$ is AP-free with size $\ge m^{d-2}/d$.

**Step 3: Optimize $d$ and $m$.**

We have $N \approx (2m)^d$. So $\log N \approx d\log(2m)$. We have $|A| \ge m^{d-2}/d = N \cdot \dfrac{(2m)^{-2}}{d} \cdot m^d / (2m)^d ...$ More careful: $m^{d-2}/d = (2m)^d \cdot \dfrac{1}{d(2m)^2 2^d}$? Let's optimize.

Take $m = \exp(\sqrt{\log N})$? Standard optimization: choose $d \approx \sqrt{\log N}$ and $m \approx \exp(\sqrt{\log N})$. Then $(2m)^d = N$ and $m^{d-2}/d = N \cdot \exp(-O(\sqrt{\log N}))$.

Precise bound Behrend proved:

$$r_3(N) \ge N \cdot \exp(-C\sqrt{\log N})$$

for some absolute constant $C$ (original $C=2\sqrt{2}+o(1)$).

### Elkin's Tweak (2008) — The Thick Shell

For 62 years no one beat Behrend. The problem: Behrend uses an _infinitely thin_ sphere — only points with _exactly_ $\|x\|^2=R$. Most points in the cube lie near but not exactly on that radius.

Elkin's idea: Use a _thick_ spherical shell $R \le \|x\|^2 \le R+\delta$ — a doughnut layer. It contains far more points, about $\delta$ times more. But now a line _can_ intersect a thick shell in 3 points — you lose the sphere property.

Elkin's innovation: Inside the thick shell, most triples that form a 3-AP are still rare. He used probabilistic method and careful counting: pick random subset of shell where you delete one point from each 3-AP inside shell. Since number of 3-APs in shell is much smaller than shell size when $\delta$ is small ($\approx \sqrt{d}$), you delete little.

This salvages extra points. Result:

$$r_3(N) \ge C_1 \dfrac{N \log^{1/4} N}{\exp(2\sqrt{2}\sqrt{\log N})}$$

for $C_1>0$. Elkin gained a factor $\approx \sqrt{\log N} = (\log N)^{1/4}$? Actually $\log^{1/4} N$ extra. In his form:

$$r_3(N) \ge \dfrac{N}{\exp(-C\sqrt{\log N})} \cdot \dfrac{\sqrt{\log N}}{2^{...}}$$

Green & Wolf (2010) refined to $C=2\sqrt{2\log2}$ improvement.

The improvement is tiny — $\sqrt{\log N}$ vs $\exp(\sqrt{\log N})$ — but conceptually huge: it showed Behrend was not optimal, and thick shells could be made to work.

### Why It Defines the Boundary for Roth and Szemerédi

Behrend tells us:

> You cannot prove $r_3(N) \le N^{0.99}$. You cannot even prove $r_3(N) \le \dfrac{N}{(\log N)^{100}}$. Because Behrend sets of size $\dfrac{N}{\exp(C\sqrt{\log N})}$ are AP-free and larger than $\dfrac{N}{(\log N)^{100}}$ for large $N$.

So Roth's theorem $r_3(N) \ll \dfrac{N}{\log\log N}$ was far from optimal, but Behrend shows you can never push it down to $N^{1-\epsilon}$. The true $r_3(N)$ lives in the strange intermediate regime $N^{1-o(1)}$.

This is why Szemerédi's regularity lemma was necessary. If AP-free sets were small and structured like $N^{0.9}$, you could find APs by simple pigeonhole. Because Behrend showed they can be large, pseudorandom, and sphere-like — looking random but with hidden quadratic structure — Szemerédi needed a decomposition that separates _all_ large sets into structured + pseudorandom pieces. The regularity lemma is forced by Behrend-type examples.

In Fourier terms: Behrend sets have _no_ large linear Fourier coefficient — they are $U^2$-uniform — but they _do_ have large $U^3$ quadratic bias (they live on a sphere). This is why Roth's linear Fourier analysis cannot prove $r_3(N) \ll \dfrac{N}{\exp(\sqrt{\log N})}$; you need quadratic Fourier analysis, which is exactly what Bloom-Sisask and higher-order methods do.

### The Behrend-Roth Gap and Bloom-Sisask Closure

For 70 years:

- Lower: $N \exp(-C\sqrt{\log N})$
- Upper: $\dfrac{N}{\log\log N}$, then $\dfrac{N \sqrt{\log\log N}}{\sqrt{\log N}}$, then $\dfrac{N (\log\log N)^5}{\log N}$

Massive gap: $\exp(\sqrt{\log N})$ vs $\log N$.

Behrend says upper bound can never go below $N\exp(-C\sqrt{\log N})$. Roth says it must go to $0$.

Bloom & Sisask (2020) closed half the gap: $r_3(N) \ll \dfrac{N}{(\log N)^{1+c}}$ with $c>0$. This is first time upper bound is $\dfrac{N}{(\log N)^{1+c}}$, i.e., smaller than $\dfrac{N}{\log N}$.

Why $\dfrac{N}{\log N}$ is threshold? Because $\displaystyle\sum_{n\in A} 1/n$ diverges if $|A\cap[1,N]| \approx \dfrac{N}{\log N}$ (like primes). Bloom-Sisask implies any 3-AP-free set has convergent reciprocal sum — proving $k=3$ case of Erdős's conjecture.

Behrend's construction is thus the compass: it tells us how far we _can_ hope to push. Until we match $N\exp(-C\sqrt{\log N})$, we haven't finished. The true $r_3(N)$ is conjectured to be closer to Behrend than to Roth — most experts believe $r_3(N) = N \exp(-\Theta(\sqrt{\log N}))$.

In Ramsey language: Behrend is the construction for $R_3$, like the 5-cycle is for $R(3,3)$. It is the maximal disorder that avoids order, and its size dictates how sophisticated your order-finding tool must be.
