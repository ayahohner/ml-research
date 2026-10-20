# 03 · Theory

The theory agenda for graph ML was laid out in [R8]: expressivity, generalization and optimization, which until recently were studied separately. The 2025–26 trend is to **combine them**.

## 1. Expressivity

- **The WL hierarchy.** Message-passing GNNs are at most as powerful as 1-WL color refinement. Higher-order, subgraph and positional-encoding GNNs climb the hierarchy. The 2026 KR paper [G4] gives a unified account of *uniform* expressivity: what a single fixed-size GNN can express across graphs of all sizes, as opposed to non-uniform (size-dependent) results.
- **Geometric expressivity.** For 3D GNNs, invariant models such as distance-only networks cannot distinguish some point clouds. Equivariant models with higher-order irreps, or complete local frames, can. This is why irrep order ℓ_max matters for MLIP accuracy.
- **Caveat.** Expressivity says nothing about whether a model *learns* the separating function or *generalizes* [R8]. That gap motivates the next section.

## 2. Generalization

- **Rademacher complexity unifying expressivity and geometry** [G3]. Carrasco et al. give data-dependent bounds in which complexity depends on how the training sample falls into equivalence classes induced by a graph invariant (such as WL colors), and on Lipschitz and covering-number geometry inside those classes. Under Wasserstein-type distances this yields robustness guarantees. More expressivity can *hurt* generalization if it shatters the sample into many classes.
- **Empirical counterpart.** In TDL, models that saturate the training distribution fail on refined triangulations [G5]. That is a clean case of expressivity without structural generalization.

## 3. Propagation pathologies: over-smoothing and over-squashing

- **Over-smoothing**: deep message passing drives node features toward a low-dimensional subspace (Dirichlet energy goes to 0).
- **Over-squashing**: information from exponentially many distant nodes must pass through bottleneck edges. Sensitivity bounds tie it to curvature, effective resistance and commute time.
- **The 2026 unification** [R3]. Both phenomena have Transformer counterparts: **rank collapse** (attention makes token representations collapse) and **representational collapse** (in decoder-only models, distinct sequences map to near-identical final-token states). Self-attention is a learned adjacency, so one set of tools covers both GNNs and LLMs, including residual scaling, normalization, rewiring and attention sparsity.
- **Myth-busting** [G1]. Arnaiz-Rodriguez & Errica collect formal counterexamples to common overgeneralizations, for example that over-smoothing always hurts, that heterophily implies GNNs fail, and that over-squashing and long-range dependence are the same thing. Their point is that these are *conditional* phenomena and papers should state the conditions.
- **Short-range over-squashing** [G6]: bottlenecks also matter for near neighbors, not only long-range ones.
- **The recurrent connection** [G7]. Deep GNNs share vanishing-gradient dynamics with RNNs. Stability analysis (contractive, edge-of-chaos) connects directly to the echo state property in reservoir computing (see [`../reservoir-computing/03-theory.md`](../reservoir-computing/03-theory.md)).

## 4. Unification of architectures

The common layer equation [G2] is partly a theoretical tool. It separates *propagation* (where) from *message* (what), so results about one component (for example spectral properties of the propagation bank and over-smoothing) transfer across all architectures that share it.

## 5. Optimization of equivariant networks

This used to be a gap and now has its first results.

- **Learning-rate pathology** [E4]. Parameter sharing across the 2ℓ+1 components of an irrep block makes the effective Adam step size depend on block structure. Blocks of different degrees then train at inconsistent rates. Block-level normalization of updates fixes this, and orthogonalized optimizers (Muon) get it for free.
- **Compute-optimal scaling** [E1]. Equivariant and non-equivariant models follow different power laws, and the compute-optimal model-size versus training-duration split differs between them. Scaling recipes from LLMs therefore do not transfer unchanged.

## 6. Symmetry: hard constraints vs learned

The theoretical case for equivariance rests on sample-complexity gains roughly proportional to group size, and on guaranteed out-of-distribution behavior under the group action. Recent work refines this:

- augmentation is equivalent to orbit-averaging the loss, and a Fourier analysis of augmentation clarifies which frequencies it regularizes [E9]
- Bayesian treatments compare the two [E8]
- learned or relaxed equivariance can recover most of the benefit when an explicit equivariance objective is optimized [E2, E6, E7]

What remains open is a theory of *when* a soft symmetry is preferable, especially when the true symmetry is broken, as with external fields, chirality or surfaces.

## 7. Representation convergence

The "Platonic representation" result for MLIPs [S6] shows that models with different architectures and constraints learn latent spaces that are equivalent up to a transformation fit via atomic anchors. Deviations from the shared geometry predict failures. This mirrors the Platonic representation hypothesis for vision and language models and suggests the **data/physics, not the architecture, determines the learned representation** at scale.
