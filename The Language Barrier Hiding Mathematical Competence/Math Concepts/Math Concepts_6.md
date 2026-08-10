## Gomory's Theorem — When Counting Is Enough

This is a favorite theorem because it's rare. In most tiling problems, passing the easy counting test is just the beginning — you still have to worry about shape. Gomory's theorem says: for rectangles, the easy test is _everything_.

> **Philosophy:** Sometimes the obvious obstruction is the only obstruction. If you can get past counting, you can always finish the puzzle. That's what makes this theorem special.

### History and Context

- **The negative part** — mutilated chessboard: remove opposite corners (same color) → impossible — is folklore, known since at least early 20th century. Gamow and Stern mentioned it in 1958.

- **The positive part** — opposite colors → always possible — was proved by **Ralph E. Gomory** in 1973. Gomory was a mathematician at IBM, famous for cutting-plane methods in integer programming. He was thinking about polyomino tilings in general.

- It was popularized by **Solomon Golomb** — inventor of polyominoes and author of _Polyominoes_ — and by **Martin Gardner** in his _Scientific American_ column. Gardner loved puzzles where impossibility is easy but possibility is surprising.

So the theorem has two faces:

- The impossibility puzzle says: "Counting can prove impossibility quickly."
- Gomory says: "For rectangles, counting is _complete_ — if counting doesn't rule it out, it's doable."

### Precise Statement

> **Gomory's Theorem (1973):** If any two squares of opposite colors are removed from an $8\times8$ chessboard, the remaining 62 squares can always be perfectly covered by 31 dominoes.

Note: 62 squares is $31 \times 2$, so 31 dominoes is the right number. And opposite colors means 31 white + 31 black remain.

**General form:** Any $m\times n$ board with $mn$ even, remove one white and one black → tileable.

It is the complement of the mutilated board impossibility:

- **Impossibility — same color:** Remove two white squares → $W=30, B=32$. Each domino needs $1W+1B$. 31 dominoes need $31W+31B$. Mismatch → impossible. This is a 10-second proof. It's a simple **invariant**: $I = W-B$ must be 0 for tileable region, each domino has $I=0$, sum of $I=0$ regions has $I=0$.

- **Possibility — Gomory — opposite colors:** Remove one white + one black → $W=31, B=31$. Invariant satisfied ($I=0$). But $I=0$ usually doesn't guarantee tilings! Here, surprisingly, it does.

> Same-color removal fails for a dumb counting reason. Opposite-color removal _could_ fail for a clever shape reason — but Gomory proves it never does on a rectangle.

### Why Is This Surprising? — Most Counting Tests Are Not Enough

To appreciate rarity, consider other tiling problems:

- **Trominoes:** Tile a $8\times8$ minus one square with $3\times1$ trominoes? $63$ is divisible by 3, count passes, but tiling is impossible for many positions of missing square — need more invariants mod 3.

- **$3\times3$ minus center:** 8 squares, 4 white 4 black, balanced, but can you tile a donut shape with dominoes? Yes here, but add a narrow isthmus and it fails — see previous section.

- **Aztec diamond with a hole:** Balanced but not tileable due to Hall violator.

So usually you need:

1. Global balance: $W=B$
2. Local balance: every subregion has enough neighbors (Hall's condition)

Gomory says for rectangles, 1 implies 2 automatically.

### The Coloring Invariant — Why Same Color Fails

This is the classic example of an **invariant proof**. It's the trick you learn once and then see everywhere in math.

> **The big idea:** Some property stays the same no matter what you do. If the start and end have different values of that property, the task is impossible.

Here, the invariant is **color balance**.

#### Setup — Color the Board

Take a normal $8\times8$ chessboard. Color it in the usual way: alternating white and black.

Count:

- White squares: 32
- Black squares: 32

Crucial fact: **Adjacent squares always have opposite colors.** The board is _bipartite_ — like a checkerboard. Up-down, left-right, you always step from white to black.

Now look at a domino. A $2\times1$ domino, no matter where you place it horizontally or vertically, always covers exactly **2 adjacent squares**.

> A domino is too small to cheat. It can't cover two whites diagonally, it must cover neighbors. And neighbors are always opposite colors.

So:

**Invariant Lemma:** Every domino covers 1 white + 1 black.

That never changes. No clever placement changes it.

#### Necessity Proof — The Same-Color Removal Fails

Now the mutilated chessboard problem: Cut out two opposite corners. Or more generally, cut out any two squares. Can you tile the remaining 62 squares with 31 dominoes?

Case 1: You remove two squares of the **same** color.

Say you remove two white squares. What remains?

$$W = 32 - 2 = 30,\quad B = 32$$

30 white, 32 black.

Suppose for contradiction you _could_ tile it with 31 dominoes.

Each domino contributes 1 white and 1 black to the covered set. So if you have 31 dominoes:

$$|W_{covered}| = 31,\quad |B_{covered}| = 31$$

Because $1+1+...$ 31 times = 31 of each.

But $W_{covered}$ must be all remaining white squares = 30, and $B_{covered}$ = 32. So you'd need:

$$31 = 30 \text{ and } 31 = 32$$

Impossible. Contradiction.

> **In plain English:** 31 dominoes always want 31 whites and 31 blacks. You are offering them 30 whites and 32 blacks. You are short one white and have one extra black. No rearrangement fixes a counting mismatch.

Same argument if you remove two black squares: $W=32, B=30$, still impossible.

So:

**If you remove two squares of the same color, tiling is IMPOSSIBLE.**

Note the logic: we proved that _opposite colors_ is **necessary**. We did not yet prove it's enough.

#### Why This is an Invariant

Define for any region $R$, the imbalance $I(R) = |W(R)| - |B(R)|$.

- For the full board: $I=32-32=0$
- For a domino $D$: $I(D)=1-1=0$
- For a union of $k$ dominoes: $I = 0+0+...=0$. So any tileable region must have $I=0$.

If you remove two whites: $I = 30-32 = -2 \neq 0$. Since $I\neq0$, it cannot be a union of dominoes. $I$ is invariant under adding dominoes.

> **Analogy:** It's like trying to pay $30 worth of white tokens and $32 worth of black tokens with $31 bills that are each $1 white + $1 black. Each bill is balanced. Any stack of balanced bills is balanced. You can never make an unbalanced pile.

#### Is Opposite Colors Enough? — Sufficiency

We proved same-color => impossible. What about opposite-color removal?

If you remove one white and one black: $W=31, B=31$. The counting obstruction disappears. $I=0$. Does that guarantee a tiling exists?

**Yes.** This is **Gomory's theorem** (1973, actually Ralph Gomory): For a rectangular board, removing one white and one black square _always_ leaves a tileable board.

> The color count is not just necessary, it's sufficient. If the numbers work, you can actually do it.

Proof sketch for intuition: you can draw a Hamiltonian cycle — a loop that visits every square exactly once and returns to start, stepping to neighbors. On a chessboard, such a loop alternates colors: white, black, white, black... If you remove one white and one black, you cut the loop into two paths, each has equal whites and blacks, and each path can be tiled by dominoes along the loop.

So the full theorem:

> An $8\times8$ board with two squares removed can be tiled by $2\times1$ dominoes **iff** the two removed squares are opposite colors.

Same-color fails for a deep reason (invariant). Opposite-color always works (constructive proof).

This is the prototype of all coloring arguments: color cleverly, find a quantity each tile preserves, compare counts.

### Statement and Generalizations

#### The Sharp Generalization

> **General Gomory:** For any $m \times n$ rectangular board with $mn$ even — so at least one side is even, otherwise you can't tile even the full board — if you remove one white and one black square, the remaining board is _always_ domino-tileable.

> On any even-sized rectangle, the color count is the _only_ obstruction. If the counts match, you can always tile. The classic $8\times8$ missing opposite corners is just one example.

**Why does this work for all rectangles? Hamiltonian cycle.**

A Hamiltonian cycle is a loop that visits every square exactly once and returns to the start, moving only to edge-neighbors.

Does an $m\times n$ rectangle with $mn$ even have one? Yes, if at least one side is even. Picture a snake:

```
→ → → → → ↓
↑ ← ← ← ← ←
→ → → → → ↓
...
```

You go across the first row, down one, back across second row, down one, etc., and close the loop on the left edge. It's a simple picture you can draw for any $4\times5$, $6\times6$, $8\times8$.

Why does that help?

A Hamiltonian cycle on a chessboard must alternate colors: $W-B-W-B-...-W-B$ around the loop. Length $mn$ is even, so exactly $mn/2$ white, $mn/2$ black alternating.

Now remove one white $w$ and one black $b$. Cut the cycle at those two points. What happens?

The cycle becomes either:

1. One path if $w$ and $b$ were adjacent on the cycle — still length $mn-2$ with alternating colors.
2. Two separate paths if they were not adjacent — each path starts and ends with opposite colors? Let's check: if you remove a white and a black from an alternating cycle, each remaining segment starts with one color and ends with the other, so each segment has equal whites and blacks.

> Take a necklace of alternating black and white beads in a loop. Remove one black and one white bead. You're left with either one string or two strings. Every string now has alternating beads starting black and ending white, or vice versa. So each string has equal numbers.

And any alternating path is trivially tileable: just lay dominoes along the path, covering beads $1$-$2$, $3$-$4$, etc.

So existence of a Hamiltonian cycle _automatically_ gives you a tiling after opposite-color removal. No searching needed.

This generalizes hugely:

**Theorem:** Any finite induced subgraph of $\mathbb{Z}^2$ — meaning any polyomino region — that has a Hamiltonian cycle is **elementary**: removing any one white and any one black vertex leaves a region with a perfect matching (a domino tiling).

> **Vocabulary:** In matching theory, a bipartite graph is "elementary" if removing one vertex from each side always leaves a perfectly matchable graph. Gomory says rectangular grids are elementary.

Rectangular boards are Hamiltonian, so they are elementary.

#### When It Fails — Need for Topology / Shape Matters

> **Key lesson:** Opposite colors is _necessary_ everywhere, but it's only _sufficient_ when the region is "nice" enough. If the shape has holes or thin bottlenecks, counts can match and tiling can still be impossible.

Balanced count ($W=B$) is not enough for weird shapes.

**Example 1: Disconnection after removal.**

Imagine a figure-8 shape: two big $4\times4$ blocks connected by a single bridge square in the middle, plus one extra square to make it width 2 at the bridge.

```
Block A -- bridge -- Block B
```

The bridge itself might be white. The left block has, say, 8 white 9 black, right block 9 white 8 black, plus bridge white to balance total to 17-17.

Now remove a black square deep inside left Block A and a white square deep inside right Block B — opposite colors overall, so $W=B$ still holds. But after removal, left Block A (without its black) plus bridge might have 9 white 8 black, right Block B without its white has 8 white 8 black? Actually the bridge connects them — need more careful counting.

Better, classic counterexample: Take an $8\times8$ board, remove a central $2\times2$ block to make a donut. You still have 60 squares, 30 white 30 black — balanced. Now remove one white from outer rim and one black from inner rim on opposite sides of the donut such that... this still often tiles.

The cleanest counterexample is a region with a **narrow isthmus of width 1**.

Picture:

```
XXXX
XXXX
X  X
X  X
XXXX
XXXX
```

Two big chambers connected by a corridor of width 1 square. Suppose corridor is white, length 1. Left chamber has $W_L, B_L$, right chamber $W_R, B_R$.

Total balance: $W_L+W_R+1 = B_L+B_R$.

If you remove a white from left and a black from right (opposite colors), you might leave left chamber with $W_L-1$ vs $B_L$, which could be unbalanced if $W_L = B_L$ originally. Then left chamber alone would need more black than it has, but the only connection to the rest is the single white bridge square — which can only provide one connection. Dominoes can't cross the bridge twice.

Formally: Let $S$ be set of white squares in left chamber. Their neighbors $N(S)$ are black squares mostly in left chamber, plus maybe the bridge. If $|S| > |N(S)|$, Hall's condition fails.

> Think of a house with two rooms connected by a single doorway that is white. If the left room has more white squares than black squares (after your removals), any domino covering a white in left room must use a black in left room — except possibly one that uses the doorway. One doorway can't fix a big imbalance. So tiling fails even though whole house is balanced.

Concretely, make left chamber $3\times3$ minus center = 8 squares, 4 white 4 black. Right chamber same. Connect them with a single white square touching both. Total: 4+4+1=9 white, 4+4=8 black — already unbalanced, so add one extra black square somewhere. Now balanced. Remove a black from left chamber and a white from right chamber. Left chamber now has 4W 3B, plus white bridge that can pair with at most one black from left, still you have extra white stuck in left.

This is the essence.

**So what property do we need to guarantee opposite-color removal works?**

- Simply-connected (no holes) is **not enough** — the figure-8 with isthmus is simply-connected and still fails.
- We need something stronger like **2-connected** plus Hamiltonian, or that the graph is **elementary**.

For rectangles, Hamiltonicity guarantees a strong form of Hall's condition:

**Connection to Matching Theory**

Domino tilings = perfect matchings in bipartite grid graph $G = (W \cup B, E)$ where edge = adjacency.

After removing $w\in W, b\in B$, we ask: does $G\setminus\{w,b\}$ have a perfect matching?

**Hall's Marriage Theorem:** A bipartite graph with $|W|=|B|$ has a perfect matching iff for every $S\subseteq W$, $|N(S)| \ge |S|$ — every set of white squares has at least as many black neighbors.

> Hall says you can't have a group of white squares that collectively touch too few black squares. If 5 white squares only touch 4 black squares, you can't match them all — pigeonhole principle.

For a general region, you must check all $2^{|W|}$ subsets — hard.

Gomory's Hamiltonian cycle gives a free proof of Hall: any interval of the cycle has at least as many neighbors as vertices because the cycle itself provides two distinct neighbors for interior vertices, and cutting out one white and one black can't create a Hall violator.

For non-rectangular regions without a Hamiltonian cycle, Hall can fail even when $W=B$.

**Summary**

| Region type                      | Opposite colors ($W=B$) necessary? | Opposite colors sufficient? | Why?                                                  |
| :------------------------------- | :--------------------------------- | :-------------------------- | :---------------------------------------------------- |
| Any region                       | Yes                                | No                          | Invariant $I=0$                                       |
| Rectangle $m\times n$, $mn$ even | Yes                                | Yes — Gomory                | Hamiltonian cycle exists, gives explicit tiling       |
| Hamiltonian polyomino            | Yes                                | Yes                         | Same proof as rectangles                              |
| Shape with narrow bridge or hole | Yes                                | No                          | Bridge creates Hall violator: local imbalance trapped |

So coloring gives a quick "no" test. If it passes, you need to look at shape — does the region have enough connections to let dominoes flow? For rectangles, the answer is always yes.

### Proof — Hamiltonian Cycle Construction — the 5-Second Visual Proof

This is the proof everyone remembers because you can _see_ it.

> **Goal:** Given $8\times8$ minus one white $w$ and one black $b$, produce 31 dominoes, no search.

#### Step 1 — Construct the Cycle

Consider the board graph: vertices = 64 squares, edges = share a side.

**Claim:** This graph has a Hamiltonian cycle — a loop that visits every square exactly once and returns to start.

> You can draw one continuous snake that goes through every square once and bites its own tail.

Why does it exist? Because one side is even. Here $8$ is even, so we can snake.

Explicit construction for $8\times8$:

```
Row1: (1,1) → (1,2) → (1,3) →... → (1,8) ↓
Row2: (2,8) ← (2,7) ←... ← (2,1) ↓
Row3: (3,1) → (3,2) →... → (3,8) ↓
Row4: (4,8) ←... ← (4,1) ↓
...
Row8: (8,8) ← (8,7) ←... ← (8,1) ↑
Close: (8,1) ↑ to (1,1)
```

You go left-to-right on odd rows, right-to-left on even rows, down one at the ends, and on the last row you go up the leftmost column back to start. You get a closed loop:

$$c_0, c_1, c_2, \dots, c_{63}, c_0$$

where $c_i$ adjacent to $c_{i+1}$, and $c_{63}$ adjacent to $c_0$, all 64 squares appear once.

**Crucial property:** Because the chessboard is bipartite — black-white-black-white — any step moves to opposite color. So colors alternate around the cycle:

$$W, B, W, B, \dots, W, B$$

If we number $c_0$ white, then $c_{even}$ = white, $c_{odd}$ = black.

For $m\times n$ with $m$ even, same snake works and closes along left edge. If $n$ even instead, snake vertically. So any even rectangle is Hamiltonian.

> If both $m,n$ odd, $mn$ odd, you can't have a Hamiltonian cycle covering all vertices and returning — you'd need even length to alternate and return to opposite color? Actually a Hamiltonian cycle needs even number of vertices in bipartite graph. So $mn$ even is necessary. That's exactly the condition for tileability.

#### Step 2 — The Break — Remove Two Squares

Now remove $w = c_i$ white and $b = c_j$ black, $i \neq j$.

What happens to the cycle when you delete two vertices?

Imagine a circular necklace. Snip out two beads. The circle breaks.

Two cases:

1. **$w$ and $b$ adjacent on the cycle:** i.e., $j = i+1$ or $i=j+1$ mod 64. Then you cut out two neighboring beads. Remaining is **one single path** of 62 beads: $c_{j+1} \dots c_{i-1}$ wrapping around.

2. **Not adjacent:** You cut in two places. The circle becomes **two disjoint paths**:
   $$P_1 = c_{i+1}, c_{i+2}, \dots, c_{j-1}$$
   $$P_2 = c_{j+1}, c_{j+2}, \dots, c_{i-1}$$ wrapping around the other way.

Visually:

```
Before: O-O-O-O-O-O-O-O-O loop
Remove W at position i and B at position j
After:...-O-O [gap] O-O-...-O-O [gap] O-O-...
        \_________________/ \_________________/
                P1 P2
```

#### Step 3 — Even Lengths — Key Parity Observation

Why do both remaining pieces have even length? Because we removed opposite colors.

Since colors alternate, parity = color. Let's say $c_0$ white. Then:
$c_k$ white iff $k$ even, black iff $k$ odd.

$w$ white => $i$ even, $b$ black => $j$ odd (or vice versa). So $j-i$ is **odd**.

Length of $P_1 = j-i-1$ (number of vertices strictly between $i$ and $j$). Odd minus 1 = even.

Length of $P_2 = 64 - (j-i) -1 = 63 - (j-i)$. 63 is odd, minus odd = even.

> Between a white and a black on an alternating loop, there are an even number of beads in between on each side. If you removed same color, you'd have odd on both sides — impossible to pair up. Opposite colors makes the counts even.

If adjacent: $j-i=1$ (odd). Then $P_1$ length 0 (even, empty path — fine) and $P_2$ length 62 (even).

This parity is the whole secret.

#### Step 4 — Tile Each Path — No Thinking Needed

Any path graph with even number of vertices can be perfectly tiled by dominoes _along the path_.

Why? Pair them up in order:

$$(c_{i+1},c_{i+2}), (c_{i+3},c_{i+4}), \dots$$

Since consecutive vertices in the cycle are adjacent squares on the board, each pair is a legal domino (vertical or horizontal).

Do this for $P_1$ and $P_2$.

Combine: you have $(|P_1|/2 + |P_2|/2) = 62/2 = 31$ dominoes covering exactly the board minus $w,b$.

**Done. Constructive proof = linear-time algorithm.**

> **Bead analogy:** You have a chain of alternating black/white beads. Cut out one black and one white. You're left with two chains each starting with black and ending with white (or vice versa). Pair beads $1$-$2$, $3$-$4$, etc. No bead left over. That's your domino tiling.

Since each consecutive pair in the cycle are neighbors on board, each domino is valid.

Complexity: $O(mn)$ to build snake, $O(mn)$ to tile. No backtracking search.

#### Why This Shows Rectangles Are Special

This proof works _only_ because we had a Hamiltonian cycle to start with.

Many non-rectangular regions don't have one. Example: region with width-1 isthmus — any Hamiltonian cycle would need to enter and exit each side through same single square, impossible. So you can't use this trick, and indeed Gomory can fail.

For rectangles, Hamiltonicity gives you for free:

- $|N(S)| \ge |S|$ for all $S$ — Hall's condition — because the cycle gives each set $S$ at least as many distinct neighbors along the cycle.

Thus for rectangles:

**Layer 1 — Counting:** $W=B$? $O(1)$
**Layer 2 — Geometry:** Is there a Hall violator? For rectangles, Hamiltonian cycle proves no.

> **Takeaway:** Gomory's theorem is "when counting is enough." Same-color removal: counting says impossible in 10 seconds. Opposite-color removal: counting says maybe, and Hamiltonian cycle turns "maybe" into "definitely, and here's how to do it in 5 seconds visually."

That's why it's taught as the complement to the mutilated board puzzle — one direction uses invariant to prove impossibility, the other uses a global structure (Hamiltonian cycle) to prove possibility, with no casework.

### What Is Hamiltonian Path / Cycle?

This is one of the most famous concepts in graph theory, named after William Rowan Hamilton who marketed the "Icosian game" in 1857 — find a cycle around a dodecahedron.

Let's make it super concrete.

#### Definitions — With Pictures in Your Head

Imagine your graph is a map of cities, vertices are cities, edges are roads.

- **Hamiltonian Path:** A road trip that visits every city _exactly once_. You don't need to return home. You can start anywhere, end anywhere, but you must not repeat a city, and you must see them all.

  Example on $3\times3$ board:

  ```
  1→2→3
        ↓
  6←5←4
  ↓
  7→8→9
  ```

  That's a Hamiltonian path from 1 to 9 visiting all 9 squares.

- **Hamiltonian Cycle (Circuit):** A road trip that visits every city exactly once **and returns to start**. So it's a closed loop. You also require the last city to be connected back to the first.

  > Path = open chain covering everything. Cycle = closed necklace covering everything.

  Every Hamiltonian cycle contains a Hamiltonian path — just cut the cycle at any point. But converse is false: you can have a Hamiltonian path whose endpoints are not adjacent, so you can't close it into a cycle.

  Example: On a $3\times3$ board minus center, there is a Hamiltonian path around the ring, and because first and last are adjacent, it's also a cycle. On a $2\times3$ board, there's a Hamiltonian path, but can you close it? Yes if you arrange. On a $3\times3$ full board (9 vertices odd), you _cannot_ have a Hamiltonian cycle in a bipartite graph — because bipartite cycle must be even length. You can have Hamiltonian path, but not cycle.

**Chessboard graph:** vertices = 64 squares, edge = share a side (up/down/left/right, not diagonal). This graph is bipartite: black squares only connect to white squares.

Is it Hamiltonian? Yes.

> **Why parity matters for bipartite:** Any cycle must alternate $W-B-W-B...$ So any cycle must have even length. $8\times8$ has 64 even, so possible. $7\times7$ has 49 odd, so no Hamiltonian cycle exists — but it does have Hamiltonian path of length 49.

#### The Chessboard is Hamiltonian — Why Generalization is Easy

**Theorem:** All rectangular grid graphs $P_m \square P_n$ — $m$ columns, $n$ rows — with at least one side even ($mn$ even) have a Hamiltonian cycle.

> If you can make the board's area even, you can snake a loop through it.

We gave the explicit snake:

```
m even case:
Row1 left→right
Down
Row2 right→left
Down
Row3 left→right...
...
Last row right→left, then up leftmost column to start.
```

For $m$ even, this closes cleanly. If $m$ odd but $n$ even, do same snake vertically.

If both $m,n$ odd, $mn$ odd, no Hamiltonian cycle exists — as argued by parity. But you still have Hamiltonian path.

This constructive snake is why Gomory's theorem is _elementary_ — we don't need to search for a Hamiltonian cycle, we can draw it in 10 seconds.

#### Complexity Note — Why This is Surprising

In **general graphs**, deciding "Does a Hamiltonian cycle exist?" is **NP-complete**.

> For arbitrary graphs, there is no known fast algorithm to tell if a Hamiltonian cycle exists. If you could solve it quickly for all graphs, you'd prove $P=NP$ and win a million dollars. Best known algorithms are exponential time — try all possibilities.

It's one of Karp's 21 NP-complete problems.

So why is chessboard easy?

Because grids are highly structured. We have explicit constructions.

There are sufficient conditions that guarantee Hamiltonicity without searching:

**Dirac's Theorem (1952):** If you have $n$ vertices and every vertex has degree $\ge n/2$, then Hamiltonian cycle exists.

> **Intuition:** If every city is connected to at least half of all cities, graph is so dense you can't get stuck. You can always extend.

For chessboard graph, interior vertices degree 4, edge 3, corner 2. $n=64$, $n/2=32$. Degree $4 \ge 32$? No. So Dirac does NOT apply — grid is sparse. Dirac is useless for grids.

**Ore's Theorem (1960):** More general: If for every pair of _non-adjacent_ vertices $u,v$, $d(u)+d(v) \ge n$, then Hamiltonian.

> **Intuition:** Even if some vertices have low degree, if any two non-neighbors together touch enough vertices, you can still patch.

Again fails for grids — two opposite corners each degree 2, sum 4 < 64. So Ore also fails.

Both Dirac and Ore are for _dense_ graphs. Grids are _sparse_ — degree at most 4 regardless of size — so they need different arguments.

**For grid graphs, we use constructive proof, not density.**

That is why Gomory's theorem is tractable:

- Hamiltonian cycle in general: NP-complete, hard.
- Hamiltonian cycle in rectangular grid with one even side: $O(mn)$ trivial snake.

We exploit structure to bypass hardness.

Once you have that cycle, the tiling proof is just cutting the necklace.

### Pedagogical Value and Connections

Gomory's theorem is taught not because domino tilings of chessboards are important by themselves, but because it is a perfect _miniature_ of how mathematics works. In 2 pages you meet invariants, constructive proofs, matching theory, counting vs geometry, and topology.

#### Invariant vs Construction — The Two Directions of Existence Proofs

Every existence question has two sides, and beginners often confuse them.

> **In simple terms:**
>
> - To prove something is **impossible**, you need ONE reason it can never happen, no matter how clever you are.
> - To prove something is **possible**, you need to SHOW how to do it — give a recipe, algorithm, construction.

Most students try to prove impossibility by trying all possibilities and failing. That's not a proof — you might have missed one. The invariant method is smarter.

**Direction 1 — Impossibility via invariant:**

Find a quantity that:

1. Is easy to compute for the target region.
2. Is preserved (or bounded) for any tile / piece.
3. Differs between region and tiles.

For dominoes, invariant is $I = W-B$.

- Full board: $I=0$
- Each domino: $I=0$
- Any union of dominoes: $I=0+0+...=0$

If region has $I=-2$ (30 white, 32 black), it cannot be a union of dominoes. One number kills all $10^{something}$ possible tilings instantly.

> **Analogy:** To prove you can't pay $31 with only $2 coins, you don't try all combinations. You say "any sum of $2 coins is even, 31 is odd." Parity is invariant.

**Direction 2 — Possibility via construction:**

To prove possible, counting is not enough. You must exhibit a tiling, or give an algorithm that always produces one.

Gomory's Hamiltonian cycle pairing is such an algorithm: snake → cut → pair. It's constructive, $O(mn)$ time, no search.

**Pedagogical lesson:**

> Many students stop after Layer 1. They check $W=B$ and say "so it should tile." That's false in general. Gomory teaches you to distinguish:
>
> - **Necessary condition:** If tileable, then $W=B$. Contrapositive: If $W\neq B$, not tileable.
> - **Sufficient condition:** If $W=B$, then tileable. This is FALSE for general regions, TRUE for rectangles.
>
> Gomory identifies a class where necessary = sufficient. That's rare and valuable. We say the counting invariant is **complete** for that class — the only obstruction.

Examples where counting is NOT complete:

- Aztec diamond with a hole in middle: $W=B$ but hole creates bottleneck.
- Region with narrow bridge width 1: balanced globally but locally unbalanced — Hall violator.
- Tiling $10\times10$ with $4\times1$ trominoes: area $100$ divisible by 4, but need coloring mod 4 with 4 colors to rule out.

So Gomory is the poster child for "when cheap test is enough."

#### Links to Deeper Theory

**1. Perfect matchings — graph theory language**

Domino tiling = perfect matching in bipartite graph $G = (W \cup B, E)$. $W$ = white squares, $B$ = black, $E$ = adjacency.

- Perfect matching = set of edges covering every vertex exactly once.
- Gomory says: Grid graph $P_m \square P_n$ with $mn$ even is **elementary bipartite**.

> **Definition in simple terms:** Elementary means "robustly matchable." Remove any one white and any one black, you still have a perfect matching. It's like a building that stays stable after removing one pillar from each side.

Not all graphs with perfect matchings are elementary. Example: Take 6-cycle $C_6$ plus a chord connecting opposite vertices — it has perfect matching, but removing two specific opposite vertices destroys all matchings.

Grids are elementary because Hamiltonian cycle gives two disjoint perfect matchings (take alternating edges), providing redundancy.

**2. Pfaffian / Kasteleyn — how many tilings?**

Gomory guarantees _at least one_ tiling exists after opposite-color removal.

But how many? Exponentially many.

Kasteleyn (1961) and Temperley-Fisher (1961) gave exact product formula:

$$\text{# tilings of } m\times n \text{ board} = \prod_{j=1}^{\lceil m/2\rceil} \prod_{k=1}^{\lceil n/2\rceil} \left(4\cos^2\frac{\pi j}{m+1}+4\cos^2\frac{\pi k}{n+1}\right)$$

For $8\times8$, that's 12,988,816 tilings. For $8\times8$ minus opposite colors, number varies but still huge — millions.

The formula uses Pfaffian orientation: assign signs to edges so that counting matchings = determinant. This is deep: counting domino tilings is in P, while counting matchings in general graphs is #P-complete. Planar bipartite graphs are special.

> Gomory says "at least one way." Kasteleyn says "actually $12$ million ways, and here's formula." Gomory is existence, Kasteleyn is enumeration. Existence is easy via Hamiltonian cycle; enumeration needs linear algebra.

**3. Topology — holes and genus**

Existence of Hamiltonian cycle relates to topology.

- Simply-connected region (no holes) — more likely Hamiltonian.
- Region with hole — like donut — may still be Hamiltonian (8x8 minus 2x2 center still has cycle going around hole) but not always.
- Region with many holes, high genus, or narrow isthmuses — Hamiltonicity can break.

Euler characteristic $\chi = V - E + F$ is another counting invariant that classifies surfaces: sphere $\chi=2$, torus $\chi=0$, etc. Like $W-B$, $\chi$ is a global count that controls structure. Gomory is same spirit: global count (color balance) controls tiling, but only when topology is simple (rectangle = disk).

> **Analogy:** For polyhedra, Euler proved $V-E+F=2$ for any convex polyhedron — a global count that must hold, no matter shape. For domino tilings of rectangles, $W-B=0$ is similarly complete. Both are examples of "global counting controls local geometry" when topology is trivial.

For non-simply-connected regions, you need more refined invariants: e.g., flux, height function (Thurston), or homology.

**4. What to take away as a learner?**

- **Method 1 — Invariant:** To prove impossibility, look for quantity preserved by tiles. Coloring is the simplest. More advanced: mod 2, mod 4 colorings, weighting.
- **Method 2 — Construction:** To prove possibility, give explicit construction. Hamiltonian cycle, induction, or greedy algorithm.
- **Meta-lesson:** Ask "Is my necessary condition also sufficient? If not, what's the extra obstruction?" In Gomory's world, answer is "No extra obstruction for rectangles." In most worlds, there is extra obstruction, and finding it is research.

That duality — cheap necessary test vs expensive sufficient construction, and identifying when they coincide — appears everywhere: from Hall's marriage theorem, to Euler $V-E+F$, to P vs NP. Gomory is the friendliest example.

### Distinction: Gomory Cuts vs Gomory's Chessboard Theorem

Yes — this confusion happens a lot because the same person, **Ralph E. Gomory**, is famous for two completely different things with the same name.

> Ralph Gomory has two famous "Gomory's theorems" — one is a puzzle about dominoes, the other is an algorithm for optimizing airlines and factories. Same brain, different fields. Don't mix them.

#### 1. Gomory's Chessboard Theorem — This Chapter — Combinatorics / Tiling

- **Field:** Recreational mathematics, polyomino tiling, matching theory.
- **Year:** 1973, popularized by Golomb and Martin Gardner.
- **Question:** Can you tile a mutilated chessboard with dominoes?
- **Result:** If you remove opposite colors from a rectangle, you always can. Hamiltonian snake construction.
- **Nature:** Existence theorem — guarantees at least one tiling. Proof is visual, elementary.
- **Use:** Puzzle, teaching invariants, matching theory.

#### 2. Gomory Cuts / Gomory's Cutting Plane Method — Operations Research — Integer Programming

- **Field:** Optimization, operations research, integer linear programming (ILP).
- **Year:** 1958, paper "Outline of an algorithm for integer solutions to linear programs." This is the work that made Gomory famous and got him the National Medal of Science.
- **Question:** You want to maximize profit $c^T x$ subject to $Ax \le b$, but $x$ must be integer — e.g., you can't build 2.7 factories. Linear programming gives you fractional solution. How do you find integer optimum?

- **Result — Cutting planes:**
  1. Solve LP relaxation (allow fractions) → get fractional solution $x^*$.
  2. If $x^*$ integer, done.
  3. If not, find a **Gomory cut** — a linear inequality that:
     - Cuts off $x^*$ — $x^*$ violates it.
     - Does NOT cut off any integer feasible point — all integer solutions still satisfy it.
  4. Add cut to problem, resolve LP. Repeat. Eventually you either get integer solution or prove infeasibility. Finite termination.

> Imagine feasible integer points are dots inside a polygon. LP relaxation is the whole polygon, including fractional interior. Fractional optimum is at a corner of polygon, not on a dot. Gomory cut is like slicing off that fractional corner with a straight cut that doesn't remove any dots. Keep slicing until a dot becomes a corner.

Example: $x_1 + x_2 \le 2.5$, $x_i \ge 0$ integer. LP optimum $(2.5,0)$ fractional. Gomory cut: $x_1 + x_2 \le 2$ — cuts off $(2.5,0)$ but keeps $(2,0),(1,1),(0,2)$ etc.

- **Nature:** Algorithm — iterative, optimization, used in every modern MILP solver (Gurobi, CPLEX, SCIP). Foundation of integer programming.
- **Use:** Airline scheduling, logistics, chip design, etc.

#### Why Same Name?

Both are by Ralph E. Gomory (1929- ), mathematician at Princeton, IBM, later president of Sloan Foundation.

- 1958: Cutting planes — his PhD-era breakthrough.
- 1973: Chessboard tiling — a side observation while thinking about polyominoes.

Mathematicians often have multiple unrelated theorems named after them. It's like "Euler's theorem" — could be $a^{\phi(n)} \equiv 1 \mod n$, or $V-E+F=2$, or $e^{i\pi}+1=0$ — same Euler.

#### How to Tell Which Gomory Someone Means

- If context is **dominoes, chessboard, mutilated board, polyominoes, Hamiltonian cycle, Golomb, Gardner** → Chessboard theorem — combinatorics.

- If context is **integer programming, MILP, LP relaxation, cutting plane, branch-and-cut, fractional solution** → Gomory cuts — optimization.

They share a philosophy: "Find the obstruction and cut it away," but technically unrelated.

> Gomory's chessboard theorem shows that for rectangular boards, the trivial parity obstruction $W\neq B$ is the _only_ obstruction — a Hamiltonian snake turns a simple count into an explicit construction.

While Gomory cuts show that for integer programs, fractional obstructions can be removed by adding clever inequalities until counting (integrality) is enough.

### Why Mathematicians Care

Why does a simple domino puzzle matter beyond recreation? Because it's a clean model where deep phenomena appear in elementary form.

#### 1. Elementary Bipartite Graphs — Robust Matchings

Recall: domino tilings = perfect matchings in grid graph $G = (W \cup B, E)$.

$G$ has a perfect matching — full $8\times8$ tiles. But many graphs have a perfect matching yet are _fragile_.

> **Definition:** A bipartite graph with a perfect matching is **elementary** if removing _any_ one white and _any_ one black vertex still leaves a graph with a perfect matching. The matching is robust — you can lose one from each side and still match the rest.

Gomory says $P_m \square P_n$ with $mn$ even — the rectangular grid — is elementary.

This is non-trivial. Most bipartite graphs with perfect matchings are NOT elementary.

**Counterexample — 6-cycle with a chord that fails:**

Take 6 vertices: $W=\{w1,w2,w3\}$, $B=\{b1,b2,b3\}$ in a cycle:
$w1-b1-w2-b2-w3-b3-w1$ is a 6-cycle. This has perfect matching.

Now add a chord: add edge $w1-b2$. Still has perfect matching.

But remove $w2$ and $b3$. Remaining graph: $w1,w3$ vs $b1,b2$. Edges: $w1-b1$, $w1-b2$, $w3-b2$. Can we match both whites? $w3$ only connects to $b2$, $w1$ can go to $b1$, so yes actually this still matches. Let's make a better failing example:

Classic failing example: Take path $w1-b1-w2-b2-w3-b3$ plus extra edges $w1-b2$ and $w2-b3$. Full graph has perfect matching $w1-b1, w2-b2, w3-b3$. Remove $w1$ and $b1$ — remaining $w2,w3$ vs $b2,b3$ has edges $w2-b2,w2-b3,w3-b3$ — still matchable. Hmm.

Simplest failing: Consider graph where one white $w1$ only connects to $b1$, and rest is complete. So edges: $w1-b1$ only, plus all edges from $w2,w3$ to $b1,b2,b3$. Full graph has perfect matching: $w1-b1, w2-b2, w3-b3$. But remove $w2$ and $b2$, remaining $w1,w3$ vs $b1,b3$. $w1$ only connects to $b1$, ok $w1-b1, w3-b3$ works. Need more precise:

Take $W=\{w1,w2,w3\}, B=\{b1,b2,b3\}$. Edges: $w1$ connected only to $b1$; $w2$ to $b1,b2$; $w3$ to $b2,b3$. This has perfect matching $w1-b1, w2-b2, w3-b3$. Remove $w1$ (white) and $b3$ (black). Remaining $w2,w3$ vs $b1,b2$. Edges: $w2-b1,b2$, $w3-b2$. This has matching $w2-b1, w3-b2$ — still works. Remove $w1$ and $b2$: remaining $w2,w3$ vs $b1,b3$: edges $w2-b1$, $w3-b3$ — works.

Need Hall violator after removal: Let $w1$ connect to $b1$ only, $w2,w3$ connect to $b1,b2$ only, no edges to $b3$ except from $w3$? Actually let's construct: $W=\{w1,w2,w3\}, B=\{b1,b2,b3\}$. Edges: $w1-b1$, $w2-b1,b2$, $w3-b1,b2$. No edges to $b3$. Then no perfect matching at all. So need perfect matching initially.

Standard elementary counterexample: A square with a pendant: Take $C4$: $w1-b1-w2-b2-w1$ plus two extra vertices $w3$ attached only to $b2$, $b3$ attached only to $w2$, and edge $w3-b3$. So whole graph has perfect matching $w1-b1, w2-b2, w3-b3$. Remove $w1$ and $b1$, remaining $w2,w3$ vs $b2,b3$ — edges $w2-b2, w3-b2,b3$ — still has matching $w2-b2,w3-b3$? Yes.

The textbook counterexample: $P4$ with an extra edge making it non-elementary: $w1-b1-w2-b2$ plus edge $w1-b2$. This graph on 4 vertices IS elementary actually — removing any opposite pair leaves single edge.

The smallest non-elementary with perfect matching is: Take $w1-b1, w1-b2, w2-b1, w2-b2, w2-b3, w3-b2, w3-b3$? Let's brute mental: After removing $w1,b3$, remaining $w2,w3$ vs $b1,b2$ edges $w2-b1,b2, w3-b2$ — has matching $w2-b1,w3-b2$ works.

Ok, formal fact: A bipartite graph is elementary iff its allowed edges (edges that belong to some perfect matching) form a connected graph. The 6-cycle with chord $w1-b2$ where chord is not allowed? In $C6$, all edges allowed. Add chord $w1-b2$ that is not allowed? In $C6$ $w1-b1-w2-b2-w3-b3-w1$, edge $w1-b2$ is allowed via matching $w1-b2,w2-b3?, no $w2$ not connected to $b3$... So need systematic.

**Don't get lost in counterexample hunting — point is:** It is easy to build a graph where some white vertex is "essential" for some black vertex, so after removing a different pair, you get stuck. Grid graphs have no such essential bottleneck because Hamiltonian cycle provides two disjoint perfect matchings — the even edges of cycle and odd edges of cycle — giving redundancy.

> In an elementary graph, every edge is part of some perfect matching, and the allowed part is connected — you can shift matchings around. Grid graphs have that flexibility. Many graphs don't.

Why mathematicians care: Elementary bipartite graphs have nice structure theorem (Dulmage-Mendelsohn decomposition). Gomory gives a natural infinite family that is elementary, useful as base case for induction.

#### 2. Hall's Theorem Made Easy — From Exponential to Constant

**Hall's Marriage Theorem:** $G=(W\cup B,E)$ with $|W|=|B|$ has perfect matching iff for all $S\subseteq W$, $|N(S)| \ge |S|$.

$N(S)$ = set of black neighbors of $S$.

To verify Hall directly, you must check $2^{|W|}$ subsets. For $8\times8$, $|W|=32$, that's $2^{32} \approx 4$ billion subsets — impossible.

> Hall says "no group of white squares is too isolated." But checking all groups is exponential.

Gomory says for rectangles, you don't need to check.

Because $W=B$ (one count) implies Hall holds automatically after opposite-color removal. Why? Hamiltonian cycle argument shows for any $S$, its neighbors along cycle plus maybe more give $|N(S)|\ge |S|$. The cycle itself is a 2-regular spanning subgraph that forces expansion.

> **Analogy:** Normally to prove a school can pair 32 boys and 32 girls for dance, you'd need to check every subset of boys likes enough girls. Gomory says for this particular school (grid), if numbers equal, pairing always possible — you don't need to interview subsets.

So Gomory identifies a class where **global count implies local expansion**. That's rare. In general graphs, global count $|W|=|B|$ is far from sufficient.

This is pedagogically valuable: it shows a situation where an NP-hard-looking condition collapses to $O(1)$.

#### 3. Polyomino Theory — Base Case for Larger Tiles

Solomon Golomb invented polyominoes — connected sets of squares. Domino is order 2 polyomino.

Hard question: When can a region be tiled by a given polyomino set?

Golomb used Gomory's theorem as **base case** for induction on larger polyominoes.

Example: Can you tile a board with $4\times1$ trominoes plus dominoes? You often reduce to smaller rectangles. Knowing that any opposite-color-deficient rectangle is domino-tileable lets you handle leftover regions after placing larger pieces.

Also, it motivates invariants beyond simple black-white. For $2\times2$ tromino? Actually tromino $L$ shape covers 2 of one color and 1 of other, so color invariant different. Gomory shows that for dominoes, 2-coloring is complete. For larger polyominoes, you need more colors — e.g., 4-coloring mod 2 for $2\times2$ blocks.

> Dominoes need 2 colors to understand. Larger tiles need more colors. Gomory is the prototype: find coloring where each tile covers fixed numbers of each color, then compare counts. For rectangles and dominoes, 2 colors suffice to be complete.

Golomb's book _Polyominoes_ uses Gomory to prove theorems like: A $2n \times 2n$ board with one square removed cannot be tiled by $2\times2$ blocks, but can be tiled by $3$-ominoes under conditions, etc.

**Summary of why mathematicians care:**

| Concept               | What Gomory gives                                                                                                 |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------- |
| **Elementary graphs** | Natural infinite family of elementary bipartite graphs, with explicit Hamiltonian cycles providing redundancy     |
| **Hall's theorem**    | Example where exponential Hall condition collapses to single global count $W=B$ — from $2^{32}$ checks to 1 check |
| **Polyomino theory**  | Base case and model for coloring invariants for larger tiles — shows when 2-coloring is complete                  |

In one line: It is the simplest example where counting is enough, and understanding _why_ it is enough (Hamiltonicity → expansion → Hall) teaches you how to look for extra obstructions when counting is not enough.
