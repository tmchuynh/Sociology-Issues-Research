


## Graph Theory — Mathematics of Connections

In mathematics, a "graph" is not a plot or chart — not $y=x^2$; rather, it is a collection of points, known as vertices or nodes, connected by lines called edges — abstract model of pairwise relations. Graph theory examines how these points are linked, how one can navigate through networks, and what patterns or structures may arise. It represents mathematics of connections and networks and is applicable in many aspects of daily life and technology, including social media, transportation, biology, and project management. By utilizing graph theory, we can better understand and optimize various webs of relationships that connect the world.

Formally, a graph $G=(V,E)$ where $V$ finite set of vertices, $E\subseteq V\times V$ — or $\binom{V}{2}$ for undirected — set of edges — each edge is unordered pair $\{u,v\}$ — undirected — or ordered $(u,v)$ — directed digraph. Loops — $\{v,v\}$ — and multiple edges — multigraph — allowed depending on context.

### Historical Origin — Königsberg to Today

Founded 1736 by Leonhard Euler solving Königsberg bridge problem: can you walk through city crossing each of seven bridges exactly once and return? Euler modeled landmasses as vertices $A,B,C,D$ and bridges as edges, proved impossible — Euler trail exists iff zero or two vertices have odd degree — because entering and leaving uses two edges, odd degree forces start/end. This introduced abstraction: ignore geometry, keep connectivity — birth of topology and graph theory.

Later: Kirchhoff 1847 — electrical networks — spanning trees; Cayley 1857 — counting trees for chemistry — isomers; Four Color Theorem — 1852 Guthrie, proved 1976 Appel-Haken — every planar map colorable with 4 colors — first major computer-assisted proof. Erdős–Rényi 1959 — random graphs $G(n,p)$ — probabilistic method.

### Core Definitions — Vocabulary of Networks

- **Vertex, Edge, Degree:** Degree $d(v)$ = number of edges incident to $v$. Handshaking Lemma: $\sum_{v\in V} d(v)=2|E|$ — sum of degrees even — number of odd-degree vertices even — parity invariant used in Euler proof.

- **Path, Cycle, Walk:** Walk = sequence $v_0 e_1 v_1\dots e_k v_k$ where $e_i=\{v_{i-1},v_i\}$. Trail = no repeated edges. Path = no repeated vertices — Hamiltonian path if visits all vertices exactly once — as in earlier section — NP-complete to find. Cycle = closed path $v_0=v_k$, length $\ge3$. Simple cycle — Hamiltonian cycle — visits all vertices.

- **Connectedness:** Graph connected if for all $u,v$ exists path $u\to v$. Connected components = maximal connected subgraphs. For digraphs: strongly connected if directed path both ways, weakly if underlying undirected connected.

- **Subgraph, Induced Subgraph:** $H\subseteq G$ if $V(H)\subseteq V(G)$, $E(H)\subseteq E(G)$. Induced $G$ = keep all edges among $S\subseteq V$.[S]

- **Isomorphism:** Two graphs same up to renaming vertices — bijection $f:V(G)\to V(H)$ with $\{u,v\}\in E(G)\iff\{f(u),f(v)\}\in E(H)$ — structure same, drawing different — graph isomorphism problem — not known P nor NP-complete — Babai quasi-polynomial.

- **Types:**
  - Complete graph $K_n$ — all $\binom{n}{2}$ edges.
  - Bipartite — $V=X\sqcup Y$, edges only between $X$ and $Y$ — no edges inside part — e.g., chessboard black-white — no odd cycle — characterization: graph bipartite iff no odd cycle.
  - Tree — connected acyclic — $n$ vertices, $n-1$ edges — unique path between any two vertices — e.g., family tree, spanning tree.
  - Planar — can draw in plane without crossing edges — Kuratowski theorem: planar iff no $K_5$ or $K_{3,3}$ minor.
  - Directed, weighted — edges have direction or cost $w:E\to\mathbb{R}$ — models flights with distances.

### Fundamental Theorems and Concepts

- **Eulerian Trails vs Hamiltonian Paths:** Eulerian trail visits every _edge_ exactly once — characterization easy — $O(E)$: connected and 0 or 2 odd degree for undirected, balanced indegree=outdegree for directed. Hamiltonian visits every _vertex_ — no simple characterization — NP-complete. Confusingly similar names, wildly different complexity — illustrates P vs NP.

- **Trees and Spanning Trees:** Every connected graph has spanning tree — contains all vertices, minimal connected — can find via BFS/DFS. Number of spanning trees given by Kirchhoff's Matrix-Tree Theorem: $\tau(G)=\det(L^*)$ where $L=D-A$ Laplacian minor. Cayley's formula: $K_n$ has $n^{n-2}$ spanning trees. Minimum spanning tree — cheapest to connect all vertices — Kruskal, Prim $O(E\log V)$.

- **Coloring:** Chromatic number $\chi(G)$ = minimum colors needed to color vertices so adjacent vertices different — e.g., map coloring. Bipartite iff $\chi\le2$. Brooks' Theorem: $\chi\le\Delta$ unless $G$ is clique or odd cycle. Four Color Theorem: planar $\chi\le4$. Applications: scheduling — exams as vertices, edge if share student, color = time slot.

- **Matching:** Set of edges with no shared vertices — pairing. Matching in bipartite graph corresponds to assignment — Hall's Marriage Theorem: bipartite $X-Y$ has matching covering $X$ iff for all $S\subseteq X$, $|N(S)|\ge|S|$ — neighbor set large enough — proves Gomory tiling: black squares $X$, white $Y$, domino edge if adjacent — Hall condition holds when opposite colors removed? Actually Hamiltonian cycle provides perfect matching. Domino tiling = perfect matching in grid graph.

- **Connectivity and Menger:** Vertex connectivity $\kappa(G)$ = min vertices to delete to disconnect. Edge connectivity $\lambda(G)$. Menger's Theorem: max number of disjoint $u$-$v$ paths = min $u$-$v$ cut — max-flow min-cut duality. For chessboard Hamiltonian cycle, removing 1 vertex leaves Hamiltonian path — still connected — but removing 2 opposite colors disconnects parity.

- **Planarity and Duality:** Euler formula for planar connected: $V-E+F=2$ — vertices minus edges plus faces =2. Implies $E\le3V-6$ for $V\ge3$, average degree <6, so planar graph has vertex degree ≤5 — used in 5-color proof.

### Why Graph Theory Everywhere

- **Social Media:** People = vertices, friendship = edges — social graph — Facebook. Centrality measures — degree, betweenness, PageRank — who influential. Community detection — clustering — find groups. Small world — six degrees — Milgram 1967, Watts-Strogatz — diameter $O(\log n)$.

- **Transportation:** Intersections = vertices, roads = weighted edges — shortest path Dijkstra $O(E\log V)$ — GPS. Eulerian trail = snowplow route covering every street. Hamiltonian = traveling salesman visiting every city — TSP NP-hard.

- **Biology:** Protein interaction network, neural network — vertices neurons, edges synapses — brain connectome. Phylogenetic trees.

- **Project Management:** Tasks = vertices, dependency = directed edge — DAG — topological sort orders tasks, critical path longest path.

- **Computer Science:** Internet = graph, web = directed graph — PageRank = stationary distribution of random walk on web graph — eigenvector centrality — $\pi=\pi P$. Compilation — register allocation = graph coloring of interference graph.

### Relation to Earlier Sections

Chessboard graph — vertices squares, edges orthogonal adjacency — is bipartite, Hamiltonian, planar — its Hamiltonian cycle gave alternating-color loop for Gomory proof — existence of perfect matching after opposite-color removal. More generally, any grid graph with at least one even side Hamiltonian — snake construction — provides Hamiltonian cycle for tiling proofs. Random walk on chessboard — Markov chain — state space 64, transition to 4 neighbors — stationary uniform, ergodic, mixing time $O(n^2)$. Queueing network — e.g., Jackson network — is graph of queues — product-form stationary.

Graph theory thus unifies tiling puzzles, stochastic processes, and ergodicity: tiling = perfect matching in bipartite graph; Markov chain = random walk on directed weighted graph; ergodic = walk explores whole graph — irreducibility = graph strongly connected.

In short: graph is abstraction of relation — $G=(V,E)$ — study of how local adjacency determines global structure — existence of Euler trails, Hamiltonian cycles, colorings, matchings — tools to model any system of connections, from Königsberg bridges to Facebook friendships to chessboard dominoes.


## Combinatorics — Art of Counting

Key concepts in combinatorics include factorials, graph theory, and principle of inclusion-exclusion. This field has significant applications in computer science, cryptography, probability, statistical physics. Combinatorics addresses questions such as "How many ways can I choose or arrange these items?" It involves discovering all possible patterns, groupings, or orders that can be created from given set of objects. Unlike analysis which studies continuum, combinatorics studies discrete finite structures — counting, existence, optimization.

Root intuition: if you can list, you can count — but listing is huge — need formulas.

### Basic Concepts and Formulas

Two fundamental counting principles:

- **Rule of Sum:** If one task can be done in $n$ ways and another in $m$ ways, and they cannot be done together — disjoint — there are $n+m$ ways — partition of possibilities.
- **Rule of Product:** If one task can be done in $n$ ways and second independent task in $m$ ways, there are $n\times m$ ways — Cartesian product.

All else derived from these plus bijections — one-to-one correspondences.

#### Permutations — Order Matters

Number of ways to order $n$ distinct objects, denoted $n! = n\times(n-1)\times\dots\times1$ — factorial — grows superexponential — Stirling $n!\sim\sqrt{2\pi n}(n/e)^n$.

Proof: $n$ choices for first position, $n-1$ for second, etc. — product rule. Example: 52! deck arrangements = $8.06\times10^{67}$ as before.

Partial permutations: $P(n,r)=n!/(n-r)!$ — number of ways to choose and order $r$ from $n$ — first $r$ positions.

Permutations with repetition: If items not distinct — e.g., word MISSISSIPPI with 1 M, 4 I, 4 S, 2 P — $11!/(4!4!2!1!)$.

#### Combinations — Order Does Not Matter

Number of ways to choose $r$ objects from set of $n$ without regard to order, calculated as
$$\binom{n}{r} = \dfrac{n!}{r!(n-r)!}$$
— binomial coefficient — choose $r$. How many ways to choose subset from larger set — like picking committee from group?

Derivation: permutations $P(n,r)=n!/(n-r)!$ overcount by $r!$ — each subset ordered $r!$ ways — divide.

Properties: symmetry $\binom{n}{r}=\binom{n}{n-r}$, Pascal recurrence $\binom{n}{r}=\binom{n-1}{r-1}+\binom{n-1}{r}$, Binomial theorem $(x+y)^n=\sum\binom{n}{r}x^r y^{n-r}$.

Example: choose 3 from 10: $\binom{10}{3}=120$.

Stars and bars — combinations with repetition: number ways to choose $r$ items from $n$ types with unlimited repetition — e.g., $r$ scoops from $n$ flavors — $\binom{n+r-1}{r}$ — identical items into distinct boxes.

### Types of Combinatorics — Map of Field

- **Enumerative Combinatorics:** Counting number of elements in finite sets — classic — how many? Uses bijections, generating functions, recurrence. Example: number of domino tilings of $8\times8$ board = 12,988,816.

- **Extremal Combinatorics:** Determining maximum or minimum size of collection of finite structures that satisfy certain properties — how large can family be without containing forbidden pattern? Turán's theorem — max edges in graph without $K_r$. Erdős–Ko–Rado.

- **Algebraic Combinatorics:** Using algebraic methods — groups, rings, representation theory — to solve combinatorial problems — e.g., counting via characters, symmetric functions.

- **Probabilistic Combinatorics:** Using probability theory to prove existence of specific configurations — Erdős' method: show random object satisfies property with positive probability → existence. E.g., existence of graphs with high girth and chromatic number.

- **Graph Theory:** Study of graphs — mathematical structures used to model pairwise relations — vertices and edges — central to combinatorics — matching, coloring, connectivity — as expanded earlier.

### Partitions — Breaking Into Unordered Pieces

Methods of breaking down integers or sets — order irrelevant.

**Types:**

- **Integer Partitions:** Partition function $p(n)$ represents number of ways to write integer $n$ as sum of positive integers, order irrelevant. Number of partitions of 4 is 5: (4), (3+1), (2+2), (2+1+1), (1+1+1+1). Note (3+1) same as (1+3) — compositions distinguish them. $p(n)$ grows fast: $p(10)=42$, $p(100)=190,569,292$, $p(1000)\approx2.4\times10^{31}$ — Hardy-Ramanujan asymptotic $p(n)\sim \dfrac{1}{4n\sqrt3}\exp(\pi\sqrt{2n/3})$.

- **Set Partitions:** Partition of set $A$ is collection of disjoint non-empty subsets — blocks — whose union equals original set — equivalence relation. Number of ways to partition set with $n$ elements is Bell number $B_n$ — $B_3=5$, $B_4=15$, $B_5=52$ — $B_n=\sum_{k=0}^n S(n,k)$. For complex set partitions, number of ways to partition $k$ distinct elements into $n$ subsets described by Stirling number of second kind, denoted $S(k,n)$ or $\left\{ {k \atop n} \right\}$ — counts set partitions into $n$ blocks.

**Representations:**

- **Ferrers/Young Diagrams:** Visual representations using dots or squares to represent integer partitions — rows nonincreasing — e.g., partition 4+3+1 of 8 as 4 boxes first row, 3 second, 1 third — left-aligned.
- **Conjugate Partitions:** Obtained by reflecting Ferrers diagram along diagonal — transpose — e.g., conjugate of (4,3,1) is (3,2,2,1) — number parts = largest part of original — involution — proves partitions into at most $k$ parts equals partitions with largest part ≤ $k$.

**Special Partition Types:**

- **Distinct Parts:** Partitions where each integer used at most once — e.g., 4=3+1 — $q(n)$.
- **Odd Parts:** Partitions where each part odd — Euler's theorem: number partitions into distinct parts = number partitions into odd parts — bijection via binary expansion.

**Counting Methods:**

- **Generating Functions:** Used to calculate $p(n)$ using power series — Euler's generating function $\sum p(n)x^n = \prod_{k\ge1}1/(1-x^k)$. Pentagonal number theorem gives recurrence $p(n)=\sum_{k\neq0}(-1)^{k+1}p(n-k(3k-1)/2)$.
- **Recurrence Relations:** Used for computing $p(n,k)$ — partitions of $n$ with $k$ parts — $p(n,k)=p(n-1,k-1)+p(n-k,k)$.

### Compositions — Order Matters

Composition of integer $n$ is ordered arrangement of positive integers sum to $n$. Example compositions of 4: (4), (3+1), (1+3), (2+2), (2+1+1), (1+2+1), (1+1+2), (1+1+1+1) — 8 = $2^{3}$. Number of compositions of $n$ is $2^{n-1}$ — each of $n-1$ gaps between $n$ dots can be cut or not — binary choice.

**Types:**

- **Ordered Compositions:** Order matters — $(2+1)$ different from $(1+2)$ — that's definition of composition.
- **Unordered Compositions:** Order does not matter — i.e., partitions — terminology sometimes confused.

More refined types with constraints:

- Compositions with Distinct Parts
- Compositions with Odd Parts
- Compositions with Bounded Parts — each part within range $$[a][b]
- Compositions with Fixed Number of Parts — $k$ parts — number $\binom{n-1}{k-1}$ — stars and bars: choose $k-1$ cuts among $n-1$.
- Compositions with Fixed Largest Part, Smallest Part, Sum, Product, Difference.

**Representations:**

- **Binary Representation:** Each composition can be represented as binary string length $n-1$, where 1 indicates break between parts — bijection proves $2^{n-1}$ count.
- **Generating Functions:** $\sum c(n)x^n = 1/(1-\sum_{allowed} x^k)$
- **Recurrence Relations:** $c(n)=c(n-1)+c(n-2)+\dots$ depending on allowed parts.

**Counting Methods:** Generating functions, recurrence, inclusion-exclusion to enforce constraints — e.g., count compositions with no part 1 via inclusion-exclusion.

### Key Difference: Partitions vs Compositions

- Partitions: Order does not matter — $2+1$ same as $1+2$ — equivalence under permutation — fewer.
- Compositions: Order matters — $2+1$ different from $1+2$ — more — exactly $2^{n-1}$ vs $p(n)$ subexponential.

### Common Techniques — Toolbox

- **Recurrence Relations:** Defining sequence based on rule relating terms to earlier terms — e.g., Bell numbers $B_{n+1}=\sum_{k=0}^n \binom{n}{k}B_k$, Stirling $S(n,k)=k S(n-1,k)+S(n-1,k-1)$.

- **Generating Functions:** Using power series to solve counting problems — ordinary generating function $A(x)=\sum a_n x^n$, exponential $ \hat A(x)=\sum a_n x^n/n!$ for labelled structures — product = combinatorial product. For partitions: $\prod 1/(1-x^k)$.

- **Inclusion-Exclusion Principle:** Technique to compute size of union of multiple sets — $|A_1\cup\dots\cup A_n|=\sum|A_i|-\sum|A_i\cap A_j|+\dots$ — used to count onto functions, derangements — $!n = n!\sum_{k=0}^n (-1)^k/k!$ — permutations with no fixed point.

### Examples of Combinatorial Problems

#### The Twelvefold Way — Master Cheat Sheet

Systematic classification of 12 basic counting problems — Rota — like cheat sheet for figuring out how many ways to put $n$ items into $k$ boxes. 12 variations depend on three simple questions:

1. Are items distinct — labeled — or identical — unlabeled?
2. Are boxes distinct — labeled — or identical — unlabeled?
3. Restrictions on boxes? Can be empty? Must have at least one item? Or exactly one?

| Items ($n$) | Boxes ($k$) | Any number per box                                                                                                             | $\ge1$ per box — Surjective                                                        | $\le1$ per box — Injective                                                |
| ----------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Distinct    | Distinct    | $k^n$ — each item $k$ choices                                                                                                  | $k! S(n,k)$ — onto — inclusion-exclusion $k!S = \sum_{i}(-1)^i\binom{k}{i}(k-i)^n$ | $P(k,n)=k!/(k-n)!$ if $n\le k$ else 0                                     |
| Identical   | Distinct    | $\binom{n+k-1}{k-1}$ — stars and bars                                                                                          | $\binom{n-1}{k-1}$ — put 1 in each first                                           | $\binom{k}{n}$ — choose which boxes get 1                                 |
| Distinct    | Identical   | $\sum_{j\le k} S(n,j)$ — Bell partial — set partitions into ≤k blocks                                                          | Stirling $S_{n,k}$ — set partitions into exactly k blocks                          | $1$ if $n\le k$ else 0 — at most 1 per box, boxes unlabeled, only one way |
| Identical   | Identical   | Partitions $p_k(n+k)$? Actually number partitions of $n$ into ≤k parts — equals partitions into parts ≤k — generating function | Partitions $p_k(n)$ — partitions of $n$ into exactly k parts                       | $1$ if $n\le k$ else 0                                                    |

Instead of memorizing 12 formulas, identify scenario:

- Distinct items into Distinct boxes ($k^n$): Like assigning $n$ different jobs to $k$ different employees — each job chooses employee.

- Distinct items into Identical boxes — Stirling Numbers: Like grouping $n$ different students into $k$ unnamed study groups — set partition — $S(n,k)=\dfrac1{k!}\sum_{i=0}^k(-1)^{k-i}\binom{k}{i}i^n$.

- Identical items into Distinct boxes — Stars and Bars: Like distributing $n$ identical cookies to $k$ children — $n$ stars, $k-1$ bars separate.

- Identical items into Identical boxes — Partitions: Like putting $n$ plain coins into $k$ identical piggy banks — integer partition — uses partition function, no closed form — recurrence via generating function.

This framework unifies permutations $\binom{n}{n}n!=n!$ — distinct into distinct injective with $k=n$ — combinations $\binom{n}{k}$ — identical? Actually choose, etc.

Thus combinatorics provides language to count everything from deck shuffles $52!$ to domino tilings to set partitions — foundation for probability — $\text{Probability}= \dfrac{\text{favorable count}}{\text{total count}}$ when uniform — and for complexity analysis — algorithms enumeration.

and clarified version, explicitly linked to combinatorics:

#### Password Creation — Combinatorics in Action

Password strength is pure combinatorics. The size of the search space — how many strings satisfy a policy — determines entropy and crack time. Each new requirement changes the counting problem. Two tools do all the work: the **Twelvefold Way** and **Inclusion-Exclusion**.

We model the alphabet as a union of character classes:

- $L = 26$ lowercase
- $U = 26$ uppercase
- $D = 10$ digits
- $S = 32$ specials — e.g., `!@#$%` — printable ASCII without space

Total pool $94 = L+U+D+S$. Let $L$ = password length. We count fixed length first, then sum for $\ge$ min.

> **Combinatorial link:** Counting passwords = counting functions from $n=L$ distinct positions — distinct boxes — to $k$ distinct character types, with restricted counts per type. This is the Twelvefold Way: distinct balls into distinct boxes.

##### Basic — Lowercase only, min 6 characters

26 choices per slot, independent. Product Rule.

Exact length $L$:
$$N = 26^L = k^n,\; k=26$$

At least 6 up to $L_{max}$ — Rule of Sum:
$$N_{\ge 6} = \sum_{i=6}^{L_{max}} 26^i$$

For $L=6$:
$$26^6 = 308,915,776 \approx 3.1\times10^8$$

Entropy: $\log_2(26^6)=6\log_2 26 \approx 28.2$ bits. At 1k guesses/sec → ~3.5 days.

Type: $k^n$ with repetition allowed.

##### At Least One Capital — Complement Principle

"At least one" = Total $-$ Illegal. Complement is the $n=1$ case of Inclusion-Exclusion.

Pool $= 26$ lower + $26$ upper $= 52$.

- Total strings: $52^L$
- Illegal — zero capitals: $26^L$

$$N_{cap\ge1}=52^L-26^L$$

For $L=6$:
$$52^6-26^6 = 19,770,609,664 - 308,915,776 = 19,468,362,432 \approx 1.94\times10^{10}$$
~63x larger than lowercase-only.

**Summation view:** Partition by number of capitals $k=1\ldots L$.

- Choose positions: $\binom{L}{k}$
- Choose caps: $26^k$
- Choose remaining lower: $26^{L-k}$

$$\sum_{k=1}^{L} \binom{L}{k}26^k 26^{L-k} = (2^L-1)26^L$$

By Binomial Theorem $(x+y)^L=\sum\binom{L}{k}x^k y^{L-k}$ with $x=y=26$, this equals $52^L-26^L$.

Link: Enumerative combinatorics — binomial coefficient counts position subsets. Entropy $\approx 34.2$ bits for $L=6$.

##### At Least One Capital AND One Number — PIE for 2 Properties

Now subtract all illegal sets with **Principle of Inclusion-Exclusion**.

Pool $= 26+26+10 = 62$.

Let $A=$ no caps, $B=$ no digits. Want $\overline{A\cup B}$:
$$|\overline{A\cup B}| = Total -|A|-|B|+|A\cap B|$$

- $|A|$ — no caps = lower+digit = $36^L$
- $|B|$ — no digits = lower+upper = $52^L$
- $|A\cap B|$ — no caps and no digits = lower only = $26^L$

$$N_{cap\ge1,\,digit\ge1}=62^L-36^L-52^L+26^L$$

For $L=6$:
$$56,800,235,584 - 2,176,782,336 - 19,770,609,664 + 308,915,776 = 35,161,759,360 \approx 3.5\times10^{10}$$

**Multinomial summation view:** Ensure $j\ge1$ caps, $k\ge1$ digits, $j+k\le L$.

$$\sum_{j=1}^{L-1}\sum_{k=1}^{L-j} \dfrac{L!}{j!\,k!\,(L-j-k)!}\;26^{j}\,10^{k}\,26^{L-j-k}$$

Multinomial coefficient counts permutations of types. This equals the PIE closed form by the multinomial theorem.

Link: Distinct positions into 3 types with 2 types non-empty — surjective onto subset. Entropy $\approx 35.0$ bits for $L=6$.

##### At Least One Capital, One Number AND One Special — PIE for 3 Properties

Full PIE for $A=$ no caps, $B=$ no digits, $C=$ no specials.

Pool $= 94$.

$$|\overline{A\cup B\cup C}| = Total -(|A|+|B|+|C|)+(|A\cap B|+|A\cap C|+|B\cap C|)-|A\cap B\cap C|$$

- $|A|$ = no caps = lower+digit+special = $68^L$
- $|B|$ = no digits = lower+upper+special = $84^L$
- $|C|$ = no specials = lower+upper+digit = $62^L$
- $|A\cap B|$ = no caps no digits = lower+special = $58^L$
- $|A\cap C|$ = no caps no specials = lower+digit = $36^L$
- $|B\cap C|$ = no digits no specials = lower+upper = $52^L$
- $|A\cap B\cap C|$ = only lower = $26^L$

$$N = 94^L - (68^L+84^L+62^L) + (58^L+36^L+52^L) - 26^L$$

For $L=6$ with $S=32$:
$$94^6=689,869,781,056$$
$$68^6+84^6+62^6=506,965,751,104$$
$$58^6+36^6+52^6=60,016,084,544$$
$$N = 242,611,198,720 \approx 2.4\times10^{11}$$

**General summation:**
$$\sum_{c=1}^{L-2}\sum_{n=1}^{L-c-1}\sum_{s=1}^{L-c-n} \dfrac{L!}{c!\,n!\,s!\,(L-c-n-s)!}\;26^{c}\,10^{n}\,32^{s}\,26^{L-c-n-s}$$
where $c+n+s\le L$.

Link: 4-type multinomial — permutations of character types.

##### Summary

| Requirement                  | Counting Principle | Closed Form — PIE                             | $L=6$ Combinations  | Entropy   |
| :--------------------------- | :----------------- | :-------------------------------------------- | :------------------ | :-------- |
| Lowercase only               | Product Rule $k^n$ | $26^L$                                        | $3.08\times10^8$    | 28.2 bits |
| At least 1 Cap               | Complement         | $52^L-26^L$                                   | $1.94\times10^{10}$ | 34.2 bits |
| At least 1 Cap + 1 Num       | PIE — 2 sets       | $62^L-36^L-52^L+26^L$                         | $3.51\times10^{10}$ | 35.0 bits |
| At least 1 Cap +1 Num+1 Spec | PIE — 3 sets       | $94^L-(68^L+84^L+62^L)+(58^L+36^L+52^L)-26^L$ | $2.43\times10^{11}$ | 37.8 bits |

##### Why It Matters — Policy Design

1.  Adding character classes increases base $k$ — $k^L$ dominates.
2.  Requiring "at least one of each" _reduces_ space vs. unrestricted $94^L$: $94^6=689B$ vs $242B$ with 3 requirements — ~65% reduction. Policy trades slight entropy loss for avoiding weak all-lowercase passwords.
3.  **Length beats alphabet:** $26^{12}=9.5\times10^{16}$ dwarfs $94^6=6.9\times10^{11}$. Doubling length 6→12 adds ~48 bits; adding symbols adds ~10 bits.

Combinatorics proves: prioritize length.  
Passphrase `correct horse battery staple` — 4 words from 7776-word.  
Diceware list: $7776^4=3.6\times10^{15}$ combos ≈ 52 bits — stronger than 6-char complex.

Password counting = applied combinatorics: $k^L$ permutations with repetition, $\binom{L}{k}$ to choose positions, multinomial $\dfrac{L!}{j!k!\dots}$ for multiple types, and Inclusion-Exclusion to enforce "at least one" constraints — same tools that count deck shuffles and domino tilings, now quantifying security.

#### Lottery Odds — Combinatorics of Huge Sample Spaces

Lottery odds are pure enumerative combinatorics: count total equally likely outcomes, count favorable outcomes, probability = favorable / total. Because every ticket is a subset — order doesn't matter — binomial coefficients $\binom{n}{k}$ do all work, and hypergeometric distribution generalizes to partial matches.

##### Standard Jackpot Formula — $n$ Choose $k$

For a lottery where you choose $k$ numbers from a pool of $n$, with no repetition and order irrelevant, total possible combinations is Binomial Coefficient — "$n$ choose $k$":

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

- $n$: total numbers in pool — e.g., 49 or 69.
- $k$: how many you must pick — e.g., 6.
- $!$: factorial — $n! = n\times(n-1)\times\dots\times1$.

**Combinatorial link:** This is Twelvefold Way — identical balls? No — combinations — distinct pool, distinct picks, injective, order irrelevant — $P(n,k)/k!$.

Derivation: $P(n,k)=n!/(n-k)!$ ordered picks — $n$ choices first, $n-1$ second. Each unordered set counted $k!$ times — permutations of its $k$ elements — divide by $k!$.

Example 6/49 — UK Lotto, German Lotto:
$$\binom{49}{6}= \frac{49!}{6!\,43!} = \frac{49\times48\times47\times46\times45\times44}{6\times5\times4\times3\times2\times1}=13,983,816$$

So 1 ticket: $P=1/13,983,816\approx7.15\times10^{-8}$. Odds quoted as "1 in 13,983,816".

For 5/69 + 1/26 Powerball: $\binom{69}{5}\times26 = 11,238,513\times26 = 292,201,338$. Same product rule — independent choices — white balls and powerball.

Entropy: $\log_2(13,983,816)\approx23.7$ bits — less than 6-char lowercase password!

##### Odds for Arithmetic Patterns — All Outcomes Equally Likely

The math for a specific sequence such as arithmetic progression $\{2,4,6,8,10,12\}$ is identical to any other combination:

- Specific pattern counts as **1** possible outcome.
- Denominator is total combinations $\binom{n}{k}$.

Odds of hitting $\{2,4,6,8,10,12\}$ are identical to hitting $\{1,19,23,31,44,48\}$. Both **1 in 13,983,816**.

**Why humans think patterns less likely — combinatorics vs psychology:** Enumerative combinatorics says each _individual_ combination equally likely. But _classes_ of combinations have different sizes. Number of combinations that look "patterned" is tiny vs number that look "random".

Count: How many 6-number sets are arithmetic progressions in 1..49? $d=$ common difference. For $d=1$: $\{1..6\}$ to $\{44..49\}$ →44 sets. $d=2$: first ≤37 →37 sets, etc. Total $\sum_{d=1}^{8} (49-6d+1) = 44+37+30+23+16+9+2 = 161$ — actually up to $d=8$ — $49-5*8=9$ → 9? Let's compute: $d=1$ to $8$ gives 44+42? Wait formula $n-kd+1$? For 6 terms: max start $49-5d$. So sum $d=1..9$: $49-5d$ →44+39+34+29+24+19+14+9+4=216. So 216 arithmetic progressions out of 13,983,816 → probability $216/13.9M \approx 1.5\times10^{-5}$ that winning set is arithmetic progression. So _class_ "is arithmetic" is rare, but _specific_ progression is as rare as any specific random set.

This is same as deck of cards: $\{A\heartsuit,2\heartsuit,\dots\}$ straight flush vs random hand — same probability for each specific hand, but "straight flush" class small.

Combinatorial moral: Do not avoid $\{1,2,3,4,5,6\}$ because "too unlikely" — if it hits, you split prize with thousands who picked same pattern. Expected value lower due to prize sharing, not probability.

##### The Hypergeometric Distribution — Odds of Matching Some But Not All

To find odds of matching some but not all numbers — e.g., getting 3 out of 6 correct — use Hypergeometric Distribution — sampling without replacement from finite population with two types: winning vs losing numbers.

Formula:
$$P(X=k)=\frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}$$

- $N$: total pool size — 49.
- $K$: number of winning balls drawn — 6 — successes in population.
- $n$: numbers you picked — 6 — sample size.
- $k$: number of your balls that must match — $k$ successes in sample.

Explanation via counting:

- Denominator $\binom{N}{n}$: total ways to pick your ticket.
- Numerator: choose $k$ of the $K$ winning numbers $\binom{K}{k}$ — which you match — and choose remaining $n-k$ from $N-K$ losing numbers $\binom{N-K}{n-k}$ — which you miss. Product Rule.

Example — match exactly 3 in 6/49:

$$\binom{6}{3}=20,\quad \binom{43}{3}=12,341,\quad \binom{49}{6}=13,983,816$$
$$P(X=3)=\frac{20\times12,341}{13,983,816}= \frac{246,820}{13,983,816}\approx0.01765 = 1\text{ in }56.7$$

Complete distribution 6/49:

- 6/6: $\binom{6}{6}\binom{43}{0}/\binom{49}{6}=1/13,983,816$ → 1 in 13.9M
- 5/6: $6\times43/13,983,816 =258/13,983,816$ → 1 in 54,201
- 4/6: $15\times903/13,983,816=13,545/13,983,816$ → 1 in 1,032
- 3/6: 1 in 56.7
- 2/6: 1 in 8.0
- etc.

Expected number matches $E[X]=nK/N = 36/49\approx0.73$ — linearity of expectation.

For Powerball-style two drums — white $n_1=5$ from $N_1=69$ and red $n_2=1$ from $N_2=26$ — total probability product of hypergeometrics: $P_{white}(k_1)\times P_{red}(k_2)$. Jackpot $k_1=5,k_2=1$: $1/\binom{69}{5}\times1/26$.

##### Putting It In Perspective — Comparison Table

| Event                                           | Odds — 1 in X | Combinatorics                                                    |
| :---------------------------------------------- | :------------ | :--------------------------------------------------------------- |
| Winning Mega Millions Jackpot — 5/70 + 1/25     | 302,575,350   | $\binom{70}{5}\times25$                                          |
| Winning Powerball Jackpot — 5/69 + 1/26         | 292,201,338   | $\binom{69}{5}\times26$                                          |
| Winning standard 6/49 Lottery                   | 13,983,816    | $\binom{49}{6}$                                                  |
| Matching exactly 3/6 in 6/49                    | ~56.7         | Hypergeometric $\frac{\binom{6}{3}\binom{43}{3}}{\binom{49}{6}}$ |
| Being struck by lightning — lifetime            | ~15,300       | empirical risk                                                   |
| Hole-in-one — amateur per par-3                 | ~12,500       | empirical                                                        |
| Injured by toilet — annually                    | ~10,000       | empirical                                                        |
| Bitten by shark per beach visit                 | ~3,700,000    | empirical                                                        |
| Killed by shark — lifetime                      | ~4,332,817    | empirical                                                        |
| Average person winning Olympic medal — lifetime | ~662,000      | population / medals                                              |
| Killed by vending machine — annually            | ~112,000,000  | empirical                                                        |

**Takeaway:** Lottery jackpot ~24 bits entropy, but you buy 1 ticket — chance $2^{-23.7}$. 6-char password $2^{28}$ — similar magnitude. Difference: attacker can try billions of passwords per second — GPU, combinatorics of search space matters — while lottery draw happens twice weekly — time-limited.

**Combinatorics summary for lotteries:**

- **Permutations** $P(n,k)$ if order mattered — would be $49\times48\dots44=10B$ vs $13.9M$ — dividing by $k!$ saves factor 720.
- **Combinations** $\binom{n}{k}$ if order irrelevant — standard.
- **Hypergeometric** for partial matches — without replacement — vs **Binomial** $\binom{n}{k}p^k(1-p)^{n-k}$ would apply with replacement — with replacement would be $n$ independent draws.
- **Inclusion-Exclusion** for "at least $k$ matches": $P(\ge k)=\sum_{i=k}^n P(X=i)$ or inclusion-exclusion if overlapping prizes.

Thus lottery = textbook example: sample space size from binomial coefficient, uniform probability over subsets, partial win probabilities from hypergeometric — same $\binom{n}{k}$, $\binom{K}{k}\binom{N-K}{n-k}$ toolkit used for password counting, committee selection, and card hands.



## Dirichlet's Box Principle — The Pigeonhole Principle — When Too Many Objects Forces Collision

Also known as Dirichlet's box principle or Dirichlet's drawer principle, named after German mathematician Peter Gustav Lejeune Dirichlet — 1805-1859 — who formalized it in 1834, sometimes referring to it as the Schubfachprinzip — "drawer principle". Despite its simplicity, pigeonhole principle is fundamental tool in combinatorics and is closely related to Ramsey Theory — both guarantee that certain patterns must appear when structure large enough. The principle guarantees that situation exists — e.g., at least two boxes share item — but does not specify which box contains items or which items they are — pure existence proof, non-constructive.

Intuition: if you have more socks than drawers, some drawer gets at least two socks. Trivial, but surprisingly powerful — turns counting into guarantee.

### Formal Statements

**The Basic Principle:** If you try to put 11 pigeons into 10 pigeonholes, at least one pigeonhole must contain at least 2 pigeons. More generally, if you have $n$ pigeons and $m$ holes where $n>m$, at least one hole must contain at least $\lceil n/m \rceil$ pigeons — ceiling function rounds up to nearest integer.

Proof by contradiction: suppose each hole contains at most 1 — actually at most $\lceil n/m\rceil-1$. Then total pigeons $\le m(\lceil n/m\rceil-1)<n$ — contradiction with $n$ pigeons placed — product rule.

**The Strong — Quantitative — Pigeonhole Principle:** If $n$ items distributed among $m$ containers, then at least one container must hold at least $\lceil n/m \rceil$ items. For example, if you distribute 100 items into 7 containers, at least one container must hold at least $\lceil100/7\rceil=15$ items — because $7\times14=98<100$.

Generalized version — Erdős–Szekeres form: If $n$ items in $m$ boxes and $n>km$, then some box has at least $k+1$ items. Basic principle is $k=1$.

**Probabilistic refinement:** Principle is worst-case guarantee — if $n\gg m$, average $\mu=n/m$, some box $\ge\mu$. By averaging argument — pigeonhole is averaging principle.

### Why It Matters — Non-Constructive Existence

The pigeonhole principle proves that coincidences and patterns are sometimes unavoidable mathematical necessities rather than unlikely events. It's tool for proving existence without construction — you can prove something must exist without finding or identifying it.

The principle proves that collision exists, but does not tell you which container holds items. The principle assumes all items placed into containers, but real-world scenarios might involve complexities where items don't fit, acting as "blockages" in container — e.g., capacity constraints.

This non-constructive nature is feature: often easier to prove existence via counting than to construct example — e.g., prove two people in NYC have same number of hairs — without finding them.

### Continuous and Infinite Versions

- **Continuous pigeonhole:** If $n$ points placed in unit interval, two within $1/(n-1)$. Proof: divide into $n-1$ subintervals length $1/(n-1)$ — holes.

- **Infinite pigeonhole:** If infinitely many pigeons into finitely many holes, some hole infinite — used to prove Bolzano-Weierstrass — infinite sequence in $$ has accumulation point: divide into 2 halves, one has infinitely many points — iterate.[0][1]

- **Measure pigeonhole:** If $A_1,\dots,A_m\subset[0,1]$ and $\sum|A_i|>k$, some point belongs to at least $k+1$ sets — averaging — used in ergodic theory — Kac's lemma.

### Uses of the Pigeonhole Principle

#### Hash Collisions — Information Must Be Lost

**Statement:** Any hash function $H: \{0,1\}^* \to \{0,1\}^n$ mapping arbitrary-length inputs to $n$-bit outputs must have collisions — two distinct inputs $x\neq y$ with $H(x)=H(y)$. In fact infinitely many collisions per output.

This is pure pigeonhole on infinite vs finite, not on counting subsets.

**Setup:**

- **Pigeons:** All possible files — infinite set $\{0,1\}^*$ — every string of bits length $0,1,2,...$ — countably infinite.
- **Holes:** All $n$-bit hashes — set $\{0,1\}^n$ — size $m=2^n$ finite — e.g., for SHA-256, $n=256$, $m=2^{256}\approx1.15\times10^{77}$.
- **Function:** $H$ assigns each pigeon to a hole.

Since $|\text{Domain}|=\infty > 2^n=|\text{Codomain}|$, by Dirichlet's principle $H$ cannot be injective — cannot preserve distinctness. Formal proof: consider first $2^n+1$ distinct inputs $x_0,...,x_{2^n}$ — $2^n+1$ pigeons, $2^n$ holes — at least two collide: $H(x_i)=H(x_j)$. That's basic principle. For infinitely many collisions per output, infinite pigeonhole: infinitely many pigeons into finitely many holes → some hole gets infinitely many.

**Why not combinatorics?** We are not counting $k^n$ assignments or $\binom{n}{k}$ subsets. We are proving _non-existence_ of injection from infinite to finite — cardinality argument — $|A|>|B|\implies$ no injection $A\hookrightarrow B$. No binomial coefficients.

**Consequences:**

- **Lossy compression unavoidable:** Any compressor that maps all $N$-bit files to $<N$ bits must make two different $N$-bit files compress to same file — cannot be decompressed losslessly for all inputs. Proof: $2^N$ inputs, $2^N-1$ possible compressed outputs ($0$ to $N-1$ bits) — pigeonhole.

- **Birthday bound — probabilistic pigeonhole:** Pigeonhole guarantees collision after $2^n+1$ inputs worst-case. But random hashing finds collision much earlier: after about $\sqrt{2^n}=2^{n/2}$ random inputs, collision probability >50%. Why? Number of pairs among $k$ inputs = $\binom{k}{2}\approx k^2/2$. Each pair collides with prob $1/2^n$. Expected collisions $\approx k^2/2^{n+1}$. Set =1 → $k\approx2^{n/2}$. This explains why SHA-256 — 256-bit — offers only 128-bit security against collision attacks — need $2^{128}$ work, not $2^{256}$.

- **Pigeonhole in cryptography:** Merkle-Damgård construction, hash tables: load factor $\alpha=n/m$ — $n$ items, $m$ slots — strong principle says some slot has $\lceil\alpha\rceil$ items. So hash table worst-case lookup $\Omega(n/m)$. No way to avoid — Dirichlet forces it.

No counting of permutations — just function $f: \text{infinite}\to\text{finite}$ cannot be injective.

#### Pumping Lemma — Regular Languages Must Loop

**Statement:** For any regular language $L$, there exists pumping length $p$ such that any string $s\in L$ with $|s|\ge p$ can be split $s=xyz$ with $|y|>0$, $|xy|\le p$, and $xy^i z\in L$ for all $i\ge0$ — you can repeat middle part forever and stay in language.

This proves languages like $\{0^n1^n\}$ not regular.

**Setup — DFA as pigeonholes:**
A regular language is recognized by Deterministic Finite Automaton DFA with finite number of states $m$ — e.g., $m=5$ states.

- **Holes:** States of DFA — $Q=\{q_0,...,q_{m-1}\}$ — $m$ holes.
- **Pigeons:** Positions visited while reading string $s=s_1 s_2 ... s_n$ length $n$ — we visit $n+1$ states: $q_0$ start, then after each character $q_1,q_2,...,q_n$ — $n+1$ pigeons.

If $n\ge m$ — string longer than number states — then $n+1 > m$ pigeons into $m$ holes → by pigeonhole, some state repeats: exists $i<j$ with $q_i=q_j$ — loop in state diagram.

Then split: $x=s_1...s_i$ leads to first occurrence, $y=s_{i+1}...s_j$ is loop — takes state back to itself, so $|y|>0$, and $z=s_{j+1}...s_n$ remainder. Since loop can be taken 0 times or repeated $i$ times, $xy^i z$ also accepted — pumping.

**Why not combinatorics?** We are not enumerating $\binom{n}{k}$ strings. We are using topological property of directed graph with finite vertices: any walk of length $\ge m$ must repeat a vertex — pigeonhole on path vs vertices. This is graph theory as _dynamics_, not counting.

**Consequence:** Proves finiteness of memory forces periodicity. Same argument gives pumping for context-free languages — stack + states finite — uses infinite pigeonhole on parse tree height.

Example: prove $\{0^n1^n: n\ge0\}$ not regular: assume DFA with $p$ states, take $s=0^p1^p$, $|s|\ge p$, split $s=xyz$ with $|xy|\le p$ → $y$ all zeros → $xy^2z=0^{p+|y|}1^p$ not in language → contradiction. Existence of loop — forced by pigeonhole — destroys language.

#### Fermat's Little Theorem — Repetition Mod $p$ Forces $a^{p-1}\equiv1$

**Statement:** For prime $p$ and integer $a$ not divisible by $p$, $a^{p-1}\equiv1\pmod p$.

Classic number theory — proof is pigeonhole on residues as holes, not counting combinations.

**Proof:**

Consider $p-1$ numbers:
$$a, 2a, 3a, ..., (p-1)a$$

- **Pigeons:** these $p-1$ multiples.
- **Holes:** non-zero residues mod $p$: $1,2,...,p-1$ — also $p-1$ holes.

Claim 1: None of these multiples $\equiv0\pmod p$ — since $p$ prime and $p\nmid a$, $p\nmid k$ for $1\le k<p$, so $p\nmid ka$.

Claim 2: They are all distinct mod $p$. If $ia\equiv ja\pmod p$ with $1\le i<j\le p-1$, then $p\mid(j-i)a$ → $p\mid(j-i)$ since $p\nmid a$ → impossible as $0<j-i<p$.

So we have $p-1$ distinct non-zero residues — pigeons into $p-1$ holes distinct → they must be exactly a permutation of $1,...,p-1$ — bijection.

Thus product of set = product of residues mod $p$:
$$(a)(2a)...((p-1)a) \equiv 1\cdot2\cdots(p-1) \pmod p$$
$$a^{p-1}(p-1)! \equiv (p-1)! \pmod p$$

Since $(p-1)!$ not divisible by $p$ — $p$ prime — invertible mod $p$, cancel it:

$$a^{p-1}\equiv1\pmod p$$

**Why not combinatorics?** No $\binom{n}{k}$, no $k^n$. We use pigeonhole to prove map $x\mapsto ax \mod p$ is bijection on $(\mathbb{Z}/p\mathbb{Z})^\times$ — finite set to itself injective → surjective. This is group theory: multiplication by $a$ permutes non-zero residues. Pigeonhole is used as "injective map finite set to itself is bijective".

**Generalization — Euler:** For any $m$ coprime to $a$, $a^{\phi(m)}\equiv1\pmod m$ where $\phi(m)=|(\mathbb{Z}/m)^\times|$ — number of residues coprime to $m$. Same proof: $a$ times units permutes units — $p-1$ holes = units — pigeonhole forces permutation.

This underlies RSA: $e d\equiv1\pmod{\phi(N)}$ → $a^{ed}\equiv a$.

Related pigeonhole lemma: sequence $a, a^2, a^3,...$ mod $m$ must eventually repeat — only $m$ residues — holes — with $m+1$ powers — pigeons — $a^i\equiv a^j$ for $i<j$ → $a^{j-i}\equiv1$ if $a$ invertible. Existence of order of element in finite group — Lagrange.

#### No Injective Continuous Map $\mathbb{R}^2\to\mathbb{R}$ — Topology Needs Pigeonhole on Connectedness

**Statement:** There is no continuous injection $f:\mathbb{R}^2\to\mathbb{R}$. You cannot embed plane into line continuously without tearing — dimension matters.

This is not about counting — about connected components as holes.

**Proof by contradiction via pigeonhole on components:**

Assume continuous injective $f:\mathbb{R}^2\to\mathbb{R}$.

Take plane minus origin: $\mathbb{R}^2\setminus\{(0,0)\}$ — this set is still path-connected — you can go around origin — one piece — connected.

Its image under $f$: $f(\mathbb{R}^2\setminus\{0\}) = f(\mathbb{R}^2)\setminus\{f(0)\}$ because $f$ injective — removing one point from domain removes exactly one point $f(0)$ from image.

Now $f(\mathbb{R}^2)\subseteq\mathbb{R}$ is some interval or union? Since $\mathbb{R}^2$ connected and $f$ continuous, $f(\mathbb{R}^2)$ is connected in $\mathbb{R}$ → interval $I$.

Remove a point $f(0)$ from interior of interval: what happens? $\mathbb{R}$ minus a point disconnects into at most 2 components:

- If $f(0)$ is interior point of $I$, then $I\setminus\{f(0)\}$ = two disjoint open intervals $(-\infty,f(0))$ and $(f(0),\infty)$ intersect $I$ → 2 components.
- If $f(0)$ is endpoint, $I\setminus\{f(0)\}$ = 1 component.

In either case, $I\setminus\{f(0)\}$ has at most 2 connected components.

But $\mathbb{R}^2\setminus\{0\}$ is connected — 1 component — its continuous image must be connected? Wait continuous image of connected is connected, but $f$ restricted to $\mathbb{R}^2\setminus\{0\}$ is still continuous, its image should be connected — so $I\setminus\{f(0)\}$ must be connected — so $f(0)$ must be endpoint of $I$.

So far possible. Need stronger: remove _two_ points.

Consider $\mathbb{R}^2\setminus\{a,b\}$ — two points removed — still path-connected — you can go around — 1 component — still one piece. (In $\mathbb{R}^2$, removing finite set does not disconnect).

But image: $I\setminus\{f(a),f(b)\}$ — interval minus two distinct points — has at most 3 components, but if $f(a),f(b)$ interior, it has 3 components: $(-\infty,\min)$, $(\min,\max)$, $(\max,\infty)$. That's 3 components — but domain $\mathbb{R}^2\setminus\{a,b\}$ has 1 component — continuous image of connected must be connected — cannot be 3 components — contradiction?

Wait we need more precise pigeonhole: continuous injective map from connected to disconnected impossible, but $I\setminus\{f(a),f(b)\}$ with 2 points removed is disconnected — 3 pieces — but $\mathbb{R}^2\setminus\{a,b\}$ is still connected — 1 piece — so its image under continuous $f$ must be connected — contradiction. Therefore no such injection.

More formal: If $f$ continuous injective, $f$ restricted to $\mathbb{R}^2\setminus\{a,b\}$ is continuous, domain connected → image connected. But image = $f(\mathbb{R}^2)\setminus\{f(a),f(b)\}$ = interval $I$ minus two points → disconnected — at least 2 components. Contradiction.

**Why pigeonhole?** We use pigeonhole principle on _connected components as holes_:

- Holes = connected components of codomain minus points.
- Pigeons = connected domain remains one piece — cannot be split into multiple holes continuously.

In $\mathbb{R}$, removing 1 point creates 2 holes, removing 2 creates 3 holes — pigeonhole: 1 connected pigeon cannot occupy 2 holes simultaneously.

This is invariant of domain: number of components after removing $k$ points is topological invariant — distinguishes dimensions — $\mathbb{R}^2$ minus $k$ points has 1 component, $\mathbb{R}$ minus $k$ points has $k+1$ components — different.

Generalization: No injective continuous map $\mathbb{R}^n\to\mathbb{R}^m$ if $n>m$ — invariance of domain — Brouwer — deeper pigeonhole on homology.

So all four examples use same Dirichlet skeleton: $n$ pigeons > $m$ holes → collision — but holes are hashes, DFA states, residues mod $p$, and connected components — not combinatorial subsets.
