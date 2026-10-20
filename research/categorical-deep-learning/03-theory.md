# 03 · Theory: Results and Claims

CDL is mostly a theory program. This document separates what has been **proved** from what has been **proposed**.

## 1. Proved results

| Result | Statement (informal) | Ref |
|---|---|---|
| Backprop is a functor | Gradient descent with backprop gives a monoidal functor from parametrised functions to learners | [F1] |
| Uniform semantics for gradient learning | Optimizers, losses and architectures are all parametric lenses over a reverse-derivative category, which also covers non-real domains (Boolean and polynomial circuits) | [F2, F3] |
| Equivariance = algebra homomorphism | For a group-action monad, monad-algebra homomorphisms are exactly G-equivariant maps. GDL embeds in CDL. | [R1] |
| RNN families as (co)algebras | Folding and recursive NNs are endofunctor algebras; full RNNs are Mealy-machine coalgebras | [R1] |
| GNN ↔ DP common structure | Both factor as integral transforms (pullback / monoid aggregate / pushforward) | [A1] |
| Asynchrony invariance | Cocycle conditions on messages give invariance to execution order | [A2] |
| GCNN factorization | A faithful 2-functor sends GCNNs into Para(CoKleisli(ℝⁿˣⁿ × −)) | [A4] |
| **Category-equivariant universal approximation** | Finite-depth CENNs are dense in continuous equivariant maps, for topological categories with Radon measures. Corollaries for groups, groupoids, posets, lattices, graphs and sheaves. | [E1] |
| **Equivariant attention has no universal architecture** | For L ≥ 3 tokens, G-equivariant MHSA requires G to act by head-cluster permutations with constraints on QK/OV. The equivariance locus has many Zariski-irreducible components, and any fixed polynomially parametrized architecture covers at most one (Ω(C⁶⁴) for D₄ with 8 heads). | [E4] |
| Networks as coherent theories | Any functorial database schema has a κ-coherent theory whose models are its instances. Dense, sparse and convolutional feed-forward nets fit this. | [F6] |
| Test-time symmetrization | Aggregating over equivalent rewritings recovers success invariance in the sampling limit | [E3] |
| Parsimony criterion | Under stated conditions, minimizing representation complexity provably gives better compositional explanations | [L1] |
| SPD sheaves are more expressive | SPD-valued sheaves admit consistent sections that vector-valued sheaves cannot represent | [S4] |

## 2. Claims and programs (not yet demonstrated)

- **"A theory of all architectures"** [R1]. The 2024 position gives a language general enough to describe all architectures, plus worked examples (RNNs, GNNs, GDL). It has not been shown to *derive new architectures that beat existing ones*. The paper itself frames this as a research program.
- **Structured, data-efficient models.** Symbolica's public pitch was that categorical structure lets models learn from less data and compute [C3]. No public evidence at scale exists as of Oct 2026.
- **Topos-theoretic learning** [R5, A6]. Gives descriptive results about where architectures "live" logically. No predictive consequences have been tested.
- **AGI comparison framework** [R6]. A working paper with categorical formulations of agent architectures and no empirical component.

## 3. Relationship to geometric deep learning theory

| Aspect | GDL | CDL |
|---|---|---|
| Symmetry object | Group G (invertible) | Category, monad, sheaf (non-invertible allowed) |
| Equivariant layer | Intertwiner of representations | Algebra homomorphism / natural transformation |
| Construction recipe | Solve the linear equivariance constraint (irreps, Clebsch–Gordan) | Not generally constructive. Solving naturality constraints for general categories has no e3nn-like toolkit except in special cases (sheaves, posets) |
| Universal approximation | Known for many groups | Generalized to categories [E1] |
| Expressivity limits | WL hierarchy etc. | Limits of fixed equivariant attention [E4] |
| Empirical base | Large (MLIPs, proteins, weather) | Small |

The key asymmetry is that GDL's success came from **constructive** recipes (CNNs, e3nn, PyG) that practitioners can implement. CDL has an elegant *descriptive* account, while its *constructive* pipelines are only beginning to appear [D1, D4].

## 4. Theoretical open questions

1. **Constructivity.** Given a monad or category, how do you automatically derive the space of equivariant (natural) parametric layers, as e3nn does for groups?
2. **Nonlinearities.** Softmax, LayerNorm and gating are often left out of categorical treatments [A5]. A compositional account of them is needed.
3. **Optimization and generalization.** Lenses describe *how* learning composes but do not predict *whether* it succeeds. Nothing connects CDL to generalization bounds or loss-landscape theory.
4. **Approximate and lax structure.** Lax algebras are proposed in [R1], and approximate equivariance is open in [E4]. Real data has *soft* symmetry, so a quantitative theory of laxness is needed.
5. **Depth.** [E4] covers one MHSA layer. Characterizing equivariance loci for full blocks or stacks is open.
