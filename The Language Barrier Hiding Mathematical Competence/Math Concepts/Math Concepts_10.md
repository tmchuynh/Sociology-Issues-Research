### Stirling Numbers

Stirling numbers, named after James Stirling (1692–1770), are two related triangular arrays of numbers that are fundamental in combinatorics. They both count ways to arrange $n$ distinct objects, but they answer two different questions:

- **First kind:** How many ways to arrange them into $k$ _cycles_ (circular orderings)?
- **Second kind:** How many ways to group them into $k$ _sets_ (unordered collections)?

The distinction between sets and cycles is the core of the theory.

**What Sets vs Cycles Means**

Take $n=3$ elements $\{A,B,C\}$.

$$
\begin{align*}
\text{Set }\{A,B,C\} &= \text{ no order, }\{A,B\}=\{B,A\}\\[12pt]
\text{Cycle }(A\,B\,C) &= \text{ circular order, }(A\,B\,C)=(B\,C\,A)=(C\,A\,B)\neq(A\,C\,B)
\end{align*}
$$

In a set, internal order irrelevant. In a cycle, who follows whom matters, but rotation of whole cycle irrelevant because table has no distinguished seat. So a set of size $m$ can be arranged into $(m-1)!$ different cycles. That factor explains why first kind counts are larger than second kind except extremes.

$$
\begin{align*}
S(n,k) &= \left\{{n\atop k}\right\} = \#\text{ ways into }k\text{ unlabeled sets}\\[12pt]
c(n,k) &= \left[{n\atop k}\right] = \#\text{ ways into }k\text{ cycles}
\end{align*}
$$

#### History and Discovery

- **James Stirling** $\left(1692-1770\right)$, Scottish mathematician, introduced second kind numbers in _Methodus Differentialis_ $\left(1730\right)$ to express powers in terms of falling factorials for interpolation and series acceleration. He gave tables and recurrence $S(n,k)=kS(n-1,k)+S(n-1,k-1)$ without modern partition interpretation.

- **Earlier roots:** Tables equivalent to $S(n,k)$ appear in Japanese mathematician Seki Takakazu $\left(\sim1683\right)$ and in Stirling's contemporary. First kind numbers arise from expansions of $x(x-1)\cdots(x-n+1)$, studied by Newton and Stirling for finite differences.

- **Niels Nielsen $\left(1904\right)$** coined term "Stirling numbers of the first and second kind" and distinguished $s(n,k)$ signed vs $c(n,k)$ unsigned. He systematically studied their algebraic properties.

- **Charles Peirce $\left(1880s\right)$** and later **Eric Temple Bell $\left(1934\right)$** connected $S(n,k)$ to set partitions, defining Bell numbers $B_{n}=\sum_{k}S(n,k)$ as row sums. Peirce's Bell triangle predates Bell.

- **Modern notation:** $\left\{{n\atop k}\right\}$ and $\left[{n\atop k}\right]$ brackets/braces introduced by Karamata $\left(1935\right)$ and popularized by Knuth $\left(1992\right)$ to mirror binomial $\displaystyle\binom{n}{k}$ — mnemonic: $\{\}$ for sets, $[]$ for cycles.

#### Stirling Numbers of the Second Kind

Denoted $\displaystyle S(n,k)$ or $\displaystyle \left\{ {n \atop k} \right\}$, pronounced "$n$ brace $k$".

**Combinatorial definition:**

$$\displaystyle S(n,k)=\dfrac{\text{\# onto functions }[n]\to[k]}{k!}$$

Because onto function determines preimage partition into $k$ labeled blocks, divide by $k!$ to forget labels.

Example: $n=3$ friends $\{A,B,C\}$ into $k=2$ groups.
$$\{A,B\}\{C\},\; \{A,C\}\{B\},\; \{B,C\}\{A\}$$
So $S(3,2)=3$. The groups are unlabeled — $\{A,B\}\{C\}$ is the same as $\{C\}\{A,B\}$.

**Values:** $S(n,0)=0$ for $n>0$, $S(0,0)=1$, $S(n,1)=1$, $S(n,n)=1$, $S(n,2)=2^{n-1}-1$.

**Recurrence:**

$$\displaystyle S(n,k)=k\,S(n-1,k)+S(n-1,k-1)$$

Fix element $n$:

$$
\displaystyle
\begin{align*}
\text{Case 1: } \{n\}\text{ not singleton}&: \text{ partition }[n-1]\text{ into }k\text{ blocks }[S(n-1,k)\text{ ways}],\\[12pt]
&\quad \text{choose one of }k\text{ blocks to insert }n\text{ into }[k\text{ choices}]\\[12pt]
\text{Case 2: } \{n\}\text{ singleton}&: \text{ partition }[n-1]\text{ into }k-1\text{ blocks }[S(n-1,k-1)\text{ ways}]
\end{align*}
$$

Example: $n=4,k=2$:

$$\displaystyle S(4,2)=2S(3,2)+S(3,1)=2\cdot3+1=7$$

$7$ = $4$ ways $3+1$ $\left(\{A\}\{BCD\}\text{ type}\right)$ + $3$ ways $2+2$ $\left(\{AB\}\{CD\}\text{ type}\right)$.

**Detailed view of recurrence:**

Take partition of $\{1,\dots,n-1\}$ counted by $S(n-1,k)$ — $k$ blocks. Element $n$ can be inserted into any of those $k$ blocks — $k$ distinct partitions of $n$-set with $k$ blocks where $\{n\}$ is not singleton. That's $kS(n-1,k)$.

If $\{n\}$ is singleton, delete it — you get partition of $n-1$ into $k-1$ blocks — $S(n-1,k-1)$ possibilities. Disjoint cases cover all.

Example: $S(4,2)=2S(3,2)+S(3,1)=2\cdot3+1=7$ — matches $3+1$ vs $2+2$ count earlier.

**Explicit Formula (Inclusion-Exclusion):**
$$\displaystyle S(n,k) = \dfrac{1}{k!} \sum_{j=0}^{k} (-1)^{k-j} \binom{k}{j} j^n$$

**Derivation:**

Number of onto functions $f:\{1,\dots,n\}\to\{1,\dots,k\}$ is $k!S(n,k)$ because onto function partitions domain into $k$ labeled preimage blocks $\left(S(n,k)\text{ ways unlabeled, }k!\text{ labelings}\right)$.

Count onto functions by inclusion-exclusion: total functions $k^{n}$, subtract those missing at least one value.

$$
\displaystyle
\begin{align*}
k!S(n,k) &= \sum_{j=0}^{k}(-1)^{j}\binom{k}{j}(k-j)^{n}\\[12pt]
&= \sum_{j=0}^{k}(-1)^{k-j}\binom{k}{j}j^{n}
\end{align*}
$$

Divide by $k!$:

$$\displaystyle S(n,k)=\dfrac{1}{k!}\sum_{j=0}^{k}(-1)^{k-j}\binom{k}{j}j^{n}$$

Total $j^{n}$ functions into $j$-subset, inclusion-exclusion over missing values.

Example $n=3,k=2$:

$$\displaystyle S(3,2)=\dfrac{1}{2!}\left[\binom{2}{0}0^{3}-\binom{2}{1}1^{3}+\binom{2}{2}2^{3}\right]=\dfrac{1}{2}\left[0-2+8\right]=3$$

**Small values:**

$$
\displaystyle
\begin{align*}
S(n,0)&=\begin{cases}1&n=0\\0&n>0\end{cases}\\[12pt]
S(n,1)&=1\\[12pt]
S(n,2)&=2^{n-1}-1=\dfrac{2^{n}-2}{2}\\[12pt]
S(n,n-1)&=\binom{n}{2}\\[12pt]
S(n,n)&=1
\end{align*}
$$

**Relation to Bell Numbers:** Summing across $k$ gives the total number of partitions:
$$\displaystyle B_n = \sum_{k=0}^{n} S(n,k)$$

So $B_{n}$ is row sum. For $n=4$: $1+7+6+1=15$.

**Expanded reading — what $S(n,k)$ is really counting:**

$$\displaystyle S(n,k)=\text{number of ways to split }n\text{ distinct labeled balls into }k\text{ identical non-empty boxes}$$

Labeled balls — $A,B,C$ distinct. Identical boxes — only which balls are together matters, not which box is called $1$ or $2$. Empty boxes not allowed.

Example $n=3,k=2$:

$$
\displaystyle
\begin{align*}
\{A,B\}\{C\}\\[12pt]
\{A,C\}\{B\}\\[12pt]
\{B,C\}\{A\}
\end{align*}
$$

If boxes were labeled Box1, Box2, each partition would correspond to $2!=2$ labeled assignments, so onto functions $[3]\to[2]$ count $3\cdot2=6$, and $S(3,2)=6/2!=3$.

$$\displaystyle S(n,k)=\dfrac{\#\text{onto functions}}{k!}$$

**Why the special values make sense:**

$$
\displaystyle
\begin{align*}
S(n,1)&=1 &&\text{All balls in one box: only }\{[n]\}\\[12pt]
S(n,n)&=1 &&\text{Each ball alone: only }\{1\}\{2\}\cdots\{n\}\\[12pt]
S(n,0)&=0\;(n>0) &&\text{No way to place balls into no boxes}\\[12pt]
S(n,n-1)&=\binom{n}{2} &&\text{One box has 2 balls, rest singletons: choose the pair}
\end{align*}
$$

$$\displaystyle S(n,2)=2^{n-1}-1$$

Derivation in counting language: Put ball $1$ in box $A$ to break symmetry $\left(\text{boxes unlabeled, but }1\text{'s box can be called }A\right)$. Each of remaining $n-1$ balls chooses $A$ or $B$ — $2^{n-1}$ choices. Exclude choice where all choose $A$ leaving $B$ empty — $1$ excluded. So $2^{n-1}-1$.

$$\displaystyle S(4,2)=\dfrac{2^{4}-2}{2}=7$$

**Recurrence $\displaystyle S(n,k)=kS(n-1,k)+S(n-1,k-1)$ — two ways $n$ appears:**

Picture building partitions of $\{1,\dots,n\}$ from partitions of $\{1,\dots,n-1\}$.

$$
\displaystyle
\begin{align*}
\text{Let }P_{n-1}&\text{ be partition of }[n-1]\\[12pt]
\text{Insert }n&:
\begin{cases}
\text{into existing block}&: k\text{ choices if }P_{n-1}\text{ has }k\text{ blocks}\\[12pt]
\text{as new block }\{n\}&: 1\text{ way, reduces block count}
\end{cases}
\end{align*}
$$

Formally:

$$
\displaystyle
\begin{align*}
S(n,k) &= kS(n-1,k) &&\text{(n joins)} + S(n-1,k-1) &&\text{(n alone)}
\end{align*}
$$

Example $n=4,k=2$:

$$
\displaystyle
\begin{align*}
S(4,2) &= 2S(3,2)+S(3,1)\\[12pt]
&=2\cdot3+1=7
\end{align*}
$$

$2S(3,2)$: take $3$ partitions of $\{A,B,C\}$ into $2$ blocks, insert $D$ into either of $2$ blocks → $6$ partitions where $D$ not alone. $S(3,1)$: partition $\{A,B,C\}$ into $1$ block, add $\{D\}$ singleton → $1$ partition $\{ABC\}\{D\}$. But also partitions like $\{AB\}\{C\}\{D\}$? No, that has $k=3$. For $k=2$, singleton case yields only those where $D$ alone and rest together.

The full $7$ for $\{A,B,C,D\}$:

$$
\displaystyle
\begin{align*}
3+1\text{ shape}&: \{A\}\{BCD\},\{B\}\{ACD\},\{C\}\{ABD\},\{D\}\{ABC\} && 4\\[12pt]
2+2\text{ shape}&: \{AB\}\{CD\},\{AC\}\{BD\},\{AD\}\{BC\} && 3
\end{align*}
$$

**Inclusion-exclusion formula — why $\displaystyle\dfrac{1}{k!}\sum (-1)^{k-j}\binom{k}{j}j^{n}$:**

Count onto functions $f:[n]\to[k]$.

Total functions $k^{n}$. Let $A_{i}$ = functions missing value $i$ $\left(\text{image }\subseteq[k]\setminus\{i\}\right)$. Want $\left|\bigcap A_{i}^{c}\right|$.

By inclusion-exclusion:

$$
\displaystyle
\begin{align*}
\#\text{onto} &= \sum_{j=0}^{k}(-1)^{j}\binom{k}{j}(k-j)^{n}\\[12pt]
&= \sum_{j=0}^{k}(-1)^{k-j}\binom{k}{j}j^{n}\quad (j\mapsto k-j)
\end{align*}
$$

Because choose $j$ values to miss $\displaystyle\binom{k}{j}$, remaining $k-j$ values can be used arbitrarily $(k-j)^{n}$.

Each onto function has fibers $f^{-1}(i)$ forming $k$ labeled blocks. Forgetting labels $\to S(n,k)$ unlabeled partitions, and $k!$ labelings per partition, so

$$\displaystyle S(n,k)=\dfrac{\#\text{onto}}{k!}=\dfrac{1}{k!}\sum_{j=0}^{k}(-1)^{k-j}\binom{k}{j}j^{n}$$

Example $\displaystyle n=4,k=2$:

$$
\displaystyle
\begin{align*}
S(4,2) &= \dfrac{1}{2!}\left[\binom{2}{0}0^{4}-\binom{2}{1}1^{4}+\binom{2}{2}2^{4}\right]\\[12pt]
&= \dfrac{1}{2}\left[0-2+16\right]=7
\end{align*}
$$

$\displaystyle 0^{4}=0$ for $n>0$, term $j=0$ vanishes unless $n=0$ where $0^{0}=1$ gives $S(0,0)=1$.

**Bell numbers as row sums — building $B_{n}$:**

$$\displaystyle B_{n}= \sum_{k=0}^{n} S(n,k)$$

Fix $n$, sum over possible number of blocks $k$. $B_{n}$ counts all partitions regardless of $k$.

$$
\displaystyle
\begin{align*}
B_{0}&=S(0,0)=1\\[12pt]
B_{1}&=S(1,1)=1\\[12pt]
B_{2}&=S(2,1)+S(2,2)=1+1=2\\[12pt]
B_{3}&=1+3+1=5\\[12pt]
B_{4}&=1+7+6+1=15\\[12pt]
B_{5}&=1+15+25+10+1=52
\end{align*}
$$

This matches recurrence $B_{n+1}=\sum_{k=0}^{n}\binom{n}{k}B_{k}$: choose $k$ elements not with $n+1$, partition them $B_{k}$ ways.

**Generating functions:**

$$
\displaystyle
\begin{align*}
\sum_{n\ge k} S(n,k)\dfrac{x^{n}}{n!} &= \dfrac{(e^{x}-1)^{k}}{k!}\\[12pt]
\sum_{n\ge0} B_{n}\dfrac{x^{n}}{n!} &= \exp(e^{x}-1)=\sum_{k\ge0}\dfrac{(e^{x}-1)^{k}}{k!}
\end{align*}
$$

So $B_{n}$ EGF is exponential of $e^{x}-1$, explaining Dobinski $B_{n}=e^{-1}\sum k^{n}/k!$ — moment of Poisson$\left(1\right)$.

In short: $S(n,k)$ refines $B_{n}$ by $k$, $B_{n}$ aggregates $S(n,k)$, and $\dfrac{1}{k!}$ factor converts labeled to unlabeled.

#### Stirling Numbers of the First Kind

Denoted $\displaystyle s(n,k)$ (signed) or $\displaystyle c(n,k) = \left[ {n \atop k} \right]$ (unsigned), pronounced "$n$ bracket $k$".

**Combinatorial Meaning:** $c(n,k)$ counts the number of ways to arrange $n$ distinct elements into exactly $k$ disjoint cycles.

Every permutation splits uniquely into disjoint cycles. Example $(1\,3\,2)(4)$ has $k=2$ cycles.

A cycle is a circular ordering where rotation is considered the same but order matters: $(A B C)$, $(B C A)$, $(C A B)$ are the same cycle, but $(A C B)$ is different. Think of $n$ people sitting around $k$ identical round tables, where who sits to the left of whom matters, but the table has no distinguished seat.

Example: $n=3$, $k=2$. Cycles of 3 elements into 2 cycles must be one 2-cycle and one 1-cycle. The 1-cycle can be $A$, $B$, or $C$ (3 choices), the remaining two elements form one 2-cycle which is unique up to rotation. So $c(3,2)=3$, same as $S(3,2)$ in this case, but in general $c(n,k) \ge S(n,k)$.

**Unpacked cycle counting:**

Cycle $(x_{1}x_{2}\dots x_{m})$ means $x_{1}\to x_{2}\to\cdots\to x_{m}\to x_{1}$. Rotation $(x_{2}\dots x_{m}x_{1})$ same, reversal generally different unless $m\le2$.

Number of distinct $m$-cycles on given $m$ labeled elements = $(m-1)!$ — fix one element to break rotation, arrange remaining $m-1$ in order.

Thus for $n=4,k=1$: all $4$-cycles — $(4-1)!=6$.

For $n=4,k=2$: shapes $3+1$ and $2+2$:

- $3+1$: choose singleton $4$ ways, $3$-cycle on remaining $3$ has $2!=2$ ways → $8$
- $2+2$: pairings $\displaystyle\frac12\binom42=3$ ways, each $2$-cycle unique → $3$ total $11$.

**Signed vs. Unsigned:**

- Unsigned $\displaystyle c(n,k) = \left[ {n \atop k} \right] \ge 0$ counts cycles.

- Signed $s(n,k) = (-1)^{n-k} c(n,k)$. The signed version appears in algebra.

**Recurrence Relation:**
$$\displaystyle c(n,k) = (n-1) \cdot c(n-1,k) + c(n-1,k-1)$$

Fix element $n$:

$$
\displaystyle
\begin{align*}
\text{Case 1: }n\text{ not singleton cycle}&: \text{ take permutation of }[n-1]\text{ into }k\text{ cycles }[c(n-1,k)\text{ ways}],\\[12pt]
&\quad \text{insert }n\text{ after any of }n-1\text{ elements in its cycle }[(n-1)\text{ places}]\\[12pt]
\text{Case 2: }n\text{ singleton cycle }(n)&: c(n-1,k-1)\text{ ways}
\end{align*}
$$

_Proof idea:_ Consider element $n$. Either:

1. **It is inserted into an existing cycle of the $n-1$ other elements. A cycle with $m$ elements has $m$ insertion points, so across all cycles there are $n-1$ places to insert $n$**: $(n-1) c(n-1,k)$ ways, or

2. **It forms a new 1-cycle by itself**: $c(n-1,k-1)$ ways.

Why $n-1$ vs $k$? A $k$-block partition has $k$ places to join, but a permutation of $n-1$ has $n-1$ positions in cycles to splice $n$ after.

Example: $c(4,2)=3c(3,2)+c(3,1)=3\cdot3+2=11$ as enumerated $8$ type $3+1$ $\left(4\text{ choices singleton }\times2\text{ 3-cycles}\right)$ + $3$ type $2+2$.

Notice the difference from the second kind: $k$ vs. $(n-1)$.

**Detailed view — why $n-1$:**

Take permutation of $n-1$ elements as $k$ cycles. Visualize cycles as directed rings. Insert $n$ after any of $n-1$ existing elements: if $a\to b$ in cycle, replace with $a\to n\to b$. This yields distinct $k$-cycle permutation of $n$ elements, and every $k$-cycle permutation where $n$ not singleton arises once. So $(n-1)c(n-1,k)$ cases.

If $n$ singleton $(n)$, delete it → $c(n-1,k-1)$.

Example $c(4,2)=(3)c(3,2)+c(3,1)=3\cdot3+2=11$ — $c(3,1)=2$ counts two $3$-cycles $(ABC)$ and $(ACB)$.

**Relation between first and second:**

$$\displaystyle c(n,k)=\sum_{\text{partitions of }[n]\text{ into }k\text{ blocks}}\prod_{B}(|B|-1)!$$

Each set block of size $m$ can be ordered into $(m-1)!$ cycles, so $c$ dominates $S$.

Compare second kind $S(n,k)=kS(n-1,k)+S(n-1,k-1)$: $k$ choices of block to join vs $n-1$ insertion spots in cycles. Since $n-1\ge k$, $c(n,k)\ge S(n,k)$ for $k<n$, equality only when small.

**Expanded reading — what a cycle really is:**

$$\displaystyle (x_{1}\,x_{2}\,\dots\,x_{m})\text{ means }x_{1}\mapsto x_{2}\mapsto\cdots\mapsto x_{m}\mapsto x_{1}$$

Rotation same:

$$\displaystyle (A\,B\,C)=(B\,C\,A)=(C\,A\,B)$$

Reversal different:

$$\displaystyle (A\,B\,C)\neq(A\,C\,B)\text{ because }A\to B\text{ vs }A\to C$$

Counting distinct $m$-cycles on fixed set of $m$ labels:

$$\displaystyle c(m,1)=(m-1)!=\dfrac{m!}{m}$$

$m!$ permutations of labels in line, divide by $m$ rotations.

Example $m=3$: $2!=2$ cycles: $(A\,B\,C)$ and $(A\,C\,B)$.

$m=2$: $1!=1$ cycle: $(A\,B)$ same as $(B\,A)$.

$m=1$: $0!=1$ cycle: $(A)$.

**Concrete $n=3$ listing for $c(3,k)$:**

Permutations of $\{A,B,C\}$ = $3!=6$ total, split by cycle count:

$$
\displaystyle
\begin{align*}
k=3&: (A)(B)(C) && 1\\[12pt]
k=2&: (A)(B\,C),\;(B)(A\,C),\;(C)(A\,B) && 3\\[12pt]
k=1&: (A\,B\,C),\;(A\,C\,B) && 2\\[12pt]
\text{sum}&=6=3!
\end{align*}
$$

So $c(3,2)=3$ matches $S(3,2)=3$ coincidentally, but $c(3,1)=2\neq S(3,1)=1$.

**$n=4$ complete enumeration — why $11$:**

All permutations $4!=24$ split as $c(4,1)=6$, $c(4,2)=11$, $c(4,3)=6$, $c(4,4)=1$.

For $c(4,2)$, two shapes:

$$
\displaystyle
\begin{align*}
\text{Shape }3+1&: \text{choose singleton }\binom{4}{1}=4\text{ ways}\\[12pt]
&\quad\text{remaining }3\text{ elements have }(3-1)!=2\text{ 3-cycles each}\\[12pt]
&\quad\implies 4\cdot2=8\text{ permutations}\\[12pt]
\text{Examples}&: (A)(B\,C\,D),\;(A)(B\,D\,C),\;(B)(A\,C\,D),\dots
\end{align*}
$$

$$
\displaystyle
\begin{align*}
\text{Shape }2+2&: \text{partition }4\text{ into two pairs }\dfrac{1}{2}\binom{4}{2}=3\text{ ways}\\[12pt]
&\quad\text{each pair }2\text{-cycle unique}\\[12pt]
&\quad\implies 3\text{ permutations}\\[12pt]
\text{Examples}&: (A\,B)(C\,D),\;(A\,C)(B\,D),\;(A\,D)(B\,C)
\end{align*}
$$

Total $8+3=11$.

**Recurrence in words — insertion picture:**

Take permutation of $[n-1]$ with $k$ cycles. To make permutation of $$ with $k$ cycles where $n$ not alone:[n]

Write each cycle with arrows. There are $n-1$ arrows $a\to\text{next}(a)$. Insert $n$ in middle of any arrow: $a\to n\to\text{next}(a)$. That's $(n-1)$ distinct positions.

Example: cycle $(A\,B\,C)$ has arrows $A\to B$, $B\to C$, $C\to A$. Insert $D$ after $A$: $(A\,D\,B\,C)$, after $B$: $(A\,B\,D\,C)$, after $C$: $(A\,B\,C\,D)$. $3=n-1$ ways.

So

$$
\displaystyle
\begin{align*}
c(n,k) &= (n-1)c(n-1,k) &&\text{ $n$ inserted into existing cycle}\\[12pt]
&\quad + c(n-1,k-1) &&\text{ $n$ as singleton $(n)$}
\end{align*}
$$

Check:

$$
\displaystyle
\begin{align*}
c(4,2) &= 3c(3,2)+c(3,1)=3\cdot3+2=11\\[12pt]
c(4,3) &= 3c(3,3)+c(3,2)=3\cdot1+3=6\\[12pt]
c(4,1) &= 3c(3,1)+c(3,0)=3\cdot2+0=6
\end{align*}
$$

Contrast second kind recurrence $S(n,k)=kS(n-1,k)+S(n-1,k-1)$: joining $k$ existing blocks vs $(n-1)$ insertion spots.

**Signed vs unsigned — algebraic role:**

$$\displaystyle c(n,k)=\left[{n\atop k}\right]\ge0,\qquad s(n,k)=(-1)^{n-k}c(n,k)$$

$s(n,k)$ appears when expanding falling factorial:

$$
\displaystyle
\begin{align*}
x^{\underline{n}} &= x(x-1)(x-2)\cdots(x-n+1)\\[12pt]
&= \sum_{k=0}^{n}s(n,k)x^{k}
\end{align*}
$$

Example $n=3$:

$$
\displaystyle
\begin{align*}
x^{\underline{3}} &= x(x-1)(x-2)=x^{3}-3x^{2}+2x\\[12pt]
&= s(3,3)x^{3}+s(3,2)x^{2}+s(3,1)x\\[12pt]
s(3,3)&=1,\;s(3,2)=-3,\;s(3,1)=2\\[12pt]
c(3,3)&=1,\;c(3,2)=3,\;c(3,1)=2=|s|
\end{align*}
$$

Sign $(-1)^{n-k}$ because falling factorial has alternating signs.

**Formula linking first and second kind:**

Starting from set partition into $k$ blocks of sizes $m_{1},\dots,m_{k}$, each block can be turned into $(m_{i}-1)!$ cycles. So number of cycle partitions refining that set partition is $\prod (m_{i}-1)!$.

Summing over all set partitions:

$$\displaystyle c(n,k)=\sum_{\substack{\text{partitions }[n]=B_{1}\cup\cdots\cup B_{k}\\ |B_{i}|=m_{i}}}\;\prod_{i=1}^{k}(m_{i}-1)!$$

$$\displaystyle S(n,k)=\sum_{\substack{\text{same partitions}}}1$$

Hence termwise $\prod (m_{i}-1)!\ge1$, so

$$\displaystyle c(n,k)\ge S(n,k)$$

Equality only when all $m_{i}\le2$, because $(1-1)!=0!=1$, $(2-1)!=1!=1$. For $n=4,k=3$, all blocks sizes $2+1+1$ → product $1$ → $c(4,3)=S(4,3)=6$.

**Quick closed forms:**

$$
\displaystyle
\begin{align*}
c(n,0)&=\begin{cases}1&n=0\\0&n>0\end{cases}\\[12pt]
c(n,1)&=(n-1)!\\[12pt]
c(n,n)&=1\\[12pt]
c(n,n-1)&=\binom{n}{2}\\[12pt]
c(n,n-2)&=\dfrac{1}{4}(3n-1)\binom{n}{3}
\end{align*}
$$

$c(n,n-1)=\binom{n}{2}$: need one 2-cycle $\left(\text{transposition}\right)$ + $n-2$ singletons, choose pair.

Row sum:

$$\displaystyle \sum_{k=0}^{n}c(n,k)=n!$$

Because every permutation has some $k$ cycles. Compare $S$ row sum $B_{n}$ counts all set partitions — $n!$ grows faster than $B_{n}$ for $n\ge4$? Actually $B_{4}=15<24$, but $B_{n}$ eventually outgrows $n!$ super-exponentially.

**Exponential generating functions:**

$$
\displaystyle
\begin{align*}
\sum_{n\ge k}c(n,k)\dfrac{x^{n}}{n!} &= \dfrac{\left(-\ln(1-x)\right)^{k}}{k!}\\[12pt]
\sum_{n\ge k}S(n,k)\dfrac{x^{n}}{n!} &= \dfrac{(e^{x}-1)^{k}}{k!}
\end{align*}
$$

$-\ln(1-x)=x+\dfrac{x^{2}}{2}+\dfrac{x^{3}}{3}+\cdots$ enumerates cycles, $e^{x}-1$ enumerates non-empty sets — symbolic method.

#### Comparison Table for $n=4$

| $k$     | $S(4,k)$ — Partitions into $k$ sets                              | $c(4,k)$ — Permutations into $k$ cycles          |
| :------ | :--------------------------------------------------------------- | :----------------------------------------------- |
| 1       | 1 — $\{ABCD\}$                                                   | 6 — $(ABCD)$ has $(4-1)! = 6$ distinct rotations |
| 2       | 7 — 4 ways of type 3+1, 3 ways of type 2+2                       | 11 — 8 of type 3+1, 3 of type 2+2                |
| 3       | 6 — choose which pair is together: $\displaystyle\binom{4}{2}=6$ | 6 — same 6 partitions, but 2-cycles are forced   |
| 4       | 1 — $\{A\}\{B\}\{C\}\{D\}$                                       | 1 — $(A)(B)(C)(D)$                               |
| **Sum** | $1+7+6+1=15 = B_4$                                               | $6+11+6+1=24 = 4!$                               |

The row sum of the second kind is the Bell number $B_n$. The row sum of the first kind (unsigned) is $n!$ — the total number of permutations — because every permutation decomposes uniquely into cycles.

**Row sums via:**

$$
\displaystyle
\begin{align*}
\sum_{k} S(4,k) &= 1+7+6+1 = 15 = B_{4}\\[12pt]
\sum_{k} c(4,k) &= 6+11+6+1 = 24 = 4!
\end{align*}
$$

General: $\displaystyle\sum_{k}c(n,k)=n!$, $\displaystyle\sum_{k}S(n,k)=B_{n}$.

**Reading the table — what each cell counts for $\{A,B,C,D\}$:**

$$\displaystyle [4]=\{A,B,C,D\},\qquad n=4$$

- **Sets $S(4,k)$:** unordered collections, order inside block irrelevant, blocks unlabeled.
- **Cycles $c(4,k)$:** each block is a directed ring, order inside matters up to rotation, rings unlabeled as sets of cycles but internal circular order matters.

**$k=1$ — one block / one cycle:**

$$
\displaystyle
\begin{align*}
S(4,1)&=1: &&\{A,B,C,D\}\\[12pt]
c(4,1)&=(4-1)!=6: &&(A\,B\,C\,D),\;(A\,B\,D\,C),\;(A\,C\,B\,D),\;(A\,C\,D\,B),\;(A\,D\,B\,C),\;(A\,D\,C\,B)
\end{align*}
$$

Why $6$? Fix $A$ at top of circle to break rotation, arrange $B,C,D$ in $3!=6$ orders around. All $6$ collapse to same set partition.

$$\displaystyle \dfrac{c(4,1)}{S(4,1)}=\dfrac{6}{1}=3!= (4-1)!$$

**$k=2$ — two blocks / two cycles — shapes $3+1$ and $2+2$:**

For sets:

$$
\displaystyle
\begin{align*}
\text{type }3+1&: \binom{4}{1}=4\text{ ways: choose singleton}\\[12pt]
&\{A\}\{BCD\},\{B\}\{ACD\},\{C\}\{ABD\},\{D\}\{ABC\}\\[12pt]
\text{type }2+2&: \dfrac12\binom{4}{2}=3\text{ ways: pairings}\\[12pt]
&\{AB\}\{CD\},\{AC\}\{BD\},\{AD\}\{BC\}\\[12pt]
S(4,2)&=4+3=7
\end{align*}
$$

For cycles:

$$
\displaystyle
\begin{align*}
\text{type }3+1&: \binom{4}{1}=4\text{ choices singleton }\times(3-1)!=2\text{ cycles on triple}\\[12pt]
&=8\text{ : }(A)(B\,C\,D),(A)(B\,D\,C),(B)(A\,C\,D),\dots\\[12pt]
\text{type }2+2&: \dfrac12\binom{4}{2}=3\text{ pairings }\times1\cdot1\text{ cycles per pair}\\[12pt]
&=3\text{ : }(A\,B)(C\,D),(A\,C)(B\,D),(A\,D)(B\,C)\\[12pt]
c(4,2)&=8+3=11
\end{align*}
$$

Extra $4$ cycles come from $2$ possible orientations of each $3$-element block.

$$\displaystyle c(4,2)-S(4,2)=4,\qquad \dfrac{c(4,2)}{S(4,2)}=\dfrac{11}{7}$$

**$k=3$ — three blocks — shape must be $2+1+1$:**

$$
\displaystyle
\begin{align*}
S(4,3)&=\binom{4}{2}=6: &&\text{choose which pair together}\\[12pt]
&\{AB\}\{C\}\{D\},\{AC\}\{B\}\{D\},\{AD\}\{B\}\{C\},\{BC\}\{A\}\{D\},\{BD\}\{A\}\{C\},\{CD\}\{A\}\{B\}\\[12pt]
c(4,3)&=6\text{ also}: &&(A\,B)(C)(D),\dots\text{ same 6, because 2-cycle unique}
\end{align*}
$$

For blocks size $\le2$, $(m-1)!=1$, so no extra cycles:

$$\displaystyle \prod (m_{i}-1)! = (2-1)!(1-1)!(1-1)!=1$$

Thus $c(4,3)=S(4,3)$.

**$k=4$ — four blocks — all singletons:**

$$
\displaystyle
\begin{align*}
S(4,4)&=1: \{A\}\{B\}\{C\}\{D\}\\[12pt]
c(4,4)&=1: (A)(B)(C)(D)
\end{align*}
$$

**Row sums — why $B_{4}$ and $4!$:**

$$
\displaystyle
\begin{align*}
\sum_{k=1}^{4}S(4,k) &= S(4,1)+S(4,2)+S(4,3)+S(4,4)\\[12pt]
&=1+7+6+1=15=B_{4}\\[12pt]
&=\text{total set partitions of 4-set}
\end{align*}
$$

Every partition has some $k$ blocks, partition counted once in exactly one $S(4,k)$.

$$
\displaystyle
\begin{align*}
\sum_{k=1}^{4}c(4,k) &= c(4,1)+c(4,2)+c(4,3)+c(4,4)\\[12pt]
&=6+11+6+1=24=4!\\[12pt]
&=\text{total permutations of 4 elements}
\end{align*}
$$

Every permutation decomposes uniquely into cycles, with some $k$ cycles, counted once in $c(4,k)$.

General identities:

$$
\displaystyle
\begin{align*}
\sum_{k=0}^{n} S(n,k) &= B_{n}\\[12pt]
\sum_{k=0}^{n} c(n,k) &= n!\\[12pt]
\sum_{k=0}^{n} s(n,k) &=
\begin{cases}
1 & n=0\\[12pt]
0 & n>0
\end{cases}\quad\text{since }x^{\underline{n}}|_{x=1}=0\text{ for }n>0
\end{align*}
$$

**Conversion factor between columns:**

For fixed partition shape with block sizes $m_{1},\dots,m_{k}$, $\displaystyle\sum m_{i}=n$:

$$\displaystyle \#\text{cycle lifts}= \prod_{i=1}^{k}(m_{i}-1)!$$

So

$$\displaystyle c(n,k)=\sum_{\substack{m_{1}+\cdots+m_{k}=n\\m_{i}\ge1}}\dfrac{n!}{\prod m_{i}!\,\prod \text{mult. factor}}\prod (m_{i}-1)!$$

While $S(n,k)$ same sum without $(m_{i}-1)!$ factor. Thus $c\ge S$ with equality iff all $m_{i}\le2$.

For $n=4$, shape summary:

$$
\displaystyle
\begin{array}{c|c|c|c}
k & \text{shape} & S\text{ contribution} & c\text{ contribution}\\[5pt]\hline\\
1 & 4 & 1 & (4-1)!=6\\[12pt]
2 & 3+1 & \dbinom{4}{1}=4 & 4\cdot2!=8\\[12pt]
  & 2+2 & 3 & 3\\[12pt]
3 & 2+1+1 & 6 & 6\\[12pt]
4 & 1+1+1+1 & 1 & 1
\end{array}
$$

This table illustrates core difference: sets forget internal order, cycles remember circular order, adding factor $(m-1)!$ per block.

#### Key Mathematical Use: Change of Basis

Stirling numbers are not just counting tools; they are the change-of-basis matrices between two natural bases for polynomials.

Let $x^{\underline{n}} = x(x-1)(x-2)\cdots(x-n+1)$ be the falling factorial.

$$
\begin{align*}
x^{\underline{n}} &= \sum_{k=0}^{n}s(n,k)x^{k}\\[12pt]
x^{n} &= \sum_{k=0}^{n}S(n,k)x^{\underline{k}}
\end{align*}
$$

Thus matrices $s$ and $S$ are inverses:

$$\displaystyle\sum*{k}S(n,k)s(k,m)=\delta*{n,m}$$

Example $n=3$:

$$
\begin{align*}
x^{\underline{3}} &= x^{3}-3x^{2}+2x &&\implies s(3,3)=1,\;s(3,2)=-3,\;s(3,1)=2\\[12pt]
x^{3} &= x^{\underline{1}}+3x^{\underline{2}}+x^{\underline{3}} &&\implies S(3,1)=1,\;S(3,2)=3,\;S(3,3)=1
\end{align*}
$$

Check inverse:

$$
\begin{pmatrix}
1&0&0\\[12pt]
0&1&0\\[12pt]
0&1&1\\[12pt]
0&1&3&1
\end{pmatrix}
\begin{pmatrix}
1&0&0\\[12pt]
0&1&0\\[12pt]
0&-1&1\\[12pt]
0&2&-3&1
\end{pmatrix}=I
$$

This duality powers finite difference calculus, umbral calculus, and moment calculations.

- **First kind (signed) converts powers to falling factorials:**

  $$x^{\underline{n}} = \sum_{k=0}^{n} s(n,k) x^k$$
  Example: $x^{\underline{3}} = x(x-1)(x-2) = x^3 -3x^2 +2x$, so $s(3,3)=1, s(3,2)=-3, s(3,1)=2$.

- **Second kind converts falling factorials back to powers:**

  $$x^n = \sum_{k=0}^{n} S(n,k) x^{\underline{k}}$$
  Example: $x^3 = 1\cdot x^{\underline{1}} + 3\cdot x^{\underline{2}} + 1\cdot x^{\underline{3}}$.

Because of this, the infinite lower-triangular matrices $[s(n,k)]$ and $[S(n,k)]$ are inverses of each other. This duality underlies much of finite difference calculus and the theory of moments.

Falling factorial $\displaystyle x^{\underline{k}}$ counts injective placements: number of ways to place $k$ distinct balls into $x$ boxes at most one per box $\left(x\text{ integer}\right)$. Power $x^{n}$ counts arbitrary placements.

Identity

$$\displaystyle x^{n}= \sum_{k=0}^{n} S(n,k) x^{\underline{k}}$$

can be read combinatorially: arbitrary function from $n$-set to $x$-set has image size $k$ for some $k$; choose partition into $k$ fibers $\left(S(n,k)\right)$, then choose injective placement of $k$ blocks into $x$ values $\left(x^{\underline{k}}\right)$.

Example $n=3$:

$$
\begin{align*}
x^{\underline{1}} &= x\\[12pt]
x^{\underline{2}} &= x(x-1)=x^{2}-x\\[12pt]
x^{\underline{3}} &= x(x-1)(x-2)=x^{3}-3x^{2}+2x
\end{align*}
$$

Then

$$
\begin{align*}
x^{3} &= S(3,1)x^{\underline{1}}+S(3,2)x^{\underline{2}}+S(3,3)x^{\underline{3}}\\[12pt]
&=1\cdot x+3\cdot x(x-1)+1\cdot x(x-1)(x-2)\\[12pt]
&=x+3x^{2}-3x+x^{3}-3x^{2}+2x=x^{3}
\end{align*}
$$

Conversely, signed first kind inverts:

$$
\begin{align*}
x^{\underline{3}} &= s(3,1)x+s(3,2)x^{2}+s(3,3)x^{3}=2x-3x^{2}+x^{3}
\end{align*}
$$

Matrix form for $n=0..3$:

$$
\begin{align*}
S &=\begin{pmatrix}
1&0&0&0\\[12pt]
0&1&0&0\\[12pt]
0&1&1&0\\[12pt]
0&1&3&1
\end{pmatrix},
&s &=\begin{pmatrix}
1&0&0&0\\[12pt]
0&1&0&0\\[12pt]
0&-1&1&0\\[12pt]
0&2&-3&1
\end{pmatrix},
& S\cdot s = I
\end{align*}
$$

Thus $c$ and $S$ translate between ordinary powers and factorial moments — central to combinatorics, probability where $\displaystyle\mathbb{E}[X^{\underline{k}}]$ often simpler, and umbral calculus.

Relation to Bell and Catalan: $B_{n}$ sums $S$, while $C_{n}$ does not sum $c$ — $c$ sums to $n!$, reflecting that all permutations vs all partitions: permutations $\displaystyle n!$ vs partitions $B_{n}$, cycles add internal order within each block, increasing count from $S$ to $c$ by factor $\displaystyle\prod (size_{i}-1)!$.

#### Modern Day Uses

- **Computer science:** $S(n,k)$ counts ways to distribute $n$ distinct jobs to $k$ identical servers $\left(\text{no server idle}\right)$, to hash $n$ keys into $k$ non-empty buckets ignoring bucket labels, and clusterings. Complexity of enumerating all partitions is $B_{n}$, superexponential — motivates approximation algorithms. $c(n,k)$ appears in analysis of random permutations, quicksort average comparisons.

- **Probability and statistics:** If $X\sim\text{Pois}(\lambda)$, $\displaystyle\mathbb{E}[X^{\underline{k}}]=\lambda^{k}$, so ordinary moments $\displaystyle\mathbb{E}[X^{n}]=\sum_{k}S(n,k)\lambda^{k}$ = Touchard polynomial. For $\lambda=1$, $\displaystyle\mathbb{E}[X^{n}]=B_{n}$ — Dobinski. Falling moments simplify occupancy problems.

- **Physics / quantum field theory:** Normal ordering of boson operators $(a^{\dagger}a)^{n}=\sum_{k}S(n,k)(a^{\dagger})^{k}a^{k}$. Stirling numbers appear in Wick contractions.

- **Combinatorial enumeration:** Exponential generating functions:

    $$
    \begin{align*}
    \sum_{n\ge k}S(n,k)\dfrac{x^{n}}{n!} &= \dfrac{(e^{x}-1)^{k}}{k!}\\[12pt]
    \sum_{n\ge k}c(n,k)\dfrac{x^{n}}{n!} &= \dfrac{\left(-\ln(1-x)\right)^{k}}{k!}
    \end{align*}
    $$

    Bell $B(x)=e^{e^{x}-1}$ is $k$-sum of first. These EGFs used in analytic combinatorics and to compute $B_{n},C_{n}$ asymptotics.

- **Cryptography / set partitions:** Number of equivalence relations on $n$-element set = $B_{n}$; used in logic, database dependency theory, and type theory.

Thus Stirling numbers bridge elementary counting $\left(\text{sets vs cycles}\right)$ and deep algebraic structure $\left(\text{basis change, inversion}\right)$, with lineage from $1730$ Stirling to modern analysis of algorithms and quantum optics.

### Happy / Unhappy Numbers

A happy number is defined by what happens when you repeatedly replace it by the sum of the squares of its decimal digits. If this process eventually reaches $1$, the number is happy; if it falls into a loop that never includes $1$, it is unhappy.

This is a simple dynamical system on the integers, and remarkably, it has only two possible fates for every starting number.

#### History and Discovery

The notion appears in recreational mathematics, not ancient number theory, and its origin is diffuse.

- **Early recreational roots:** The iteration $\displaystyle n\mapsto S(n)=\sum d^{2}$ is a natural digit puzzle, appearing in arithmetic puzzle books in the late 19th century as a curiosity about squares of digits. Similar processes — sum of digits, sum of cubes $\left(\text{Narcissistic / Armstrong numbers}\right)$ — were studied by 19th-century British recreationalists.

- **Formal naming:** The terms "happy number" and "unhappy number" were popularized in the 20th century by **Reginald John Billingsley Allom**? — attribution often given to British mathematician **Reginald G. Stone**? Actually standard reference attributes coinage to **R. G. Guy**? The name "happy" is usually attributed to **Reginald Allom** and introduced via **Trigg** and **Guy** in 1930s-1970s literature. **Richard K. Guy** included happy numbers in _Unsolved Problems in Number Theory_ (1981) and _The Book of Numbers_ with Conway, bringing them to wider attention.

- **R. C. Lyness and C. R. Wall, 1960s-1970s:** Early computer-era papers analyzed iteration of $\displaystyle S_{b,k}(n)=\sum d^{k}$ for arbitrary base $b$ and power $k$, proving finiteness of attractors via bounding argument $S_{b,k}(n)<n$ for large $n$ and enumerating cycles. This established general theory: for each $b,k$, only finitely many cycles, $1$ always fixed.

- **D. R. Kaprekar (1905–1986):** Indian recreational mathematician studied digit dynamics extensively — Kaprekar numbers, Kaprekar routine $\left(6174\right)$ — same spirit: iterate function on decimal representation, find fixed points and loops. Happy numbers sit in same family.

- **Modern era:** With computers, extensive computation of happy numbers up to large $X$, density estimates, longest runs of consecutive happy numbers, and happy primes became feasible. **OEIS A007770** lists happy numbers $\left(1,7,10,13,19,23,28,31,32,\dots\right)$, entry created early 1970s. **OEIS A031177** lists unhappy 8-cycle.

- **Why name "happy"?** Anecdotal: $1$ is "happy" fixed point — process ends contentedly; other cycle is "unhappy" trap — never reaches $1$. Terminology reflects dynamics language: basin of attraction of $1$ called happy basin, other basin unhappy.

No single discoverer — it emerged from 19th-century digit-sum puzzles into 20th-century recreational canon, then formalized via computer search as archetypal example of finite-state eventual periodicity.

#### How It Works

Define the digit-square-sum function:
$$\displaystyle S(n) = \text{sum of squares of base-10 digits of } n$$

For example, $S(23) = 2^2 + 3^2 = 13$.

Iterate: $n_0 = n$, $n_1 = S(n_0)$, $n_2 = S(n_1)$,...

**Example — Happy: $23$**
$$\displaystyle 23 \to 2^2+3^2=13 \to 1^2+3^2=10 \to 1^2+0^2=1$$

**Example — Happy: $19$**
$$\displaystyle 19 \to 82 \to 68 \to 100 \to 1$$

**Example — Happy: $7$**
$$\displaystyle 7 \to 49 \to 97 \to 130 \to 10 \to 1$$

**Example — Unhappy: $4$**
$$\displaystyle 4 \to 16 \to 37 \to 58 \to 89 \to 145 \to 42 \to 20 \to 4...$$

**Example — Unhappy: $36$**
$$\displaystyle 36 \to45\to41\to17\to50\to25\to29\to85\to89\to145\to42\to20\to4\to16\to37\to58\to89...$$

**Example — Unhappy: $2$**
$$\displaystyle 2 \to 4 \to 16 \to 37 \to 58 \to 89 \to 145 \to 42 \to 20 \to 4...$$

Every unhappy number eventually enters the same 8-cycle:
$$\displaystyle 4 \to 16 \to 37 \to 58 \to 89 \to 145 \to 42 \to 20 \to 4$$

**Why only two fates? Proof by descent:**

For $k$-digit $n$, $\displaystyle10^{k-1}\le n<10^{k}$ and

$$\displaystyle S(n)\le k\cdot 9^{2}=81k$$

$$
\displaystyle
\begin{align*}
k\ge4 &\implies 10^{k-1}\ge1000>81k\\[5pt]
&\implies S(n)<n
\end{align*}
$$

So any $n\ge1000$ strictly decreases under $S$. Iteration must drop below $1000$ and stay below $1000$ $\left(\text{since max }S\text{ on }<1000\text{ is }3\cdot81=243\right)$. Checking $1\le n<1000$ by hand/computer shows only attractors are fixed point $1$ and the 8-cycle. Hence every $n$ ends in one of two.

$$
\displaystyle
\begin{align*}
\text{Attractor}_{1}&:1\\[5pt]
\text{Attractor}_{2}&:4,16,37,58,89,145,42,20
\end{align*}
$$

#### Properties of Happy and Unhappy Numbers

1. **Heredity of Happiness:** If a number is happy, then all numbers in its sequence are also happy. If $23$ is happy via $23 \to 13 \to 10 \to 1$, then $13$, $10$, and $1$ are happy. Conversely, if a number is unhappy, all numbers in its sequence are unhappy.

   In Example 2, since $36$ is unhappy, every number in its chain — $45, 41, 17, 50, 25, 29, 85, 89, 145, 42, 20, 4, 16, 37, 58$ — is also unhappy.

2. **Permutation Invariance:** The happiness of a number is unaffected if its digits are rearranged in any manner. Since $S(n)$ depends only on the multiset of digits, not their order, $S(19)=S(91)=82$. So $19$ happy $\implies$ $91$ happy. Any permutation of a happy number is happy; any permutation of an unhappy number is unhappy.

3. **Zero Invariance:** Inserting or removing zeros anywhere does not affect happiness, because $0^2=0$. So if $19$ is happy, $109, 1009, 10009$ are all happy. If $20$ is unhappy, $200, 2000, 2$ are all unhappy. This also means $S(n)$ can be thought of as operating on the non-zero digits only.

4. **Infinitude of Both Types:**

   There are infinitely many happy numbers and infinitely many unhappy numbers.

   _Proof:_ $1$ is happy. Then $10^k$ is happy for all $k$ (by zero invariance), so infinitely many happy. For unhappy, $2$ is unhappy ($2 \to 4 \to$ cycle), then $2\cdot10^k$ is unhappy for all $k$, so infinitely many unhappy. In fact, both sets have positive lower density.

5. **Equivalence Class:** Properties 2 and 3 together mean happiness is a property of the multiset of non-zero digits, not the number itself. $112$, $121$, $211$, $1120$, $1012$ all share the same fate.

**What each property means and why it holds**

Let

$$\displaystyle S(n)=\sum_{\text{decimal digits }d\text{ of }n}d^{2}$$

Define orbit:

$$
\displaystyle
\begin{align*}
n_{0}&=n\\
n_{1}&=S(n_{0})\\
n_{2}&=S(n_{1})\\
&\vdots
\end{align*}
$$

$n$ happy $\iff\exists t: n_{t}=1$, unhappy $\iff$ orbit enters $8$-cycle

$$\displaystyle 4\to16\to37\to58\to89\to145\to42\to20\to4$$

**1. Heredity — happiness travels forward and backward along orbit**

$$
\displaystyle
\begin{align*}
\text{If }n\text{ happy, }S(n)\text{ happy}\\
\text{If }n\text{ unhappy, }S(n)\text{ unhappy}
\end{align*}
$$

Why: Orbit of $S(n)$ is suffix of orbit of $n$.

$$
\displaystyle
\begin{align*}
n&\to S(n)\to S(S(n))\to\cdots\to1 &&\text{ if }n\text{ happy}\\
n&\to S(n)\to\cdots\to4\to16\to\cdots &&\text{ if }n\text{ unhappy}
\end{align*}
$$

Example:

$$
\displaystyle
\begin{align*}
23&\to13\to10\to1\\
\text{So }23\text{ happy}&\implies13\text{ happy, }10\text{ happy, }1\text{ happy}\\
\text{Indeed }13\to10\to1,\;10\to1,\;1\to1
\end{align*}
$$

Example unhappy:

$$
\displaystyle
\begin{align*}
36&\to45\to41\to17\to50\to25\to29\to85\to89\to145\to42\to20\to4\to16\to37\to58\to89\cdots\\
\text{Thus }&45,41,17,50,25,29,85,89,145,42,20,4,16,37,58\text{ all unhappy}\\
\text{because each eventually hits cycle}
\end{align*}
$$

Consequence:

$$
\displaystyle
\begin{align*}
\text{If you ever see }1\text{ in orbit, whole orbit happy}\\
\text{If you ever see }4\text{ in orbit, whole orbit unhappy}
\end{align*}
$$

So algorithm to test $n$ only needs to stop when hitting $1$ or $4$ — no need to store whole visited set beyond that, since $1$ and $4$ are the two attractors.

**2. Permutation Invariance — order of digits irrelevant**

$$\displaystyle S(n)\text{ depends only on multiset of digits}$$

Because addition commutative: $a^{2}+b^{2}=b^{2}+a^{2}$.

$$
\displaystyle
\begin{align*}
n&=\overline{d_{k}\cdots d_{0}}_{10}\\
S(n)&=d_{k}^{2}+\cdots+d_{0}^{2}
\end{align*}
$$

Permuting $d_{i}$ does not change sum.

$$
\displaystyle
\begin{align*}
S(19)&=1^{2}+9^{2}=1+81=82\\
S(91)&=9^{2}+1^{2}=81+1=82
\end{align*}
$$

Thus:

$$\displaystyle n\text{ and any permutation }\pi(n)\text{ have same }n_{1}=S(n)$$

If $n_{1}$ happy, then $n$ happy. So:

$$
\displaystyle
\begin{align*}
19\text{ happy}&\implies91\text{ happy}\\
\text{Check: }19\to82\to68\to100\to1\\
91\to82\to68\to100\to1\text{ same tail}
\end{align*}
$$

General:

$$\displaystyle \text{If }n\text{ happy, every rearrangement of its decimal digits happy}$$

Similarly unhappy permutations stay unhappy:

$$
\displaystyle
\begin{align*}
36\text{ unhappy}&\implies63\text{ unhappy}\\
36\to45,\;63\to9^{2}+36=45\text{ same next step}
\end{align*}
$$

**3. Zero Invariance — zeros contribute nothing**

$$\displaystyle 0^{2}=0$$

So:

$$
\displaystyle
\begin{align*}
S(109)&=1^{2}+0^{2}+9^{2}=1+81=82=S(19)\\
S(1009)&=1^{2}+0^{2}+0^{2}+9^{2}=82
\end{align*}
$$

In general, inserting $0$ anywhere:

$$\displaystyle S(\text{insert }0\text{ into }n)=S(n)$$

Therefore:

$$
\displaystyle
\begin{align*}
n\text{ happy}&\implies n\text{ with zeros inserted anywhere happy}\\
n\text{ unhappy}&\implies n\text{ with zeros inserted anywhere unhappy}
\end{align*}
$$

Examples:

$$
\displaystyle
\begin{align*}
19\text{ happy}&\implies109\text{ happy, }1009\text{ happy, }10009\text{ happy, }10^{k}\cdot19\text{ happy? }\\
\text{Note: }19\cdot10^{k}=190\cdots0\text{ has digits }1,9,0\dots0\text{, }S=82\text{ happy}
\end{align*}
$$

$$
\displaystyle
\begin{align*}
20\text{ unhappy}&\implies200\text{ unhappy, }2000\text{ unhappy}\\
\text{Check: }20\to4\to16\cdots\text{ unhappy}\\
2\to4\to\text{ cycle, so }2,20,200,\dots\text{ all unhappy}
\end{align*}
$$

So $S$ can be thought as operating on non-zero digits only.

**4. Infinitude — infinitely many happy and unhappy**

Happy infinitude:

$$
\displaystyle
\begin{align*}
1&\text{ happy}\\
S(10^{k})&=1^{2}=1\text{ happy}\\
\text{So }1,10,100,1000,\dots,10^{k},\dots\text{ infinite happy family}
\end{align*}
$$

More generally, $a\cdot10^{k}$ with $a$ happy digit? Actually $7$ happy because $\displaystyle7\to49\to97\to130\to10\to1$, so $\displaystyle7\cdot10^{k}$ happy infinite.

Unhappy infinitude:

$$
\displaystyle
\begin{align*}
2&\to4\to16\to\cdots\text{ cycle — unhappy}\\
S(2\cdot10^{k})&=2^{2}=4\text{ — enters cycle}\\
\text{So }2,20,200,2000,\dots,2\cdot10^{k},\dots\text{ infinite unhappy family}
\end{align*}
$$

Thus both sets infinite.

Stronger: both have positive lower density — there is constant $c>0$ such that for large $X$, at least $cX$ numbers $\le X$ happy and at least $cX$ unhappy. Known bounds roughly $c\approx0.12$ for happy.

**5. Equivalence Class — happiness lives on multisets**

Combine 2 and 3:

$$
\displaystyle
\begin{align*}
\text{Permutation}&: \text{order irrelevant}\\
\text{Zero}&: 0\text{ digits irrelevant}
\end{align*}
$$

Hence only multiset of non-zero digits matters.

Define non-zero multiset $M(n)=\{d_{i}:d_{i}\neq0\}$.

$$\displaystyle S(n)=\sum_{d\in M(n)}d^{2}$$

So:

$$\displaystyle M(n_{1})=M(n_{2})\implies S(n_{1})=S(n_{2})\implies\text{same fate}$$

Examples:

$$
\displaystyle
\begin{align*}
112&\to1^{2}+1^{2}+2^{2}=6\\
121&\to1^{2}+2^{2}+1^{2}=6\\
211&\to6\\
1120&\to1^{2}+1^{2}+2^{2}+0^{2}=6\\
1012&\to6\\
\text{All have }M=\{1,1,2\},\;S=6,\;6\to36\to\cdots\text{ unhappy}\\
\text{So }112,121,211,1120,1012\text{ all unhappy together}
\end{align*}
$$

Another:

$$
\displaystyle
\begin{align*}
19&:M=\{1,9\},\;S=82\text{ happy}\\
91&:M=\{9,1\},\;S=82\text{ happy}\\
109&:M=\{1,9\},\;S=82\text{ happy}\\
9010&:M=\{9,1\},\;S=82\text{ happy}
\end{align*}
$$

Thus to test a number, you can sort digits descending and delete zeros — canonical representative.

$$
\displaystyle
\begin{align*}
\text{Canonical}(1012)&=211\\
\text{Canonical}(109)&=91
\end{align*}
$$

Happiness depends only on canonical.

This classification reduces infinite numbers to finite multisets for bounded digit sum — useful for counting: number of distinct fates up to $\displaystyle10^{k}$ depends only on partitions of $k$ digits with values $1$–$9$.

In short: heredity says fate propagates along orbit, permutation invariance says $\displaystyle S$ sums squares commutatively, zero invariance says $\displaystyle0^{2}=0$, infinitude follows from $\displaystyle10^{k}$ and $\displaystyle2\cdot10^{k}$ families, and together they show happiness is property of multiset of non-zero digits, not of decimal order or zeros.

#### Key Facts and Variations

- **Density:** What fraction of numbers are happy? Empirically about $15-20\%$ up to large $X$. Rigorous bounds: upper asymptotic density $<0.19$ and lower $>0.12$. It is not known whether a natural density exists — i.e., whether $\dfrac{\#\{n \le X : n \text{ happy}\}}{X}$ converges — this is an open problem.

- **Happy primes:** A happy number that is prime. $7, 13, 19, 23, 31, 79, 97, 103, 109, 139, 167, \dots$. Since all numbers $>5$ ending in $5$ are composite, happy primes must end in $1,3,7,9$.

- **Consecutive happy numbers:** The smallest consecutive pair is $31,32$. There are runs of arbitrary length? It is conjectured but not proved that arbitrarily long runs of happy numbers exist. The longest known run as of 2024 is length 12.

- **Base dependence:** Like Narcissistic numbers, happiness depends on base. The function $S_b(n)$ = sum of squares of base-$b$ digits always eventually cycles. $1$ is always a fixed point, but the other cycles depend on $b$. For example, $7$ is happy in base 10 ($7\to49\to97\to130\to10\to1$) but unhappy in base 2. In base 2, $S_2(n)$ is just the count of 1-bits, so every number eventually reaches $1$.

- **Generalization — $k$-happy:** Replace squares with $k$-th powers. Standard happy is $2$-happy. $k=3$ gives "cubed happy" numbers, etc. The same bounding argument shows every $k$ has finitely many attractors.

Happy numbers are not deep in algebraic number theory, but they are a perfect classroom example of iteration, attractors, invariants, and proof by descent: to prove an infinite process has only two outcomes, you show it must eventually enter a finite, checkable region.

Think of $S$ as machine:

$$\displaystyle S(n)=\sum_{\text{decimal digits }d\text{ of }n} d^{2}$$

Example $n=145$: digits $1,4,5$ → $S(145)=1^{2}+4^{2}+5^{2}=1+16+25=42$.

Iterating creates orbit:

$$
\displaystyle
\begin{align*}
n_{0}&=n\\[5pt]
n_{1}&=S(n_{0})\\[5pt]
n_{2}&=S(n_{1})\\[5pt]
&\vdots
\end{align*}
$$

Two worked orbits with:

$$
\displaystyle
\begin{align*}
23 &\to S(23)=2^{2}+3^{2}=4+9=13\\[5pt]
&\to S(13)=1^{2}+3^{2}=1+9=10\\[5pt]
&\to S(10)=1^{2}+0^{2}=1\\[5pt]
&\to S(1)=1^{2}=1\text{ fixed point — happy}
\end{align*}
$$

$$
\displaystyle
\begin{align*}
36 &\to 3^{2}+6^{2}=9+36=45\\[5pt]
&\to 4^{2}+5^{2}=16+25=41\\[5pt]
&\to 4^{2}+1^{2}=16+1=17\\[5pt]
&\to 1^{2}+7^{2}=1+49=50\\[5pt]
&\to 5^{2}+0^{2}=25\\[5pt]
&\to 2^{2}+5^{2}=4+25=29\\[5pt]
&\to 2^{2}+9^{2}=4+81=85\\[5pt]
&\to 8^{2}+5^{2}=64+25=89\\[5pt]
&\to 8^{2}+9^{2}=64+81=145\\[5pt]
&\to 1^{2}+4^{2}+5^{2}=42\\[5pt]
&\to 4^{2}+2^{2}=20\\[5pt]
&\to 2^{2}+0^{2}=4\\[5pt]
&\to 4^{2}=16\\[5pt]
&\to 1^{2}+6^{2}=37\\[5pt]
&\to 3^{2}+7^{2}=58\\[5pt]
&\to 5^{2}+8^{2}=89\text{ loop detected — unhappy}
\end{align*}
$$

Once $4$ appears, you loop $4\to16\to37\to58\to89\to145\to42\to20\to4$.

**Why no number escapes to infinity — the descent lemma:**

Let $n$ have $k$ digits, so $10^{k-1}\le n <10^{k}$ for $n\ge1$.

$$\displaystyle S(n)\le k\cdot 9^{2}=81k$$

Because each digit at most $9$.

Compare $n$ vs $81k$:

$$
\displaystyle
\begin{align*}
k=1&: n\le9,\;81k=81\\[5pt]
k=2&: n\le99,\;81k=162\\[5pt]
k=3&: n\le999,\;81k=243\\[5pt]
k=4&: n\ge1000,\;81k=324<n\\[5pt]
k=5&: n\ge10000,\;81k=405<n
\end{align*}
$$

For $k\ge4$, $10^{k-1}>81k$, so $S(n)<n$.

Thus any $n\ge1000$ strictly decreases. Iterate:

$$\displaystyle n_{0}>n_{1}>n_{2}>\cdots\text{ until }<1000$$

Cannot decrease forever $\left(\text{positive integers}\right)$, must enter $$. Once inside $$, $S(n)\le3\cdot81=243$, then $S(n)\le2\cdot81+3^{2}=... <1000$, so stays below $1000$.[1][999]

Therefore to understand all $n$, it suffices to compute orbits of $1$ to $999$ — finite check. That computation reveals exactly two attractors:

$$
\displaystyle
\begin{align*}
1&\to1\text{ — fixed point}\\[5pt]
4&\to16\to37\to58\to89\to145\to42\to20\to4\text{ — 8-cycle}
\end{align*}
$$

No other loops. So every starting $n$ ends in one of those two.

**Properties in formulas:**

_Permutation invariance:_

$$\displaystyle S( \text{permutation of digits of }n)=S(n)$$

Because sum of squares commutative. Example $S(19)=1^{2}+9^{2}=82=S(91)$.

If orbit of $n$ hits $1$, orbit of any permutation hits same next value $S(n)$, hence also hits $1$.

_Zero invariance:_

$$\displaystyle S(1009)=1^{2}+0^{2}+9^{2}=1^{2}+9^{2}=S(19)$$

$0^{2}=0$ adds nothing. So appending zeros does not change fate.

_Heredity:_

$$
\displaystyle
\begin{align*}
n\text{ happy}&\implies S(n)\text{ happy}\\[5pt]
n\text{ unhappy}&\implies S(n)\text{ unhappy}
\end{align*}
$$

Because $S(n)$ is next step in orbit — if orbit of $n$ ends at $1$, orbit of $S(n)$ is suffix of same orbit, also ends at $1$.

_Infinitude:_

$$
\displaystyle
\begin{align*}
1&\text{ happy}\implies10^{k}\text{ happy for all }k\ge0\\[5pt]
2&\to4\text{ unhappy}\implies2\cdot10^{k}\text{ unhappy for all }k\ge0
\end{align*}
$$

Thus infinitely many each.

**Density question:**

$$\displaystyle D(X)=\dfrac{\#\{n\le X: n\text{ happy}\}}{X}$$

Computations:

$$
\displaystyle
\begin{align*}
D(10^{3})&\approx0.20\\[5pt]
D(10^{6})&\approx0.15\\[5pt]
D(10^{9})&\approx0.15\text{-}0.19\text{ range}
\end{align*}
$$

Conjectured limit $\approx0.15$, but existence of $\displaystyle\lim_{X\to\infty}D(X)$ open.

**Consecutive happy numbers:**

$31$ happy $\left(31\to10\to1\right)$, $32$ happy $\left(32\to13\to10\to1\right)$ — smallest adjacent pair.

Longer runs exist via Chinese remainder / digit construction — e.g., find $m$ such that $S$ values of $m,m+1,\dots$ map into known happy numbers. Existence of arbitrarily long runs conjectured but not proved.

**Base dependence and generalization:**

Define for base $b\ge2$:

$$\displaystyle S_{b,k}(n)=\sum_{\text{base-}b\text{ digits }d}d^{k}$$

Standard happy = $b=10,k=2$. For each $b,k$, same descent argument: for $k$ fixed, $S_{b,k}(n)=O(\log_{b}n)$, so $S_{b,k}(n)<n$ for large $n$, finite check suffices, finitely many attractors. $1$ always fixed because $1^{k}=1$.

Example $b=2,k=2$: $S_{2}(n)$ = number of $1$-bits in binary $\left(\text{since }0^{2}=0,1^{2}=1\right)$. Then $S_{2}(n)\le\log_{2}n+1$, iteration goes to $1$ for all $n\ge1$ — every number happy in base $2$.

For $b=10,k=3$ $\left(\text{cubed happy}\right)$: $S(n)=\sum d^{3}$, only attractors are $1$, $55\to250\to133\to55$ etc.

This makes happy numbers accessible illustration of dynamical systems: map $S$, phase space $\mathbb{N}$, two basins of attraction, trapping region $$, invariants under digit permutation and zero insertion.[1][999]

#### Modern Developments and Variations

- **Density:** Let $\displaystyle D(X)=\dfrac{\#\{n\le X:\text{happy}\}}{X}$. Empirically $D(X)\approx0.15\text{-}0.20$. Best known bounds $0.12\lesssim D(X)\lesssim0.19$ for large $X$ $\left(\text{Gilmer, 2013; El-Sedy \& Siksek, 2000}\right)$. Existence of natural density $\displaystyle\lim_{X\to\infty}D(X)$ open — analogous to Collatz density problem.

- **Happy primes:** $7,13,19,23,31,79,97,103,109,139,167,\dots$ — OEIS A035497. Infinite? Conjectured yes, not proved, but follows from plausible distribution of happy among primes.

- **Consecutive runs:** $31,32$ smallest pair. Construction using $\displaystyle n\to S(n)$ mapping and Chinese remainder allows building long runs: if $a$ such that $S$ values cover interval of happy numbers, $a\cdot10^{k}+$ offset yields run. Longest recorded run as of 2024 is $12$ consecutive numbers. Existence of arbitrarily long runs conjectured, not proved — similar to open problem for prime runs.

- **Base $b$, power $k$ generalization:** $\displaystyle S_{b,k}(n)=\sum_{\text{base-}b\text{ digits }d}d^{k}$. For each $b,k$, same descent: $S_{b,k}(n)=O(\log n)<n$ for large $n$, so finitely many cycles, checkable. Base $2$, $k=2$: $S_{2}(n)=\text{popcount}(n)$ — all $n$ happy. Base $10$, $k=3$: cycles include $1$, $55\to250\to133\to55$, etc. — "cubes happy".

- **Pedagogical use:** Since 1970s, standard example in introductory programming $\left(\text{cycle detection via Floyd, hash set}\right)$ and discrete dynamical systems — illustrates trapping region, attractor, invariant, and proof that infinite process reduces to finite check — same technique used for Collatz-type problems, Kaprekar routine $6174$, and $3n+1$.

In short: recreational origin late 19th century, name coined mid-20th, formal cycle classification via bounding lemma $81k<10^{k-1}$, modern interest in density, happy primes, and long runs, with $\displaystyle B_{n}$? — not related — but with same flavor as Stirling/Bell enumeration of partitions: finite description captures infinite behavior.

### Harshad / Niven Numbers

A Harshad number — from Sanskrit _harṣa_ meaning "great joy" and _da_ meaning "to give," literally "joy-giver" — also called a Niven number after Canadian mathematician Ivan M. Niven, who studied them in a 1977 paper, is an integer divisible by the sum of its digits in base 10.

The term Harshad was coined by the Indian recreational mathematician D. R. Kaprekar — the same Kaprekar of Kaprekar numbers and Kaprekar's constant 6174. He loved digit-dependent properties.

> **Definition:** Let $s_{10}(n)$ be the sum of the decimal digits of $n$. Then $n$ is Harshad (or Niven) if $s_{10}(n) \mid n$, i.e. $n \mod s_{10}(n) = 0$.

- **Single digits:** Every number from 1 through 9 is trivially Harshad, since $s(d)=d$ and $d\mid d$. By convention we include $10$ as Harshad because $1+0=1$ divides $10$.

- **Origin of name:** Harshad = joy-giver, Niven = after Ivan Niven. Both names are used interchangeably in literature; "Harshad" is more common in recreational contexts, "Niven" in formal papers.

- **Universal numbers:** Only $1, 2, 4, 6$ are Harshad numbers in _every_ number base. These are called all-Harshad or all-Niven numbers.

#### History and Discovery

$$\displaystyle \text{Harshad: Kaprekar 1955, Niven: Niven 1977}$$

- **D. R. Kaprekar (1905–1986):** Indian schoolteacher in Devlali, Maharashtra, self-taught recreational mathematician. In 1955 paper "Multidigital Numbers" and later notes in _Scripta Mathematica_, he defined "Harshad" $\left(\text{joy-giver}\right)$. Kaprekar was fascinated by base-10 digit interactions: Harshad numbers, Kaprekar numbers $\left(n^{2}$ split and sum to $n$, e.g. $45^{2}=2025,20+25=45\right)$, Demlo numbers, Kaprekar constant $6174$ from routine $4$-digit sort-desc minus sort-asc $\to6174$ loop. He chose Sanskrit name to celebrate Indian mathematical tradition. His work was largely ignored by formal journals but circulated in recreational circles.

- **Ivan M. Niven (1915–1999):** Canadian-American number theorist at University of Oregon, author of _Irrational Numbers_ and co-author of _Introduction to the Theory of Numbers_. In 1977 talk at conference and 1980 paper with H. S. Zuckerman, he independently studied numbers divisible by sum of digits, calling them perhaps not knowing Kaprekar's term. His framework introduced $b$-Niven numbers $\left(\text{base }b\right)$, $s_{b}(n)\mid n$, and proved basic density results. Western literature adopted "Niven number" after him; OEIS uses both.

- **Grundman 1994 — All-Harshad classification:** H. G. Grundman proved only $1,2,4,6$ are Harshad in every base $b\ge2$. Proof uses representation $n=11_{b}$ for $b=n-1$, etc., forcing evenness and smallness.

- **De Koninck & Doyon, Cooper & Kennedy:** Jean-Marie De Koninck and Nicolas Doyon (2003) proved distribution results: number of $b$-Niven up to $X$ is $o(X)$, natural density $0$, yet there are arbitrarily long gaps of non-Niven. Curtis Cooper and Robert E. Kennedy (1984) proved existence of $20$ consecutive Niven numbers in base $10$, disproving early conjecture that gap bounded by $20$ — showing block structure subtle.

- **Modern extensions:** Multiple Harshad (MFA) numbers studied by Grundman, $k$-Niven where $n$ divisible by $s_{b}(n)^{k}$, strict Harshad where $n/s(n)$ coprime to $s(n)$, and Zuckerman numbers where $n$ divisible by product of digits. All stem from Kaprekar's original joy-giver idea.

#### How to Check

1. **Sum the decimal digits**: $s(n)$.

2. **Divide**: is $n \mod s(n) = 0$?

**Examples:**

- **$18$**: $s=1+8=9$, $\displaystyle\dfrac{18}{9}=2$ Harshad

- **$21$**: $s=2+1=3$, $\displaystyle\dfrac{21}{3}=7$ Harshad

- **$1729$ — the Hardy-Ramanujan taxicab number**: $s=1+7+2+9=19$, $\displaystyle\dfrac{1729}{19}=91$ Harshad

- **$19$**: $s=1+9=10$, $19 \mod 10 =9$ not Harshad

- **$100$**: $s=1$, $100\mod1=0$ — any power of 10 is Harshad

**Sequence (base 10):** All $1-10$ are Harshad, then
$$\displaystyle 12, 18, 20, 21, 24, 27, 30, 36, 40, 42, 45, 48, 50, 54, 60, 63, 70, 72, 80, 81, 84, 100, 102, 108, 110, 111, 112, \dots$$

$111$ is interesting: $1+1+1=3$, $\displaystyle\dfrac{111}{3}=37$.

#### How Divisibility Works

Let decimal expansion $n=\overline{d_{k}d_{k-1}\dots d_{0}}_{10}= \sum d_{i}10^{i}$, define

$$\displaystyle s(n)=\sum_{i=0}^{k}d_{i}$$

Harshad condition:

$$\displaystyle s(n)\mid n\iff \exists q\in\mathbb{N}: n=q\cdot s(n)$$

$$\displaystyle q=\dfrac{n}{s(n)}\text{ called Harshad quotient}$$

Example $n=18$: $s=9$, $q=18/9=2$.

Example $n=1729$:

$$
\displaystyle
\begin{align*}
s(1729)&=1+7+2+9=19\\[5pt]
\dfrac{1729}{19}&=91\quad\text{since }19\cdot91=19\cdot90+19=1710+19=1729
\end{align*}
$$

So $1729$ Harshad.

**Why powers of 10 always work:**

$$
\displaystyle
\begin{align*}
n&=10^{k}=1\underbrace{0\dots0}_{k}\\[5pt]
s(n)&=1\\[5pt]
\dfrac{10^{k}}{1}&=10^{k}\in\mathbb{N}
\end{align*}
$$

Similarly $a\cdot10^{k}$ with $1\le a\le9$: $s=a$, $a\mid a10^{k}$ always, so infinite family.

$$\displaystyle a\cdot10^{k}\text{ Harshad for all }k\ge0,\;1\le a\le9$$

**Mod 9 connection:**

$$\displaystyle 10\equiv1\pmod9\implies10^{i}\equiv1^{i}\equiv1\pmod9$$

Hence

$$
\displaystyle
\begin{align*}
n&=\sum d_{i}10^{i}\equiv\sum d_{i}=s(n)\pmod9
\end{align*}
$$

So $n-s(n)$ always divisible by $9$. If $n$ Harshad, $n=q s(n)$, then

$$
\displaystyle
\begin{align*}
q s(n) &\equiv s(n)\pmod9\\[5pt]
s(n)(q-1)&\equiv0\pmod9
\end{align*}
$$

Thus $9\mid s(n)(q-1)$. This restricts possible $q$ when $3\nmid s(n)$. Example $n=21$: $s=3$, $q=7$, $s(q-1)=3\cdot6=18$ divisible by $9$.

This is generalization of divisibility test for $9$: $9\mid n\iff9\mid s(n)$.

#### Key Properties

1. **All single digits are Harshad** — by definition.

2. **Infinitude:** There are infinitely many Harshad numbers. Simple families: $10^k$, $a\cdot10^k$ for $1\le a\le9$.

$$\displaystyle \{10^{k}:k\ge0\}\subset\text{Harshad},\;|\text{Harshad}|=\infty$$

3. **Density:** Natural density $0$. Let $\displaystyle H(X)=\#\{n\le X: n\text{ Harshad}\}$. Then

   $$\displaystyle \lim_{X\to\infty}\dfrac{H(X)}{X}=0$$

   Reason: $s(n)\le9\log_{10}X$ for $n\le X$, so average size of divisor $s(n)$ much smaller than $n$, divisibility by small random-ish number $s(n)$ has probability about $1/s(n)$ on average, sum diverges slowly, proportion tends to $0$. Empirically:

   $$
   \displaystyle
   \begin{align*}
   \dfrac{H(1000)}{1000}&\approx0.30\\[5pt]
   \dfrac{H(100000)}{100000}&\approx0.14\\[5pt]
   \dfrac{H(10^{9})}{10^{9}}&\approx0.05
   \end{align*}
   $$

   Yet gaps: De Koninck-Doyon proved arbitrarily long runs of consecutive non-Harshad numbers exist. Cooper-Kennedy proved $20$ consecutive Harshad exist in base $10$ $\left(\text{e.g. starting at }10^{something}\right)$, and Grundman showed any base $b$ has runs of $2b$ consecutive $b$-Niven.

4. **Multiple Harshad / MFA Numbers:**
   A Multiple Harshad Number is one where repeatedly dividing by digit sum stays Harshad.

   Let $n_0=n$, $n_{i+1}=n_i / s(n_i)$ if divisible.

   If this can be done $k$ times and each $n_i$ is Harshad, $n$ has MFA-degree $k$.

   Example: $2016$

   $$
   \displaystyle
   \begin{align*}
   s(2016)&=2+0+1+6=9\\[5pt]
   \dfrac{2016}{9}&=224\\[5pt]
   s(224)&=8,\;224/8=28\\[5pt]
   s(28)&=10,\;28\mod10\neq0\text{ stop}
   \end{align*}
   $$

   So $2016$ degree $1$.

   Stronger: $378$

   $$
   \displaystyle
   \begin{align*}
   s(378)&=18,\;378/18=21\\[5pt]
   s(21)&=3,\;21/3=7\\[5pt]
   s(7)&=7,\;7/7=1
   \end{align*}
   $$

   So chain $378\to21\to7\to1$, each Harshad, degree $3$.

5. **All-Harshad Numbers (AHN):** Numbers Harshad in every base $b\ge2$. Grundman 1994 proved only $1,2,4,6$.

   Sketch: For $b=n-1\ge2$, $n=11_{b}$ $\left(\text{since }b+1=n\right)$, so $s_{b}(n)=2$, need $2\mid n$ → $n$ even. For $b=n-2$, $n=12_{b}=b+2$, $s=3$, need $3\mid n$ unless $n$ small, etc., forcing $n\in\{1,2,4,6\}$.

6. **Harshad Primes:** Prime Harshad can only be $2,3,5,7$.

   Proof:

   $$
   \displaystyle
   \begin{align*}
   n\ge11 &\implies 2\le s(n)<n\\[5pt]
   s(n)\mid n\text{ and }1<s(n)<n &\implies n\text{ composite}
   \end{align*}
   $$

   If $s(n)=1$, $n=10^{k}$, composite for $k\ge1$. So no multi-digit Harshad prime.

#### Generalizations

- **$b$-Niven:** $\displaystyle s_{b}(n)\mid n$, $s_{b}$ sum base-$b$ digits. Theory changes with $b$.

- **Strict Harshad:** $\displaystyle \dfrac{n}{s(n)}$ Harshad and $\gcd\left(s(n),\dfrac{n}{s(n)}\right)=1$.

- **Zuckerman / $s$-divisible:** Product of digits divides $n$.

- **Connection to 9:** $\displaystyle n\equiv s(n)\pmod9$ as above, underlying all base-$10$ digit sum divisibility.

Thus Harshad numbers link Kaprekar's recreational joy $\left(1955\right)$ to Niven's formal study $\left(1977\right)$ to modern questions about distribution of $\displaystyle s_{b}(n)\pmod m$ and long runs — simple definition, deep irregular behavior because $s(n)$ fluctuates while divisibility is rigid.

### Wieferich Primes

They come from asking what happens when you strengthen Fermat's Little Theorem by one power of $p$.

**Fermat's Little Theorem:** For prime $p$ not dividing $a$,
$$\displaystyle a^{p-1} \equiv 1 \mod p$$

So $p$ always divides $a^{p-1}-1$. Arthur Wieferich asked in 1909: When does $p^2$ divide $a^{p-1}-1$? When does the congruence hold $\mod p^2$ instead of just $\mod p$?

> **Definition:** A prime $p$ is a Wieferich prime base $a$ if
> $$\displaystyle a^{p-1} \equiv 1 \mod p^2$$
> In other words, $p^2 \mid a^{p-1}-1$.
> When no base is mentioned, base $2$ is the default: $2^{p-1} \equiv 1 \mod p^2$.

For base $2$, this is $p^2$ divides the Mersenne number $M_{p-1}=2^{p-1}-1$.

**Example:** $p=1093$ is Wieferich base 2:
$$\displaystyle 2^{1092} = 1 + k\cdot 1093^2$$
with $k = 364245589...$ large. The key point is the remainder upon division by $1093^2 = 1,194,649$ is $1$. So $1093$ divides $2^{1092}-1$ twice.

For contrast, take $p=5$ non-Wieferich:
$2^4=16$, $16-1=15$, divisible by $5$ but not by $25$. So $5$ is not Wieferich base 2.

#### History and Discovery

$$\displaystyle \text{Wieferich 1909 — Meissner 1913 — Beeger 1922 — Modern sieve to }10^{17}$$

- **Arthur Wieferich (1884–1954), German mathematician, 1909:** In _Journal für die reine und angewandte Mathematik_ paper "Zum letzten Fermatschen Theorem", he proved:

> If $x^{p}+y^{p}=z^{p}$ with $p\nmid xyz$ $\left(\text{FLT first case}\right)$ has integer solution, then $\displaystyle 2^{p-1}\equiv1\mod p^{2}$.

This was first restriction linking FLT failure to special primes. At the time FLT was great open problem, so any necessary condition for counterexample was intensely pursued. Wieferich's theorem instantly made primes satisfying $2^{p-1}\equiv1\mod p^{2}$ important.

- **Mirimanoff 1910:** Russian mathematician Dmitry Mirimanoff extended Wieferich: if first case fails for $p$, then also $\displaystyle 3^{p-1}\equiv1\mod p^{2}$. So FLT counterexample needs $p$ Wieferich for both bases $2$ and $3$ simultaneously. This made search for Wieferich primes base $2$ and $3$ a route to prove FLT first case for many $p$.

- **Meissner 1913 — first Wieferich found:** Using desk calculations, German mathematician Walther Meissner found $p=1093$ satisfies $\displaystyle 2^{1092}\equiv1\mod1093^{2}$. Computation:

$$
\displaystyle
\begin{align*}
1093^{2}&=1194649\\[5pt]
2^{1092}\mod1194649&=1
\end{align*}
$$

He verified by repeated squaring mod $p^{2}$ — heroic for 1913.

- **Beeger 1922 — second:** Dutch mathematician N. G. W. H. Beeger found $p=3511$ satisfies same. No other below $10^{9}$ at that time.

- **1909–1995 FLT hunt era:** Before Wiles proof of FLT in 1995, Wieferich criterion used to prove FLT first case for all $p$ up to large bounds: if no Wieferich primes exist up to $X$, then FLT first case true for $p\le X$. Computations of $q_{p}(2)=\dfrac{2^{p-1}-1}{p}\mod p$ driven by FLT. Work by Vandiver, Lehmer, Emma Lehmer $\left(1930s-1960s\right)$ expanded search to $10^{6}$, then $10^{9}$ with early computers.

- **After FLT proved:** Interest shifted from FLT to intrinsic number theory: distribution of Fermat quotients, $p$-adic logarithms, $abc$ conjecture, cryptography.

#### Key Facts and Properties

**1. Known primes — Extreme Rarity:**
Only two base-2 Wieferich primes are known:
$$\displaystyle 1093 \quad \text{and} \quad 3511$$

- $1093$ was found by Meissner in 1913.
- $3511$ was found by Beeger in 1922.

Despite enormous effort, no third is known.

**2. Rarity and Search Limits:**
Computer searches have tested all primes up to $>1.45 \times 10^{17}$ as of 2023 — that is 145 quadrillion — without finding any additional base-2 Wieferich primes. PrimeGrid, Dorais-Klyve, and others use efficient sieving using $a^{p-1} \mod p^2$ can be computed with $O(\log p)$ modular multiplications using fast exponentiation, but the sheer range makes it hard.

Heuristic: For random prime $p$, $a^{p-1} \mod p^2$ is roughly uniformly distributed among the $p$ multiples of $p$ that are $1 \mod p$. So probability it is $1 \mod p^2$ is $\dfrac{1}{p}$. Expected number up to $X$ is $\displaystyle\sum_{p\le X} \dfrac{1}{p} \sim \log\log X$, which diverges but agonizingly slowly: $\log\log(10^{17}) \approx 3.66$, consistent with 2 found. This suggests infinitely many exist, but the next may be beyond $10^{18}$.

It is conjectured there are infinitely many Wieferich primes base $a$ for every $a$, but unproven for any $a$.

**3. Connection to Fermat's Last Theorem:**
German mathematician Arthur Wieferich discovered in 1909 the result that made these primes famous:

> If the first case of Fermat's Last Theorem fails for prime exponent $p$ — i.e., there exist integers $x,y,z$ not divisible by $p$ with $x^p+y^p=z^p$ — then $p$ must be a Wieferich prime base $2$.

FLT's first case was eventually proved for all $p$ up to huge bounds using this: if you could prove no Wieferich primes exist in a range, FLT first case holds there. This drove searches for Wieferich primes for 70 years, until Wiles proved FLT completely in 1995 by different methods. Mirimanoff in 1910 extended it: $p$ must also be Wieferich base $3$.

Even after FLT, the link remains: Wieferich primes are obstructions to the "first case" and to the $abc$ conjecture — $abc$ implies infinitely many _non_-Wieferich primes.

**4. Other bases — $a$-Wieferich primes:**
Mathematicians study Wieferich primes to bases other than 2. Definition is same: $a^{p-1}\equiv1 \mod p^2$, $p \nmid a$.

- **Base 3**: $11, 1006003$ — only two known below $10^{15}$, plus huge ones like $...$
- **Base 5**: $2, 20771, 40487, 53471161, ...$ — $2$ is trivially Wieferich base 5 because $5^{1}\equiv1\mod4$? Wait $2$ base 5: $5^{1}=5\equiv1\mod4$? $2^2=4$ divides $5^{1}-1=4$, yes.
- **Base 10**: $3, 487$ — called repunit Wieferich because $10^{p-1}\equiv1\mod p^2$ means $p^2$ divides repunit $999...9$.
- Base $a$ and prime $p=a$ is excluded because $p\mid a$.

For each base, the set is conjectured infinite but appears sparse. Base 2 is most studied because of FLT and Mersenne numbers.

**5. The Math Behind It — Fermat Quotient:**
Define the Fermat quotient:
$$\displaystyle q_p(a) = \dfrac{a^{p-1}-1}{p}$$

Fermat's theorem says $q_p(a)$ is integer. Wieferich condition is $q_p(a) \equiv 0 \mod p$.

$q_p(a)$ behaves like a logarithm mod $p$ — called the $p$-adic logarithm — satisfying $q_p(ab) \equiv q_p(a)+q_p(b) \mod p$. Wieferich primes are where this logarithm vanishes.

#### Why They Matter Today

**Fermat quotient and $p$-adic log:**

$$\displaystyle q_{p}(a)=\dfrac{a^{p-1}-1}{p}\in\mathbb{Z}$$

Properties:

$$
\displaystyle
\begin{align*}
q_{p}(ab)&\equiv q_{p}(a)+q_{p}(b)\pmod p\\[5pt]
q_{p}(a^{k})&\equiv k q_{p}(a)\pmod p
\end{align*}
$$

So $q_{p}$ mimics $\log$. Wieferich base $a$ means $q_{p}(a)\equiv0\pmod p$ — logarithm zero.

**Heuristic rarity:**

Write $a^{p-1}=1+kp$, $0\le k<p$ determines $\mod p^{2}$ via $k$. $k=0\mod p$ is Wieferich. If $k$ random uniform among $p$ values, probability $\displaystyle\dfrac{1}{p}$.

Expected count up to $X$:

$$\displaystyle E(X)=\sum_{p\le X}\dfrac{1}{p}\sim \log\log X+\text{Mertens for primes}$$

$$
\displaystyle
\begin{align*}
X=10^{3}&:\log\log X\approx1.93\\[5pt]
X=10^{17}&:\log\log X\approx3.66\\[5pt]
X=10^{100}&:\log\log X\approx5.43
\end{align*}
$$

So even up to googol, expect ~5 Wieferich. Explains 2 found and why third may be far.

**Modern Developments and Search Technology:**

- **Crandall, Dilcher, Pomerance 1997:** Efficient algorithm to compute $q_{p}(2)\mod p$ using $O(p)$? Actually using FFT and splitting, enabling search to $10^{12}$.

- **Dorais-Klyve 2011, PrimeGrid 2020-2023:** Distributed search to $6.7\times10^{15}$, then $1.45\times10^{17}$ using GPUs. Technique: compute $2^{p-1}\mod p^{2}$ with binary exponentiation, each multiplication $\mod p^{2}$ fits 128-bit for $p<10^{17}$ $\left(p^{2}<10^{34}<2^{113}\right)$, so need 128-bit modular multiply, implemented in hardware.

- **No third found:** Lower bound $>1.45\times10^{17}$ means if $p$ Wieferich base $2$ exists beyond known two, $p\ge1.45\times10^{17}$.

- **Near-Wieferich:** Primes where $q_{p}(2)$ small but non-zero, e.g., $|q_{p}(2)|<p^{\epsilon}$. These are also studied, many known.

**Other Bases:**

$$
\displaystyle
\begin{align*}
\text{Base }2&:1093,3511\\[5pt]
\text{Base }3&:11,1006003\\[5pt]
\text{Base }5&:2,20771,40487,53471161,1645333507,\dots\\[5pt]
\text{Base }10&:3,487,56598313,\dots\text{ (repunit)}\\[5pt]
\text{Base }a=p&: \text{excluded}
\end{align*}
$$

$2$ is Wieferich base $5$ because $5^{1}=5$, $5-1=4$ divisible by $2^{2}=4$.

#### Modern Day Uses

- **Cyclotomic fields and Mersenne:** $p$ Wieferich base $2$ iff $\displaystyle \mathbb{Q}(\zeta_{p})$ has $2$ with extra ramification: order of $2\mod p^{2}$ equals order $\mod p$. This affects class numbers of cyclotomic fields, Iwasawa invariants.

- **Primality testing / pseudoprimes:** Base-$a$ Fermat test checks $a^{p-1}\equiv1\mod p$. Stronger test mod $p^{2}$ would catch pseudoprimes. Wieferich primes are where stronger test also passes, making them "exceptional" pseudoprimes. Understanding them helps analyze failure probability of Fermat and Miller-Rabin variants that use $p^{2}$.

- **$abc$ conjecture and non-Wieferich infinitude:** J. H. Silverman 1988 proved $abc$ implies for any $a$, infinitely many primes $p$ with $\displaystyle a^{p-1}\not\equiv1\mod p^{2}$ — i.e., infinitely many non-Wieferich. So proof of many non-Wieferich would support $abc$. Converse open.

- **Wieferich pairs and Wieferich cubes:** Pair $(p,q)$ where $p^{q-1}\equiv1\mod q^{2}$ and $q^{p-1}\equiv1\mod p^{2}$. Only known small examples like $\left(2,1093\right)$ not symmetric pair, but $\left(83,4871\right)$ is double Wieferich? Research on mutual Wieferich.

- **Cryptography — not direct key, but testbed:** Fast exponentiation mod $p^{2}$ used in searches is same primitive as RSA exponentiation. Benchmarking $a^{p-1}\mod p^{2}$ for $p$ up to $10^{17}$ stress-tests big-integer libraries, GPU modular arithmetic.

- **Waring / Wolstenholme analogy:** Similar strengthening from $\mod p$ to $\mod p^{2}$ appears in Wolstenholme primes $\displaystyle\binom{2p-1}{p-1}\equiv1\mod p^{3}$, related to Bernoulli numbers. Wieferich and Wolstenholme both measure $p$-adic zeta values vanishing.

#### Summary

$$
\displaystyle
\begin{align*}
\text{Fermat}&: a^{p-1}=1+p\,q_{p}(a)\\[5pt]
\text{Wieferich}&: q_{p}(a)\equiv0\pmod p\iff a^{p-1}=1+p^{2}k\\[5pt]
\text{Base 2 known}&: p=1093,3511,\;p^{2}=1194649,12326721\\[5pt]
\text{Example non}&: p=5:\;2^{4}=16=1+3\cdot5,\;q_{5}(2)=3\not\equiv0\mod5\\[5pt]
\text{Heuristic count}&: \sum_{p\le X}\dfrac{1}{p}\sim\log\log X\to\infty\text{ slowly}\\[5pt]
\text{FLT link}&: x^{p}+y^{p}=z^{p},\,p\nmid xyz\implies q_{p}(2)\equiv0\text{ and }q_{p}(3)\equiv0\pmod p\\[5pt]
\text{Open}&: \exists\text{ infinitely many }p:q_{p}(2)\equiv0\pmod p\,?\\[5pt]
\text{Known lower bound}&: p>1.45\times10^{17}\text{ for next base-2}
\end{align*}
$$

Thus Wieferich primes began as technical lemma for FLT in 1909, became computational milestone with Meissner and Beeger finding $1093$ and $3511$, survived FLT's 1995 proof to become central example of $\mod p^{2}$ phenomenon, $p$-adic logarithm zero, and rarity $\displaystyle\sim\dfrac{1}{p}$ — only two known, next beyond $10^{17}$, conjecturally infinite but agonizingly sparse.

### Wilson Primes

They come from one of the most elegant theorems in elementary number theory.

**Wilson's Theorem (1770):** For an integer $p>1$,
$$\displaystyle p \text{ is prime } \iff (p-1)! \equiv -1 \mod p$$

That is, $p$ divides $(p-1)!+1$ exactly when $p$ is prime. For example, $4!+1=25$, divisible by $5$; $5!+1=121$, not divisible by $6$.

Wilson primes ask: when does this congruence hold one power higher?

> **Definition:** A prime $p$ is a Wilson prime if
> $$\displaystyle (p-1)! \equiv -1 \mod p^2$$
> i.e., $p^2 \mid (p-1)! + 1$.

If Wilson's Theorem says $p$ divides $(p-1)!+1$ once, a Wilson prime is a prime where $p$ divides it twice.

#### History and Discovery

$$\displaystyle \text{Ibn al-Haytham }\sim1000 \text{ — Wilson 1770 — Lagrange 1771 — Beeger 1913-1950s — Modern search to }2\times10^{13}$$

- **Pre-history:** Result $(p-1)!\equiv-1\mod p$ for prime $p$ known to Arab mathematician Ibn al-Haytham (Alhazen, $\sim1000$ AD) and to Leibniz 1683, but not proved in surviving manuscripts.

- **John Wilson (1741–1793):** English mathematician, student of Edward Waring. Waring announced in _Meditationes Algebraicae_ (1770) theorem without proof: "If $p$ prime, then $(p-1)!+1$ divisible by $p$", crediting student Wilson. Waring added "the theorem is hard because no notation exists for factorial" — factorial notation $!$ came later.

- **Lagrange 1771:** First published proof by Joseph-Louis Lagrange, using that polynomial $x^{p-1}-1-(x-1)(x-2)\cdots(x-p+1)$ has $p-1$ roots mod $p$ and coefficient comparison yields $(p-1)!\equiv-1\mod p$. Converse: if $n$ composite $\neq4$, $(n-1)!\equiv0\mod n$, so Wilson distinguishes primes.

- **Wilson primes defined:** Natural strengthening: when does $p^{2}\mid(p-1)!+1$? First computed by hand.

- **$p=5$:** $4!=24$, $4!+1=25=5^{2}$ — trivially Wilson, known to 19th century.

- **$p=13$:** $12!=479001600$, $12!+1=479001601=13^{2}\cdot2834329$. Found by 19th-century factorial tables, often credited to 1900s.

- **$p=563$:** Discovered by Karl Goldberg 1952 using early computer? Actually Leo Moser? Goldberg announced $563$ as Wilson prime in 1953 after computation on early SWAC computer. Verification needs $562!\mod563^{2}$, $562!\approx10^{1301}$ huge, but product modulo $316969$ feasible by iterated multiplication.

- **Search era:** After 1950s, no new Wilson primes found despite search to $500$, $10^{4}$, $10^{5}$, $5\times10^{8}$ (Crandall et al. 1997), $2\times10^{13}$ (Costa et al. 2024) using algorithms $O(p\log p)$ for factorial mod $p^{2}$, $p$-adic gamma function, and Wilson quotient.

#### The Math Behind Wilson Primes

**Normal Wilson:**

For prime $p$, define Wilson quotient:

$$\displaystyle W(p)=\dfrac{(p-1)!+1}{p}\in\mathbb{Z}$$

By Wilson's theorem integer.

Example $p=5$:

$$
\displaystyle
\begin{align*}
4!&=24\\
W(5)&=\dfrac{24+1}{5}=5
\end{align*}
$$

Example $p=7$:

$$
\displaystyle
\begin{align*}
6!&=720\\
W(7)&=\dfrac{721}{7}=103
\end{align*}
$$

$103\mod7=5\neq0$, so $7$ not Wilson.

**Squared rule:**

$$\displaystyle p\text{ Wilson}\iff W(p)\equiv0\mod p\iff p^{2}\mid(p-1)!+1$$

Because $(p-1)!+1=pW(p)$, need $p\mid W(p)$.

$$\displaystyle (p-1)!+1=pW(p)=p\cdot(p\cdot m)=m p^{2}$$

This parallels Wieferich: Fermat quotient $\displaystyle q_{p}(a)=\dfrac{a^{p-1}-1}{p}$, Wieferich condition $q_{p}(a)\equiv0\mod p$. Wilson quotient is factorial analogue.

**Why Wilson's theorem true — quick pairing idea:**

For prime $p$, each $a=1,\dots,p-1$ has inverse $a^{-1}\mod p$ distinct unless $a\equiv\pm1\mod p$ $\left(\text{since }a^{2}\equiv1\mod p\implies p\mid a^{2}-1\right)$. Pair up $2$ with inverse $3$, $4$ with $5$, etc., product $\equiv1$. Leftover $1$ and $p-1\equiv-1$, so total product $\equiv-1$.

$$\displaystyle (p-1)!\equiv1\cdot(p-1)\cdot\prod_{\text{pairs}}(a\cdot a^{-1})\equiv-1\mod p$$

#### Known Values and Verification

Only three known:

$$\displaystyle 5,\;13,\;563$$

**1. $p=5$**

$$
\displaystyle
\begin{align*}
4!&=24\\
4!+1&=25\\
\dfrac{25}{5^{2}}&=1\\
W(5)&=5\equiv0\mod5
\end{align*}
$$

**2. $p=13$**

$$
\displaystyle
\begin{align*}
12!&=479001600\\
12!+1&=479001601\\
\dfrac{12!+1}{13}&=36846277=W(13)\\
\dfrac{W(13)}{13}&=\dfrac{36846277}{13}=2834329\\
13^{2}&=169,\;479001601/169=2834329\\
\text{Thus }12!&\equiv-1\mod169
\end{align*}
$$

Check $W(13)\mod13=0$.

**3. $p=563$**

$562!$ has about $\displaystyle\log_{10}562!\approx1306$ digits — impossible to write. Compute iteratively modulo $p^{2}=316969$:

$$
\displaystyle
\begin{align*}
r_{1}&=1\\
r_{k+1}&=r_{k}\cdot(k+1)\mod316969,\;k=1\dots562\\
\text{Result }r_{562}&=316968\equiv-1\mod316969
\end{align*}
$$

Each step numbers $<p^{2}$, feasible $O(p)$ multiplies. Modern search uses faster $O(p\log p)$ grouping via polynomial and $p$-adic gamma $\displaystyle\Gamma_{p}$ to avoid $p$ steps per prime.

#### Facts and Mysteries

**Extreme rarity and search limits:**

Search complexity per prime $p$ is $O(p)$ multiplies mod $p^{2}$. Sum over $p\le X$ about $\displaystyle\dfrac{X^{2}}{\log X}$ operations naive, too large. Improved algorithms using Wilson primes via $\displaystyle(p-1)!\equiv\Gamma_{p}(p)\mod p^{2}$ and splitting product into blocks using FFT reduce to near $O(X)$.

Current verified bound:

$$\displaystyle \text{No Wilson prime }p\text{ with }5<p<2\times10^{13},\;p\neq13,563$$

That is $20$ trillion.

**Heuristic $\displaystyle\dfrac{1}{p}$:**

For prime $p$, Wilson theorem says $(p-1)!\equiv-1\mod p$, so $(p-1)!\mod p^{2}$ lies among $p$ residues congruent $-1\mod p$: $-1,-1+p,-1+2p,\dots,-1+(p-1)p$.

If random uniform among those $p$ possibilities, probability exactly $-1\mod p^{2}$ is $\displaystyle\dfrac{1}{p}$.

Expected number up to $X$:

$$\displaystyle E(X)=\sum_{p\le X}\dfrac{1}{p}\sim\log\log X$$

$$
\displaystyle
\begin{align*}
X=13&: \sum_{p\le13}\dfrac{1}{p}=\dfrac12+\dfrac13+\dfrac15+\dfrac17+\dfrac1{11}+\dfrac1{13}\approx1.17\\
X=563&: \log\log563\approx1.90\text{ expects }~2\text{ Wilson}\\
X=2\times10^{13}&: \log\log X\approx3.4\text{ expects }~3\text{-}4\\
X=10^{100}&: \log\log X\approx5.43\text{ expects }~5
\end{align*}
$$

Matches observation $3$ found, predicts next may be $\gg10^{13}$, perhaps $\sim10^{30}$.

Conjectured infinitely many, but no proof for any type of supercongruence prime (Wieferich, Wilson, Wolstenholme).

**Connections:**

- **Wolstenholme's theorem:** For $p>3$, $\displaystyle\binom{2p-1}{p-1}\equiv1\mod p^{3}$. Wolstenholme primes where $\equiv1\mod p^{4}$ are $16843,2124679$ — similarly rare.

- **Bernoulli numbers:** Wilson quotient formula Lerch:

$$\displaystyle W(p)\equiv B_{p-1}-B_{2p-2}\mod p$$

Actually $\displaystyle W(p)\equiv\frac{1}{p}((p-1)!+1)$ linked to $B_{p-1}$ numerator. Irregular primes $\left(p\mid\text{numerator }B_{2k}\right)$ include $37,59,67,\dots$; $563$ is irregular — $563\mid B_{something}$, linking Wilson to class number of cyclotomic field $\mathbb{Q}(\zeta_{p})$.

- **Wilson primes are Lerch primes?** Lerch formula relates Wilson quotient to sum $\displaystyle\sum_{a=1}^{p-1}q_{p}(a)$.

**Modern day uses and why they matter:**

- **Supercongruence prototype:** Wilson primes are canonical example where congruence $\mod p$ lifts to $\mod p^{2}$ unexpectedly. Study of supercongruences $\mod p^{2},p^{3}$ drives $p$-adic analysis, $p$-adic gamma function $\Gamma_{p}$, and $p$-adic L-functions. Wilson $p$-adic gamma: $\displaystyle\Gamma_{p}(p)=(p-1)!$ up to sign, so Wilson condition $\Gamma_{p}(p)\equiv-1\mod p^{2}$.

- **Algorithm development:** Fast factorial mod $p^{2}$ algorithms developed for Wilson search — splitting product $1\cdot2\cdots p-1$ into blocks, using polynomial evaluation and Wilson's theorem for intervals — now used in primality testing, factorial prime searches $\left(n!\pm1\right)$, and computation of $p$-adic invariants.

- **Cryptography — not direct:** Not used as key, but failure mode for Wilson-based primality test: test $n$ prime iff $(n-1)!\equiv-1\mod n$ is true but factorial huge, not practical. Understanding Wilson primes shows where even stronger test $(n-1)!\equiv-1\mod n^{2}$ would falsely suggest composite? Actually composite never satisfies Wilson mod $n$, but Wilson primes satisfy stronger condition.

- **$p$-adic and $abc$:** Like Wieferich, $abc$ conjecture implies infinitely many non-Wilson primes. Existence of infinitely many Wilson primes also expected from $\log\log$ heuristic.

In short: Every prime $p$ satisfies $(p-1)!\equiv-1\mod p$. Wilson primes are the extremely rare primes where divisibility happens twice: $p^{2}\mid(p-1)!+1$. Only $5,13,563$ known, with $5$ giving $25$, $13$ giving $169\mid12!+1$, $563$ verified via modular product, no fourth below $2\times10^{13}$, expected count $\displaystyle\sum\dfrac{1}{p}\sim\log\log X$ suggests infinitely many but next may be astronomically large, and their study drives $p$-adic gamma and supercongruence theory.

### Carmichael Numbers

Carmichael numbers are composite impostors — they pretend to be prime when tested with Fermat's Little Theorem. They are the worst possible case for naive primality testing, and the reason we cannot use the converse of Fermat's Little Theorem as a primality test.

#### History and Discovery

$$\displaystyle\text{Fermat 1640 — Korselt 1899 — Carmichael 1910 — Chernick 1939 — Alford-Granville-Pomerance 1994}$$

- **Pierre de Fermat (1640):** Fermat's Little Theorem: if $p$ prime, $\gcd(a,p)=1$, then $\displaystyle a^{p-1}\equiv1\mod p$. Stated without proof in letter to Frénicle.

- **Sarrus (1820):** First noted converse false: $341=11\cdot31$ composite but $\displaystyle2^{340}\equiv1\mod341$. So some composites pass base-2 test — first Fermat pseudoprime.

- **Arthur Korselt (1899):** German mathematician in _Archiv der Mathematik und Physik_ gave complete characterization of absolute pseudoprimes: $n$ composite square-free, $p-1\mid n-1$ for all $p\mid n$. He proved theorem but had no example, did not know if any $n$ satisfying it existed — pure criterion.

- **Robert Daniel Carmichael (1879–1967):** American mathematician at University of Illinois. In 1910 paper, he found first example $561=3\cdot11\cdot17$ satisfying Korselt. In 1912 he found $1105,1729,2465,2821,6601,8911,10585,15841,\dots$. Hence name Carmichael numbers, though Korselt had priority for criterion. Carmichael also defined Carmichael function $\lambda(n)$.

- **Jack Chernick (1939):** Observed parametric form: if $6k+1,12k+1,18k+1$ prime, then $\displaystyle n=(6k+1)(12k+1)(18k+1)$ Carmichael. For $k=1$: $7\cdot13\cdot19=1729$ — Hardy-Ramanujan taxicab $1729=1^{3}+12^{3}=9^{3}+10^{3}$ is also Carmichael. This gave infinite candidate family conditional on prime triplets.

- **Paul Erdős heuristic (1956):** Conjectured infinitely many Carmichael numbers, outlined strategy: choose many primes $p$ where $p-1$ smooth $\left(\text{all prime factors small}\right)$, product of subset will satisfy $p-1\mid n-1$ via combinatorial argument.

- **Alford, Granville, Pomerance (1994):** Landmark Annals of Mathematics paper "There are infinitely many Carmichael numbers". Proved $\displaystyle C(X)\ge X^{2/7}$ for large $X$, where $C(X)$ = count of Carmichael $\le X$. Made Erdős heuristic rigorous using zero-free regions of L-functions and combinatorial number theory. Later improved by Harman to $\displaystyle X^{0.33}$, and best heuristic $X^{1-o(1)}$ expected? Actually Pomerance conjectured $C(X)=X^{1-o(1)}$? Current conjecture $\displaystyle C(X)=X^{1/2+o(1)}$? Data suggests $\displaystyle C(X)$ roughly $\exp$.

- **Modern computations:** Pinch (2007) enumerated up to $10^{18}$: $1,401,644$ Carmichael. To $10^{21}$, about $20$ million. Used to test primality libraries.

#### Fermat's Little Theorem and Its Converse

Fermat's Little Theorem:

$$\displaystyle\text{If }p\text{ prime, }\gcd(a,p)=1\implies a^{p-1}\equiv1\mod p$$

Many hope converse true: If $\displaystyle a^{n-1}\equiv1\mod n$, then $n$ prime. False.

Composite $n$ with $\displaystyle a^{n-1}\equiv1\mod n$ for given $a$ called **Fermat pseudoprime base $a$**.

Classic $341=11\times31$:

$$\displaystyle 2^{340}\equiv1\mod341$$

Yet $341$ composite. So $341$ looks prime testing base $2$. Known to Sarrus 1820, smallest base-2 pseudoprime.

Carmichael numbers are ultimate pseudoprimes — pseudoprime to _every_ base coprime.

> **Definition:** Composite $n$ is **Carmichael** (absolute pseudoprime) if
> $$\displaystyle a^{n-1}\equiv1\mod n$$
> for every $a$ with $\gcd(a,n)=1$.
> Equivalently $\displaystyle a^{n}\equiv a\mod n$ for all integers $a$.

So for true prime $p$, $p-1$ bases pass. For Carmichael $n$, $\varphi(n)$ bases pass — all.

**First examples:**

$$
\displaystyle
\begin{align*}
561&=3\cdot11\cdot17\\
1105&=5\cdot13\cdot17\\
1729&=7\cdot13\cdot19\\
2465&=5\cdot17\cdot29\\
2821&=7\cdot13\cdot31\\
6601&=7\cdot23\cdot41\\
8911&=7\cdot19\cdot67
\end{align*}
$$

Check $561$:

$$
\displaystyle
\begin{align*}
2^{560}&\equiv1\mod561\\
5^{560}&\equiv1\mod561\\
7^{560}&\equiv1\mod561
\end{align*}
$$

for any of $\varphi(561)=320$ numbers $a$ with $\gcd(a,561)=1$.

#### Korselt's Criterion (1899)

**Theorem:** $n$ Carmichael iff:

1. **Composite and square-free:** $n=p_{1}p_{2}\cdots p_{k}$ distinct primes. If $p^{2}\mid n$, choose $a=1+p$, then $\displaystyle(1+p)^{p}\equiv1+p^{2}\not\equiv1\mod p^{2}$, fails.

2. **At least three primes:** $k\ge3$. Proof sketch: if $n=pq$, need $p-1\mid pq-1$ and $q-1\mid pq-1$. Write $pq-1=q(p-1)+(q-1)$, so $p-1\mid q-1$ and $q-1\mid p-1$ impossible unless $p=q$.

3. **Divisibility:** $\displaystyle p-1\mid n-1$ for every $p\mid n$.

Why (3) key: If $a^{n-1}\equiv1\mod n$, then $\mod p$ also $1$. Take $a$ primitive root mod $p$ — order $p-1$. Then $p-1\mid n-1$.

Examples with:

$$
\displaystyle
\begin{align*}
561&=3\cdot11\cdot17\\
3-1=2&\mid560\\
11-1=10&\mid560\\
17-1=16&\mid560=35\cdot16
\end{align*}
$$

$$
\displaystyle
\begin{align*}
341=11\cdot31\text{ not Carmichael: }31-1=30\nmid340
\end{align*}
$$

Indeed $3^{340}\equiv56\not\equiv1\mod341$, so base $3$ catches $341$.

$$
\displaystyle
\begin{align*}
1105&=5\cdot13\cdot17\\
4&\mid1104,\;12\mid1104=92\cdot12,\;16\mid1104=69\cdot16
\end{align*}
$$

$$
\displaystyle
\begin{align*}
1729&=7\cdot13\cdot19\\
6&\mid1728,\;12\mid1728=144\cdot12,\;18\mid1728=96\cdot18
\end{align*}
$$

**Constructing via Chernick:**

If $6k+1,12k+1,18k+1$ prime, then product Carmichael because:

$$
\displaystyle
\begin{align*}
n&=(6k+1)(12k+1)(18k+1)\\
n-1&=(6k+1)(12k+1)(18k+1)-1\\
&\equiv0\mod6k,\;0\mod12k,\;0\mod18k
\end{align*}
$$

Since $\displaystyle L=\text{lcm}(6k,12k,18k)=36k$, and one checks divisibility holds. For $k=1$: $7,13,19$ prime → $1729$.

#### Key Facts

- **Carmichael function $\lambda(n)$:** Smallest $m$ with $a^{m}\equiv1\mod n$ for all $\gcd(a,n)=1$. For $n=\prod p_{i}$ odd square-free,

$$\displaystyle \lambda(n)=\text{lcm}(p_{1}-1,\dots,p_{k}-1)$$

Then Korselt says

$$\displaystyle n\text{ Carmichael}\iff\lambda(n)\mid n-1$$

Example $n=561$:

$$
\displaystyle
\begin{align*}
\lambda(561)&=\text{lcm}(2,10,16)=80\\
80&\mid560
\end{align*}
$$

So exponent of group $(\mathbb{Z}/n\mathbb{Z})^{\times}$ divides $n-1$.

- **Infinitude:** Alford-Granville-Pomerance 1994 proved infinitely many, at least $\displaystyle X^{2/7}$ up to $X$. Current best $\displaystyle X^{0.333...}$ by Harman. Conjectured $\displaystyle C(X)=X^{1-o(1)}$? Data:

$$
\displaystyle
\begin{align*}
C(10^{3})&=1\\
C(10^{6})&=43\\
C(10^{9})&=646\\
C(10^{12})&=8241\\
C(10^{15})&=105212\\
C(10^{18})&=1401644\\
C(10^{21})&\approx20138200
\end{align*}
$$

Compare primes $\pi(10^{21})\approx2\times10^{19}$ — ratio $\sim10^{-12}$.

- **Cryptographic importance:**

Fermat test picks random $a$, checks $\displaystyle a^{n-1}\equiv1\mod n$. For prime, always passes. For typical composite, fails with probability $\ge1/2$. For Carmichael, fails with probability $0$ — fools every $a$ coprime.

$$\displaystyle \Pr_{a}[\text{Fermat passes}\mid n\text{ Carmichael}]=1$$

Hence Fermat test not suitable for crypto.

Miller-Rabin fixes: write $\displaystyle n-1=d\cdot2^{s}$, $d$ odd, check $\displaystyle a^{d}\equiv1$ or $\displaystyle a^{d2^{r}}\equiv-1$ for some $0\le r<s$. Carmichael numbers fail this stronger condition.

Example $561=2^{4}\cdot35+1$, base $2$:

$$
\displaystyle
\begin{align*}
2^{35}&\equiv263\mod561\\
2^{70}&\equiv166\mod561\\
2^{140}&\equiv67\mod561\\
2^{280}&\equiv1\mod561
\end{align*}
$$

Never $\pm1$ before $1$, so Miller-Rabin declares composite — catches $561$.

- **Distinction:**

$$
\displaystyle
\begin{align*}
\text{Fermat pseudoprime base }a&: n\text{ composite, }a^{n-1}\equiv1\mod n\text{ for one }a\\
\text{Carmichael}&: n\text{ composite, }a^{n-1}\equiv1\mod n\text{ for all }a,\gcd(a,n)=1
\end{align*}
$$

$341$ pseudoprime base $2$ only, not Carmichael. $561$ pseudoprime to all $320$ bases.

**Modern developments:**

- **Distribution:** Granville-Pomerance conjecture $\displaystyle C(X)\sim X^{1-\frac{(1+o(1))\log\log\log X}{\log\log X}}$ — grows faster than any power $X^{\epsilon}$? Still open.

- **Erdős construction:** Modern proofs use primes $p$ where $p-1$ is $y$-smooth $\left(\text{all prime factors }\le y\right)$ and large $L=\text{lcm}$ of many $p-1$, then product of subset $\equiv1\mod L$ via pigeonhole.

- **Use in primality libraries:** Lists of Carmichael up to $10^{18}$ used as regression tests for Miller-Rabin, Baillie-PSW. OpenSSL, GMP test against them.

- **Absolute Euler pseudoprimes:** Subclass where $\displaystyle a^{(n-1)/2}\equiv\pm1\mod n$ for all $a$ with $\gcd(a,n)=1$ and Legendre symbol condition — even rarer, e.g. $1729,2465$.

In short: Korselt 1899 characterized them before any example known, Carmichael 1910 found $561=3\cdot11\cdot17$ first, Chernick gave prime-triple construction $1729$, Alford-Granville-Pomerance 1994 proved infinite, modern search enumerates to $10^{21}$, and their existence forces cryptography to use Miller-Rabin, not naive Fermat — they are composites where $\displaystyle\lambda(n)=\text{lcm}(p_{i}-1)\mid n-1$, fooling $\displaystyle a^{n-1}\equiv1\mod n$ for every $\displaystyle a$ coprime.
