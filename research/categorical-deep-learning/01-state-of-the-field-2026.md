# 01 · State of the Field (late 2026)

## The one-paragraph version

Categorical deep learning (CDL) uses category theory as a **specification and implementation language for neural networks**. It has two strands.

- **Learning as composition** (2017–22): backprop is a functor [F1], and gradient-based learning is built from parametric lenses and optics [F2, F3].
- **Architecture as algebra** (2022–24): architectures are algebras of monads or endofunctors in the 2-category Para [R1]. This subsumes geometric deep learning's group equivariance and extends it to non-invertible structure such as lists, trees, automata and algorithms [A1, A2].

In 2025–26 CDL matured into a **small but productive research niche**. It has not become a paradigm that changes how mainstream models are built. Its most tangible 2026 outputs are:

- formal architecture languages with working compilers (pyncd/tsncd, TMLR 2026) [D1, D2, D4]
- equivariance generalized from groups to categories, with universal approximation [E1, E2]
- category-theoretic notions of symmetry applied to LLM theorem proving [E3] and interpretability [L1]
- sheaf neural networks, the most experimentally developed descendant, now benchmarked honestly [S2]

The flagship commercial bet, Symbolica, was built on the ICML 2024 position paper. It then went through public turmoil and has not published CDL results at scale [C1].

## Five storylines of 2025–26

### 1. From manifesto to formalism with compilers

The 2024 position paper [R1] promised a single theory that covers both *top-down* constraint specification (GDL) and *bottom-up* implementation (autodiff frameworks). The clearest 2026 delivery on the bottom-up half is **Weaves, Wires, and Morphisms** [D1] (TMLR 08/2026).

- It formalizes broadcasting through axis-stride and array-broadcasted categories.
- It ships Python and TypeScript libraries that build architectures algebraically, convert them to graphs, compile them to PyTorch and render diagrams.
- It builds on *FlashAttention on a Napkin* [D2], which derived FlashAttention and its IO cost model from diagrams.
- *Graphical einops* [D4] adds a proof-enabling calculus that turns equivariance proofs into diagram rewrites and yields sparse attention.

### 2. Equivariance beyond groups

GDL handles invertible symmetries (groups). CDL's central technical claim is that many useful structures are not invertible, for example algorithmic contractions, causal or temporal order, and hierarchies [R1].

- **Category-equivariant NNs (CENNs)** [E1] define equivariance as naturality. They prove a universal approximation theorem that covers groups, groupoids, posets, lattices, graphs and cellular sheaves.
- **Copresheaf TNNs** (NeurIPS 2025) [E2] give a single framework that formally contains GNNs, Transformers, sheaf NNs and topological NNs.
- The 2026 theorem-proving paper [E3] uses *rewriting categories* for non-invertible tactic rewrites. It turns this into a measurable failure of LLM provers: DeepSeek-Prover-V2 falls from 50% to 4.7% success on equivalent statements. It also gives a test-time fix.

### 3. Limits of hard-wired symmetry, proved algebraically

*No Equivariant Architecture Covers All Equivariant Attention* [E4] (Aug 2026) shows that the space of equivariant multi-head attention layers has very many irreducible components (Ω(C⁶⁴) for D₄ with 8 heads). Any fixed constrained architecture captures at most one of them. This is a formal counterpart to the GDL finding that *learned* symmetry can rival *hard-wired* symmetry (see [`../geometric-deep-learning/05-benchmarks-and-evidence.md`](../geometric-deep-learning/05-benchmarks-and-evidence.md)).

### 4. Interpretability and semantics

- **Compositional interpretability** [L1] defines an explanation as a commuting syntax/semantics square, scored by minimum description length. It offers a principled target for mechanistic interpretability.
- **Enriched-category models of language** [L2, L3] treat LLM next-token probabilities as enrichment and study their magnitude.
- Other work uses categorical analysis for AGI comparison [R6] and for symbol grounding [L5].

### 5. Sheaves are the empirical frontier, and the evidence is sobering

Sheaf neural networks are the most deployed category-flavored architecture. Activity in 2026 covered SPD-valued sheaves [S4], equivariant sheaves [S3], pooling [S5] and Gaussian sheaves [S6]. The first systematic inductive benchmark [S2] (1,890 runs, 14 datasets) found:

- SNNs transfer to inductive settings but **underperform the strongest baselines**
- generic architectural components matter more than sheaf design

## Where CDL stands, by maturity

| Area | Maturity | Evidence |
|---|---|---|
| Learning as optics/lenses (backprop, optimizers, RL) | Mature theory; research libraries | [F1–F5] |
| Architecture specification and diagrams | Formalisms with compilers to PyTorch | [D1–D4] |
| Equivariance generalized to categories | Theory with universal approximation; few experiments | [E1, E2] |
| Algorithmic alignment (GNN ↔ DP, cocycles, monoids) | Theory with modest experiments | [A1–A3, A7] |
| Symmetry for LLM reasoning (theorem proving) | First empirical wins | [E3] |
| Sheaf neural networks | Empirically tested; not state of the art | [S2] |
| Category-designed models at scale | **Not demonstrated** | [C1] |

## Is there a meta-analysis?

**No.** There is no meta-analysis, and very few head-to-head empirical comparisons exist. CDL is primarily a theoretical and formal-methods program. The literature is reviewed by four surveys [R3, R4, R5, R7]. [05-evidence-and-critiques.md](05-evidence-and-critiques.md) covers what empirical evidence exists and the main critiques.
