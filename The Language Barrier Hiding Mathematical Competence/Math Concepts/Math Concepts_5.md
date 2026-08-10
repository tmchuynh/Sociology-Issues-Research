## Lie Algebras — Infinitesimal Symmetry

Lie algebras, introduced by Sophus Lie in the 1870s to study continuous transformation groups and solve differential equations, are the linearization of symmetry. A Lie group like rotations is a curved manifold — hard to work globally. Its tangent space at the identity is a flat vector space — easy linear algebra — but it remembers non-commutativity via a bracket. Lie algebras allow nonlinear problems in geometry and physics — rotations, Lorentz boosts, gauge fields — to be reduced to linear algebra.

Lie algebras, named after Sophus Lie (1842-1899) who studied continuous transformation groups to solve differential equations, are mathematical structures used to study continuous symmetries, often acting as linearized or infinitesimal version of Lie group. They allow complex nonlinear problems in geometry and physics — rotations, Lorentz boosts, gauge transformations — to be translated into simpler linear algebra. Lie theory is fundamental to modern particle physics where fundamental particles are seen as representations of Lie groups like $SU(3)$ color or $SU(2)$ weak isospin and to study of differential equations via symmetry reduction.

> **Slogan:** Lie group = global, curved, nonlinear symmetry. Lie algebra = infinitesimal, flat, linear approximation at identity that still remembers curvature.

Intuition: Lie group is curved manifold — e.g., circle $S^1$ of rotations — hard to work globally. Its tangent space at identity is flat vector space — line of angular velocities — easy linear algebra. Lie algebra is that flat approximation, but retains essential non-commutative structure via bracket.

### Definition and Core Axioms

#### What Is a Lie Algebra?

> A Lie algebra is a playground where we can add vectors and measure how much they fail to commute.

Formally: A **Lie algebra** $\mathfrak{g}$ is a vector space over a field $F$ — usually $\mathbb{R}$ or $\mathbb{C}$ — plus an extra operation called the **Lie bracket** $[\cdot,\cdot]: \mathfrak{g}\times\mathfrak{g}\to\mathfrak{g}$.

You already know vector spaces: you can add vectors $x+y$ and scale them $ax$. The bracket is new. It takes two vectors $x,y$ and produces a third vector $$. Think of it as a question: "If I wiggle a little bit in the $x$ direction and then in the $y$ direction, how much does the order matter?"[x][y]

If $=0$, they commute — order doesn't matter. If $[x,y]\neq 0$, they don't — and the result tells you in which direction you drift.[x][y]

**Why do we need three axioms?** We can't allow any random operation. We want the bracket to behave like it came from a real curved symmetry group. The three axioms are the minimal rules that guarantee that.

#### The Three Axioms

##### Bilinearity

$$[ax+by, z] = a[x,z] + b[y,z], \quad [z, ax+by] = a[z,x] + b[z,y]$$

> The bracket respects addition and scaling. It's linear like a derivative, not wild like a square.

**What this really means:**

If you double $x$, you double the non-commutativity: $ = 2$. If you do $x_1 + x_2$ vs $y$, the failure to commute splits: $[x_1+x_2, y] = [x_1,y] + [x_2,y]$.[y][x]

**Why we care — two huge consequences:**

1. Structure constants determine everything. Pick a basis $e_1,..., e_n$ of $\mathfrak{g}$. You only need to know what the bracket does on basis vectors:

$$[e_i, e_j] = \sum_k c_{ij}^k e_k$$

The numbers $c_{ij}^k$ are called **structure constants**. Then for ANY vectors $x=\sum x_i e_i$, $y=\sum y_j e_j$:

$$[x,y] = \sum_{i,j,k} x_i y_j c_{ij}^k e_k$$

Without bilinearity, you'd have to define $$ for infinitely many $x,y$. With it, you just need $n^2$ numbers. Classification becomes possible.[x][y]

Example: For $\mathfrak{so}(3)$ with basis $J_x,J_y,J_z$, we have $[J_x,J_y]=J_z$, $[J_y,J_z]=J_x$, $[J_z,J_x]=J_y$. So $c_{12}^3 = 1$, etc. That's the whole algebra.

2. The $ad$ map is linear. Define $ad_x: \mathfrak{g} \to \mathfrak{g}$ by $ad_x(y) = [x,y]$ — "bracket with $x$." Bilinearity says for fixed $x$, $ad_x$ is a linear transformation. So each element of the Lie algebra acts as a linear operator on the algebra itself. This is how the algebra studies itself.

##### Alternating Property — $[x,x]=0$[x]

$$[x,x]=0 \quad \forall x$$

> Everything commutes with itself. Wiggling twice in the same direction causes no extra drift.

This looks trivial, but it forces **anticommutativity**. Proof:

$$0 = [x+y, x+y] = + + + = 0 + + + 0$$[x][y]

So:

$$ = -$$[x][y]

Swapping order flips the sign.

**Why not just require $ = -$?** Over $\mathbb{R}$ and $\mathbb{C}$ they are almost the same. But if the field has characteristic 2 where $1 = -1$, anticommutativity would not imply $=0$. The alternating condition $=0$ is stronger and is the correct one. It also captures the geometry:[x][y]

> **Geometric picture:** $$ would be the gap when you go $t$ in $x$, then $t$ in $x$, then back. Of course you come back — you just went twice in the same line and reversed. So the gap is zero. An associative algebra like matrices has $x^2 \neq 0$ generally — going twice in same direction does something. A Lie algebra forgets that and only remembers the _antisymmetric_ part $xy-yx$.[x]

A Lie algebra where all $=0$ is called **abelian**. It's flat $\mathbb{R}^n$. Non-abelian means some $[x,y]\neq 0$ — that's where interesting geometry lives.[x][y]

##### Jacobi Identity — The Heart of It

$$[x,] + [y,] + [z,] = 0$$[y][z][x]

> This is the rule that replaces associativity. The bracket itself is not associative — $[x,]$ is not $[,z]$ in general. Jacobi says the three possible double-brackets balance out to zero.[y][z][x]

This is the hardest axiom to feel intuitively, so here are three ways to think about it:

**View 1: $ad_x$ is a derivation.**

Rewrite Jacobi as:

$$[x,] = [,z] + [y,]$$[y][z][x]

Remember $ad_x(y) = [x,y]$. Then this is:

$$ad_x([y,z]) = [ad_x(y), z] + [y, ad_x(z)]$$

That's exactly the Leibniz product rule from calculus: $D(fg) = D(f)g + f D(g)$, but with $$ as the product. So:[y][z]

> $ad_x$ — bracketing with $x$ — acts like a derivative on the bracket operation.

**View 2: It comes from associativity of the group.**

Take the group law $(e^{tX}e^{tY})e^{tZ} = e^{tX}(e^{tY}e^{tZ})$. Expand both sides using BCH to order $t^3$. The terms with single brackets cancel, and what remains is precisely Jacobi. If Jacobi failed, you couldn't exponentiate to an associative group — you'd get a non-associative "loop" instead. So Jacobi is the shadow that group associativity leaves on the flat tangent plane.

**View 3: Consistency check.**

If you think of $$ as an infinitesimal transformation of $y$ by $x$, Jacobi says those transformations are consistent: doing $x$ then $y$ vs $y$ then $x$ differs by exactly $$ acting.[x][y]

#### What Happens If Jacobi Fails? — A Counterexample

Define a 3D vector space with basis $e_1,e_2,e_3$ and define, with antisymmetry:

$$[e_1,e_2]=e_1,\quad [e_2,e_3]=e_1,\quad [e_3,e_1]=e_2$$

Check Jacobi for $(e_1,e_2,e_3)$:

$$[e_1,[e_2,e_3]] + [e_2,[e_3,e_1]] + [e_3,[e_1,e_2]] = [e_1,e_1] + [e_2,e_2] + [e_3,e_1]$$

$$= 0 + 0 + e_2 = e_2 \neq 0$$

So this is **not** a Lie algebra. Bilinearity and alternation hold, but Jacobi fails. You cannot find a Lie group whose tangent space behaves like this. The BCH formula would give you a non-associative multiplication.

#### The Big Picture in Numbers

If $\dim \mathfrak{g}=n$, how much data defines it?

- Antisymmetry: $c_{ij}^k = -c_{ji}^k$ and $c_{ii}^k=0$, so we only need $i<j$. That's $n(n-1)/2$ pairs times $n$ choices for $k$ = $n^2(n-1)/2$ numbers.
- Jacobi imposes quadratic constraints:

$$\sum_m \left(c_{ij}^m c_{mk}^l + c_{jk}^m c_{mi}^l + c_{ki}^m c_{mj}^l\right)=0 \quad \forall i,j,k,l$$

These are not linear — they are quadratic equations in the $c$'s. Classifying Lie algebras is solving these equations up to change of basis. That's why classification is hard but doable in low dimensions.

> **Final simple summary:**
>
> 1. **Vector space** = we can add and scale.
> 2. **Bilinearity** = bracket respects that linear structure.
> 3. **$=0$** = bracket measures _antisymmetric_ failure to commute.
> 4. **Jacobi** = that failure is consistent enough to come from a real curved group.[x]

With just these three, you have enough to build all of Lie theory.

### The Lie Group — Lie Algebra Connection

This is the central idea. Let's unpack it slowly.

**What is a Lie group?** It's something that is two things at once:

1. A **group** — you can multiply two elements and get another, there is an identity, and inverses exist.
2. A **smooth manifold** — it's also a smooth, curved shape where you can do calculus. Multiplication and taking inverses are smooth operations.

If that sounds abstract, don't worry. All the important examples are matrices.

> A Lie group is a _continuous family of symmetries_. $SO(3)$ is not just 3 rotations — it's ALL possible rotations of 3D space, and you can smoothly wiggle from one rotation to another. A Lie group is that whole wiggle-able space.

**Examples:**

- $GL_n(\mathbb{R})$: all invertible $n \times n$ matrices. This is almost all of $\mathbb{R}^{n^2}$, just with the non-invertible ones removed. Dimension = $n^2$.
- $SO(3)$: all 3D rotations. You can describe any rotation by 3 numbers — e.g. yaw, pitch, roll. So its dimension is 3. Even though the matrices are $3 \times 3$, you only need 3 parameters.

Working directly with the group is hard because multiplication is curved and nonlinear. So we do a classic calculus trick: zoom in very close to the identity element $e$ and look at the flat approximation.

That flat approximation is the Lie algebra.

> **Analogy:** Think of Earth. Earth is a curved sphere — that's the Lie group. It's hard to do geometry on a sphere. But if you stand in a field in Orange and look around, the ground looks flat. That flat field is the tangent plane at your location. The Lie algebra is the flat field at the identity point of the group.

Formally, the Lie algebra is $\mathfrak{g} = T_e G$ — the tangent space at identity. A vector in it is a "velocity vector": take a smooth path $\gamma(t)$ inside the group with $\gamma(0) = e$, and take its velocity at time 0, $\gamma'(0)$. That velocity lives in $\mathfrak{g}$.

The extra magic is the **Lie bracket**. The flat plane forgets how curved the group is. The bracket $$ is a little memory chip that says "if you go a tiny bit in X direction, then Y, then back, you don't quite return — here's how much curvature you felt."[X][Y]

#### Tangent Space at Identity — In More Detail

For a matrix group, this is very concrete.

Take $G = SO(n) = \{ R \mid R^T R = I, \det R = 1 \}$. This is a curved surface inside all matrices.

Take a curve through identity: $R(t)$ with $R(0)=I$. Since $R(t)^T R(t)=I$ always, differentiate at $t=0$:

$$ \frac{d}{dt} [R(t)^T R(t)]\_{t=0} = 0 \implies R'(0)^T I + I^T R'(0) = 0 $$

If we call $X = R'(0)$, we get $X^T + X = 0$. So $X$ is skew-symmetric!

That means:
$$\mathfrak{so}(n) = \{ X \mid X^T = -X \}$$

We turned a nonlinear condition ($R^T R = I$) into a linear condition ($X^T = -X$). Linear is much easier. That's the whole point.

Other examples:

- $\mathfrak{gl}_n$ = all $n \times n$ matrices
- $\mathfrak{sl}_n$ = trace zero matrices (from $\det = 1$)
- $\mathfrak{u}(n)$ = skew-Hermitian matrices: $X^\dagger = -X$

Dimension of $\mathfrak{g}$ = dimension of $G$.

#### The Lie Bracket — What Does "Failure to Commute" Mean?

For matrix groups, the bracket has a simple formula:

$$ = AB - BA$$[A][B]

> It asks: does order matter? If you do A then B, vs B then A, do you get the same result? If $AB = BA$, they commute and $=0$. If not, the bracket measures _how much_ they don't commute.[A][B]

**Why does this matter?** Rotations in 3D don't commute. Hold a book: rotate 90° around x then 90° around y — you get a different orientation than y then x. That non-commuting is encoded in the bracket.

Let's calculate a simple example:

$$A = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \quad B = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}$$

1. $AB = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$
2. $BA = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}$
3. $[A, B] = AB - BA = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$

It's not zero, so A and B don't commute.

This commutator operation automatically gives you a Lie algebra because it satisfies three rules:

1. **Bilinearity:** $[A, B+C] = + $. Bracket is linear in each slot. Like multiplication.[A][B][C]
2. **Skew-symmetry:** $ = -$. Swapping order flips the sign. In particular $=0$.[A][B]
3. **Jacobi Identity:** $[A,] + [B,] + [C,] = 0$. This is less intuitive at first, but it's the rule that says "the bracket is consistent with itself." If you expand it with matrices, all 12 terms cancel. For abstract Lie algebras, we _require_ this to hold — it's like an associativity condition for brackets.[B][C][A]

> Jacobi says if you have three infinitesimal motions, the way they interfere with each other has to balance out. It's the price we pay for working on a flat plane that remembers curvature.

#### Infinitesimal Motions and Generators

A generator is just a basis vector of the Lie algebra. Any tiny motion near identity is a combination of generators.

**Example — $SO(2)$ (rotations of a circle):**

$$R_\theta = \begin{pmatrix}\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta\end{pmatrix}$$

For tiny $\theta$, using Taylor expansion $\cos\theta \approx 1, \sin\theta \approx \theta$:

$$R_\theta \approx I + \theta \begin{pmatrix}0 & -1 \\ 1 & 0\end{pmatrix} = I + \theta J$$

$J$ is the _generator_. It is the direction of "rotate a little bit." The Lie algebra $\mathfrak{so}_2$ is just all multiples $\theta J$, so it's 1-dimensional.

**Example — $SO(3)$ (rotations of 3D space):**

We have 3 basic infinitesimal rotations:

$$J_x=\begin{pmatrix}0&0&0\\0&0&-1\\0&1&0\end{pmatrix},\; J_y=\begin{pmatrix}0&0&1\\0&0&0\\-1&0&0\end{pmatrix},\; J_z=\begin{pmatrix}0&-1&0\\1&0&0\\0&0&0\end{pmatrix}$$

Any angular velocity vector $\omega = (\omega_x, \omega_y, \omega_z)$ — the thing physicists use — is really just $X = \omega_x J_x + \omega_y J_y + \omega_z J_z$.

> $J_x$ is "infinitesimally nudge around the x-axis." If you combine them, you get any infinitesimal rotation. Generators are like the x, y, z axes, but for rotations.

Their brackets encode the geometry of 3D space: $[J_x, J_y] = J_z$ (and cyclic permutations). That says: doing an x-rotation then a y-rotation is slightly different from y then x, and the difference is a z-rotation.

#### The Exponential Map — From Flat to Curved

How do we go back from the easy flat algebra to the hard curved group? We exponentiate.

$$e^X = I + X + \frac{X^2}{2!} + \frac{X^3}{3!} + \cdots$$

> If the Lie algebra tells you "keep walking in direction X", the exponential tells you where you end up on the curved group after walking for 1 second. $X$ is the velocity, $e^X$ is the final position.

For $SO(2)$: $\exp(\theta J) = R_\theta$ exactly. The infinite series magically rebuilds $\cos\theta$ and $\sin\theta$.

For $SO(3)$: If $X = \theta \hat{u}\cdot\vec{J}$ where $\hat{u}$ is a unit axis and $\theta$ is an angle, then

$$e^X = I + \sin\theta\,\hat{U} + (1-\cos\theta)\hat{U}^2$$

This is Rodrigues' formula. It says: $e^X$ is "rotate by $\theta$ around axis $\hat{u}$". So exponentiation turns angular velocity into an actual rotation.

**Important caveats:**

- Near identity, $\exp$ is a perfect dictionary — you can go back and forth with $\log$.
- Globally, it may not cover everything. For example, some matrices in $SL_2(\mathbb{R})$ are not $e^X$ for any single $X$, but you can get them as products $e^{X_1}e^{X_2}...$.

**The key link between bracket and group commutator:**

$$e^{tX}e^{tY}e^{-tX}e^{-tY}=I+t^2[X,Y]+O(t^3)$$

> Go a tiny $t$ in X, tiny $t$ in Y, then back in X, back in Y. In a flat abelian world like $\mathbb{R}^n$, you'd be back where you started. On a curved non-abelian group, you miss by a tiny amount. That miss, to second order, is exactly $t^2[X,Y]$. The bracket IS the gap.

So $e^{tX}e^{tY}=e^{tY}e^{tX}$ for all small $t$ if and only if $=0$.[X][Y]

#### Baker-Campbell-Hausdorff (BCH) Formula

If we know how to multiply $e^X e^Y$, do we get $e^{\text{something}}$? Yes, and that "something" only uses brackets.

$$e^X e^Y = \exp\left( X+Y+\frac12[X,Y]+\frac1{12}[X,[X,Y]]-\frac1{12}[Y,[X,Y]]+\cdots\right)$$

> It says "the product of two curved moves, written in flat coordinates, is the sum plus half the non-commutativity, plus corrections that are brackets of brackets."

If $=0$ for all $X,Y$, all correction terms die and $e^X e^Y = e^{X+Y}$. That's what happens for $G=\mathbb{R}^n$ — its Lie algebra is abelian, life is simple.[X][Y]

This is why the Lie algebra determines the local group law. If you know all brackets, you know how to multiply nearby group elements.

#### Lie's Three Theorems — Why We Bother

1. **Existence:** Every abstract Lie algebra (a vector space with a bilinear, skew-symmetric bracket satisfying Jacobi) comes from _some_ Lie group (at least locally). You can invent a bracket table and it will be geometrically realizable.
2. **Uniqueness:** If two simply connected Lie groups have the same Lie algebra, they are the same group. More generally, maps between simply connected groups are the same as maps between their Lie algebras. So to understand group homomorphisms, it suffices to study linear maps preserving brackets.
3. **Subgroups:** Closed subgroups of a Lie group correspond to subalgebras of its Lie algebra. Example: $SO(n) \subset GL_n$ corresponds to skew-symmetric $\subset$ all matrices.

> Lie groups are complicated curved objects of symmetry. Lie algebras are flat vector spaces that are their linear shadow at the identity. The bracket remembers how the shadow was curved. By studying linear algebra + bracket, we understand almost everything about the local behavior of the continuous symmetries. It's a linearization trick that turns nonlinear geometry into linear algebra.

### Key Classifications — Periodic Table of Symmetry

> **The Big Idea:** Just like numbers break into primes, or molecules into atoms, Lie algebras break into simpler pieces. Classification tells us what the "atoms of continuous symmetry" are, and how to build everything else from them.

To talk about breaking, we need the concept of an **ideal**.

#### What is an Ideal?

Take a subspace $I \subseteq \mathfrak{g}$. We say $I$ is an **ideal** if:

$$[\mathfrak{g}, I] \subseteq I$$

Meaning: bracket *anything* in $\mathfrak{g}$ with *anything* in $I$, you stay inside $I$.

> An ideal is a piece you can't escape. If you stir the whole algebra with it, it absorbs the stirring. This is exactly like a normal subgroup in group theory — if $N$ is normal in $G$, then $gNg^{-1} \subseteq N$.

Why do we care? If $I$ is an ideal, you can form the **quotient** $\mathfrak{g}/I$ — you collapse $I$ to zero and still have a valid Lie algebra. So ideals are how we decompose. If an algebra has no non-trivial ideals, it's indivisible — an atom.

Think of it like this: a subalgebra $S$ is "closed under bracketing with itself": $[S,S]\subseteq S$. An ideal is much stronger: it's "closed under bracketing with the *whole* algebra."

#### Abelian Type — The Boring but Important One

All brackets zero: $=0$ for all $x,y$. All structure constants $c_{ij}^k = 0$.[x][y]

> Nothing fails to commute. Order never matters. This is flat, Euclidean space.

**Examples:** $\mathbb{R}^n$ with zero bracket. This is the Lie algebra of:
* $\mathbb{R}^n$ itself under addition — translations.
* $T^n = (S^1)^n$, the $n$-torus — $n$ independent circles, like $n$ independent phases.

The group is commutative. Its representation theory is trivial: every irreducible representation is 1-dimensional — just a phase $e^{i \lambda \cdot x}$. No interesting mixing.

This is the simplest building block, but alone it can't make rotations, because rotations don't commute.

#### Simple — The Atoms

**Definition:** Non-abelian, and has no non-trivial ideals — only $0$ and $\mathfrak{g}$ itself. You cannot break it into smaller pieces.

> A simple Lie algebra is a prime number. You can't factor it. If you try to take a quotient, you get either zero or the whole thing.

**Standard examples — the matrix families:**

* $\mathfrak{sl}_n$ for $n\ge2$: traceless $n\times n$ matrices. Dimension $n^2-1$. Lie algebra of $SL_n$ and $SU(n)$. This is $A_{n-1}$ in the classification.
* $\mathfrak{so}_n$ for $n\neq2,4$: skew-symmetric matrices, $X^T=-X$. Dimension $n(n-1)/2$. Lie algebra of rotations. $SO(3)$ and $SO(4)$ are special — $SO(4)$ actually splits, which is why we exclude it.
* $\mathfrak{sp}_{2n}$: matrices preserving a skew-symmetric form, $X^T J + JX=0$. Dimension $n(2n+1)$. Lie algebra of Hamiltonian mechanics — preserves symplectic structure.

How do we know something is simple without checking all subspaces? Use the **Killing form**:

$$B(X,Y) = \text{tr}(ad_X \circ ad_Y)$$

where $ad_X(Y)=[X,Y]$. So $B$ measures how much $X$ and $Y$ interact via double bracketing and takes the trace.

> $B$ is a dot product made from the bracket itself. If you have a Lie algebra, you can make your own geometry out of it.

**Cartan's criterion:** $\mathfrak{g}$ is semisimple iff $B$ is non-degenerate — no non-zero $X$ with $B(X,\cdot)=0$. For compact simple algebras, $B$ is negative-definite, so $-B$ is a real Euclidean inner product. That negativity is why compact groups have nice, finite-volume geometry.

Simple algebras are the atoms. Everything semisimple is made of them.

#### Semisimple — Molecules Made of Atoms

**Definition:** $\mathfrak{g} = \mathfrak{s}_1 \oplus \cdots \oplus \mathfrak{s}_k$ where each $\mathfrak{s}_i$ is simple, direct sum meaning they commute with each other: $[\mathfrak{s}_i, \mathfrak{s}_j]=0$ for $i\neq j$.

Equivalently: $\mathfrak{g}$ has no non-zero **solvable** ideal.

What's solvable? Define the **derived series**: $\mathfrak{g}^{(0)}=\mathfrak{g}$, $\mathfrak{g}^{(1)}=[\mathfrak{g},\mathfrak{g}]$, $\mathfrak{g}^{(2)}=[\mathfrak{g}^{(1)},\mathfrak{g}^{(1)}]$,... If this eventually hits $0$, the algebra is solvable.

> Solvable = you can keep taking commutators and eventually everything becomes zero. Example: upper triangular matrices. If you take commutator of two upper triangular, you get strictly upper triangular (zeros on diagonal). Commutator again, more zeros, etc., eventually zero. Solvable is "almost abelian" — not zero immediately, but nilpotent in steps.

Semisimple means "no almost-abelian junk inside." It's pure non-commutativity built from simple atoms.

This is where the great classification lives — work of Killing 1888-1890 and Cartan 1894.

**How did they classify? In 3 steps:**

**Step 1 — Find a maximal abelian piece.**
Choose a **Cartan subalgebra** $\mathfrak{h}$: a maximal set of commuting diagonalizable elements. Think "all diagonal matrices" inside $\mathfrak{sl}_n$.

> **Simple picture:** In $\mathfrak{sl}_3$, $\mathfrak{h}$ is $\text{diag}(a_1,a_2,a_3)$ with $a_1+a_2+a_3=0$. These all commute with each other, like the $z$-axis in our symmetry space.

**Step 2 — Decompose by roots.**
We look at how $\mathfrak{h}$ acts on the rest via $ad_H$. Since the $H$'s commute, we can simultaneously diagonalize them. So:

$$\mathfrak{g} = \mathfrak{h} \oplus \bigoplus_{\alpha \in \Phi} \mathfrak{g}_\alpha$$

Each $\mathfrak{g}_\alpha$ is a 1-dimensional space (for simple $\mathfrak{g}$) where:

$$[H, X_\alpha] = \alpha(H) X_\alpha \quad \forall H\in\mathfrak{h}$$

$\alpha$ is a linear functional on $\mathfrak{h}$, i.e., $\alpha \in \mathfrak{h}^*$. It's called a **root**. $\Phi$ is the set of all roots — a finite constellation of vectors in Euclidean space.

> Roots are the "charges" or "weights" of how the rest of the algebra rotates when you act with the diagonal Cartan part. For $\mathfrak{sl}_3$, there are 6 roots living in a plane, forming a hexagon. They can only meet at very special angles: 90°, 120°, 135°, 150° — that's the "crystallographic" restriction. This rigidity is what makes classification possible.

**Step 3 — Encode in a Dynkin diagram.**
Pick simple roots — a basis of $\Phi$ where every root is positive or negative combination. Then draw a graph:
* Node = simple root
* Number of edges between nodes = angle: 0 edges = 90° (orthogonal), 1 edge = 120°, 2 edges = 135°, 3 edges = 150°.
* Arrow tells which root is longer.

The whole algebra is determined by this little graph.

**The final list — the periodic table:**

Four infinite families:

* **$A_n = \mathfrak{sl}_{n+1}$**, $n\ge1$, dim $n(n+2)$: Special linear/unitary. Symmetries of complex $n+1$-dimensional volume. $A_1=\mathfrak{sl}_2$ is angular momentum in quantum mechanics. $A_2$ is flavor symmetry of quarks.
* **$B_n = \mathfrak{so}_{2n+1}$**, $n\ge2$, dim $n(2n+1)$: Odd orthogonal. Rotations in odd dimensions $2n+1$.
* **$C_n = \mathfrak{sp}_{2n}$**, $n\ge3$, dim $n(2n+1)$: Symplectic. Symmetries preserving Hamiltonian phase space. Same dimension as $B_n$ but different structure.
* **$D_n = \mathfrak{so}_{2n}$**, $n\ge4$, dim $n(2n-1)$: Even orthogonal. Rotations in even dimensions.

And five exceptional jewels that don't fit families:

* **$G_2$**, dim 14: The smallest exceptional. Automorphisms of octonions. You can picture it as symmetries of a very special 7D cross product.
* **$F_4$**, dim 52, **$E_6$** dim 78, **$E_7$** dim 133, **$E_8$** dim 248.

> **Why should you care about $E_8$?** $E_8$ is the largest, most intricate atom of symmetry. Its root system has 240 roots in 8D, incredibly symmetric. It appears in heterotic string theory as $E_8 \times E_8$, and $E_6$ is a candidate for Grand Unified Theory — all particles in one representation of $E_6$.

This classification is considered one of the greatest achievements of mathematics. We know *all* possible continuous simple symmetries.

#### Reductive — What Physicists Actually Use

**Definition:** $\mathfrak{g} = \mathfrak{z} \oplus \mathfrak{s}$ where $\mathfrak{z}$ is abelian (the center — elements commuting with everything) and $\mathfrak{s}$ is semisimple.

> Reductive = abelian center + semisimple part, which don't talk to each other. It's semisimple plus some extra $U(1)$'s.

**Examples:**

* $\mathfrak{gl}_n = \mathbb{R} I \oplus \mathfrak{sl}_n$. The $I$ is multiples of identity — they commute with everything and have trace. $\mathfrak{sl}_n$ is traceless. Any matrix = (trace part) + (traceless part).
* $\mathfrak{u}_n = \mathfrak{u}_1 \oplus \mathfrak{su}_n$. $U(n)$ rotations have a phase $U(1)$ and a special unitary part $SU(n)$.

Most groups in physics — Standard Model gauge group $U(1)\times SU(2)\times SU(3)$, $U(n)$, $GL_n$ — are reductive, not strictly semisimple, because they have that central $U(1)$ phase.

**Summary Table**

| Type | Bracket | Ideals? | Analogy | Example |
| :--- | :--- | :--- |
| **Abelian** | All zero | Everything is ideal | Vacuum, no interaction | $\mathbb{R}^n$ |
| **Simple** | Non-zero | Only $0$ and itself | Prime number / Atom | $\mathfrak{sl}_2$, $\mathfrak{so}_3$ |
| **Semisimple** | Non-zero | Direct sum of simples | Molecule of atoms | $\mathfrak{so}_4 \cong \mathfrak{so}_3\oplus\mathfrak{so}_3$ |
| **Reductive** | Center + semisimple | Center + simples | Molecule + inert gas | $\mathfrak{gl}_n$, $\mathfrak{u}_n$ |

If abelian is silence, simple is a single pure tone, semisimple is a chord of pure tones, and reductive is a chord plus a drone.
### Why Physics Cares — Representation = Particle

#### Wigner Principle

Particles are irreducible representations (irreps) of Lie algebra. Generators $T_a$ obey $[T_a,T_b]=if_{ab}^c T_c$ — physics convention with $i$ making $T_a$ Hermitian. Structure constants $f_{ab}^c$ determine interactions.

- **$\mathfrak{su}_3$ color:** Irreps dimensions 1,3,$\bar3$,6,8,10,... Quarks in 3 fundamental, anti-quarks $\bar3$, gluons in 8 adjoint, baryons decuplet 10. Lagrangian contains $f_{abc}A^b A^c$ gluon self-coupling from non-abelian bracket. Abelian $\mathfrak{u}_1$ electromagnetism $f=0$, photons don't self-interact.
- **$\mathfrak{so}_3$ orbital angular momentum:** Irreps labeled $l=0,1,2,\dots$, dimension $2l+1$, spherical harmonics $Y_{lm}$.
- **$\mathfrak{su}_2$ spin:** Irreps $j=0,1/2,1,3/2,\dots$, dimension $2j+1$. Spin-1/2 from $\mathfrak{su}_2$ not $\mathfrak{so}_3$ — double cover. Pauli principle from antisymmetric representation.

#### Ladder Operators — Solving Without Differential Equations

Bracket table $[J_i,J_j]=i\epsilon_{ijk}J_k$ for angular momentum predicts $J^2=j(j+1)$ and $J_z=m$ with $-j\le m\le j$ using only $[J_z,J_\pm]=\pm J_\pm$, $[J_+,J_-]=2J_z$ — no Schrödinger equation needed. This method generalizes to all simple algebras via Cartan-Weyl basis: $E_\alpha$, $F_\alpha$, $H_\alpha$ with $[H,E_\alpha]=\alpha(H)E_\alpha$.

Thus studying bracket table directly predicts allowed quantum states.

#### In Differential Equations

Sophus Lie's original motivation: If ODE/PDE invariant under Lie group action, use Lie algebra to reduce order. Symmetry $X$ gives first integral. This is Lie symmetry reduction — still used to find exact solutions of nonlinear PDEs.

In one sentence: Lie algebra is the flat ruler that measures curved symmetry, and its bracket table is the multiplication table of infinitesimal motions — the DNA from which all continuous symmetry, from spinning tops to quarks, is built.

### Examples of Lie Algebras — From Matrices to Fields

#### Matrix Commutator — Universal Source

Any associative algebra of $n\times n$ matrices becomes Lie algebra if you define bracket $=AB-BA$ — commutator — measures failure of $A$ and $B$ to commute. Jacobi holds because associativity of matrix product: expand $[x,] = x(yz-zy)-(yz-zy)x = xyz -xzy -yzx+zyx$, cyclic sum cancels — $xyz$ terms cancel pairwise. This is source of most finite-dimensional examples — $\mathfrak{gl}_n$, $\mathfrak{sl}_n$, $\mathfrak{so}_n$, $\mathfrak{su}_n$ are all subspaces of $\mathfrak{gl}_n$ closed under commutator. Ado's theorem: every finite-dimensional Lie algebra isomorphic to subalgebra of $\mathfrak{gl}_n$ for some $n$ — so studying matrix commutator captures all.[A][B][y][z]

Why commutator appears physically: infinitesimal rotations $I+\epsilon A$ and $I+\epsilon B$ composed in two orders differ by $\epsilon^2[A,B]$ — $$ measures non-commutativity to second order.[A][B]

#### General Linear $\mathfrak{gl}_n$

All $n\times n$ matrices over field $F$ — $\mathbb{R}$ or $\mathbb{C}$ — dimension $n^2$, bracket commutator. Lie algebra of $GL_n(F)$ — group of all invertible matrices — tangent at $I$ is all matrices because $GL_n$ open subset of $M_n$ — near $I$, any small matrix $I+\epsilon X$ invertible for small $\epsilon$, so no condition on $X$. So $\mathfrak{gl}_n$ is largest, contains all others as subalgebras.

Basis: $E_{ij}$ matrix with 1 at $(i,j)$ else 0 — $n^2$ basis. Bracket $[E_{ij},E_{kl}]=\delta_{jk}E_{il}-\delta_{li}E_{kj}$ — standard commutation relations.

Not simple — center $\mathfrak{z}= \text{span}\{I\}$ — scalar matrices commute with all — $=0$, ideal, so $\mathfrak{gl}_n = \mathfrak{sl}_n\oplus \mathbb{R}I$ as vector space, not simple but reductive.[I][X]

Example $n=1$: $\mathfrak{gl}_1\cong F$, abelian, $=0$, Lie algebra of non-zero scalars under multiplication.[a][b]

#### Special Linear $\mathfrak{sl}_n$ — Volume Preserving

Matrices with trace zero $\text{tr}X=0$, dimension $n^2-1$ — one linear condition, bracket closed because $\text{tr}[A,B]=\text{tr}(AB-BA)=0$ always, so $$ traceless if $A,B$ traceless. Corresponding Lie group $SL_n(F)=\{M\mid\det M=1\}$ — special linear group — determinant 1 — volume-preserving linear transformations — preserves volume of parallelepiped because $\det$ = volume scale factor. Relation $\det e^X = e^{\text{tr}X}$ — Lie theory identity from $\det$ = product eigenvalues, $\text{tr}$ = sum log eigenvalues — so $\text{tr}X=0 \iff \det e^X=1$. Thus $\mathfrak{sl}_n$ is infinitesimal volume-preserving.[A][B]

Example $\mathfrak{sl}_2$ — smallest simple Lie algebra, prototype for all — dimension $2^2-1=3$, basis:
$$e=\begin{pmatrix}0&1\\0&0\end{pmatrix},\quad f=\begin{pmatrix}0&0\\1&0\end{pmatrix},\quad h=\begin{pmatrix}1&0\\0&-1\end{pmatrix}$$
with commutation relations:
$$[h,e]=2e,\quad [h,f]=-2f,\quad [e,f]=h$$
This is $A_1$ root system: $h$ Cartan subalgebra — diagonal — acts on $e,f$ by eigenvalues $\pm2$ — roots. Any semisimple Lie algebra built from copies of $\mathfrak{sl}_2$ — Chevalley generators. Representation theory of $\mathfrak{sl}_2$ completely known: irreps $V_j$ dimension $2j+1$, $j=0,1/2,1,...$ — spin — classified by highest weight, basis $|j,m\rangle$ with $h|j,m\rangle=2m|j,m\rangle$.

$\mathfrak{sl}_n$ simple for $n\ge2$ over characteristic 0 — no non-trivial ideals — except $\mathfrak{sl}_2$ mod 2 etc.

#### Special Orthogonal $\mathfrak{so}_n$ — Infinitesimal Rotations

Skew-symmetric matrices $M^T=-M$ — i.e., $M_{ij}=-M_{ji}$, diagonal zero — dimension $n(n-1)/2$ — choose entries above diagonal — representing infinitesimal rotations — because rotation group $SO(n)=\{R\mid R^TR=I,\det R=1\}$, differentiate condition at $I$: $(I+\epsilon X)^T(I+\epsilon X)=I+\epsilon(X^T+X)+O(\epsilon^2)=I$ requires $X^T+X=0$. So tangent = skew-symmetric.

For $n=2$: $\mathfrak{so}_2$ dimension 1 — single generator $J=\begin{pmatrix}0&-1\\1&0\end{pmatrix}$ — abelian, $=0$ — rotations in plane commute.[J]

For $n=3$: $\mathfrak{so}_3$ dimension 3 — consists of
$$X(x,y,z)=\begin{pmatrix}0&-z&y\\z&0&-x\\-y&x&0\end{pmatrix}$$
identified with vector $\mathbf{x}=(x,y,z)$ via $X\mathbf{v}=\mathbf{x}\times\mathbf{v}$ — cross product matrix. Bracket corresponds to cross product:
$$[X(\mathbf{x}),X(\mathbf{y})]=X(\mathbf{x}\times\mathbf{y})$$
So Lie algebra of 3D rotations is cross product algebra — Jacobi identity for $\mathfrak{so}_3$ is vector triple product identity $\mathbf{x}\times(\mathbf{y}\times\mathbf{z})+\text{cyc}=0$. Non-abelian — rotations about different axes don't commute — $[X,Y]\neq0$.

Isomorphic to $\mathfrak{su}_2$ via $2:1$ covering — $SU(2)$ double covers $SO(3)$ — Pauli matrices: $\mathfrak{su}_2$ basis $\dfrac12 i\sigma$, same brackets. Explains spin-1/2.

$\mathfrak{so}_n$ simple for $n\neq2,4$ — $\mathfrak{so}_4\cong\mathfrak{so}_3\oplus\mathfrak{so}_3$ semisimple not simple.

#### Special Unitary $\mathfrak{su}_n$ — Quantum Infinitesimals

Anti-Hermitian traceless matrices $X^\dagger=-X$, $\text{tr}X=0$ — dimension $n^2-1$ over $\mathbb{R}$ — infinitesimal quantum unitaries preserving probability — group $SU(n)=\{U\mid U^\dagger U=I,\det U=1\}$ — unitary matrices — preserve Hermitian inner product — quantum evolution. Differentiate $U^\dagger U=I$: $X^\dagger+X=0$. Traceless from determinant condition.

- $\mathfrak{su}_2$ dimension 3 — basis $i\sigma_x,i\sigma_y,i\sigma_z$ where Pauli matrices $\sigma_x=\begin{pmatrix}0&1\\1&0\end{pmatrix},\sigma_y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\sigma_z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}$ — physics uses Hermitian $\sigma$ for observables, mathematicians anti-Hermitian $i\sigma$ for Lie algebra. Brackets $[i\sigma_j,i\sigma_k]=-2\epsilon_{jkl}i\sigma_l$. Irreps dimension $2j+1$ — spin — fundamental representation 2-d — qubit.

- $\mathfrak{su}_3$ dimension 8 — basis Gell-Mann matrices $\lambda_a$, $a=1\dots8$ — traceless Hermitian $3\times3$ — $\mathfrak{su}_3$ basis $i\lambda_a$. Used for color $SU(3)_c$ — quarks transform as 3, antiquarks $\bar{3}$, gluons as 8 — adjoint representation — dimension = dim algebra itself. Structure constants $f_{abc}$ defined by $[\lambda_a,\lambda_b]=2if_{abc}\lambda_c$.

$\mathfrak{su}_n$ compact real form of $\mathfrak{sl}_n(\mathbb{C})$ — $\mathfrak{sl}_n(\mathbb{C})$ as complex algebra dimension $n^2-1$ complex, its compact real form $\mathfrak{su}_n$.

#### Vector Fields — Infinite-Dimensional Example

Space of smooth vector fields $\mathfrak{X}(M)$ on manifold $M$ forms infinite-dimensional Lie algebra under Lie derivative bracket $=XY-YX$ as differential operators — acting on functions: $(XY)(f)=X(Y(f))$, $X$ derivation. In coordinates $X=\sum X^i\partial_i$, $Y=\sum Y^j\partial_j$, then $[X,Y]=\sum (X^i\partial_i Y^j - Y^i\partial_i X^j)\partial_j$ — commutator of flows — measures failure of flows to commute: flow along $X$ time $t$, then $Y$ time $s$, vs opposite order difference $\approx st[X,Y]$.[X][Y]

Fundamental to general relativity — diffeomorphism invariance — and fluid dynamics — Euler equation $\partial_t\omega + [u,\omega]=0$ — and control theory — Lie bracket generates new directions from two allowed motions, e.g., parallel parking.

Subalgebras: Hamiltonian vector fields preserve symplectic form — infinite-dimensional simple? — volume-preserving divergence-free fields — Lie algebra of $\text{SDiff}(M)$ — etc. Not all finite-dimensional classifications extend, but Jacobi still holds.

These examples show progression: from all matrices $\mathfrak{gl}_n$ to volume-preserving $\mathfrak{sl}_n$, to rotations $\mathfrak{so}_n$, to quantum $\mathfrak{su}_n$, to infinite-dimensional fields — each adds condition — trace zero, skew, Hermitian, divergence-free — corresponding to preserving geometric structure — volume, metric, complex inner product, volume form — illustrating Klein's Erlangen philosophy: geometry = group, infinitesimal geometry = Lie algebra.
