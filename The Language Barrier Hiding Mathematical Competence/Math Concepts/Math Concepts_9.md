## Different Types of Numbers

### Narcissistic Numbers

A narcissistic number — also known as an Armstrong number, a plus perfect number, or a pluperfect digital invariant (PPDI) — is an $n$-digit integer that is exactly equal to the sum of its own digits each raised to the $n$-th power. They are "full of themselves" in a literal sense: you dismantle the number into its digits, apply the power operation, and it reconstructs itself.

#### How They Work

To test a number in base 10:

1. **Count the digits**: $n = \text{number of digits}$.

2. Raise each digit $d_i$ to the $n$-th power.

3. **Sum the results**: $S = \sum d_i^n$.

4. If $S$ equals the original number, it is narcissistic.

**Classic Examples:**

- **Single digits (0–9):** All are trivially narcissistic because $d^1 = d$. Some definitions exclude 0, but mathematically it qualifies.

- **153 (3 digits):** $1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153$

- **370 (3 digits):** $3^3 + 7^3 + 0^3 = 27 + 343 + 0 = 370$

- **371 (3 digits):** $3^3 + 7^3 + 1^3 = 27 + 343 + 1 = 371$

- **1634 (4 digits):** $1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634$

The 3-digit cases are the most famous because they are the first non-trivial ones, and $153$ appears in the New Testament and in many introductory programming exercises.

#### Key Facts and Limitations

**1. Finiteness:** Unlike primes, there are only finitely many narcissistic numbers in any base. In base 10, there are exactly 88. The list is complete and proven.

**2. Why they must end — the Upper Bound Proof:**
For an $n$-digit number, the smallest possible value is $10^{n-1}$. The largest possible sum of $n$-th powers is when every digit is 9: $n \times 9^n$.

We need $10^{n-1} \le n \times 9^n$ for a narcissistic number to even be possible.

Take logs: $n-1 \le \log_{10}(n) + n \log_{10}(9)$. Since $\log_{10}(9) \approx 0.9542$, the right side grows as $0.9542n$ while the left grows as $n$. For $n > 60$, $10^{n-1}$ is always larger than $n \times 9^n$. Therefore no $n$-digit narcissistic number can exist for $n > 60$. This proves the search is finite — a computer can check everything up to 60 digits and be done.

More refined analysis shows the actual limit is much lower: the largest base-10 narcissistic number has only 39 digits.

**3. The Largest Number:**
$$115132219018763992565095597973971522401$$
Check: it has 39 digits, and the sum of each of its 39 digits raised to the 39th power equals itself.

**4. Mathematical Status:** They are beloved in recreational mathematics and computer science as an exercise in brute force and digit manipulation. G.H. Hardy, in _A Mathematician's Apology_ (1940), famously dismissed them: "These are odd facts, very suitable for puzzle columns and likely to amuse amateurs, but there is nothing in them which appeals to the mathematician."

**Common Base-10 Narcissistic Numbers:**

- **3 digits:** $153, 370, 371, 407$

- **4 digits:** $1634, 8208, 9474$

- **5 digits:** $54748, 92727, 93084, 548834$ is actually 6 digits — the three 5-digit ones are $54748, 92727, 93084$

- **6 digits:** $548834$

- **7 digits:** $1741725, 4210818, 9800817, 9926315$

After that they become extremely sparse.

#### Base Changes: A Universal Phenomenon

Narcissistic numbers exist in every base $b \ge 2$, but _which_ numbers qualify changes because both the digit values and the interpretation of the number depend on $b$. The general definition is: a number $N$ with $k$ digits in base $b$ is narcissistic if $N = \sum d_i^k$, where $d_i$ are its base-$b$ digits evaluated in decimal.

##### How it Works in Other Bases

- **Binary (Base 2):** Only $0$ and $1$ are narcissistic. For any $k \ge 2$, the maximum sum is $k \times 1^k = k$, but the smallest $k$-digit binary number is $2^{k-1}$, which quickly outgrows $k$. So no larger examples exist.

- **Base 3 (Ternary):** In addition to $0,1,2$, we have:

  $5_{10} = 12_3$: $1^2 + 2^2 = 1+4=5$
  $8_{10} = 22_3$: $2^2 + 2^2 = 8$
  $17_{10} = 122_3$: $1^3 + 2^3 + 2^3 = 1+8+8=17$

- **Base 4 (Quaternary):** Example $35_{10} = 203_4$:

  $2^3 + 0^3 + 3^3 = 8+0+27=35$
  Another: $28_{10} = 130_4$: $1^3+3^3+0^3 = 28$

##### Comparison Across Bases

Every base has the same bounding argument: $b^{k-1} \le k(b-1)^k$. Since $b^{k-1}$ grows exponentially faster than $k(b-1)^k$ in $k$, each base has finitely many.

| Base | Total Count | Representative Narcissistic Numbers (decimal value and representation) |
| :--- | :---------- | :--------------------------------------------------------------------- |
| 2    | 2           | $0, 1$                                                                 |
| 3    | 6           | $0,1,2,5 (12_3), 8 (22_3), 17 (122_3)$                                 |
| 4    | 15          | $0-3, 28 (130_4), 29 (131_4), 35 (203_4), 43 (223_4)$                  |
| 10   | 88          | $0-9, 153, 370, 371, 407, 1634, 8208, 9474, 54748 \dots$               |
| 16   | 294         | $0-\text{F}, 156 (9C_{16}), 193 (C1_{16}), 1025 (401_{16})$            |

##### Why Bases Matter

Changing base changes both sides of the equation. A larger base increases the digit limit $(b-1)$, so the sum $k(b-1)^k$ can grow larger, allowing for more and larger narcissistic numbers. Base 16 has 294 such numbers compared to base 10's 88, but still finitely many.

This makes narcissistic numbers a base-dependent curiosity rather than a deep number-theoretic property — their existence depends on our choice of representation, not on intrinsic properties of the integers themselves. That is precisely why they remain in the realm of recreational mathematics, but they are a perfect illustration of a Ramsey-type finiteness principle: even in an infinite set of numbers, a restrictive digit condition forces only finitely many solutions.

### Kaprekar Numbers

A Kaprekar number is a natural number with a striking "split-square" property: when you square it, you can split the result into two parts that add back to the original number. For example, $45^2 = 2025$, and $20 + 25 = 45$.

They are named after the Indian recreational mathematician D. R. Kaprekar (1905–1986), who described them in 1949 and introduced them to the Western literature around 1980. Kaprekar worked as a schoolteacher in Maharashtra and made numerous contributions to recreational number theory despite having little formal training.

#### Formal Definition

Let $k$ be a $k$-digit number in base 10. Let $n$ be the number of digits of $k$.

$k$ is a Kaprekar number if there exists a split of $k^2$ into two parts $q$ and $r$ such that:

$$k^2 = q \cdot 10^n + r$$
$$k = q + r$$

where:

- $0 \le r < 10^n$ — $r$ is the right part, with at most $n$ digits (leading zeros allowed)

- $q \ge 0$ — $q$ is the left part

- $r \neq 0$ by convention, to exclude trivial cases like $10, 100, 1000$ where $k^2 = 100, 10000, \dots$ would give $q=1, r=0$.

Some definitions require $0 < r < 10^n$ and $q > 0$, but most allow $q=0$ for $k=1$.

The split point is dictated by the original number: a $d$-digit number must split its square so the right part has $d$ digits. This is what makes $4879$ work: $4879$ has 4 digits, $4879^2 = 23804641$, split as $238$ | $4641$, and $238+4641=4879$.

#### How to Identify a Kaprekar Number

To test a number $k$:

**1. Square it:** Compute $k^2$.
**2. Split it:** Let $n = $ number of digits in $k$. Take the last $n$ digits of $k^2$ as $r$, and the remaining leading digits as $q$. If $k^2$ has fewer than $n$ digits, take $q=0$.
**3. Sum and check:** If $q+r = k$ and $r \neq 0$, it is Kaprekar.

**Worked Examples:**

- **$9$**: $n=1$, $9^2=81$, $q=8, r=1$, $8+1=9$

- **$45$**: $n=2$, $45^2=2025$, $q=20, r=25$, $20+25=45$

- **$55$**: $55^2=3025$, $30+25=55$ — note the complement pair with 45.

- **$99$**: $99^2=9801$, $98+01=99$. Leading zeros in $r$ are allowed, interpreted as $1$.

- **$297$**: $n=3$, $297^2=88209$, $88+209=297$

- **$703$**: $703^2=494209$, $494+209=703$

- **$2223$**: $2223^2=4941729$, $494+1729=2223$

**First few Kaprekar numbers (base 10):**
$$1, 9, 45, 55, 99, 297, 703, 999, 2223, 2728, 4879, 4950, 5050, 5292, 7272, 7777, 9999, 17344, 22222, 77778, 82656, 95121, 99999, \dots$$

Note $5050$ is famous from the Gauss sum story: $5050^2=25502500$, $255+02500=255+2500=5050$.

#### Common Properties

**1. Complement Pairs to $10^n$:** If $k$ is an $n$-digit Kaprekar number, then $10^n - k$ is often also Kaprekar. Example: $45+55=100=10^2$, $2223+7777=10000=10^4$. This arises from the divisor structure of $10^n-1$.

**2. The Nines Pattern:** All numbers consisting only of 9's are Kaprekar numbers: $9, 99, 999, 9999, \dots$ Proof: $99\dots9 = 10^n-1$, and $(10^n-1)^2 = 10^{2n} -2\cdot10^n +1 = (10^n-2)10^n +1$, but more directly $ (10^n-1)^2 = (10^n-2)\cdot10^n + (2\cdot10^n -2\cdot10^n +1)$ — simpler example: $99^2=9801$, $999^2=998001$, $998+001=999$.

**3. Infinitude:** Unlike narcissistic numbers, there are infinitely many Kaprekar numbers. There is no upper bound — you can construct arbitrarily large ones.

**4. Divisor Characterization:** This is the deep structure. $k$ is Kaprekar iff $k$ divides $10^n \cdot q + r - k$? More usefully, Kaprekar numbers correspond to unitary divisors of $b^n-1$ in base $b$. That is, $k$ is Kaprekar in base $b$ iff there exists a divisor $d$ of $b^n-1$ such that... This explains why they come in complementary pairs.

#### Kaprekar's Constant — A Common Confusion

The Kaprekar number is different from **Kaprekar's Constant (6174)**, though both are due to the same mathematician.

Kaprekar's Routine: Take any 4-digit number with at least two distinct digits, arrange its digits in descending and ascending order, and subtract (largest - smallest). Repeat. You will always reach 6174 in at most 7 steps, and then stay there: $7641-1467=6174$.

6174 is the fixed point of that dynamical process, not a split-square number.

#### Comparison by Base

While $1$ is Kaprekar in every base, other values depend on $b$. In base $b$, the definition uses $b^n$ instead of $10^n$: $k^2 = q \cdot b^n + r$, $0 \le r < b^n$, $q+r=k$.

| Base   | Kaprekar Numbers (decimal value)     | Example in Base                                              |
| :----- | :----------------------------------- | :----------------------------------------------------------- |
| **10** | $1, 9, 45, 55, 99, 297, 703, \dots$  | $45^2=2025 \to 20+25=45$                                     |
| **12** | $1, 11, 66, 78, 143, \dots$          | $B_{12}=11_{10}$, $B_{12}^2 = A1_{12}$ ($121_{10}$), $A+1=B$ |
| **16** | $1, 6, 15, 85, 171, 205, 255, \dots$ | $F_{16}=15_{10}$, $F_{16}^2 = E1_{16}$ ($225_{10}$), $E+1=F$ |

**Key Differences Across Bases:**

- **The $b-1$ Rule:** In any base $b$, $b-1$ is always Kaprekar. This is the generalization of the "all 9's" rule. $9$ in base 10, $B=11$ in base 12, $F=15$ in base 16 are all $b-1$.

- **Density Varies:** Some bases are richer than others because the factorization of $b^n-1$ is richer. Base 10 and base 16 have many small Kaprekar numbers; other bases have fewer.

- **Unitary Divisors:** Formally, the $n$-digit Kaprekar numbers in base $b$ are in bijection with unitary divisors $d$ of $b^n-1$ where $d \equiv 0$ or $1 \pmod{\dots}$. This number-theoretic characterization is why the list changes so dramatically with $b$.

### Catalan Numbers

The Catalan numbers are one of the most ubiquitous sequences in combinatorics. The sequence begins:

$$1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, 16796, 58786, 208012, 742900, 2674440, 9694845, \dots$$

Named after the Belgian mathematician Eugène Charles Catalan (1814–1894), who studied them in 1838, they were actually known much earlier to Euler (1751) and to the Chinese mathematician Minggatu (c. 1730).

A Catalan number counts the number of ways to arrange objects into recursive, non-crossing structures. There are over 200 known combinatorial interpretations. The fact that the same numbers count such wildly different objects is a hallmark of deep underlying structure.

#### Formula and Calculation

The $n$-th Catalan number, denoted $C_n$ (with $C_0 = 1$ by convention), has several equivalent definitions:

**1. Closed Form:**
$$C_n = \dfrac{1}{n+1} \binom{2n}{n} = \dfrac{(2n)!}{(n+1)!\,n!} = \dfrac{1}{2n+1}\binom{2n+1}{n}$$

This shows $C_n$ is an integer despite the division, since $\binom{2n}{n}$ is divisible by $n+1$.

**2. Recurrence Relation (Convolution):**
$$C_0 = 1, \quad C_{n+1} = \sum_{i=0}^{n} C_i C_{n-i}$$

This recurrence captures the recursive decomposition that defines most Catalan structures: an object of size $n+1$ splits into two smaller Catalan objects of sizes $i$ and $n-i$.

$$C_{n+1} = C_0C_n + C_1C_{n-1} + C_2C_{n-2} + \dots + C_nC_0$$

For example, $C_3 = C_0C_2 + C_1C_1 + C_2C_0 = 1\cdot2 + 1\cdot1 + 2\cdot1 = 5$.

**3. Growth:** Asymptotically, $C_n \sim \dfrac{4^n}{n^{\dfrac{3}{2}}\sqrt{\pi}}$.

| $n$   | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8    | 9    | 10    |
| :---- | :-- | :-- | :-- | --- | --- | --- | --- | --- | ---- | ---- | ----- |
| $C_n$ | 1   | 1   | 2   | 5   | 14  | 42  | 132 | 429 | 1430 | 4862 | 16796 |

#### The Five Classic Interpretations

All of the following are counted by $C_n$:

**1. Dyck Paths — Monotonic Lattice Paths**
The number of monotonic paths from $(0,0)$ to $(n,n)$ that never rise above the main diagonal. Each path consists of $n$ steps East $(1,0)$ and $n$ steps North $(0,1)$ and stays weakly below the line $y=x$. Equivalently, the number of ways to walk from the bottom-left to top-right of an $n \times n$ grid without crossing above the diagonal.

For $n=3$, the 5 paths are: EEENNN stays below? Actually E = right, N = up. Valid paths are those that never have more N than E at any prefix.

This interpretation directly proves the formula: total monotonic paths are $\binom{2n}{n}$. The number that cross the diagonal is $\binom{2n}{n+1}$ by the reflection principle, so $C_n = \binom{2n}{n} - \binom{2n}{n+1} = \dfrac{1}{n+1}\binom{2n}{n}$.

**2. Polygon Triangulation**
The number of ways to divide a convex polygon with $n+2$ sides into $n$ triangles using $n-1$ non-intersecting diagonals. This was Euler's original problem.

For $n=3$, a pentagon ($5$ sides) has $5$ triangulations. For $n=6$, an octagon has $132$ triangulations.

<figure>
  <img src="../images/Catalan_Numbers_8_Sides.png" alt="Illustration of the number of ways a polygon with 8 sides can be cut into 6 triangles">
  <figcaption>All 14 ways to triangulate a hexagon ($n=4$). An $(n+2)$-gon has $C_n$ triangulations. Source: MacTutor.</figcaption>
</figure>

**3. Correct Parenthesization**
The number of ways to correctly match $n$ pairs of parentheses.

For $n=3$: $((()))$, $(()())$, $(())()$, $()(())$, $()()()$ — exactly $5 = C_3$.

Equivalently: number of ways to place parentheses in a product of $n+1$ factors to specify the order of multiplication (associativity), e.g., $C_3=5$ ways to multiply $a\cdot b\cdot c\cdot d$: $((ab)c)d$, $(a(bc))d$, $(ab)(cd)$, $a((bc)d)$, $a(b(cd))$.

**4. Rooted Binary Trees**
The number of distinct rooted binary trees with $n$ internal nodes (or $n+1$ leaves), or with $n+1$ nodes total if we consider full binary trees where each node has 0 or 2 children. Also the number of plane trees, stack-sortable permutations, and ways to dissect a staircase shape with $n$ steps into $n$ rectangles.

**5. Non-Crossing Handshakes**
The number of ways $2n$ people sitting around a circular table can shake hands simultaneously without any arms crossing. Fix one person — they must shake with someone of opposite parity, splitting the circle into two smaller circles, giving the recurrence $C_{n+1} = \sum C_i C_{n-i}$.

#### Why Are They the Same?

The recurrence $C_{n+1} = \sum C_i C_{n-i}$ is the universal skeleton. In each interpretation:

- **Triangulation:** Fix one side of the $(n+3)$-gon as base. Choose a third vertex to form a triangle with it. This triangle splits the polygon into two smaller polygons with $i+2$ and $n-i+2$ sides.

- **Parentheses:** The outermost pair encloses $()$ as $ ( A ) B $ where $A$ has $i$ pairs and $B$ has $n-1-i$ pairs.

- **Dyck Path:** The first return to the diagonal splits the path into two smaller Dyck paths.

Thus all these problems satisfy the same recurrence and initial condition, so they must have the same solution: the Catalan numbers.

### Bell Numbers

The Bell number, denoted $B_n$, counts the number of ways to partition a set of $n$ distinct labeled elements into any number of non-empty, non-overlapping, unordered subsets. In other words, it is the total number of possible equivalence relations on an $n$-element set.

If $C_n$ counts non-crossing, recursive structures, $B_n$ counts _all_ possible groupings — crossing allowed.

Named after Eric Temple Bell (1883–1960), who studied them systematically in the 1930s, they were actually discovered earlier by Charles Sanders Peirce in 1880.

#### The Sequence

The first Bell numbers, starting from $B_0 = 1$ for the empty set, are:
$$1, 1, 2, 5, 15, 52, 203, 877, 4140, 21147, 115975, 678570, 4213597, \dots$$

They grow extremely quickly — faster than exponential $c^n$ but slower than factorial $n!$.

#### Formulas and Calculation

There is no simple closed form, but several powerful formulas generate them:

**1. Recurrence with Binomial Coefficients:**
$$B_{n+1} = \sum_{k=0}^{n} \binom{n}{k} B_k$$
with $B_0 = 1$.

Intuition: To form a partition of $\{1,\dots,n+1\}$, choose the $k$ elements that will _not_ be in the same block as element $n+1$ — there are $\binom{n}{k}$ ways — and partition those $k$ elements arbitrarily in $B_k$ ways. The remaining $n-k$ elements join $n+1$'s block.

**2. Relation to Stirling Numbers of the Second Kind:**
Let $S(n,k) = \left\{ {n \atop k} \right\}$ be the number of ways to partition $n$ elements into exactly $k$ blocks. Then:
$$B_n = \sum_{k=0}^{n} S(n,k)$$
So Bell numbers are the row sums of the Stirling triangle. $B_n$ is the total number of partitions; $S(n,k)$ refines it by number of blocks.

**3. Dobinski's Formula — the analytic jewel:**
$$B_n = \dfrac{1}{e} \sum_{k=0}^{\infty} \dfrac{k^n}{k!}$$
This remarkable formula expresses an integer counting partitions as an infinite series involving $e$. It arises because the exponential generating function for Bell numbers is $e^{e^x -1}$.

#### The Bell Triangle (Aitken's Array)

Charles Sanders Peirce discovered a construction analogous to Pascal's triangle fifty years before Bell. It is now called the Bell triangle or Aitken's array. It lets you generate Bell numbers without binomial coefficients.

**Construction:**

1.  Start with $1$ in row 1.

2.  Each new row starts with the last number of the previous row.

3.  Each subsequent number in the row is the sum of the number to its left and the number directly above that left neighbor.

```
Row 1:  1
Row 2:  1   2
Row 3:  2   3   5
Row 4:  5   7   10   15
Row 5:  15  20  27   37   52
Row 6:  52  67  87   114  151  203
...
```

Formally, if $a_{n,1} = a_{n-1,n-1}$ and $a_{n,k} = a_{n,k-1} + a_{n-1,k-1}$ for $k>1$, then $a_{n,1} = B_{n-1}$ and $a_{n,n} = B_n$.

So the Bell numbers appear as the first element of each row (shifted by one) and also as the last element: Row $n$ starts with $B_{n-1}$ and ends with $B_n$. The first column is $B_0, B_1, B_2, B_3, \dots$

#### Practical Example: $B_3 = 5$

Take three distinct items $\{A, B, C\}$. How many ways to bucket them?

1.  **One block:** $\{A,B,C\}$ — $S(3,1)=1$ way

2.  **Two blocks — one pair + one singleton:** $\{A,B\}\{C\}$, $\{A,C\}\{B\}$, $\{B,C\}\{A\}$ — $S(3,2)=3$ ways

3.  **Three blocks:** $\{A\}\{B\}\{C\}$ — $S(3,3)=1$ way

Total $1+3+1=5 = B_3$.

For $B_4 = 15$, add the partitions of $\{A,B,C,D\}$: 1 way with 1 block, 7 ways with 2 blocks, 6 ways with 3 blocks, 1 way with 4 blocks.

#### Why Bell Numbers Matter

- **Rhyme Schemes:** $B_n$ is the number of possible rhyme schemes for an $n$-line poem. Each letter represents a rhyme sound; the blocks are lines that rhyme together. For a 4-line stanza, $B_4=15$ schemes: AAAA, AAAB, AABA, AABB, AABC, ABAA, ABAB, ABAC, ABBA, ABBB, ABBC, ABCA, ABCB, ABCC, ABCD.

- **Number Theory:** For a square-free integer $N = p_1 p_2 \dots p_n$ (product of $n$ distinct primes), the number of ways to write $N$ as a product of integers >1, where order doesn't matter, is $B_n$. For $30=2\cdot3\cdot5$, $B_3=5$ factorizations: $30$, $2\cdot15$, $3\cdot10$, $5\cdot6$, $2\cdot3\cdot5$.

- **Computer Science and Statistics:** Bell numbers appear in clustering — the number of ways to cluster $n$ data points — and in analyzing the complexity of set partitions, database equivalence, and the moments of the Poisson distribution. In fact, $B_n$ is the $n$-th moment of a Poisson(1) random variable, which is exactly what Dobinski's formula states.
