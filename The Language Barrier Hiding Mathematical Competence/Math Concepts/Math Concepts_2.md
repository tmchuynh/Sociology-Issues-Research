## Van der Waerden's Theorem — The Root of Arithmetic Ramsey Theory

Where Ramsey finds cliques in graphs and Erdős–Szekeres finds convex polygons in point sets, van der Waerden finds regular patterns in colorings of numbers. Oldest Ramsey-type theorem 1927, archetypal statement that complete disorder impossible.

> **Van der Waerden 1927:** For any finite $r$ colors and desired length $k$, exists minimum $W(r,k)$ such that for any $N\ge W(r,k)$, every $r$-coloring of $\{1,\dots,N\}$ contains monochromatic arithmetic progression length $k$.

Paint integers red/blue however cleverly to break equally-spaced patterns. Paint long enough, you lose — long one-color progression forced.

### Key Concepts — Van der Waerden

**Coloring:** $c:\{1,\dots,N\}\to\{1,\dots,r\}$.

Function assigning each integer a color label. For $r=2$, Red/Blue.

Think painting houses $1..N$ red/blue. No rule, any assignment allowed — you're adversary trying to avoid pattern.

**AP:** Arithmetic progression $a, a+d, \dots, a+(k-1)d$.

- $a$ start, $d>0$ common difference, $k$ length.
- $3,6,9$ = $a=3,d=3,k=3$.
- $4,11,18,25$ = $a=4,d=7,k=4$.
- Difference $d$ not required to be small — can be large jump.

Equal spacing is order: points line up arithmetic, not geometric.

**Monochromatic:** All $k$ terms same color.

$c(a)=c(a+d)=\dots=c(a+(k-1)d)$.

You tried to color to break APs, but this $k$-set slipped through one color.

**Van der Waerden number $W(r,k)$:** Threshold where avoidance ends.

> Least $N$ such that _every_ $r$-coloring of $\{1,\dots,N\}$ contains monochromatic $k$-AP.

Two sides:

- $W-1$ avoidable: exists at least one coloring of $\{1,\dots,W-1\}$ with _no_ monochromatic $k$-AP — maximal disorder example. For $W(2,3)=9$, that's $RRBBRRBB$ on $1..8$.

- $W$ unavoidable: no coloring of $\{1,\dots,W\}$ avoids. Every attempt forces $k$-AP. For $W(2,3)=9$, every red/blue of $1..9$ yields red $a,a+d,a+2d$ or blue.

> **Party version:** $W(r,k)$ = number of houses on street you must paint with $r$ colors before $k$ equally-spaced houses of one color become unavoidable, no matter how clever you paint.

It's Ramsey number for integer line — host structure is $\{1,\dots,N\}$ with AP hyperedges, colors try to avoid monochromatic hyperedge, $W$ is when host large enough that avoidance impossible.

Like $R(3,3)=6$ is threshold for monochromatic triangle in complete graph, $W(2,3)=9$ is threshold for monochromatic 3-AP on line, $N(4)=5$ threshold for convex quadrilateral in point set, $HJ(n,c)$ threshold for combinatorial line in cube.

All measure same thing: disorder budget.

### Why $W(2,3)=9$ — Only Case You Can See

This is van der Waerden's $R(3,3)=6$ — only number you can prove by hand, and it contains whole general proof idea: local constraints propagate until collision.

Goal: 2 colors, avoid monochromatic 3-term $a, a+d, a+2d$.

Forcing rule: If $a,b$ same color, then $2b-a$ must be opposite color, else $a,b,2b-a$ is monochromatic AP with difference $d=b-a$.

#### Part A: $W(2,3)>8$ — 8 Can Avoid

$$1:R,2:R,3:B,4:B,5:R,6:R,7:B,8:B = RRBBRRBB$$

Check reds $\{1,2,5,6\}$:

- $d=1$: $1,2,3$ needs 3 — 3 is B, safe. $5,6,7$ needs 7 — B safe.
- $d=2$: $1,3,5$ needs 3 — B safe. $2,4,6$ needs 4 — B safe.
- $d=3$: $2,5,8$ needs 8 — B safe. $1,4,7$ needs 7 but 4 is B.
- $d=4$: $1,5,9$ out of range.

No red $a,a+d,a+2d$ fully red.

Blues $\{3,4,7,8\}$ symmetric: $3,5,7$ needs 5 R safe, $4,6,8$ needs 6 R safe.

So 8 avoids. Pattern = blocks of 2: $RRBBRRBB$ — you avoid 3-AP by never making run of 3, and offsetting blocks so $a,a+d,a+2d$ always hits opposite block.

Thus $W(2,3)$ at least 9.

#### Part B: $W(2,3)\le9$ — 9 Forces

We need show _every_ 2-coloring of $1..9$ forces monochromatic 3-AP, not just $RRBBRRBB$ extended.

Brute casework but organized by forcing:

Assume coloring of $1..8$ avoids 3-AP. WLOG $1=R$ by symmetry.

Consider middle point 5 — it participates in many APs: $1,5,9$ ; $2,5,8$ ; $3,5,7$ ; $4,5,6$.

If we try to 2-color $1..8$ without 3-AP, constraints propagate:

- $1:R$ and $2:R$ → $3$ must be $B$, else $1,2,3$ red.
- $3:B$ and $4$? If $4=R$, then $2,3,4$? 2 R,3 B no. Let's systematic search — classic proof enumerates 8 avoiding colorings of length 8 — there are essentially 2 types up to swap colors and reflection: $RRBBRRBB$ and $RBRBR...$ variations? Actually complete enumeration shows only 4 colorings of $1..8$ avoid 3-AP up to symmetry, all end with $...BB$.

Simplified argument for $RRBBRRBB$ case you wrote:

Extend to 9:

- If $9=R$: then $1,5,9$ with $d=4$ is $1:R,5:R,9:R$ — red AP.
- If $9=B$: then $7,8,9$ with $d=1$ is $7:B,8:B,9:B$ — blue AP.

So this maximal coloring dies at 9.

Why do all other 8-colorings die? Same collision: any avoiding coloring of $1..8$ must have last two same color — say $7:B,8:B$ — otherwise you'd have created AP earlier. Then $9=B$ completes $7,8,9$ blue. If you try $9=R$ to avoid that, you complete long difference AP $1,5,9$ or $3,6,9$ or $2,5,8$ etc red.

You run out of room to satisfy all $2b-a\neq color(a)$ constraints simultaneously.

Formal: 8 points impose constraints like $c(9)\neq c(1)$ if $c(1)=c(5)$, and $c(9)\neq c(7)$ if $c(7)=c(8)$, etc. At $N=9$, constraint graph has odd cycle — unsatisfiable.

Hence no coloring of $1..9$ avoids monochromatic 3-AP. $W(2,3)\le9$.

Together $>8$ and $\le9$ ⇒ $W(2,3)=9$.

> Try to avoid red $a,a+d,a+2d$ and blue $a,a+d,a+2d$ by alternating blocks $RRBB$. You can juggle 8 houses. 9th house forces you to close a monochromatic equally-spaced triple — either you close $7,8,9$ same block, or you close long jump $1,5,9$.

That's local-to-global forcing — same as $N(4)=5$ hull case analysis and $R(3,3)=6$ degree case analysis: enumerate small types of disorder, show each forces order at next size.

### How Fast Do They Grow? Faster Than Ramsey Graph Numbers

$W(r,k)$ exists — van der Waerden proved finiteness — but values explode much faster than $R(n,m)$.

| $W$       |   Value   | Meaning                                                                                            |
| :-------- | :-------: | :------------------------------------------------------------------------------------------------- |
| $W(2,3)$  |   **9**   | 1..8 avoids 3-AP, 1..9 cannot. Hand.                                                               |
| $W(3,3)$  |  **27**   | 3 colors, 3-AP. First non-trivial with >2 colors                                                   |
| $W(2,4)$  |  **35**   | Chvátal 1970 backtracking search — $2^{34}$ naive                                                  |
| $W(2,5)$  |  **178**  | $2^{177}$ colorings ruled out conceptually                                                         |
| $W(2,6)$  | **1,132** | Kouril & Paul 2008 SAT solvers months CPU. You _can_ 2-color 1..1131 with no 6-AP, but 1132 forces |
| $W(2,7)$  | **3,703** | Current SAT best 2008-2017                                                                         |
| $W(2,10)$ |  Unknown  | lower bound >10k, upper bound tower                                                                |

#### Why Explosive

$R(4,4)=18$ means among 18 people, monochromatic $K_4$ forced. Host graph has $\binom{18}{2}=153$ edges, $2^{153}$ colorings — huge but search feasible with symmetry.

$W(2,6)=1,132$ means among 1,132 integers, monochromatic 6-AP forced. Host has $2^{1132}$ colorings — astronomically larger search space, cannot brute force. Plus constraints long-range: AP with $d=500$ connects distant positions, constraint graph not local.

Proofs for $W(2,6)$ used DPLL SAT solvers with clause learning:

- Encode each $a\in[1,N]$ boolean variable $x_a$ = Red/Blue.
- For each 6-AP $a,a+d,\dots,a+5d$ in $$, add clauses $\neg(x_a\land\dots\land x_{a+5d})$ and $\neg(\neg x_a\land\dots)$ — forbid all-red and all-blue.[1][N]
- SAT solver tries to satisfy. If UNSAT, $N\ge W$. If SAT, coloring found, $N<W$.

For $N=1,131$, SAT finds model — explicit coloring avoiding 6-AP, highly non-repetitive, not simple $RRBB$ pattern, looks pseudo-random.

For $N=1,132$, solver proves UNSAT after exploring search tree with backtracking, symmetry breaking ($1=R$ wlog), and learning.

Months CPU 2008, today hours with modern CDCL solvers — but still non-trivial.

#### Comparison to Ramsey Numbers

- $R(3,3)=6$, $R(4,4)=18$, $R(5,5)$ unknown 43-48.
- $W(2,3)=9$, $W(2,4)=35$, $W(2,5)=178$, $W(2,6)=1132$.

Growth of $W(2,k)$ already exponential $2^k$ lower bound (Berlekamp $p\cdot2^p$ algebraic using finite fields), upper bound tower of exponentials — gap huge.

$W(3,3)=27$ vs $R(3,3)=6$ shows extra color costs less than longer progression.

$W(2,6)=1132$ instructive because it shows disorder budget: you can be clever and avoid 6 equally spaced same color for 1,131 houses, using complicated pattern that is not simple periodic — looks random — but at 1,132 cleverness exhausted, arithmetic order forced.

Same as Erdős–Szekeres: you can avoid convex 6-gon with 16 points using flat double construction, but 17 forces it. Difference: $N(6)=17$ small, $W(2,6)=1132$ large — integer line needs much larger host to force AP than plane needs to force convex polygon, because AP is more rigid condition than convexity.

That's why van der Waerden numbers are among largest small Ramsey-type numbers known exactly — they measure how long you can delay arithmetic order.

### History and Bounds: From Ackermann to Fields Medal

Van der Waerden proved 1927 answering conjecture of Baudet and Schur: does $W(r,k)$ finite? Yes.

His original proof double induction on $r$ and $k$:

- Induct on $k$, with inner induction building blocks of size $W(r',k-1)$ etc.
- Each step replaces $N$ by $r^{N}$ — exponentiation.
- After $k$ steps, tower of height $k$ — Ackermann-type, not primitive recursive.

For 60 years bound stayed tower of exponentials whose height grows with $k$ — essentially uncomputable for large $k$. Upper bound far from true value.

#### Modern View 1: Hales-Jewett ⇒ van der Waerden

Today we don't teach original proof. We derive van der Waerden from Hales-Jewett — shift from numbers to words.

**Coding:**

Alphabet $A=\{0,\dots,k-1\}$. Word $w\in A^H$ length $H$.

Pick large base $M>kH$ to avoid carries. Map word to number:

$$N(w)=\sum_{i=0}^{H-1} w_i M^i$$

This is injective — different words different numbers because no carry.

Variable word $v(x)$ — word with $x$ placeholders, e.g. $v(x)=1x0x2$ with $x$ at positions $i=1,3$.

Then $N(v(a)) = C + a\cdot d$ where $C=\sum_{\text{const positions}}c_iM^i$, $d=\sum_{\text{x positions}}M^i$ fixed independent of $a$.

As $a$ runs $0,\dots,k-1$, $N(v(a))$ runs $k$-term AP: $C, C+d, C+2d,\dots,C+(k-1)d$.

**HJ ⇒ vdW:** Hales-Jewett says for $H=HJ(k,c)$ large enough, any $c$-coloring of $A^H$ yields monochromatic combinatorial line — set $\{v(0),\dots,v(k-1)\}$ for some variable word $v$ all same color.

Color integers by coloring words via $N$: color of $N(w)$ = color of $w$. Then monochromatic line maps to monochromatic $k$-AP $C+ad$.

So

> Order in words forces order in numbers.

Van der Waerden becomes coding of HJ — purely combinatorial operation substitution, no arithmetic needed. Shows AP forcing is special case of variable substitution forcing.

This also gives new upper bound $W(r,k)\le M^{HJ(k,r)}$ — still tower, because $HJ$ itself tower, but conceptually clean.

#### Modern View 2: Gowers Quantitative Bound

1987 Shelah gave primitive recursive bound for HJ, thus for vdW — first tower not Ackermann.

2001 Gowers gave first _reasonable_ bound using Fourier analysis and Szemerédi theorem:

$$W(2,k) \le 2^{2^{2^{2^{k+9}}}}$$

Tower of 5 exponentials.

Still astronomically huge — for $k=6$, bound is $2^{2^{2^{2^{15}}}}$ with $2^{15}=32768$, tower $\approx 10^{10^{9860}}$ vs true $W(2,6)=1132$. But it was first bound that is elementary recursive — fixed height tower independent of $k$ growth inside top.

Idea: Gowers uniformity norms $U^d$ — measure how "pseudo-random" set is vs structured. Decompose dense set $A\subset[1,N]$ into structured + small + uniform. If uniform, many $k$-APs by counting lemma; if structured, correlate with polynomial phase, iterate.

For this work connecting Fourier analysis to Ramsey theory, Gowers received Fields Medal 1998.

**Lower bounds:** Exponential, not tower.

Berlekamp 1968 algebraic construction: For prime $p$, using quadratic residues in $\mathbb{F}_p$, construct coloring of $p\cdot2^p$ with no $(p+1)$-AP? More precisely $W(2,p+1) > p\cdot2^p$.

Take finite field $\mathbb{F}_{2^n}$, trace map, color by quadratic character — gives long AP-free coloring length $\approx k\cdot2^k$.

So $p2^p \le W(2,p+1) \le \text{tower}(k)$.

True growth between exponential and tower — one of largest gaps in combinatorics. We don't know if closer to bottom or top — most conjecture closer to exponential, but no proof.

#### Timeline

- 1927 van der Waerden double induction — Ackermann tower bound.
- 1968 Berlekamp exponential lower bound.
- 1963 Hales-Jewett — new abstraction, implies vdW.
- 1987 Shelah primitive recursive bound for HJ.
- 2001 Gowers 5-exponential bound — Fields Medal work.
- 2008 $W(2,6)=1132$ SAT.
- 2017-2024 Polymath improvements lower order exponents to $O(k^2)$ in top.

Status: $W(r,k)$ finite, exact values up to $k=7$, growth exponential ≤ $W$ ≤ tower — same pattern as $N(n)=2^{n+o(n)}$ vs $2^{n-2}+1$ and $HJ$ tower vs primitive recursive — order forced, but how soon remains mystery.

### Why It Matters — Partition Regularity

Van der Waerden first formalized what all Ramsey-type theorems formalize:

> **Partition regularity:** You cannot destroy all arithmetic structure by finitely partitioning $\mathbb{N}$. One cell of the partition still contains arbitrarily long APs.

Try to paint integers red/blue to break equally-spaced patterns — you can delay, up to $W(r,k)-1$, but not forever. Some color retains structure.

This idea launched three generations — each stronger, each asking "how sparse can host be and still force AP?"

#### 1. Szemerédi 1975 — From Partition to Density

van der Waerden: you color _all_ of $\mathbb{N}$ with $r$ colors — whole line partitioned — one color forces $k$-AP.

Szemerédi: you don't need to color everything. If $A\subset\mathbb{N}$ has positive upper density

$$\bar d(A)=\limsup \dfrac{|A\cap[1,N]|}{N} \ge \delta>0$$

— e.g., contains at least $1\%$ of numbers up to large $N$ — then $A$ alone contains arbitrarily long APs.

No partition, no other colors. Thickness alone forces.

This implies van der Waerden: $r$-color $\mathbb{N}$, one color has density $\ge1/r>0$, apply Szemerédi, get $k$-AP.

Strictly stronger — Szemerédi applies to sets that are not complements of partition, like set of numbers with first digit 1 — density $\approx 0.1$ but not from finite coloring.

Proof created regularity lemma, launched additive combinatorics.

#### 2. Green-Tao 2004 — Density Zero Still Forces

Primes $P=\{2,3,5,7,11,\dots\}$ have density $0$ — $|P\cap[1,N]|\sim N/\log N$, so $|P|/N\to0$. Szemerédi does NOT apply.

Green-Tao: primes contain arbitrarily long APs anyway.

Why? Primes are not arbitrary sparse set — they are _dense inside pseudorandom host_.

Take almost-primes — numbers with no small prime factors, called $W$-tricked primes / Selberg sieve majorant $\nu$. $\nu$ is pseudorandom — Fourier uniform — and has positive density. Primes sit inside $\nu$ with relative density $>0$ — weighted primes behave like dense subset of random-like set.

Relative Szemerédi: dense subset of pseudorandom set forces $k$-AP.

Thus $k$-AP of primes exists for every $k$. Longest known as of 2024: 27-term AP of primes, start $224584605939537911+81292139\cdot23\#\cdot n$ — huge.

Primes have 26-term APs known explicitly, but Green-Tao says arbitrarily long exist, not constructed.

#### Ramsey Language Unification

- $R(3,3)=6$: host = complete graph $K_6$, coloring edges 2 colors, forced structure = monochromatic triangle.
- $N(4)=5$: host = 5 points in plane, forced = convex quadrilateral.
- $N(n)=2^{n-2}+1$: host = $2^{n-2}+1$ points, forced = convex $n$-gon.
- $HJ(n,c)$: host = $n$-dimensional cube $[n]^H$, coloring words $c$ colors, forced = monochromatic combinatorial line.
- $W(r,k)$: host = interval $$, coloring integers $r$ colors, forced = monochromatic $k$-AP.[1][W]
- Szemerédi: host = dense set $A\subset[1,N]$, forced = $k$-AP inside $A$.
- Green-Tao: host = primes weighted by sieve, forced = $k$-AP of primes.

Same philosophy:

> **For any finite coloring / dense subset of large enough structure, monochromatic / internal order unavoidable.**

#### Disorder Budget View

Each theorem defines budget parameter and threshold where budget exhausted:

- Gomory: budget $W-B$ color imbalance — if $\neq0$, no tiling.
- Egregium: budget $K$ curvature difference — if $\neq0$, no isometry.
- Ramsey $R$: budget $N=R-1$ vertices — can avoid monochrome clique, at $R$ cannot.
- Erdős–Szekeres $N(n)$: budget $2^{n-2}$ points — can avoid convex $n$-gon, at $2^{n-2}+1$ cannot — conjectured.
- Hales-Jewett $HJ$: budget $H=HJ-1$ dimension — can avoid monochromatic line, at $HJ$ cannot.
- van der Waerden $W(r,k)$: budget $W-1$ length — can avoid $k$-AP, at $W$ cannot.

All say: **Local disorder can exist for a while, but global order forced by size alone in right parameter.**

And that's why van der Waerden matters — first time arithmetic progression shown partition regular, seed for 100 years of additive combinatorics, from Szemerédi to Green-Tao to 2023 breakthrough on Roth's theorem. Order hides in numbers, not just graphs and point sets.

## Szemerédi's Theorem — Density Forces Progression

> **Szemerédi 1975, resolving Erdős–Turán 1936:** Any subset of $\mathbb{N}$ with positive upper density contains arbitrarily long arithmetic progressions.

This is van der Waerden on steroids.

### Core Concepts — Szemerédi's Theorem

**Density:** $A\subset\mathbb{N}$ has positive upper density if

$$\bar d(A)=\limsup_{N\to\infty}\dfrac{|A\cap\{1,\dots,N\}|}{N} >0$$

Meaning $A$ contains fixed percentage of numbers up to large $N$ infinitely often.

- Evens: $|E\cap[1,N]|\approx N/2$ → density $1/2$.
- Multiples of 3: $N/3$ → $1/3$.
- Squares: $|Squares\cap[1,N]|\approx \sqrt N$ → $\sqrt N / N =1/\sqrt N\to0$ → density 0.
- Primes: $N/\log N$ → density 0.

$\limsup$ not $\lim$ — set may not have limiting frequency, but if it infinitely often reaches $\delta$ fraction, positive upper density.

Positive density = not too sparse. You keep $\delta$ fraction infinitely often.

**AP:** $a, a+d, a+2d,\dots,a+(k-1)d$ constant step $d>0$.

$k$-term arithmetic progression — $k$ equally spaced numbers.

- $3,5,7$ is $a=3,d=2,k=3$.
- $10,20,30,40$ is $a=10,d=10,k=4$.
- $d$ can be huge — not required small.

Structure to avoid if you want disorder.

**Arbitrarily long:** For every $k$, exists $k$-term AP inside $A$. Not same AP for all $k$.

For $k=3$ some triple $a,a+d,a+2d\in A$ — maybe $a=100,d=7$.

For $k=4$ maybe different quadruple $a'=1000,d'=50$.

For $k=100$ maybe $a''$ enormous.

Theorem does NOT say infinite AP inside $A$ — set $A$ finite blocks? Actually infinite AP would be $a,a+d,a+2d,\dots$ forever — density would be $>0$ but infinite AP would imply $A$ contains infinite arithmetic progression, stronger than Szemerédi claims. Szemerédi claims for each finite $k$ finite progression, not one infinite progression.

> If set is not too sparse — contains $\delta>0$ fraction of integers infinitely often — you cannot avoid $k$-term progression, no matter how you try to hide gaps.

Try to construct $A$ density $1/2$ with no 3-AP: choose numbers avoiding $a,a+d,a+2d$. Greedy fails — eventually pigeonhole forces. Szemerédi says impossible for any $k$.

This is why stronger than van der Waerden: van der Waerden needs coloring of all $\mathbb{N}$ — whole line partitioned — pigeonhole guarantees one color has density $\ge1/r$. Szemerédi needs only one set thick enough — no partition of complement needed.

And why Green-Tao needed new idea: primes density 0, so Szemerédi does NOT force AP in primes — primes too sparse. Need relative density inside pseudorandom host.

Budget view: Density $\delta$ is disorder budget. If $\delta>0$, you can avoid $k$-AP for a while up to some $N(\delta,k)$, but eventually AP forced. Threshold $N(\delta,k)$ grows as $\delta\to0$ — sparser you are, longer you can avoid.

Exactly same as $W(r,k)$ budget $W-1$, $N(n)$ budget $2^{n-2}$, $HJ$ budget dimension — local disorder exists, global order forced by size alone.

### Significance — Why Szemerédi Matters

**Foundational pillar of additive combinatorics**

Before 1975, additive number theory was collection of tricks — van der Waerden, Roth $k=3$, etc. No systematic theory of _structure_ inside dense sets.

Szemerédi proved: density alone forces arbitrary additive structure — $k$-AP for every $k$.

This made additive combinatorics field: study of what additive patterns dense sets must contain, and what tools detect them — Fourier analysis, graph regularity, ergodic theory, higher-order uniformity.

Every result since — Green-Tao primes APs, 2023 Kelley-Meka breakthrough on Roth, 2024 $2^{n-o(n)}$ Erdős–Szekeres bounds — lives in framework Szemerédi created.

**Regularity Lemma — accidental revolution**

To prove theorem, Szemerédi needed to handle graph encoding of APs.

Invented 1975 regularity lemma:

> Any large graph can be partitioned into $M(\epsilon)$ pieces — bounded number independent of graph size — such that most pairs of pieces are $\epsilon$-pseudorandom — edges between pieces behave like random bipartite graph with density $d_{ij}$.

Huge graph → compressed into small weighted template — Szemerédi graphon picture.

Consequences:

- Graph removal lemmas — if few copies of $H$, can delete few edges to destroy all $H$.
- Property testing — can test triangle-freeness in $O(1)$ queries, independent of graph size.
- Computer science — algorithmic regularity, approximation algorithms for dense Max-Cut, etc.
- Itself stronger than Szemerédi theorem — cornerstone of extremal graph theory.

Lemma now taught before theorem — tool bigger than application.

**Alternative proofs opened fields:**

- **Furstenberg 1977 ergodic theory proof** — translated combinatorial statement into dynamical system.

Idea: set $A$ with $\bar d(A)>0$ → measure-preserving system $(X,T)$ and set $E$ measure $\ge\delta$ such that $A$ contains $k$-AP iff $\mu(E\cap T^{-d}E\cap\dots\cap T^{-(k-1)d}E)>0$.

Density → recurrence: system returns close to itself infinitely often.

Then Furstenberg proved multiple recurrence theorem — ergodic Szemerédi.

Impact: created ergodic Ramsey theory — field connecting number theory to dynamics. Furstenberg correspondence principle now standard tool: combinatorics ↔ dynamics.

Furstenberg won Abel Prize 2020 partly for this translation.

- **Gowers 2001 Fourier-analytic proof with higher-order uniformity**

Roth 1953 proved $k=3$ case using Fourier analysis — large Fourier coefficient ⇒ density increment on arithmetic progression.

For $k=4$, classical Fourier fails — need quadratic Fourier.

Gowers invented $U^d$ uniformity norms — measure correlation with polynomial phases degree $<d$.

$U^2$ = Fourier uniformity, $U^3$ detects quadratic structure, etc.

Decomposition: dense set $A = f_{structured}+f_{small}+f_{uniform}$ where $f_{structured}$ is nilsequence-like, $f_{uniform}$ small in $U^{k-1}$ norm so counts $k$-APs correctly.

Proved Szemerédi with tower-type bounds — first reasonable bound after 60 years.

Invented higher-order Fourier analysis, won Fields Medal 1998.

That proof led directly to Green-Tao: primes uniform in $U^d$ after $W$-trick, so contain APs.

So Szemerédi's theorem significance triple:

1. Theorem itself — density forces arbitrary APs — final form of van der Waerden strengthening.
2. Tools created to prove it — regularity lemma, ergodic correspondence, Gowers norms — each became field.
3. Philosophy — same as your central lesson: **randomness shallow**. Density $\delta>0$ budget finite, eventually structure unavoidable. But unlike $W(2,3)=9$ you can see, here structure unavoidable for reason deep enough to need new mathematics to explain _why_ randomness collapses.

### van der Waerden vs Szemerédi — Core Distinction

#### Partition vs Density

| Feature   | van der Waerden                                        | Szemerédi                                                            |
| :-------- | :----------------------------------------------------- | :------------------------------------------------------------------- |
| Framework | Ramsey / Coloring                                      | Density / Additive combinatorics                                     |
| Condition | $\mathbb{Z}$ split into $r$ colors — whole set colored | Single $A\subset\mathbb{Z}$ with $\bar d(A)>0$ — no partition needed |
| Guarantee | At least one color class has $k$-AP                    | This specific dense $A$ has $k$-AP                                   |
| Strength  | Weaker                                                 | Stronger — implies van der Waerden                                   |

**van der Waerden — needs everything colored.**

Host is whole $\mathbb{N}$ partitioned into $r$ colors. You paint every house on infinite street red/blue/yellow... $r$ colors total.

Pigeonhole: you covered all integers, so average color occupies $1/r$ fraction. But theorem does not use thickness directly — it uses that you _partitioned_ everything. If you miss even one integer uncolored, hypothesis fails.

Think: you try to avoid red $k$-AP and blue $k$-AP simultaneously by clever global coloring. $W(r,k)$ says you can delay up to $W-1$, but at $W$ any complete coloring forces monochrome $k$-AP somewhere.

Needs global info: you must know color of every integer up to $W$ to guarantee.

**Szemerédi — needs only one thick set.**

Host is single $A$ with positive upper density — $\bar d(A)=\limsup|A\cap[1,N]|/N>0$ — e.g., contains $1\%$ of numbers infinitely often.

You don't care about complement. $A^c$ can be anything, not colored, missing. $A$ alone thick enough forces its own $k$-AP.

Think: pick any 50% of integers trying to avoid $k$-AP — e.g., choose numbers avoiding $a,a+d,a+2d$. Try as hard as you want, hide gaps cleverly. Szemerédi says impossible for every $k$ large — if you keep density $>0$, AP appears inside your set.

So van der Waerden needs partition budget $r$, Szemerédi needs density budget $\delta>0$.

> van der Waerden: **global partition forces order somewhere.**
> Szemerédi: **local thickness forces order inside this set.**

That is why Szemerédi ⇒ van der Waerden: $r$-coloring of $\mathbb{N}$ ⇒ some color class has density $\ge1/r>0$ ⇒ by Szemerédi that class contains $k$-AP.

#### Why Szemerédi ⇒ van der Waerden

**Setup:** Color $\mathbb{N}=C_1\cup\dots\cup C_r$ disjoint $r$-coloring — every integer gets exactly one color.

Goal: Show some $C_i$ contains $k$-AP for every $k$ — that's van der Waerden.

**Step 1: Pigeonhole for density**

For each $N$, $\sum_{i=1}^r |C_i\cap[1,N]| = N$ — counts partition $$.[1][N]

Divide by $N$: $\sum |C_i\cap[1,N]|/N =1$.

Take $\limsup_{N\to\infty}$: $\sum \bar d(C_i) \ge 1$ — upper densities cannot all be small, sum at least 1.

If all $\bar d(C_i) < 1/r$, say $\le 1/r -\epsilon$, sum $\le r(1/r-\epsilon)=1-r\epsilon<1$ contradiction.

Thus exists $i_0$ with

$$\bar d(C_{i_0}) \ge 1/r >0$$

One color occupies at least $1/r$ fraction infinitely often — pigeonhole principle for density.

**Step 2: Apply Szemerédi to thick color**

Szemerédi hypothesis: Any $A\subset\mathbb{N}$ with $\bar d(A)>0$ contains $k$-AP for every $k$.

Our $C_{i_0}$ has $\bar d \ge 1/r>0$ ⇒ hypothesis satisfied.

Conclusion: For every $k$, $C_{i_0}$ contains $k$-term AP $a,a+d,\dots,a+(k-1)d$.

That's monochromatic $k$-AP in color $i_0$.

**Step 3: Conclude van der Waerden**

Thus any $r$-coloring of $\mathbb{N}$ yields monochromatic $k$-AP.

For finite interval $$, compactness argument gives existence of finite $W(r,k)$ — if infinite version holds, finite threshold must exist, else take sequence of colorings avoiding $k$-AP on $$ and limit to coloring of $\mathbb{N}$ avoiding — contradiction.[1][N]

So $W(r,k)$ finite follows.

> Coloring forces a color to be dense ($\ge1/r$) ⇒ density forces AP (Szemerédi) ⇒ coloring forces AP (van der Waerden).

Szemerédi strictly stronger — it tells you _which_ color is forced to be dense one, and works even when you don't have partition of whole $\mathbb{N}$, only one dense set.

Converse false: van der Waerden says some color of partition has AP, but doesn't guarantee a prescribed density-$1/2$ set has AP unless you know its complement is other color.

#### Why Converse False — Density Strictly Stronger

Van der Waerden cannot guarantee AP in prescribed set density $1/2$ unless you know complement.

**The gap:** van der Waerden says:

> For partition $\mathbb{N}=C_1\cup C_2$, _some_ $C_i$ has $k$-AP.

It does NOT say _which_ $i$. Could be $C_1$, could be $C_2$. If you care about specific $A$ with density $1/2$, van der Waerden applied to $A\cup A^c$ tells you _either $A$ or $A^c$ has $k$-AP_ — but you don't know which. If the AP lands in $A^c$, you learned nothing about $A$.

Example you gave: $A=$ numbers with first digit 1 — $1,10-19,100-199,...$ Upper density $\approx0.11$? Actually Benford — $\limsup|A\cap[1,N]|/N =5/9$? In $$ about $1111/1999\approx0.55$, infinitely often high, so $\bar d(A)>0$. Van der Waerden says for $A\cup A^c$, one has $k$-AP — trivial, but could be $A^c$ every time for each $k$? No, but vdW alone doesn't rule out that AP always lands in complement. You need Szemerédi to force AP inside $A$ itself.[1][1999]

Formally:

- vdW is $\exists i$ : $C_i$ contains $k$-AP.
- Szemerédi is $\forall A$ with $\bar d(A)>0$: $A$ contains $k$-AP.

Second quantifier stronger — universal over sets, not existential over partition cell.

**Two ways converse fails:**

1. **Prescribed set:** Let $A$ density $1/2$ — e.g., take random half of integers avoiding 3-AP as long as possible? Can you avoid? Szemerédi says no — for large enough $N$, any $N/2$-sized subset of $$ contains $k$-AP. vdW does not imply this. vdW only if you 2-color whole $\mathbb{N}$ and look, but if you only look at $A$ alone — without coloring complement — hypothesis of vdW not satisfied, because vdW needs coloring of all $\mathbb{N}$. Knowing $A$ density $1/2$ alone does not give you a coloring where $A$ is a color class? Actually it does — $A\cup A^c$ is coloring — but vdW says _some_ color has AP, not necessarily $A$. So $A$ could still be AP-free if AP hides in $A^c$. Szemerédi rules that out.[1][N]

2. **Density zero sets:** $A$ sparse, density 0 like primes, squares. vdW says nothing — partition $\mathbb{N}=A\cup A^c$ — $A^c$ density 1, so vdW likely forces AP in $A^c$, not in $A$. Squares have density 0 and indeed contain no 4-term AP — consistent. Primes have density 0 but _do_ contain arbitrarily long APs — this needs Green-Tao, beyond both vdW and Szemerédi. vdW cannot even ask question because host not partition-dense.

Hence hierarchy:

$$\text{van der Waerden} < \text{Szemerédi} < \text{Green-Tao relative Szemerédi}$$

- vdW: finite partition forces AP somewhere.
- Szemerédi: positive density forces AP inside set itself.
- Green-Tao: relative density inside pseudorandom host forces AP even when absolute density 0.

Each step weakens hypothesis about host — from covering whole $\mathbb{N}$ with $r$ colors, to one thick set, to sparse but pseudorandomly embedded set — and conclusion stays: AP unavoidable.

That is why Szemerédi strictly stronger — it isolates property that makes van der Waerden true: not coloring, but thickness.

#### Restatement

**1. van der Waerden — finite threshold, partition**

> For any $r,k$, exists $W(r,k)$ such that if $\{1,\dots,W\}$ $r$-colored, then some color contains $k$-AP.

Host = interval $$, length $W(r,k)$. Condition = you color every integer in host with $r$ colors.

Conclusion = monochromatic $k$-AP somewhere, in some color.

Quantitative — gives number $W(r,k)$. We know $W(2,3)=9$, $W(2,4)=35$, $W(2,6)=1132$ — actual thresholds where avoidance ends.[1][W]

Philosophy = **partition regularity**: finite coloring cannot destroy all arithmetic structure. Disorder budget = $r$ colors, $W-1$ length where you can still avoid.

Same as $R(3,3)=6$: color edges $K_6$ 2 colors, monochromatic triangle forced — finite threshold forces graph order.

**2. Szemerédi — no number, density**

> If $A\subset\mathbb{N}$ and $\displaystyle\limsup_{N\to\infty}\dfrac{|A\cap|}{N}>0$ then for every $k$, $A$ contains $k$-term AP.[1][N]

Host = any $A\subset\mathbb{N}$ with positive upper density — e.g., $\ge1\%$ infinitely often. No interval length given.

Condition = thickness alone, no coloring, no partition of complement needed.

Conclusion = this specific $A$ contains $k$-AP for every $k$ — arbitrarily long, but for each $k$ possibly different AP.

Non-quantitative in statement — no explicit $W$, existence for each $k$ with $N(\delta,k)$ depending on $\delta$. Gowers gives tower bound.

Philosophy = **density regularity**: positive fraction cannot avoid all APs. Disorder budget = $\delta>0$ density, you can avoid up to $N(\delta,k)-1$ inside $A$, at $N(\delta,k)$ forced.

Same as Erdős–Szekeres density version, Turán vs Ramsey: Turán says dense graph forces $K_t$, Ramsey says complete graph colored forces monochrome $K_t$. Szemerédi is Turán-type strengthening of van der Waerden's Ramsey-type.

**Summary mapping:**

- van der Waerden: $r$ colors → one color density $\ge1/r$ → forces $k$-AP. Needs pigeonhole to get density, then density → AP hidden inside.
- Szemerédi: density $>0$ → forces $k$-AP directly, no pigeonhole needed.

Thus Szemerédi isolates core: thickness, not partition, is what forces arithmetic order.

van der Waerden first showed $K=0$ vs $W-B$ vs $W(r,k)$ all same — budget finite, order forced. Szemerédi showed budget can be measured as $\delta>0$ fraction, far more general — you don't need to paint whole street, owning $1\%$ of houses thickly enough forces equally spaced houses in your set.

### Hierarchy of Forcing — Where It Sits in Your Story

You have now full ladder — same meta-theorem in different hosts:

- **Gomory:** budget $W-B$ black-white imbalance — count forces no tiling. If $W\neq B$, domino tiling impossible. Disorder = color imbalance.

- **Egregium:** budget $K$ Gaussian curvature — curvature forces no isometry. If $K_1\neq K_2$, surface cannot be bent isometrically. Disorder = curvature difference.

- **Ramsey $R(3,3)=6$:** budget $N=5$ vertices — 6 forces monochromatic triangle. Host = complete graph, coloring edges 2 colors. Disorder = avoid monochrome triangle.

- **Hales-Jewett $HJ(k,c)$:** budget dimension $H=HJ-1$ — $HJ$ forces monochromatic combinatorial line. Host = word cube $[k]^H$. This implies van der Waerden by coding $N(w)=\sum w_i M^i$ — AP becomes variable word. Disorder = dimension.

- **van der Waerden $W(r,k)$:** budget $W-1$ length — $W$ forces monochromatic $k$-AP. Host = interval $$, coloring integers $r$ colors. Disorder = length of avoidance coloring.

- **Erdős–Szekeres $N(n)=2^{n-2}+1$:** budget $2^{n-2}$ points — $2^{n-2}+1$ forces convex $n$-gon. Host = point set in general position. Disorder = number of points.

- **Szemerédi:** budget $\delta>0$ density — positive density forces arbitrarily long AP. Host = any $A\subset\mathbb{N}$ with $\bar d(A)>0$. Implies van der Waerden — partition into $r$ colors gives one color density $\ge1/r>0$, apply Szemerédi.

All same:

> **Disorder budget finite.** You can avoid structure for a while with clever construction, but size/density/dimension/curvature budget exhausted → structure forced.

For Szemerédi, budget measured by density $\delta$:

- If you keep $\delta>0$ — keep $\delta$ fraction of integers infinitely often — you can avoid $k$-AP up to some $N(\delta,k)$ by clever sparse choice, but beyond that progression forced.

- If $\delta\to0$, $N(\delta,k)\to\infty$ — sparser you are, longer you can avoid. Primes $\delta=0$, so Szemerédi does not apply — need Green-Tao relative density inside pseudorandom host.

- Like $HJ$ and $N(n)$, proof non-constructive in sense of location: Szemerédi proves $k$-AP exists in $A$, does not tell where $a,d$ are — size alone forces existence, not position. Same as regularity lemma gives existence of partition, not explicit partition; same as van der Waerden proves $W(r,k)$ exists, does not give explicit coloring up to $W-1$ — SAT solver finds it for $W(2,6)=1132$.

That non-constructiveness is feature: Ramsey theory never says _where_ order appears, only that it must — disorder cannot be extended forever.

This completes arc from Gomory elementary counting to Szemerédi density — each step weakens hypothesis, strengthens conclusion, keeps same message: **randomness shallow, order inevitable when host large enough.**

## Green-Tao Theorem — Inevitable Order Inside the Primes

Final step in 100-year progression:

- **van der Waerden 1927:** Coloring $\mathbb{N}$ with $r$ colors → monochromatic APs of any length. Need to color _everything_.
- **Szemerédi 1975:** Density >0 → APs of any length inside _that set_. Need thickness $>0$.
- **Green-Tao 2004:** Primes density 0 → still APs of any length. Even sparse set that _looks random_ forces APs.

> **Green-Tao 2004:** For every $k$, there exist $a,d>0$ such that $a, a+d,\dots,a+(k-1)d$ all prime.

You can find $k$ primes perfectly equally spaced, $k$ as large as you want.

Primes look random locally, globally cannot avoid arithmetic structure.

### What It Says — And What It Does Not

**Simple picture:** Arithmetic progression = equally spaced stepping stones across number line. Step size $d$ is distance between stones.

- $3,7,11$: $a=3$, $d=4$, stones at $3+0\cdot4, 3+1\cdot4, 3+2\cdot4$.
- $5,11,17,23,29$: $a=5$, $d=6$, five stones.

Green-Tao: you can find $k$ prime stones in perfect line, for any $k$ you name. Want 10 prime stones equally spaced? Exists somewhere far out. Want 100? Exists, just much farther.

Local primes look random — gaps irregular — but global desert still contains arbitrarily long straight highways made entirely of prime stones.

**Arbitrary vs Infinite**

- Arbitrary length = for each $k=3,4,5,\dots$ there is _some_ prime AP length $k$. Different $k$ may have totally different $a,d$. For $k=3$, $a=3,d=4$ works. For $k=5$, $a=5,d=6$ works. For $k=100$, there is some $a_{100},d_{100}$ enormous — proof says exists, doesn't tell you numbers.

- Not infinite length = one AP $a,a+d,a+2d,\dots$ infinite all primes is impossible. Proof in one line: term number $a$ steps ahead is $a + a\cdot d = a(1+d)$ = $a$ times $(1+d)$ → composite if $a>1$. So after $a$ steps you always hit multiple of first term.

> **Analogy**: You can find arbitrarily long straight segments of road in desert, but you cannot have infinite straight road with no bends that stays on prime stones forever — you'll eventually hit a non-prime rock because $a$ divides that future term.

Think: finite rows possible, infinite row impossible — just like van der Waerden says arbitrarily long APs in one color, not infinite AP.

**Infinitude for fixed $k$.**

Green-Tao proves not just existence of one $k$-AP, but infinitely many distinct $k$-APs for each fixed $k$. And count up to $N$:

$$\#\{prime\ k\text{-APs with }a\le N,d\le N\} \sim C_k \dfrac{N^2}{(\log N)^k}$$

$C_k>0$ constant depending on $k$ — Hardy-Littlewood prime tuples constant.

Simple: infinitely many prime triples equally spaced, infinitely many prime 5-tuples, etc. If you search to $N=10^{12}$, you expect about $N^2/(\log N)^k$ of them — many for $k=3$, fewer for larger $k$.

**Why common difference explodes**:

Why must $d$ be huge? Small primes force divisibility.

- $k\ge3$: All primes >2 odd. If $d$ odd, $a$ odd + odd = even → $a+d$ even composite. So $d$ must be even = divisible by 2. Otherwise you'd alternate odd/even and hit even composite immediately.

- $k\ge4$: Consider mod 3. Numbers mod 3 are $0,1,2$. If $d$ not multiple of 3, then $a, a+d, a+2d$ cover all three residues mod 3 — pigeonhole. One residue is $0\bmod3$ → that term divisible by 3. If term >3, composite. To have 4 primes >3 all prime, you must avoid hitting $0\bmod3$, so need $3|d$. So $d$ multiple of $3$.

- $k\ge6$: Similarly mod 5. If $5\nmid d$, then $a,a+d,\dots,a+4d$ cover all residues mod 5 → one term $0\bmod5$ composite. To have 6 primes >5, need $5|d$.

General rule: To have $k$ primes all >$k$, $d$ must be divisible by every prime $p<k$. Otherwise progression hits $0\bmod p$.

This product is primorial:

$$k\# = \prod_{p<k}p$$

- $k=5$: primes $<5$ are $2,3$ → $k\#=6$. Indeed $5,11,17,23,29$ $d=6$.
- $k=6$: primes $<6$ are $2,3,5$ → $30$. Must have $d$ multiple of 30. Smallest 6-term example $7,37,67,97,127,157$ $d=30$.
- $k=10$: primes $<10$ are $2,3,5,7$ → $210$. Indeed $199,\dots,2089$ $d=210$.
- $k=27$: need divisible by all primes $<27$ → $2\cdot3\cdot5\cdot7\cdot11\cdot13\cdot17\cdot19\cdot23 = 223,092,870 =23\#$.

So even before you search, number theory forces $d$ huge. This is why $k=27$ record has $d\approx9.6\times10^{17}$ — it must be multiple of $223$ million, and random prime density $1/\log N$ tiny, so you need enormous search space to get lucky.

> **Takeaway**: primes want to be AP, but small primes are obstacles — to avoid being divisible by 2,3,5,..., you must step by multiples of them. The longer AP you want, the more obstacles, the bigger mandatory step.

### The Central Difficulty: Density Zero

Density answers: if you look at first $N$ numbers $1,\dots,N$, what fraction belongs to your set $A$?

$$d_N(A)=\dfrac{|A\cap[1,N]|}{N}$$

If $d_N(A)$ stays above some $\delta>0$ infinitely often — even if it wiggles — we say $A$ has positive upper density $\bar d(A)>0$.

- **Evens:** $2,4,6,\dots$ Up to $N$, about $N/2$ evens → $d_N\approx1/2$ → $\bar d=1/2>0$. Thick.

- **Numbers starting with 1:** $1,10-19,100-199,\dots$ Up to $1999$, you have $1 +10 +100+... =1111$ numbers → $1111/1999\approx55\%$. Up to $2999$, fraction drops to $\approx37\%$. It oscillates, but infinitely often hits $>50\%$ — $\limsup>0$. So positive upper density even though no limit. Still thick infinitely often.

- **Squares:** $1,4,9,16,\dots$ Up to $N$, about $\sqrt N$ squares → $d_N\approx \sqrt N/N=1/\sqrt N$. For $N=10^6$, $1000/10^6=0.1\%$. For $N=10^{12}$, $10^6/10^{12}=0.0001\%$ → $0$. Density 0 — sparse.

- **Primes:** Prime Number Theorem: $\pi(N)\sim N/\log N$ primes up to $N$ → $d_N\sim1/\log N$.
  - $N=10^6$: $\log N\approx13.8$ → ~7.2% predicted, actually 7.8%.
  - $N=10^{12}$: $\log N\approx27.6$ → ~3.6%.
  - $N=10^{100}$: $\log N\approx230$ → ~0.4%.

Goes to $0$ as $N\to\infty$. In limit, primes occupy 0% of integers. Density 0 — vanishing fraction.

**Why this kills Szemerédi:**

Szemerédi hypothesis: $\limsup|A\cap[1,N]|/N>0$ — need to contain e.g., $1\%$ of numbers infinitely often. Then theorem says $A$ contains $k$-AP for every $k$ — e.g., set with $1\%$ contains 1000-term AP somewhere.

Primes fail: eventually contain $<1\%$, $<0.1\%$, $<0.0001\%$... So hypothesis false, theorem says nothing.

And density-zero sets _can_ avoid APs! Example powers of 2: $1,2,4,8,16,32,\dots$ — grows exponentially, density 0, and contains no 3-term AP. Why? If $2^a,2^b,2^c$ in AP, then $2^b-2^a=2^c-2^b$ → $2^a(2^{b-a}-1)=2^b(2^{c-b}-1)$ → impossible for $a<b<c$ unless trivial. So sparse sets can escape.

So primes could have been like powers of 2 — sparse enough to avoid APs forever. Szemerédi cannot rule out.

**Why primes different?**

Powers of 2 structured sparse — lacunary. Primes pseudorandom sparse — they look random locally, not growing regularly. They _should_ contain APs if they were random set with same density $1/\log N$ — random set with $N/\log N$ points expects many $k$-APs for small $k$.

But random heuristic not proof — need to prove pseudorandomness enough to force APs despite density zero.

Green-Tao insight: Don't apply Szemerédi to primes in integers. Apply Szemerédi _relative_ to a larger pseudorandom host that has density 1, inside which primes are relatively dense.

Think: desert vs oasis. Primes = trees density 0 in whole desert. Can't apply Szemerédi to desert. But find oasis $\nu$ covering 1% of desert, looking random, containing trees at 10% density inside oasis. Inside oasis, trees are _relatively_ dense — relative density >0 — so relative Szemerédi forces AP among trees.

That is transference principle — transfer density theorem from dense world to sparse pseudorandom world.

### The Breakthrough: Transference Principle — Simple Explanation

Proof 50 pages, but idea now standard template — used for polynomial primes, Gaussian primes, etc.

> **Metaphor:** Imagine desert huge — integers. Trees = primes — very sparse, $0\%$ of desert. Want to prove there is straight line of $k$ trees equally spaced.

You cannot prove directly — trees too sparse. Random 3 trees almost never equally spaced.

Trick: Find oasis $\nu$ inside desert that:

- Covers say $1\%$ of desert — not too small.
- Looks completely random — if you test it with Fourier, Gowers norms, it indistinguishable from random cloud.
- Contains all trees — wherever tree, oasis cloud at least as high.

If trees occupy $10\%$ of oasis — relatively dense inside oasis — then inside oasis, Szemerédi applies! Because inside oasis world, trees have positive relative density.

So problem reduces to building such oasis and proving Szemerédi _relative_ to oasis.

#### Step 1: Build pseudorandom majorant — Selberg envelope

We need function $\nu:[1,N]\to\mathbb{R}_{\ge0}$ — think weight at each $n$.

Properties:

1. **Majorizes primes:** $\nu(n)\ge c\cdot1_{prime}(n)$. Where $n$ prime, $\nu(n)$ at least constant $c$. Where $n$ composite, $\nu(n)$ can be small but nonnegative. So primes sit under cloud.

   How built? Goldston-Yıldırım / Selberg sieve — classic sieve weight that approximates prime indicator but smoother, less spiky. Truncated divisor sum: $\nu(n)\approx(\sum_{d|P(n), d\le R}\mu(d)\log(R/d))^2$ — roughly counts $n$ with no small prime factors — pseudoprime detector. Not 0/1, but nonnegative, mean ~1.

2. **Pseudorandom:** $\nu$ looks like constant 1 for counting linear patterns. Formal: $\|\nu-1\|_{U^{k-1}}$ small — Gowers uniformity norm small. Also linear forms condition — number of solutions to systems like $\nu(n)\nu(n+d)...$ matches random.

   Test $\nu$ with any Fourier wave $e^{2\pi i \alpha n}$ — average $\approx0$ like random. Test with quadratic phase $e^{2\pi i\alpha n^2}$ — also random. So cloud has no hidden arithmetic bias.

3. **Mean 1:** $\mathbb{E}_{n\le N}\nu(n)=1+o(1)$. So total mass $N$ — like constant 1 function mass. Not sparse — occupies positive fraction.

**$W$-trick — killing trivial bias.**

Primes >2 odd → not random mod 2 — all $1\bmod2$. Similarly mod 3, primes $>3$ are $1,2\bmod3$ not $0$. This is not pseudorandom — fails linear forms condition.

Fix: Let $w$ slowly growing, say $\log\log N$, $W=\prod_{p\le w}p$ primorial of small primes. Look only at arithmetic progression $Wn+1$ — numbers congruent $1\bmod W$. Inside this progression, primes equidistributed — no bias mod small primes because we fixed residue.

Define new universe $[N']$ where $N'\approx N/W$, and study $Wn+1$ prime. After this $W$-trick, $\nu$ becomes truly pseudorandom — $W$-tricked primes have no residue bias.

> **Analogy**: Primes are like people who never sit in certain chairs — obviously not random. $W$-trick removes those chairs from room, then remaining seating looks random.

#### Step 2: Prove relative Szemerédi — heart

Gowers' proof of Szemerédi 2001:

Take bounded $f:[N]\to[0,1]$, mean $\ge\delta$. Want to count $k$-APs: $\mathbb{E}_{a,d}f(a)f(a+d)...f(a+(k-1)d)$.

Either $f$ Gowers-uniform — $U^{k-1}$ small — then by generalized von Neumann, count $\approx\delta^k N^2$ — random number, many APs.

Or $f$ not uniform — $U^{k-1}$ large — then Gowers inverse theorem says $f$ correlates with nilsequence — structured object like $e^{2\pi i(\alpha n^2+\beta n)}$ for $k=4$. Then you can decompose $f=f_{str}+f_{sml}+f_{unif}$, density increment on structured piece — iterate, density increases, must stop, find AP.

Green-Tao need same but with $0\le f\le\nu$, not $0\le f\le1$. $\nu$ unbounded pointwise but mean 1, pseudorandom.

Prove:

> **Relative Szemerédi:** If $\nu$ pseudorandom (linear forms + correlation conditions), and $0\le f\le\nu$, $\mathbb{E}f\ge\delta>0$, then $f$ contains $\ge c(\delta,k)N^2$ $k$-APs.

Ingredients simple terms:

- **Generalized von Neumann relative:** If $f$ bounded by $\nu$ and $U^{k-1}$ small relative to $\nu$, then AP count close to random. Needs $\nu$ pseudorandom so Cauchy-Schwarz still works.

- **Dense model + inverse theorem:** If $f$ not uniform, need to find structure. Show $f$ has dense model $\tilde f$ bounded by 1 with similar Gowers norm — transference. Then apply usual inverse theorem to $\tilde f$, lift correlation back to $f$. This uses Hahn-Banach separation — Green-Tao dense model theorem — if $\nu$ pseudorandom, any $f\le\nu$ approximable by bounded $\tilde f$.

- **Structure theorem + density increment:** Once correlate with nilsequence, run energy increment as Gowers.

Plain language: If universe $\nu$ random enough, any relatively dense subset $f$ inherits Ramsey property. Random universe cannot hide structure to help you avoid APs — any thick subset inside it still forces APs.

#### Step 3: Transfer primes into envelope

Final check: primes actually dense inside $\nu$.

After $W$-trick, define normalized prime indicator:

$$\tilde f(n)=\dfrac{\phi(W)}{W}\log N\cdot1_{prime}(Wn+1)$$

Factor $\dfrac{\phi(W)}{W}\log N$ — normalizes mean to $\approx1$. Prime number theorem in AP says primes $\equiv1\bmod W$ have density $\sim1/\phi(W)\cdot1/\log N$, so after multiply by $\phi(W)/W\cdot\log N$, mean $\approx1/W\cdot? Actually $\approx1$ — constant.

Goldston-Yıldırım construction ensures $0\le\tilde f\le\nu$ pointwise, $\mathbb{E}\tilde f\gg1$ — say $\ge\delta=1/2$.

So primes relatively dense in $\nu$.

Apply relative Szemerédi to $\tilde f$ → $\tilde f$ contains many $k$-APs → those correspond to $k$-APs of primes $Wn+1$ → $k$-APs of primes in original integers.

Done.

**Why this template powerful:** Once you have pseudorandom majorant for any sparse set — polynomial values of primes, Gaussian primes, etc. — same relative Szemerédi gives APs there. Green-Tao opened industry: transference principle.

### Records: What We Can Actually Find — Simple Explanation

Green-Tao is **purely existential** — like Erdős–Szekeres says $2^{n-2}+1$ points force convex $n$-gon but doesn't tell you where. It says _some_ prime $k$-AP exists somewhere, no bound how far you must search.

Computationally brutal because of $k\#$ divisibility we explained.

**Small examples you can verify by hand:**

- $k=3$: $3,7,11$ — step $d=4$. Check: $3$ prime, $7$ prime, $11$ prime, equally spaced. Many triples exist.

- $k=4$: $5,11,17,23$ — $d=6$. All prime? $5,11,17,23$ yes.

- $k=5$: $5,11,17,23,29$ — $d=6$ again, minimal. Why $d=6$ minimal? Must be multiple of $6=2\cdot3$ to avoid hitting multiple of 2 or 3. So 6 smallest possible.

- $k=6$: $7,37,67,97,127,157$ — $d=30=2\cdot3\cdot5$. Check difference $30$ each time. Why $30$? Need divisible by $2,3,5$ for $k\ge6$. So 30 minimal. This progression works.

Notice pattern: As $k$ grows, minimal allowed $d$ jumps at each prime.

**Bigger — why search explodes:**

- $k=10$: $199,409,619,829,1039,1249,1459,1669,1879,2089$ — $d=210=2\cdot3\cdot5\cdot7$. $210$ mandatory. Starting at $199$ to avoid small composites hitting. You can test with computer — each term prime.

Simple reasoning: To get 10 primes, need $d$ multiple of $210$, else among 7 terms you'd hit multiple of 7. So search space steps of 210.

- $k=22$: Found 2008 by Wróblewski — required $d$ multiple of $19\#=9699690$ — almost 10 million step minimal. So you must check numbers spaced 10 million apart for 22 primes all prime — probability tiny: each ~ $1/\log N$ prime, so $k$ primes probability $(1/\log N)^k$ — needs $N$ huge to get one success. For $k=22$, $N$ astronomically large.

- $k=25$: Formula $a_n=6171054912832631 + n\cdot366384\cdot23\#$ — $a_0$ 16 digits, $d=366384\cdot223,092,870\approx8.1\times10^{13}$. 25 terms. Found by Chermoni & Wróblewski 2008 after months distributed search.

- $k=27$ — **current world record 2019** Rob Gahan + PrimeGrid volunteers:

$$a_n = 2245848550833 + n\cdot 4314276143\cdot23\#\quad n=0..26$$

where $23\#=223,092,870$, so

$$d = 4,314,276,143 \times 223,092,870 \approx 9.62\times10^{17}$$

$26$ steps span $26d\approx2.5\times10^{19}$ — from 2.2 trillion to 25 quintillion range. Each of 27 numbers proven prime with deterministic Miller-Rabin + ECPP. Search required years of CPU on PrimeGrid BOINC.

Why $23\#$? For $k=27$, need $d$ divisible by all primes $<27$ — $2,3,5,7,11,13,17,19,23$ → $23\#$. Could also be divisible by larger prime factor $4,314,276,143$ extra — to fine-tune residues to avoid small prime divisors of $a_n$.

**Why we will never find $k=100$ by brute force — simple math:**

- $d$ must be divisible by $97\# = 2\cdot3\cdot5\cdots97$ — product of primes <100. This is about $2.3\times10^{36}$ — 37 digits. Minimal step 37 digits.

- Heuristic: Probability $k$ numbers $a+nd$ all prime $\approx 1/(\log N)^k$. For $k=100$, $(\log N)^{100}$ huge — need $N$ enormous, far beyond $10^{100}$ — $a$ would have hundreds of digits, search space $(\log N)^{100}\approx$ impossible.

- Green-Tao gives no explicit $N(\delta,k)$ — best bounds tower-exponential — so doesn't help locate.

So Green-Tao tells us length-100 prime AP exists _somewhere_ — maybe at $10^{1000}$ or $10^{10^{100}}$ — but we will never see it.

This is same non-constructive flavor as van der Waerden $W(2,6)=1132$ — existence proved 1927, exact value found only 2008 via SAT solver searching 30 orders of magnitude. And $W(2,7)$ still unknown, estimated >$10^4$.

> **Takeaway:** Existence ≠ construction. Ramsey theory guarantees order eventually, but location may be vastly beyond computational reach. Primes contain 100-term equally spaced line, but universe too big to find it — like guaranteeing a specific grain of sand exists somewhere in cosmos without telling which galaxy.

### Why It Is Culmination — Simple Explanation for First Time

This is end of 100-year story with same moral, each time stronger:

**Ladder:**

- **Gomory 1960s:** Chessboard $8\times8$ minus two opposite corners cannot be tiled by dominoes. Why? Count $W=30$ white, $B=32$ black, each domino covers 1 white 1 black. Budget $W-B\neq0$ forces impossibility. Simple counting forces global structure.

- **Egregium Theorema Gauss 1827:** Curvature $K$ budget forces no isometry. Sphere cannot be flattened to plane because $K=1/R^2$ vs $0$. Budget = curvature difference.

- **Ramsey $R(3,3)=6$ 1930:** Host = 6 people, color edge red = knows, blue = strangers. Budget 5 people can avoid monochrome triangle, 6 forces it. Complete disorder in friendships impossible.

- **Hales-Jewett 1963:** Host = high-dimensional cube $[k]^n$ — words length $n$. Budget dimension $n=HJ(k,c)-1$ can avoid monochrome combinatorial line, $HJ$ forces it. This implies van der Waerden — AP coded as word.

- **Erdős–Szekeres 1935:** Host = points in plane. Budget $2^{n-2}$ points can avoid convex $n$-gon, $2^{n-2}+1$ forces it. Geometry forces order.

- **van der Waerden 1927:** Host = integers colored with $r$ colors. Budget $W(r,k)-1$ length can avoid $k$-AP monochrome, $W$ forces it. Disorder = finite coloring, cannot destroy all APs.

- **Szemerédi 1975:** Host = dense set density $\delta>0$. Budget $N(\delta,k)-1$ size can avoid $k$-AP, $N$ forces it. Disorder = thickness, not coloring. Much stronger — you don't need to color everything, just be thick.

- **Green-Tao 2004:** Host = primes density 0. Budget = pseudorandomness. Primes look random, but relative density inside pseudorandom envelope $\nu$ positive → forces $k$-AP.

Each step weakens hypothesis — needs less about host — but keeps same conclusion: AP / convex / monochrome forced.

> **Disorder budget finite.**

For Gomory, budget = imbalance count. For Ramsey, budget = number of vertices. For van der Waerden, budget = length $W-1$. For Szemerédi, budget = $1/\delta$ — sparser you are, longer you can avoid, but if $\delta>0$ fixed, avoidance length finite.

For Green-Tao, budget = how random you look. Primes look random locally — gaps irregular, no formula — but globally their randomness is _shallow_. They live inside Selberg sieve envelope $\nu$ that is truly random for counting APs. Since primes occupy positive fraction of envelope, they inherit envelope's Ramsey property.

> - **Van der Waerden**: You paint whole infinite street $r$ colors. Some color must contain equally spaced houses. You must paint everything.
> - **Szemerédi**: You don't paint everything. You just own $1\%$ of houses scattered. If you keep $1\%$ forever, some $k$ equally spaced houses you own forced.
> - **Green-Tao**: You own $0\%$ in limit — primes get rarer. Naively you could avoid equally spaced houses, like powers of 2 do. But primes are not adversarially placed — they are pseudorandomly placed. Pseudorandom $0\%$ set can still force APs if it sits inside random cloud with positive relative density. Powers of 2 fail because their cloud not pseudorandom — powers of 2 highly structured, not uniform in Gowers norm.

**Why primes were supposed to be counterexample:**

For century, primes thought enemy of patterns — Euclid proves infinitely many, but no formula. Cramér model 1936 models primes as random set where $n$ prime with probability $1/\log n$ independently. Random set contains $k$-APs with probability 1 for each fixed $k$, but random model not proof.

Many thought density-zero sets could avoid APs — squares have no 4-term AP, powers of 2 have no 3-term AP. So primes could be like that.

Green-Tao shows: Even most famous pseudorandom set cannot escape perfect arithmetic order if you look far enough. Chaos only local — up to $10^6$, primes look irregular — globally, order forced at scale $10^{19}$ for $k=27$, at far larger scale for $k=100$.

**Final meta-theorem:**

> **Structure vs randomness dichotomy, structure wins eventually.**

Every proof in hierarchy uses same scheme: If no structure, then randomness/uniformity → counting lemma gives many patterns → contradiction. If not random, then correlation with structured object → density increment on substructure → induction, budget decreases.

For Green-Tao, this dichotomy lifted to relative world — even sparse primes obey it because envelope $\nu$ provides random background to compare to.

Thus Green-Tao is ultimate vindication of Ramsey philosophy: **Even the set that looks most random cannot escape perfect arithmetic order.**

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

If Roth says dense sets must contain $3$-AP, Behrend says you can be almost dense and still avoid one. Ultimate counterexample — lower bound sandwiching $r_{3}(N)$.

Let

$$\displaystyle r_{3}(N)=\max\left\{\left|A\right|:A\subset[1,N],\,A\text{ contains no }a,a+d,a+2d,\;d\neq0\right\}.$$

- Roth upper: $r_{3}(N)$ cannot be too big, otherwise $3$-AP forced.
- Behrend lower: $r_{3}(N)$ can be at least this big while AP-free.

Together:

$$\displaystyle N\cdot\exp\!\left(-C\sqrt{\log N}\right)\le r_{3}(N)\le\dfrac{N}{\left(\log N\right)^{1+c}}$$

For $62$ years Behrend lower unbeaten. Shattered pre-1946 intuition that AP-free sets must be polynomially small.

### Intuition Before Behrend: Power-Law Conjecture

Erdős and Turán $1930$s conjectured AP-free must be tiny, like $\displaystyle N^{0.9}$ or $\displaystyle N^{1-\epsilon}$ or even $\displaystyle\frac{N}{\left(\log N\right)^{C}}$ — power-law saving over $N$.

**Simple picture:** You want many numbers from $\left[1,N\right]$ with no three equally spaced. How many can you keep? If you keep $N^{0.9}$, you keep almost all — $10\%$ loss in exponent. If you keep $\displaystyle\frac{N}{\left(\log N\right)^{C}}$, you keep $N$ divided by slowly growing factor.

**Why they thought power-law small:** easy greedy construction gives $\displaystyle N^{0.63}$ and looks optimal.

Construction — numbers with no digit $2$ in base $3$, Stanley sequence:

$$\displaystyle A_{3}=\left\{ n : \text{base-}3\text{ expansion of }n\text{ uses only }0,1\right\}=\left\{0,1,3,4,9,10,12,13,\dots\right\}$$

Take $x,y,z\in A_{3}$ with $x+z=2y$. Look digitwise: each digit $x_{i},z_{i}\in\left\{0,1\right\}$, so $x_{i}+z_{i}\in\left\{0,1,2\right\}$. $2y_{i}\in\left\{0,2\right\}$. For equality $x_{i}+z_{i}=2y_{i}$ without carries — base $3$ large enough — need $x_{i}+z_{i}=0$ or $2$. If $1$, left $1$ odd cannot equal $0$ or $2$. So forces $x_{i}=z_{i}=y_{i}$. Thus $x=z=y$ — no nontrivial $3$-AP.

Size: up to $\displaystyle 3^{k}$, numbers with $k$ base-$3$ digits using $0,1$ only are $\displaystyle2^{k}$. So $N=3^{k}$ gives $\left|A\right|=2^{k}=N^{\log_{3}2}$.

$$\displaystyle \log_{3}2=\dfrac{\log2}{\log3}\approx0.6309$$

So $\displaystyle\left|A\right|=N^{\log_{3}2}\approx N^{0.63}$ AP-free.

If simple greedy gives $\displaystyle N^{0.63}$, perhaps maximal is $\displaystyle N^{0.9}$? Could you do much better? $1930$s intuition: you cannot get close to $N$ — must lose power $\displaystyle N^{\epsilon}$.

Behrend $1946$ destroyed this.

**What Behrend showed:** $\displaystyle N^{1-o(1)}$ possible — $\displaystyle\frac{N}{\text{something growing slower than }N^{\epsilon}}$ for any $\epsilon>0$.

Precise meaning $N^{1-o(1)}$:

$$\displaystyle \frac{\log r_{3}(N)}{\log N}\to1$$

So

$$\displaystyle r_{3}(N)=N\cdot\exp\!\left(-o\!\left(\log N\right)\right)$$

not $\displaystyle N^{1-\epsilon}=N\cdot\exp\!\left(-\epsilon\log N\right)$.

In words: ratio $\displaystyle\frac{r_{3}(N)}{N}=\exp\!\left(-o(\log N)\right)$ tends to $0$, but slower than any $\displaystyle N^{-\epsilon}=\exp\!\left(-\epsilon\log N\right)$. You lose factor $\displaystyle\exp\!\left(o(\log N)\right)$, which is $\displaystyle N^{o(1)}$, negligible compared to $\displaystyle N^{\epsilon}$.

**Compare table**

| $N$        | Power law $\displaystyle N^{0.9}$ | Behrend $\displaystyle N\cdot\exp\!\left(-\sqrt{\log N}\right)$ | Density $\displaystyle\frac{\left                                                                                                    | A\right | }{N}$ |
| :--------- | :-------------------------------- | :-------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- |
| $10^{4}$   | $3981$                            | $\sim1800$                                                      | $\displaystyle18\%$                                                                                                                  |
| $10^{10}$  | $10^{9}$                          | $3.1\times10^{8}$                                               | $\displaystyle3.1\%$                                                                                                                 |
| $10^{20}$  | $10^{18}$                         | $6.7\times10^{17}$                                              | $\displaystyle6.7\%$ — wait $\displaystyle\frac{6.7\times10^{17}}{10^{20}}=0.0067=0.67\%$ actually, but order $\displaystyle10^{-2}$ |
| $10^{100}$ | $10^{90}$                         | $3.8\times10^{95}$                                              | $\displaystyle10^{-5}$ fraction, but $\displaystyle10^{5}$ times larger than $N^{0.9}$                                               |

Check: For $N=10^{100}$, $\displaystyle N^{0.9}=10^{90}$, Behrend $\approx3.8\times10^{95}$ —

$$\displaystyle \frac{3.8\times10^{95}}{10^{90}}=3.8\times10^{5}$$

times larger. So eventually Behrend vastly beats power law.

**Why $\displaystyle\exp\!\left(-\sqrt{\log N}\right)$ slower decay than $\displaystyle N^{-\epsilon}$:**

$\displaystyle\exp\!\left(-\sqrt{\log N}\right)$ decays to $0$ slower than any $N^{-\epsilon}=\exp\!\left(-\epsilon\log N\right)$, because

$$\displaystyle \sqrt{\log N}\ll\epsilon\log N\quad\text{as }N\to\infty$$

for any fixed $\epsilon>0$. Square root vs linear — linear wins.

So:

$$\displaystyle \frac{N\cdot\exp\!\left(-\sqrt{\log N}\right)}{N^{1-\epsilon}}=\frac{N}{N^{1-\epsilon}}\cdot\exp\!\left(-\sqrt{\log N}\right)=N^{\epsilon}\exp\!\left(-\sqrt{\log N}\right)=\exp\!\left(\epsilon\log N-\sqrt{\log N}\right)\to\infty$$

Numerator $\displaystyle\epsilon\log N$ dominates $\displaystyle\sqrt{\log N}$. Ratio $\to\infty$.

In plain: $N^{\epsilon}$ grows much faster than $\displaystyle\exp\!\left(\sqrt{\log N}\right)$. So dividing $N$ by $\displaystyle\exp\!\left(\sqrt{\log N}\right)$ loses much less than dividing $N$ by $N^{\epsilon}= \exp(\epsilon\log N)$.

Hence Behrend sets eventually vastly larger than any power-law bound $\displaystyle N^{1-\epsilon}$. Erdős-Turán power-law false — you can stay within $\displaystyle N^{1-o(1)}$.

**Clarification on history:**

Erdős-Turán $1936$ actually conjectured stronger: $\displaystyle r_{k}(N)=o(N)$ — density $0$, not just power law. But many believed true order $\displaystyle N/\left(\log N\right)^{C}$ or $\displaystyle N^{1-c}$ — some polynomial saving.

Behrend showed even $\displaystyle\frac{N}{\left(\log N\right)^{100}}$ eventually smaller than Behrend? No, compare: $\displaystyle\frac{N}{\left(\log N\right)^{100}}$ vs $\displaystyle\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}$. Since

$$\displaystyle \exp\!\left(C\sqrt{\log N}\right)\gg\left(\log N\right)^{100}\quad\text{for large }N$$

because $\displaystyle C\sqrt{\log N}\gg100\log\log N$, we have

$$\displaystyle \frac{N}{\exp\!\left(C\sqrt{\log N}\right)}\ll\frac{N}{\left(\log N\right)^{100}}$$

so Behrend lower does not rule out $\displaystyle N/\left(\log N\right)^{100}$ upper — it rules out $\displaystyle N^{0.99}=N/N^{0.01}$ upper, since $\displaystyle N^{0.01}=\exp\!\left(0.01\log N\right)\gg\exp\!\left(C\sqrt{\log N}\right)$.

Important distinction:

- Power-law $\displaystyle N^{1-\epsilon}$ ruled out — cannot have $\displaystyle r_{3}(N)\le N^{1-\epsilon}$.
- Polylog $\displaystyle N/\left(\log N\right)^{C}$ still possible — and Bloom-Sisask proved $\displaystyle N/\left(\log N\right)^{1+c}$ indeed upper bound, consistent with Behrend.

Thus Behrend killed $\displaystyle N^{0.9}$ guess, forced new regime $\displaystyle N^{1-o(1)}$ — intermediate between polynomial $\displaystyle N^{1-\epsilon}$ and $\displaystyle N/\text{polylog}$. Lives in strange zone $\displaystyle\exp\!\left(-C\sqrt{\log N}\right)$ — decays faster than $\displaystyle1/\text{polylog}$? No, decays slower than $\displaystyle1/\text{polylog}$? Actually $\displaystyle\exp\!\left(-C\sqrt{\log N}\right)\ll\frac{1}{\left(\log N\right)^{100}}$, so Behrend density smaller than polylog density — but still $\displaystyle N^{o(1)}$ close to $N$.

This is why $r_{3}(N)$ problem hard: true answer lives in $\displaystyle N^{1-o(1)}$ regime where linear Fourier cannot reach — needs quadratic Fourier, Bohr sets, spectral boosting.

### Construction: Spheres Have No $3$-Term Lines

Key geometric fact: line intersects sphere in at most $2$ points. If $x,y,z$ distinct collinear with $y$ midpoint of $x,z$, cannot all lie on same sphere centered at origin, because

$$\displaystyle \left\|y\right\|^{2}=\left\|\frac{x+z}{2}\right\|^{2}<\frac{\left\|x\right\|^{2}+\left\|z\right\|^{2}}{2}$$

by strict convexity of $\displaystyle L^{2}$ norm unless $x=z$.

So sphere is $3$-AP-free.

**Why? Simple terms:** Take any sphere — e.g., circle in plane. Take two distinct points $x,z$ on circle. Their midpoint $y=\frac{x+z}{2}$ lies strictly inside circle — closer to center — not on circle, unless $x=z$. This is because sphere bulges outward — straight line chord inside.

If $x,y,z$ form $3$-AP in $\mathbb{Z}^{d}$, meaning $\displaystyle x+z=2y$, then $y$ is midpoint, $x,y,z$ collinear. So if all three on same sphere radius $R$, then $\left\|x\right\|^{2}=\left\|y\right\|^{2}=\left\|z\right\|^{2}=R$, but midpoint inequality gives $\left\|y\right\|^{2}<R$ contradiction unless $x=z$. So no distinct triple in AP can sit on one sphere.

This geometric observation turns AP-free problem into sphere-packing.

**Step 1: Grid in high dimensions.**

Fix integers $d,m$. Grid

$$\displaystyle G=\left\{0,1,\dots,m-1\right\}^{d}\subset\mathbb{Z}^{d}$$

Think $d$-dimensional cube with side $m$. Size

$$\displaystyle \left|G\right|=m^{d}$$

For $x\in G$, squared length

$$\displaystyle S(x)=\sum_{i=1}^{d}x_{i}^{2}=\left\|x\right\|^{2}$$

ranges $\displaystyle0$ to $d(m-1)^{2}$ — at most $\displaystyle dm^{2}$ distinct integer values, because each $x_{i}^{2}\le(m-1)^{2}$, sum $\le d(m-1)^{2}<dm^{2}$.

Only $\displaystyle dm^{2}$ possible $S$ values, but $\displaystyle m^{d}$ points. Pigeonhole principle: some $R$ gets many points:

$$\displaystyle \exists R:\;\left|\left\{x\in G:\left\|x\right\|^{2}=R\right\}\right|\ge\frac{m^{d}}{dm^{2}}=\frac{m^{d-2}}{d}$$

Average points per radius at least total divided by number radii. So there exists sphere radius $\sqrt{R}$ containing at least $\displaystyle\frac{m^{d-2}}{d}$ grid points.

Call set $T_{R}$ — all grid points on that sphere.

$T_{R}$ has no $3$-AP in $\mathbb{Z}^{d}$: if $x+z=2y$ with $x,z\in T_{R}$, $x\neq z$, then $y$ midpoint would also need $\left\|y\right\|^{2}=R$ to stay in $T_{R}$, impossible by convexity as above.

**Simple count example:** Take $d=2$, $m=3$, $G=3\times3=9$ points. $S$ values $0,1,2,4,5,8$. Pigeonhole: some $R$ has $\ge 9/8$ points? Actually $\ge2$. Sphere $R=1$ has $(1,0),(0,1)$ — 2 points — no $3$-AP.

In high $d$, pigeonhole gain huge: $m^{d}$ vs $dm^{2}$ — exponential vs polynomial.

**Step 2: Map to integers without creating APs.**

Need set of integers AP-free, not $\mathbb{Z}^{d}$ points. Encode vector as base-$(2m)$ number:

$$\displaystyle \phi(x)=\sum_{i=1}^{d}x_{i}(2m)^{i-1}=x_{1}+x_{2}(2m)+x_{3}(2m)^{2}+\cdots+x_{d}(2m)^{d-1}$$

Why base $2m$? Digits $x_{i}\in[0,m-1]$, so $x_{i}+z_{i}\in[0,2m-2]<2m$. No carry when adding in base $2m$. Similarly $2y_{i}\in[0,2m-2]<2m$ no carry.

Thus

$$\displaystyle \phi(x)+\phi(z)=2\phi(y)\iff x_{i}+z_{i}=2y_{i}\;\forall i\iff x+z=2y$$

coordinate-wise. Equality of integers equivalent to equality digitwise because no carries.

Since $T_{R}$ has no solution $x+z=2y$ with $x\neq z$, $\phi(T_{R})$ has no $3$-term AP in integers.

Where does $\phi(T_{R})$ live? Max value $< (2m)^{d}$, because largest digit $m-1<2m$, so

$$\displaystyle A=\phi(T_{R})\subset\left[0,(2m)^{d}\right)$$

AP-free with

$$\displaystyle \left|A\right|\ge\frac{m^{d-2}}{d}$$

**Simple terms:** We turned $d$-dimensional points into $1$-dimensional numbers by writing coordinates as digits in large base — like packing vector into decimal expansion. Base large enough prevents digits interfering. AP property preserved digitwise.

**Step 3: Optimize $d,m$.**

We have $N\approx(2m)^{d}$. So $\displaystyle\log N\approx d\log(2m)$.

Size $\displaystyle\left|A\right|\ge\frac{m^{d-2}}{d}=\frac{(2m)^{d}}{d(2m)^{2}2^{d}}\cdot 2^{d}$? Let's compute clean:

$$\displaystyle \frac{m^{d-2}}{d}= \frac{(2m)^{d}}{d}\cdot\frac{m^{d-2}}{(2m)^{d}}=\frac{(2m)^{d}}{d}\cdot\frac{1}{m^{2}2^{d}}=\frac{N}{d\,m^{2}2^{d}}$$

up to factor. So

$$\displaystyle \frac{\left|A\right|}{N}\ge\frac{1}{d\,m^{2}2^{d}}$$

Take logs: $\displaystyle\log\left(\frac{N}{\left|A\right|}\right)\approx\log d+2\log m+d\log2$.

We want minimize this loss given $d\log(2m)\approx\log N$.

Set $\displaystyle d\approx\sqrt{\log N}$ and $\displaystyle\log m\approx\sqrt{\log N}$ — balance $2\log m\approx d$.

More precisely choose

$$\displaystyle d=\left\lfloor\sqrt{\frac{\log N}{\log2}}\right\rfloor,\quad m=\left\lfloor\frac{1}{2}N^{1/d}\right\rfloor\approx\exp\!\left(\sqrt{\log N}\right)$$

Then $(2m)^{d}=N$ and

$$\displaystyle \log\left(\frac{N}{\left|A\right|}\right)=O\!\left(\sqrt{\log N}\right)$$

so

$$\displaystyle \left|A\right|=N\cdot\exp\!\left(-O\!\left(\sqrt{\log N}\right)\right)$$

Precise bound Behrend proved:

$$\displaystyle r_{3}(N)\ge N\cdot\exp\!\left(-C\sqrt{\log N}\right)$$

for absolute $C$, original $C=2\sqrt{2}+o(1)$ after optimization $\displaystyle C=2\sqrt{2\log2}$ etc.

**Simple final picture:** High dimension $d$ gives many points per sphere — $m^{d}/dm^{2}$ — but encoding blows up $N=(2m)^{d}$ exponential in $d$. Too small $d$, pigeonhole weak; too large $d$, $2^{d}$ loss big. Optimum $d\approx\sqrt{\log N}$ balances — loss $\displaystyle\exp\!\left(C\sqrt{\log N}\right)$.

Result: AP-free set almost size $N$ — density $\displaystyle\exp\!\left(-C\sqrt{\log N}\right)$ — decays slower than any power $N^{-\epsilon}$, so $r_{3}(N)=N^{1-o(1)}$.

### Elkin's Tweak 2008 — Thick Shell

$62$ years no one beat Behrend. Problem: Behrend uses infinitely thin sphere — only points with exactly $\displaystyle\left\|x\right\|^{2}=R$. Most points near but not exactly on that radius wasted.

**Simple count of waste:** Grid $G=\left\{0,\dots,m-1\right\}^{d}$ has $m^{d}$ points. Values $S(x)=\left\|x\right\|^{2}$ range $\left[0,dm^{2}\right]$, about $dm^{2}$ possibilities. Best sphere gets $\displaystyle\frac{m^{d}}{dm^{2}}$ points. But total points $m^{d}$ — we keep only $\displaystyle\frac{1}{dm^{2}}$ fraction — about $\displaystyle\frac{1}{\text{poly}(d,m)}$ fraction. Most points lie on other radii, not used.

Idea: use thick shell — doughnut — to keep many radii at once.

$$\displaystyle \text{Shell}_{R,\delta}=\left\{x\in G : R\le\left\|x\right\|^{2}\le R+\delta\right\}$$

Layer thickness $\delta$. Number of points roughly $\displaystyle\approx\delta\cdot\frac{m^{d}}{dm^{2}}$ if radii distribution roughly uniform — $\delta$ times more than thin sphere.

For $\delta\approx\sqrt{d}$, get factor $\sqrt{d}\approx\left(\log N\right)^{1/4}$ extra — small but real.

**But problem:** thin sphere is perfectly $3$-AP-free — line hits sphere at most $2$ points. Thick shell is not: line can go through shell, exit, re-enter? Actually convex shell: line can intersect thick shell in $3$ points? Yes. Take $x,z$ on outer radius, midpoint $y$ may fall inside shell thickness — still inside shell — so $x,y,z$ all in shell forming $3$-AP. So thick shell contains many $3$-APs.

Elkin innovation: inside thick shell, $3$-APs are still rare if $\delta$ small relative to $m^{2}$.

**Count $3$-APs In Shell:**

Take $x,z\in\text{Shell}$, $y=\frac{x+z}{2}$ integer midpoint. Condition $x+z=2y$. When does $y$ stay in shell?

Write $\left\|y\right\|^{2}= \left\|\frac{x+z}{2}\right\|^{2}= \frac{\left\|x\right\|^{2}+\left\|z\right\|^{2}}{2}-\frac{\left\|x-z\right\|^{2}}{4}$

by parallelogram law:

$$\displaystyle \left\|\frac{x+z}{2}\right\|^{2}+\left\|\frac{x-z}{2}\right\|^{2}= \frac{\left\|x\right\|^{2}+\left\|z\right\|^{2}}{2}$$

So

$$\displaystyle \left\|y\right\|^{2}= \frac{\left\|x\right\|^{2}+\left\|z\right\|^{2}}{2}-\frac{\left\|x-z\right\|^{2}}{4}$$

If $\left\|x\right\|^{2},\left\|z\right\|^{2}\in\left[R,R+\delta\right]$, then average $\in\left[R,R+\delta\right]$, but subtracting $\displaystyle\frac{\left\|x-z\right\|^{2}}{4}$ pushes $\left\|y\right\|^{2}$ below $R$ unless $\left\|x-z\right\|^{2}\le4\delta$.

Thus for $y$ to stay in shell $\left[R,R+\delta\right]$, need $\displaystyle\left\|x-z\right\|^{2}\le4\delta$ — $x,z$ close.

So $3$-APs in thick shell correspond to pairs $x,z$ close: distance $\le2\sqrt{\delta}$.

Number of such close pairs much smaller than total pairs if $\delta\ll m^{2}$.

Formal count: For fixed $x$, number of $z$ with $\left\|x-z\right\|\le2\sqrt{\delta}$ about volume of ball radius $2\sqrt{\delta}$ in $\mathbb{Z}^{d}$ — about $\displaystyle\left(C\sqrt{\delta/d}\right)^{d}$? Actually $\approx\left(\frac{c\delta}{d}\right)^{d/2}$ tiny if $\delta\ll d m^{2}$.

Elkin chooses $\delta=c_{1}d$ or $\approx\sqrt{d}$? Standard choice $\delta\approx c d$ gives extra $\sqrt{d}$ gain. Let's follow Elkin optimal: $\delta\approx m^{2}/\sqrt{d}$? Wait need precise.

Elkin's analysis: Choose $m$ large, $d\approx\sqrt{\log N}$, shell thickness $\displaystyle\delta\approx c\frac{m^{2}}{\sqrt{d}}$? Different parametrizations equivalent.

Simplify: choose $\delta\approx\epsilon m^{2}$ small constant fraction, then ball volume still $\approx(\epsilon)^{d/2}m^{d}$ — still exponential but factor $(\epsilon)^{d/2}$ small. Number of $3$-APs in shell about $m^{d}\cdot(\text{small})^{d}$ $\ll$ shell size.

Thus we can destroy all $3$-APs by deleting one point per AP, losing little.

**Probabilistic deletion method**

1. Take thick shell $S=\text{Shell}_{R,\delta}$ size $\displaystyle\left|S\right|\approx\delta\frac{m^{d}}{dm^{2}}$.
2. Count number of $3$-APs inside $S$: call $T$ = number of triples $\left\{x,y,z\right\}$ with $x+z=2y$, $x\neq z$, all in $S$. Show $T\ll\left|S\right|$ if $\delta$ not too large — e.g., $T\le\left|S\right|/10$.
3. Form random subset $S'$ by picking each $x\in S$ with probability $p\approx\frac{1}{2}$? Actually Elkin picks random shift + then deletion: for each $3$-AP triple, delete one point. Number deleted $\le T$. So remaining $\left|S'\right|\ge\left|S\right|-T\ge\frac{9}{10}\left|S\right|$ — still large, now $3$-AP-free.

More careful Elkin uses random subset where each point kept with probability $p$ small to reduce $T$ to $p^{3}T$ while keeping $p\left|S\right|$ points — choose $p$ so $p^{3}T\ll p\left|S\right|$.

Result after deletion: $3$-AP-free set in $\mathbb{Z}^{d}$ size $\approx\left|S\right|$.

Then map to integers via same base-$(2m)$ map $\displaystyle\phi(x)=\sum_{i=1}^{d}x_{i}(2m)^{i-1}$ — still no carries, preserves AP-free.

**Result:**

$$\displaystyle r_{3}(N)\ge C_{1}\frac{N\log^{1/4}N}{\exp\!\left(2\sqrt{2}\sqrt{\log N}\right)}$$

for $C_{1}>0$.

Some forms write:

$$\displaystyle r_{3}(N)\ge\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}\cdot\log^{1/4}N$$

i.e., Behrend $\displaystyle\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}$ times extra $\displaystyle\log^{1/4}N$.

**Why $\log^{1/4}N$? Simple origin:**

Optimal $d\approx\sqrt{\frac{2}{\log2}\log N}$. Thickness $\delta\approx c\sqrt{d}\,m^{2}$? Shell volume $\propto\delta$ gives factor $\delta/(m^{2})\propto\sqrt{d}\propto\left(\log N\right)^{1/4}$. Indeed $\sqrt{d}=\left(\log N\right)^{1/4}$ up to constants.

So extra factor is $\displaystyle\sqrt{d}=\left(\log N\right)^{1/4}$.

Green & Wolf 2010 refined constant to

$$\displaystyle r_{3}(N)\ge C\frac{N\log^{1/4}N}{2^{2\sqrt{2}\sqrt{\log_{2}N}}}= \frac{N\log^{1/4}N}{\exp\!\left(2\sqrt{2\log2}\sqrt{\log N}\right)}$$

with $C=2\sqrt{2\log2}\approx2.355...$ improved $C$ from $2\sqrt{2}\approx2.828$.

Improvement tiny — $\sqrt{\log N}$ vs $\exp(\sqrt{\log N})$ — dominant term still $\displaystyle\exp\!\left(-C\sqrt{\log N}\right)$. But conceptually huge: showed Behrend not optimal, thick shells can be made to work, opened door to further improvements via more efficient removal, using central limit theorem for distribution of $\left\|x\right\|^{2}$ — Gaussian — to get more precise density of shell.

In Fourier language: Behrend sets are $U^{2}$-uniform — no large linear Fourier coefficient — but have quadratic structure sphere. Elkin shows you can take thickened quadratic level set and still kill remaining additive structure by sparse random deletion — first use of probabilistic method inside Behrend construction.

### Why It Defines Boundary for Roth and Szemerédi

Behrend tells us:

> You cannot prove $\displaystyle r_{3}(N)\le N^{0.99}$. You cannot even prove $\displaystyle r_{3}(N)\le\dfrac{N}{\exp\!\left(c\sqrt{\log N}\right)}$ with $c<C$. Because Behrend sets of size $\displaystyle\frac{N}{\exp\!\left(C\sqrt{\log N}\right)}$ AP-free exist.

**Correction of common confusion:**

Many think Behrend rules out $\displaystyle\frac{N}{\left(\log N\right)^{100}}$ upper bound. It does not.

Compare growth:

$$\displaystyle \exp\!\left(C\sqrt{\log N}\right)\quad\text{vs}\quad\left(\log N\right)^{100}$$

Take logs:

$$\displaystyle \log\left(\exp\!\left(C\sqrt{\log N}\right)\right)=C\sqrt{\log N}$$

$$\displaystyle \log\left(\left(\log N\right)^{100}\right)=100\log\log N$$

Since $\displaystyle\sqrt{\log N}\gg\log\log N$ as $N\to\infty$, we have

$$\displaystyle \exp\!\left(C\sqrt{\log N}\right)\gg\left(\log N\right)^{100}\quad\text{eventually}$$

Thus

$$\displaystyle \frac{N}{\exp\!\left(C\sqrt{\log N}\right)}\ll\frac{N}{\left(\log N\right)^{100}}$$

Behrend lower bound is smaller than $\displaystyle\frac{N}{\left(\log N\right)^{100}}$, so $\displaystyle\frac{N}{\left(\log N\right)^{100}}$ upper bound is still possible — and indeed Bloom-Sisask proved $\displaystyle\frac{N}{\left(\log N\right)^{1+c}}$ which is $\ll\frac{N}{\left(\log N\right)^{100}}$? Actually $\displaystyle\frac{N}{(\log N)^{1+c}}\gg\frac{N}{(\log N)^{100}}$ for large $c$? Wait $1+c\approx1.01$ vs $100$, so $N/(\log N)^{1.01}$ much larger than $N/(\log N)^{100}$. So $\displaystyle N/(\log N)^{100}$ upper would be stronger than Bloom-Sisask. Behrend does not rule it out.

What Behrend does rule out:

$$\displaystyle r_{3}(N)\le N^{0.99}= \frac{N}{N^{0.01}}$$

Because

$$\displaystyle N^{0.01}=\exp\!\left(0.01\log N\right)\gg\exp\!\left(C\sqrt{\log N}\right)$$

for large $N$, since $0.01\log N\gg C\sqrt{\log N}$. So $\displaystyle\frac{N}{N^{0.01}}\ll\frac{N}{\exp(C\sqrt{\log N})}$ — if you claimed $r_{3}(N)\le N^{0.99}$, you would claim maximal AP-free $\le$ smaller than Behrend construction which we know exists size $\displaystyle\frac{N}{\exp(C\sqrt{\log N})}$ — contradiction. So $\displaystyle N^{1-\epsilon}$ upper impossible.

Precise barrier: You cannot prove

$$\displaystyle r_{3}(N)\le\frac{N}{\exp\!\left(c\sqrt{\log N}\right)}\quad\text{for any }c>C_{\text{Behrend}}$$

Because construction achieves $\displaystyle\frac{N}{\exp(C\sqrt{\log N})}$. But you could hope to prove $\displaystyle r_{3}(N)\le\frac{N}{\exp(c\sqrt{\log N})}$ with $c<C$? No, that would be weaker upper, larger bound — allowed. Actually lower bound says $r_{3}\ge N\exp(-C\sqrt{\log N})$, so any upper bound $\le N\exp(-c\sqrt{\log N})$ with $c>C$ would be $\ll$ lower bound eventually, impossible. So limit is $C$.

Thus true $r_{3}(N)$ lives in window:

$$\displaystyle N\exp\!\left(-C_{1}\sqrt{\log N}\right)\le r_{3}(N)\le\frac{N}{\left(\log N\right)^{1+c_{2}}}$$

Left almost $N$, right $N/\text{polylog}$.

**Why regularity lemma necessary:**

If AP-free sets were small like $\displaystyle N^{0.9}$, you could find $3$-AP by simple averaging — any dense set $\delta N$ with $\delta=N^{-0.1}$ would contain many triples $x,x+d,x+2d$ — $\approx\delta^{3}N^{2}$ expected — and pigeonhole would force.

Behrend showed AP-free sets can be large — $\displaystyle N^{1-o(1)}$ — density $\displaystyle\exp(-C\sqrt{\log N})$ which tends to $0$ slower than any $N^{-\epsilon}$. So they are almost dense, look random to linear tests, but hide structure.

They are pseudorandom: take Behrend set $A=\phi(T_{R})$. Its balanced function $f=1_{A}-\delta1_{[1,N]}$ has

$$\displaystyle \left|\widehat{f}(r)\right|=\left|\frac{1}{N}\sum_{x\in A}e^{2\pi i r x/N}-\delta\frac{1}{N}\sum_{x\le N}e^{2\pi i r x/N}\right|=o(\delta N)$$

for all $r\neq0$ — no large linear Fourier coefficient. In Gowers norms:

$$\displaystyle \left\|1_{A}-\delta\right\|_{U^{2}}=o(1)$$

$U^{2}$-uniform — looks random to Roth test.

But

$$\displaystyle \left\|1_{A}-\delta\right\|_{U^{3}}\gg1$$

large — has quadratic bias — lives on sphere $\sum x_{i}^{2}=R$ — quadratic condition $\displaystyle\sum x_{i}^{2}=R$ preserved by $\phi$? Actually $\phi$ maps quadratic condition to digit quadratic.

So Roth linear Fourier cannot detect Behrend sets — they appear random to linear phases $\displaystyle e^{2\pi i r x/N}$. Therefore Roth method can never prove $\displaystyle r_{3}(N)\ll\frac{N}{\exp(\sqrt{\log N})}$ — would need to detect quadratic structure.

This forces higher-order Fourier analysis. Szemerédi regularity lemma was invented because such examples exist — need decomposition of any large set into structured part + pseudorandom part where structured part includes quadratic and higher-degree nilsequences, not just linear.

In Fourier terms:

- Behrend: $U^{2}$-uniform — $\displaystyle\left\|\cdot\right\|_{U^{2}}$ small — no linear bias.
- But $U^{3}$-nonuniform — $\displaystyle\left\|\cdot\right\|_{U^{3}}$ large — quadratic bias sphere.

Bloom-Sisask pushes Roth beyond $\displaystyle N/\log N$ by using spectral boosting — many large Fourier coefficients have additive structure — almost-periodicity — first step toward quadratic.

Full resolution $r_{3}(N)=N\exp(-\Theta(\sqrt{\log N}))$ conjectured — experts believe true size closer to Behrend lower than Roth upper — would require optimal quadratic Fourier inverse, which is exactly what $U^{3}$ inverse theorem does: if $\left\|f\right\|_{U^{3}}\ge\eta$, then $f$ correlates with quadratic phase $\displaystyle e^{2\pi i(\alpha n^{2}+\beta n)}$ or nilsequence.

Behrend construction is thus compass: it tells us maximal disorder avoiding order, and its size dictates how sophisticated order-finding tool must be — must be at least quadratic.

### Behrend-Roth Gap and Bloom-Sisask Closure

For $70$ years:

**Lower** — Behrend $1946$ + Elkin $2008$:

$$\displaystyle r_{3}(N)\ge C_{1}\frac{N\log^{1/4}N}{\exp\!\left(C_{0}\sqrt{\log N}\right)}=N\cdot\exp\!\left(-C_{0}\sqrt{\log N}+ \tfrac{1}{4}\log\log N+O(1)\right)$$

with $C_{0}=2\sqrt{2}\approx2.828$, later $C_{0}=2\sqrt{2\log2}\approx2.355$.

**Upper** — progression of improvements:

$$
\displaystyle \begin{aligned}
\text{Roth 1953:}&\quad r_{3}(N)\ll\frac{N}{\log\log N}\\
\text{Heath-Brown + Szemerédi:}&\quad r_{3}(N)\ll\frac{N}{\left(\log N\right)^{c}}\\
\text{Bourgain 1999:}&\quad r_{3}(N)\ll N\cdot\frac{\sqrt{\log\log N}}{\sqrt{\log N}}\\
\text{Bourgain 2008:}&\quad r_{3}(N)\ll N\cdot\frac{\left(\log\log N\right)^{2}}{\left(\log N\right)^{2/3}}\\
\text{Sanders 2011:}&\quad r_{3}(N)\ll\frac{N\left(\log\log N\right)^{5}}{\log N}
\end{aligned}
$$

**Massive gap**: $\displaystyle\exp\!\left(\sqrt{\log N}\right)$ vs $\displaystyle\log N$.

To see scale, write densities $\displaystyle\frac{r_{3}(N)}{N}$:

$$\displaystyle \exp\!\left(-C\sqrt{\log N}\right)\le\frac{r_{3}(N)}{N}\ll\frac{\left(\log\log N\right)^{5}}{\log N}$$

Take $N=10^{100}$: $\displaystyle\exp\!\left(-C\sqrt{\log N}\right)\approx10^{-5}$, $\displaystyle\frac{\left(\log\log N\right)^{5}}{\log N}\approx\frac{5^{5}}{230}\approx13\%$ — upper allows $13\%$, lower says $0.001\%$ achievable AP-free. Gap $10^{4}$ factor, grows.

**Bloom & Sisask 2020 closed half:**

$$\displaystyle r_{3}(N)\ll\frac{N}{\left(\log N\right)^{1+c}},\qquad c>0$$

First time upper bound is $\displaystyle o\!\left(\frac{N}{\log N}\right)$, smaller than $\displaystyle\frac{N}{\log N}$. Their $c\approx0.01$? Later Kelley-Meka $2023$ improved to $\displaystyle\exp\!\left(-c(\log N)^{1/12}\right)$? Actually Kelley-Meka broke to $\displaystyle\frac{N}{\exp(c(\log N)^{1/9})}$ — much closer to Behrend, but we keep focus on threshold.

**Why $\displaystyle\frac{N}{\log N}$ threshold matters — reciprocal sum viewpoint:**

Consider set $A\subset\mathbb{N}$ with counting function $\displaystyle A(N)=\left|A\cap[1,N]\right|$.

Reciprocal sum up to $N$:

$$\displaystyle S(N)=\sum_{\substack{a\in A\\a\le N}}\frac{1}{a}\approx\int_{2}^{N}\frac{dA(t)}{t}$$

Integration by parts:

$$\displaystyle S(N)=\frac{A(N)}{N}+\int_{2}^{N}\frac{A(t)}{t^{2}}dt$$

If $\displaystyle A(t)\approx\frac{t}{\log t}$, like primes by Prime Number Theorem $\displaystyle\pi(t)\sim\frac{t}{\log t}$, then

$$\displaystyle \int_{2}^{N}\frac{dt}{t\log t}= \log\log N\to\infty$$

So $\displaystyle\sum_{a\in A}\frac{1}{a}$ diverges — harmonic over $\displaystyle t\log t$.

If $\displaystyle A(t)\ll\frac{t}{\left(\log t\right)^{1+c}}$ with $c>0$, then

$$\displaystyle \int_{2}^{N}\frac{dt}{t\left(\log t\right)^{1+c}}=\frac{1}{c}\left(\frac{1}{\left(\log2\right)^{c}}-\frac{1}{\left(\log N\right)^{c}}\right)<\infty$$

converges, because $\displaystyle\int^{\infty}\frac{dx}{x(\log x)^{1+c}}<\infty$.

Thus:

- Density $\displaystyle\frac{t}{\log t}$ → divergent reciprocals.
- Density $\displaystyle\frac{t}{(\log t)^{1+c}}$ → convergent reciprocals.

Primes sit exactly at threshold $\displaystyle\frac{N}{\log N}$.

Erdős conjecture: If $\displaystyle\sum_{a\in A}\frac{1}{a}=\infty$, then $A$ contains $k$-AP for all $k$.

For $k=3$, need to show any $A$ with divergent reciprocals contains $3$-AP. Contrapositive: If $A$ is $3$-AP-free, then $\displaystyle\sum\frac{1}{a}<\infty$.

If we only knew Roth upper $\displaystyle\frac{N}{\log\log N}$, then $3$-AP-free could still have $\displaystyle A(N)\approx\frac{N}{\log\log N}$, and

$$\displaystyle \int\frac{dt}{t\log\log t}\sim\log N\cdot\text{? Actually }\int\frac{dt}{t\log\log t}\text{ diverges faster than }\log\log N$$

so reciprocal sum could diverge — cannot rule out. Need upper below $\displaystyle\frac{N}{\log N}$.

Bloom-Sisask $\displaystyle\ll\frac{N}{(\log N)^{1+c}}$ gives convergent reciprocals:

$$\displaystyle \text{if }A\;3\text{-AP-free}\implies A(N)\ll\frac{N}{(\log N)^{1+c}}\implies\sum_{a\in A}\frac{1}{a}<\infty$$

Hence any $A$ with $\displaystyle\sum\frac{1}{a}=\infty$ must contain $3$-AP — $k=3$ case of Erdős conjecture proved.

**Picture of gap closure:**

$$\displaystyle \underbrace{N\exp\!\left(-C\sqrt{\log N}\right)}_{\text{Behrend lower, maximal disorder you can build}} \le r_{3}(N) \le \underbrace{\frac{N}{(\log N)^{1+c}}}_{\text{Bloom-Sisask upper, order must appear}}$$

Left side says: you can avoid $3$-AP while keeping density $\displaystyle\exp(-C\sqrt{\log N})$.

Right side says: you cannot avoid $3$-AP if density $\displaystyle\ge(\log N)^{-1-c}$.

True $r_{3}(N)$ lies somewhere between. Behrend is compass — tells how far we can hope to push upper bound. Until we match $\displaystyle N\exp(-C\sqrt{\log N})$, we haven't finished — upper still larger than known construction.

Most experts believe true order closer to Behrend:

$$\displaystyle r_{3}(N)=N\exp\!\left(-\Theta\!\left(\sqrt{\log N}\right)\right)$$

meaning there exist constants $c_{1},c_{2}>0$ with

$$\displaystyle N\exp\!\left(-c_{1}\sqrt{\log N}\right)\le r_{3}(N)\le N\exp\!\left(-c_{2}\sqrt{\log N}\right)$$

Conjecture: exponent $\sqrt{\log N}$ is correct, only constant in front uncertain.

**Ramsey language:** Behrend is extremal construction for $R_{3}$, like $5$-cycle is for $R(3,3)=6$. $R(3,3)=6$ says any $2$-coloring of $K_{6}$ has monochrome triangle; $C_{5}$ coloring of $K_{5}$ shows $5$ not enough — maximal disorder avoiding order. Similarly Behrend set shows $N\exp(-C\sqrt{\log N})$ size can avoid $3$-AP — maximal disorder. Its size dictates how sophisticated order-finding tool must be: to beat $\displaystyle N/\log N$ need beyond linear Fourier — need to detect sphere quadratic structure $\displaystyle\sum x_{i}^{2}=R$. Roth tool sees only linear phases $\displaystyle e^{2\pi i r x/N}$ — blind to spheres. Bloom-Sisask and Kelley-Meka use almost-periodicity, spectral boosting, higher energies $\displaystyle E_{k}$ to detect quadratic bias.

In short: Behrend defines limit of avoidance, Roth defines guarantee of order, Bloom-Sisask bridges them at $\displaystyle\frac{N}{\log N}$ threshold — first time upper crosses divergent harmonic series barrier.
