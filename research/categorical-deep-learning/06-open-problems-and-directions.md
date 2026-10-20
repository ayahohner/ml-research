# 06 · Open Problems and Directions

## Open problems

1. **A constructive equivariance toolkit for categories.** For groups, e3nn and escnn turn a symmetry specification into layers automatically. The CDL analogue would take a monad, category or sheaf and produce the space of natural parametric layers. Only special cases exist so far: posets, sheaves and copresheaves [E1, E2].
2. **New architectures from theory.** Find at least one architecture that is derived from categorical structure and beats tuned baselines on a task people care about. Algorithmic reasoning [A1, A7] and structured reasoning or theorem proving [E3] are the most promising candidates.
3. **Lax and approximate structure.** A quantitative theory of "almost commuting" diagrams (lax algebras, approximate naturality) [R1, E4] would connect CDL to soft or learned symmetry, which the GDL evidence favors at scale.
4. **Nonlinearities and normalization.** Give compositional categorical semantics for softmax, LayerNorm/RMSNorm, gating and MoE routing [A5].
5. **Bridge to learning theory.** Generalization bounds, optimization dynamics and scaling laws are all missing. Lenses say how updates compose, not whether they converge or generalize.
6. **Depth-wise structure theorems.** Extend single-layer results such as equivariance loci of MHSA [E4] to blocks and stacks.
7. **Benchmarks.** Sheaf NNs got their first inductive benchmark in 2026 [S2]. Similar benchmarks are needed for CENNs and CTNNs on genuinely poset-, lattice- or sheaf-structured data.
8. **Interpretability that scales.** Compositional interpretability [L1] needs efficient, optimizable faithfulness and complexity measures, for example via tensor networks.

## Directions to watch (late 2026 → 2027)

- **Architecture compilers.** pyncd/tsncd [D1] and graphical einops [D4] could become a formal intermediate representation for architecture search, kernel derivation and verification. The DARPA/AFOSR funding behind [D1] suggests a verification angle.
- **Symmetry for reasoning models.** Test-time symmetrization over rewriting categories [E3] is cheap and works with any model. Expect it to spread to code generation, SQL and math word problems, and possibly into training objectives.
- **Formal verification of NN-enabled systems.** Dependent types, coherent logic [F6] and proof-theoretic readings of architectures [F7] meet neural-network verification.
- **Compositional interpretability** as a principled objective for mechanistic interpretability [L1].
- **CDL ↔ learned symmetry.** Combining categorical *specification* of desired structure with *learned or soft* enforcement (losses, test-time aggregation) instead of hard architectural constraints. This reconciles CDL with the bitter-lesson-style evidence from GDL.

## Practical recommendations (Oct 2026)

| If you are… | Then… |
|---|---|
| Learning the area | Read [R1] → [F2] → [R4]/[R5], then [D1] for the implementation side. Keep [R7] as an index. |
| Designing a novel architecture | Use the cheat-sheet in [02](02-frameworks-and-architectures.md) to *specify* the structure. Implement with standard tools and benchmark against tuned baselines. Don't expect the formalism to supply performance. |
| Working on efficient kernels | Try neural circuit diagrams / pyncd for deriving fused or IO-aware implementations [D1, D2] |
| Working on LLM reasoning robustness | Identify the rewriting category of your domain and apply test-time aggregation over equivalent inputs [E3] |
| Working on graph data with heterophily or hierarchy | Try sheaf NNs, but tune generic components first; SNNs are not yet a default win [S2] |
| Evaluating CDL claims | Use the checklist in [05](05-evidence-and-critiques.md) |
