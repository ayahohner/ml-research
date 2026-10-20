# Cross-Topic Notes: Reservoir Computing ↔ Geometric Deep Learning ↔ Categorical Deep Learning

These are short notes on where the three digests overlap. IDs refer to each topic's own bibliography. RC IDs are prefixed `RC:`, GDL IDs `GDL:` and CDL IDs `CDL:`.

## 1. One propagation theory for RNNs, SSMs, GNNs and Transformers

- In RC, the echo state property and the edge-of-chaos regime govern how far input information travels through time and how fast it fades (fading memory). The 2026 RC theory notes cover stability-vs-reach bounds ([RC 03](reservoir-computing/03-theory.md)).
- In GDL, over-smoothing and over-squashing govern how information travels through *depth and graph topology*. The 2026 survey [GDL:R3] unifies these with Transformer rank and representational collapse. Separate work links deep GNNs to recurrent vanishing gradients [GDL:G7].
- **Takeaway.** A sequence is a path graph, and an RNN or reservoir is message passing along it. Memory–nonlinearity trade-offs (RC) and over-squashing sensitivity bounds (GDL) are two faces of the same Jacobian-product analysis.

## 2. Structured linear recurrences

ParalESN and FRESCO bring RC close to diagonal state-space models ([RC 02](reservoir-computing/02-algorithms-and-architectures.md)). On the graph side, graph SSMs and graph-Mamba variants apply the same linear-recurrence machinery to node orderings. Untrained or randomized propagation, in the style of reservoirs, is a natural cheap baseline there.

## 3. Graph reservoirs

Graph echo state networks (GraphESN, and later work by Gallicchio, Micheli and colleagues) apply fixed random recurrent message passing to graphs and train only a readout. Their stability conditions mirror the echo state property. Given the 2026 finding that tuned simple baselines often beat elaborate models [GDL:F1], untrained graph reservoirs deserve a place as baselines in graph-learning studies.

## 4. A shared methodological lesson

Both fields reached a "benchmarking crisis" around 2025–26:

- RC benchmarks are critiqued in [RC 05](reservoir-computing/05-benchmarks-and-evidence.md)
- graph benchmarks are critiqued in [GDL:R7] and the fair GFM evaluation [GDL:F1]

Neither field has a formal meta-analysis. In both, the recommended protocol is the same: tuned strong baselines, compute-matched comparisons, multiple seeds, and out-of-distribution or structural-generalization splits.

## 5. Physical substrates and symmetry

Physical and quantum reservoirs exploit the native dynamics of a substrate. Equivariant networks exploit the native symmetries of a domain. Both are bets that **structure supplied for free beats structure learned at cost**. Both face the same 2026 counter-trend: generic, hardware-efficient trained models (digital SSMs, unconstrained Transformers with learned symmetry [GDL:E2]) that win whenever data and compute are plentiful.

## 6. CDL as the "type system" over GDL

CDL contains GDL. Group-equivariant layers are monad-algebra homomorphisms [CDL:R1], and category-equivariant networks extend universal approximation from groups to posets, graphs and sheaves [CDL:E1]. The 2026 results point the same way in both fields:

- GDL: learned symmetry rivals hard-wired symmetry at scale [GDL:E1, GDL:E2]
- CDL: no fixed equivariant attention architecture covers all equivariant attention [CDL:E4], and test-time symmetrization over non-invertible rewrites helps LLM provers [CDL:E3]

Together they suggest *specifying* structure categorically and *enforcing* it softly, through losses or test-time aggregation, rather than only through hard architectural constraints.

## 7. Reservoirs in categorical terms

An echo state network is a **Mealy-machine coalgebra** with a *fixed* (unlearned) state map and a learned readout. In CDL terms [CDL:R1], it is a Para morphism whose parameters live only on the output port. Folding RNNs are endofunctor algebras over lists. A reservoir is then an unfold with frozen dynamics, and the echo state property says that this coalgebra forgets its initial state. Categorical cybernetics [CDL:F4, CDL:F5] would describe training an RC readout as an optic acting only on the readout parameters. This is a compact way to compare RC, trained RNNs and SSMs in one framework.
