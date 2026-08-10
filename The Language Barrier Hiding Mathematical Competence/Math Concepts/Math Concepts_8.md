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

### Perfect Graph Theorem

#### Historical Discovery

First major result 1972 **Perfect Graph Theorem**, resolving **Weak Perfect Graph Conjecture** of Claude Berge 1960s. Question: is perfection preserved under complementation? Lovász proved yes.

#### Clique Number and Chromatic Number

Clique = set vertices pairwise connected. Largest clique size

$$\displaystyle \omega(G)=\text{size of largest clique in }G$$

Proper coloring: adjacent vertices different colors. Smallest colors needed

$$\displaystyle \chi(G)$$

For every graph

$$\displaystyle\boxed{\chi(G)\ge\omega(G)}$$

If clique size 5, need at least 5 colors.

#### Definition of a Perfect Graph

Graph $\displaystyle G$ perfect if every induced subgraph $\displaystyle H$ satisfies

$$\displaystyle\boxed{\chi(H)=\omega(H)}$$

Induced subgraph: choose vertices and keep all edges between them. Perfection strong: equality must hold for every induced subgraph, not just $\displaystyle G$.

#### Why Perfect Graphs Matter

For arbitrary graphs, $\displaystyle\chi$ and $\displaystyle\omega$ computationally difficult $\left(\text{NP-hard}\right)$. For perfect graphs structure forces equality on every induced subgraph, so understanding largest clique determines coloring. Many optimization problems tractable on perfect graphs.

#### Complement

$$\displaystyle G=(V,E),\quad \overline{G}\text{ same }V,\quad uv\in E(\overline{G})\iff uv\notin E(G)$$

Edges become non-edges, $\displaystyle\overline{\overline{G}}=G$.

Complementation exchanges:

$$\displaystyle\boxed{\omega(G)=\alpha(\overline{G})},\quad\boxed{\alpha(G)=\omega(\overline{G})}$$

where $\displaystyle\alpha$ independence number. Coloring of $\displaystyle G$ = partition into independent sets = clique covering of $\displaystyle\overline{G}$.

#### Lovász's Perfect Graph Theorem

$$\displaystyle\boxed{G\text{ perfect}\iff\overline{G}\text{ perfect}}$$

Called Weak Perfect Graph Theorem. Remarkable because complementation dramatically changes graph while preserving perfection.

Example bipartite graphs: $\displaystyle V=A\cup B$, edges only $\displaystyle A$-$B$, $\displaystyle\chi\le2$, $\displaystyle\omega\le2$, every induced subgraph bipartite $\implies$ perfect. Complement $\displaystyle\overline{K_{3,3}}=K_{3}\cup K_{3}$ two disjoint triangles, not bipartite but still perfect — illustrates theorem.

#### Strong Perfect Graph Theorem

Distinct: Perfect Graph Theorem says perfection preserved under complement. Strong Perfect Graph Theorem $\left(\text{Chudnovsky, Robertson, Seymour, Thomas 2002}\right)$ characterizes:

$$\displaystyle\boxed{G\text{ perfect}\iff G\text{ contains no odd hole and no odd antihole}}$$

Odd hole = induced cycle length $\ge5$ odd, odd antihole = complement of such cycle.

Modern perfect graph theory: structural decompositions, recognition in polynomial time, optimization via $\displaystyle\vartheta$.

---

### Lovász Local Lemma

#### Discovery

Developed by Erdős and Lovász 1975, belongs to probabilistic method: show random construction avoids every bad event with positive probability $\implies$ successful construction exists.

#### Basic Problem

Bad events $\displaystyle A_{1},\dots,A_{n}$. Want

$$\displaystyle\Pr\left(\bigcap_{i=1}^{n}\overline{A_{i}}\right)>0$$

If independent, easy. Real problems dependent but only locally.

Dependency graph: vertex per event, edge when events may depend. Degree $\le d$ means each event interacts with at most $\displaystyle d$ others.

#### Symmetric Local Lemma

If $\displaystyle\Pr(A_{i})\le p$ and each event depends on at most $\displaystyle d$ others, and

$$\displaystyle\boxed{e\,p(d+1)\le1},\qquad e\approx2.71828$$

then

$$\displaystyle\boxed{\Pr\left(\bigcap_{i=1}^{n}\overline{A_{i}}\right)>0}$$

Existence statement.

Meaning:

$$\displaystyle\boxed{\text{Rare events}+\text{limited dependence}\implies\text{simultaneous avoidance}}$$

#### Example: Random Coloring

Color vertices randomly with $\displaystyle q$ colors. For edge $\displaystyle uv$, bad event $\displaystyle A_{uv}=\{u,v\text{ same color}\}$, $\displaystyle\Pr(A_{uv})=\dfrac1q$. $\displaystyle A_{uv}$ depends only on edges sharing endpoint with $\displaystyle u$ or $\displaystyle v$ — local. If $\displaystyle q$ large relative to max degree, Local Lemma proves proper coloring exists, stronger than naive union bound.

#### Algorithmic Local Lemma — Moser–Tardos 2010

For years existential only. Moser and Tardos 2010 gave algorithm:

1. Generate random configuration.
2. Find violated $\displaystyle A_{i}$.
3. Resample variables involved in $\displaystyle A_{i}$.
4. Repeat.

Local repair, not full restart. Received Paris Kanellakis Award.

Modern developments: distributed versions, cluster-expansion, entropy variants, applications to constraint satisfaction, SAT, hypergraph coloring, coding theory, sparse structures.

In distributed system each processor knows only local neighborhood — exactly dependency structure handled by Local Lemma, making it central to distributed algorithms.

---

### Lovász–Kneser Theorem and Borsuk–Ulam

#### Kneser Graph Construction

Let $\displaystyle[n]=\{1,\dots,n\}$. Kneser graph

$$\displaystyle KG(n,k):\;V=\{k\text{-subsets of }[n]\},\;|V|=\binom{n}{k},\;A\sim B\iff A\cap B=\emptyset$$

#### Kneser's Conjecture — History

Martin Kneser 1955 observed easy upper bound $\displaystyle\chi(KG(n,k))\le n-2k+2$ via explicit anchor coloring and conjectured equality. For 23 years combinatorial attempts failed due to high symmetry.

László Lovász 1978 proved lower bound using **Borsuk–Ulam theorem**, paper _Kneser's conjecture, chromatic number, and homotopy_. Introduced neighborhood complex $\displaystyle N(G)$ where simplices = sets with common neighbor, related to sphere. This was birth of **topological combinatorics**.

Shortly after: Imre Bárány shorter proof, Alexander Schrijver 1978 found subgraph $\displaystyle SG(n,k)$ stable Kneser still $\displaystyle\chi=n-2k+2$ but vertex-critical.

#### Lovász–Kneser Formula

$$\displaystyle\boxed{\chi(KG(n,k))=n-2k+2\text{ for }n\ge2k}$$

If $\displaystyle n<2k$, any two $\displaystyle k$-sets intersect by pigeonhole, graph edgeless, $\displaystyle\chi=1$.

##### Example $KG(5,2)$ = Petersen

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

##### General Upper Bound Coloring Strategy

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

#### Borsuk–Ulam Theorem — The Topological Engine

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

#### Lovász Topological Proof Sketch

Assume for contradiction $\displaystyle KG(n,k)$ $m=n-2k+1$ colorable. Place $\displaystyle n$ points in general position on $\displaystyle S^{m}$. For $\displaystyle x\in S^{m}$, let $\displaystyle H(x)$ open hemisphere centered at $\displaystyle x$. Define continuous $\displaystyle f:S^{m}\to\mathbb{R}^{m}$ where $\displaystyle f_{i}(x)$ measures presence of color $\displaystyle i$ $k$-sets inside $\displaystyle H(x)$. Borsuk–Ulam gives $\displaystyle x^{*}$ with $\displaystyle f(x^{*})=f(-x^{*})$. If $\displaystyle f_{i}(x^{*})>0$, both $\displaystyle H(x^{*})$ and $\displaystyle H(-x^{*})$ contain color $\displaystyle i$ $k$-sets — but hemispheres disjoint, so those $k$-sets disjoint, edge inside same color — invalid. So all $\displaystyle f_{i}(x^{*})=0$: neither hemisphere contains any colored $k$-set, meaning each contains $<k$ points of $\displaystyle[n]$, so $\ge n-2k+2$ points lie on equator $\displaystyle S^{m-1}$, contradicting general position $\displaystyle\le m=n-2k+1$. Hence need $\displaystyle m+1$ colors.

Conceptual summary:

$$\displaystyle\boxed{\text{too few colors}\implies\text{forbidden odd map }S^{m}\to S^{m-1}\implies\text{contradiction}}$$

General paradigm:

$$\displaystyle\boxed{\text{Discrete object}\to\text{topological space}\to\text{topological invariant}\to\text{combinatorial bound}}$$

This method now used in graph coloring, hypergraph, discrete geometry, fair division.

#### Other Applications of Borsuk–Ulam

- **Ham Sandwich:** In $\displaystyle\mathbb{R}^{d}$, $\displaystyle d$ volumes can be simultaneously bisected by hyperplane. Proof: param directions by $\displaystyle S^{d}$, choose $\displaystyle t(u)$ bisecting $\displaystyle\mu_{1}$ via IVT, define $\displaystyle f(u)=(\mu_{2}^{+}-\mu_{2}^{-},\dots)$ $\displaystyle S^{d}\to\mathbb{R}^{d-1}$? Actually $\displaystyle S^{d}\to\mathbb{R}^{d-1}$ after fixing? Standard $\displaystyle S^{d}\to\mathbb{R}^{d}$ version gives bisection. Steps: orientation $\displaystyle u$, plane $\displaystyle P_{u,t}=\{x:u\cdot x=t\}$, $\displaystyle f_{i}(u)=$ mass of object $i+1$ positive side, Borsuk–Ulam gives $\displaystyle u^{*}$ with $\displaystyle f(u^{*})=f(-u^{*})$ meaning positive=negative side $\implies$ bisects.

- **Necklace splitting:** $\displaystyle t$ bead types, $\displaystyle k$ thieves, $\le t(k-1)$ cuts suffice — via $\displaystyle S^{t(k-1)}$.

- **Consensus halving:** $\displaystyle n$ people value cake, $\le n$ cuts partition into two pieces each values half — via $\displaystyle S^{n}$.

- **Covering theorem:** $\displaystyle S^{n}=F_{1}\cup\cdots\cup F_{n+1}$ closed $\implies$ some $\displaystyle F_{i}$ contains antipodal pair.

---

### Lovász Theta Function

#### Definition and Sandwich Theorem

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

#### Geometric Picture

Assign vector $\displaystyle v_{i}$ per vertex, orthogonality represents non-adjacency $\displaystyle v_{i}^{T}v_{j}=0$ if non-edge? Various formulations. Optimization asks how tightly vectors can be arranged relative to handle. So

$$\displaystyle\boxed{\text{graph}\to\text{vectors}\to\text{geometry}\to\text{optimization}}$$

Not exact always: $\displaystyle\omega(G)<\vartheta(\overline{G})<\chi(G)$ may occur. But for perfect graphs bounds collapse to exact.

#### Shannon Capacity

Shannon introduced graph model for distinguishability of signals. Shannon capacity $\displaystyle\Theta(G)$ asymptotic efficiency. Lovász showed

$$\displaystyle\boxed{\Theta(G)\le\vartheta(G)}$$

Famous $\displaystyle C_{5}$ five-cycle:

$$\displaystyle\boxed{\Theta(C_{5})=\vartheta(C_{5})=\sqrt5}$$

Problem about communication solved via geometric invariant.

Modern connections: quantum information — graphs model compatibility, vectors and SDP fit quantum mechanics, appears in quantum contextuality, nonlocal correlations, state discrimination.

#### Philosophy of Relaxation

Hard discrete $\displaystyle\mathcal{F}_{\text{discrete}}\subseteq\mathcal{F}_{\text{relaxed}}$ larger easier set. Relaxed optimum gives bound. Theta is powerful because relaxation geometrically meaningful and computationally tractable.

---

### Historical Timeline and Modern Developments

#### Timeline

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

#### Modern Developments

- **Perfect graphs:** structural decompositions, polynomial recognition via Strong theorem, optimization.
- **Topological combinatorics:** simplicial complexes, neighborhood complexes, independence complexes, homology, $\displaystyle\mathbb{Z}_{2}$-index, box complexes, Hom-complexes. Strategy $\displaystyle\text{Discrete}\to\text{space}\to\text{obstruction}\to\text{bound}$ now standard.
- **Local Lemma:** algorithmic, distributed, constructive, cluster-expansion, entropy variants. Distributed computing: each processor knows local neighborhood — exactly dependency structure.
- **Theta:** approximation algorithms, SDP, graph products, coding theory $\displaystyle\text{graph geometry}\to\text{independence bounds}\to\text{coding bounds}$, Shannon capacity.

Applications: scheduling $\left(\text{conflict graph, }\chi\text{ = slots, perfect }\implies\chi=\omega\right)$, frequency assignment $\left(\text{transmitters vertices, interference edges, coloring = frequencies}\right)$, constraint satisfaction $\left(\text{local dependencies, Local Lemma}\right)$, network science, coding theory.

#### Comparing Results

| Result          | Year | Area                      | Idea                                                         |
| --------------- | ---: | ------------------------- | ------------------------------------------------------------ |
| Perfect Graph   | 1972 | Graph theory              | Perfection preserved by complement                           |
| Local Lemma     | 1975 | Probability               | Rare locally dependent bad events avoidable                  |
| Kneser          | 1978 | Topological combinatorics | Topology lower bound $\displaystyle\chi=n-2k+2$              |
| Theta           | 1979 | Optimization              | Geometry+SDP bounds $\displaystyle\omega\le\vartheta\le\chi$ |
| Algorithmic LLL | 2010 | Algorithms                | Local resampling constructs LLL objects                      |

#### Unified View and Final Perspective

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

## Stone–Tukey Theorem

The **Stone–Tukey theorem**, more commonly known through its most famous special case as the **Ham Sandwich Theorem**, is a fundamental result connecting **geometry, measure theory, topology, and computational geometry**.

> If you have $\displaystyle d$ measurable distributions in $\displaystyle d$-dimensional space, then there is always a single $\displaystyle (d-1)$-dimensional hyperplane that divides all $\displaystyle d$ distributions exactly in half.

The word "distribution" is important. The things being divided do not have to be physical objects such as bread, cheese, or ham. They can represent:

- physical volume, mass, density
- probability, population
- collections of points, or other mathematically defined measures.

The famous three-dimensional version: any three suitable objects in $\displaystyle\mathbb{R}^{3}$ can be simultaneously bisected by one plane. Ham and two breads floating independently in space — one plane divides volume of ham exactly half, and each bread half. Objects can have completely different shapes, can overlap, do not need same center.

### History

Not simply "Stone and Tukey invented".

$$\displaystyle\boxed{\text{Steinhaus}\to\text{Banach and 3D problem}\to\text{topological formulation}\to\text{Stone–Tukey generalization}}$$

- **1930s Lwów, Scottish Book:** Hugo Steinhaus posed whether three measurable sets in $\displaystyle\mathbb{R}^{3}$ always simultaneously bisected by plane. Informal: piece ham under meat cutter to cut components equal halves.
- **1938:** Solution _A Note on the Ham Sandwich Theorem_ associated with Stefan Banach, using topological ideas underlying Borsuk–Ulam.
- **1942:** Arthur H. Stone and John W. Tukey _Generalized "Sandwich" Theorems_, Duke Math J. 9, 356–359. Major contribution broader measure-theoretic formulation to $\displaystyle d$ measures in $\displaystyle\mathbb{R}^{d}$.

Hence two names:

$$\displaystyle\boxed{\text{Ham Sandwich}\approx\text{Stone–Tukey}}$$

Ham Sandwich = geometric statement, Stone–Tukey = generalized measure formulation.

### The Basic Idea

For one object easy: disk in plane, line through center divides area equal.

For two objects more interesting: large circle left, small irregular shape right. Line bisecting first may not bisect second.

> Is there always some line that divides both exactly in half?

In $\displaystyle\mathbb{R}^{2}$ answer yes.

In $\displaystyle\mathbb{R}^{3}$:

> Given three objects in space, is there always one plane that simultaneously divides all three into equal halves?

Answer yes.

Stone–Tukey says phenomenon continues in arbitrary dimension: $\displaystyle d$ measures in $\displaystyle\mathbb{R}^{d}$ $\to$ one hyperplane.

### The General Mathematical Statement

Let

$$\displaystyle \mu_{1},\mu_{2},\ldots,\mu_{d}$$

be $\displaystyle d$ finite, suitably non-atomic measures on $\displaystyle\mathbb{R}^{d}$.

Then exists affine hyperplane

$$\displaystyle H\subset\mathbb{R}^{d}$$

such that

$$\displaystyle \mu_{i}(H^{+})=\mu_{i}(H^{-})$$

for every $\displaystyle i=1,\dots,d$, where $\displaystyle H^{+},H^{-}$ are two closed half-spaces determined by $\displaystyle H$.

If $\displaystyle\mu_{i}(\mathbb{R}^{d})<\infty$,

$$\displaystyle\boxed{\mu_{i}(H^{+})=\mu_{i}(H^{-})=\dfrac12\mu_{i}(\mathbb{R}^{d})}$$

for every $\displaystyle i$.

$$\displaystyle\boxed{\exists H\subset\mathbb{R}^{d}\text{ such that }\forall i\in\{1,\dots,d\},\;\mu_{i}(H^{+})=\mu_{i}(H^{-})}$$

### What Is a Measure?

Measure assigns quantity to sets:

$$
\begin{align*}
\text{Length:}&\;\mu([0,5])=5\\[5pt]
\text{Area:}&\;\mu(D)=\pi r^{2}\\[5pt]
\text{Volume:}&\;\mu(A)=\operatorname{Vol}(A)\\[5pt]
\text{Mass:}&\;\mu(A)=\int_{A}\rho(x)\,dx,\;\rho\text{ density}\\[5pt]
\text{Probability:}&\;\mu(A)=P(X\in A),\;P(X\in H^{+})=P(X\in H^{-})=\dfrac12\text{ if bisects}
\end{align*}
$$

So theorem bisects mass even with non-uniform density, and bisects probability distributions.

### What Is a Hyperplane?

Higher-dimensional generalization of line and plane:

$$
\begin{array}{c|c|c}
\text{Space}&\text{Bisecting object}&\text{Dimension}\\[3pt]\hline\\[-5pt]
\mathbb{R}^{1}&\text{point}&0\\[3pt]
\mathbb{R}^{2}&\text{line}&1\\[3pt]
\mathbb{R}^{3}&\text{plane}&2\\[3pt]
\mathbb{R}^{4}&\text{hyperplane}&3\\[3pt]
\mathbb{R}^{d}&\text{hyperplane}&d-1
\end{array}
$$

$$\displaystyle H=\{x\in\mathbb{R}^{d}:a\cdot x=b\},\quad a\neq0\text{ normal},\;b\in\mathbb{R}\text{ position}$$

$$\displaystyle H^{+}=\{x:a\cdot x\ge b\},\quad H^{-}=\{x:a\cdot x\le b\}$$

### Low-Dimensional Versions

**$\displaystyle d=1$:** Hyperplane is point. Finite mass distribution on line has median $\displaystyle c$:

$$\displaystyle\mu((-\infty,c])=\mu([c,\infty))=\dfrac12\mu(\mathbb{R})$$

**$\displaystyle d=2$:** Any two suitable measures in plane simultaneously bisected by one line:

$$
\begin{align*}
\operatorname{Area}(A\cap L^{+})&=\operatorname{Area}(A\cap L^{-})\\[5pt]
\operatorname{Area}(B\cap L^{+})&=\operatorname{Area}(B\cap L^{-})
\end{align*}
$$

Same line satisfies both — surprising because shapes unrelated.

**$\displaystyle d=3$ Ham Sandwich:** Three measures $\displaystyle\mu_{1},\mu_{2},\mu_{3}$ in $\displaystyle\mathbb{R}^{3}$:

$$
\begin{align*}
\mu_{1}(H^{+})&=\mu_{1}(H^{-})=\dfrac12\mu_{1}(\mathbb{R}^{3})\\[10pt]
\mu_{2}(H^{+})&=\mu_{2}(H^{-})=\dfrac12\mu_{2}(\mathbb{R}^{3})\\[10pt]
\mu_{3}(H^{+})&=\mu_{3}(H^{-})=\dfrac12\mu_{3}(\mathbb{R}^{3})
\end{align*}
$$

One plane divides ham, bread, cheese volume half.

### Crucial Points: Disconnected and Overlapping

- **Disconnected allowed:** $\displaystyle A=A_{1}\cup\cdots\cup A_{1000}$ scattered pieces, $\displaystyle\mu(A)=\sum\mu(A_{i})$ if disjoint. Theorem only cares total measure:

$$\displaystyle\mu(A\cap H^{+})=\mu(A\cap H^{-})=\dfrac12\mu(A)$$

- **Overlapping allowed:** $\displaystyle A\cap B\neq\emptyset$ fine, region can belong to both measures. Theorem concerns measures separately, not physical cutting. So $\displaystyle\mu_{1}(H^{+})=\dfrac12\mu_{1}$ and $\displaystyle\mu_{2}(H^{+})=\dfrac12\mu_{2}$ can hold even if supports overlap extensively.

### Connection to Borsuk–Ulam — The Engine

Borsuk–Ulam:

$$\displaystyle f:S^{d}\to\mathbb{R}^{d}\text{ continuous}\implies\exists x:f(x)=f(-x)$$

Antipodal $\displaystyle x,-x$.

**Encoding hyperplane:** $\displaystyle H(u,t)=\{x:u\cdot x=t\}$, $\displaystyle\|u\|=1$ direction normal, $\displaystyle t$ position. Half-space $\displaystyle u\cdot x\ge t$ positive side. Changing $\displaystyle u\to -u$ reverses sides — antipodal relevance.

**Constructing Ham Sandwich function:** Have $\displaystyle d$ measures $\displaystyle\mu_{1},\dots,\mu_{d}$. For each direction $\displaystyle u$, choose hyperplane $\displaystyle H_{u}$ that bisects $\displaystyle\mu_{1}$ $\left(\text{exists by IVT sliding }t\right)$. Define imbalance

$$\displaystyle f_{i}(u)=\mu_{i}(H_{u}^{+})-\mu_{i}(H_{u}^{-}),\qquad f(u)=\begin{pmatrix}f_{1}(u)\\\vdots\\f_{d}(u)\end{pmatrix}$$

$\displaystyle f_{i}(u)>0$ more on positive side, $\displaystyle<0$ too little, $\displaystyle=0$ perfect bisection. Since $\displaystyle H_{-u}$ same geometric hyperplane reversed,

$$\displaystyle f_{i}(-u)=-f_{i}(u)\implies\boxed{f(-u)=-f(u)}$$

odd map. Under continuity assumptions $\displaystyle f:S^{d}\to\mathbb{R}^{d}$ continuous. Borsuk–Ulam gives $\displaystyle u^{*}$ with $\displaystyle f(u^{*})=f(-u^{*})$. But $\displaystyle f(-u^{*})=-f(u^{*})$, so

$$\displaystyle f(u^{*})=-f(u^{*})\implies2f(u^{*})=0\implies\boxed{f(u^{*})=0}$$

Thus

$$\displaystyle f_{1}(u^{*})=\cdots=f_{d}(u^{*})=0\implies\mu_{i}(H^{+})=\mu_{i}(H^{-})\;\forall i$$

Common bisecting hyperplane exists.

**Why continuity matters:** Moving plane slowly through continuously distributed mass changes amount gradually from $0$ to $\displaystyle\mu(\mathbb{R}^{d})$. Needs intermediate value to hit $\displaystyle\dfrac12$. If jump $40\%\to60\%$ without $50\%$, reasoning fails. For regular volumes hyperplane has zero volume, overlap $\displaystyle H^{+}\cap H^{-}=H$ measure zero, so

$$\displaystyle\text{positive}+\text{negative}=\text{whole}$$

clean. Need non-atomic: hyperplanes measure zero.

**Point masses care:** Five points cannot have $\displaystyle2.5$ each side with line avoiding points. Discrete version uses closed half-spaces:

$$\displaystyle |P_{i}\cap H^{+}|\ge\left\lceil\dfrac{|P_{i}|}{2}\right\rceil$$

allowing points on hyperplane count both sides. So

$$\displaystyle\boxed{\text{continuous bisection}\neq\text{literal equal counting of indivisible points}}$$

but closely related.

### Concrete Two-Dimensional Example

Disks $\displaystyle D_{1},D_{2}$. For direction $\displaystyle\theta$, choose line perpendicular to $\theta$ bisecting $\displaystyle D_{1}$. Family continuous. Imbalance of second:

$$\displaystyle g(\theta)=\operatorname{Area}(D_{2}\cap H_{\theta}^{+})-\operatorname{Area}(D_{2}\cap H_{\theta}^{-})$$

Rotating $180^{\circ}$ reverses sides:

$$\displaystyle g(\theta+\pi)=-g(\theta)$$

Continuous $\implies\exists\theta^{*}:g(\theta^{*})=0$. So $\displaystyle H_{\theta^{*}}$ bisects both. This is 2D shadow of full theorem.

Three-dimensional: $\displaystyle\mu_{\text{ham}},\mu_{\text{bread1}},\mu_{\text{bread2}}$, choose $\displaystyle H_{u}$ bisecting ham for each $\displaystyle u\in S^{2}$,

$$\displaystyle f(u)=\begin{pmatrix}\mu_{\text{bread1}}(H_{u}^{+})-\mu_{\text{bread1}}(H_{u}^{-})\\[5pt] \mu_{\text{bread2}}(H_{u}^{+})-\mu_{\text{bread2}}(H_{u}^{-})\end{pmatrix}:S^{2}\to\mathbb{R}^{2}$$

Borsuk–Ulam forces $\displaystyle f(u)=0$, bisects all three.

### Dimension-Matching Principle

$$\displaystyle\boxed{\text{number of measures}=\text{dimension of space}}$$

$$
\begin{align*}
\mathbb{R}^{2}&:2\text{ measures}\to1\text{ line}\\[5pt]
\mathbb{R}^{3}&:3\text{ measures}\to1\text{ plane}\\[5pt]
\mathbb{R}^{d}&:d\text{ measures}\to1\text{ hyperplane }(d-1\text{-dim})
\end{align*}
$$

$$\displaystyle d\text{ measures in }\mathbb{R}^{d}\implies(d-1)\text{-dim bisecting hyperplane}$$

Does NOT generally guarantee $\displaystyle d+1$ measures bisected by one hyperplane in $\displaystyle\mathbb{R}^{d}$. Fundamental limitation.

Surprising because infinite hyperplanes exist, can rotate, translate, tilt — theorem guarantees at least one satisfying $\displaystyle d$ equations simultaneously.

### What Theorem Does Not Say

$$\displaystyle\boxed{\text{Exists bisecting hyperplane}}$$

Not:

- unique — many may exist if symmetric
- passes through centers
- objects must be convex, disjoint
- easy algorithm to find
- $\displaystyle d+1$ measures in $\displaystyle\mathbb{R}^{d}$ always bisected

### From Existence to Algorithms — Computational Geometry

Difference:

$$\displaystyle\boxed{\text{Does cut exist?}}\quad\text{vs}\quad\boxed{\text{Can we find efficiently?}}$$

Stone–Tukey answers first, computational geometry second.

Discrete version: point sets $\displaystyle P_{1},\dots,P_{d}\subset\mathbb{R}^{d}$, seek bisecting hyperplane.

- $\displaystyle d=1$: median.
- $\displaystyle d=2$: line bisecting two planar sets — Lo and Steiger optimal $\displaystyle O(n)$ time $\displaystyle n$ total points — linear.
- Fixed $\displaystyle d>2$: polynomial algorithms exist but exponent grows. Lo, Matoušek, Steiger bounds $\displaystyle O(n^{d-1-\alpha(d)})$, $\displaystyle\alpha(d)>0$ decreasing.
- Under separation assumptions, linear-time also possible in 3D.

**Curse of dimensionality:** $\displaystyle d=2$ few degrees freedom, $\displaystyle d=100$ many parameters, brute-force search impractical. $\displaystyle\text{difficulty}\uparrow$ as $\displaystyle d\uparrow$.

**PPA-completeness:** Discrete/high-dimensional Ham Sandwich search problems PPA-complete — Polynomial Parity Argument. Existence follows from parity argument, same class as Borsuk–Ulam, Nash equilibrium. Means:

$$\displaystyle\boxed{\text{Solution guaranteed mathematically, finding can still be hard}}$$

PPA-complete not proven exponential, but as hard as every PPA problem; polynomial algorithm would imply major collapse.

**$\displaystyle\alpha$-Ham Sandwich:** Instead $\displaystyle\dfrac12$, prescribe fractions $\displaystyle\alpha_{1},\dots,\alpha_{d}$, e.g. $20\%,40\%,70\%$. Much more restrictive. For convex well-separated inputs, unique solution exists. Unique-solution variants lie in $\displaystyle\mathrm{UEOPL}$ = Unique End of Potential Line — structured search class. Shows unique geometric solution $\implies$ special search structure.

Approximate version for numerics: allow error $\displaystyle\varepsilon$:

$$\displaystyle\left|\mu_{i}(H^{+})-\dfrac12\mu_{i}(\mathbb{R}^{d})\right|\le\varepsilon$$

Real computers finite precision.

### Modern Generalizations and Uses

**Generalizations:** more than two equal parts, several measures partitioned simultaneously, lower-dimensional bisecting object $\left(\text{center transversal theorem}\right)$, prescribed unequal fractions $\displaystyle\alpha$-problem, noisy data, manifolds, oriented matroids.

**Uses:**

- Computational geometry — balanced spatial partition $\displaystyle P\to P_{1}\cup P_{2}$ recursively for searching, nearest-neighbor, range searching, collision detection, clustering.
- Data partitioning — homes, businesses, schools balanced simultaneously: $\displaystyle\boxed{\text{one partition can balance multiple datasets at once}}$
- Statistics — multivariate median-like partitions, probability $\displaystyle\mu_{i}(H^{+})=\mu_{i}(H^{-})=\dfrac12$, foundation for Tukey depth $\displaystyle\text{how deeply buried point inside distribution}$, centerpoint theorem $\displaystyle\text{find central point}$ vs $\displaystyle\text{find common balancing hyperplane}$: $\displaystyle\boxed{\text{Ham Sandwich}\leftrightarrow\text{centerpoints}\leftrightarrow\text{Tukey depth}}$
- Fair division — resources $\displaystyle\mu_{1}$ amount resource 1 etc., common hyperplane divides every resource equal halves: $\displaystyle\boxed{\text{different quantities can sometimes be divided equally by same cut}}$
- Image processing, scientific data — density $\displaystyle\rho(x,y,z)$, mass $\displaystyle M=\iiint\rho\,dV$, plane divides mass $\displaystyle\dfrac{M}{2}$, Stone–Tukey asks same plane balances several quantities.

### Summary of Structure

Chain:

$$\displaystyle\boxed{\text{Objects}\to\text{Measures}\to\text{Hyperplanes}\to\text{Continuous imbalance}\to\text{Topological theorem}\to\text{Perfect balance}}$$

Explicitly:

$$
\begin{align*}
\text{physical objects}&\to\text{mathematical measures}\\[5pt]
\text{possible cuts}&\to\text{points/directions on sphere }S^{d}\\[5pt]
\text{cut quality}&\to f:S^{d}\to\mathbb{R}^{d},\;f_{i}=\mu_{i}^{+}-\mu_{i}^{-}\\[5pt]
\text{antipodal symmetry}&\to f(-u)=-f(u)\\[5pt]
\text{Borsuk–Ulam}&\to f(u^{*})=f(-u^{*})\implies f(u^{*})=0\\[5pt]
\text{topological zero}&\to\mu_{i}(H^{+})=\mu_{i}(H^{-})\;\forall i
\end{align*}
$$

Deep idea:

$$\displaystyle\boxed{\text{continuous antipodal symmetry forces a balancing point}}$$

$$\displaystyle\boxed{\text{Borsuk–Ulam}\implies\text{Ham Sandwich}\implies\text{Stone–Tukey generalization}}$$

Comparison IVT: IVT one dimension one zero, Borsuk–Ulam higher-dimensional sphere forced coincidence/zero.

Computational summary:

$$
\begin{array}{c|c|c}
d&\text{Problem}&\text{Algorithmic}\\[3pt]\hline\\[-5pt]
1&\text{bisect 1 measure point}&\text{median}\\[5pt]
2&\text{2 sets line}&O(n)\text{ optimal}\\[5pt]
3&\text{3 sets plane}&\text{polynomial, linear if separated}\\[5pt]
\text{fixed }>3&\text{d sets hyperplane}&\text{polynomial but expensive in }d\\[5pt]
\text{high-dim discrete}&\text{find bisecting}&\text{some PPA-complete}\\[5pt]
\alpha\text{-version}&\text{prescribed fractions}&\text{unique variants in UEOPL}
\end{array}
$$

One sentence:

$$\displaystyle\boxed{\forall\mu_{1},\dots,\mu_{d}\;\exists H\;\forall i,\;\mu_{i}(H^{+})=\mu_{i}(H^{-})=\dfrac12\mu_{i}(\mathbb{R}^{d})}$$

$$\displaystyle d\text{ measures in }\mathbb{R}^{d}\implies\exists\text{ one }(d-1)\text{-dim hyperplane bisecting all}$$

Enduring importance: existence guaranteed by topology $\displaystyle\text{Measure}\leftrightarrow\text{Geometry}\leftrightarrow\text{Topology}\leftrightarrow\text{Combinatorics}\leftrightarrow\text{Algorithms}\leftrightarrow\text{Complexity}$, while finding cut remains deep computational problem — classical existence generating new mathematics decades later.

Historical references: Stone–Tukey Duke Math J. 9 (1942) 356–359; Steinhaus 1938; Beyer–Zardecki Early History Amer Math Monthly 2004; Lo–Matoušek–Steiger Algorithms for Ham-Sandwich Cuts; Matoušek Using Borsuk–Ulam; Filos-Ratsikas–Goldberg PPA-completeness; Chiu–Choudhary–Mulzer $\displaystyle\alpha$-Ham Sandwich complexity.
