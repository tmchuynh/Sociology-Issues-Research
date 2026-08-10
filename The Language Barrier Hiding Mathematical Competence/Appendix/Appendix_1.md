# Appendix

## Laplace Transform

It is one of the great operational tools of applied mathematics: it turns calculus into algebra.

> **Definition:** For a function $f(t)$ defined for $t\ge0$, the Laplace Transform is
> $$\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st} f(t) \,dt$$
> where $s$ is a complex variable, $s=\sigma+i\omega$, provided the improper integral converges.

The integral converges when $f$ is of exponential order: $|f(t)|\le Me^{ct}$ for some $M,c$ and $t$ large. Then $F(s)$ exists for $\Re(s)>c$.

This tool is widely used in engineering and physics to analyze control systems, circuits, and differential equations (Campbell and Haberman 247-250). The idea: differentiation in $t$-domain becomes multiplication by $s$ in $s$-domain.

### Historical Note

While named after Pierre-Simon Laplace who used it in probability in 1782, the essential ideas appeared much earlier in Leonhard Euler's work from the 1730s and 1750s (Deakin 264-267). Euler used similar integral transforms $ \int X(x) e^{ax} dx $ to solve differential equations decades before Laplace formalized the method, demonstrating how mathematical concepts often exist in practice before receiving formal names and notation (Deakin 268-269).

The transform remained relatively obscure until Oliver Heaviside rediscovered and popularized operational methods $p = d/dt$ in the 1880s-1890s for solving electrical circuit problems (Widder 419-420). Heaviside could solve telegraph equations "by inspection" but without rigorous justification. Thomas Bromwich, Gustav Doetsch and David Widder later made it rigorous via complex inversion.

### How to Compute and Invert

**Forward:** Evaluate the improper integral, often using integration by parts, or using tables for common functions (MIT OCW).

Example: $\mathcal{L}\{1\} = \int_0^\infty e^{-st}dt = 1/s$, $\Re(s)>0$.

**Inverse:** Recover $f(t)$ from $F(s)$, typically using partial fraction decomposition and inverse transform tables (Ungar 786-788; Widder 179-180). The rigorous inversion is Bromwich integral:

$$f(t) = \dfrac{1}{2\pi i}\int_{\sigma-i\infty}^{\sigma+i\infty} e^{st}F(s)\,ds$$

In practice, however, the inversion process can be remarkably intuitive once patterns are recognized, allowing practitioners to work "by inspection" without formal contour integration (Ungar 789-791). Most engineers use tables.

Beyond basic forms, the Laplace transform has been computed for remarkably complex functions including Bessel functions $J_n(t)$ (Spiegel 329-330), error functions $\text{erf}(t)$ (Opatowski 392), and the psi (digamma) function $\psi(t)$ (Dixit 593-600). These specialized results connect the Laplace transform to deep areas of analysis including the gamma function and Euler's constant (Pribitkin 241-245). Generalizations extend the classical Laplace transform to time scales and conformable derivatives, broadening applicability to discrete-continuous hybrid systems (Thange et al. 1699-1705).

### Properties — Why It Works

Let $F(s)=\mathcal{L}\{f\}$, $G(s)=\mathcal{L}\{g\}$ (Campbell and Haberman 251-255; Guggenheimer 196-198):

**1. Linearity:**
$$\mathcal{L}\{af+bg\} = aF+bG$$
Transform respects superposition.

**2. Differentiation in $t$ becomes multiplication in $s$:**
$$\mathcal{L}\{f'\}=sF(s)-f(0)$$
$$\mathcal{L}\{f''\}=s^2F(s)-sf(0)-f'(0)$$
$$\mathcal{L}\{f^{(n)}\}=s^nF(s)-s^{n-1}f(0)-\dots-f^{(n-1)}(0)$$

This is the core advantage: ODE becomes algebraic. Initial conditions $f(0),f'(0)$ are automatically incorporated — ideal for transient analysis (Guggenheimer 199-200).

**3. Differentiation in $s$:**
$$\mathcal{L}\{t f(t)\} = -F'(s)$$
$$\mathcal{L}\{t^n f(t)\}=(-1)^n F^{(n)}(s)$$

**4. Integration:**
$$\mathcal{L}\left\{\int_0^t f(\tau)d\tau\right\} = \dfrac{F(s)}{s}$$

**5. Time shift:**

$$\mathcal{L}\{f(t-a)u(t-a)\}=e^{-as}F(s)$$

where $u(t-a)$ is unit step.

**6. Frequency shift / Damping:**
$$\mathcal{L}\{e^{at}f(t)\}=F(s-a)$$

**7. Convolution — Transforms multiply:**
$$(f*g)(t)=\int_0^t f(\tau)g(t-\tau)d\tau$$
$$\mathcal{L}\{f*g\}=F(s)G(s)$$

This is crucial for LTI systems: output = input \* impulse response, so in $s$-domain $Y(s)=H(s)X(s)$.

**8. Initial and Final Value Theorems:**
$$f(0^+)=\lim_{s\to\infty}sF(s)$$
$$f(\infty)=\lim_{s\to0}sF(s)$$
if limits exist.

### Advantages of Laplace Transform

- **Simplification:** Converts complicated linear integro-differential equations with constant coefficients into easy algebraic equations (Lunardi 185-188). Solve algebraically, then invert.
- **Initial Conditions Built-In:** Unlike Fourier, automatically incorporates $f(0), f'(0)$ — making it ideal for initial value problems, transient circuit analysis, mechanical vibrations.
- **System Function / Transfer Function:** For ODE $a_n y^{(n)}+\dots+a_0 y = b_m x^{(m)}+\dots$, $H(s)=Y(s)/X(s)= \dfrac{b_m s^m+\dots}{a_n s^n+\dots}$. Poles of $H(s)$ give stability, frequency response, without solving entire equation (Campbell and Haberman 258-262).
- **Matrix Exponentials:** Provides elegant methods for computing $e^{At}$ in systems $\mathbf{x}'=A\mathbf{x}$ using $ \mathcal{L}\{e^{At}\} = (sI-A)^{-1}$ and algorithmic partial fractions (Adkins and Davidson 267-273).
- **Handles Discontinuities:** Easily handles Heaviside steps, Dirac deltas, periodic forcing — where classical methods break.

### Table of Common Transforms

| $f(t), t\ge0$             | $F(s)=\mathcal{L}\{f\}$                   | ROC        | Notes                                            |
| :------------------------ | :---------------------------------------- | :--------- | :----------------------------------------------- | --- | --- |
| $1$ (unit step)           | $\dfrac{1}{s}$                            | $\Re(s)>0$ |                                                  |
| $t^n$, $n\in\mathbb{N}_0$ | $\dfrac{n!}{s^{n+1}}$ (Pribitkin 238-240) | $\Re(s)>0$ | extends to $\Gamma(n+1)/s^{n+1}$ for non-integer |
| $e^{at}$                  | $\dfrac{1}{s-a}$                          | $\Re(s)>a$ |                                                  |
| $\sin(bt)$                | $\dfrac{b}{s^2+b^2}$ (Efthimiou 376-378)  | $\Re(s)>0$ |                                                  |
| $\cos(bt)$                | $\dfrac{s}{s^2+b^2}$                      | $\Re(s)>0$ |                                                  |
| $\sinh(bt)$               | $\dfrac{b}{s^2-b^2}$                      | $\Re(s)>b$ |                                                  |     |     |
| $\cosh(bt)$               | $\dfrac{s}{s^2-b^2}$                      | $\Re(s)>b$ |                                                  |     |     |
| $e^{at}\sin(bt)$          | $\dfrac{b}{(s-a)^2+b^2}$                  | $\Re(s)>a$ | damping shifts                                   |
| $e^{at}\cos(bt)$          | $\dfrac{s-a}{(s-a)^2+b^2}$                | $\Re(s)>a$ |                                                  |
| $t^n e^{at}$              | $\dfrac{n!}{(s-a)^{n+1}}$                 | $\Re(s)>a$ |                                                  |
| $\delta(t)$ Dirac         | $1$                                       | all $s$    |                                                  |
| $u(t-a)$ step at $a$      | $\dfrac{e^{-as}}{s}$                      | $\Re(s)>0$ |                                                  |
| Bessel $J_0(at)$          | $\dfrac{1}{\sqrt{s^2+a^2}}$ (Spiegel)     | $\Re(s)>0$ |                                                  |

In short: Laplace transform trades a hard calculus problem for an easier algebra problem in the $s$-domain, solves it, and trades back. Its power comes from linearity, the differentiation rule, and convolution theorem — which together make it the natural language of linear time-invariant systems.

## Taylor Series

For a function $f(x)$ that is infinitely differentiable near $a$, the Taylor series is the infinite polynomial that matches $f$ and all its derivatives at $a$:

$$f(x) = f(a) + f'(a)(x-a) + \dfrac{f''(a)}{2!}(x-a)^2 + \dfrac{f'''(a)}{3!}(x-a)^3 + \cdots = \sum_{n=0}^{\infty} \dfrac{f^{(n)}(a)}{n!}(x-a)^n$$

When $a=0$, this special case is called the Maclaurin series. The remarkable fact is that every power series with positive radius of convergence is actually a Taylor series of its sum function (Meyerson 51-52), creating a fundamental equivalence between locally convergent power series and analytic functions.

### The Core Idea: Local Polynomial Approximation

The Taylor series represents one of mathematics' most powerful ideas: any sufficiently smooth curve can be approximated locally by polynomials (Eves 40-45).

Think iteratively:

- **0th order:** $P_0(x)=f(a)$ — constant approximation. Matches value.
- **1st order:** $P_1(x)=f(a)+f'(a)(x-a)$ — tangent line. Matches value and slope. This is linear approximation.
- **2nd order:** $P_2(x)=P_1 + \dfrac{f''(a)}{2}(x-a)^2$ — osculating parabola. Matches curvature too.
- **nth order:** $P_n$ matches $f, f', ..., f^{(n)}$ at $a$.

Each term corrects the error of previous polynomial to higher order: $f(x)-P_n(x) = O((x-a)^{n+1})$.

This is why Taylor series are ubiquitous in physics: for small $(x-a)$, low-order Taylor polynomial is excellent. $\sin x \approx x$, $e^x \approx 1+x$, $\sqrt{1+x}\approx1+x/2$ are all first-order Taylor.

### Remainder and Convergence

Writing infinite series is formal; does it equal $f(x)$?

**Taylor's Theorem with Remainder:** If $f$ is $(n+1)$-times differentiable, then for $x$ near $a$,

$$f(x)=P_n(x)+R_n(x)$$

where $P_n$ is $n$th Taylor polynomial, and $R_n$ can be expressed in several forms. Lagrange form:

$$R_n(x)=\dfrac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1}$$

for some $\xi$ between $a$ and $x$. This is a direct generalization of the Mean Value Theorem, which is the $n=0$ case (Spiegel 263-266). Other forms: Cauchy, integral form:

$$R_n(x)=\dfrac{1}{n!}\int_a^x (x-t)^n f^{(n+1)}(t)dt$$

This connection guarantees that error in truncating after $n$ terms can be bounded and estimated if you can bound $f^{(n+1)}$.

**Convergence:** The series converges to $f(x)$ iff $R_n(x)\to0$ as $n\to\infty$.

Taylor series converge to the original function within a specific radius of convergence $R$, but can diverge outside this region or at pathological points (Erdős et al. 262-266).

- If $f$ is analytic (complex differentiable) near $a$, then $R$ is distance from $a$ to nearest singularity in complex plane. Example: $f(x)=1/(1+x^2)$ has Maclaurin series $1-x^2+x^4-\dots$ with $R=1$, because singularities at $\pm i$ are distance 1 from 0, even though $f$ is smooth on $\mathbb{R}$.
- If $f$ is $C^\infty$ but not analytic, series may converge to wrong function. Classic counterexample: $f(x)=e^{-1/x^2}$ for $x\neq0$, $f(0)=0$. All derivatives at $0$ are $0$, so Maclaurin series is $0$, which does not equal $f(x)$ for $x\neq0$. So infinite differentiability is not enough.
- Coefficients' behavior determines convergence: bounded coefficients $|f^{(n)}(a)/n!|\le M$ ensures convergence at least within unit circle $|x-a|<1$ (Duffin and Schaeffer 141-145). More generally, $R=1/\limsup |c_n|^{1/n}$ by Cauchy-Hadamard.

This enables both theoretical analysis and practical computation (Widder 126-130). Integration methods like Romberg integration leverage Taylor series to achieve high-precision numerical results by extrapolating trapezoidal errors which have even-power Taylor expansion (Rozema 284-288).

### Standard Maclaurin Series — The Toolbox

These converge for stated $x$ and are used constantly:

$$e^x = \sum_{n=0}^\infty \dfrac{x^n}{n!}=1+x+\dfrac{x^2}{2!}+\dfrac{x^3}{3!}+\cdots \quad |x|<\infty$$

$$\sin x = \sum_{n=0}^\infty (-1)^n\dfrac{x^{2n+1}}{(2n+1)!}=x-\dfrac{x^3}{3!}+\dfrac{x^5}{5!}-\cdots \quad |x|<\infty$$

$$\cos x = \sum_{n=0}^\infty (-1)^n\dfrac{x^{2n}}{(2n)!}=1-\dfrac{x^2}{2!}+\dfrac{x^4}{4!}-\cdots \quad |x|<\infty$$

$$\dfrac{1}{1-x}= \sum_{n=0}^\infty x^n =1+x+x^2+\cdots \quad |x|<1$$

$$\ln(1+x)=\sum_{n=1}^\infty (-1)^{n+1}\dfrac{x^n}{n}=x-\dfrac{x^2}{2}+\dfrac{x^3}{3}-\cdots \quad |x|<1, x=1\text{ converges conditionally}$$

$$(1+x)^\alpha = \sum_{n=0}^\infty \binom{\alpha}{n}x^n =1+\alpha x+\dfrac{\alpha(\alpha-1)}{2!}x^2+\cdots \quad |x|<1$$

These generate others by substitution, differentiation, integration.

### Operations with Taylor Series

If $f=\sum c_n(x-a)^n$ and $g=\sum d_n(x-a)^n$ converge for $|x-a|<R$:

- Addition, multiplication by polynomial multiplication (Cauchy product)
- Composition if inner series has zero constant term
- Differentiation and integration term-by-term inside $R$

This is why power series are so powerful: calculus on functions becomes algebra on coefficients.

Deep connection: The deep connection between Taylor series and Laplace transforms provides powerful tools for solving differential equations (Euler 305-307). Formally, $\mathcal{L}\{f\}(s)=\int_0^\infty e^{-st}f(t)dt$ can be expanded by expanding $f$ in Taylor series, and Laplace transform of $t^n$ is $n!/s^{n+1}$, linking Taylor coefficients to asymptotic expansion of $F(s)$ at infinity.

### Why Taylor Series Matter

1.  **Local linearization** is foundation of calculus, Newton's method, stability analysis.
2.  **Definition of functions:** Many functions ($e^x, \sin x, \cos x$) are _defined_ in analysis by their Taylor series, proving existence.
3.  **Numerical computation:** Computers evaluate transcendental functions by truncated Taylor / Chebyshev polynomials.
4.  **Physics:** Small oscillations, perturbation theory, relativity corrections — all Taylor expansions: $(1-v^2/c^2)^{-1/2}=1+v^2/2c^2+\cdots$.
5.  **Analytic continuation and complex analysis:** Taylor series is the seed from which analytic functions grow.

In one line: Taylor series says that if you know a function and all its derivatives at one point, you know the function everywhere within its radius of convergence — local information determines global behavior for analytic functions.

## Eigenvalue / Eigenvector

Formally, given a linear transformation represented by matrix $A \in \mathbb{F}^{n\times n}$, a nonzero vector $v$ is an eigenvector with eigenvalue $\lambda \in \mathbb{F}$ if

$$Av = \lambda v$$

The transformation takes vector $v$ and multiplies it by a scalar factor $\lambda$, preserving its direction up to flip: if $\lambda>0$ direction preserved, $\lambda<0$ reversed, $|\lambda|$ stretches, $|\lambda|<1$ compresses. Zero vector is excluded by definition because $A0 = \lambda 0$ holds for all $\lambda$ trivially (Chu 1-5).

The eigenvalue problem is one of the most fundamental in all of mathematics, appearing in differential equations, quantum mechanics, structural engineering, graph theory, and data analysis (Chu 5-10). It is the nonlinear heart of linear algebra.

### Why $Av=\lambda v$ Matters — Geometric Intuition

Most vectors are rotated and stretched by $A$. Eigenvectors are the special directions where $A$ acts purely as scaling.

- For rotation matrix $\begin{pmatrix}0&-1\\1&0\end{pmatrix}$ in $\mathbb{R}^2$, no real eigenvector — every nonzero vector is rotated $90^\circ$. Complex eigenvalues $\pm i$ appear.
- For shear $\begin{pmatrix}1&1\\0&1\end{pmatrix}$, one eigenvector direction $e_1=(1,0)$, eigenvalue $1$ — horizontal lines stay horizontal.
- For diagonal $D=\text{diag}(2,3)$, $e_1$ stretched by 2, $e_2$ by 3 — axes are eigenvectors.
- If $A$ describes deformation of an elastic body, eigenvectors are principal directions of strain.

If you have a basis of eigenvectors, $A$ becomes diagonal in that basis — the transformation decouples into independent 1D scalings. That is the goal of diagonalization.

### Finding Eigenvalues — Characteristic Equation

Finding eigenvalues requires solving the characteristic equation (Tisseur and Meerbergen 235-240).

$Av=\lambda v \iff (A-\lambda I)v=0$ has nonzero solution $v$ iff $A-\lambda I$ is singular:

$$\det(A-\lambda I)=0$$

This is a degree $n$ polynomial in $\lambda$ — the characteristic polynomial $p_A(\lambda)$.

For $n\times n$ matrix, this yields $n$ eigenvalues counting algebraic multiplicity over $\mathbb{C}$ by Fundamental Theorem of Algebra, though they may be complex even when $A$ is real. Example: rotation above gives $p(\lambda)=\lambda^2+1$, roots $\pm i$.

Steps:

1. Compute $p_A(\lambda)=\det(A-\lambda I)$.
2. Find roots $\lambda_i$ — eigenvalues.
3. For each $\lambda_i$, solve $(A-\lambda_i I)v=0$ to find eigenspace $E_{\lambda_i}= \ker(A-\lambda_i I)$. Dimension is geometric multiplicity $\le$ algebraic multiplicity.

If algebraic = geometric for all $\lambda$, $A$ is diagonalizable: $A = PDP^{-1}$ where $D=\text{diag}(\lambda_i)$ and columns of $P$ are eigenvectors. Then $A^k = PD^kP^{-1}$ easy, and ODE $x' = Ax$ solved by $x(t)=\sum c_i e^{\lambda_i t}v_i$.

If not diagonalizable, Jordan normal form $A = PJP^{-1}$ with Jordan blocks.

Numerical computation does NOT use $\det(A-\lambda I)$ for $n>4$ — polynomial root-finding is unstable. Instead QR iteration, power iteration, Lanczos/Arnoldi for large sparse.

### Spectrum of Generalizations

The standard problem $Av=\lambda v$ generalizes:

**1. Generalized eigenvalue problem:**
$$Av = \lambda B v$$
Appears in vibration: $Kx = \lambda Mx$ where $K$ stiffness, $M$ mass. If $B$ invertible, equivalent to $B^{-1}Av=\lambda v$, but better solved without inversion.

**2. Quadratic eigenvalue problem (QEP):**
$$(\lambda^2 M + \lambda C + K)x = 0$$
Arises in vibration analysis, acoustic modeling, and fluid-structure interaction, generalizing standard problem to account for mass $M$, damping $C$, and stiffness $K$ (Tisseur and Meerbergen 240-250). Second-order system $M\ddot{x}+C\dot{x}+Kx=0$ with ansatz $x=e^{\lambda t}v$ yields QEP. Linearized to $2n\times2n$ problem $\begin{pmatrix}0&I\\-K&-C\end{pmatrix}$.

**3. Polynomial and nonlinear eigenvalue problems:**
$$P(\lambda)x = (\sum_{k=0}^m \lambda^k A_k)x =0$$
$T(\lambda)x=0$ nonlinear in $\lambda$. Arise in delay equations, photonics.

**4. Singular value decomposition relation:** For $A$ non-square, $A^TA v = \sigma^2 v$ gives singular values $\sigma$.

### Inverse and Structured Problems

**Inverse eigenvalue problem:** Construct matrix with specified eigenvalues — given $\{\lambda_i\}$, find $A$ with properties (symmetric, nonnegative, banded) having those eigenvalues. Has applications in control theory, system identification, molecular structure determination, and designing mass-spring systems with given frequencies (Chu 10-20). Highly nontrivial — not all spectra realizable.

**Structured eigenvalue problems:** If $A$ symmetric/Hermitian: eigenvalues real, eigenvectors orthogonal, always diagonalizable. This is spectral theorem — basis of quantum mechanics where observables are Hermitian, eigenvalues are measurement outcomes. If $A$ orthogonal/unitary: eigenvalues $|\lambda|=1$. If $A$ stochastic: $\lambda=1$ is largest (Perron-Frobenius).

**Random matrix theory:** When entries of $A$ random, eigenvalue distributions exhibit phase transitions and universal behavior — Wigner semicircle for symmetric Gaussian, circular law for non-Hermitian, Tracy-Widom for largest eigenvalue — with applications to statistics (PCA), nuclear physics (energy levels), wireless communications, and finance (Baik et al. 1643-1650).

### Why Eigenvalues Dominate Applications

1.  **Differential equations:** $x' = Ax$ solution $x(t)=e^{At}x_0$. Growth/decay determined by $\Re(\lambda)$. $\Re(\lambda)<0$ stable.
2.  **Stability:** Linearized dynamical system stable iff all eigenvalues in left half-plane (continuous) or unit disk (discrete).
3.  **Vibrations:** Natural frequencies $\omega = \sqrt{\lambda}$ of $Kx=\lambda Mx$. Resonance.
4.  **Quantum mechanics:** Schrödinger $H\psi = E\psi$ — eigenvalues $E$ are energy levels.
5.  **Data analysis:** Covariance matrix $C$ eigenvalues are variances along principal components — PCA. Largest eigenvectors = directions of maximal variation. PageRank eigenvalue 1 of Google matrix.
6.  **Graph theory:** Adjacency matrix eigenvalues encode connectivity, expansion, clustering.

### Examples in Physics and Engineering

#### Musical Instruments (Resonance) — Eigenvalues You Can Hear

Musicians intuitively understand that instruments have "sweet spots" where certain notes resonate — they are finding physical eigenmodes without solving differential equations (Tisseur and Meerbergen 270-275). Every note an instrument plays is an eigenvalue; every timbre is a superposition of eigenfunction coefficients.

##### The Model: Ideal String Fixed at Both Ends

A guitar string fixed at both ends, length $L$, under tension $T$, with mass per length $\mu$, obeys the 1D wave equation derived from $F=ma$ on a small element:

$$\dfrac{\partial^2 u}{\partial t^2} = c^2 \dfrac{\partial^2 u}{\partial x^2}$$
where $u(x,t)$ is transverse displacement at position $x$ and time $t$, and
$$c = \sqrt{\dfrac{T}{\mu}}$$
is wave speed. Higher tension = faster wave = higher pitch; heavier string = slower wave = lower pitch.

Boundary conditions: $u(0,t)=u(L,t)=0$ — fixed at nut and saddle, cannot move. Initial conditions: shape $u(x,0)=f(x)$ and velocity $u_t(x,0)=g(x)$ from pluck.

##### Separation of Variables → Eigenvalue Problem

Seek standing wave solutions where spatial and temporal parts separate: $u(x,t)=X(x)\cdot \cos(\omega t)$ or $\sin(\omega t)$. Plug into wave equation:

$$\dfrac{X''}{X} = -\dfrac{\omega^2}{c^2} = -k^2 = \text{constant}$$

This yields the spatial eigenvalue problem — a Helmholtz equation in 1D:

$$\dfrac{d^2 X}{dx^2} = -k^2 X, \quad X(0)=X(L)=0, \quad \text{where } k=\dfrac{\omega}{c}$$

Here $d^2/dx^2$ is the linear operator, $X$ is eigenfunction, $-k^2$ is eigenvalue. Boundary conditions quantize $k$.

General solution: $X(x)=A\sin(kx)+B\cos(kx)$. $X(0)=0 \implies B=0$. $X(L)=0 \implies A\sin(kL)=0$. For nontrivial $A\neq0$, need $\sin(kL)=0$:

$$k_n L = n\pi, \quad n=1,2,3,\dots$$

Only discrete $k$ allowed — quantization emerges from boundary conditions. This is exactly like particle in a box in quantum mechanics.

##### Eigenfunctions and Eigenvalues

**Eigenfunctions (mode shapes):**
$$X_n(x) = \sin\left(\dfrac{n\pi x}{L}\right), \quad n=1,2,3,\dots$$

These are the only shapes the string can vibrate in without "twisting into chaos" — each is an eigenfunction of $d^2/dx^2$ with eigenvalue $-k_n^2=-(n\pi/L)^2$. They are orthogonal: $\int_0^L X_n X_m dx =0$ for $n\neq m$. They form basis for any shape — Fourier sine series.

- $n=1$: one hump, no interior nodes. Whole string moves in phase.
- $n=2$: two humps, one node in middle at $x=L/2$ that stays still.
- $n=3$: three humps, two nodes at $L/3, 2L/3$.
- $n$: $n$ humps, $n-1$ interior nodes.

**Eigenvalues (frequencies):**
$$\omega_n = c k_n = \dfrac{n\pi c}{L}, \quad f_n = \dfrac{\omega_n}{2\pi} = \dfrac{nc}{2L} = \dfrac{n}{2L}\sqrt{\dfrac{T}{\mu}}$$

Frequencies are integer multiples of fundamental — harmonic series. This harmonicity is why string sounds musical. Inharmonic instruments like drums have $f_n$ not integer multiples.

For a guitar A string: $L\approx0.65$ m, $f_1=110$ Hz (A2). Then $c=2Lf_1=143$ m/s, implies $T=\mu c^2$. With typical $\mu\approx0.005$ kg/m, $T\approx102$ N.

- $n=1$: Fundamental, 110 Hz — dominant pitch you hear, amplitude largest.
- $n=2$: First overtone / second harmonic, 220 Hz — octave higher (A3).
- $n=3$: Second overtone, 330 Hz — octave+fifth (E4 approx).
- $n=4$: Third overtone, 440 Hz — two octaves (A4).
- $n=5$: 550 Hz — etc., diminishing amplitude.

##### Superposition — What Happens When You Pluck

When you pluck, initial displacement $f(x)$ is triangular — pulled at point $x_0$. The string "knows" its eigenmodes instinctively — physics forces vibration into these patterns. Any initial shape decomposes into sum of eigenfunctions (Fourier's insight):

$$u(x,t)=\sum_{n=1}^\infty a_n \sin\left(\dfrac{n\pi x}{L}\right)\cos(2\pi f_n t + \phi_n)$$

Coefficients $a_n$ depend on _where_ you pluck, given by projection:
$$a_n = \dfrac{2}{L}\int_0^L f(x)\sin\left(\dfrac{n\pi x}{L}\right)dx$$

If pluck at center $x_0=L/2$:
$$a_n \propto \dfrac{1}{n^2}\sin\left(\dfrac{n\pi}{2}\right)$$
So $a_2,a_4,a_6=0$ — even harmonics have node at center, cannot be excited by plucking at node. Result: hollow, clarinet-like, only odd harmonics.

If pluck near bridge $x_0\approx0.1L$:
$\sin(n\pi x_0/L)$ non-zero for many $n$, $a_n \sim 1/n$ slowly decaying — many high harmonics excited, bright, twangy timbre (Tisseur and Meerbergen 250-255). Classical guitarists move plucking hand to control timbre — sul tasto (near fingerboard) = soft, few harmonics; ponticello (near bridge) = bright, many harmonics.

Damping $C$ in real string makes higher modes decay faster: $u_n\sim e^{-\zeta_n t}\cos(\omega_{d,n}t)$, so brightness fades.

##### Every Instrument is an Eigenvalue Problem

- **Violin, piano, harp:** Same as guitar, but stiffness adds term $EI u_{xxxx}$ → slight inharmonicity $f_n \approx n f_1 (1+Bn^2)$, why piano octaves are stretched when tuned.
- **Flute / organ pipe (air column):** Pressure $p$ obeys wave equation. Open-open pipe: $p=0$ at both ends → same eigenvalues $f_n=nc/2L$. Closed-open (clarinet): node at closed, antinode at open → $f_n=(2n-1)c/4L$ — only odd harmonics, hence clarinet sounds different from flute (Chu 25-30).
- **Drum membrane (2D):** $\nabla^2 X = -k^2 X$ on disk with $X=0$ at rim. Eigenfunctions are Bessel functions $J_m(k_{mn}r)\cos(m\theta)$, eigenvalues are zeros of Bessel $J_m$. Frequencies not harmonic — drum sounds inharmonic.
- **Room acoustics:** Same wave equation in 3D box — eigenvalues are room modes causing boomy bass at $f_{nx,ny,nz}= (c/2)\sqrt{(n_x/L_x)^2+(n_y/L_y)^2+(n_z/L_z)^2}$.

---

#### Google's Original PageRank Algorithm — The \$25 Billion Eigenvector

When you search Google and trust that the top result is probably most relevant, you're relying on eigenvector mathematics you've never seen (Bryan and Leise 580-581). The formalism $Av=\lambda v$ and characteristic polynomials $\det(A-\lambda I)=0$ provide precision, but the conceptual competence — recognizing special directions, resonant patterns, influential positions, and dominant modes — operates continuously in perception, music, social navigation, and spatial reasoning (Schonefeld 318-319).

**The \$25 Billion Eigenvector:** In 2006, Google's market value was tied to this eigenvector computation running on billions of pages (Bryan and Leise 569). Larry Page and Sergey Brin's 1998 Stanford paper's brilliance: reducing the subjective problem of "importance" to an objective eigenvalue problem (Langville and Meyer 135-145). Modern search uses hundreds of factors, but PageRank's eigenvector remains foundational as a centrality signal (Langville and Meyer 145-155).

##### The Core Idea: Importance as Recursive Voting

Old search counted keywords. Page and Brin asked: what if a page's importance is determined by who links to it?

Idea: A link $j \to i$ is a vote by $j$ for $i$. But not all votes equal — a vote from an important page counts more than a vote from an obscure page. So:

$$\text{importance}(i) = \sum_{j \text{ links to } i} \dfrac{\text{importance}(j)}{\text{outlinks}(j)}$$

This is recursive: importance of $i$ depends on importance of $j$, which depends on who links to $j$, etc. This is exactly $ \pi = H\pi$ — an eigenvector problem.

Imagine simplified web with 4 pages. Define hyperlink matrix $H$ where

$$H_{ij} = \dfrac{1}{n_j} \text{ if page } j \text{ links to page } i, \quad 0 \text{ otherwise}$$

$n_j$ = number of outlinks from page $j$. Column $j$ sums to 1 if $j$ has outlinks — $H$ is column-stochastic — representing how $j$ distributes its importance equally among pages it links to.

Suppose:

- Page 1 links to pages 2,3,4 ($n_1=3$)
- Page 2 links to page 1 ($n_2=1$)
- Page 3 links to pages 1,4 ($n_3=2$)
- Page 4 links to pages 1,2,3 ($n_4=3$)

Then:

$$
H = \begin{bmatrix}
0 & 1 & \dfrac12 & \dfrac13 \\
\dfrac13 & 0 & 0 & \dfrac13 \\
\dfrac13 & 0 & 0 & \dfrac13 \\
\dfrac13 & 0 & \dfrac12 & 0
\end{bmatrix}
$$

Check columns: col1 = 0+1/3+1/3=1, etc. $H$ describes a Markov chain — random surfer following random outlink.

If we tried to solve $H\pi = \pi$, we get stationary distribution of this Markov chain. But two problems:

1.  **Dangling nodes:** Pages with no outlinks make column sum 0, not stochastic.
2.  **Disconnected components / rank sinks:** Random surfer can get trapped in loop, never leave. Eigenvalue 1 may have multiplicity >1 or zero entries.

##### The Google Fix: Teleportation

PageRank assumes a "random surfer" who follows links with probability $d\approx0.85$ and with probability $1-d=0.15$ gets bored and jumps to a uniformly random page anywhere on web.

Google matrix:

$$G = dH + \dfrac{1-d}{n}E$$

where $E$ is $n\times n$ matrix of all ones, $n=4$ pages, $d$ damping factor usually $0.85$. Second term = $(1-d)/n$ everywhere.

Now $G$ is positive (all entries >0), column-stochastic, irreducible and aperiodic. By Perron-Frobenius theorem for positive matrices:

- Spectral radius $\rho(G)=1$ is simple eigenvalue
- Eigenvalue 1 has strictly positive eigenvector $\pi$ unique up to scaling
- All other eigenvalues $|\lambda|<1$, in fact $|\lambda_2|\le d$

So power method converges quickly.

With $d=0.85$, $n=4$:

$$G = 0.85H + 0.0375\begin{bmatrix}1&1&1&1\\1&1&1&1\\1&1&1&1\\1&1&1&1\end{bmatrix}$$

$$
G \approx \begin{bmatrix}
0.0375 & 0.8875 & 0.4625 & 0.3208\\
0.3208 & 0.0375 & 0.0375 & 0.3208\\
0.3208 & 0.0375 & 0.0375 & 0.3208\\
0.3208 & 0.0375 & 0.4625 & 0.0375
\end{bmatrix}
$$

##### The Eigenvector Equation

PageRank vector $\pi$ satisfies

$$G\pi = \pi$$

This is eigenvector equation with eigenvalue $\lambda=1$ (Bryan and Leise 572-575). Normalization $\sum_i \pi_i =1$, $\pi_i\ge0$ — it is probability distribution of where random surfer is after long time.

Solve $(G-I)\pi=0$. For our 4-page example, solving gives (up to rounding):

$$\pi = \begin{bmatrix}0.387 \\ 0.213 \\ 0.177 \\ 0.223 \end{bmatrix}$$

Interpretation:

- Page 1 receives 38.7% of importance — top result. Why? 3 pages link to it (2,3,4), including Page 2 which gives it all its importance.
- Page 4: 22.3%
- Page 2: 21.3%
- Page 3: 17.7% last.

Ranking: 1 > 4 > 2 > 3. If you search query matching all 4, Page 1 returned first.

In real web of 1998: $n=25$ million, $H$ is $25M\times25M$ but sparse — average 10 outlinks per page, so only ~250M nonzeros. Storing dense $G$ impossible. Power method uses sparsity:

Initialize $\pi^{(0)}=(1/n)\mathbf{1}$, iterate:

$$\pi^{(k+1)} = G\pi^{(k)} = dH\pi^{(k)} + \dfrac{1-d}{n}\mathbf{1}$$

Because $H$ sparse, $H\pi^{(k)}$ is $O(n)$. Convergence rate $O(d^k)$ — error after $k$ steps $\approx d^k$. With $d=0.85$, 50-100 iterations enough for tolerance $10^{-9}$ even for $n=8$ billion today.

This is why PageRank scaled — it is power iteration for dominant eigenvector of sparse Markov chain.

##### Why Eigenvalue 1?

$G$ is column-stochastic: columns sum to 1, because $H$ columns sum to 1 and $E$ columns sum to $n$ times $(1-d)/n$. So $\mathbf{1}^T G = \mathbf{1}^T$. So 1 is eigenvalue with left eigenvector $\mathbf{1}^T$. Since spectrum of $A$ and $A^T$ same, $G$ has right eigenvector with eigenvalue 1 — our $\pi$.

Perron-Frobenius guarantees $\pi>0$ and unique, solving rank sink problem.

##### Intuition: Flow of Importance

Think of $\pi$ as fluid. Each page $j$ has $\pi_j$ amount. It keeps $(1-d)\pi_j$ to distribute uniformly via teleportation, and sends $d\pi_j/n_j$ along each outlink. Equilibrium when inflow = outflow for each page — stationary distribution. Important pages are those with large inflow — many inlinks from important pages.

This is eigenvector centrality — same math used for social influence, protein importance, etc. Google's insight was web's link graph encodes human judgment; eigenvector extracts global consensus from local votes.

Modern search: PageRank now one of hundreds of signals (BERT, freshness, location), but original principle — web as Markov chain, importance as dominant eigenvector of $G$ — remains foundational architecture that turned a linear algebra problem into a \$2 trillion company.

## Game Theory

Game theory is a mathematical framework for analyzing strategic interactions between rational decision-makers, where the outcome for each participant depends on the actions of others (Binmore 25-27). It models scenarios involving conflict or cooperation to identify optimal strategies, commonly used in economics, political science, evolutionary biology, and social sciences to predict behaviors (Resnik 121-125).

It was formalized by von Neumann and Morgenstern in _Theory of Games and Economic Behavior_ (1944) and revolutionized by John Nash's equilibrium concept in 1950.

The notation of payoff matrices $u_i(s_1, s_2, \ldots, s_n)$ and Nash equilibrium conditions formalizes thinking that humans already do implicitly in countless social situations — haggling, poker, driving in traffic, dating. While formal game theory requires mathematical sophistication, strategic competence — anticipating others' responses and optimizing accordingly — operates constantly in daily life, unrecognized as "mathematics" by those who claim to be "bad at math" (Stone 240-244; Rubinstein 140-146).

### Formal Setup

A finite game in normal form is:

- $N=\{1,\dots,n\}$ players
- For each player $i$, a strategy set $S_i$ — pure strategies available
- For each player $i$, a payoff / utility function $u_i: S_1\times\cdots\times S_n \to \mathbb{R}$

A strategy profile $s=(s_1,\dots,s_n)\in S$ determines payoff $u_i(s)$ to each player.

**Assumptions:** Players are rational — they maximize expected utility; they are intelligent — they know the game, know others are rational, know others know they know, etc. — common knowledge of rationality.

Game theory provides a rigorous mathematical framework, often requiring knowledge of calculus and real analysis, particularly for finding "existence proofs" of solutions such as Nash's theorem (Binmore 28-30). The core goal is to determine the best action for a player when outcome depends on actions of others (Resnik 125-128). Interestingly, game theory exhibits uncertainty principles analogous to quantum mechanics, where certain strategic information cannot be simultaneously optimized (Székely and Rizzo 688-695) — e.g., you cannot simultaneously maximize payoff and guarantee minimax in some games.

### Payoff Matrices

Used to visualize and calculate results of simultaneous-move games for each player based on their choices (Resnik 130-135). Matrix entries represent utilities $u_i(s_1,s_2)$.

Classic 2-player, 2-strategy Prisoner's Dilemma. Two suspects, Cooperate = stay silent, Defect = betray. Payoffs = negative years in prison, higher is better:

|                  | B: Cooperate | B: Defect |
| ---------------- | ------------ | --------- |
| **A: Cooperate** | (-1, -1)     | (-3, 0)   |
| **A: Defect**    | (0, -3)      | (-2, -2)  |

First number $u_A$, second $u_B$. If both cooperate, 1 year each. If A defects, B cooperates, A free, B gets 3 years. Both defect, 2 years each. What happens? See Nash below.

### Nash Equilibrium

**Nash Equilibrium**: A situation where no player can benefit by unilaterally changing strategies while others keep theirs unchanged (Binmore 30-32). It is a stable fixed point of best-response reasoning — no one wants to deviate alone.

Formally, strategy profile $(s_1^*, s_2^*, \dots, s_n^*)$ is a Nash equilibrium if for every player $i$ and every alternative strategy $s_i \in S_i$:

$$u_i(s_1^*, \dots, s_i^*, \dots, s_n^*) \geq u_i(s_1^*, \dots, s_i, \dots, s_n^*)$$

where $u_i$ is player $i$'s utility function. It is foundational for predicting stable outcomes in competitive scenarios (Resnik 135-140).

In Prisoner's Dilemma, (Defect, Defect) is unique Nash equilibrium: if B defects, A's best response is defect (-2 > -3); if B cooperates, A's best response is still defect (0 > -1). Defect dominates. So rational play leads to (-2,-2), worse than (-1,-1) — dilemma.

Nash's Theorem (1950): Every finite game has at least one Nash equilibrium in mixed strategies. Proof uses Kakutani fixed point theorem — requires calculus and real analysis (Binmore 28-30). Existence proof is non-constructive.

### Mixed Strategies and Utility Maximization

Often no pure Nash exists. Rock-Paper-Scissors has no pure equilibrium — any pure strategy is beaten.

Players assign numerical values (utility) to outcomes, acting to maximize own expected utility (Binmore 26-28). To guarantee equilibrium, allow randomization.

Mixed strategy $\sigma_i$ is probability distribution over $S_i$. Let $\sigma_i(s_i)$ = prob player $i$ plays $s_i$. Profile $\sigma=(\sigma_1,\dots,\sigma_n)$ induces distribution over outcomes:

Expected utility for mixed strategies is computed as

$$E[u_i] = \sum_{s \in S} p(s)\cdot u_i(s) = \sum_{s_1\in S_1}\cdots\sum_{s_n\in S_n} \left(\prod_{j=1}^n \sigma_j(s_j)\right) u_i(s_1,\dots,s_n)$$

where $p(s)$ is probability of strategy profile $s$ — product if independent randomization.

Nash equilibrium in mixed: $\sigma^*$ such that for all $i$, $\sigma_i^*$ maximizes $E[u_i]$ given $\sigma_{-i}^*$.

Rock-Paper-Scissors equilibrium: each player plays (1/3,1/3). Expected payoff 0. Any deviation exploited.

**Indifference principle:** In mixed equilibrium, player randomizes to make opponent indifferent among strategies in support. This gives linear equations to solve.

### Mathematical Techniques

The mathematics needed scales with the game. Simple parlor games need arithmetic; general existence and computation need topology, convex analysis, and fixed-point theorems (Weil 360-363; Binmore 25-34).

**1. Basic 2x2 — Arithmetic, Dominance, Best-Response**

For finite games with 2 players, 2 strategies each, you can solve by hand.

- **Strict dominance:** Strategy $s_i$ strictly dominates $s_i'$ if $u_i(s_i,s_{-i}) > u_i(s_i',s_{-i})$ for all $s_{-i}$. Rational player never plays dominated strategy — eliminate it. Iterate: iterated elimination of strictly dominated strategies (IESDS) yields unique prediction in Prisoner's Dilemma, many games.
- **Best-response:** For each column (opponent's strategy), mark row player's highest payoff; for each row, mark column player's highest payoff. Cells where both payoffs marked are pure Nash equilibria.
- Example: Stag Hunt
  | | Hare | Stag
  |---|---|---|
  | Hare | 2,2 | 2,0 |
  | Stag | 0,2 | 3,3 |

Best responses: If opponent plays Hare, you prefer Hare (2>0). If opponent plays Stag, you prefer Stag (3>2). Two pure Nash: (Hare,Hare) and (Stag,Stag) — coordination problem.

**2. Calculus — Continuous Strategies**

For continuous $S_i=[0,\infty)$ like Cournot duopoly where firms choose quantity $q_i$, market price $P(Q)=a-bQ$, $Q=q_1+q_2$, cost $c q_i$, profit:

$$u_i(q_1,q_2)= q_i(a-b(q_1+q_2))-c q_i$$

Nash equilibrium solves first-order condition $\partial u_i/\partial q_i =0$ with $\partial^2 u_i/\partial q_i^2 <0$ for max:

$$\partial u_1/\partial q_1 = a - b(2q_1+q_2)-c =0 \implies q_1 = \dfrac{a-c-bq_2}{2b} = BR_1(q_2)$$

Similarly $BR_2(q_1)=\dfrac{a-c-bq_1}{2b}$. Intersection of best-response functions gives Nash:

$$q_1^*=q_2^*=\dfrac{a-c}{3b}$$

This method — best-response calculus — extends to any differentiable $u_i$: solve $\nabla_{s_i} u_i =0$. Requires checking second-order and boundary.

For Hotelling location, Bertrand pricing, public goods contribution games, calculus yields interior equilibria; often need Kuhn-Tucker for inequality constraints.

**3. Linear Algebra — Zero-Sum, Lemke-Howson, Perron**

Zero-sum game $u_1=-u_2=A$ payoff matrix for row player.

Row player chooses mixed $\mathbf{x}\ge0, \sum x_i=1$ to maximize $\min_j \mathbf{x}^T A e_j$.
Column player chooses $\mathbf{y}$ to minimize $\max_i e_i^T A \mathbf{y}$.

Von Neumann's Minimax theorem:
$$\max_{\mathbf{x}}\min_{\mathbf{y}} \mathbf{x}^T A \mathbf{y} = \min_{\mathbf{y}}\max_{\mathbf{x}} \mathbf{x}^T A \mathbf{y} = v^*$$

Value $v^*$ found via linear programming duality:

Primal: $\max v$ s.t. $A^T\mathbf{x} \ge v\mathbf{1}, \sum x_i=1, \mathbf{x}\ge0$
Dual: $\min v$ s.t. $A\mathbf{y} \le v\mathbf{1}, \sum y_j=1, \mathbf{y}\ge0$

Solving LP via simplex gives equilibrium. Eigenvector methods appear when $A$ is symmetric — equilibrium proportional to Perron eigenvector.

For general bimatrix games $(A,B)$ not zero-sum, Lemke-Howson algorithm follows a path of almost-completely-labeled polytopes defined by linear inequalities $A\mathbf{y}\le \mathbf{1}$, $B^T\mathbf{x}\le \mathbf{1}$ to find Nash. It is pivoting like simplex. Complexity is PPAD-complete — believed hard, but practical for moderate size.

**4. Probability — Mixed Strategies and Minimax**

For mixed strategies, expected utility is linear in probabilities:

$$E[u_i](\sigma)=\sum_{s} \left(\prod_j \sigma_j(s_j)\right) u_i(s)$$

Linearity yields key property:

> **Indifference principle:** If $\sigma^*$ is Nash and player $i$ mixes between $s_i$ and $s_i'$ with positive probability, then $E[u_i(s_i,\sigma_{-i}^*)]=E[u_i(s_i',\sigma_{-i}^*)]$ — otherwise he'd shift to higher.

So to find mixed equilibrium, set opponent indifferent.

Example: Matching Pennies $A=\begin{pmatrix}1&-1\\-1&1\end{pmatrix}$. Let column mix $(q,1-q)$. Row payoff for playing Top: $q*1+(1-q)*(-1)=2q-1$. Bottom: $q*(-1)+(1-q)*1=1-2q$. Indifference $2q-1=1-2q \implies q=1/2$. So equilibrium $(1/2,1/2)$.

Minimax theorem: $\max_{\sigma_1}\min_{\sigma_2}E[u] = \min_{\sigma_2}\max_{\sigma_1}E[u]$ — order of pessimism doesn't matter in zero-sum. Proof uses separating hyperplane.

**5. Fixed Point Topology — Existence Proof**

Nash's 1950 existence theorem: Every finite game has at least one mixed Nash equilibrium.

Proof sketch: Define best-response correspondence $BR(\sigma) = \{ \tau : \tau_i \in \arg\max E[u_i(\cdot,\sigma_{-i})] \}$. Show $BR$ is upper hemicontinuous, convex-valued, maps compact convex simplex $\Delta=\prod \Delta_i$ to itself. Apply Kakutani fixed-point theorem — a generalization of Brouwer fixed-point — there exists $\sigma^* \in BR(\sigma^*)$, which is Nash. Requires real analysis, topology. Same technique gives Arrow-Debreu existence of competitive equilibrium in economics.

**6. Dynamic Programming / Backward Induction — Extensive Form**

For sequential games, represent as game tree with information sets. Use backward induction to find subgame perfect equilibrium (SPE) — Nash in every subgame, eliminating non-credible threats.

Algorithm: Start at leaves, compute payoffs, move up: at decision node of player $i$, choose action maximizing $u_i$ given already-solved continuation. Replace node with that payoff.

Example: Entry game: Entrant chooses In/Out, then Incumbent chooses Fight/Accommodate. Payoffs: (Out:0,2), (In,Fight:-1,-1), (In,Accommodate:1,1). Backward induction: If Entrant In, Incumbent prefers Accommodate (1>-1). So Entrant anticipates 1>0, chooses In. SPE (In, Accommodate), even though (Out, Fight) is Nash with threat "I will fight" — not credible, because Fight not optimal off-path.

For imperfect information, need sequential rationality and beliefs — Perfect Bayesian Equilibrium solved via Bayes rule + backward induction.

### Types and Extensions

**1. Cooperative vs Non-cooperative**

- **Non-cooperative:** Studies individual strategic choice, self-enforcing agreements. Solution: Nash equilibrium. Focus of most modern theory.
- **Cooperative:** Allows binding agreements, coalitions. Question: how to divide surplus? $N$ players, characteristic function $v(C)$ value coalition $C$ can achieve. Solutions:
  - **Core:** allocations where no coalition can deviate and do better for all its members — $ \sum*{i\in C} x_i \ge v(C)$ for all $C$, $\sum*{i\in N} x_i=v(N)$.
  - **Shapley value:** Fair division based on marginal contribution averaged over all arrival orders: $\phi_i(v)=\dfrac1{n!}\sum_{\pi}[v(P_i^\pi\cup\{i\})-v(P_i^\pi)]$, where $P_i^\pi$ players before $i$ in permutation $\pi$. Axiomatizes fairness.

**2. Zero-Sum vs Non-Zero-Sum**

- **Zero-sum:** $u_1+u_2=0$ — strictly competitive, one's gain is other's loss. Poker simplified, chess. Minimax, value. No cooperation possible.
- **Non-zero-sum:** General $u_1+u_2\neq0$ — allows both conflict and cooperation. Prisoner's Dilemma, Stag Hunt, Chicken. Win-win possible, but also dilemma. Nash equilibria may be Pareto inefficient — (Defect,Defect) Pareto dominated by (Cooperate,Cooperate).

**3. Repeated Games**

Same stage game $G$ played infinitely ($t=0,1,\dots$) with discount factor $\delta\in(0,1)$ — future payoff weighted $\delta^t$. Total payoff $\sum \delta^t u_i(s^t)$.

Folk theorem: If players patient enough $\delta$ close to 1, any feasible payoff above minmax can be sustained as subgame perfect equilibrium via threat strategies — e.g., Grim Trigger: cooperate until someone defects, then punish forever. So cooperation can be sustained by threats even when stage Nash is defect — explains social norms, cartels, relational contracts. Tit-for-Tat (cooperate initially, copy opponent's last move) famously robust in Axelrod tournaments.

Mathematically, uses one-shot deviation principle and dynamic programming.

**4. Evolutionary Game Theory**

Strategies are phenotypes encoded in genes, payoff is fitness (expected offspring). Population state $\mathbf{x}$ frequencies. Replicator dynamics: $\dot{x}_i = x_i (u_i(\mathbf{x})-\bar{u}(\mathbf{x}))$ — strategies with above-average fitness grow.

Equilibrium concept: Evolutionarily Stable Strategy (ESS) — strategy $\sigma$ resistant to invasion by small mutant fraction $\epsilon$: $u(\sigma,(1-\epsilon)\sigma+\epsilon \tau) > u(\tau,(1-\epsilon)\sigma+\epsilon \tau)$ for all $\tau\neq\sigma$ near. Stronger than Nash: Nash is resistant to best-response, ESS resistant to mutant that could do equally well. Example: Hawk-Dove game: $V$ resource, $C$ cost of fight. Pure Hawk not ESS if $C>V$, mixed ESS with $p=V/C$ probability Hawk.

Explains animal conflict, cooperation without rationality — just natural selection.

**5. Bayesian Games — Incomplete Information**

Players have private types $t_i$ — e.g., valuation in auction, cost in oligopoly, ability. Types drawn from common prior $p(t)$. Player knows own type, not others'. Strategy is type-dependent $s_i(t_i)$.

Payoff $u_i(s_1,\dots,s_n; t_1,\dots,t_n)$. Equilibrium: Bayes-Nash equilibrium where each type $t_i$ maximizes expected utility given beliefs about others' types conditional on own type:

$$\sigma_i^*(\cdot|t_i) \in \arg\max \mathbb{E}_{t_{-i}|t_i}[u_i(\sigma_i, \sigma_{-i}^*(t_{-i}); t_i,t_{-i})]$$

Foundation of auction theory (Vickrey, Myerson), signaling games (Spence education), screening, mechanism design — designing games to achieve desired outcome — e.g., second-price auction is dominant-strategy incentive compatible, revenue equivalence theorem.

In all cases, mathematics turns "what will others do?" into fixed-point, optimization, or dynamical systems problems — making intuition precise and testable.

Game theory is the mathematics of $u_i(s_i, s_{-i})$ — your payoff depends on others' choices. Nash equilibrium is the point where expectations are consistent and no one regrets their choice given others' choices — the natural rest point of strategic reasoning.

### Prisoner's Dilemma

Two suspects are arrested and interrogated separately, no communication. Prosecutor offers deal. Each has two strategies:

- **Cooperate** (with each other, stay silent — C)
- **Defect** (betray the other, confess — D)

Note: terminology is confusing — Cooperate means cooperate with accomplice, defect from prosecutor, and vice versa. Game theorists often use C/D.

The payoff matrix shows years in prison as negative utility — higher numbers better, less prison. Entry $(a,b)$ = (Suspect 1's years, Suspect 2's years):

|                          | **Suspect 2: Cooperate** | **Suspect 2: Defect** |
| ------------------------ | ------------------------ | --------------------- |
| **Suspect 1: Cooperate** | (-1, -1)                 | (-10, 0)              |
| **Suspect 1: Defect**    | (0, -10)                 | (-5, -5)              |

Interpretation: If both silent, police have minor evidence: 1 year each. If one confesses and other silent, confessor goes free 0, silent gets 10. If both confess, 5 years each — reduced from 10 for cooperation with police, but worse than mutual silence.

#### Dominance Reasoning

From Suspect 1's perspective:

- If Suspect 2 cooperates: Defect gives 0 years vs. Cooperate gives 1 year → **Defect is better** by 1 year.
- If Suspect 2 defects: Defect gives 5 years vs. Cooperate gives 10 years → **Defect is better** by 5 years.

Defecting yields strictly higher payoff regardless of opponent's choice. It strictly dominates Cooperate.

Defecting is a **dominant strategy** — optimal regardless of opponent's choice (Cunningham 15-18). Dominant strategy equilibrium concept is stronger than Nash: it doesn't require belief about opponent.

By symmetry, Suspect 2 has identical reasoning. Both rationally choose to defect, yielding outcome **(-5, -5)**.

#### Nash Equilibrium

(Defect, Defect) is the unique Nash equilibrium (Cunningham 18-20). At this point, no unilateral deviation helps:

$$u_1(\text{Defect}, \text{Defect}) = -5 \geq u_1(\text{Cooperate}, \text{Defect}) = -10$$
$$u_2(\text{Defect}, \text{Defect}) = -5 \geq u_2(\text{Defect}, \text{Cooperate}) = -10$$

Check deviations: If 1 deviates to Cooperate while 2 stays Defect, 1 goes from -5 to -10 — worse. So Nash.

Mutual cooperation (-1,-1) would be better for both than mutual defection (-5,-5) — 4 years less each. But it is not stable: each has temptation to deviate to 0. If both at (-1,-1), each thinks "if I defect while other cooperates, I go free."

This illustrates how individual rationality can lead to collective irrationality — a fundamental insight with implications for environmental policy, arms races, and public goods provision (Rubinstein 100-110). (Cooperate, Cooperate) Pareto dominates (Defect,Defect) — both better — but not Nash. (Defect,Defect) is Nash but Pareto inefficient. That tension is the dilemma.

General definition: Prisoner's Dilemma requires payoffs $T > R > P > S$ where $T$=Temptation to defect, $R$=Reward mutual cooperate, $P$=Punishment mutual defect, $S$=Sucker's payoff. Here 0 > -1 > -5 > -10.

#### Why It Matters Everywhere

- **Environmental:** Two firms can pollute (Defect) cheaply or abate (Cooperate) costly. Mutual abatement good for both long-term, but each has incentive to free-ride and pollute while other abates.
- **Arms race:** Cooperate = disarm, Defect = arm. Mutual disarm best, but each fears being exploited, so both arm.
- **Public goods:** Cooperate = contribute, Defect = free ride. Doping in sports, overfishing, climate change — all PD.
- **Pricing:** Two firms can keep prices high (Cooperate) or undercut (Defect). Mutual high price profitable, but each wants to undercut to steal market — leads to price war.

#### Repeated Prisoner's Dilemma — How Cooperation Emerges

When game repeats indefinitely, cooperation can emerge through conditional strategies (Resnik 155-165).

One-shot PD predicts defection. Real humans cooperate often. Why? Because life is repeated. If you defect today, opponent can punish tomorrow.

Let game repeated with discount factor $\delta \in (0,1)$ — next period's payoff worth $\delta$ times today's. Patience high = $\delta$ close to 1.

Strategies:

- **Grim Trigger:** Cooperate until opponent defects once, then defect forever. Cooperation sustainable if $\delta$ large enough to make one-time temptation $T$ not worth future loss. Condition: $R/(1-\delta) \ge T + \delta P/(1-\delta)$ → $\delta \ge (T-R)/(T-P)$.
  With our numbers $R=-1,P=-5,T=0$: Need $\delta \ge (0-(-1))/(0-(-5))=1/5=0.2$. So if future matters at least 20% as much as present, cooperation possible.
- **Tit-for-Tat:** Start cooperating, then mirror opponent's previous move. Anatol Rapoport's strategy won Axelrod's 1980 tournament — nice, retaliatory, forgiving, clear. It rewards cooperation, punishes defection, but forgives.
- **Tit-for-Two-Tats, Generous Tit-for-Tat, Win-Stay-Lose-Shift:** Variants that handle noise — if opponent defects by mistake, forgiving versions avoid endless retaliation spiral.

**Folk theorem:** With sufficient patience (low discount rate, high $\delta$), nearly any feasible payoff between full defection and full cooperation can be sustained as subgame perfect equilibrium in infinitely repeated game. Formally, for any feasible individually rational payoff profile $v$ with $v_i > P$, exists $\bar{\delta}<1$ such that for all $\delta>\bar{\delta}$, $v$ is SPE.

Implications: Repeated interaction enables social norms, trust, reputation. Institutions that make future interaction likely (communities, long-term contracts) promote cooperation. One-shot anonymous interaction — e.g., one-time online transaction — predicts defection, hence need for enforcement.

---

### Helping a Coworker — Prisoner's Dilemma at Work

You and a coworker are both working on a project that affects both your reputations — presentation to boss, shared OKR. Each can choose:

- **Help** — contribute extra effort, stay late, polish deck
- **Slack** — minimal effort, free-ride

Payoffs represent net benefit = recognition minus effort cost:

|                | **Coworker: Help** | **Coworker: Slack** |
| -------------- | ------------------ | ------------------- |
| **You: Help**  | (3, 3)             | (-1, 4)             |
| **You: Slack** | (4, -1)            | (0, 0)              |

Interpretation:

- **(Help, Help) = (3, 3)**: Both contribute, project succeeds impressively, both get credit minus effort cost. 5 units credit -2 effort =3. Team win.
- **(Help, Slack) = (-1, 4)**: You work hard while they coast; they get credit, you're exhausted. You: 1 credit -2 effort = -1; they: 4 credit -0 effort =4. Sucker's payoff.
- **(Slack, Help) = (4, -1)**: You coast while they work; you get credit without effort — temptation.
- **(Slack, Slack) = (0, 0)**: Project mediocre, no one looks good, minimal effort wasted. Baseline.

This is Prisoner's Dilemma with $T=4 > R=3 > P=0 > S=-1$.

#### Analysis

From your perspective:

- If coworker helps: Slacking gives 4 vs. Helping gives 3 → **Slack is better** by +1 gain — free credit.
- If coworker slacks: Slacking gives 0 vs. Helping gives -1 → **Slack is better** by +1 gain — avoid being sucker.

Slacking strictly dominates Helping. No matter what coworker does, you are +1 better by slacking.

Nash Equilibrium: (Slack, Slack) with payoff **(0,0)** (Binmore 30-32). Neither can improve unilaterally:

$$u_{\text{you}}(\text{Slack}, \text{Slack}) = 0 \geq u_{\text{you}}(\text{Help}, \text{Slack}) = -1$$
$$u_{\text{coworker}}(\text{Slack}, \text{Slack}) = 0 \geq u_{\text{coworker}}(\text{Slack}, \text{Help}) = -1$$

Check: If you are at (0,0) and you deviate to Help, you go to -1 — worse. So Nash.

But mutual helping **(3,3)** is Pareto superior — better for everyone, total welfare 6 vs 0 (Cunningham 24-26). No one wants to move to (3,3) alone because deviator gains 1, but both moving helps both. This creates workplace tension: rational self-interest suggests slacking, but everyone worse off than if they'd cooperated. Classic social dilemma.

Why workplaces feel draining? Because many tasks are PD: documentation, cleaning shared kitchen, mentoring. Each person prefers others do it.

#### Real-World Modifications — How Cooperation Emerges

The $2\times2$ one-shot model misses structure that saves workplaces.

**1. Repeated interaction — Shadow of the Future**

If you work together repeatedly — same team for months — defecting (slacking) now damages future cooperation. Game becomes repeated Prisoner's Dilemma (Resnik 155-160).

Let discount factor $\delta$ = how much you value next week's interaction vs this week's. With Grim Trigger — "I will Help as long as you Help; if you Slack once, I Slack forever" — cooperation sustained if:

$$R + \delta R + \delta^2 R + \dots \ge T + \delta P + \dots$$
$$\frac{3}{1-\delta} \ge 4 + \frac{0}{1-\delta} \implies 3 \ge 4(1-\delta) \implies \delta \ge 0.25$$

If you care at least 25% about future, cooperation rational. In long-term teams $\delta$ high, cooperation emerges naturally. In one-off project with contractor you never see again $\delta\approx0$, slack expected.

Practical strategies people use without naming them:

- **Tit-for-Tat:** Start Help, then copy coworker's last move. "I'll help if they help, but I'm not getting taken advantage of" — exactly computing conditional strategies in implicit repeated game (van Benthem et al. 126-129). Nice, retaliatory, forgiving, clear.
- **Win-Stay-Lose-Shift:** If last outcome (3,3) or (4,-1) good for you, repeat; if (-1,4) or (0,0) bad, switch. Helps recover from errors.

**2. Reputation — Beyond Dyad**

In office environments, your choice affects reputation beyond one coworker. Single-shot payoffs don't capture long-term career costs of being known as slacker (Rubinstein 110-120).

Model: Add third party observers. If you Slack, others update belief about you, reduce future opportunities. Effective payoff of Slack when coworker Helps becomes $4 - r$, where $r$ = reputation cost. If $r>1$, Help becomes dominant. Companies create this intentionally via 360 reviews, public kudos, visibility.

So (Help,Help) can be sustained by indirect reciprocity: "I help you because others watch and will help me later."

**3. Altruism / Reciprocity / Inequality Aversion**

People often have utility functions that value fairness and reciprocity beyond pure self-interest, changing effective payoff matrix (Rubinstein 120-130).

- **Altruism:** $u_i^{\text{eff}} = u_i + \alpha u_j$, $\alpha>0$ care about coworker. If $\alpha>0.33$, effective payoff of (Help,Help) becomes $3+3\alpha >4-\alpha$ of (Slack,Help), so Help dominates.
- **Inequality aversion:** Dislike unfair outcomes: $u_i^{\text{eff}} = u_i - \beta \max(u_j-u_i,0)$. (Slack,Help) gives inequality 5 for sucker, so psychological cost high.
- **Reciprocity:** Utility depends on intentions — being kind to kind person feels good.

Experimentally, in lab PD with payoffs (3,3)/(0,4) etc., ~50% cooperate one-shot, not 0% — because social preferences transform matrix.

**4. Mechanism Design — How Managers Fix PD**

Managers can change game to make (Help,Help) equilibrium:

- **Make contributions observable:** Daily standup, shared commits — increase $r$, turns hidden Slack into visible.
- **Joint accountability + individual accountability:** Split credit by observable contribution, not equal split. Change payoffs from (4,-1) to (2,-1) if slacker gets less credit.
- **Reduce effort cost:** Tools, templates — increase Help payoff from 3 to 4.5.
- **Increase $P$ penalty for mutual slacking:** If project fails, both get -2 not 0, (Slack,Slack) worse than being sucker, transforms game into Stag Hunt with two equilibria, coordination on Help possible.
- **Formal contracts:** If you can contract "if you Slack, you owe me", enforceable commitment changes game.

In one line: Workplace Help game is PD with $T>R>P>S$. One-shot logic says Slack, but repetition, reputation, and social preferences turn it into a repeated game where Tit-for-Tat and observable contribution make Help rational — which is why teams with long horizon and transparency outperform collections of rational slackers.

## Fourier Transform

The continuous Fourier Transform is the ultimate prism: it decomposes a signal into its pure frequencies.

$$\mathcal{F}\{f(t)\} = F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i\omega t} \,dt$$

where $f(t)$ is time-domain signal, $F(\omega)$ is frequency-domain representation — complex amplitude of frequency $\omega$ present in $f$ (Berry 227-230). $e^{-i\omega t} = \cos\omega t - i\sin\omega t$ by Euler, so integral correlates $f$ with sine/cosine at $\omega$.

The inverse transform reconstructs original signal from frequencies:

$$f(t) = \dfrac{1}{2\pi}\int_{-\infty}^{\infty} F(\omega) e^{i\omega t}\,d\omega$$

This bidirectional relationship — Fourier Transform Identity Theorem — guarantees information perfectly preserved in both representations: $f \leftrightarrow F$ is bijection (in $L^1\cap L^2$, extended to $L^2$ by Plancherel). Time domain tells you _when_, frequency domain tells you _what pitch_ (Berry 230-232, 227). Both are same signal.

### Intuition: Eigenfunction Expansion

$e^{i\omega t}$ are eigenfunctions of differentiation $d/dt$ with eigenvalue $i\omega$: $\dfrac{d}{dt}e^{i\omega t}=i\omega e^{i\omega t}$. They are also eigenfunctions of translation and convolution operators. Fourier transform is change of basis to eigenbasis of time-shift invariant linear systems — diagonalizing them. Same story as eigenvectors: $F$ is coordinates of $f$ in eigenbasis $\{e^{i\omega t}\}$.

### Properties — Why Engineers Live In Frequency Domain

Let $F(\omega)=\mathcal{F}\{f\}$, $G=\mathcal{F}\{g\}$.

- **Linearity:** $\mathcal{F}\{af+bg\}=aF+bG$
- **Time shift:** $\mathcal{F}\{f(t-a)\}=e^{-i\omega a}F(\omega)$ — delay = phase rotation
- **Frequency shift:** $\mathcal{F}\{e^{i\omega_0 t}f(t)\}=F(\omega-\omega_0)$ — modulation
- **Scaling:** $\mathcal{F}\{f(at)\}= \dfrac1{|a|}F(\omega/a)$ — compress in time, spread in frequency
- **Differentiation:** $\mathcal{F}\{f'(t)\}=i\omega F(\omega)$ — ODE becomes algebra, like Laplace but for all $t\in\mathbb{R}$
- **Convolution:** $\mathcal{F}\{f*g\}=F(\omega)G(\omega)$, where $(f*g)(t)=\int f(\tau)g(t-\tau)d\tau$. And $\mathcal{F}\{fg\}= \dfrac1{2\pi}F*G$ dual. Filtering is multiplication in frequency.
- **Parseval / Plancherel:** Energy preserved: $\int |f(t)|^2 dt = \dfrac1{2\pi}\int |F(\omega)|^2 d\omega$. Power spectrum $|F|^2$ tells where energy lies.

### Convergence and Uncertainty

Mean convergence theorems ensure Fourier representations converge to original function under broad conditions — e.g., if $f\in L^2$, partial integrals $\int_{-R}^{R} F(\omega)e^{i\omega t}d\omega$ converge in $L^2$ mean to $f$ as $R\to\infty$ (McShane 205-208). Pointwise convergence needs more: Dirichlet conditions piecewise smooth → convergence to midpoint of jump.

The Fourier Transform satisfies remarkable inequalities that constrain how "spread out" a function can be simultaneously in time and frequency domains (Beckner 159-165). These are uncertainty principles, formalized through weighted norm inequalities, with profound implications from quantum mechanics to signal processing (Beckner 175-180; Muckenhoupt 729-735).

- **Heisenberg uncertainty:** Cannot be localized in both time and frequency. For $f$ normalized, define variances $\Delta_t^2, \Delta_\omega^2$. Then $\Delta_t \Delta_\omega \ge 1/2$. Proof uses Cauchy-Schwarz and $\mathcal{F}\{tf(t)\}=iF'(\omega)$. Equality for Gaussian $e^{-t^2/2}$. In quantum mechanics $p=\hbar\omega$, this is $\Delta x \Delta p \ge \hbar/2$.
- **Hardy, Hausdorff-Young, Beckner:** Quantitative bounds: If $|f(t)|\le Ce^{-at^2}$ and $|F(\omega)|\le Ce^{-b\omega^2}$ with $ab>1/4$, then $f=0$. Weighted $L^p$ norms $\|F\|_{q} \le C\|f\|_{p}$ for $1/p+1/q=1$, $1\le p\le2$ — Beckner's sharp constant.
- **Implication:** No signal is both time-limited and band-limited — if $f(t)=0$ outside interval, $F(\omega)$ cannot be 0 outside interval unless $f=0$. This limits perfect filtering.

### Generalizations and Modern Extensions

The transform extends beyond real and complex numbers to quaternions and higher algebraic structures, enabling analysis of multidimensional rotations and color image processing (Gao 9851-9860).

- **Discrete Time Fourier Transform (DTFT):** $f$ discrete, $F(\omega)=\sum f[n]e^{-i\omega n}$, periodic in $\omega$.[n]
- **Discrete Fourier Transform (DFT):** Both discrete, length $N$: $F[k]=\sum_{n=0}^{N-1} f[n]e^{-i2\pi kn/N}$. Computable via FFT $O(N\log N)$ — basis of digital signal processing.
- **Fourier Series:** Periodic $f(t+T)=f(t)$ → discrete frequencies $F_n=\dfrac1T\int_0^T f(t)e^{-i n\omega_0 t}dt$, $f=\sum F_n e^{i n\omega_0 t}$ — our guitar string eigenfunctions.
- **$n$-D Fourier:** $F(\omega_1,\omega_2)=\iint f(x,y)e^{-i(\omega_1x+\omega_2y)}dxdy$ — image processing, low-pass blur = keep low $\omega$, high-pass edge detection = keep high $\omega$.
- **Quaternion Fourier Transform:** For $f: \mathbb{R}^2\to\mathbb{H}$ quaternion-valued, allows processing color (RGB as i,j,k) while preserving cross-channel correlation — used in color image filtering, flow analysis. Noncommutative: left vs right transform differ.
- **Short-Time Fourier Transform (STFT) / Gabor:** To get time _and_ frequency, window $f(t)g(t-\tau)$ then Fourier in $t$: spectrogram $|STFT(\tau,\omega)|^2$ — what you see in music apps. Tradeoff governed by uncertainty.
- **Fractional Fourier, Wavelet:** Intermediate bases.

### Examples and Applications

#### Input Signals — Time Domain Hides What Frequency Domain Shows

**Pure tone:** Input signal $f(t)=\cos(\omega_0 t)$: mathematically simple, infinitely long cosine. Its Fourier Transform:
$$F(\omega)=\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]$$
— two spikes at $\pm\omega_0$ (Dirac deltas). Negative frequency appears because $\cos\omega_0t=(e^{i\omega_0t}+e^{-i\omega_0t})/2$ — needs both. Real signals have Hermitian symmetry $F(-\omega)=F^*(\omega)$.

**Noisy signal:** Real world $y(t)=f(t)+n(t)$ where $f$ desired signal band-limited to $|\omega|<\omega_c$, $n(t)$ high-frequency noise. In time domain $y(t)$ looks messy — signal buried. In frequency domain:

$$Y(\omega)=F(\omega)+N(\omega)$$

$F$ concentrated near $\pm\omega_0$, $N$ spread at high $|\omega|$. They separate. Filtering: multiply $Y(\omega)$ by ideal low-pass $H(\omega)=1$ for $|\omega|<\omega_{cut}$, $0$ otherwise, then inverse transform $y_{filtered}(t)=\dfrac1{2\pi}\int H(\omega)Y(\omega)e^{i\omega t}d\omega$ to recover clean signal. This is exactly how:

- **Noise cancellation:** Mic captures $S(t)+Noise(t)$, adaptive filter estimates $Noise$ spectrum, subtracts in frequency domain.
- **MRI reconstruction:** MRI scanner samples k-space which _is_ Fourier domain: $k_x,k_y$ correspond to spatial frequencies. Inverse 2D Fourier $\mathcal{F}^{-1}\{K(k_x,k_y)\}$ = image $I(x,y)$. Undersample k-space = blurry image.
- **MP3/AAC compression:** Human ear masks quiet frequencies near loud ones — psychoacoustic model keeps perceptually important $F(\omega)$ bins, discards 90% of coefficients. File size drops 10x, sounds same because discarded information inaudible. JPEG does same in 2D with DCT, a real version of Fourier.

In one line: Fourier transform is rotation of basis to eigenvectors of translation — turning convolution into multiplication, differentiation into scaling, and revealing hidden harmonic content that time domain obscures, at cost of Heisenberg tradeoff that you cannot be sharp in both domains.

#### Piano Chords — Hearing Eigenmodes

When you play a single note, say middle A at 440 Hz (A4), ideal sound wave — ignoring decay — can be approximated as:
$$A(t)=\sin(2\pi\cdot440\cdot t)$$

Pure sine sounds artificial, like tuning fork or synthesizer with no harmonics — not like piano.

When you play a chord — say A-major triad with notes A4 (440 Hz), C#5 (554.37 Hz), and E5 (659.25 Hz) — time domain waveform looks like messy wobble:

$$S(t)=A_1\sin(2\pi\cdot440t)+A_2\sin(2\pi\cdot554t)+A_3\sin(2\pi\cdot659t)$$

where $A_1,A_2,A_3$ amplitudes (loudness) of each note, dependent on velocity of keypress. Graph $S(t)$ vs $t$ shows beating, interference — you cannot read frequencies by eye.

Fourier Transform decomposes composite wave:

$$\mathcal{F}\{S(t)\}=F(\omega)$$

producing frequency spectrum with three distinct peaks at 440 Hz, 554 Hz, and 659 Hz, with heights proportional to $A_1,A_2,A_3$ (Alm and Walker 461-465). Technically, $\mathcal{F}\{\sin\omega_0t\}= i\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$, imaginary spikes. Magnitude $|F(\omega)|$ shows peaks.

This decomposition reveals exactly which notes present and relative volumes — information that exists in composite waveform but invisible in time domain. This is what Shazam does: computes spectrogram of audio, peaks correspond to chord notes, matches fingerprint to database.

#### Real Instruments: Harmonic Series Defines Timbre

Real instruments far more complex. A piano string doesn't produce pure sine wave; fixed ends quantize allowed modes, as in Eigenvalue section. It generates overtones — harmonics — at integer multiples of fundamental frequency: $f_n=n f_1$: 440 Hz, 880 Hz, 1320 Hz, 1760 Hz, etc. (Alm and Walker 465-470).

Fourier series of periodic piano A:

$$\text{Piano A}(t)=\sum_{n=1}^{\infty} a_n \sin(2\pi\cdot n\cdot440\cdot t + \phi_n)$$

where coefficients $a_n$ decrease with $n$, roughly $a_n\sim1/n$ for plucked/string with some envelope, and $\phi_n$ phases. For ideal string plucked at center, even $a_n=0$.

The unique pattern of these overtones — relative strengths $a_n$ — defines instrument's timbre (Alm and Walker 471-473).

- **Piano:** $a_n$ decays slowly, many harmonics, plus inharmonicity due to string stiffness: actual partials slightly sharp $f_n = n f_1\sqrt{1+Bn^2}$, $B\sim10^{-4}$, gives piano its bright, slightly out-of-tune shimmer.
- **Violin:** Sawtooth-like bowing excites strong higher harmonics, $a_n\sim1/n$, very rich — why violin sounds bright, cutting. Body resonances filter $a_n$ further, formants.
- **Flute:** Near pure sine, $a_1$ dominant, $a_{n>1}$ tiny — hollow, pure.
- **Clarinet:** Closed-open pipe, only odd harmonics $n=1,3,5,\dots$ — hence hollow quality.

A violin playing same note A4 has different pattern $a_n$ values, which is why it sounds distinct from piano despite same fundamental $f_1$. Your ear does Fourier transform mechanically: cochlea is frequency analyzer — basilar membrane different positions resonate at different $\omega$, hair cells send $ |F(\omega)|$ to brain. You _hear_ Fourier transform.

**Chord with harmonics:** A-major chord on real piano:

$$S_{\text{real}}(t)=\sum_{n=1}^\infty a_n^{(A)}\sin(2\pi n440t)+\sum_{m=1}^\infty a_m^{(C\#)}\sin(2\pi m554t)+\sum_{k=1}^\infty a_k^{(E)}\sin(2\pi k659t)$$

Spectrum $|F(\omega)|$ now shows clusters: peaks at 440, 554, 659 and each has harmonic comb at multiples. Some harmonics overlap nearly — e.g., 3rd harmonic of A =1320 Hz near 2nd harmonic of E=1318.5 Hz — they beat, creating richness and consonance/dissonance perception. Consonant chords have many overlapping harmonic partials aligning; dissonant chords have partials clashing within critical band ~15% of frequency.

Thus playing piano is physically adding eigenvectors of wave operator, and listening is computing their Fourier coefficients — your auditory system performing spectral decomposition to infer which keys pressed and which instrument played.
