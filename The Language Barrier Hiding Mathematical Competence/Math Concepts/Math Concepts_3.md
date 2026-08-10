## Lovász–Kneser Theorem

The Lovász–Kneser theorem states that the chromatic number of the Kneser graph $\displaystyle KG(n,k)$ is exactly $\displaystyle n-2k+2$. Proved by László Lovász in 1978, it resolved Martin Kneser's 1955 combinatorial conjecture and successfully launched the field of topological combinatorics.

### Core Concepts

- **Kneser Graph $\displaystyle KG(n,k)$:** Vertices = all $\displaystyle\binom{n}{k}$ $k$-subsets of $\displaystyle[n]=\{1,\dots,n\}$. Edge between $\displaystyle A,B$ iff $\displaystyle A\cap B=\emptyset$.

$$\displaystyle V(KG(n,k))=\{A\subset[n]:|A|=k\},\quad E=\{\{A,B\}:A\cap B=\emptyset\}$$

Interpretation: each vertex is a committee of size $\displaystyle k$ from $\displaystyle n$ people. Edge means committees completely disjoint — no common member. So graph encodes disjointness relation.

Size:

$$\displaystyle |V(KG(n,k))|=\binom{n}{k}=\dfrac{n!}{k!(n-k)!}$$

Degree: fix $\displaystyle A$, number of $\displaystyle B$ disjoint from $\displaystyle A$ is $\displaystyle\binom{n-k}{k}$, so regular degree $\displaystyle\binom{n-k}{k}$ if $\displaystyle n\ge2k$, otherwise $\displaystyle0$.

- **Chromatic Number $\displaystyle\chi(G)$:** Smallest $\displaystyle c$ so vertices can be colored with $\displaystyle c$ colors, no edge monochromatic. Formal:

$$\displaystyle \chi(G)=\min\{c:\exists f:V\to[c],\;uv\in E\implies f(u)\neq f(v)\}$$

$\displaystyle\chi$ measures how much intersection structure forces diversity. If graph has no edges, $\displaystyle\chi=1$. If contains clique size $\displaystyle\omega$, then $\displaystyle\chi\ge\omega$.

- **Kneser's Conjecture 1955:** $\displaystyle\chi(KG(n,k))=n-2k+2$ for $\displaystyle n\ge2k$.

If $\displaystyle n<2k$, any two $\displaystyle k$-sets intersect by pigeonhole principle:

$$\displaystyle |A|+|B|=2k>n\implies|A\cap B|\ge2k-n\ge1$$

So $\displaystyle E=\emptyset$, edgeless, $\displaystyle\chi=1$. Interesting only when $\displaystyle n\ge2k$, disjoint pairs exist.

Kneser intuition: to color so disjoint sets get different colors, need $\displaystyle n-2k+2$ colors. Try with fewer, you must give same color to two disjoint sets — violates coloring.

**Deep expansion of each concept**

#### 1. Kneser Graph $\displaystyle KG(n,k)$

**Ground set:**

$$\displaystyle [n]=\{1,2,\dots,n\}$$

**Vertices:** Every $\displaystyle k$-element subset

$$\displaystyle \binom{[n]}{k}=\{A\subset[n]:|A|=k\}$$

Number

$$\displaystyle |V|=\binom{n}{k}=\dfrac{n!}{k!(n-k)!}$$

Examples:

$$
\displaystyle
\begin{align*}
n=5,k=2&:\;|V|=\binom52=10\\
&V=\{12,13,14,15,23,24,25,34,35,45\}\\
n=6,k=2&:\;|V|=15\\
n=7,k=3&:\;|V|=35\\
n=10,k=3&:\;|V|=120
\end{align*}
$$

We abbreviate $\displaystyle\{1,2\}$ as $\displaystyle12$.

**Edges:** Unordered pair $\displaystyle\{A,B\}$ is edge iff

$$\displaystyle A\cap B=\emptyset$$

No common element. So $\displaystyle12$ adjacent to $\displaystyle34$ because $\displaystyle\{1,2\}\cap\{3,4\}=\emptyset$, but $\displaystyle12$ not adjacent to $\displaystyle23$ because intersection $\displaystyle\{2\}\neq\emptyset$.

**Degree calculation:**

Fix $\displaystyle A$, $|A|=k$. Remaining ground $\displaystyle[n]\setminus A$ size $\displaystyle n-k$. To be disjoint from $\displaystyle A$, $\displaystyle B$ must be chosen entirely from remaining $\displaystyle n-k$ elements:

$$\displaystyle \deg(A)=\binom{n-k}{k}\quad\text{if }n\ge2k$$

If $\displaystyle n<2k$, $\displaystyle n-k<k$, binomial $\displaystyle0$, no disjoint $\displaystyle k$-set, degree $0$, graph edgeless.

Thus when $\displaystyle n\ge2k$, $\displaystyle KG(n,k)$ is regular of degree $\displaystyle\binom{n-k}{k}$.

Example $\displaystyle KG(5,2)$: $\displaystyle\deg=\binom{3}{2}=3$, cubic 10-vertex Petersen.

$\displaystyle KG(6,2)$: $\displaystyle\deg=\binom{4}{2}=6$, 15 vertices degree 6.

**Clique number:** Clique = set of vertices pairwise disjoint $\displaystyle k$-sets. How many pairwise disjoint $\displaystyle k$-sets can pack into $\displaystyle[n]$? At most $\displaystyle\left\lfloor\dfrac{n}{k}\right\rfloor$. So

$$\displaystyle \omega(KG(n,k))=\left\lfloor\dfrac{n}{k}\right\rfloor$$

For $\displaystyle n=5,k=2$, $\displaystyle\omega=2$ — just an edge, no triangle of pairwise disjoint 2-sets needs 6 distinct elements. For $\displaystyle n=7,k=2$, $\displaystyle\omega=3$: $\{12,34,56\}$ pairwise disjoint.

Clique number much smaller than conjectured chromatic number $\displaystyle n-2k+2$ when $\displaystyle k$ large. e.g. $\displaystyle n=2k+1$: $\displaystyle\omega=2$, but $\displaystyle n-2k+2=3$. So $\displaystyle\chi>\omega$.

**Interpretations:**

- Committees: $\displaystyle n$ people, each committee $\displaystyle k$ people, edge when committees have no common member — conflict graph for sharing member.
- Constant-weight codes: binary strings length $\displaystyle n$, weight $\displaystyle k$ $\left(\displaystyle k$ ones$)$, two strings adjacent if supports disjoint $\iff$ Hamming distance $\displaystyle2k$. Independent set = intersecting family $\left(\text{pairwise intersect}\right)$.
- Scheduling: $\displaystyle k$-sets are resource requirements, disjoint means can run in parallel? Actually edge = conflict? Depends, but disjointness often conflict for coloring.

**Symmetry:** $\displaystyle KG(n,k)$ vertex-transitive: symmetric group $\displaystyle S_{n}$ permutes ground set, induces automorphism of graph. Highly symmetric, no distinguished vertex, combinatorial lower bound proofs difficult because no obvious bottleneck.

#### 2. Chromatic Number $\displaystyle\chi(G)$ — What It Measures

$$\displaystyle \chi(G)=\min\{c:\exists f:V\to[c],\;uv\in E\implies f(u)\neq f(v)\}$$

Proper coloring: assign color label $\displaystyle f(v)\in\{1,\dots,c\}$ so adjacent vertices different colors. No edge monochromatic.

**Intuition:** Color classes are independent sets — sets with no internal edges.

$$\displaystyle V=I_{1}\sqcup I_{2}\sqcup\cdots\sqcup I_{c},\quad I_{i}\text{ independent}$$

For $\displaystyle KG(n,k)$, independent set = family of $\displaystyle k$-sets pairwise intersecting $\left(\text{not necessarily all share one common element, but no two disjoint}\right)$. Erdős–Ko–Rado says for $\displaystyle n\ge2k$, largest intersecting family size $\displaystyle\binom{n-1}{k-1}$ — all sets containing fixed element $\displaystyle1$.

**Bounds:**

$$\displaystyle \omega(G)\le\chi(G)\le\Delta(G)+1$$

$\displaystyle\omega$ clique needs distinct colors for each vertex in clique. $\displaystyle\Delta$ max degree greedy gives $\displaystyle\Delta+1$ colors suffice.

For Kneser: $\displaystyle\omega=\lfloor n/k\rfloor$, $\displaystyle\Delta=\binom{n-k}{k}$ huge, so $\displaystyle\Delta+1$ bound useless, gives $\displaystyle\chi\le\binom{n-k}{k}+1$ far larger than $\displaystyle n-2k+2$.

If graph edgeless, $\displaystyle\chi=1$ — one color paints all vertices, no conflict.

**Why $\displaystyle\chi$ matters:** Minimum number of groups to partition vertices so no conflict inside group. For Kneser, minimum number of intersecting families to partition all $\displaystyle k$-sets.

**Example calculations:**

$$
\displaystyle
\begin{align*}
KG(5,2)&:\;10\text{ vertices, cubic, contains odd cycle, }\chi=3\\
KG(6,2)&:\;15\text{ vertices, degree }6,\;\chi=6-4+2=4\\
KG(7,2)&:\;\chi=7-4+2=5\\
KG(7,3)&:\;\binom73=35\text{ vertices, degree }\binom43=4,\;\chi=7-6+2=3
\end{align*}
$$

Notice $\displaystyle KG(7,3)$ has 35 vertices degree 4, yet needs 3 colors — sparse but chromatic 3.

#### 3. Kneser's Conjecture 1955 — Intuition

**Statement:**

$$\displaystyle\boxed{\chi(KG(n,k))=n-2k+2\quad\text{for }n\ge2k}$$

If $\displaystyle n<2k$, $\displaystyle\chi=1$ trivial by pigeonhole.

**Proof of trivial case $\displaystyle n<2k$:**

Let $\displaystyle A,B$ be any two $\displaystyle k$-sets. $\displaystyle|A\cup B|=|A|+|B|-|A\cap B|=2k-|A\cap B|\le n$. So

$$\displaystyle |A\cap B|\ge2k-n$$

If $\displaystyle n<2k$, then $\displaystyle2k-n\ge1$, so $\displaystyle|A\cap B|\ge1$, always intersect. Hence no edge:

$$\displaystyle E(KG(n,k))=\emptyset\implies\chi=1$$

**Why conjecture plausible — upper bound easy, lower bound hard:**

Upper bound $\displaystyle\chi\le n-2k+2$ via anchor coloring $\left(\text{see general strategy}\right)$:

$$
\displaystyle
\begin{align*}
\text{For }i=1\text{ to }n-2k+1:&\;\text{color all }k\text{-sets containing }i\text{ and not containing }1,\dots,i-1\text{ with color }i\\
\text{Final color }n-2k+2:&\;\text{all }k\text{-sets }\subseteq\{n-2k+2,\dots,n\},\text{ size }2k-1\text{ pool}
\end{align*}
$$

Final pool size $\displaystyle2k-1$, any two $\displaystyle k$-sets intersect, so independent.

Thus $\displaystyle n-2k+2$ colors suffice — easy explicit construction.

Lower bound $\displaystyle\chi\ge n-2k+2$ says cannot do with $\displaystyle n-2k+1$ colors. Try to color with fewer, you'd be forced to give same color to two disjoint sets. Why forced? Not obvious combinatorially. For $\displaystyle KG(6,2)$, try 3 colors for 15 vertices degree 6 — seems maybe possible? But formula says need 4. Need deep reason.

**Intuition for necessity:** Suppose we have $\displaystyle m=n-2k+1$ color classes, each independent = intersecting family. Need to cover all $\displaystyle\binom{n}{k}$ sets by $\displaystyle m$ intersecting families. Is it possible? Erdős–Ko–Rado says largest intersecting families are stars $\displaystyle\mathcal{F}_{i}=\{A:i\in A\}$. Stars centered at $\displaystyle1,\dots,m$ cover many sets, but sets completely contained in complement $\displaystyle\{m+1,\dots,n\}$ of size $\displaystyle2k-1$ avoid all those centers. That complement contains $\displaystyle\binom{2k-1}{k}$ sets, pairwise intersecting, could be one more family, but that would be $\displaystyle m+1$-th color. So with only $\displaystyle m$ stars you cannot cover all. But intersecting families need not be stars — Hilton–Milner shows non-trivial intersecting families exist — so need topology to rule out all possibilities.

**Example $\displaystyle n=6,k=2,m=3$ attempt fails:** Need 3 intersecting families cover all 15 edges-sets. Stars at 1,2,3 cover: star1 = {12,13,14,15,16} 5 sets, star2 = {23,24,25,26} 4 new, star3 = {34,35,36} 3 new, total 12, missing {45,46,56} 3 sets — they intersect each other but need 4th color. Any other intersecting families also fail — proved only via Borsuk–Ulam.

**Dimension intuition:** $\displaystyle n-2k+2$ grows with $\displaystyle n$ linearly, while $\displaystyle\omega=\lfloor n/k\rfloor$ grows slower when $\displaystyle k$ large. So chromatic number much larger than clique number — Kneser graphs are not perfect, have high $\displaystyle\chi$ despite small cliques. This makes them interesting counterexamples and test cases.

In short: $\displaystyle KG(n,k)$ encodes disjointness, $\displaystyle\binom{n}{k}$ vertices, degree $\displaystyle\binom{n-k}{k}$, clique number $\displaystyle\lfloor n/k\rfloor$, chromatic number measures partition into intersecting families, trivial $\displaystyle\chi=1$ when $\displaystyle n<2k$ by $\displaystyle|A\cap B|\ge2k-n$, and Kneser conjectured exact value $\displaystyle n-2k+2$ for $\displaystyle n\ge2k$ — upper bound easy by $\displaystyle n-2k+1$ stars plus final $\displaystyle2k-1$ pool, lower bound deep requiring Borsuk–Ulam, resolved by Lovász 1978 launching topological combinatorics.

### History, Discovery, Modern Developments

$$\displaystyle\text{Kneser 1955 — Erdős — Lovász 1978 — Bárány 1978 — Schrijver 1978 — Dol'nikov-Kriz — Matoušek 2004 — Modern}$$

**Martin Kneser (1928–2004), German algebraist, 1955:** In _Aufgabe 360_ in _Jahresbericht der Deutschen Mathematiker-Vereinigung_, observed easy upper bound $\displaystyle\chi(KG(n,k))\le n-2k+2$ via explicit coloring $\left(\text{anchor colors, see below}\right)$, and conjectured equality. Could not prove lower bound. Problem looked purely combinatorial.

**1970s — gap:** For 23 years attempts failed. Paul Erdős popularized problem, asked about chromatic number, offered prizes. Combinatorial methods failed because Kneser graphs highly symmetric, vertex-transitive, no obvious small bottleneck. Standard bounds like clique number $\displaystyle\omega(KG(n,k))=\left\lfloor\dfrac{n}{k}\right\rfloor$ $\left(\text{partition }[n]\text{ into disjoint }k\text{-sets}\right)$ gives only $\displaystyle\chi\ge\left\lfloor n/k\right\rfloor$, far from $\displaystyle n-2k+2$ when $\displaystyle k$ large. e.g. $\displaystyle n=2k+1$: $\displaystyle\lfloor n/k\rfloor=2$ but conjectured $\displaystyle\chi=3$.

**László Lovász (1948– ), 1978:** Then 29, in Szeged, Hungary. Proved lower bound using **Borsuk–Ulam theorem**. Paper _"Kneser's conjecture, chromatic number, and homotopy"_ in _J. Combinatorial Theory A_.

Introduced **neighborhood complex** $\displaystyle N(G)$: simplicial complex where vertices are vertices of $\displaystyle G$, simplex $\displaystyle\sigma=\{v_{1},\dots,v_{r}\}$ is simplex iff $\displaystyle\sigma$ has common neighbor: $\displaystyle\exists w:\{w,v_{i}\}\in E\;\forall i$. So $\displaystyle N(G)$ encodes overlapping neighborhoods.

Lovász showed: if $\displaystyle G$ is $\displaystyle m$-colorable, then $\displaystyle N(G)$ is $\displaystyle(m-1)$-connected? Actually: if $\displaystyle N(G)$ is $\displaystyle k$-connected then $\displaystyle\chi(G)\ge k+3$. More precisely, connectivity of $\displaystyle N(G)$ lower bounds chromatic number.

For $\displaystyle KG(n,k)$, he computed homotopy type: $\displaystyle N(KG(n,k))$ homotopy equivalent to sphere $\displaystyle S^{n-2k}$? Actually wedge of spheres, but at least $\displaystyle(n-2k-1)$-connected. Using Borsuk–Ulam to show non-trivial homology, deduced $\displaystyle\chi\ge n-2k+2$.

This was first major use of algebraic topology to solve discrete problem — birth of **topological combinatorics**.

**Imre Bárány 1978:** Shortly after Lovász, gave even shorter proof using same Borsuk–Ulam but more direct, avoiding neighborhood complex language, using Gale's lemma about placing points on sphere.

**Alexander Schrijver 1978:** Found subgraph $\displaystyle SG(n,k)$ $\left(\text{stable Kneser / Schrijver graph}\right)$: vertices are $\displaystyle k$-sets with no two cyclic consecutive elements in $\displaystyle[n]$ arranged on circle, and no pair containing both $1$ and $n$. Still has $\displaystyle\chi=n-2k+2$ but vertex-critical — removing any vertex drops chromatic number. Shows Lovász bound tight for minimal graphs. $\displaystyle |V(SG(n,k))|$ much smaller than $\displaystyle\binom{n}{k}$. For example $\displaystyle SG(5,2)=C_{5}$, 5-cycle, $\displaystyle\chi=3$.

**1980s–2000s — is topology necessary?** Question: is there purely combinatorial proof of Kneser? Jiří Matoušek 2004 gave proof that still uses Borsuk–Ulam but avoids simplicial complexes, making it accessible to combinatorialists. Uses Lemma: there exists set $\displaystyle X\subset S^{d}$ of $\displaystyle n$ points in general position such that every open hemisphere contains at least $\displaystyle k$ points? Actually Gale's lemma: $\displaystyle n$ points on $\displaystyle S^{n-2k}$ can be placed so every open hemisphere contains at least $\displaystyle k$ points. This is key.

$$\displaystyle\text{Borsuk–Ulam: If }f:S^{d}\to\mathbb{R}^{d}\text{ continuous, }\exists x:f(x)=f(-x)$$

Equivalent **Lyusternik–Schnirelmann**: If $\displaystyle S^{d}$ covered by $\displaystyle d+1$ closed sets, one contains antipodal pair $\displaystyle x,-x$. Or open sets.

This equivalence used to derive contradiction.

**2000s–now — modern developments:**

- **Dol'nikov 1988, Kriz 1992, 2000:** Generalization: For family $\displaystyle\mathcal{F}$ of subsets, define Kneser graph $\displaystyle KG(\mathcal{F})$ where vertices are sets in $\displaystyle\mathcal{F}$, edges disjoint. Define 2-colorable defect $\displaystyle\text{cd}_{2}(\mathcal{F}) = $ minimum size of set to delete from ground set so remaining family 2-colorable $\left(\text{no monochromatic set}\right)$. Then $\displaystyle\chi(KG(\mathcal{F}))\ge\text{cd}_{2}(\mathcal{F})$. Lovász–Kneser is special case where $\displaystyle\mathcal{F}=\binom{[n]}{k}$, $\displaystyle\text{cd}_{2}=n-2k+2$. Proof uses $\displaystyle\mathbb{Z}_{2}$-index $\displaystyle\text{ind}_{\mathbb{Z}_{2}}$.

- **Ziegler, Björner, de Longueville:** Systematic theory of $\displaystyle\mathbb{Z}_{2}$-spaces, box complexes $\displaystyle B(G)$, Hom-complexes $\displaystyle\text{Hom}(G,H)$. Box complex $\displaystyle B(G)$: vertices $\displaystyle V(G)\times\{0,1\}$, etc., its $\displaystyle\mathbb{Z}_{2}$-connectivity gives lower bound $\displaystyle\chi(G)\ge\text{ind}(B(G))+2$.

- **Alishahi–Hajiabolhassan:** Chromatic number of Kneser hypergraphs where edge = $\displaystyle r$ pairwise disjoint sets, $\displaystyle\chi$ of Kneser hypergraph $\displaystyle KG^{r}(n,k)$.

- **Computational:** $\displaystyle KG(n,k)$ huge $\displaystyle\binom{n}{k}$ vertices, e.g. $\displaystyle KG(100,40)$ astronomically huge, but its chromatic number known exactly $\displaystyle100-80+2=22$ — rare case where $\displaystyle\chi$ computable in closed form, while computing $\displaystyle\chi$ generally NP-hard.

**Modern day uses:**

$$\displaystyle\text{Topological lower bounds used for scheduling, coding, fair division}$$

- **Combinatorial geometry:** Proof method used for ham sandwich $\displaystyle S^{d}\to\mathbb{R}^{d}$, necklace splitting $\displaystyle k$ thieves fairly split necklace with $\displaystyle t$ types using $\displaystyle\le t(k-1)$ cuts, Tverberg theorem $\displaystyle (d+1)(r-1)+1$ points in $\displaystyle\mathbb{R}^{d}$ can be partitioned into $\displaystyle r$ parts whose convex hulls intersect, consensus halving.

- **Complexity:** Kneser graphs are test cases for hardness of graph coloring approximation. $\displaystyle\chi(KG(n,k))$ known, so can test algorithms that try to color with fewer colors — they must fail.

- **Coding theory:** Kneser graphs appear as conflict graphs for constant-weight codes: vertices = weight-$\displaystyle k$ binary strings length $\displaystyle n$ $\left(\text{characteristic vectors of }k\text{-sets}\right)$, edge = disjoint support $\implies$ Hamming distance $\displaystyle2k$. Independent set = intersecting family, max size given by Erdős–Ko–Rado $\displaystyle\binom{n-1}{k-1}$. Chromatic number = partition of all $\displaystyle k$-sets into intersecting families.

- **Equivariant topology:** Lovász's neighborhood complex led to Hom-complexes $\displaystyle\text{Hom}(G,H)$ used to bound $\displaystyle\chi(G)$ via $\displaystyle\mathbb{Z}_{2}$-index. $\displaystyle\text{Hom}(K_{2},G)$ is essentially neighborhood complex.

### Topological Proof — Detailed in Steps

Goal: show $\displaystyle\chi(KG(n,k))\ge n-2k+2$. Upper bound easy $\left(\text{anchor coloring}\right)$. Lower bound hard — need to prove fewer colors impossible.

#### 1. Topological Foundation — Borsuk–Ulam

$$\displaystyle\boxed{\text{If }f:S^{d}\to\mathbb{R}^{d}\text{ continuous, }\exists x\in S^{d}:f(x)=f(-x)}$$

**What is $\displaystyle S^{d}$?**

$$\displaystyle S^{d}=\{x\in\mathbb{R}^{d+1}:\|x\|=1\}=\{x:x_{1}^{2}+\cdots+x_{d+1}^{2}=1\}$$

- $\displaystyle S^{0}=\{-1,1\}$ two points
- $\displaystyle S^{1}=\{x_{1}^{2}+x_{2}^{2}=1\}$ circle
- $\displaystyle S^{2}=\{x_{1}^{2}+x_{2}^{2}+x_{3}^{2}=1\}$ ordinary sphere surface
- $\displaystyle S^{d}$ $d$-dimensional sphere

Antipodal map $\displaystyle A:S^{d}\to S^{d}$, $\displaystyle A(x)=-x$, opposite point, $\displaystyle A(A(x))=x$, free involution no fixed point.

**Picture:**

- $\displaystyle d=1$: $\displaystyle S^{1}$ circle to $\displaystyle\mathbb{R}$ line, continuous $\displaystyle f:S^{1}\to\mathbb{R}$ temperature around circle, opposite points same height — Intermediate Value Theorem forces $\displaystyle\exists x:f(x)=f(-x)$. Indeed define $\displaystyle g(x)=f(x)-f(-x)$, $\displaystyle g(-x)=-g(x)$ odd, if $\displaystyle g(x_{0})>0$ then $\displaystyle g(-x_{0})<0$, IVT gives zero.

- $\displaystyle d=2$: Earth $\displaystyle S^{2}$ to plane $\displaystyle\mathbb{R}^{2}$ $\left(\text{temperature, pressure}\right)$ → antipodal points same temperature and pressure simultaneously. Not just temperature equal somewhere and pressure equal elsewhere, same pair for both.

**Equivalent LS formulation:** Cover $\displaystyle S^{d}$ by $\displaystyle d+1$ open sets $\displaystyle U_{1},\dots,U_{d+1}$, one contains antipodal pair $\displaystyle x,-x$. Closed version same: If $\displaystyle S^{d}=F_{1}\cup\cdots\cup F_{d+1}$ closed, some $\displaystyle F_{i}$ contains $\displaystyle x,-x$.

Why equivalent? Given $\displaystyle f:S^{d}\to\mathbb{R}^{d}$, suppose no $\displaystyle x$ with $\displaystyle f(x)=f(-x)$, then $\displaystyle g(x)=f(x)-f(-x)\neq0$, define $\displaystyle h(x)=g(x)/\|g(x)\|:S^{d}\to S^{d-1}$ odd. Then sets $\displaystyle U_{i}^{+}=\{x:h_{i}(x)>0\}$, $\displaystyle U_{i}^{-}=\{x:h_{i}(x)<0\}$ cover, no contains antipodal pair — contradict LS.

This LS version directly used for Kneser: if we could color with $\displaystyle d$ colors, we would get covering of $\displaystyle S^{d}$ by $\displaystyle d$ open sets none containing antipodal pair, plus one more set for equator — total $\displaystyle d+1$ sets, LS says one contains antipodal pair, contradiction.

**Why Borsuk–Ulam deep:** Degree theory. Odd map $\displaystyle S^{d}\to S^{d}$ has odd degree $\displaystyle\neq0$, cannot factor through $\displaystyle S^{d-1}$ which has degree $0$. Homology $\displaystyle H_{d}(S^{d})\cong\mathbb{Z}$, $\displaystyle H_{d}(S^{d-1})=0$.

#### 2. Place points on sphere in general position

Ground set $\displaystyle[n]=\{1,\dots,n\}$. Let

$$\displaystyle d=n-2k+1,\qquad m=d$$

We work on sphere $\displaystyle S^{d}\subset\mathbb{R}^{d+1}$. Place $\displaystyle n$ points $\displaystyle v_{1},\dots,v_{n}\in S^{d}$ in general position:

$$\displaystyle\text{No }d+1\text{ points lie in a hyperplane through origin}$$

That is, no $\displaystyle d+1$ points lie on a great $\displaystyle S^{d-1}$ equator.

**How to achieve?** Moment curve trick: $\displaystyle\gamma(t)=(1,t,t^{2},\dots,t^{d})\in\mathbb{R}^{d+1}$, normalize $\displaystyle v(t)=\gamma(t)/\|\gamma(t)\|\in S^{d}$. Any $\displaystyle d+1$ distinct $\displaystyle t$ give linearly independent vectors $\displaystyle\gamma(t)$ $\left(\text{Vandermonde determinant }\neq0\right)$, so no hyperplane through origin contains $\displaystyle d+1$ of them.

**Gale's lemma strengthened:** For $\displaystyle n\ge2k$, exists set $\displaystyle X\subset S^{n-2k}$ of $\displaystyle n$ points such that every open hemisphere contains at least $\displaystyle k$ points. Proof uses same moment curve and ham sandwich. We need one dimension higher $\displaystyle S^{n-2k+1}=S^{d}$, so we can also ensure general position plus property that any open hemisphere contains at least $\displaystyle k$ points? Actually in Matoušek proof we place on $\displaystyle S^{d}$ with $\displaystyle d=n-2k+1$, then property: every open hemisphere contains at least $\displaystyle k$ points? Check: For $\displaystyle d=n-2k$, every open hemisphere contains at least $\displaystyle k$ points. For $\displaystyle d=n-2k+1$, every open hemisphere contains at least $\displaystyle k+1$? Let's not confuse, we only need general position for counting argument later. The key property for contradiction is that if both open hemispheres $\displaystyle H(x^{*}),H(-x^{*})$ contain $\displaystyle<k$ points, then $\displaystyle\ge n-2k+2$ points on equator, contradicting general position bound $\displaystyle\le d=n-2k+1$.

Why important: ensures that if open hemisphere $\displaystyle H(x)$ contains $\displaystyle<k$ points of $\displaystyle[n]$, then complement contains many points. For our contradiction, we will deduce both $\displaystyle H(x^{*}),H(-x^{*})$ contain $\displaystyle<k$ points, forcing many points on equator.

**Visualization:** $\displaystyle n$ points sprinkled on sphere fairly evenly, no cluster on equator. Any great circle $\displaystyle E(x)$ can contain at most $\displaystyle d$ points.

#### 3. Proof by contradiction — assume too few colors

Suppose $\displaystyle KG(n,k)$ colorable with $\displaystyle m=n-2k+1$ colors $\displaystyle\{1,\dots,m\}$. Want contradiction.

Let

$$\displaystyle c:\binom{[n]}{k}\to[m]$$

proper coloring:

$$\displaystyle A\cap B=\emptyset\implies c(A)\neq c(B)$$

So each color class

$$\displaystyle\mathcal{F}_{i}=c^{-1}(i)=\{A:c(A)=i\}$$

is intersecting family: any two sets in same $\displaystyle\mathcal{F}_{i}$ intersect $\displaystyle\left(\text{otherwise edge monochromatic}\right)$.

We have $\displaystyle m$ intersecting families covering all $\displaystyle\binom{n}{k}$ $k$-sets:

$$\displaystyle \binom{[n]}{k}=\bigcup_{i=1}^{m}\mathcal{F}_{i}$$

Goal show impossible when $\displaystyle m=n-2k+1$.

#### 4. Define continuous map $\displaystyle f:S^{d}\to\mathbb{R}^{d}$ construction

For $\displaystyle x\in S^{d}$, define open hemisphere centered at $\displaystyle x$:

$$\displaystyle H(x)=\{y\in S^{d}:\langle x,y\rangle>0\}$$

$\displaystyle\langle\cdot,\cdot\rangle$ standard inner product. $\displaystyle H(x)$ all points making acute angle $<90^{\circ}$ with $\displaystyle x$.

Properties:

$$
\displaystyle
\begin{align*}
H(-x)&=\{y:\langle -x,y\rangle>0\}=\{y:\langle x,y\rangle<0\}=-H(x)\\
H(x)\cap H(-x)&=\emptyset\\
E(x)&=\{y:\langle x,y\rangle=0\}=S^{d-1}\text{ equator separates them}\\
S^{d}&=H(x)\sqcup E(x)\sqcup H(-x)
\end{align*}
$$

For a $\displaystyle k$-set $\displaystyle F\subset[n]$, say $\displaystyle F\subset H(x)$ means all its points lie in hemisphere:

$$\displaystyle F\subset H(x)\iff\forall j\in F:\;v_{j}\in H(x)\iff\forall j\in F:\langle x,v_{j}\rangle>0$$

Set

$$\displaystyle H_{F}=\{x\in S^{d}:F\subset H(x)\}=\bigcap_{j\in F}\{x:\langle x,v_{j}\rangle>0\}$$

Intersection of $\displaystyle k$ open hemispheres $\displaystyle\{x:\langle x,v_{j}\rangle>0\}$, each open, so $\displaystyle H_{F}$ open $\left(\text{maybe empty if points not contained in any open hemisphere, but Gale ensures many non-empty}\right)$.

Now define for each color $\displaystyle i$:

$$\displaystyle U_{i}=\bigcup_{F:c(F)=i} H_{F}$$

$\displaystyle U_{i}$ open as union of open sets. $\displaystyle x\in U_{i}$ iff $\displaystyle H(x)$ contains at least one $\displaystyle k$-set colored $\displaystyle i$.

Idea: $\displaystyle f_{i}(x)>0$ iff $\displaystyle x\in U_{i}$.

**Matoušek explicit bump functions:**

For each $\displaystyle F$, define continuous function $\displaystyle\phi_{F}:S^{d}\to[0,1]$ supported in $\displaystyle H_{F}$, e.g.

$$\displaystyle \phi_{F}(x)=\max\left\{0,\min_{j\in F}\langle x,v_{j}\rangle\right\}$$

$\displaystyle\phi_{F}(x)>0\iff F\subset H(x)$ and distance from boundary positive. Then define

$$\displaystyle f_{i}(x)=\sum_{F:c(F)=i}\phi_{F}(x)$$

Sum over all $\displaystyle F$ colored $\displaystyle i$. Since each $\displaystyle\phi_{F}$ continuous, finite sum of continuous? Actually infinite sum but $\displaystyle\binom{n}{k}$ finite, so finite sum, continuous. Moreover $\displaystyle f_{i}(x)>0\iff\exists F:c(F)=i,\;F\subset H(x)$.

Alternative definition using distance to complement:

$$
\displaystyle f_{i}(x)=\begin{cases}
\text{dist}(x,S^{d}\setminus U_{i})&x\in U_{i}\\
0&x\notin U_{i}
\end{cases}
$$

Distance to closed complement continuous, zero outside $\displaystyle U_{i}$, positive inside.

Thus

$$\displaystyle f(x)=(f_{1}(x),\dots,f_{d}(x))\in\mathbb{R}^{d}\text{ continuous}$$

$\displaystyle d=m=n-2k+1$ coordinates matching colors.

**Intuition:** $\displaystyle f$ measures, for each color, how deeply hemisphere $\displaystyle H(x)$ contains a $\displaystyle k$-set of that color. If hemisphere contains none, coordinate zero.

#### 5. Apply Borsuk–Ulam

$\displaystyle f$ continuous $\displaystyle S^{d}\to\mathbb{R}^{d}$, where $\displaystyle d=n-2k+1$.

Borsuk–Ulam gives $\displaystyle\exists x^{*}\in S^{d}$ with

$$\displaystyle f(x^{*})=f(-x^{*})$$

That is for each $\displaystyle i$,

$$\displaystyle f_{i}(x^{*})=f_{i}(-x^{*})$$

#### 6. Expose combinatorial contradiction

$\displaystyle H(x^{*})$ and $\displaystyle H(-x^{*})$ disjoint opposite hemispheres.

**Lemma:** For each color $\displaystyle i$, at most one of $\displaystyle H(x^{*}),H(-x^{*})$ can contain a $\displaystyle k$-set colored $\displaystyle i$.

_Proof:_ Suppose $\displaystyle H(x^{*})$ contains $\displaystyle A$ colored $\displaystyle i$ and $\displaystyle H(-x^{*})$ contains $\displaystyle B$ colored $\displaystyle i$. Then

$$\displaystyle A\subset H(x^{*}),\;B\subset H(-x^{*}),\;A\cap B=\emptyset$$

Why disjoint? If $\displaystyle j\in A$, then $\displaystyle v_{j}\in H(x^{*})$, so $\displaystyle\langle x^{*},v_{j}\rangle>0$. If $\displaystyle j\in B$, then $\displaystyle v_{j}\in H(-x^{*})$, so $\displaystyle\langle -x^{*},v_{j}\rangle>0\iff\langle x^{*},v_{j}\rangle<0$. Cannot have both $\displaystyle>0$ and $\displaystyle<0$ for same $\displaystyle j$, so $\displaystyle j$ cannot belong to both $\displaystyle A$ and $\displaystyle B$. Hence $\displaystyle A\cap B=\emptyset$. Then $\displaystyle A,B$ adjacent in $\displaystyle KG(n,k)$ but same color $\displaystyle i$ — violates proper coloring. Contradiction. So at most one hemisphere contains color $\displaystyle i$.

Thus for each $\displaystyle i$, not both $\displaystyle f_{i}(x^{*})>0$ and $\displaystyle f_{i}(-x^{*})>0$. At most one positive.

But Borsuk–Ulam equality $\displaystyle f_{i}(x^{*})=f_{i}(-x^{*})$ says they are equal. If one positive, both positive — impossible. Therefore

$$\displaystyle f_{i}(x^{*})=0\quad\forall i=1,\dots,d$$

Meaning: neither $\displaystyle H(x^{*})$ nor $\displaystyle H(-x^{*})$ contains any $\displaystyle k$-set colored with colors $1,\dots,d$.

Since we assumed all $\displaystyle\binom{n}{k}$ vertices colored with these $\displaystyle d$ colors, any $\displaystyle k$-set contained in $\displaystyle H(x^{*})$ would need a color, contradiction unless $\displaystyle H(x^{*})$ contains no $\displaystyle k$-set at all. Similarly for $\displaystyle H(-x^{*})$.

When does open hemisphere $\displaystyle H(x^{*})$ contain no $\displaystyle k$-set? Exactly when number of ground points inside $\displaystyle H(x^{*})$ is $\displaystyle<k$:

$$\displaystyle |\{j:v_{j}\in H(x^{*})\}|\le k-1$$

Because if $\displaystyle\ge k$ points lie in $\displaystyle H(x^{*})$, then those $\displaystyle k$ points form a $\displaystyle k$-set contained in $\displaystyle H(x^{*})$, which would need a color. So must be $\displaystyle\le k-1$.

Similarly

$$\displaystyle |\{j:v_{j}\in H(-x^{*})\}|\le k-1$$

Total points in both open hemispheres:

$$\displaystyle |H(x^{*})|+|H(-x^{*})|\le2k-2$$

Remaining points lie on equator $\displaystyle E(x^{*})=S^{d-1}=\{y:\langle x^{*},y\rangle=0\}$:

$$\displaystyle |\{j:v_{j}\in E(x^{*})\}|=n-|H(x^{*})|-|H(-x^{*})|\ge n-(2k-2)=n-2k+2$$

But equator is intersection of $\displaystyle S^{d}$ with hyperplane through origin orthogonal to $\displaystyle x^{*}$: $\displaystyle\{y:\langle x^{*},y\rangle=0\}$. By general position assumption, no $\displaystyle d+1=n-2k+2$ points lie in a hyperplane through origin. At most $\displaystyle d=n-2k+1$ points can lie on equator.

We have $\displaystyle\ge n-2k+2$ points on equator, contradiction because

$$\displaystyle n-2k+2 > n-2k+1 = d$$

Thus assumption $\displaystyle m=n-2k+1$ colorable false.

Hence need at least $\displaystyle m+1=n-2k+2$ colors.

Combined with upper bound anchor coloring giving $\displaystyle\chi\le n-2k+2$:

$$
\displaystyle
\begin{align*}
\chi(KG(n,k))&\ge n-2k+2\\
\chi(KG(n,k))&\le n-2k+2\\
\implies\chi(KG(n,k))&=n-2k+2
\end{align*}
$$

QED.

**Remarks on original Lovász proof:** Used neighborhood complex $\displaystyle N(KG(n,k))$ and showed its connectivity $\displaystyle\ge n-2k-1$, then $\displaystyle\chi\ge\text{conn}+3$. Matoušek version above avoids simplicial complexes, uses only Borsuk–Ulam and Gale's lemma, more elementary but same topological core.

This completes lower bound, establishing Lovász–Kneser theorem.

### The General Coloring Strategy — Upper Bound 

Why $\displaystyle n-2k+2$ colors sufficient? Constructive greedy anchor. This is the easy half of Lovász–Kneser, giving

$$\displaystyle\chi(KG(n,k))\le n-2k+2$$

Combined with hard topological lower bound $\displaystyle\ge n-2k+2$, gives equality.

#### Setup

Let

$$\displaystyle c=n-2k+2$$

We will color all $\displaystyle\binom{n}{k}$ vertices with $\displaystyle c$ colors.

$$
\displaystyle
\begin{align*}
\text{Colors }1,\dots,c-1&=n-2k+1\text{ colors = anchors}\\
\text{Color }c&=\text{ final dump = leftover pool}
\end{align*}
$$

Ground set

$$\displaystyle [n]=\{1,2,\dots,n\}$$

Split ground into two parts:

$$
\displaystyle
\begin{align*}
A&=\{1,2,\dots,n-2k+1\},\quad |A|=n-2k+1=c-1\\
B&=\{n-2k+2,\dots,n\},\quad |B|=n-(n-2k+1)=2k-1
\end{align*}
$$

Note $\displaystyle[A]\sqcup B=[n]$, $\displaystyle|A|+|B|=n$, $\displaystyle|B|=2k-1$ critical size.

#### Procedure — Greedy Anchor

For each $\displaystyle k$-set $\displaystyle F\subset[n]$:

$$
\displaystyle
\begin{align*}
\text{For }i=1\text{ to }n-2k+1:\\
&\quad\text{if }i\in F\text{ then color}(F)=i\text{ and stop}\\
\text{If loop ends, }F\subseteq\{n-2k+2,\dots,n\}=B\\
&\quad\text{color}(F)=c
\end{align*}
$$

In words: scan anchors $\displaystyle1,2,\dots,n-2k+1$ in order, assign first anchor that belongs to $\displaystyle F$. If $\displaystyle F$ contains none of them, then $\displaystyle F$ lies entirely in $\displaystyle B$, assign final color $\displaystyle c$.

This is well-defined because every $\displaystyle F$ either meets $\displaystyle A$ or is contained in $\displaystyle B$ $\left(\text{if }F\cap A=\emptyset\implies F\subseteq[n]\setminus A=B\right)$.

Formally:

$$
\displaystyle
\text{color}(F)=
\begin{cases}
\min(F\cap A)&\text{if }F\cap A\neq\emptyset\\
c&\text{if }F\cap A=\emptyset
\end{cases}
$$

$\displaystyle\min$ uses natural order $\displaystyle1<\dots<n$.

#### Validity Detailed — Why Proper?

Need each color class independent: no edge inside class, i.e., no two vertices same color are disjoint.

- **Color $\displaystyle i<n-2k+2$:** Suppose $\displaystyle\text{color}(F_{1})=i$ and $\displaystyle\text{color}(F_{2})=i$, $\displaystyle1\le i\le n-2k+1$.

By construction, $\displaystyle i\in F_{1}$ and $\displaystyle i\in F_{2}$, and for all $\displaystyle j<i$, $\displaystyle j\notin F_{1},F_{2}$ $\left(\text{otherwise earlier anchor would have been chosen}\right)$, but crucial is both contain $\displaystyle i$.

Then

$$\displaystyle F_{1}\cap F_{2}\supseteq\{i\}\neq\emptyset$$

So $\displaystyle F_{1},F_{2}$ not disjoint, no edge between them in $\displaystyle KG(n,k)$. Hence color class $\displaystyle i$ is independent set — actually a star centered at $\displaystyle i$, the classic Erdős–Ko–Rado extremal intersecting family.

Indeed $\displaystyle\mathcal{F}_{i}=\{F:i\in F,\;F\cap\{1,\dots,i-1\}=\emptyset\}$ is subfamily of star, but any two contain $\displaystyle i$, intersect.

- **Final color $\displaystyle c$:** $\displaystyle\text{color}(F)=c$ means $\displaystyle F\cap A=\emptyset$, so $\displaystyle F\subseteq B$, where $\displaystyle|B|=2k-1$.

Let $\displaystyle A,B$ be two $\displaystyle k$-subsets of $\displaystyle B$ $\left(\text{using }A,B\text{ for sets now, not ground partition}\right)$:

$$\displaystyle |A|=|B|=k,\;A,B\subseteq B,\;|B|=2k-1$$

By pigeonhole principle:

$$\displaystyle |A\cup B|=|A|+|B|-|A\cap B|\le|B|=2k-1$$

So

$$\displaystyle k+k-|A\cap B|\le2k-1\implies|A\cap B|\ge2k-(2k-1)=1$$

Thus

$$\displaystyle |A\cap B|\ge1$$

Any two $\displaystyle k$-sets inside $\displaystyle(2k-1)$-set intersect. No disjoint pair, no edge. So final color class independent as well.

Hence coloring proper with $\displaystyle c=n-2k+2$ colors.

$$\displaystyle\chi(KG(n,k))\le n-2k+2$$

#### Examples — Step by Step

**$\displaystyle KG(6,2)$:** $\displaystyle n=6,k=2\implies c=6-4+2=4$ colors, ground $\displaystyle\{1,\dots,6\}$, $\displaystyle A=\{1,2,3\}$, $\displaystyle B=\{4,5,6\}$, $\displaystyle|B|=3=2k-1$.

List all $\displaystyle\binom62=15$ vertices:

$$
\displaystyle
\begin{align*}
\text{Color1 }i=1&:\{12,13,14,15,16\} &&\text{contains 1}\\
&\;12\cap13=\{1\},\;12\cap14=\{1\},\dots\text{ all intersect at 1}\\
\text{Color2 }i=2&:\{23,24,25,26\} &&\text{contains 2 not 1}\\
&\;23=\{2,3\},\;24=\{2,4\},\;23\cap24=\{2\}\neq\emptyset\\
\text{Color3 }i=3&:\{34,35,36\} &&\text{contains 3 not 1,2}\\
&\;34\cap35=\{3\},\text{ etc.}\\
\text{Color4 }c=4&:\{45,46,56\} &&\subseteq\{4,5,6\}=B\\
&\;45=\{4,5\},46=\{4,6\},45\cap46=\{4\}\\
&\;45\cap56=\{5\},\;46\cap56=\{6\}
\end{align*}
$$

Check no edges inside classes: $\displaystyle45,46$ share $\displaystyle4$, not disjoint. So 4-colorable. Lower bound says cannot do with 3.

Count: $5+4+3+3=15$ all vertices covered.

**$\displaystyle KG(5,2)$ Petersen:** $\displaystyle n=5,k=2\implies c=3$, $\displaystyle A=\{1,2\}$, $\displaystyle B=\{3,4,5\}$, $|B|=3$.

$$
\displaystyle
\begin{align*}
\text{Color1}&:\{12,13,14,15\}\text{ contains 1}\\
\text{Color2}&:\{23,24,25\}\text{ contains 2 not 1}\\
\text{Color3}&:\{34,35,45\}\subseteq\{3,4,5\}
\end{align*}
$$

$4+3+3=10$ vertices, proper 3-coloring. No 2-coloring because contains odd cycle.

**$\displaystyle KG(7,3)$:** $\displaystyle n=7,k=3\implies c=7-6+2=3$ colors. $\displaystyle A=\{1,2\}$, $\displaystyle B=\{3,4,5,6,7\}$, $|B|=5=2k-1$. Colors:

$$
\displaystyle
\begin{align*}
\text{Color1}&:\text{ all }3\text{-sets containing }1,\;\binom62=20\text{ sets but some also contain 1? Actually count }\\
&\;|\{F:1\in F\}|=\binom{6}{2}=15\\
\text{Color2}&:\text{ sets containing }2\text{ not }1,\;|\{F:2\in F,1\notin F\}|=\binom{5}{2}=10\\
\text{Color3}&:\text{ sets }\subseteq\{3,4,5,6,7\},\;\binom53=10
\end{align*}
$$

$15+10+10=35=\binom73$. Color3: any two 3-sets inside 5-set intersect? $\displaystyle3+3=6>5$, so by pigeonhole intersect at least $1$. So independent.

**General counting check:** Number colored with final color = $\displaystyle\binom{2k-1}{k}$. Number colored with anchor $\displaystyle i$:

$$\displaystyle |\mathcal{F}_{i}|=\binom{n-i}{k-1}\text{ with first }i-1\text{ excluded?}$$

Actually $\displaystyle|\{F:i\in F,\;1,\dots,i-1\notin F\}|=\binom{n-i}{k-1}$. Sum:

$$\displaystyle\sum_{i=1}^{n-2k+1}\binom{n-i}{k-1}+\binom{2k-1}{k}=\binom{n}{k}$$

Identity holds by hockey-stick.

#### Why $\displaystyle2k-1$ Is Magic Number

$\displaystyle2k-1$ is largest size of ground set where every two $\displaystyle k$-sets intersect. If ground size $\displaystyle2k$, then disjoint pair exists: $\{1,\dots,k\}$ and $\{k+1,\dots,2k\}$ disjoint. So $\displaystyle2k-1$ threshold where Kneser graph on that ground becomes edgeless:

$$\displaystyle KG(2k-1,k)\text{ has } \chi=1$$

Indeed $\displaystyle n=2k-1<2k$, no edges. So final dump color class is exactly $\displaystyle KG(2k-1,k)$, edgeless, can be one color.

If we tried to use $\displaystyle n-2k+1$ colors only $\left(\text{no final dump}\right)$, leftover ground $\displaystyle2k$ would contain disjoint pair needing extra color. So $\displaystyle n-2k+2$ minimal for this anchor scheme.

#### Optimality and Hilton–Milner

Anchor stars $\displaystyle\mathcal{F}_{i}=\{F:i\in F\}$ are maximum intersecting families by Erdős–Ko–Rado for $\displaystyle n\ge2k$. This coloring uses largest possible independent sets, greedy optimal. Hilton–Milner shows non-trivial intersecting families smaller, so anchor optimal for upper bound.

Thus easy upper bound construction gives $\displaystyle\chi\le n-2k+2$, and Lovász topological lower bound gives $\displaystyle\chi\ge n-2k+2$, together equality.

In short: scan $\displaystyle1,\dots,n-2k+1$ as anchors, color $\displaystyle k$-set by first anchor it contains, otherwise dump into final pool $\displaystyle B$ of size $\displaystyle2k-1$ where any two $\displaystyle k$-sets intersect by pigeonhole $\displaystyle|A\cap B|\ge1$, so each color class independent, $\displaystyle n-2k+2$ colors suffice.

### Petersen Graph $\displaystyle KG(5,2)$

Ground $\displaystyle\{1,2,3,4,5\}$, vertices $\displaystyle\binom{5}{2}=10$. List all 10:

$$\displaystyle 12,13,14,15,23,24,25,34,35,45$$

Edge when disjoint: $\displaystyle12$ adjacent to $\displaystyle34,35,45$ $\left(\text{3 neighbors}\right)$, etc. Degree $\displaystyle\binom{3}{2}=3$, cubic graph.

$$\displaystyle \chi(KG(5,2))=5-4+2=3$$

Coloring with $\displaystyle c=3$:

$$
\displaystyle
\begin{align*}
\text{Color1}&:\{12,13,14,15\} &&\text{share 1 — star centered 1}\\
\text{Color2}&:\{23,24,25\} &&\text{share 2 — remaining containing 2}\\
\text{Color3}&:\{34,35,45\} &&\subseteq\{3,4,5\},\;|\{3,4,5\}|=3=2k-1
\end{align*}
$$

Valid: $\displaystyle34\cap35=\{3\}$, $\displaystyle34\cap45=\{4\}$, $\displaystyle35\cap45=\{5\}$, no edges.

No 2-coloring possible because $\displaystyle KG(5,2)$ contains odd cycle e.g. $\displaystyle12-34-25-13-45-12$ length 5, and odd cycle needs 3 colors. So $\displaystyle\chi=3$ matches formula.

Petersen is also $\displaystyle SG(5,2)$ stable Kneser — minimal 3-chromatic.

### Why It Matters Today

- **Launch of topological combinatorics:** First proof that continuity / antipodal maps can prove discrete lower bound. Now standard toolkit for $\displaystyle\chi(G)$, e.g., Borsuk graphs $\displaystyle BG(n)$ where vertices points on sphere, edges almost antipodal, $\displaystyle\chi$ grows with dimension via Borsuk–Ulam. Schrijver graphs $\displaystyle SG(n,k)$ vertex-critical with same chromatic number.

- **Method paradigm:** Transform coloring problem into $\displaystyle\mathbb{Z}_{2}$-equivariant map $\displaystyle S^{d}\to\text{complex}$, show map cannot exist via Borsuk–Ulam index. Steps:

$$\displaystyle\text{Graph }G\to\text{ Box complex }B(G)\to\mathbb{Z}_{2}\text{-space}\to\text{index }\text{ind}_{\mathbb{Z}_{2}}B(G)\to\chi(G)\ge\text{ind}+2$$

Used for ham sandwich, necklace splitting $\displaystyle n$ thieves, consensus halving, Tverberg, etc.

- **Sharpness:** Schrijver's $\displaystyle SG(n,k)$ shows bound tight even after deleting many vertices, so topology captures exact obstruction, not just estimate. $\displaystyle SG(n,k)$ still needs $\displaystyle n-2k+2$ colors but much sparser — proves coloring difficulty not due to many vertices but topological structure.

- **Pedagogical:** Clean example where easy upper bound $\displaystyle n-2k+2$ via greedy, hard lower bound needs topology — illustrates gap between constructing solution and proving optimality. Most combinatorics problems easy to give upper bound, lower bound hard — topology provides powerful lower bound method.

- **Coding and intersecting families:** Erdős–Ko–Rado says largest intersecting family of $\displaystyle k$-sets size $\displaystyle\binom{n-1}{k-1}$. Partition of all $\displaystyle\binom{n}{k}$ sets into intersecting families needs at least $\displaystyle\dfrac{\binom{n}{k}}{\binom{n-1}{k-1}}=\dfrac{n}{k}$ families, but Lovász–Kneser gives stronger $\displaystyle n-2k+2$ which for large $\displaystyle n$ about $\displaystyle n$, larger than $\displaystyle n/k$ when $\displaystyle k>1$. So chromatic number much larger than simple ratio bound.

In short: $\displaystyle KG(n,k)$ vertices = $\displaystyle k$-sets, edges = disjointness, $\displaystyle\chi=n-2k+2$ by anchor coloring upper bound and Borsuk–Ulam lower bound $\displaystyle S^{d}\to\mathbb{R}^{d}$ collapsing antipodal $\displaystyle x^{*},-x^{*}$, forcing $\displaystyle2k-1$ pigeonhole violation — Lovász 1978 solving Kneser 1955, spawning topological combinatorics used for fair division, coding, complexity, equivariant topology.
