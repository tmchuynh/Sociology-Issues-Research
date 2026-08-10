## Borsuk–Ulam Theorem

The **Borsuk–Ulam theorem** is one of the central results of algebraic topology. At its heart is a surprisingly simple idea: **a continuous function cannot completely separate every point on a sphere from the point directly opposite it when the sphere and the target space have the same dimension**.

More precisely, if a continuous function assigns an $\displaystyle n$-dimensional vector to every point of an $\displaystyle n$-dimensional sphere, then there must be at least one pair of antipodal points that receive exactly the same vector.

$$\displaystyle\boxed{\text{If }f:S^{n}\to\mathbb{R}^{n}\text{ is continuous, then there exists }x\in S^{n}\text{ such that }f(x)=f(-x).}$$

Here $\displaystyle S^{n}=\{x\in\mathbb{R}^{n+1}:\|x\|=1\}$ denotes the $\displaystyle n$-dimensional sphere and $\displaystyle -x$ is the point antipodal to $\displaystyle x$. The line segment joining $\displaystyle x$ and $\displaystyle -x$ passes through the center of the sphere. On the circle $\displaystyle x=(\cos\theta,\sin\theta)$, $\displaystyle -x=(-\cos\theta,-\sin\theta)=(\cos(\theta+\pi),\sin(\theta+\pi))$, separated by $180^{\circ}$.

This result is remarkable because the conclusion concerns **two different points** while the hypothesis only assumes continuity. There is no assumption that the function is symmetric, injective, differentiable, linear, or otherwise specially structured. Continuity alone forces the coincidence.

### History, Discovery, Modern Developments

$$\displaystyle\text{Ulam 1930 conjecture — Borsuk 1933 proof — Hopf, Lyusternik–Schnirelmann — Stone–Tukey ham sandwich — Lovász 1978 — Matoušek 2003}$$

- **Stanisław Ulam (1909–1984), 1930:** Polish mathematician in Lwów school conjectured theorem as problem.

- **Karol Borsuk (1905–1982), 1933:** Proved conjecture in _Drei Sätze über die $n$-dimensionale euklidische Sphäre_ using degree theory and antipodal maps. Named Borsuk–Ulam to credit conjecture + proof.

- **1930s equivalences:** Quickly shown equivalent to:

$$
\begin{align*}
\text{(BU1)}&\;f:S^{n}\to\mathbb{R}^{n}\text{ cont.}\implies\exists x:f(x)=f(-x)\\[5pt]
\text{(BU2)}&\;\nexists\text{ odd continuous }h:S^{n}\to S^{n-1},\;h(-x)=-h(x)\\[5pt]
\text{(LS)}&\;\text{Lyusternik–Schnirelmann 1930: If }S^{n}\text{ covered by }n+1\text{ closed sets, one contains antipodal pair}
\end{align*}
$$

Lyusternik and Schnirelmann gave covering proof useful for combinatorics.

- **1950s–1970s — ham sandwich and beyond:** Stone–Tukey theorem $\left(\text{bisect }n\text{ volumes in }\mathbb{R}^{n}\text{ by hyperplane}\right)$ proved as corollary.

- **László Lovász 1978:** Used Borsuk–Ulam to prove Kneser's conjecture $\displaystyle\chi(KG(n,k))=n-2k+2$, launching **topological combinatorics**. First use to solve purely discrete coloring problem.

- **1980s–2000s — generalizations:** Bárány, Shlosman, Szűcs necklace splitting — $\displaystyle k$ thieves fairly split necklace with $\displaystyle t$ bead types using $\le t(k-1)$ cuts via Borsuk–Ulam. Jiří Matoušek book _Using the Borsuk–Ulam Theorem_ (2003) systematic exposition.

- **Modern developments:**
  - Equivariant topology: $\displaystyle\mathbb{Z}_{2}$-index, for $\displaystyle f:S^{n}\to\mathbb{R}^{m},\;m<n$, coincidence set dimension $\displaystyle\ge n-m$.
  - Computational: finding $\displaystyle\epsilon$-approximate coincidence PPAD-complete, connection to Nash equilibrium, Tucker's lemma.
  - Data / TDA: centerpoint theorem, robust statistics.

- **Modern day uses:** fair division, consensus halving $\left(\text{cut cake so }n\text{ people agree piece worth half}\right)$, Kneser–Lovász coloring lower bounds, ham sandwich bisection, game theory symmetric equilibria.

### Mathematical Statement and What Continuity Does

Let $\displaystyle S^{n}=\{x\in\mathbb{R}^{n+1}:\|x\|=1\}$ and $\displaystyle f:S^{n}\to\mathbb{R}^{n}$ continuous.

$$\displaystyle\boxed{\exists x\in S^{n}:f(x)=f(-x)}$$

**Why continuity essential:** Discontinuous can avoid coincidence, e.g.

$$\displaystyle f(x)=\begin{cases}1&x_{n+1}>0\\0&x_{n+1}\le0\end{cases}$$

has $\displaystyle f(x)\neq f(-x)$ for $\displaystyle x$ not on equator, but jump at equator — discontinuous. Continuity prevents abrupt jump. Sphere connected and wraps around, attempt to keep antipodal pairs separated creates sign reversal forced to zero.

**$S^{1}\to\mathbb{R}$ case — IVT visible:**

$$\displaystyle S^{1}=\{(\cos\theta,\sin\theta)\},\quad f:S^{1}\to\mathbb{R}$$

Define

$$\displaystyle g(\theta)=f(\theta)-f(\theta+\pi),\quad g(\theta+\pi)=-g(\theta)$$

If $\displaystyle g(\theta_{0})>0$, then $\displaystyle g(\theta_{0}+\pi)<0$. Continuous $\displaystyle g$ on $[\theta_{0},\theta_{0}+\pi]$, IVT gives $\displaystyle\theta^{*}$ with $\displaystyle g(\theta^{*})=0\implies f(\theta^{*})=f(\theta^{*}+\pi)$.

$$\displaystyle \text{Connectedness + oddness}\implies\text{zero}$$

This is core structure for all $\displaystyle n$.

### Understanding the Dimension

Domain $\displaystyle S^{n}$ dimension $\displaystyle n$, target $\displaystyle\mathbb{R}^{n}$ dimension $\displaystyle n$ — matching crucial.

$$
\begin{align*}
S^{0}&=\{-1,1\}\\[5pt]
S^{1}&=\{x_{1}^{2}+x_{2}^{2}=1\}\text{ circle}\\[5pt]
S^{2}&=\{x_{1}^{2}+x_{2}^{2}+x_{3}^{2}=1\}\text{ ordinary sphere}\\[5pt]
S^{n}&=\{x_{1}^{2}+\cdots+x_{n+1}^{2}=1\}
\end{align*}
$$

Sharpness:

$$
\begin{align*}
m<n&:\;f:S^{n}\to\mathbb{R}^{m}\implies\dim\{x:f(x)=f(-x)\}\ge n-m\\[5pt]
m=n&:\;\exists x:f(x)=f(-x)\text{ (Borsuk–Ulam)}\\[5pt]
m>n&:\;\text{possible no coincidence, e.g. inclusion }S^{n}\hookrightarrow\mathbb{R}^{n+1},\;i(x)=x\neq -x=i(-x)
\end{align*}
$$

Example $\displaystyle S^{1}\to\mathbb{R}^{2}$ circle embedded in plane — opposite points distinct, no forced coincidence. So $\displaystyle n$ is threshold.

Antipodal map $\displaystyle A(x)=-x$, free involution $\displaystyle A(A(x))=x$.

### The Deeper Meaning of the Circle Proof

Question $\displaystyle f(x)\stackrel{?}{=}f(-x)$. Construct difference

$$\displaystyle g(x)=f(x)-f(-x),\quad g(-x)=-g(x)$$

$\displaystyle g$ odd. Desired conclusion $\displaystyle f(x)=f(-x)\iff g(x)=0$.

So Borsuk–Ulam = **Every continuous odd map $\displaystyle S^{n}\to\mathbb{R}^{n}$ must vanish somewhere.**

#### Equivalent Formulation: Odd Maps

Suppose $\displaystyle g:S^{n}\to\mathbb{R}^{n}$ continuous, $\displaystyle g(-x)=-g(x)$ $\left(\text{antipodal-equivariant}\right)$. Then

$$\displaystyle\boxed{\exists x\in S^{n}:g(x)=0}$$

Equivalence: $\displaystyle f\mapsto g(x)=f(x)-f(-x)$ odd; $\displaystyle g(x)=0\iff f(x)=f(-x)$.

Geometrically: $\displaystyle S^{n}$ with $\displaystyle x\mapsto -x$, $\displaystyle\mathbb{R}^{n}$ with $\displaystyle y\mapsto -y$, equivariance $\displaystyle g(-x)=-g(x)$. Picture $\displaystyle S^{1}$: temperature difference changes sign after $180^{\circ}$, forces zero.

For general $\displaystyle n$ need $\displaystyle n$ simultaneous equations

$$\displaystyle g_{1}(x)=g_{2}(x)=\cdots=g_{n}(x)=0$$

Borsuk–Ulam asserts solvable.

Example $\displaystyle n=2$: $\displaystyle f(p)=(T(p),P(p))$, $\displaystyle g(p)=(T(p)-T(-p),P(p)-P(-p))$. Zero means same temperature and pressure at antipodal pair.

#### Why There Cannot Be Odd Map $S^{n}\to S^{n-1}$

If odd $\displaystyle g:S^{n}\to\mathbb{R}^{n}$ never zero, normalize

$$\displaystyle h(x)=\dfrac{g(x)}{\|g(x)\|}\in S^{n-1},\quad h(-x)=-h(x)$$

Thus nowhere-zero odd map would give odd continuous $\displaystyle S^{n}\to S^{n-1}$. Borsuk–Ulam says no such map exists.

Chain:

$$
\begin{align*}
\text{Assume }&f(x)\neq f(-x)\;\forall x\\[5pt]
g(x)&=f(x)-f(-x)\neq0,\;g(-x)=-g(x)\\[5pt]
h(x)&=\dfrac{g(x)}{\|g(x)\|}:S^{n}\to S^{n-1}\text{ odd}\\[5pt]
\text{No such }h\text{ exists}&\implies\text{contradiction}
\end{align*}
$$

So equivalent:

$$\displaystyle (A)\;f(x)=f(-x)\text{ some }x\iff(B)\;g\text{ odd has zero}\iff(C)\;\nexists\text{ odd }S^{n}\to S^{n-1}$$

**Why (C) true:** Degree. Odd map $\displaystyle S^{n}\to S^{n}$ has odd degree $\neq0$. Any map $\displaystyle S^{n}\to S^{n-1}\hookrightarrow S^{n}\setminus\{\text{poles}\}$ missing points has degree $0$. Contradiction. For $\displaystyle n=1$, $\displaystyle S^{1}$ connected cannot odd-map to $\displaystyle S^{0}=\{-1,1\}$ disconnected.

### Topological Intuition, Degree, Homology

**Intuition:** Trying to assign direction in $\displaystyle S^{n-1}$ to every point of $\displaystyle S^{n}$ antipodally — opposite points opposite directions — impossible because higher sphere contains too much global structure to compress.

**Degree:** $\displaystyle\deg: [S^{n}\to S^{n}]\to\mathbb{Z}$ counts wrapping. $\displaystyle\text{id}:S^{n}\to S^{n}$ has degree $\displaystyle1$, antipodal $\displaystyle A(x)=-x$ has degree $\displaystyle(-1)^{n+1}$. Odd map $\displaystyle S^{n}\to S^{n}$ has odd degree. Continuous deformation cannot change integer degree.

**Homology:** $\displaystyle H_{n}(S^{n})\cong\mathbb{Z}$, nontrivial $\displaystyle n$-cycle, while $\displaystyle H_{n}(S^{n-1})=0$. So $\displaystyle S^{n}$ cannot collapse antipodally into lower sphere. Algebraic topology converts geometric intuition into algebraic obstruction.

**Why higher dimensions harder:** $\displaystyle S^{1}\to\mathbb{R}$ needs one equation, IVT suffices. $\displaystyle S^{2}\to\mathbb{R}^{2}$ needs

$$\displaystyle f(x)=(f_{1}(x),f_{2}(x)),\quad f_{1}(x)=f_{1}(-x),\;f_{2}(x)=f_{2}(-x)$$

simultaneously. Finding zero of one coordinate easy, simultaneous needs deeper.

Inductive picture: $\displaystyle Z_{1}=\{x:g_{1}(x)=0\}\sim S^{n-1}$, then $\displaystyle g_{2}=0$ on $\displaystyle Z_{1}$ like $\displaystyle S^{n-1}\to\mathbb{R}$, etc.:

$$\displaystyle S^{n}\xrightarrow{g_{1}=0}Z_{1}\sim S^{n-1}\xrightarrow{g_{2}=0}Z_{2}\sim S^{n-2}\to\cdots\to Z_{n}\neq\emptyset$$

Precise needs $\displaystyle\mathbb{Z}_{2}$-homology non-triviality.

### The Basic Idea, Proof Sketch, and Core Strategy

**Basic idea:** $\displaystyle n=1$: $\displaystyle f:S^{1}\to\mathbb{R}$ temperature around circle, $\displaystyle g(x)=f(x)-f(-x)$ odd, sign change $\implies$ zero. $\displaystyle n=2$: $\displaystyle f(p)=(T(p),P(p))$, theorem gives antipodal pair same temperature and pressure simultaneously — not just same temperature somewhere else and same pressure elsewhere, same pair for both.

$$
\begin{align*}
g&:S^{1}\to\mathbb{R},\;g(x)=f(x)-f(-x),\;g(-x)=-g(x)\\[5pt]
\text{If }g(x_{0})>0,\;g(-x_{0})<0,\;\text{IVT}\implies\exists x:g(x)=0
\end{align*}
$$

**Proof sketch $n=1,2$:**

$$
\begin{align*}
n=1&:\;S^{1}=\{(\cos\theta,\sin\theta)\},\;g(\theta)=f(\theta)-f(\theta+\pi),\;g(\theta+\pi)=-g(\theta)\\[5pt]
&\;g(\theta_{0})g(\theta_{0}+\pi)<0\implies g(\theta^{*})=0\\[5pt]
n\ge2&:\;\text{Suppose }f(x)\neq f(-x)\;\forall x\implies h(x)=\dfrac{f(x)-f(-x)}{\|f(x)-f(-x)\|}:S^{n}\to S^{n-1}\text{ odd}\\[5pt]
&\;\text{Borsuk degree shows no such }h\text{ exists}
\end{align*}
$$

**General 5-step strategy:**

$$
\begin{align*}
1&:\;g(x)=f(x)-f(-x)\text{ odd}\\[5pt]
2&:\;\text{Assume }g(x)\neq0\;\forall x\\[5pt]
3&:\;h(x)=\dfrac{g(x)}{\|g(x)\|}:S^{n}\to S^{n-1}\text{ odd}\\[5pt]
4&:\;\text{Topological obstruction: no such }h\\[5pt]
5&:\;\text{Thus }g(x)=0\text{ some }x\implies f(x)=f(-x)
\end{align*}
$$

Deepest part Step 4 uses degree, homology, Tucker lemma.

Central insight:

$$\displaystyle\boxed{\text{Antipodal symmetry + continuity + dimension}\Longrightarrow\text{forced coincidence}}$$

### Ham-Sandwich Theorem — Canonical Application

**Theorem:** In $\displaystyle\mathbb{R}^{d}$, given $\displaystyle d$ finite measures, exists hyperplane simultaneously bisecting all.

In $\displaystyle\mathbb{R}^{3}$: ham, bread, bread — one plane cuts each volume half.

**Parameterizing planes:** Unit vector $\displaystyle u\in S^{2}$ = normal direction. Plane $\displaystyle P_{u,t}=\{x\in\mathbb{R}^{3}:u\cdot x=t\}$, $\displaystyle u$ orientation, $\displaystyle t$ position.

**Choosing bisecting first object:** Fix $\displaystyle u$, slide $\displaystyle t$ from $-\infty$ to $\infty$, volume on positive side continuous from $0$ to $\displaystyle\mu_{1}(\mathbb{R}^{3})$. By IVT, exists $\displaystyle t(u)$ where half volume each side. Choose that plane continuously in $\displaystyle u$.

**Reversing direction:** $\displaystyle -u$ represents same geometric plane $\displaystyle u\cdot x=t\iff(-u)\cdot x=-t$, sides exchanged.

**Measuring other two:** $\displaystyle\mu_{1},\mu_{2},\mu_{3}$, plane for $\displaystyle u$ bisects $\displaystyle\mu_{1}$ by construction. Define

$$
\begin{align*}
f_{1}(u)&=\text{mass of }\mu_{2}\text{ on positive side}\\[5pt]
f_{2}(u)&=\text{mass of }\mu_{3}\text{ on positive side}\\[5pt]
f(u)&=(f_{1}(u),f_{2}(u)):S^{2}\to\mathbb{R}^{2}\text{ continuous}
\end{align*}
$$

Borsuk–Ulam gives $\displaystyle u^{*}$ with $\displaystyle f(u^{*})=f(-u^{*})$. But $\displaystyle f(-u^{*})$ = masses on negative side. Equality means

$$
\begin{align*}
\mu_{2}(\text{positive})&=\mu_{2}(\text{negative})\\[5pt]
\mu_{3}(\text{positive})&=\mu_{3}(\text{negative})
\end{align*}
$$

So plane bisects $\displaystyle\mu_{2},\mu_{3}$ too, and $\displaystyle\mu_{1}$ by construction. One plane bisects all three.

Strategy:

$$\displaystyle\boxed{\text{Geometric problem}\to\text{continuous map}\to\text{topological theorem}\to\text{geometric solution}}$$

### Connection to Combinatorics — Lovász–Kneser

Kneser graph $\displaystyle KG(n,k)$: vertices $\displaystyle k$-subsets of $\displaystyle[n]$, edge when disjoint. Kneser conjectured 1955 $\displaystyle\chi(KG(n,k))=n-2k+2$.

Upper bound $\displaystyle\le n-2k+2$ via anchor coloring: colors $1,\dots,n-2k+1$ assign to $k$-sets containing $i$, final color dump sets inside remaining $2k-1$ elements — any two intersect by pigeonhole.

Lower bound hard: Lovász 1978 used Borsuk–Ulam. Assume $m=n-2k+1$ colorable, build $\displaystyle f:S^{m}\to\mathbb{R}^{m}$ via hemispheres $\displaystyle H(x)$ containing $k$-sets. Borsuk–Ulam gives $\displaystyle x^{*}$ with $\displaystyle f(x^{*})=f(-x^{*})$, forcing both $\displaystyle H(x^{*})$ and $\displaystyle H(-x^{*})$ contain same color $k$-sets disjoint — invalid coloring. Hence need $m+1$.

Importance not just one graph, but launch of **topological combinatorics** — topological invariants give lower bounds for combinatorial quantities.

### Lusternik–Schnirelmann Covering, Borsuk Number, Intuitive Analogies

**Covering theorem:** If $\displaystyle S^{n}=F_{1}\cup\cdots\cup F_{n+1}$ closed sets, some $\displaystyle F_{i}$ contains antipodal pair. Equivalent to Borsuk–Ulam: if none contained pair, could build map contradicting.

**Borsuk partition problem:** Distinct but related — given bounded set in $\displaystyle\mathbb{R}^{d}$, into how many subsets can it always be partitioned so each has smaller diameter? Motivated by Borsuk, involves geometry-topology.

**Intuitive analogy:**

$$
\begin{align*}
f:S^{2}\to\mathbb{R}&:\;\exists\text{ antipodal equal values}\\[5pt]
f:S^{2}\to\mathbb{R}^{2}&:\;\exists\text{ antipodal equal vector}\\[5pt]
f:S^{2}\to\mathbb{R}^{3}&:\;\text{no guarantee, inclusion }S^{2}\subset\mathbb{R}^{3}\text{ separates opposite points}
\end{align*}
$$

Dimension matters: $\displaystyle n$ measurements on $\displaystyle S^{n}$ forces coincidence; $\displaystyle n+1$ measurements may avoid.

**Why surprising:** One might try assign values increasing steadily around circle, but circle closes — trying to make side larger than opposite forces reversal elsewhere. Difference $\displaystyle g(x)=f(x)-f(-x)$, $\displaystyle g(-x)=-g(x)$, sign reversal unless zero.

**IVT comparison:**

$$\displaystyle\boxed{\text{IVT: continuity + sign change}\implies\text{zero}}$$

$$\displaystyle\boxed{\text{Borsuk–Ulam: continuity + antipodal symmetry}\implies\text{zero}}$$

Second is higher-dimensional generalization: IVT is $\displaystyle S^{0}\to\mathbb{R}$? Actually $\displaystyle S^{1}$ case uses IVT, higher uses degree.

### Summary

The Borsuk–Ulam theorem states every continuous $\displaystyle f:S^{n}\to\mathbb{R}^{n}$ has antipodal coincidence:

$$\displaystyle\boxed{\exists x\in S^{n}:f(x)=f(-x)}$$

Ingredients:

1. $\displaystyle S^{n}$ provides antipodal involution $\displaystyle x\mapsto -x$.
2. Continuity prevents abrupt separation.
3. Equal dimensions create sharp obstruction: $\displaystyle m<n$ larger coincidence set, $\displaystyle m=n$ at least one pair, $\displaystyle m>n$ may avoid.
4. Odd formulation $\displaystyle g(-x)=-g(x)\implies g(x)=0$ some $\displaystyle x$, and no odd map $\displaystyle S^{n}\to S^{n-1}$.
5. One-dimensional case direct IVT: $\displaystyle g(\theta)=f(\theta)-f(\theta+\pi)$, $\displaystyle g(\theta+\pi)=-g(\theta)$.
6. Higher dimensions need degree/homology: odd map $\displaystyle S^{n}\to S^{n}$ has odd degree $\neq0$.
7. Ham-sandwich follows by parametrizing planes by $\displaystyle S^{2}$, choosing bisecting position for $\displaystyle\mu_{1}$, measuring other two as $\displaystyle f:S^{2}\to\mathbb{R}^{2}$, applying Borsuk–Ulam.
8. Combinatorial applications via Lovász–Kneser $\displaystyle\chi=n-2k+2$, necklace splitting, consensus halving — all same scheme geometric problem $\to$ continuous map $\to$ topological theorem $\to$ geometric solution.

Broader lesson: **Continuous deformation cannot destroy certain global structures.** Borsuk–Ulam turns qualitative obstruction into concrete existence — somewhere on sphere, two exactly opposite points become indistinguishable under any continuous $\displaystyle n$-dimensional measurement.

## Lovász's Theorems

### Overview

The name **László Lovász** is associated with some of the most influential results in modern combinatorics, graph theory, discrete mathematics, optimization, probability, and theoretical computer science.

There is not one universally defined result called **"Lovász's Theorem."** Instead, Lovász proved or co-proved a collection of major theorems:

1. **The Perfect Graph Theorem (1972)**
2. **The Lovász Local Lemma (1975, with Paul Erdős)**
3. **The Lovász–Kneser Theorem / Lovász's proof of Kneser's conjecture (1978)**
4. **The Lovász Sandwich Theorem and Lovász theta function (1979)**

These results look different:

- Perfect Graph Theorem concerns graph structure.
- Lovász Local Lemma concerns probability and existence.
- Lovász–Kneser connects topology with graph coloring.
- Lovász theta connects graph theory with geometry, linear algebra, optimization, and semidefinite programming.

Together they illustrate one contribution:

> **Difficult discrete problems can often become easier when translated into another language — topology, probability, geometry, linear algebra, or optimization.**

This way of thinking is now central to modern combinatorics.

### Who Was László Lovász?

**László Lovász** born Budapest 1948, Hungarian mathematician with enormous influence on graph theory and discrete mathematics.

Contributions: graph theory, combinatorial optimization, algorithms, probability, theoretical computer science, algebraic methods in combinatorics, topology and topological combinatorics, convex optimization.

Institutions: Eötvös Loránd University, University of Toronto, Microsoft Research. Honors: **Wolf Prize**, **Abel Prize 2021**, Knuth Prize, Fulkerson Prize. Abel citation emphasized foundational contributions to discrete mathematics and theoretical computer science.

His work helped transform graph theory from isolated puzzles into discipline connected to many other areas.

### Historical Background: Graph Theory Before Lovász

A graph

$$\displaystyle G=(V,E),\qquad V=\text{vertices},\;E=\text{edges}$$

represents cities-roads, computers-links, social relationships, molecules, web hyperlinks, task dependencies.

Early graph theory influenced by Euler Königsberg and four-color problem. Twentieth century asked:

- How many colors needed? $\displaystyle\chi(G)$
- How large a complete subgraph? $\displaystyle\omega(G)$
- Partitions, embeddings, independent sets, optimization

These often computationally difficult. Lovász showed difficult graph problems can be attacked by importing ideas from other areas.

### A Major Theme in Lovász's Work

$$\displaystyle\boxed{\text{Discrete problem}\longrightarrow\text{mathematical translation}\longrightarrow\text{new tool}\longrightarrow\text{structural conclusion}}$$

- Perfect graphs: coloring through structure of graph and complement.
- Kneser graphs: discrete coloring $\to$ topology $\to$ Borsuk–Ulam.
- Theta: difficult invariant $\to$ vectors, geometry, semidefinite optimization.
- Local Lemma: construction $\to$ probability of rare locally dependent events.

Philosophy:

> **When a combinatorial problem looks difficult in its original language, change the language.**

---

## Perfect Graph Theorem

### Historical Discovery

First major result 1972 **Perfect Graph Theorem**, resolving **Weak Perfect Graph Conjecture** of Claude Berge 1960s. Question: is perfection preserved under complementation? Lovász proved yes.

### Clique Number and Chromatic Number

Clique = set vertices pairwise connected. Largest clique size

$$\displaystyle \omega(G)=\text{size of largest clique in }G$$

Proper coloring: adjacent vertices different colors. Smallest colors needed

$$\displaystyle \chi(G)$$

For every graph

$$\displaystyle\boxed{\chi(G)\ge\omega(G)}$$

If clique size 5, need at least 5 colors.

### Definition of a Perfect Graph

Graph $\displaystyle G$ perfect if every induced subgraph $\displaystyle H$ satisfies

$$\displaystyle\boxed{\chi(H)=\omega(H)}$$

Induced subgraph: choose vertices and keep all edges between them. Perfection strong: equality must hold for every induced subgraph, not just $\displaystyle G$.

### Why Perfect Graphs Matter

For arbitrary graphs, $\displaystyle\chi$ and $\displaystyle\omega$ computationally difficult $\left(\text{NP-hard}\right)$. For perfect graphs structure forces equality on every induced subgraph, so understanding largest clique determines coloring. Many optimization problems tractable on perfect graphs.

### Complement

$$\displaystyle G=(V,E),\quad \overline{G}\text{ same }V,\quad uv\in E(\overline{G})\iff uv\notin E(G)$$

Edges become non-edges, $\displaystyle\overline{\overline{G}}=G$.

Complementation exchanges:

$$\displaystyle\boxed{\omega(G)=\alpha(\overline{G})},\quad\boxed{\alpha(G)=\omega(\overline{G})}$$

where $\displaystyle\alpha$ independence number. Coloring of $\displaystyle G$ = partition into independent sets = clique covering of $\displaystyle\overline{G}$.

### Lovász's Perfect Graph Theorem

$$\displaystyle\boxed{G\text{ perfect}\iff\overline{G}\text{ perfect}}$$

Called Weak Perfect Graph Theorem. Remarkable because complementation dramatically changes graph while preserving perfection.

Example bipartite graphs: $\displaystyle V=A\cup B$, edges only $\displaystyle A$-$B$, $\displaystyle\chi\le2$, $\displaystyle\omega\le2$, every induced subgraph bipartite $\implies$ perfect. Complement $\displaystyle\overline{K_{3,3}}=K_{3}\cup K_{3}$ two disjoint triangles, not bipartite but still perfect — illustrates theorem.

### Strong Perfect Graph Theorem

Distinct: Perfect Graph Theorem says perfection preserved under complement. Strong Perfect Graph Theorem $\left(\text{Chudnovsky, Robertson, Seymour, Thomas 2002}\right)$ characterizes:

$$\displaystyle\boxed{G\text{ perfect}\iff G\text{ contains no odd hole and no odd antihole}}$$

Odd hole = induced cycle length $\ge5$ odd, odd antihole = complement of such cycle.

Modern perfect graph theory: structural decompositions, recognition in polynomial time, optimization via $\displaystyle\vartheta$.

---

## Lovász Local Lemma

### Discovery

Developed by Erdős and Lovász 1975, belongs to probabilistic method: show random construction avoids every bad event with positive probability $\implies$ successful construction exists.

### Basic Problem

Bad events $\displaystyle A_{1},\dots,A_{n}$. Want

$$\displaystyle\Pr\left(\bigcap_{i=1}^{n}\overline{A_{i}}\right)>0$$

If independent, easy. Real problems dependent but only locally.

Dependency graph: vertex per event, edge when events may depend. Degree $\le d$ means each event interacts with at most $\displaystyle d$ others.

### Symmetric Local Lemma

If $\displaystyle\Pr(A_{i})\le p$ and each event depends on at most $\displaystyle d$ others, and

$$\displaystyle\boxed{e\,p(d+1)\le1},\qquad e\approx2.71828$$

then

$$\displaystyle\boxed{\Pr\left(\bigcap_{i=1}^{n}\overline{A_{i}}\right)>0}$$

Existence statement.

Meaning:

$$\displaystyle\boxed{\text{Rare events}+\text{limited dependence}\implies\text{simultaneous avoidance}}$$

### Example: Random Coloring

Color vertices randomly with $\displaystyle q$ colors. For edge $\displaystyle uv$, bad event $\displaystyle A_{uv}=\{u,v\text{ same color}\}$, $\displaystyle\Pr(A_{uv})=\dfrac1q$. $\displaystyle A_{uv}$ depends only on edges sharing endpoint with $\displaystyle u$ or $\displaystyle v$ — local. If $\displaystyle q$ large relative to max degree, Local Lemma proves proper coloring exists, stronger than naive union bound.

### Algorithmic Local Lemma — Moser–Tardos 2010

For years existential only. Moser and Tardos 2010 gave algorithm:

1. Generate random configuration.
2. Find violated $\displaystyle A_{i}$.
3. Resample variables involved in $\displaystyle A_{i}$.
4. Repeat.

Local repair, not full restart. Received Paris Kanellakis Award.

Modern developments: distributed versions, cluster-expansion, entropy variants, applications to constraint satisfaction, SAT, hypergraph coloring, coding theory, sparse structures.

In distributed system each processor knows only local neighborhood — exactly dependency structure handled by Local Lemma, making it central to distributed algorithms.

---

## Lovász–Kneser Theorem and Borsuk–Ulam

### Kneser Graph Construction

Let $\displaystyle[n]=\{1,\dots,n\}$. Kneser graph

$$\displaystyle KG(n,k):\;V=\{k\text{-subsets of }[n]\},\;|V|=\binom{n}{k},\;A\sim B\iff A\cap B=\emptyset$$

### Kneser's Conjecture — History

Martin Kneser 1955 observed easy upper bound $\displaystyle\chi(KG(n,k))\le n-2k+2$ via explicit anchor coloring and conjectured equality. For 23 years combinatorial attempts failed due to high symmetry.

László Lovász 1978 proved lower bound using **Borsuk–Ulam theorem**, paper _Kneser's conjecture, chromatic number, and homotopy_. Introduced neighborhood complex $\displaystyle N(G)$ where simplices = sets with common neighbor, related to sphere. This was birth of **topological combinatorics**.

Shortly after: Imre Bárány shorter proof, Alexander Schrijver 1978 found subgraph $\displaystyle SG(n,k)$ stable Kneser still $\displaystyle\chi=n-2k+2$ but vertex-critical.

### Lovász–Kneser Formula

$$\displaystyle\boxed{\chi(KG(n,k))=n-2k+2\text{ for }n\ge2k}$$

If $\displaystyle n<2k$, any two $\displaystyle k$-sets intersect by pigeonhole, graph edgeless, $\displaystyle\chi=1$.

#### Example $KG(5,2)$ = Petersen

Vertices all 2-subsets of $\{1,\dots,5\}$, $\displaystyle\binom52=10$. $\{1,2\}$ adjacent $\{3,4\}$ because $\displaystyle\{1,2\}\cap\{3,4\}=\emptyset$, not adjacent $\{2,3\}$ because intersect $\{2\}$.

$$
\begin{align*}
\chi(KG(5,2))&=5-2\cdot2+2=3
\end{align*}
$$

3-coloring via anchor:

$$
\begin{align*}
\text{Color1}&:\{12,13,14,15\}\text{ share }1\\[5pt]
\text{Color2}&:\{23,24,25\}\text{ share }2\\[5pt]
\text{Color3}&:\{34,35,45\}\subseteq\{3,4,5\},| \{3,4,5\}|=3=2k-1\text{ so pairwise intersect}
\end{align*}
$$

#### General Upper Bound Coloring Strategy

$\displaystyle c=n-2k+2$ colors: $\displaystyle c-1=n-2k+1$ anchor colors plus final dump.

For $k$-set $F$:

$$
\begin{align*}
\text{For }i=1\text{ to }n-2k+1:&\;\text{if }i\in F\text{ then color}(F)=i\text{ stop}\\[5pt]
\text{Else }&F\subseteq\{n-2k+2,\dots,n\},\;|\cdot|=2k-1,\text{ color }c
\end{align*}
$$

Valid because each anchor color class shares element $\displaystyle i$, no edge. Final class inside $(2k-1)$-set, any two $\displaystyle k$-sets intersect:

$$\displaystyle |A|=|B|=k,\;|A\cup B|\le2k-1\implies|A\cap B|\ge1$$

So $\displaystyle\chi\le n-2k+2$. Hard part $\displaystyle\ge$.

### Borsuk–Ulam Theorem — The Topological Engine

**Borsuk–Ulam:** One of central results algebraic topology. Continuous cannot separate every point on sphere from antipode when dimensions equal.

$$\displaystyle\boxed{\text{If }f:S^{n}\to\mathbb{R}^{n}\text{ continuous, }\exists x\in S^{n}:f(x)=f(-x)}$$

Here $\displaystyle S^{n}=\{x\in\mathbb{R}^{n+1}:\|x\|=1\}$, $\displaystyle -x$ antipodal. No assumption symmetric, injective, differentiable — continuity alone forces coincidence.

**History:** Stanisław Ulam 1930 conjectured in Lwów, Karol Borsuk 1933 proved _Drei Sätze über die $n$-dimensionale euklidische Sphäre_ via degree theory. Equivalents quickly:

$$
\begin{align*}
\text{(BU1)}&\;f:S^{n}\to\mathbb{R}^{n}\text{ cont.}\implies\exists x:f(x)=f(-x)\\[5pt]
\text{(BU2)}&\;\nexists\text{ odd cont. }h:S^{n}\to S^{n-1},\;h(-x)=-h(x)\\[5pt]
\text{(LS)}&\;\text{Lyusternik–Schnirelmann: Cover }S^{n}\text{ by }n+1\text{ closed sets, one contains antipodal pair}
\end{align*}
$$

**Basic idea $n=1$:** $\displaystyle S^{1}$ circle, $\displaystyle f:S^{1}\to\mathbb{R}$ temperature. Define $\displaystyle g(x)=f(x)-f(-x)$, $\displaystyle g(-x)=-g(x)$ odd. If $\displaystyle g(x_{0})>0$ then $\displaystyle g(-x_{0})<0$, connectedness $\implies$ IVT $\exists x:g(x)=0$. So

$$
\begin{align*}
g&:S^{1}\to\mathbb{R},\;g(x)=f(x)-f(-x),\;g(-x)=-g(x)\\[5pt]
\text{If }g(x_{0})>0,\;g(-x_{0})<0\implies\exists x:g(x)=0
\end{align*}
$$

$n=2$: Earth, $\displaystyle f(p)=(T(p),P(p))$, theorem gives antipodal pair same temperature and pressure simultaneously — same pair for both coordinates, stronger than separate.

**Continuity role:** Discontinuous $\displaystyle f(x)=1$ upper hemisphere $0$ lower can avoid antipodal equality except equator, but discontinuous. Continuity prevents jump.

**Dimension sharpness:**

$$
\begin{align*}
m<n&:\;f:S^{n}\to\mathbb{R}^{m}\implies\dim\{x:f(x)=f(-x)\}\ge n-m\\[5pt]
m=n&:\;\exists\text{ coincidence (Borsuk–Ulam)}\\[5pt]
m>n&:\;\text{possible no coincidence, e.g. inclusion }S^{n}\hookrightarrow\mathbb{R}^{n+1}
\end{align*}
$$

**Deeper meaning:** Set $\displaystyle g(x)=f(x)-f(-x)$. Then $\displaystyle f(x)=f(-x)\iff g(x)=0$. So theorem equivalent to **Every continuous odd map $\displaystyle S^{n}\to\mathbb{R}^{n}$ must vanish somewhere.**

If $\displaystyle g$ never zero, normalize

$$\displaystyle h(x)=\dfrac{g(x)}{\|g(x)\|}:S^{n}\to S^{n-1},\quad h(-x)=-h(x)$$

odd map to lower sphere. Borsuk–Ulam says no such map exists. Why? Degree: odd map $\displaystyle S^{n}\to S^{n}$ has odd degree $\neq0$, while map factoring through $\displaystyle S^{n-1}$ has degree $0$; homology $\displaystyle H_{n}(S^{n})\cong\mathbb{Z}$, $\displaystyle H_{n}(S^{n-1})=0$ — algebraic obstruction.

$$\displaystyle\boxed{\text{Antipodal symmetry + continuity + dimension}\implies\text{forced coincidence}}$$

**General proof strategy:**

$$
\begin{align*}
1&:\;g(x)=f(x)-f(-x)\text{ odd}\\[5pt]
2&:\;\text{Assume }g(x)\neq0\;\forall x\\[5pt]
3&:\;h(x)=g(x)/\|g(x)\|:S^{n}\to S^{n-1}\text{ odd}\\[5pt]
4&:\;\text{Topological obstruction: no such }h\\[5pt]
5&:\;\text{Thus }g(x)=0\text{ some }x\implies f(x)=f(-x)
\end{align*}
$$

Higher dimensions harder because need $\displaystyle n$ equations $\displaystyle g_{1}(x)=\cdots=g_{n}(x)=0$ simultaneously — IVT insufficient, needs degree/homology.

### Lovász Topological Proof Sketch

Assume for contradiction $\displaystyle KG(n,k)$ $m=n-2k+1$ colorable. Place $\displaystyle n$ points in general position on $\displaystyle S^{m}$. For $\displaystyle x\in S^{m}$, let $\displaystyle H(x)$ open hemisphere centered at $\displaystyle x$. Define continuous $\displaystyle f:S^{m}\to\mathbb{R}^{m}$ where $\displaystyle f_{i}(x)$ measures presence of color $\displaystyle i$ $k$-sets inside $\displaystyle H(x)$. Borsuk–Ulam gives $\displaystyle x^{*}$ with $\displaystyle f(x^{*})=f(-x^{*})$. If $\displaystyle f_{i}(x^{*})>0$, both $\displaystyle H(x^{*})$ and $\displaystyle H(-x^{*})$ contain color $\displaystyle i$ $k$-sets — but hemispheres disjoint, so those $k$-sets disjoint, edge inside same color — invalid. So all $\displaystyle f_{i}(x^{*})=0$: neither hemisphere contains any colored $k$-set, meaning each contains $<k$ points of $\displaystyle[n]$, so $\ge n-2k+2$ points lie on equator $\displaystyle S^{m-1}$, contradicting general position $\displaystyle\le m=n-2k+1$. Hence need $\displaystyle m+1$ colors.

Conceptual summary:

$$\displaystyle\boxed{\text{too few colors}\implies\text{forbidden odd map }S^{m}\to S^{m-1}\implies\text{contradiction}}$$

General paradigm:

$$\displaystyle\boxed{\text{Discrete object}\to\text{topological space}\to\text{topological invariant}\to\text{combinatorial bound}}$$

This method now used in graph coloring, hypergraph, discrete geometry, fair division.

### Other Applications of Borsuk–Ulam

- **Ham Sandwich:** In $\displaystyle\mathbb{R}^{d}$, $\displaystyle d$ volumes can be simultaneously bisected by hyperplane. Proof: param directions by $\displaystyle S^{d}$, choose $\displaystyle t(u)$ bisecting $\displaystyle\mu_{1}$ via IVT, define $\displaystyle f(u)=(\mu_{2}^{+}-\mu_{2}^{-},\dots)$ $\displaystyle S^{d}\to\mathbb{R}^{d-1}$? Actually $\displaystyle S^{d}\to\mathbb{R}^{d-1}$ after fixing? Standard $\displaystyle S^{d}\to\mathbb{R}^{d}$ version gives bisection. Steps: orientation $\displaystyle u$, plane $\displaystyle P_{u,t}=\{x:u\cdot x=t\}$, $\displaystyle f_{i}(u)=$ mass of object $i+1$ positive side, Borsuk–Ulam gives $\displaystyle u^{*}$ with $\displaystyle f(u^{*})=f(-u^{*})$ meaning positive=negative side $\implies$ bisects.

- **Necklace splitting:** $\displaystyle t$ bead types, $\displaystyle k$ thieves, $\le t(k-1)$ cuts suffice — via $\displaystyle S^{t(k-1)}$.

- **Consensus halving:** $\displaystyle n$ people value cake, $\le n$ cuts partition into two pieces each values half — via $\displaystyle S^{n}$.

- **Covering theorem:** $\displaystyle S^{n}=F_{1}\cup\cdots\cup F_{n+1}$ closed $\implies$ some $\displaystyle F_{i}$ contains antipodal pair.

---

## Lovász Theta Function

### Definition and Sandwich Theorem

1979 introduced **Lovász theta** $\displaystyle\vartheta(G)$, connecting graph theory, linear algebra, geometry, semidefinite programming.

Lovász Sandwich Theorem:

$$\displaystyle\boxed{\omega(G)\le\vartheta(\overline{G})\le\chi(G)}$$

Called sandwich because difficult $\displaystyle\omega,\chi$ trapped between tractable $\displaystyle\vartheta$.

Why important: $\displaystyle\omega$ and $\displaystyle\chi$ NP-hard generally, but $\displaystyle\vartheta$ can be formulated as semidefinite program:

$$
\begin{align*}
\text{max }&C\bullet X\\[5pt]
\text{s.t. }&A_{i}\bullet X=b_{i}\\[5pt]
&X\succeq0
\end{align*}
$$

$\displaystyle X\succeq0$ means $\displaystyle z^{T}Xz\ge0\;\forall z$. SDP solvable in polynomial time numerically, gives bounds.

### Geometric Picture

Assign vector $\displaystyle v_{i}$ per vertex, orthogonality represents non-adjacency $\displaystyle v_{i}^{T}v_{j}=0$ if non-edge? Various formulations. Optimization asks how tightly vectors can be arranged relative to handle. So

$$\displaystyle\boxed{\text{graph}\to\text{vectors}\to\text{geometry}\to\text{optimization}}$$

Not exact always: $\displaystyle\omega(G)<\vartheta(\overline{G})<\chi(G)$ may occur. But for perfect graphs bounds collapse to exact.

### Shannon Capacity

Shannon introduced graph model for distinguishability of signals. Shannon capacity $\displaystyle\Theta(G)$ asymptotic efficiency. Lovász showed

$$\displaystyle\boxed{\Theta(G)\le\vartheta(G)}$$

Famous $\displaystyle C_{5}$ five-cycle:

$$\displaystyle\boxed{\Theta(C_{5})=\vartheta(C_{5})=\sqrt5}$$

Problem about communication solved via geometric invariant.

Modern connections: quantum information — graphs model compatibility, vectors and SDP fit quantum mechanics, appears in quantum contextuality, nonlocal correlations, state discrimination.

### Philosophy of Relaxation

Hard discrete $\displaystyle\mathcal{F}_{\text{discrete}}\subseteq\mathcal{F}_{\text{relaxed}}$ larger easier set. Relaxed optimum gives bound. Theta is powerful because relaxation geometrically meaningful and computationally tractable.

---

## Historical Timeline and Modern Developments

### Timeline

$$
\begin{array}{c|l}
\text{Year}&\text{Development}\\\hline
1930&\text{Ulam conjectures Borsuk–Ulam}\\[5pt]
1933&\text{Borsuk proves, Lyusternik–Schnirelmann covering}\\[5pt]
1955&\text{Kneser proposes } \chi=n-2k+2\\[5pt]
1960s&\text{Berge perfect graphs}\\[5pt]
1972&\text{Lovász Perfect Graph Theorem }G\text{ perfect}\iff\overline{G}\text{ perfect}\\[5pt]
1975&\text{Erdős–Lovász Local Lemma }e p(d+1)\le1\\[5pt]
1978&\text{Lovász proves Kneser via Borsuk–Ulam, launches topological combinatorics; Schrijver stable Kneser}\\[5pt]
1979&\text{Lovász theta }\omega\le\vartheta(\overline{G})\le\chi\\[5pt]
2002&\text{Strong Perfect Graph Theorem Chudnovsky–Robertson–Seymour–Thomas}\\[5pt]
2003&\text{Matoušek book Using Borsuk–Ulam}\\[5pt]
2010&\text{Moser–Tardos algorithmic Local Lemma}\\[5pt]
\text{21st c.}&\text{Expansion into optimization, algorithms, information theory, quantum information}
\end{array}
$$

### Modern Developments

- **Perfect graphs:** structural decompositions, polynomial recognition via Strong theorem, optimization.
- **Topological combinatorics:** simplicial complexes, neighborhood complexes, independence complexes, homology, $\displaystyle\mathbb{Z}_{2}$-index, box complexes, Hom-complexes. Strategy $\displaystyle\text{Discrete}\to\text{space}\to\text{obstruction}\to\text{bound}$ now standard.
- **Local Lemma:** algorithmic, distributed, constructive, cluster-expansion, entropy variants. Distributed computing: each processor knows local neighborhood — exactly dependency structure.
- **Theta:** approximation algorithms, SDP, graph products, coding theory $\displaystyle\text{graph geometry}\to\text{independence bounds}\to\text{coding bounds}$, Shannon capacity.

Applications: scheduling $\left(\text{conflict graph, }\chi\text{ = slots, perfect }\implies\chi=\omega\right)$, frequency assignment $\left(\text{transmitters vertices, interference edges, coloring = frequencies}\right)$, constraint satisfaction $\left(\text{local dependencies, Local Lemma}\right)$, network science, coding theory.

### Comparing Results

| Result          | Year | Area                      | Idea                                                         |
| --------------- | ---: | ------------------------- | ------------------------------------------------------------ |
| Perfect Graph   | 1972 | Graph theory              | Perfection preserved by complement                           |
| Local Lemma     | 1975 | Probability               | Rare locally dependent bad events avoidable                  |
| Kneser          | 1978 | Topological combinatorics | Topology lower bound $\displaystyle\chi=n-2k+2$              |
| Theta           | 1979 | Optimization              | Geometry+SDP bounds $\displaystyle\omega\le\vartheta\le\chi$ |
| Algorithmic LLL | 2010 | Algorithms                | Local resampling constructs LLL objects                      |

### Unified View and Final Perspective

Formulas:

$$
\begin{align*}
\text{Perfect:}&\;G\text{ perfect}\iff\overline{G}\text{ perfect},\;G\text{ perfect}\iff\forall H\subseteq_{\text{ind}}G,\chi(H)=\omega(H)\\[5pt]
\text{LLL:}&\;e p(d+1)\le1\implies\Pr(\bigcap\overline{A_{i}})>0\\[5pt]
\text{Kneser:}&\;\chi(KG(n,k))=n-2k+2\\[5pt]
\text{Sandwich:}&\;\omega(G)\le\vartheta(\overline{G})\le\chi(G)\\[5pt]
\text{Shannon:}&\;\Theta(G)\le\vartheta(G),\;\Theta(C_{5})=\sqrt5\\[5pt]
\text{Borsuk–Ulam:}&\;f:S^{n}\to\mathbb{R}^{n}\text{ cont.}\implies\exists x:f(x)=f(-x)\iff g(-x)=-g(x)\implies g(x)=0\iff\nexists\text{ odd }S^{n}\to S^{n-1}
\end{align*}
$$

Misconceptions:

- Not one Lovász theorem — specify which.
- Perfect Graph Theorem does not say every graph perfect, only $\displaystyle G$ perfect $\iff\overline{G}$ perfect.
- Theta not always equals $\displaystyle\chi$, it's bound.
- Local Lemma allows dependence, importance is limited dependence.
- Kneser proof not just coloring trick, introduced topology.

Philosophy:

$$\displaystyle\boxed{\text{When a problem is difficult in one language, translate it into another.}}$$

$$
\begin{align*}
\text{Perfect}&:\text{structure}\\[5pt]
\text{LLL}&:\text{probability}\\[5pt]
\text{Kneser}&:\text{topology via Borsuk–Ulam}\\[5pt]
\text{Theta}&:\text{geometry and optimization}
\end{align*}
$$

Together: $\displaystyle\text{Discrete problem}\to\text{new representation}\to\text{structural insight}\to\text{algorithm or proof}$ — central strategy modern discrete mathematics, theoretical computer science, information theory, quantum information.
