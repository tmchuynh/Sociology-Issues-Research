## Ramsey Theory

The study of conditions under which order must inevitably appear in large enough structures, no matter how you arrange things. Ramsey Theory proves that complete disorder is impossible at scale; large enough systems always contain unavoidable patterns — that "complete disorder is impossible", if a structure (such as a graph or set of numbers) is sufficiently large, a specific, ordered sub-structure will inevitably appear — the "order in chaos."

### The Theorem on Friends and Strangers

This is the most famous everyday example. In a finite gathering of $R(n,m)$ people there is a group of $n$ mutual friends, or a group of $m$ mutual strangers (not friends). $R(n,m)$ is the least number with this property (Klop).

**Finite Ramsey's Theorem** for two colors is also more casually known as the Theorem on Friends and Strangers when applied to the social context of parties

**Existence of Order**: It guarantees that for any two desired pattern sizes ($n$ and $m$), there exists a specific population size $R(n, m)$ large enough that a pattern must appear. No matter how you arrange the "friendship" or "stranger" links (the bicoloring), you cannot avoid having a group of $n$ friends or $m$ strangers.

**The "Least Number" Property**: The definition of $R(n, m)$ as the least number means that for any number smaller than $R(n, m)$, it is possible to find at least one arrangement (a coloring) where neither pattern exists.

While the "party" version is a popular way to explain it, the exact theorem is a pillar of combinatorics. In graph theory terms:

- **Complete Graph ( $K_N$ )**: A network where every pair of vertices (people) is connected by an edge.
- **Bicoloring**: Assigning one of two colors (usually red and blue) to every edge in the graph.
- **Monochromatic Clique**: A subset of vertices where every single connecting edge is the same color

**Common Values and Limits** (Klop):

- $R(3,3) = 6$: It states that at any party with at least six people, you are mathematically guaranteed to find either a group of three people who all know each other or three people who are all total strangers.

<figure>
  <img src="../images/r3_3.png" alt="Graph illustrating R(3,3) = 6 with red and blue edges showing friendship and stranger relationships">
  <figcaption>A party of 6 always contains a trio of mutual friends, or a trio of mutual strangers. Red edges indicate pairs of friends, blue lines connect strangers. The three green nodes indicate the (only) trio of mutual friends. Source: Klop 4.</figcaption>
</figure>

- $R(4,3) = R(3,4) = 9$:

<figure>
    <img src="../images/r3_4.png" alt="Graph illustrating R(4,3) = R(3,4) = 9 with red and blue edges">
    <figcaption>A party of 9 people will always contain a trio (red), or a quartet of mutual friends of mutual strangers (blue). Source: Klop 5.</figcaption>
</figure>

- $R(4,4) = 18$: For four mutual friends/strangers, you need a group of $18$
- $R(5,5)$: Despite the theorem proving these numbers exist, we still do not know the exact value for $R(5,5)$, which is currently bounded between $43$ and $48$.

### Hales-Jewett Theorem

The Hales-Jewett Theorem is often described as the "heart" of Ramsey Theory because it proves that order is inevitable in high-dimensional structures, even without relying on arithmetic or geometry.

#### The Core Idea: Unavoidable Winning Lines

The most intuitive way to understand it is through a high-dimensional game of Tic-Tac-Toe:

The Hales-Jewett theorem guarantees that for any number of players and board size, there is a dimension $H$ where an $n \times n \times \dots \times n$ ($H$-dimensional) tic-tac-toe game cannot end in a draw. It ensures a "monochromatic combinatorial line" (a complete row) is inevitable, , regardless of how the cells are marked, as long as it's played in sufficient dimensions, meaning one player must win, making the game non-trivial in high dimensions. 

The theorem proves that if you are playing an $n$-in-a-row game with $c$ players, there is a dimension $H$ so large that a draw is mathematically impossible. In standard 2D $3 \times 3$ Tic-Tac-Toe, a draw is common — the Hales-Jewett number hasn't been reached. There is enough "room" to place $X$'s and $O$'s in a way that blocks every possible line. But if you move that same $3 \times 3$ grid into a high enough dimension (a "hypercube"), one player must eventually complete a line.
- If you play $3$-in-a-row on a hypercube of high enough dimension, the board becomes so "dense" with potential lines that no matter where you move, you will eventually complete a line or be forced to let your opponent complete one.
- The "order" (a winning line) is mathematically forced by the size of the board. 
- The number of winning lines for $n^d$ (dimension $d$) tic-tac-toe is given by $\frac{(n+2)^d - n^d}{2}$.

While the theorem proves a winner exists, it doesn't tell you how to win. It only proves that the game cannot end in a "Cat's Game" (draw) once the dimensions are high enough. For a $3 \times 3$ board, the dimension required to guarantee a winner is actually quite low (it's proven that 3D $3 \times 3 \times 3$ cannot end in a draw), but for larger boards, the required dimension is unimaginably huge.

The Strategy-Stealing Argument: Because Hales-Jewett guarantees that a line must exist and Tic-Tac-Toe is a "perfect information" game (no hidden moves), mathematicians use the Strategy-Stealing Argument to prove who should win
- In any dimension where a draw is impossible, the first player (X) must have a winning strategy.
- The Logic: If the second player had a winning strategy, the first player could "steal" it by making a random move first and then following that strategy. Since having an extra piece on the board can never be a disadvantage in Tic-Tac-Toe, the first player would always win.

### Happy Ending Problem

The Happy Ending Problem is a foundational theorem in Ramsey Theory that bridges geometry and combinatorics. It states that for any given integer $n$, there is a minimum number of points $N(n)$ such that any set of at least $N(n)$ points in a plane (where no three points are in a line) must contain a subset of $n$ points that form a convex polygon.

**Why is it called the "Happy Ending" Problem?**

The problem got its unusual name because the research led to the marriage of the two mathematicians who first worked on it: Esther Klein and George Szekeres. Klein proposed the initial observation, Szekeres proved the general existence, and the two married in 1937.

**Known Values and the Conjecture**

Mathematicians have calculated the exact number of points needed for small polygons, but the general formula remains an unsolved mystery known as the Erdős–Szekeres Conjecture.

| Polygon Type  | $n$ Sides | Min. Points Required | Status                              |
| ------------- | --------- | -------------------- | ----------------------------------- |
| Triangle      | 3         | 3 points             | Trivial                             |
| Quadrilateral | 4         | 5 points             | Proved by Esther Klein              |
| Pentagon      | 5         | 9 points             | Proved by Endre Makai               |
| Hexagon       | 6         | 17 points            | Proved by Szekeres & Peters in 2006 |
| Heptagon      | 7         | Unknown              | Conjectured to be 33                |

The conjectured formula for $N(n)$ is $2^{n-2} + 1$.

**How the Proof Works (for $n=4$)**

To guarantee a convex quadrilateral, you only need 5 points. You can visualize this using a convex hull—imagine stretching a rubber band around the points:

- Case 1: If the rubber band touches 4 or 5 points, those points automatically form a convex shape.
- Case 2: If the rubber band only touches 3 points (forming a triangle) with 2 points inside, the line connecting the 2 internal points will always have 2 of the triangle's vertices on one side. Those 4 points together form the convex quadrilateral.

This theorem is a geometric version of the idea that complete disorder is impossible. Just as the Theorem on Friends and Strangers guarantees a "clique" of friends in a large enough group, the Happy Ending Problem guarantees a "clique" of convexity in a large enough set of points.

### Van der Waerden’s Theorem

Van der Waerden's Theorem states that if you take a long enough sequence of integers and color them with a finite number of colors, you are guaranteed to find an arithmetic progression (a sequence of "equally spaced" numbers) where all numbers share the same color.  
It is often described as proving that "complete disorder is impossible," because no matter how hard you try to mix the colors to avoid a pattern, a pattern will eventually emerge if the list of numbers is long enough.

**Key Concepts**

- Coloring: Imagine assigning each number in a list (like $1, 2, 3, \dots, N$) a color, such as Red or Blue.
- Arithmetic Progression (AP): This is a sequence where the difference between any two consecutive terms is constant (e.g., $3, 6, 9$ has a difference of 3).
- Monochromatic: This means all terms in the progression have the same color.

While the theorem proves these numbers exist, they grow incredibly fast. For just 2 colors and a 6-term progression, you already need a sequence of 1,132 numbers. For 2 colors and a 10-term progression, the number is so large that we do not even know what it is yet—only that it exists.

**A Concrete Example: $W(2, 3) = 9$**

The "Van der Waerden number" $W(r, k)$ tells you the minimum length of numbers ($N$) needed to guarantee a monochromatic progression of length $k$ using $r$ colors.

- For 2 colors and a 3-term progression, the number is 9.
- If you color the numbers 1 through 8, you can avoid a 3-term progression. For example: R R B B R R B B.
- However, as soon as you add the 9th number, you cannot avoid a progression. If you color 9 Red, you might complete $3, 6, 9$. If you color it Blue, you might complete $1, 5, 9$.

## Green-Tao Theorem

The Green-Tao Theorem states that the set of prime numbers contains arbitrarily long arithmetic progressions.  
In simpler terms, it means you can find sequences of prime numbers that are evenly spaced (like $5, 11, 17, 23, 29$, where each number is exactly $6$ apart) and that these sequences can be as long as you want.

**Key Aspects of the Theorem**

- Arbitrary Length: For any number $k$, there exists a sequence of $k$ prime numbers in an arithmetic progression.
- The Challenge of Primes: Most similar theorems (like Szemerédi's theorem) require a set of numbers to be "thick" or "dense" within the integers. Because prime numbers become extremely rare as they get larger, they have a "density" of zero, making this incredibly difficult to prove.
- Transference Principle: Ben Green and Terry Tao (the “Mozart of Math”) (who was awarded the Fields Medal in 2006 for this and other work) proved it by showing that primes, while rare, behave like a "dense" subset of a larger "pseudorandom" set of numbers.
- Infinitude: The theorem doesn't just say one such sequence exists for each length; it implies there are infinitely many such progressions for any given length.

**Record-Breaking Examples**

While the theorem proves these sequences exist for any length, finding actual sequences manually is computationally difficult because the common differences become massive.

- Length 5: $5, 11, 17, 23, 29$ (difference of $6$).
- Length 10: $199, 409, 619, 829, 1039, 1249, 1459, 1669, 1879, 2089$ (difference of $210$).
- Current Record: As of September 2019, the longest known arithmetic progression of primes has a length of 27.

## Different Types of Numbers

### Narcissistic Numbers

A narcissistic number (also known as an Armstrong number or a plus perfect number) is an $n$-digit integer that is exactly equal to the sum of its own digits each raised to the $n$-th power. They are essentially "full of themselves," returning to their original value after this specific mathematical operation.

#### How They Work

To determine if a number is narcissistic, follow these steps:

1.  Count the digits in the number ($n$).
2.  Raise each digit to the $n$-th power.
3.  Sum these results. If the total equals the original number, it is narcissistic.

Classic Examples:

- **Single digits (0–9)**: All are narcissistic because any digit $d$ raised to the first power ($d^1$) is simply $d$.
- **153 (3 digits)**: $1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153$.
- **370 (3 digits)**: $3^3 + 7^3 + 0^3 = 27 + 343 + 0 = 370$.
- **1634 (4 digits)**: $1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634$.

#### Key Facts and Limitations

- **Finite Sequence**: There are exactly 88 narcissistic numbers in base 10.
- **Upper Bound**: It has been proven that no narcissistic number can have more than 60 digits. This is because for $n > 60$, the sum of the digits ($n \times 9^n$) will always be smaller than the smallest $n$-digit number ($10^{n-1}$).
- **Largest Number**: The largest base-10 narcissistic number has 39 digits: $115,132,219,018,763,992,565,095,597,973,971,522,401$.
- **Mathematical Interest**: While popular in recreational mathematics and programming exercises, famous mathematician G.H. Hardy once dismissed them as "odd facts" that hold little appeal for professional mathematicians.

**Common Narcissistic Numbers (Base 10):**

- **3 Digits**: 153, 370, 371, 407
- **4 Digits**: 1634, 8208, 9474
- **5 Digits**: 54748, 92727, 93084

#### Base Changes

Narcissistic numbers exist in every base, but the specific numbers that qualify change because the digit values and the power (the number of digits) are tied to the base system.

##### How it Changes

- Binary (Base 2): Only 0 and 1 are narcissistic. Because every other number is a sum of $1^n$, it quickly becomes impossible for the sum to "catch up" to the value of the binary string.
- Base 3 (Ternary): Besides the single digits, 17 is narcissistic in base 3. In ternary, 17 is written as $122_3$.
- Calculation: $1^3 + 2^3 + 2^3 = 1 + 8 + 8 = 17$.
- Base 4 (Quaternary): An example is 35, which is written as $203_4$.
- Calculation: $2^3 + 0^3 + 3^3 = 8 + 0 + 27 = 35$.

##### Comparison of Bases

As the base increases, the density and maximum possible size of these numbers change.

| Base | Representative Narcissistic Numbers (Decimal Value)                |
| ---- | ------------------------------------------------------------------ |
| 2    | 0, 1                                                               |
| 3    | 0, 1, 2, 5 ($12_3$), 8 ($22_3$), 17 ($122_3$)                      |
| 4    | 0, 1, 2, 3, 28 ($130_4$), 29 ($131_4$), 35 ($203_4$), 43 ($223_4$) |
| 10   | 0-9, 153, 370, 371, 407, 1634, 8208, 9474, ...                     |
| 16   | 0-F, 156 ($126_{16}$), 1014 ($3F6_{16}$), 1541 ($605_{16}$)        |

##### Why Bases Matter

In any base $b$, a number with $k$ digits can be at most $k \cdot (b-1)^k$. As $k$ grows, the value of the number ($b^{k-1}$) eventually grows much faster than this sum. This means every base has a finite number of narcissistic numbers. For example, while base 10 has exactly 88, a larger base like hexadecimal (base 16) has many more, but still a limited total.

### Kaprekar numbers

A Kaprekar number is a natural number with a specific "split-square" property: when you square the number, you can split the result into two parts that, when added together, return the original number. For example, $45^2 = 2025$, and $20 + 25 = 45$. They are named after the Indian recreational mathematician D.R. Kaprekar, who first described them in 1980.

A $k$-digit number $n$ is a Kaprekar number if $n^2$ can be split into a right part of $k$ digits and a left part such that their sum is $n$.

Some numbers can have a leading zero in the right part, such as $99^2 = 9801 \rightarrow 98 + 01 = 99$.

Formally, a $n$-Kaprekar number $k \geq 1$ (for $n = 1, 2, \dots$ ) satisfies the pair of equations:

$$k=q+r, \qquad k^2 = q \times 10^n + r$$

where $q \geq 1$ and $0 \leq r \le 10^n$

#### How to Identify a Kaprekar Number

To check if a number $k$ with $n$ digits is a Kaprekar number:

1.  Square the number: Calculate $k^2$.
2.  Split the square: Divide $k^2$ into two parts ($q$ and $r$), where the right part ($r$) has exactly $n$ digits.
3.  Sum the parts: Add $q + r$. If the sum equals $k$, it is a Kaprekar number.

**Example**:

- $9$: $9^2 = 81 \rightarrow 8 + 1 = 9$
- $45$: $45^2 = 2025 \rightarrow 20 + 25 = 45$
- $297$: $297^2 = 88209 \rightarrow 88 + 209 = 297$
- $703$: $703^2 = 494209 \rightarrow 494 + 209 = 703$
- $4879$: $4879^2 = 23804641 \rightarrow 238 + 4641 = 4879$
- $538461$: $538461^2 = 289940248521 \rightarrow 289940 + 248521 = 538461$

**First few Kaprekar numbers (Base 10)**:
$1, 9, 45, 55, 99, 297, 703, 999, 2223, 2728, 4879\dots$

#### Common Properties

- **Pairs to Powers of 10**: If an $n$-digit number $k$ is a Kaprekar number, then $10^n - k$ is often also a Kaprekar number (e.g., $45 + 55 = 100$).
- **Nines Pattern**: All numbers consisting only of the digit 9 (like 9, 99, 999) are Kaprekar numbers.
- **Non-Zeros**: By convention, the right part ($r$) of the split cannot be zero, which excludes powers of 10 like 10 or 100 from being Kaprekar numbers.

#### Kaprekar's Constant (A Common Confusion)

While related to the same mathematician, the Kaprekar number is different from Kaprekar's Constant (6174), which relates to a routine of rearranging and subtracting digits of 4-digit numbers. Kaprekar's Constant is the "fixed point" you reach when you repeatedly subtract the smallest arrangement of a 4-digit number's digits from its largest arrangement (e.g., $8532 - 2358 = 6174$).

#### Comparison of Kaprekar Numbers by Base

While 1 is a Kaprekar number in every base, other values change as the base increases.

| Base    | Kaprekar Numbers (Shown in Decimal Value) | Examples in Base Representation                                |
| ------- | ----------------------------------------- | -------------------------------------------------------------- |
| Base-10 | 1, 9, 45, 55, 99, 297, 703, ...           | $45^2 = 2025 \rightarrow 20+25 = 45$                           |
| Base-12 | 1, 11, 66, 78, 143, ...                   | $B_{12}^2 = A1_{12} \rightarrow A + 1 = B_{12}$ (Decimal $11$) |
| Base-16 | 1, 6, 15, 85, 171, 205, 255, ...          | $F_{16}^2 = E1_{16} \rightarrow E + 1 = F_{16}$ (Decimal $15$) |

**Key Differences**

- The "Nines" Rule: In any base $b$, the value $b-1$ is always a Kaprekar number (e.g., 9 in base-10, B in base-12, and F in base-16).
- Number Density: Some bases have many more Kaprekar numbers than others within the same range. For instance, there are more Kaprekar numbers below 500 in base-16 than in base-12.
- Unitary Divisors: Mathematically, $n$-digit Kaprekar numbers in base $b$ correspond to the unitary divisors of $b^n - 1$, which naturally vary as the base changes.

### Catalan numbers

The Catalan numbers: $1, 2, 5, 14, 42, 132, 429, 1430, 4862, 16796, 58786, 208012, 742900, 2674440, 9694845, \dots$, named after Eugéne Charles Catalan (1814--1894), arise in a number of problems in combinatorics.

Catalan numbers are a sequence of natural numbers ($1, 1, 2, 5, 14, 42, \dots$) that appear in numerous counting problems in combinatorics. Named after the Belgian mathematician Eugène Charles Catalan, these numbers typically represent the number of ways to arrange or divide objects into recursive structures, such as trees, paths, or polygons. Among other applications, Catalan numbers describe

- **Polygons:** the number of ways a polygon with $n+2$ sides can be cut into $n$ triangles.
- **Parentheses:** the number of ways in which parentheses can be placed in a sequence of numbers to be multiplied, two at a time.
- **Trees:** the number of rooted, trivalent trees with $n+1$ nodes.
- **Paths:** the number of paths of length $2n$ through an $n \times n$ grid that do not rise above the main diagonal,
- **Stairs:** the number of ways to decompose a staircase-shaped figure with $n$ steps into $n$ rectangles.

#### Formula and Calculation

The $n$-th Catalan number, denoted as $C_n$, is most commonly defined by the formula:
$$C_n = \frac{1}{n+1} \binom{2n}{n} = \frac{(2n)!}{(n+1)!n!}$$

The sequence can also be calculated using a recurrence relation, where each new number is the sum of products of previous ones:
$$C_{n+1} = \sum_{i=0}^{n} C_i C_{n-i}$$
The first few values of $C_n$ are:

| $n$   | $0$ | $1$ | $2$ | $3$ | $4$  | $5$  | $6$   | $7$   | $8$   | $9$   |
| ----- | --- | --- | --- | --- | ---- | ---- | ----- | ----- | ----- | ----- |
| $C_n$ | $1$ | $1$ | $2$ | $5$ | $14$ | $42$ | $132$ | $429$ | $132$ | $429$ |

<figure>
  <img src="../images/Catalan_Numbers_8_Sides.png" alt="Illustration of the number of ways a polygon with 8 sides can be cut">
  <figcaption>The number of ways a polygon with n+2 sides can be cut into n triangles. Source: <a href="https://mathshistory.st-andrews.ac.uk/Extras/Catalan/#polygon">MacTutor</a>.</figcaption>
</figure>
