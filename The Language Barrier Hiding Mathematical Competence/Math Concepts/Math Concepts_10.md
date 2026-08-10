### Stirling Numbers

Stirling numbers, named after James Stirling (1692–1770), are two related triangular arrays of numbers that are fundamental in combinatorics. They both count ways to arrange $n$ distinct objects, but they answer two different questions:

- **First kind:** How many ways to arrange them into $k$ _cycles_ (circular orderings)?
- **Second kind:** How many ways to group them into $k$ _sets_ (unordered collections)?

The distinction between sets and cycles is the core of the theory.

#### Stirling Numbers of the Second Kind

Denoted $\displaystyle S(n,k)$ or $\displaystyle \left\{ {n \atop k} \right\}$, pronounced "$n$ brace $k$".

**Combinatorial Meaning:** $S(n,k)$ is the number of ways to partition a set of $n$ labeled elements into exactly $k$ non-empty, unlabeled subsets.

Example: $n=3$ friends $\{A,B,C\}$ into $k=2$ groups.
$$\{A,B\}\{C\},\; \{A,C\}\{B\},\; \{B,C\}\{A\}$$
So $S(3,2)=3$. The groups are unlabeled — $\{A,B\}\{C\}$ is the same as $\{C\}\{A,B\}$.

**Values:** $S(n,0)=0$ for $n>0$, $S(0,0)=1$, $S(n,1)=1$, $S(n,n)=1$, $S(n,2)=2^{n-1}-1$.

**Recurrence Relation:**
$$S(n,k) = k \cdot S(n-1,k) + S(n-1,k-1)$$

_Proof idea:_ Consider element $n$. Either:

1. **It joins one of the $k$ existing blocks formed by the other $n-1$ elements**: $k \cdot S(n-1,k)$ ways, or

2. **It forms a new singleton block by itself**: $S(n-1,k-1)$ ways.

**Explicit Formula (Inclusion-Exclusion):**
$$S(n,k) = \dfrac{1}{k!} \sum_{j=0}^{k} (-1)^{k-j} \binom{k}{j} j^n$$

**Relation to Bell Numbers:** Summing across $k$ gives the total number of partitions:
$$B_n = \sum_{k=0}^{n} S(n,k)$$

#### Stirling Numbers of the First Kind

Denoted $\displaystyle s(n,k)$ (signed) or $\displaystyle c(n,k) = \left[ {n \atop k} \right]$ (unsigned), pronounced "$n$ bracket $k$".

**Combinatorial Meaning:** $c(n,k)$ counts the number of ways to arrange $n$ distinct elements into exactly $k$ disjoint cycles.

A cycle is a circular ordering where rotation is considered the same but order matters: $(A B C)$, $(B C A)$, $(C A B)$ are the same cycle, but $(A C B)$ is different. Think of $n$ people sitting around $k$ identical round tables, where who sits to the left of whom matters, but the table has no distinguished seat.

Example: $n=3$, $k=2$. Cycles of 3 elements into 2 cycles must be one 2-cycle and one 1-cycle. The 1-cycle can be $A$, $B$, or $C$ (3 choices), the remaining two elements form one 2-cycle which is unique up to rotation. So $c(3,2)=3$, same as $S(3,2)$ in this case, but in general $c(n,k) \ge S(n,k)$.

**Signed vs. Unsigned:**

- Unsigned $\displaystyle c(n,k) = \left[ {n \atop k} \right] \ge 0$ counts cycles.

- Signed $s(n,k) = (-1)^{n-k} c(n,k)$. The signed version appears in algebra.

**Recurrence Relation:**
$$c(n,k) = (n-1) \cdot c(n-1,k) + c(n-1,k-1)$$

_Proof idea:_ Consider element $n$. Either:

1. **It is inserted into an existing cycle of the $n-1$ other elements. A cycle with $m$ elements has $m$ insertion points, so across all cycles there are $n-1$ places to insert $n$**: $(n-1) c(n-1,k)$ ways, or

2. **It forms a new 1-cycle by itself**: $c(n-1,k-1)$ ways.

Notice the difference from the second kind: $k$ vs. $(n-1)$.

#### Comparison Table for $n=4$

| $k$     | $S(4,k)$ — Partitions into $k$ sets                                  | $c(4,k)$ — Permutations into $k$ cycles          |
| :------ | :------------------------------------------------------------------- | :----------------------------------------------- |
| 1       | 1 — $\{ABCD\}$                                                       | 6 — $(ABCD)$ has $(4-1)! = 6$ distinct rotations |
| 2       | 7 — 4 ways of type 3+1, 3 ways of type 2+2                           | 11 — 8 of type 3+1, 3 of type 2+2                |
| 3       | 6 — choose which pair is together: $\displaystyle\binom{4}{2}/2 = 6$ | 6 — same 6 partitions, but 2-cycles are forced   |
| 4       | 1 — $\{A\}\{B\}\{C\}\{D\}$                                           | 1 — $(A)(B)(C)(D)$                               |
| **Sum** | $1+7+6+1=15 = B_4$                                                   | $6+11+6+1=24 = 4!$                               |

The row sum of the second kind is the Bell number $B_n$. The row sum of the first kind (unsigned) is $n!$ — the total number of permutations — because every permutation decomposes uniquely into cycles.

#### Key Mathematical Use: Change of Basis

Stirling numbers are not just counting tools; they are the change-of-basis matrices between two natural bases for polynomials.

Let $x^{\underline{n}} = x(x-1)(x-2)\cdots(x-n+1)$ be the falling factorial.

- **First kind (signed) converts powers to falling factorials:**

  $$x^{\underline{n}} = \sum_{k=0}^{n} s(n,k) x^k$$
  Example: $x^{\underline{3}} = x(x-1)(x-2) = x^3 -3x^2 +2x$, so $s(3,3)=1, s(3,2)=-3, s(3,1)=2$.

- **Second kind converts falling factorials back to powers:**

  $$x^n = \sum_{k=0}^{n} S(n,k) x^{\underline{k}}$$
  Example: $x^3 = 1\cdot x^{\underline{1}} + 3\cdot x^{\underline{2}} + 1\cdot x^{\underline{3}}$.

Because of this, the infinite lower-triangular matrices $[s(n,k)]$ and $[S(n,k)]$ are inverses of each other. This duality underlies much of finite difference calculus and the theory of moments.

### Happy / Unhappy Numbers

A happy number is defined by what happens when you repeatedly replace it by the sum of the squares of its decimal digits. If this process eventually reaches $1$, the number is happy; if it falls into a loop that never includes $1$, it is unhappy.

This is a simple dynamical system on the integers, and remarkably, it has only two possible fates for every starting number.

#### How It Works

Define the digit-square-sum function:  
$$S(n) = \text{sum of squares of base-10 digits of } n$$

For example, $S(23) = 2^2 + 3^2 = 13$.

Iterate: $n_0 = n$, $n_1 = S(n_0)$, $n_2 = S(n_1)$, ...

**Example 1 — Happy: $23$**  
$$23 \to 2^2+3^2=13 \to 1^2+3^2=10 \to 1^2+0^2=1$$
Since the sequence reaches $1$, $23$ is happy.

**Example 2 — Happy: $19$**  
$$19 \to 1^2+9^2=82 \to 8^2+2^2=68 \to 6^2+8^2=100 \to 1^2+0^2+0^2=1$$
So $19$ is happy.

**Example 3 — Unhappy: $36$**  
$$36 \to 3^2+6^2=45 \to 4^2+5^2=41 \to 17 \to 50 \to 25 \to 29 \to 85 \to 89 \to 145 \to 42 \to 20 \to 4 \to 16 \to 37 \to 58 \to 89...$$
It never hits $1$, it enters a loop.

Every unhappy number eventually enters the same 8-cycle:  
$$4 \to 16 \to 37 \to 58 \to 89 \to 145 \to 42 \to 20 \to 4$$

**Why only two fates? Proof by descent:** For any $n \ge 1000$, $S(n) < n$. Indeed, for a $k$-digit number $n < 10^k$, $S(n) \le k \cdot 9^2 = 81k$, while $10^{k-1} \le n$. For $k \ge 4$, $81k < 10^{k-1}$. So any number $\ge 1000$ strictly decreases under $S$.

Therefore iteration from any starting $n$ must eventually drop below $1000$ and stay below $1000$ forever. Checking all $1 \le n < 1000$ — a finite computation — shows the only attractors are the fixed point $1$ and the 8-cycle above. Hence every number is either happy or unhappy.

**First few Happy numbers:**  
$$1, 7, 10, 13, 19, 23, 28, 31, 32, 44, 49, 68, 70, 79, 82, 86, 91, 94, 97, 100, 103, 109, 129, \dots$$

#### Properties of Happy and Unhappy Numbers

1. **Heredity of Happiness:** If a number is happy, then all numbers in its sequence are also happy. If $23$ is happy via $23 \to 13 \to 10 \to 1$, then $13$, $10$, and $1$ are happy. Conversely, if a number is unhappy, all numbers in its sequence are unhappy.

   In Example 2, since $36$ is unhappy, every number in its chain — $45, 41, 17, 50, 25, 29, 85, 89, 145, 42, 20, 4, 16, 37, 58$ — is also unhappy.

2. **Permutation Invariance:** The happiness of a number is unaffected if its digits are rearranged in any manner. Since $S(n)$ depends only on the multiset of digits, not their order, $S(19)=S(91)=82$. So $19$ happy $\implies$ $91$ happy. Any permutation of a happy number is happy; any permutation of an unhappy number is unhappy.

3. **Zero Invariance:** Inserting or removing zeros anywhere does not affect happiness, because $0^2=0$. So if $19$ is happy, $109, 1009, 10009$ are all happy. If $20$ is unhappy, $200, 2000, 2$ are all unhappy. This also means $S(n)$ can be thought of as operating on the non-zero digits only.

4. **Infinitude of Both Types:**

   There are infinitely many happy numbers and infinitely many unhappy numbers.

   _Proof:_ $1$ is happy. Then $10^k$ is happy for all $k$ (by zero invariance), so infinitely many happy. For unhappy, $2$ is unhappy ($2 \to 4 \to$ cycle), then $2\cdot10^k$ is unhappy for all $k$, so infinitely many unhappy. In fact, both sets have positive lower density.

5. **Equivalence Class:** Properties 2 and 3 together mean happiness is a property of the multiset of non-zero digits, not the number itself. $112$, $121$, $211$, $1120$, $1012$ all share the same fate.

#### Key Facts and Variations

- **Density:** What fraction of numbers are happy? Empirically about $15-20\%$ up to large $X$. Rigorous bounds: upper asymptotic density $<0.19$ and lower $>0.12$. It is not known whether a natural density exists — i.e., whether $\dfrac{\#\{n \le X : n \text{ happy}\}}{X}$ converges — this is an open problem.

- **Happy primes:** A happy number that is prime. $7, 13, 19, 23, 31, 79, 97, 103, 109, 139, 167, \dots$. Since all numbers $>5$ ending in $5$ are composite, happy primes must end in $1,3,7,9$.

- **Consecutive happy numbers:** The smallest consecutive pair is $31,32$. There are runs of arbitrary length? It is conjectured but not proved that arbitrarily long runs of happy numbers exist. The longest known run as of 2024 is length 12.

- **Base dependence:** Like Narcissistic numbers, happiness depends on base. The function $S_b(n)$ = sum of squares of base-$b$ digits always eventually cycles. $1$ is always a fixed point, but the other cycles depend on $b$. For example, $7$ is happy in base 10 ($7\to49\to97\to130\to10\to1$) but unhappy in base 2. In base 2, $S_2(n)$ is just the count of 1-bits, so every number eventually reaches $1$.

- **Generalization — $k$-happy:** Replace squares with $k$-th powers. Standard happy is $2$-happy. $k=3$ gives "cubed happy" numbers, etc. The same bounding argument shows every $k$ has finitely many attractors.

Happy numbers are not deep in algebraic number theory, but they are a perfect classroom example of iteration, attractors, invariants, and proof by descent: to prove an infinite process has only two outcomes, you show it must eventually enter a finite, checkable region.

### Harshad / Niven Numbers

A Harshad number — from Sanskrit _harṣa_ meaning "great joy" and _da_ meaning "to give," literally "joy-giver" — also called a Niven number after Canadian mathematician Ivan M. Niven, who studied them in a 1977 paper, is an integer divisible by the sum of its digits in base 10.

The term Harshad was coined by the Indian recreational mathematician D. R. Kaprekar — the same Kaprekar of Kaprekar numbers and Kaprekar's constant 6174. He loved digit-dependent properties.

> **Definition:** Let $s_{10}(n)$ be the sum of the decimal digits of $n$. Then $n$ is Harshad (or Niven) if $s_{10}(n) \mid n$, i.e. $n \mod s_{10}(n) = 0$.

- **Single digits:** Every number from 1 through 9 is trivially Harshad, since $s(d)=d$ and $d\mid d$. By convention we include $10$ as Harshad because $1+0=1$ divides $10$.

- **Origin of name:** Harshad = joy-giver, Niven = after Ivan Niven. Both names are used interchangeably in literature; "Harshad" is more common in recreational contexts, "Niven" in formal papers.

- **Universal numbers:** Only $1, 2, 4, 6$ are Harshad numbers in _every_ number base. These are called all-Harshad or all-Niven numbers.

#### How to Check

1. **Sum the decimal digits**: $s(n)$.

2. **Divide**: is $n \mod s(n) = 0$?

**Examples:**

- **$18$**: $s=1+8=9$, $\dfrac{18}{9}=2$ Harshad

- **$21$**: $s=2+1=3$, $\dfrac{21}{3}=7$ Harshad

- **$1729$ — the Hardy-Ramanujan taxicab number**: $s=1+7+2+9=19$, $\dfrac{1729}{19}=91$ Harshad

- **$19$**: $s=1+9=10$, $19 \mod 10 =9$ not Harshad

- **$100$**: $s=1$, $100\mod1=0$ — any power of 10 is Harshad

**Sequence (base 10):** All $1-10$ are Harshad, then
$$12, 18, 20, 21, 24, 27, 30, 36, 40, 42, 45, 48, 50, 54, 60, 63, 70, 72, 80, 81, 84, 100, 102, 108, 110, 111, 112, \dots$$

$111$ is interesting: $1+1+1=3$, $\dfrac{111}{3}=37$.

#### Key Properties

1. **All single digits are Harshad** — by definition.

2. **Infinitude:** There are infinitely many Harshad numbers. Simple families: $10^k$, $a\cdot10^k$ for $1\le a\le9$, $19\cdot10^k$? Actually $a\cdot10^k$ has digit sum $a$, and $a\mid a\cdot10^k$ always. So infinite.

3. **Density:** The natural density of Harshad numbers is 0 — the proportion up to $X$ tends to $0$ as $X\to\infty$ because $s(n)$ is at most $9\cdot\log_{10}X$, much smaller than $n$, so divisibility becomes rarer. However they are locally abundant: every block of 10 consecutive integers contains at least one Harshad? No, that is false for large $n$, but Jean-Marie De Koninck and Nicolas Doyon proved there are arbitrarily long runs of consecutive non-Harshad numbers. Empirically, about $20-30\%$ of numbers below $1,000$ are Harshad, about $14\%$ below $100,000$.

4. **Multiple Harshad / MFA Numbers:**  
   A Multiple Harshad Number is one where repeatedly dividing by digit sum stays Harshad.
   - Let $n_0=n$, $n_{i+1}=n_i / s(n_i)$ if divisible.

   - If this can be done $k$ times and each $n_i$ is Harshad, $n$ has MFA-degree $k$.

   Example: $2016$

   $s(2016)=9$, $\dfrac{2016}{9}=224$ — $224$ is Harshad ($s=8$)

   $\dfrac{224}{8}=28$ — $28$ is Harshad? $s=10$, $28\mod10\neq0$ — so stops. So $2016$ is MFA of degree 1.

   A stronger example: $378$

   $\dfrac{378}{(3+7+8=18)}=21$, $21$ Harshad, $\dfrac{21}{3}=7$, $7$ Harshad. So $378$ can be reduced to a single digit through Harshad divisions.

5. **All-Harshad Numbers (AHN):** Numbers that are Harshad in every base $b\ge2$. Grundman proved in 1994 that only $1,2,4,6$ have this property. Proof sketch: In base $b$, $s_b(n)$ can vary; for large $b>n$, $s_b(n)=n$, so $n\mid n$ always, but for $b=n-1$, $n = 11_b$, $s_b=2$, so $n$ must be even, etc., leaving only $1,2,4,6$.

6. **Harshad Primes:** A prime that is also Harshad can only be $2,3,5,7$. Reason: For $n\ge11$, $2 \le s(n) \le 9\cdot\text{digits} < n$. If $s(n)>1$ and $s(n)\mid n$, then $n$ has a proper divisor $>1$, so composite. Thus any multi-digit Harshad must be composite unless $s(n)=1$, which means $n=10^k$, also composite. So no multi-digit Harshad prime exists.

#### Generalizations

- **$b$-Niven:** Harshad concept in base $b$: $s_b(n)\mid n$. The theory changes with $b$ because $s_b(n)$ changes.

- **Strict Harshad:** $\dfrac{n}{s(n)}$ is also Harshad, and $s(n)$ and $\dfrac{n}{s(n)}$ are coprime.

- **Connection to 9:** $10 \equiv 1 \mod 9$, so $n \equiv s(n) \mod 9$. Thus if $n$ is Harshad, $\dfrac{n}{s(n)}$ is not arbitrary — $n \equiv 0 \mod s(n)$ and $n \equiv s(n) \mod 9$ gives constraints $\mod 9$. This is the generalization of the familiar divisibility rule "a number is divisible by 9 iff its digit sum is."

Why they matter beyond puzzles: Harshad numbers are the simplest example of a base-dependent divisibility sequence, used to teach modular arithmetic, and they appear in the study of $b$-Niven numbers, which have connections to the distribution of $s_b(n)$ modulo $m$ — a classic problem in uniform distribution.

### Wieferich Primes

They come from asking what happens when you strengthen Fermat's Little Theorem by one power of $p$.

**Fermat's Little Theorem:** For prime $p$ not dividing $a$,
$$a^{p-1} \equiv 1 \mod p$$

So $p$ always divides $a^{p-1}-1$. Arthur Wieferich asked in 1909: When does $p^2$ divide $a^{p-1}-1$? When does the congruence hold $\mod p^2$ instead of just $\mod p$?

> **Definition:** A prime $p$ is a Wieferich prime base $a$ if
> $$a^{p-1} \equiv 1 \mod p^2$$
> In other words, $p^2 \mid a^{p-1}-1$.
> When no base is mentioned, base $2$ is the default: $2^{p-1} \equiv 1 \mod p^2$.

For base $2$, this is $p^2$ divides the Mersenne number $M_{p-1}=2^{p-1}-1$.

**Example:** $p=1093$ is Wieferich base 2:
$$2^{1092} = 1 + k\cdot 1093^2$$
with $k = 364245589...$ large. The key point is the remainder upon division by $1093^2 = 1,194,649$ is $1$. So $1093$ divides $2^{1092}-1$ twice.

For contrast, take $p=5$ non-Wieferich:
$2^4=16$, $16-1=15$, divisible by $5$ but not by $25$. So $5$ is not Wieferich base 2.

#### Key Facts and Properties

**1. Known primes — Extreme Rarity:**
Only two base-2 Wieferich primes are known:
$$1093 \quad \text{and} \quad 3511$$

- $1093$ was found by Meissner in 1913.
- $3511$ was found by Beeger in 1922.

Despite enormous effort, no third is known.

**2. Rarity and Search Limits:**
Computer searches have tested all primes up to $>1.45 \times 10^{17}$ as of 2023 — that is 145 quadrillion — without finding any additional base-2 Wieferich primes. PrimeGrid, Dorais-Klyve, and others use efficient sieving using $a^{p-1} \mod p^2$ can be computed with $O(\log p)$ modular multiplications using fast exponentiation, but the sheer range makes it hard.

Heuristic: For random prime $p$, $a^{p-1} \mod p^2$ is roughly uniformly distributed among the $p$ multiples of $p$ that are $1 \mod p$. So probability it is $1 \mod p^2$ is $1/p$. Expected number up to $X$ is $\sum_{p\le X} 1/p \sim \log\log X$, which diverges but agonizingly slowly: $\log\log(10^{17}) \approx 3.66$, consistent with 2 found. This suggests infinitely many exist, but the next may be beyond $10^{18}$.

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
$$q_p(a) = \dfrac{a^{p-1}-1}{p}$$

Fermat's theorem says $q_p(a)$ is integer. Wieferich condition is $q_p(a) \equiv 0 \mod p$.

$q_p(a)$ behaves like a logarithm mod $p$ — called the $p$-adic logarithm — satisfying $q_p(ab) \equiv q_p(a)+q_p(b) \mod p$. Wieferich primes are where this logarithm vanishes.

#### Why They Matter Today

- **Mersenne numbers:** $p$ is Wieferich base 2 iff $2$ has extra ramification in the $p$-th cyclotomic field $\mathbb{Q}(\zeta_p)$, and iff the order of $2$ mod $p^2$ equals order mod $p$. This connects to the theory of cyclotomic fields.
- **Cryptography and primality testing:** Some base-$a$ pseudoprime tests fail more often when $p$ is Wieferich. The search for Wieferich primes tests fast modular exponentiation mod $p^2$.
- **$abc$ and Wieferich:** Silverman proved $abc$ conjecture implies infinitely many non-Wieferich primes base $a$. So Wieferich primes sit at intersection of elementary congruence and deep conjectures.
- **Wieferich pairs:** $(a,p)$ where $p$ Wieferich base $a$ and $a$ Wieferich base $p$ — only known pair is $(2,1093)$? Actually $2^{1092}\equiv1\mod1093^2$ and $1093^{1}\equiv1\mod4$? Not symmetric. True Wieferich pairs are rare.

In summary: Every prime $p$ divides $2^{p-1}-1$ once. Wieferich primes are the extremely rare primes that divide it twice. Only $1093$ and $3511$ are known, with no third below $1.45\times10^{17}$, and their original fame came from Arthur Wieferich's 1909 theorem linking them to Fermat's Last Theorem.

### Wilson Primes

They come from one of the most elegant theorems in elementary number theory.

**Wilson's Theorem (1770):** For an integer $p>1$,
$$p \text{ is prime } \iff (p-1)! \equiv -1 \mod p$$

That is, $p$ divides $(p-1)!+1$ exactly when $p$ is prime. For example, $4!+1=25$, divisible by $5$; $5!+1=121$, not divisible by $6$.

Wilson primes ask: when does this congruence hold one power higher?

> **Definition:** A prime $p$ is a Wilson prime if
> $$(p-1)! \equiv -1 \mod p^2$$
> i.e., $p^2 \mid (p-1)! + 1$.

If Wilson's Theorem says $p$ divides $(p-1)!+1$ once, a Wilson prime is a prime where $p$ divides it twice.

#### The Math Behind Wilson Primes

- **Normal Wilson:** For every prime $p$, $(p-1)! = -1 + k\cdot p$ for some integer $k$. The quotient $k = \dfrac{(p-1)!+1}{p}$ is called the Wilson quotient, often denoted $W(p)$.

- **The Squared Rule:** $p$ is Wilson iff $W(p) \equiv 0 \mod p$, i.e., $k$ is itself divisible by $p$. So $(p-1)!+1 = k\cdot p = (m\cdot p)\cdot p = m\cdot p^2$.

Equivalently, using the concept of Wilson quotient:
$$W(p) = \dfrac{(p-1)!+1}{p}$$
$$p \text{ is Wilson } \iff W(p) \equiv 0 \mod p$$

This parallels Wieferich primes, where the Fermat quotient $q_p(a) = \dfrac{a^{p-1}-1}{p}$ is $0 \mod p$.

#### Known Values and Verification

Only three Wilson primes are known despite extensive search:

**1. $p=5$**
$$4! = 24$$
$$(4!+1)/5^2 = 25/25 =1$$
So $5^2 \mid 25$ , $W(5)=5$.

**2. $p=13$**
$$12! = 479001600$$
$$12!+1 = 479001601$$
$$479001601 / 13^2 = 479001601 /169 = 2834329$$
Integer , so $13$ is Wilson. $W(13)=2834329 \equiv 0 \mod 13$? $2834329/13=218025.3$? Actually $2834329 = 13 \times 218025 + 4$ — wait, check definition: The standard check is $W(13) \mod 13 =0$ must hold. Compute $W(13)=36846277$, $36846277/13=2834329$, which is divisible? No, for Wilson we need $W(p)/p$ integer. Let's do clean: $(12!+1)/13 = 36846277$. Then $36846277 \mod 13 =0$, so $13^2$ divides $12!+1$.

**3. $p=563$**
$562!$ has $1300+$ digits — far too large to write out. But using modular arithmetic, we can compute $562! \mod 563^2$ without computing $562!$ itself by multiplying modulo $563^2$ at each step:
$$1\cdot2 \mod 316969 \to \dots \to 562 \mod 316969$$
The result is $316968 \equiv -1 \mod 316969$, so $563^2 \mid 562!+1$

#### Facts and Mysteries

- **Extreme Rarity:** Wilson primes are among the rarest known prime types. As of 2024, computers have checked all primes up to $2\times10^{13}$ — twenty trillion — and found no fourth Wilson prime. The search requires $O(p)$ modular multiplications per $p$ with numbers of size $p^2$, so it is computationally expensive.

- **Heuristic Expectation:** How many should there be? For a random prime $p$, $(p-1)! \mod p^2$ is roughly uniformly distributed among the $p$ residues that are $-1 \mod p$ (by Wilson's Theorem). So probability that it is exactly $-1 \mod p^2$ is $1/p$.

  Expected number of Wilson primes up to $X$:
  $$\sum_{p \le X} \dfrac{1}{p} \sim \log\log X$$

  This diverges, but incredibly slowly: $\log\log(10^{13}) \approx 3.3$. Since we have found 3 up to $2\times10^{13}$, this matches heuristic perfectly. It predicts about 1 more Wilson prime up to $10^{100}$.

  This is why mathematicians believe infinitely many Wilson primes exist, but we may never find the fourth — the next one could be astronomically large.

- **Unsolved Questions:**
  1.  Is there a fourth Wilson prime?
  2.  Are there infinitely many? The $\log\log X$ heuristic suggests yes, but no proof exists.
  3.  Is there a relation to Wieferich primes, irregular primes, or Bernoulli numbers? Numerically, $5,13,563$ appear in other super-congruence contexts — $13$ is also a Wall-Sun-Sun prime candidate region, and $563$ divides many Bernoulli numerators.

- **Why they matter:** Wilson primes are not used directly in cryptography, but they are the canonical example of a "supercongruence" — a congruence that holds mod $p^2$ when you only expect mod $p$. The search for such primes drives development of fast factorial modulo $p^2$ algorithms, $p$-adic gamma functions, and our understanding of Wolstenholme's theorem, which says for $p>3$, $\binom{2p-1}{p-1} \equiv 1 \mod p^3$. Wilson primes are essentially primes where Wilson's theorem can be lifted one $p$-adic level.

  They also connect to the Wilson quotient and to the concept of Lerch's formula and Bernoulli numbers:
  $$W(p) \equiv B_{p-1} - B_{2p-2} \mod p$$
  linking factorial residues to deep arithmetic invariants.

In short: Every prime satisfies $(p-1)! \equiv -1 \mod p$. Wilson primes are the rare primes where the universe is a little more symmetric than it has to be, satisfying the same congruence mod $p^2$. Only $5, 13, 563$ are known, and the fourth, if it exists, is beyond $2\times10^{13}$.

### Carmichael Numbers

Carmichael numbers are composite impostors — they pretend to be prime when tested with Fermat's Little Theorem. They are the worst possible case for naive primality testing, and the reason we cannot use the converse of Fermat's Little Theorem as a primality test.

#### Fermat's Little Theorem and Its Converse

Fermat's Little Theorem (1640) states:

> If $p$ is prime and $\gcd(a,p)=1$, then $a^{p-1} \equiv 1 \mod p$.

Many beginners hope the converse is true: If $a^{n-1} \equiv 1 \mod n$ for some $a$, then $n$ must be prime. It is false.

The converse fails: some composites also satisfy $a^{n-1} \equiv 1 \mod n$ for a given $a$. Those are called **Fermat pseudoprimes to base $a$**.

**Classic example:** $341 = 11 \times 31$ is composite, but
$$2^{340} \equiv 1 \mod 341$$
So $341$ looks prime if you only test base $2$. In fact, $341$ is the smallest base-2 Fermat pseudoprime. It was known to Sarrus in 1820.

We can have pseudoprimes to many bases: $91=7\times13$ is pseudoprime to base $3$, etc. But is there a composite that is pseudoprime to _every_ base coprime to it?

Carmichael numbers are the ultimate pseudoprimes — they are pseudoprime to _every_ base.

> **Definition:** A composite $n$ is a **Carmichael number** (or absolute pseudoprime) if
> $$a^{n-1} \equiv 1 \mod n$$
> for _every_ $a$ with $\gcd(a,n)=1$.
> Equivalently, $a^n \equiv a \mod n$ for _all_ integers $a$ — they satisfy Fermat's congruence universally, even when $\gcd(a,n)>1$.

So a Carmichael number fools the Fermat test no matter what base you pick. For a true prime $p$, there are $p-1$ bases that pass. For a Carmichael number $n$, there are $\varphi(n)$ bases that pass — all of them.

**First examples:**

$561 = 3\cdot11\cdot17$ is the smallest. Then
$1105 = 5\cdot13\cdot17$
$1729 = 7\cdot13\cdot19$ — yes, the Hardy-Ramanujan taxicab number $1729 = 1^3+12^3 = 9^3+10^3$ is also Carmichael,
$2465=5\cdot17\cdot29,\; 2821=7\cdot13\cdot31,\; 6601=7\cdot23\cdot41,\; 8911=7\cdot19\cdot67,\; 10585=5\cdot29\cdot73,\; 15841=7\cdot31\cdot73,\dots$

Check $561$:
$$2^{560} \equiv 1 \mod 561$$
$$5^{560} \equiv 1 \mod 561$$
$$7^{560} \equiv 1 \mod 561$$
... for any of the $\varphi(561)=320$ numbers $a$ with $\gcd(a,561)=1$, the congruence holds. For $a$ not coprime, e.g., $a=3$, we have $3^{561}\equiv 3 \mod 561$ still holds, but $3^{560}\equiv 375 \mod 561$, so we need the $a^n\equiv a$ form.

#### Korselt's Criterion (1899)

This is the deep structure theorem. Robert Daniel Carmichael found the first such number in 1910, but Arthur Korselt had already given a complete characterization in 1899 — 11 years earlier — without knowing any example existed. He proved a number is Carmichael iff it satisfies three simple arithmetic conditions.

**Korselt's Criterion:** $n$ is Carmichael iff:

1.  **Composite and square-free:** $n$ is composite, and no prime squared divides $n$. So $n = p_1 p_2 \cdots p_k$ with distinct primes $p_i$. If $p^2\mid n$, then the group $(\mathbb{Z}/p^2\mathbb{Z})^\times$ is not cyclic of order $p-1$, and you can find $a$ with $a^{p-1}\not\equiv1 \mod p^2$, breaking the condition.

2.  **At least three prime factors:** Every Carmichael number has at least three different prime factors. $k \ge 3$. This follows from (1) and (3): if $n=pq$ with two primes and $p-1\mid pq-1$ and $q-1\mid pq-1$, you get $p\mid q-1$ and $q\mid p-1$ impossible for $p\neq q$.

3.  **Divisibility condition:** For every prime $p \mid n$, $p-1 \mid n-1$.

_Why (3) is the key:_ If $a^{n-1}\equiv1 \mod n$, then $a^{n-1}\equiv1 \mod p$ for each $p\mid n$. Choose $a$ to be a primitive root mod $p$ — an element of order $p-1$. Then $p-1$ must divide $n-1$.

**Examples using the criterion:**

**Check $561$:** $561=3\cdot11\cdot17$, square-free, 3 primes.
$3-1=2 \mid 560$, $11-1=10 \mid 560$, $17-1=16 \mid 560$ because $560/16=35$ — so Carmichael.

**Why $341=11\cdot31$ is _not_ Carmichael:** $341$ is square-free, but $31-1=30 \nmid 340$. So it fails (3). Indeed, $341$ is pseudoprime to base $2$ but not to base $3$: $3^{340} \equiv 56 \not\equiv 1 \mod 341$. So testing base $3$ catches it.

**Check $1105$:** $1105=5\cdot13\cdot17$, $4\mid1104$, $12\mid1104$ ($1104/12=92$), $16\mid1104$ ($1104/16=69$) Carmichael.

**Check $1729$:** $1729=7\cdot13\cdot19$, $6\mid1728$, $12\mid1728$ ($1728/12=144$), $18\mid1728$ ($1728/18=96$) Carmichael.

This criterion makes it easy to construct Carmichael numbers: Find a set of primes where $L=\text{lcm}(p_i-1)$ divides $(\prod p_i)-1$. Chernick gave a famous parametric family in 1939: If $(6k+1)(12k+1)(18k+1)$ are all prime, then their product is Carmichael. For $k=1$, we get $7\cdot13\cdot19=1729$. For $k=6$, $37\cdot73\cdot109=294409$ is Carmichael.

#### Key Facts

- **Composite by definition:** No Carmichael number is prime. They are $p_1\cdots p_k$.
- **Square-free:** No $p^2\mid n$. $561=3\times11\times17$ has no repeat. If $p^2\mid n$, take $a=1+p$, then $a^{p}\not\equiv1 \mod p^2$.
- **Three or More Primes:** Minimal case is 3 primes. There is no Carmichael number with exactly 2 primes. Carmichael numbers with $k$ prime factors exist for every $k\ge3$.
- **Infinitude:** Conjectured for decades, proved by Alford, Granville, and Pomerance in 1994 in a landmark paper. They proved there are infinitely many Carmichael numbers, and at least $X^{2/7}$ up to $X$ for large $X$. The current best lower bound is $X^{0.333...}$ due to Harman. So infinite, but very sparse.
- **Rarity:**
  - **$\le 10^3$**: $1 (561)$
  - **$\le 10^6$**: $43$
  - **$\le 10^9$**: $646$
  - **$\le 10^{12}$**: $8241$
  - **$\le 10^{15}$**: $105,212$
  - **$\le 10^{18}$**: $1,401,644$
  - **$\le 10^{21}$**: $20,138,200$
    Compare to primes: $\pi(10^{21})\approx 2\times10^{19}$. So about 1 in $10^{12}$ numbers up to $10^{21}$ is Carmichael.
- **Carmichael function $\lambda(n)$:** Let $\lambda(n)$ be the exponent of $(\mathbb{Z}/n\mathbb{Z})^\times$ — the smallest $m$ such that $a^m\equiv1 \mod n$ for all $a$ coprime to $n$. For $n=\prod p_i$ square-free odd, $\lambda(n)=\text{lcm}(p_i-1)$. Then $n$ is Carmichael iff $\lambda(n)\mid n-1$. This is the group-theoretic restatement of Korselt.
- **Cryptographic Importance:** They break naive Fermat primality tests. If you test primality by picking random $a$ and checking $a^{n-1}\equiv1\mod n$, a Carmichael number fools you with probability 1 — every $a$ passes.

  This is why modern libraries use Miller-Rabin. Miller-Rabin writes $n-1 = d\cdot2^s$ with $d$ odd and checks if $a^d\equiv1$ or $a^{d2^r}\equiv-1$ for some $r<s$. This is stronger. Carmichael numbers _do_ fail Miller-Rabin. For example, $561=2^4\cdot35+1$, $2^{35}\equiv263 \mod 561$, not $1$ or $-1$, and squaring never hits $-1$, so Miller-Rabin with base $2$ declares $561$ composite. So Miller-Rabin is safe where Fermat is not.

- **Absolute Pseudoprimes:** Another name, because they are pseudoprime to all bases coprime to $n$.

**Distinction to remember:**

- **Fermat pseudoprime to base $a$:** Composite $n$ that passes Fermat test for _one specific_ $a$. Example: $341$ passes for $a=2$ only. $91=7\times13$ passes for $a=3$. There are infinitely many such to any base.
- **Carmichael / Absolute pseudoprime:** Composite $n$ that passes for _all_ $a$ coprime to $n$. $561$ passes for all 320 bases. Much rarer, much more dangerous.

In short: A Fermat pseudoprime is a liar to one interrogator. A Carmichael number lies to every interrogator you can bring — unless you change the question from Fermat to Miller-Rabin.
