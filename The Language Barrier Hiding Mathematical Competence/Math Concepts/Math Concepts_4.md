## Gauss's Theorema Egregium — Curvature Without Outside

Gauss called it _Theorema Egregium_ — Latin for "Remarkable Theorem" — in his 1827 _Disquisitiones generales circa superficies curvas_. It created differential geometry as an intrinsic science.

Before Gauss, surfaces were studied as sitting in $\mathbb{R}^3$. After Gauss, you could study a surface as a world in itself.

### Statement

> **Theorema Egregium:** Gaussian curvature $K$ is invariant under local isometry. It depends only on the First Fundamental Form $I$, not on Second Fundamental Form $II$.

Formal: If $f: S \to S'$ is a local isometry — diffeomorphism preserving $I$, i.e.,

$$I_p(v,w) = I'_{f(p)}(df_p(v), df_p(w)) \quad \forall p, v,w \in T_pS$$

equivalently $f$ preserves lengths of all curves — then

$$K(p) = K'(f(p))$$

> If you can bend, roll, but not stretch, tear, or squish one surface into another, they have same $K$ at corresponding points. $K$ doesn't change when you bend without stretching.

Definition $K = \kappa_1\kappa_2 = (LN-M^2)/(EG-F^2)$ _looks_ extrinsic — uses normal $N$, second fundamental form $II = L,M,N$. Egregium says this ratio actually depends only on $E,F,G$ and derivatives: $E,F,G$ give $K$ via Brioschi formula, which uses only Christoffel symbols $\Gamma_{ij}^k$ computed from $E,F,G$.

So $K$ is _extrinsically defined but intrinsically determined_. That's why remarkable.

**Intrinsic meaning:** Ant with ruler and protractor can compute $K$, without seeing $\mathbb{R}^3$.

### Why Definition Looks Extrinsic But Is Intrinsic

We have:

- $I = E du^2 + 2F du dv + G dv^2$ — intrinsic — ant can measure with ruler.
- $II = L du^2 + 2M du dv + N dv^2$ — extrinsic — needs normal $N$, how surface tips in $\mathbb{R}^3$.

Then $K = \det II / \det I$ seems to need $II$.

Gauss's calculation: Compute $\Gamma_{ij}^k$ from $E,F,G$:
$$\Gamma = \dfrac12 I^{-1} \partial I$$

Then Riemann curvature of $I$ as abstract metric: $K = -\dfrac1{\sqrt{EG}} \left[ \partial_u \dfrac{(\sqrt{G})_u}{\sqrt{E}} + ... \right]$ for orthogonal coordinates. Only $E,F,G$.

So $\det II / \det I$ collapses to expression in $E,F,G$ only. Individual $\kappa_1,\kappa_2$ remain extrinsic, product becomes intrinsic.

> **Analogy:** Suppose $\kappa_1 = a$, $\kappa_2 = b$. Each individually changes when you bend, but product $ab$ stays same. Like rolling paper: $\kappa_1$ $0\to1/R$, $\kappa_2$ $0\to0$, product $0$ stays $0$.

### Consequences — What Egregium Tells Us

**1. Plane $\not\cong$ Sphere — No perfect map**

$K_{\text{plane}}=0$, $K_{\text{sphere}}=1/R^2>0$.

If there were local isometry $f: \text{plane} \to \text{sphere}$ preserving distances, Egregium would force $0=1/R^2$, impossible.

> You cannot flatten a sphere onto plane without stretching. Any world map must distort — either distances, angles, or areas. That's why Mercator distorts Greenland, equal-area distorts shapes.

No amount of clever cutting (without stretching) can fix it — $K$ mismatch is intrinsic obstruction, like $W\neq B$ for dominoes. Same spirit as Gomory: global count controls possibility.

**2. Plane $\cong$ Cylinder — They are intrinsically same**

$K_{\text{plane}}=0$, $K_{\text{cylinder}}=0$.

And indeed isometry exists:
$$f(u,v) = (R\cos(u/R), R\sin(u/R), v)$$
$du^2+dv^2$ → $R^2 (du/R)^2 + dv^2$ with $dx^2+dy^2+dz^2$? Compute: $df = (-\sin(u/R) du, \cos(u/R) du, dv)$, so $|df|^2 = du^2+dv^2$. Preserves lengths.

> Ant on cylinder cannot tell it's not on plane. Unroll cylinder — distances preserved. Paper rolled into tube is intrinsically flat. That's why $K=0$ even though extrinsically looks curved.

**3. Catenoid $\cong$ Helicoid — Famous isometric deformation**

Catenoid: soap film between two parallel rings, shape $r(v)\cosh$, $K<0$.
Helicoid: spiral ramp, like parking garage, $K<0$.

They look completely different extrinsically — one like tunnel, one like spiral — but there is a continuous family of isometries (Bonnet family) bending catenoid into helicoid, preserving $I$, so $K$ preserved pointwise. Mean curvature $H$ changes — $H=0$ for both (both minimal), but principal curvatures swap.

Shows intrinsic vs extrinsic vividly: intrinsic geometry same, extrinsic shape different.

**4. $K$ is detectable internally — Ant experiments**

Because $K$ intrinsic, ant can measure it.

- Angle defect: $\alpha+\beta+\gamma = \pi + \iint_{\triangle} K dA$. For small triangle, $K \approx (\text{sum}-\pi)/A$.

- Circumference defect: $C(r)=2\pi r - \pi K r^3/3 + O(r^5)$. So $K \approx 3(2\pi r - C)/(\pi r^3)$.

Gauss as geodesist measured Hanover triangle Hoher Hagen-Brocken-Inselberg to see if space curved. He knew Egregium means surveying reveals curvature.

### Distinction $K$ vs $H$ — The Takeaway

- **Mean curvature $H=(\kappa_1+\kappa_2)/2$** — extrinsic. Tells how surface bends _in_ space. Cylinder $H=1/(2R)$ vs plane $H=0$, so bird distinguishes. Minimal surfaces $H=0$.

- **Gaussian curvature $K=\kappa_1\kappa_2$** — intrinsic. Tells whether internal geometry is Euclidean. Cylinder and plane both $K=0$ — ant thinks both Euclidean. Sphere $K>0$ — ant finds non-Euclidean.

> **Final slogan:** $H$ — how surface looks from outside. $K$ — how surface feels from inside. Egregium says inside feeling ($K$) is preserved when you bend without stretching, even though outside look ($H$) changes. You can't turn plane into sphere without stretching, but you can turn plane into cylinder.

Same philosophy as Gomory: trivial obstruction ($W=B$ or $K$ mismatch) is sometimes the only obstruction — plane vs cylinder passes $K$ test and indeed is isometric; plane vs sphere fails $K$ test and no isometry exists.

### What is Gaussian Curvature?

This is how we measure how curved a surface is _at a point_, using only two numbers.

#### Principal Curvatures — The Two Bends

Take a surface in $\mathbb{R}^3$ — like a sheet of paper bent in space. At a point $p$, look at all planes that contain the normal vector (the vector sticking straight out of surface). Each such plane cuts the surface in a curve. That curve has a curvature — how sharply it bends at $p$.

As you rotate that cutting plane around the normal, the curvature of the slice varies. It will have a maximum $\kappa_1$ and a minimum $\kappa_2$, achieved in orthogonal directions. These are the **principal curvatures**.

> Stand on the surface. Look north-south — how much does ground bend up/down? Look east-west — how much does it bend? Those two extreme bends are $\kappa_1, \kappa_2$. Every other direction's bend is in between.

Convention: $\kappa = 1/R$ where $R$ is radius of best-fitting circle (osculating circle). Positive if bending towards normal, negative away.

**Examples:**

- **Plane:** Slice any direction — straight line. $\kappa_1 = 0, \kappa_2 = 0$.
- **Cylinder radius $R$:** Around the tube, cross-section is circle radius $R$, so $\kappa_1 = 1/R$. Along the length, cross-section is straight line, $\kappa_2 = 0$.
- **Sphere radius $R$:** All directions same — great circle radius $R$. $\kappa_1 = \kappa_2 = 1/R$.
- **Saddle $z = x^2 - y^2$:** In $x$-direction bends up, $\kappa_1 >0$, in $y$-direction bends down, $\kappa_2 <0$.

#### Gaussian Curvature — The Product

Define:

$$K = \kappa_1 \cdot \kappa_2$$

Why product? Because it captures something independent of how you oriented your $x,y$ axes, and it captures the _type_ of curvature.

- **Plane:** $K = 0 \cdot 0 = 0$ — flat.
- **Cylinder:** $K = (1/R) \cdot 0 = 0$ — flat in at least one direction. You can unroll a cylinder onto a plane without stretching.
- **Sphere radius $R$:** $K = (1/R)\cdot(1/R) = 1/R^2 > 0$ — positively curved. Bends same way both directions, like a bowl.
- **Saddle / Pringles chip / Pseudosphere:** $\kappa_1 = a$, $\kappa_2 = -b$, so $K = -ab < 0$ — negatively curved. Bends opposite ways, like a mountain pass.

> **Intuition:**
>
> - $K>0$ = elliptic point — locally like sphere, both bends same side. Triangles have angle sum $>180^{\circ}$.
> - $K=0$ = parabolic point — locally like cylinder or plane, at least one flat direction. Triangles sum $=180^{\circ}$ if you can flatten.
> - $K<0$ = hyperbolic point — saddle, bends opposite. Triangles sum $<180^{\circ}$.

#### The Theorema Egregium — Ant vs Bird

Now the deep part. There are two ways to think about shape:

**Extrinsic — bird's-eye view:** You are outside the surface in $\mathbb{R}^3$, looking at how it bends in space. Principal curvatures $\kappa_1,\kappa_2$ are extrinsic — they depend on how surface sits in space. A cylinder looks curved to a bird.

**Intrinsic — ant's view:** You are an ant living _on_ the surface, with no concept of outside space. What can you measure?

- Distances along surface (geodesics)
- Angles of triangles drawn on surface
- Areas of small circles: on plane, circumference $=2\pi r$, on sphere $<2\pi r$, on saddle $>2\pi r$
- Whether you can flatten without stretching

These are intrinsic — they depend only on measurements within surface, on the **first fundamental form** $I = E du^2 + 2F du dv + G dv^2$, which is the ruler the ant carries.

**Theorema Egregium (Gauss, 1827) — Remarkable Theorem:**

> $K = \kappa_1 \kappa_2$ is **intrinsic**. It can be computed from only $E,F,G$ and derivatives, without ever knowing how surface sits in $\mathbb{R}^3$.

In formulas: $K$ depends on second derivatives of $E,F,G$, but not on second fundamental form $II$.

> The product $\kappa_1 \kappa_2$ looks like it needs outside view (needs both principal bends), but miraculously the product itself can be known by ant that never leaves surface. The individual $\kappa_1,\kappa_2$ are extrinsic, but their product is intrinsic.

**Why amazing?**

Take a sheet of paper — $K=0$. Roll it into a cylinder — as bird, you see $\kappa_1=1/R$ now, but ant still measures same distances, same angles, circumference of small circle still $2\pi r$. Ant cannot tell it's been rolled! $K$ stayed $0 = (1/R)*0$ — product unchanged.

You cannot roll paper into sphere without stretching/crumpling — because plane $K=0$ cannot become sphere $K=\dfrac{1}{R^2}>0$ via intrinsic isometry (bending without stretching). Ant would notice: triangles now have angle sum $>180^{\circ}$, circles smaller.

So:

- Cylinder is intrinsically flat — $K=0$ same as plane, even though extrinsically curved. Ant thinks it's plane.
- Sphere is intrinsically curved — $K>0$, ant can prove it's not plane by drawing a large triangle and measuring $>180^{\circ}$.
- Saddle is intrinsically negatively curved — ant finds $C>2\pi r$.

**Ant vs Bird summary:**

|            | Bird sees        | Ant measures                                       | $K$                |
| :--------- | :--------------- | :------------------------------------------------- | :----------------- |
| Plane      | Flat             | $C=2 \pi r$, angles $180^{\circ}$                  | 0                  |
| Cylinder   | Curved around    | Same as plane — can unroll                         | 0                  |
| Sphere $R$ | Curved both ways | $C<2\pi r$, angles $>180^{\circ}$, area $<\pi r^2$ | $\dfrac{1}{R^2}>0$ |
| Saddle     | Curved opposite  | $C>2\pi r$, angles $<180^{\circ}$                  | $<0$               |

The Theorema Egregium is why Gaussian curvature is so central: it's the bridge between outside shape and inside geometry. And it leads to Gauss-Bonnet theorem: $\int_M K dA = 2\pi \chi(M)$ — total curvature (intrinsic) equals Euler characteristic (topology). Same spirit as Gomory: global count controls geometry.

**One sentence:** At each point, multiply the two extreme bends; the sign tells you if you're on hill ($+$), valley tube ($0$), or pass ($-$), and miraculously an ant can compute this product without ever leaving the surface.

### The Extrinsic View

The extrinsic view is the bird's-eye view: you are outside the surface, in $\mathbb{R}^3$, watching how it sits in space.

#### Setup

Take a smooth surface $S \subset \mathbb{R}^3$, say parametrized $r(u,v)$. At point $p = r(u_0,v_0)$:

- Tangent plane $T_p S$ = all directions you can walk staying on surface to first order. Spanned by $r_u, r_v$.
- Unit normal $N(p) = \dfrac{r_u \times r_v}{\|r_u \times r_v\|}$ — the arrow sticking straight out, perpendicular to tangent plane.

> If you're standing on surface, tangent plane is the flat ground under your feet, normal is "up" in 3D space.

#### Slicing by Normal Planes — Where Principal Curvatures Come From

Take a plane $\Pi_\theta$ that contains $N(p)$ and makes angle $\theta$ in tangent plane. Intersect $\Pi_\theta$ with $S$. You get a planar curve $\gamma_\theta$ through $p$.

That curve has curvature at $p$ — how sharply it bends in that normal plane. Call it normal curvature $\kappa_n(\theta)$.

Now rotate $\theta$ from $0$ to $\pi$. $\kappa_n(\theta)$ varies. Euler proved:

$$\kappa_n(\theta) = \kappa_1 \cos^2\theta + \kappa_2 \sin^2\theta$$

where $\kappa_1$ = maximum value, $\kappa_2$ = minimum value, achieved in orthogonal directions.

> **Intuition:** Slice a cylinder vertically — you get straight line, curvature 0. Slice around — circle, curvature $1/R$. Intermediate angle — ellipse, curvature between. Max and min are orthogonal.

These $\kappa_1,\kappa_2$ are **principal curvatures**. They are extrinsic — they measure how surface bends away from its tangent plane in ambient $\mathbb{R}^3$.

#### How We Compute Them — Second Fundamental Form

To measure bending, we need to know how normal $N$ tips as you move.

First fundamental form $I = E du^2 + 2F du dv + G dv^2$ is intrinsic — measures lengths on surface: $E = \langle r_u,r_u\rangle$, $F=\langle r_u,r_v\rangle$, $G=\langle r_v,r_v\rangle$. Ant can measure $I$ with ruler on surface.

Second fundamental form $II = L du^2 + 2M du dv + N dv^2$ is extrinsic — measures how $r$ bends away from tangent plane into normal direction:

$$L = \langle r_{uu}, \mathbf{N}\rangle,\quad M = \langle r_{uv}, \mathbf{N}\rangle,\quad N = \langle r_{vv}, \mathbf{N}\rangle$$

> $r_{uu}$ is how $r_u$ changes as you move in $u$. Its component along $\mathbf{N}$ tells you if surface is curving up out of tangent plane. $II$ collects all that.

If $II=0$ everywhere, surface is plane — never leaves tangent plane.

Principal curvatures are eigenvalues of shape operator $S = I^{-1} II$ — the map that sends tangent vector $v$ to $-dN(v)$, rate of change of normal.

In matrix terms:

$$S = \begin{pmatrix} E & F \\[10pt] F & G \end{pmatrix}^{-1} \begin{pmatrix} L & M \\[10pt] M & N \end{pmatrix}$$

Eigenvalues = $\kappa_1,\kappa_2$.

Then:

$$K = \kappa_1 \cdot \kappa_2 = \dfrac{LN - M^2}{EG - F^2} = \dfrac{\det II}{\det I}$$

and

$$H = \dfrac{\kappa_1+\kappa_2}{2} = \dfrac{EN + GL -2FM}{2(EG-F^2)}$$

means curvature.

> Both $K$ and $H$ formulas use $II$, which uses $N$, which needs ambient $\mathbb{R}^3$. So they _look_ extrinsic.

#### Examples Computed Extrinsically

- **Plane $r(u,v)=(u,v,0)$:** $N=(0,0,1)$, $r_{uu}=0$, so $L=M=N=0$, $II=0$, $\kappa_1=\kappa_2=0$, $K=0$, $H=0$.

- **Cylinder radius $R$:** $r(u,v)=(R\cos u, R\sin u, v)$. $N=(\cos u,\sin u,0)$ pointing out. $r_{uu}=(-R\cos u,-R\sin u,0)=-R N$ along normal, $r_{vv}=0$. So $L = \langle r_{uu},N\rangle = -R? Actually with inward normal sign... magnitude $|L|=R$? After normalization $E=R^2$, $G=1$, $\det I=R^2$, $\det II=0$, so $K=0$. Principal: $\kappa_1 = 1/R$ around, $\kappa_2=0$ along axis. Extrinsically curved, $H=1/(2R)\neq0$.

- **Sphere radius $R$:** $r(u,v)=R(\sin v\cos u, \sin v\sin u, \cos v)$. $N = r/R$ outward. All second derivatives have component $ -r$... You get $II = (1/R) I$, so $L=E/R$, etc. $\kappa_1=\kappa_2=1/R$, $K=1/R^2$, $H=1/R$.

- **Saddle $z=x^2-y^2$:** $r(x,y)=(x,y,x^2-y^2)$. At origin, $N=(0,0,1)$, $r_{xx}=(0,0,2)$, $r_{yy}=(0,0,-2)$, $r_{xy}=0$. So $L=2, N=-2, M=0$, $E=G=1,F=0$. So $K = (2)(-2)-0 /1 = -4$, $\kappa_1=2,\kappa_2=-2$, $H=0$ — minimal surface at origin but negatively curved.

#### Extrinsic Properties — What Changes When You Bend Without Stretching

Extrinsic properties depend on $N$, i.e., how surface sits in $\mathbb{R}^3$.

- **Mean curvature $H = (\kappa_1+\kappa_2)/2$** — extrinsic. Soap films minimize area → $H=0$ minimal surfaces. Catenoid, helicoid have $H=0$ but $K<0$. Cylinder has $H=1/(2R)\neq0$.
- **Principal curvatures individually** — extrinsic. Roll paper: $\kappa_1$ goes $0\to1/R$.
- **Second fundamental form $II$** — extrinsic.

> **Key thought experiment:** Take a sheet of paper, flat: $\kappa_1=\kappa_2=0$. Roll into cylinder radius $R$ without stretching — distances on paper preserved. Extrinsically, $\kappa_1$ becomes $1/R$, $\kappa_2$ stays $0$, $H$ becomes $1/(2R)$. An outside observer says "now curved!"
>
> But product $K=(1/R)*0=0$ stayed 0. Ant living on paper measuring distances sees no change.

This suggests $K$, although defined as product of extrinsic $\kappa_i$, might have intrinsic nature. That's the surprise Gauss proved: $K$ can be expressed using only $E,F,G$ and their derivatives, no $L,M,N$.

So extrinsic view gives definition $K=\kappa_1\kappa_2$ using $N$ and $II$, seems to need outside. Intrinsic view will show product itself doesn't.

### Intrinsic Geometry — The View From Inside

Intrinsic properties can be measured by a resident of the surface using only a ruler, protractor, and the ability to walk along the surface. No concept of "outside" or "normal" is needed.

A 2D being can measure:

- **Distance:** Length of shortest path (geodesic) between points.
- **Angle:** Angle between two geodesics.
- **Area:** Area of geodesic triangles.

These are encoded in the **first fundamental form**. No normal needed.

$$I = ds^2 = E\,du^2 + 2F\,du\,dv + G\,dv^2$$

where $E=\langle r_u,r_u\rangle$, $F=\langle r_u,r_v\rangle$, $G=\langle r_v,r_v\rangle$. $I$ tells you:

- **length of any curve on the surface**: $\int \sqrt{E(u')^2+2F u'v'+G(v')^2}\,dt$
- **angle between two curves**: $\cos\theta = \dfrac{F}{\sqrt{EG}}$ in orthogonal coordinates
- **area**: $\iint \sqrt{EG-F^2}\,du\,dv$
- **geodesics**: the "straight lines" of the surface — locally shortest paths — defined via Christoffel symbols $\Gamma^k_{ij}$ which are built from $E,F,G$ alone
- parallel transport, covariant derivative, and holonomy — all intrinsic

Gauss proved $K$ can be computed from $E,F,G$ and their derivatives alone.

**Modern formula — Brioschi formula:** If $E,F,G$ are metric coefficients,

$$K = \dfrac{1}{(EG-F^2)^2} \left( \text{det of derivatives of }E,F,G \right)$$

In isothermal coordinates where $I = e^{2u}(dx^2+dy^2)$,

$$K = -e^{-2u}\Delta u$$

where $\Delta$ is Laplacian in $x,y$. No second fundamental form.

What Gauss proved is shocking: Gaussian curvature $K = \kappa_1\kappa_2$, which is defined as a product of extrinsic quantities, is itself intrinsic.

Consequence: If you have an isometry — a map preserving $E,F,G$, i.e., bending without stretching — $K$ is preserved.

### Intrinsic Measurement of $K$ — How a 2D Being Discovers Curvature

How would a resident of the surface, with no concept of 3D space, no normal vector $N$, measure $K$? This is Gauss's great insight: $K$ can be found by surveying _on_ the surface.

Think of ant with a ruler, a piece of string, and a protractor, all constrained to lie on surface. No bird's-eye view.

#### Two Intrinsic Experiments

**A. Circumference of a small geodesic circle:**

Pick point $p$. For small $r$, walk $r$ meters in every direction along shortest paths — geodesics. You trace a curve: set of points at intrinsic distance $r$ from $p$. That's a geodesic circle.

Now measure its circumference $C(r)$ with string _on_ surface.

Euclidean plane predicts $C(r)=2\pi r$ exactly.

Gauss (Bertrand-Puiseux, 1848 refining Gauss) expansion:

$$C(r) = 2\pi r \left(1 - \dfrac{K(p)}{6}r^2 + O(r^4)\right)$$

> Compare measured circumference to $2\pi r$.
>
> - If $C(r) < 2\pi r$, you have less room than flat — surface bulges like sphere. $K>0$.
> - If $C(r) > 2\pi r$, you have more room — saddle, more circumference than expected. $K<0$.
> - If $C(r)=2\pi r$ up to cubic error, $K=0$ — flat.

- On Earth (sphere radius $R=6371$ km), $K=1/R^2$. Circle radius $r=1000$ km has $C = 2\pi r (1 - r^2/(6R^2)+...) \approx 2\pi*1000*(1-0.0041) = 2\pi*1000 - 26$ km short. Measurable!

- On cylinder: unroll it, distances preserved, so $C(r)=2\pi r$ exactly for small $r$ not wrapping around. Ant thinks flat — $K=0$.

- On saddle $z=x^2-y^2$: near origin $K=-4$, so $C(r)=2\pi r(1+4r^2/6)=2\pi r + ...$ larger than Euclidean.

Area of disk $D(r)$: $A(r)=\pi r^2 (1 - K r^2/12 + O(r^4))$ — same test with area.

**B. Angle sum of a small geodesic triangle — Gauss's favorite:**

Take three points close to $p$, connect by geodesics (shortest paths on surface). Measure interior angles $\alpha,\beta,\gamma$ with protractor lying on surface, and area $A$ of triangle.

Gauss-Bonnet for small triangle:

$$\alpha + \beta + \gamma = \pi + \iint_{\triangle} K\,dA \approx \pi + K(p)A$$

> Add up angles of triangle. In flat plane sum = $180^{\circ} = \pi$. Deviation from $180^{\circ}$ divided by area = curvature.

- **Plane / Cylinder:** Geodesics are straight lines (or helices that unroll to straight lines). Triangle sum = $\pi$ exactly → $K=0$.

- **Sphere radius $R$:** $K=1/R^2$ constant. Triangle with one vertex at North Pole, two on equator $90^{\circ}$ apart: each angle $90^{\circ}$, sum $=270^{\circ} = 3\pi/2$. Area = $1/8$ sphere = $\pi R^2/2$. Check: $\pi + A/R^2 = \pi + \pi/2 =3\pi/2$ works.

- **Saddle $K<0$:** Sum $<\pi$. Pringles chip triangle looks skinny.

So ant can detect curvature by surveying!

This is exactly what Gauss attempted as geodesist. 1821-1825 he surveyed Kingdom of Hanover. He measured large triangle between mountain tops Hoher Hagen, Brocken, Inselberg ~ 200 km sides, with theodolites, to see if angle sum exceeded $\pi$ due to Earth's curvature or even space curvature. He found sum $180^{\circ}0'14.86''$ — $14.86''$ excess, but within error, mostly due to Earth curvature. Legend says he tried to test if physical space curved.

#### How Can An Ant Measure $K$ Intrinsically? — Three Practical Methods

**1. Angle defect method — most intuitive:**

$$K(p) \approx \dfrac{(\alpha+\beta+\gamma)-\pi}{\text{Area}(\triangle)}$$

Procedure for ant:

1. Pick small triangle ~ side $r$.
2. Lay strings along geodesics (stretch string tight on surface).
3. Measure angles where strings meet (with protractor on surface).
4. Measure area (count tiny squares).
5. Compute defect.

If defect positive → $K>0$, negative → $K<0$, zero → $K=0$.

Cylinder ant: Triangle drawn on cylinder, when unrolled is Euclidean triangle, sum $180^{\circ}$, so $K=0$.

**2. Circumference defect method — string method:**

$$C(r)=2\pi r -\dfrac{\pi}{3}K r^3 + O(r^5)$$

Procedure:

1. Hammer nail at $p$, tie string length $r$, walk around keeping string taut on surface, mark endpoint locus — geodesic circle.
2. Measure circumference $C(r)$ with another string along locus.
3. Compute $K \approx \dfrac{3}{\pi r^3}(2\pi r - C(r))$.

No angles needed, just lengths.

**3. Gauss-Bonnet general — for larger regions:**

For region $D$ with boundary $\partial D$:

$$\iint_D K\,dA + \int_{\partial D} k_g ds = 2\pi \chi(D)$$

$k_g$ = geodesic curvature of boundary — how much boundary bends _within_ surface. $\chi(D)$ = Euler characteristic — topology (1 for disk).

For geodesic triangle, $k_g=0$ on edges, $\int k_g$ concentrates at vertices as $\pi-\alpha$ etc., giving $\alpha+\beta+\gamma = \pi + \iint K$.

For ant, this means: if you can measure total curvature over region by measuring boundary turning, you get topology.

> **Unified picture:** Intrinsic curvature $K$ manifests as "excess" or "defect" compared to Euclidean expectations. Less circumference/area than Euclidean or more angle sum → positive $K$. More circumference or less angle sum → negative $K$. Exactly Euclidean → zero.

That's why Theorema Egregium is remarkable: $K$ defined extrinsically as $\kappa_1\kappa_2$ using normal $N$, but ant can compute same number using only ruler and protractor on surface, via $C(r)$ or angle sum. Extrinsic definition, intrinsic meaning.

### Why It Is Remarkable: Cylinder vs Sphere

The heart of Egregium is this: **looks curved $\neq$ is curved.**

#### The Physical Intuition — Bending Without Stretching

Take a sheet of paper. Coordinates $(u,v)$ on paper, intrinsic metric:

$$ds^2 = du^2 + dv^2$$

Measure distance between two ink dots by laying string on paper.

Now roll it into cylinder radius $R$:

$$r(u,v) = (R\cos(u/R), R\sin(u/R), v)$$

Compute:

$$r_u = (-\sin(u/R), \cos(u/R), 0),\quad r_v = (0,0,1)$$
$$E=\langle r_u,r_u\rangle =1,\quad F=0,\quad G=1$$

So $ds^2 = du^2+dv^2$ — _exactly same_ as flat sheet. Map $(u,v)\mapsto r(u,v)$ is a **local isometry** — preserves $E,F,G$, preserves all curve lengths.

By Theorema Egregium, $K$ must be preserved. $K_{\text{plane}}=0$, so $K_{\text{cylinder}}=0$.

> Ant on paper walks $1$ cm north, $1$ cm east, makes right angle, measures hypotenuse $\sqrt2$ cm. Roll paper into cylinder, ant does same walk on cylinder — still $\sqrt2$ cm, still right angle. Ant cannot tell it was rolled. So cylinder is intrinsically flat.

Yet bird sees cylinder curved: $\kappa_1=1/R$ around, $\kappa_2=0$ along. Product $K=\kappa_1\kappa_2=0$.

Bending created extrinsic curvature $\kappa_1$, but to keep $ds^2$ same, other direction forced to stay straight, so product stays zero.

Now try to bend paper into sphere radius $R$. Could you?

Assume you could isometrically, preserving $ds^2$. Then $K$ must stay $0$. But sphere has $K=1/R^2>0$. Contradiction.

> **Therefore you cannot wrap a sphere with paper without stretching, tearing, or crumpling.** This is why maps distorted, why orange peel rips, why gift wrap wrinkles on basketball.

This is non-obvious because formula for $K$:

$$K = \dfrac{LN-M^2}{EG-F^2}$$

$L,M,N$ explicitly use normal $\mathbf{N}$: $L=\langle r_{uu},\mathbf{N}\rangle$, etc. So $K$ _appears_ to need outside information. $H=(EN+GL-2FM)/2(EG-F^2)$ has same form, but $H$ _does_ change when you bend — $H_{\text{plane}}=0$, $H_{\text{cylinder}}=1/(2R)$. So you'd expect $K$ to change too.

Gauss's massive calculation showed $LN-M^2$ can be rewritten purely in terms of $E,F,G$ and derivatives. $\mathbf{N}$ cancels!

Modern: $K = \dfrac{\langle R(\partial_u,\partial_v)\partial_v,\partial_u\rangle}{EG-F^2}$, where $R$ is Riemann curvature tensor built from Christoffel symbols $\Gamma_{ij}^k$, $\Gamma$ built from $E,F,G$. No embedding.

So $K$ is bending invariant, $H$ is not.

#### Invariance under Bending — Why Cylinder is Flat

**Bending without stretching = isometry = preserves $E,F,G$.**

- Paper → cylinder: $E,F,G$ preserved → isometry → $K$ preserved $0\to0$ → allowed.
- Paper → sphere: would need $E,F,G$ preserved but $0\to1/R^2$ → forbidden by Egregium → any attempt forces stretching, i.e., $E,F,G$ change.

> $K$ is the memory of whether you stretched. If you only bend, $K$ cannot change. Cylinder has same memory as plane, sphere has different memory.

This formalizes: $K$ is a **bending invariant**. Mean curvature $H$ is not.

#### The Paper and The Orange Peel — Two Paradigms

**1. Paper and Cylinders — $K=0$ preserved — Developable Surfaces**

Surfaces with $K\equiv0$ called developable — can be developed (unrolled) onto plane without stretching.

Classification: plane, cylinder, cone, tangent developable of a space curve. All have $K=0$.

- **Pizza theorem:** Floppy pizza slice droops because flat sheet has no rigidity. Fold it lengthwise into U shape, you impose $\kappa_1\neq0$ across width. Dough is approximately unstretchable, so $K=\kappa_1\kappa_2$ must stay $0$. Therefore $\kappa_2$ along length forced to $0$ — slice becomes rigid, doesn't droop. You're using Theorema Egregium to stiffen pizza.

- **Engineering:** Sheet metal, cardboard, architectural panels — developable surfaces cheap to make from flat sheet because only bending needed, no stretching. $K\neq0$ panels require stamping press to stretch.

**2. Orange Peel Problem — $K>0$ obstruction — Doubly Curved**

Sphere $K=1/R^2>0$ constant, doubly curved — bends same way both directions.

Try to flatten orange peel onto table: peel in one piece, press — it rips at edges. Tears release stretching energy needed to change $K$ from $1/R^2$ to $0$.

Consequences:

- Cannot gift-wrap basketball smoothly — wrinkles are local stretch/compression to accommodate $K$ change.
- Car body panel doubly curved ($K\neq0$) requires stretching in press, not just bending.
- Map making impossible without distortion.

> **One-line distinction:** Cylinders are extrinsic illusions — look curved but intrinsically flat, ant thinks flat, triangles sum $180^{\circ}$. Spheres are intrinsically curved — no illusion, ant proves curvature by measuring circles $C<2\pi r$ and triangles sum $>180^{\circ}$, without ever leaving surface.

#### Map Making Limitation — No Perfect Map Exists

Most famous corollary, known to cartographers for millennia, proved by Gauss 1827.

- Plane: $K\equiv0$
- Sphere $R$: $K\equiv1/R^2>0$

If perfect map existed — local isometry from patch of sphere to plane preserving all distances — then Egregium would force $0=1/R^2$, impossible.

**Therefore any flat map of Earth must distort something.** Not engineering, theorem.

Different projections choose sacrifice:

- **Mercator (1569):** Conformal — preserves angles, $F=0$, $E=G$ up to scale. Rhumb lines straight, good for navigation. Distorts area massively — Greenland looks Africa size because area factor $\propto \sec^2(\text{lat})$.

- **Equal-area (Gall-Peters, Mollweide):** Preserves $\sqrt{EG-F^2}$ — area correct, but shapes squashed.

- **Equidistant (azimuthal equidistant):** Preserves distances from one point, distorts elsewhere.

- **Compromise (Winkel Tripel — National Geographic):** Distorts everything a little to minimize overall error.

Gauss proved cartographers can never win. And same reason Gomory's $W=B$ is only obstruction for rectangles but not general regions: when $K$ matches, intrinsic geometry allows isometry; when mismatches, no isometry possible — global count controls possibility.

### Relation to the First Fundamental Form

This is where Gauss does the miracle — eliminates outside.

#### What is First Fundamental Form?

Parametrize surface $r(u,v)\in\mathbb{R}^3$. Then:

$$r_u = \partial_u r,\quad r_v = \partial_v r$$

span tangent plane.

First Fundamental Form $I$ = intrinsic ruler:

$$I = E du^2 + 2F du dv + G dv^2$$

where

$$E = \langle r_u, r_u\rangle,\quad F = \langle r_u, r_v\rangle,\quad G = \langle r_v, r_v\rangle$$

> $E,F,G$ tell ant how to measure. If ant takes small step $(du,dv)$ on parameter map, real distance squared on surface is $E du^2+2F du dv+G dv^2$.
>
> - $E$ = how much $u$-step stretches
> - $G$ = how much $v$-step stretches
> - $F$ = how non-perpendicular $u$ and $v$ directions are (angle cosine)

From $I$ you get everything intrinsic:

- Length of curve $\gamma(t)=(u(t),v(t))$: $\int \sqrt{E \dot u^2+2F\dot u\dot v+G\dot v^2} dt$
- Angle between $r_u$ and $r_v$: $\cos\theta = F/\sqrt{EG}$
- Area: $dA = \sqrt{EG-F^2} du dv$

Ant can measure $E,F,G$ by laying ruler on surface — no $N$ needed.

Second Fundamental Form $II = L du^2+2M du dv+N dv^2$ needs normal $\mathbf{N}$:

$$L=\langle r_{uu},\mathbf{N}\rangle,\quad M=\langle r_{uv},\mathbf{N}\rangle,\quad N=\langle r_{vv},\mathbf{N}\rangle$$

Extrinsic — how surface bends away from tangent plane in $\mathbb{R}^3$.

Usual formula:

$$K = \dfrac{LN-M^2}{EG-F^2} = \dfrac{\det II}{\det I}$$

Looks like needs $II$.

#### Gauss's Tour de Force

Gauss-Codazzi equations relate $I$ and $II$ — compatibility conditions for surface to exist in $\mathbb{R}^3$.

Through massive algebraic manipulation (20+ pages in 1827), Gauss showed $LN-M^2$ can be expressed _entirely_ via $E,F,G$ and their first and second derivatives. $\mathbf{N}$ cancels!

> $\det II$ looks extrinsic, but divided by $\det I$, combination depends only on intrinsic ruler. Like $\kappa_1$ and $\kappa_2$ each need outside, but product doesn't.

**Orthogonal coordinates $F=0$ — most common case:**

If you can choose parameters orthogonal (like latitude-longitude on sphere, or $u$ around, $v$ along cylinder), $F=0$, formula simplifies dramatically:

$$K = -\dfrac{1}{2\sqrt{EG}}\left[ \partial_u\left(\dfrac{G_u}{\sqrt{EG}}\right) + \partial_v\left(\dfrac{E_v}{\sqrt{EG}}\right)\right]$$

> **Read it:** Take $E,G$, differentiate, divide by $\sqrt{EG}$, differentiate again. No $L,M,N$.

Example check:

- Plane $r(u,v)=(u,v,0)$: $E=1,G=1$, $E_v=G_u=0$ → $K=0$.
- Cylinder $r(u,v)=(R\cos(u/R),R\sin(u/R),v)$: $E=1,G=1$, $F=0$ → $K=0$.
- Sphere radius $R$: $r(u,v)=R(\cos u\sin v,\sin u\sin v,\cos v)$: $E=R^2\sin^2 v$, $G=R^2$, $F=0$, $\sqrt{EG}=R^2\sin v$, compute: $K = 1/R^2$.

Works!

**General coordinates — Brioschi formula (1868, but Gauss had equivalent):**

$$
K = \dfrac{1}{(EG-F^2)^2}\left( \begin{vmatrix}
-\tfrac12 E_{vv}+F_{uv}-\tfrac12 G_{uu} & \tfrac12 E_u & F_u-\tfrac12 E_v \\[10pt]
F_v-\tfrac12 G_u & E & F \\[10pt]
\tfrac12 G_v & F & G
\end{vmatrix} - \begin{vmatrix}
0 & \tfrac12 E_v & \tfrac12 G_u \\[10pt]
\tfrac12 E_v & E & F \\[10pt]
\tfrac12 G_u & F & G
\end{vmatrix} \right)
$$

Ugly, but crucial: only $E,F,G$ and derivatives up to second order. No $L,M,N$.

So ant, knowing $E,F,G$ from measuring distances, can compute $K$ via this formula, without ever knowing normal.

#### Modern Riemannian Language — Gauss 90 Years Before Riemann

Christoffel symbols — connection coefficients telling how tangent basis twists within surface:

$$\Gamma_{ij}^k = \dfrac12 g^{kl}(\partial_i g_{jl} + \partial_j g_{il} - \partial_l g_{ij})$$

where $g = \begin{pmatrix}E&F\\[10pt]F&G\end{pmatrix}$, $g^{kl}=g^{-1}$.

$\Gamma$ built only from $E,F,G$ and first derivatives. Intrinsic.

Riemann curvature tensor:

$$R^i_{jkl} = \partial_k \Gamma^i_{jl} - \partial_l \Gamma^i_{jk} + \Gamma^i_{km}\Gamma^m_{jl} - \Gamma^i_{lm}\Gamma^m_{jk}$$

Measures failure of parallel transport to commute — intrinsic.

Then Gaussian curvature:

$$K = \dfrac{\langle R(\partial_u,\partial_v)\partial_v,\partial_u\rangle}{EG-F^2} = \dfrac{R_{1212}}{\det g}$$

> Build ruler $E,F,G$ → build correction $\Gamma$ for how ruler changes → build curvature $R$ from $\Gamma$ → get $K$. All intrinsic. Gauss did this 90 years before Riemann defined $R$ abstractly.

So Egregium is first example of Riemann curvature: 2D case.

**Why remarkable philosophically:**

- $II$ describes how surface sits in space — extrinsic.
- $I$ describes geometry felt inside — intrinsic.
- Theorem says $\det II / \det I$ depends only on $I$. So combination of extrinsic quantities becomes intrinsic.

Like $H=(EN+GL-2FM)/2(EG-F^2)$ also uses $II$ but does NOT reduce to $I$ only — remains extrinsic, changes under bending. Only special combination $LN-M^2$ does.

That's why Gauss called it _egregium_ — you wouldn't expect extrinsic formula to become intrinsic.

### Sketch of Gauss's Proof

Gauss's original proof is 20 pages of brutal differentiation — no abstract machinery yet. Modern sketch captures idea in 5 steps.

#### Goal

Start with extrinsic definition:

$$K = \dfrac{LN-M^2}{EG-F^2},\quad L=\langle r_{uu},N\rangle,\;M=\langle r_{uv},N\rangle,\;N=\langle r_{vv},N\rangle$$

Show $K$ can be written using only $E,F,G$ and derivatives.

#### Step 1 — Express everything in basis $r_u,r_v,N$

We have moving frame $\{r_u,r_v,N\}$. Any second derivative $r_{uu},r_{uv},r_{vv}, N_u,N_v$ can be expressed as linear combination of this basis.

For example:

$$r_{uu} = \Gamma^1_{11} r_u + \Gamma^2_{11} r_v + L N$$
$$r_{uv} = \Gamma^1_{12} r_u + \Gamma^2_{12} r_v + M N$$
$$r_{vv} = \Gamma^1_{22} r_u + \Gamma^2_{22} r_v + N N$$

Coefficients $\Gamma^k_{ij}$ are Christoffel symbols. By dotting with $r_u,r_v$ and using $E=\langle r_u,r_u\rangle$, $F=\langle r_u,r_v\rangle$, $G=\langle r_v,r_v\rangle$, we get:

$$\Gamma = \dfrac12 g^{-1} \partial g$$

Explicitly:

$$\Gamma^1_{11}=\dfrac{G E_u -2F F_u +F E_v}{2(EG-F^2)},\;\text{etc.}$$

> **Key:** $\Gamma$ depends only on $E,F,G$ and first derivatives. Intrinsic! Ant can compute $\Gamma$ from ruler measurements, as correction for how tangent basis twists.

Similarly:

$$N_u = a_{11} r_u + a_{12} r_v,\quad N_v = a_{21} r_u + a_{22} r_v$$

with coefficients involving $L,M,N$ — extrinsic. This is Weingarten map.

#### Step 2 — Compatibility — Derivatives Must Commute

We have $r_{uuv} = r_{uvu}$ etc. — mixed third derivatives commute: $r_{uuv}=r_{uvu}$.

Compute $r_{uuv}$ two ways:

- Differentiate expression for $r_{uu}$ in $v$: $( \Gamma^1_{11} r_u + \Gamma^2_{11} r_v + L N)_v$
- Differentiate expression for $r_{uv}$ in $u$: $( \Gamma^1_{12} r_u + \Gamma^2_{12} r_v + M N)_u$

Set equal. Collect coefficients of $r_u,r_v,N$. The $N$ component gives relation between derivatives of $L,M$ and $\Gamma$, etc. The $r_u,r_v$ components give:

$$\Gamma^1_{11,v} - \Gamma^1_{12,u} + \Gamma^1_{11}\Gamma^1_{12}+... = - \text{something} \cdot (LN-M^2)$$

These are **Gauss equations** — part of Gauss-Codazzi system:

$$r_{uu}\cdot r_{vv} - r_{uv}\cdot r_{uv} = ...$$

After eliminating $r$, you get:

$$LN-M^2 = \text{Expression in } E,F,G,\Gamma,\Gamma_u,\Gamma_v$$

But $\Gamma$ already intrinsic, so right side intrinsic!

#### Step 3 — Solve for $K$

Since $K = (LN-M^2)/(EG-F^2)$, dividing above by $EG-F^2$ gives:

$$K = \dfrac{1}{EG-F^2}\left[ -\dfrac12 E_{vv}+F_{uv}-\dfrac12 G_{uu} + \text{terms with } \Gamma^2\right]$$

Explicitly for orthogonal $F=0$:

$$K = -\dfrac1{2\sqrt{EG}}\left[ \partial_u\left(\dfrac{G_u}{\sqrt{EG}}\right) + \partial_v\left(\dfrac{E_v}{\sqrt{EG}}\right)\right]$$

No $L,M,N$!

For general $F$, Brioschi formula earlier.

> You have two ways to compute $r_{uuv}$ — differentiate $r_{uu}$ then $v$, or $r_{uv}$ then $u$. They must agree. This agreement forces relation linking extrinsic $LN-M^2$ to intrinsic $E,F,G$. Solve for $LN-M^2$, you eliminate extrinsic part.

This is like you have unknown $L,M,N$ but also equations linking their derivatives to $E,F,G$. Enough equations to eliminate $L,M,N$.

#### Step 4 — Modern Language

In modern Riemannian geometry, Step 2 is definition of Riemann tensor:

$$R(\partial_u,\partial_v)\partial_v = \nabla_u \nabla_v \partial_v - \nabla_v \nabla_u \partial_v - \nabla_{[u,v]}\partial_v$$

$\nabla$ is Levi-Civita connection built from $\Gamma$, which built from $E,F,G$.

Then:

$$K = \dfrac{\langle R(\partial_u,\partial_v)\partial_v,\partial_u\rangle}{EG-F^2}$$

Gauss computed $R_{1212}$ without calling it $R$, 90 years before Riemann.

#### Why Proof is Hard — And Why Remarkable

- Gauss had no vector notation, no $\Gamma$ notation, no $R$. He did everything with $E,F,G,L,M,N$ and pages of $E_u,F_v,...$.
- He had to discover $\Gamma$ implicitly as combinations of derivatives of $E,F,G$.
- The cancellation of $L,M,N$ is miraculous — individual $\Gamma$ intrinsic, $L,M,N$ extrinsic, but particular combination $\Gamma_v - \Gamma_u + \Gamma\Gamma$ equals $K(EG-F^2)$.

> **Analogy:** Like proving $(a+b)^2 - (a^2+b^2) = 2ab$ depends only on $ab$, not $a,b$ individually — but here $a,b$ are functions.

**Final punchline:** Once you have $K$ expressed via $E,F,G$, isometry invariance follows immediately: if $f$ preserves $E,F,G$, it preserves any formula built from them, so preserves $K$.

That's Theorema Egregium — extrinsic definition, intrinsic nature, proved by forcing mixed derivatives to commute.

### Why It Matters: Birth of Intrinsic Geometry

Before 1827, surface = subset of $\mathbb{R}^3$. After Egregium, surface = abstract world with its own ruler. That shift created modern geometry, then relativity.

#### Before Gauss — Extrinsic Only

Euler, Monge studied surfaces as $z=f(x,y)$ in $\mathbb{R}^3$. Curvature meant how normal bends in space. No distinction intrinsic/extrinsic.

#### After Gauss — Intrinsic Science

Egregium says: some curvature ($K$) can be known without $\mathbb{R}^3$. So you can define surface abstractly by just $ds^2 = E du^2+2F du dv+G dv^2$, forget embedding. Ant's world exists on its own.

> Before, you needed to see hill from airplane to know it's curved. After, ant crawling on hill can prove it's curved by surveying triangles. Geometry belongs to surface itself, not to how it's placed in space.

#### 4 Consequences That Changed Mathematics

**1. Riemann (1854) — $n$-dimensional manifolds → General Relativity**

Riemann's Habilitation lecture *Über die Hypothesen, welche der Geometrie zu Grunde liegen* generalized Gauss from 2D to $n$D.

* $ds^2 = \sum g_{ij} dx^i dx^j$ — metric tensor, generalization of $E,F,G$.
* Curvature becomes Riemann tensor $R^i_{jkl}$ — generalization of $K$, with many components in $n$D. In 2D, one number $K$ suffices; in 3D, 6 numbers; in 4D, 20.
* Space can be curved intrinsically without ambient $\mathbb{R}^{N}$. No need for outside.

Einstein (1915): Spacetime is 4D manifold with metric $g_{\mu\nu}$, curvature $R$ determined by matter via

$$G_{\mu\nu}=R_{\mu\nu}-\dfrac12 R g_{\mu\nu}=8\pi T_{\mu\nu}$$

Matter tells space how to curve, curved space tells matter how to move. Curvature is intrinsic — no embedding in higher $\mathbb{R}^N$ needed. Universe can be curved and finite without edge, like sphere, because intrinsic curvature allows that.

Without Egregium, general relativity unthinkable — you'd think curvature needs outside.

**2. Cartography — Proved perfect map impossible**

We covered: plane $K=0$, sphere $K=1/R^2$. Egregium says no local isometry → no distance-preserving map.

Not engineering limitation, theorem. Any flat map must sacrifice something: angle (Mercator), area (Gall-Peters), distance (equidistant). Choice of projection is choice of what distortion you tolerate.

Gauss himself was geodesist surveying Hanover — he knew practically.

**3. Topology — Gauss-Bonnet — Curvature total = topology**

Gauss-Bonnet theorem (global version, 1848 Bonnet):

For compact oriented surface $S$ without boundary:

$$\iint_S K dA = 2\pi \chi(S)$$

$\chi(S)=V-E+F$ = Euler characteristic — topological invariant: sphere $\chi=2$, torus $\chi=0$, double torus $\chi=-2$, etc.

> Add up $K$ over whole surface, you get $2\pi$ times topology. Total curvature doesn't depend on bumpy shape, only on how many holes.

* Sphere any shape — bumpy potato — must have total curvature $4\pi$. You can move curvature around, but sum fixed.
* Torus must have total $0$: $K>0$ on outside, $K<0$ inside, cancels.
* You cannot make torus with $K>0$ everywhere — topology forbids.

This links intrinsic measurement ($K$ via triangles) to global topology ($\chi$ via counting). Same spirit as Gomory: local count ($W-B$) controls global tiling; here local curvature integral controls global shape. First great link between geometry and topology.

For region with boundary, add geodesic curvature term: $\int K + \int k_g =2\pi\chi$ — which gives triangle angle defect $\alpha+\beta+\gamma-\pi = \int K$.

**4. Non-Euclidean geometry — Hyperbolic geometry consistent**

For 2000 years, Euclid's 5th postulate (parallel postulate) thought provable. Gauss, Bolyai, Lobachevsky found alternative: hyperbolic geometry where angle sum $<\pi$.

But is it consistent? Does it contain contradiction?

Egregium showed surfaces with $K<0$ constant (pseudosphere) have intrinsic geometry exactly hyperbolic — angle sum $<\pi$, circumference $>2\pi r$. So if Euclidean $\mathbb{R}^3$ consistent, hyperbolic geometry consistent as geometry of such surface.

Later Beltrami, Klein showed full models. Egregium guaranteed model exists without needing ambient contradictions — intrinsic geometry of $K<0$ surface *is* hyperbolic.

> Saddle world where triangles sum <180° is not fantasy; ants living on saddle with $K=-1$ experience exactly non-Euclidean geometry. Gauss proved such world can exist intrinsically.

#### Slogan and Link to Gomory

**Slogan:** Extrinsic bending you see is illusion; intrinsic curvature measured by angle defect is reality. Cylinder is flat, sphere is not, and no bending without stretching can change that.

Both Gomory and Egregium share same philosophy:

| Gomory | Egregium |
| :--- | :--- |
| $W-B$ counts color imbalance | $K$ counts angle/circumference defect |
| $W=B$ necessary for tiling | $K$ preserved necessary for isometry |
| For rectangles, $W=B$ also sufficient — Hamiltonian cycle gives construction | For developable surfaces, $K=0$ sufficient to be locally isometric to plane — unrolling gives construction |
| $W\neq B$ proves impossibility of tiling | $K$ mismatch proves impossibility of perfect map |

Both say: find intrinsic invariant (color count, curvature) that is easy to compute, show it must be preserved, conclude some tasks impossible, and when invariant matches, give explicit construction (snake pairing, unrolling).

That distinction — between what depends on how you sit in space (extrinsic $H$, appearance of tiling) vs what is inherent (intrinsic $K$, $W-B$) — is birth of modern geometry.
### Connection to Physics — General Relativity

Einstein's General Relativity is Theorema Egregium grown from 2D to 4D, from static surface to dynamical spacetime.

#### Spacetime as Manifold — Metric $g_{\mu\nu}$ as $E,F,G$

**Gauss 2D:** Surface given by $ds^2 = E du^2 +2F du dv + G dv^2$. $E,F,G$ = metric. Measures distances on surface.

**Einstein 4D:** Spacetime given by $ds^2 = g_{\mu\nu} dx^\mu dx^\nu$, $\mu,\nu=0,1,2,3$ — pseudo-Riemannian metric with signature $(-,+,+,+)$. $g_{\mu\nu}$ is $4\times4$ matrix, 10 independent components, analog of $E,F,G$ but now with time.

$$ds^2 = -c^2 dt^2 + dx^2+dy^2+dz^2 \quad\text{flat Minkowski}$$

In presence of mass, $g_{\mu\nu}$ distorted, like $E,F,G$ distorted on bumpy surface.

> $E,F,G$ told ant how to measure on hill. $g_{\mu\nu}$ tells astronaut how to measure distance and time near star. Both intrinsic rulers.

Just as ant can measure $E,F,G$ with ruler, physicist measures $g_{\mu\nu}$ with clocks and laser ranging — no need for outside embedding space. Spacetime is not embedded in $\mathbb{R}^5$; it *is* the manifold.

#### Gravity as Curvature — Egregium Made Physical

Gauss: $K$ built from $E,F,G$ via $\Gamma$ and derivatives — intrinsic curvature of metric.

Riemann generalized: curvature tensor $R^i_{jkl}$ built from $g_{ij}$ via Christoffel $\Gamma^i_{jk}$.

Einstein's insight:

> **Gravitational field is not a force through space, but intrinsic curvature of spacetime metric caused by mass-energy.**

Field equations:

$$R_{\mu\nu} - \dfrac12 R g_{\mu\nu} + \Lambda g_{\mu\nu} = 8\pi T_{\mu\nu}$$

* $R_{\mu\nu}$ Ricci tensor — trace of Riemann, analog of $K$ but in 4D
* $R$ scalar curvature — trace of Ricci
* $T_{\mu\nu}$ stress-energy — matter distribution
* Left side $G_{\mu\nu}=R_{\mu\nu}-\dfrac12 R g_{\mu\nu}$ is Einstein tensor — divergence-free combination of curvature, determined by $g_{\mu\nu}$ and second derivatives, just like $K$ determined by $E,F,G$.

> Gauss said $K = (\text{stuff from }E,F,G)$. Einstein said $G_{\mu\nu} = (\text{stuff from }g_{\mu\nu}) = 8\pi T_{\mu\nu}$. Matter tells metric how to curve, curvature tells how to compute gravity.

Without Egregium, you'd think curvature needs outside space to bend into. Egregium proved curvature exists intrinsically — space can be curved without being embedded in higher dimension. That's essential: general relativity says universe can be curved, closed like 3-sphere, without outside.

#### Geodesics — Free Fall as Straightest Path

**Gauss 2D:** Geodesic equation on surface:

$$\ddot u^k + \Gamma^k_{ij} \dot u^i \dot u^j =0$$

$\Gamma$ from $E,F,G$. Shortest path for ant. On plane straight line, on sphere great circle, on cylinder helix that unrolls to straight line.

**Einstein 4D:** Free-falling particle (no rockets) travels along geodesic of spacetime:

$$\ddot x^\mu + \Gamma^\mu_{\nu\rho} \dot x^\nu \dot x^\rho =0$$

Same equation! $\Gamma^\mu_{\nu\rho}$ now Christoffel of $g_{\mu\nu}$.

> Throw ball on Earth — in Newton, force pulls down. In Einstein, ball goes straight in curved spacetime. Spacetime curved by Earth, so "straight" looks curved to us, like great circle looks curved on map but straight on sphere.

Light also follows null geodesics $ds^2=0$, bent by curvature — gravitational lensing observed 1919 eclipse, confirming intrinsic curvature.

Ant on cylinder thinks it's going straight but bird sees helix around cylinder. Astronaut orbiting Earth thinks weightless straight, we see orbit.

#### Why No GR Without Egregium

* **Conceptual:** Egregium created notion of intrinsic curvature independent of embedding. Before Gauss, curvature meant bending in $\mathbb{R}^3$. After, space itself can be curved. Einstein needed that to say spacetime curved, not bending in higher $\mathbb{R}^N$.

* **Mathematical:** Formalism — metric $g$, Levi-Civita connection $\Gamma$, Riemann tensor $R$ — all direct generalization of Gauss's $E,F,G$, $\Gamma$, $K$. Gauss computed first example of $R_{1212}$ in 2D, 27 years before Riemann's $n$D definition.

* **Physical measurement:** Gauss gave intrinsic experiments to measure $K$ — angle sum, circumference defect. Einstein gives same for spacetime: measure tidal forces (geodesic deviation) — second derivatives of $g$, i.e., curvature. If you and neighbor free-fall, distance between you changes due to curvature, just like circles $C(r)\neq2\pi r$. That's how LIGO detects gravitational waves — measures changing $g$.

**One-line:** Gomory's $W-B$ and Gauss's $K$ both say some tasks impossible due to intrinsic invariant. Einstein turned $K$ into dynamical field: mass changes $g_{\mu\nu}$, which changes $K$-like curvature $R_{\mu\nu}$, which changes geodesics, which we feel as gravity. No embedding needed — remarkable theorem became theory of universe.
### The Brioschi Formula

This is the explicit receipt for Egregium — plug $E,F,G$ in, get $K$ out, no $L,M,N$.

#### What It Says

Given $r(u,v)$, metric $ds^2 = E du^2+2F du dv+G dv^2$, $E=\langle r_u,r_u\rangle$, $F=\langle r_u,r_v\rangle$, $G=\langle r_v,r_v\rangle$.

Then $K$ is:

$$K = \dfrac{1}{(EG-F^2)^2}\left[ \begin{vmatrix} -\dfrac12 E_{vv}+F_{uv}-\dfrac12 G_{uu} & \dfrac12 E_u & F_u-\dfrac12 E_v \\[10pt] F_v-\dfrac12 G_u & E & F \\[10pt] \dfrac12 G_v & F & G \end{vmatrix} - \begin{vmatrix} 0 & \dfrac12 E_v & \dfrac12 G_u \\[10pt] \dfrac12 E_v & E & F \\[10pt] \dfrac12 G_u & F & G \end{vmatrix} \right]$$

First determinant mixes second derivatives $E_{vv},F_{uv},G_{uu}$ with first derivatives. Second determinant only first derivatives squared.

> Take ruler measurements $E,F,G$. See how they vary — first derivatives $E_u,E_v$ etc., how stretching changes. See how variation varies — second derivatives $E_{vv},G_{uu}$. Combine via those two $3\times3$ determinants, divide by $(EG-F^2)^2$, you get $K$. No normal vector.

#### Step-by-Step How to Use

**1. Identify $E,F,G$**

$$E = r_u\cdot r_u,\; F=r_u\cdot r_v,\; G=r_v\cdot r_v$$

Measures distances, angles, area element $dA=\sqrt{EG-F^2} du dv$. Must have $EG-F^2>0$ for regular patch — area positive.

**2. Compute derivatives**

First order: $E_u=\partial_u E$, $E_v$, $F_u$, $F_v$, $G_u$, $G_v$ — how metric stretches as you move.

Second order: $E_{vv}=\partial_{vv}E$, $F_{uv}$, $G_{uu}$ — curvature of stretching.

**3. Evaluate discriminants**

Denominator $(EG-F^2)^2 = (\det g)^2$ — square of area factor.

Numerator = two determinants.

**4. Orthogonal case $F=0$ — 90% of practical uses**

If coordinate curves perpendicular, $F=0$, formula collapses to:

$$K = -\dfrac{1}{2\sqrt{EG}}\left[ \partial_u\left(\dfrac{G_u}{\sqrt{EG}}\right) + \partial_v\left(\dfrac{E_v}{\sqrt{EG}}\right) \right]$$

> **Intuition:** If $G$ grows quickly in $u$, $G_u$ large, circles get larger than Euclidean → $K$ negative, etc.

Alternative expanded:

$$K = \dfrac{1}{4(EG)^2}[E(E_v G_v+G_u^2)+G(E_u G_u+E_v^2)-2EG(E_{vv}+G_{uu})]$$

#### Why It Proves Egregium

Structure explicitly eliminates second fundamental form $L,M,N$. Only $E,F,G$. Therefore any isometry preserving $E,F,G$ preserves $K$. Ant with ruler can compute $K$ — just measure distances, differentiate.

Brioschi 1868 gave this clean determinant form, but Gauss 1827 had equivalent pages of algebra — first intrinsic formula.

#### Examples — Brioschi in Action

**Plane $r=(u,v,0)$:** $E=1,F=0,G=1$, all derivatives $0$ → both determinants $0$ → $K=0$.

**Cylinder $r=(R\cos(u/R),R\sin(u/R),v)$:** $E=1,F=0,G=1$ → same as plane → $K=0$. Shows isometry plane→cylinder.

**Sphere radius $R$:** $r=R(\cos u\sin v,\sin u\sin v,\cos v)$ — here $u$ longitude, $v$ colatitude. $E=R^2\sin^2 v$, $F=0$, $G=R^2$. Then $\sqrt{EG}=R^2\sin v$. Compute: $E_v=2R^2\sin v\cos v$, $G_u=0$. Then:

$K = -\dfrac{1}{2R^2\sin v}[ \partial_v (0) + \partial_v(2R^2\sin v\cos v / (R^2\sin v)) ] /2$? Let's compute quickly: $E_v/\sqrt{EG}=2R^2\sin v\cos v / (R^2\sin v)=2\cos v$, derivative $\partial_v = -2\sin v$. $G_u=0$. So $K = -\dfrac1{2R^2\sin v}(-2\sin v)=1/R^2$.

Matches extrinsic $\kappa_1\kappa_2$.

**Pseudosphere $K=-1$:** Parametrization tractrix revolution: $E=\sinh^2 v$? Brioschi gives $-1$.

### Theoretical Significance

Brioschi is where philosophy becomes calculation.

#### From Existence to Recipe

Theorema Egregium says *there exists* formula for $K$ using only $E,F,G$. That's abstract existence.

Brioschi gives explicit algebraic recipe:

> Take $E,F,G$, differentiate up to twice, take two $3\times3$ determinants, divide by $(EG-F^2)^2$ → $K$.

No need to guess, no solving PDEs, no embedding. It's second-order differential operator on metric:

$$K = \mathcal{D}_2[g_{ij}]$$

where $\mathcal{D}_2$ involves $\partial^2 g$ and $(\partial g)^2$.

> Before Brioschi, Gauss said "K can be computed intrinsically — trust me, pages of cancellation". After Brioschi, you can compute K in 5 minutes from metric.

That's why it's constructive proof: it *constructs* $K$ from intrinsic data alone, eliminating $L,M,N$ visibly.

#### Modern View: $K = R_{1212}/\det g$

In Riemannian language:

1. $g = \begin{pmatrix}E&F\\F&G\end{pmatrix}$ — metric
2. $\Gamma^k_{ij} = \frac12 g^{kl}(\partial_i g_{jl}+\partial_j g_{il}-\partial_l g_{ij})$ — Levi-Civita connection, built from $g,\partial g$. Intrinsic.
3. $R^i_{jkl}= \partial_k\Gamma^i_{jl} - \partial_l\Gamma^i_{jk} + \Gamma\Gamma - \Gamma\Gamma$ — Riemann tensor, built from $\Gamma,\partial\Gamma$, so from $g,\partial g,\partial^2 g$.
4. In 2D, $R$ has one independent component $R_{1212}$, and:

$$K = \frac{R_{1212}}{\det g} = \frac{R_{1212}}{EG-F^2}$$

Brioschi formula is just explicit expansion of $R_{1212}$ in terms of $E,F,G$.

So Gauss discovered 2D Riemann tensor 27 years before Riemann defined $n$D version. Brioschi formula is first example of curvature as second derivatives of metric.

#### Why This Matters

**1. Intrinsic determination — ant can compute:**

Ant measures distances, gets $E,F,G$ at nearby points, numerically estimates $E_u\approx (E(u+h)-E(u))/h$, etc., plugs into Brioschi → $K$. No need to see $\mathbb{R}^3$.

Example: On sphere, ant measures $ds^2 = R^2\sin^2 v du^2 + R^2 dv^2$, computes $K=1/R^2$ via Brioschi, concludes sphere, not plane.

**2. Invariance under isometry — automatic:**

If $f$ preserves $E,F,G$, it preserves all derivatives $E_u$, etc., and $EG-F^2$, so preserves determinants, so preserves $K$. No extra argument needed — Brioschi makes Egregium trivial corollary.

**3. Foundation for general relativity:**

Einstein equations: $G_{\mu\nu}=R_{\mu\nu}-\frac12 R g_{\mu\nu}=8\pi T_{\mu\nu}$. Left side is second-order operator on $g_{\mu\nu}$, just like Brioschi is second-order operator on $E,F,G$.

Brioschi showed pattern: curvature = second derivatives of metric + squares of first derivatives. Einstein used same pattern in 4D. Matter $T_{\mu\nu}$ sources this operator.

Without Gauss-Brioschi, no template for how to build curvature from metric.

**4. Computability:**

Before computers, Brioschi allowed explicit $K$ for surfaces of revolution, helicoids, etc. Today, discrete differential geometry uses discrete Brioschi-like formulas to compute curvature on triangulated meshes from edge lengths only — used in computer graphics, $3$D scanning, cloth simulation.

**5. Distinguishes $K$ from $H$:**

Mean curvature $H = (EN+GL-2FM)/2(EG-F^2)$ *cannot* be expressed without $L,M,N$. No Brioschi-like formula exists for $H$. So $H$ remains extrinsic, changes under bending. Brioschi's existence for $K$ and non-existence for $H$ is precisely the extrinsic/intrinsic split.

> **One-line:** Brioschi turns "remarkable" philosophical statement into algebra: $K$ is function of ruler measurements alone, calculable with derivatives. That's why curvature is intrinsic reality, not embedding illusion — you can compute it with ruler and calculus, no third dimension needed.
### Real-World Examples

1.  **Cylinder vs Plane:** Same intrinsic geometry. An ant on a cylinder thinks it lives on a plane. $K=0$ for both.
2.  **Sphere vs Plane:** Different intrinsic geometry. No isometry. You must stretch. $K_{\text{sphere}}=1/R^2 \neq 0$.
3.  **Saddle:** $K<0$. A potato chip cannot be flattened without crumpling. Its angle sum for a triangle is $<\pi$.
4.  **Theorema Egregium in one sentence:** Gaussian curvature can be discovered by an inhabitant of the surface, blind to the ambient 3D world, simply by measuring distances and angles and seeing how circles and triangles deviate from Euclid.

This is why Gauss called it "remarkable" — he had defined $K$ using the embedding in space, then discovered the embedding was irrelevant.
