# 02 · Frameworks and Architectures

CDL works at three levels:

1. **How learning composes**: lenses, optics and Para.
2. **What architectures are**: algebras, monads, functors and sheaves.
3. **How architectures are written and compiled**: string diagrams and formal tensor calculi.

This document gives a working vocabulary for each. Section 4 is a cheat-sheet.

## 1. Learning as composition

### Para: parametrised maps

A morphism `A → B` in **Para(C)** is a pair `(P, f : P ⊗ A → B)`: a map with an explicit parameter object. Composition takes the tensor product of the parameter spaces. Para is a **2-category**: reparametrisations `P → Q` are 2-cells. This is what lets CDL state **weight tying** and **batching** precisely, as reparametrisations through copy maps [R2].

### Lenses and optics: forward and backward passes

A lens pairs a forward map `A → B` with a backward map `A × B' → A'`. Backprop is lens composition, which is the chain rule made compositional [F1, F2].

**Parametric lenses** (Para of Lens over a reverse-derivative category) model a learner. They have three interfaces: inputs, outputs and parameters [F2, F3]. The following plug into the same algebra:

- optimizers (SGD, momentum, Nesterov, Adam, AdaGrad), as lenses on the parameter port
- losses (MSE, softmax cross-entropy)
- learning rates

The construction works over any reverse-derivative category, including **Boolean and polynomial circuits**, so "gradient-based learning" is not tied to ℝ [F2].

### Categorical cybernetics

The same optics describe agents and games. RL algorithms (value iteration, Q-learning, Bellman operators) become parametrised optics [F4, F5].

### Coherent-logic view (2026)

Pugh et al. [F6] treat an architecture as a **coherent theory**. Its Set-models are the concrete networks, inference is precomposition along a coherent functor, and weight tying and sparsity come from 2-coequalizers. The slogan is that an architecture is a *hypothesis about the structure of the data*, and training lifts a dataset into a model of that theory. Ramírez Ovalle [F7] goes the other direction: he reads off a resource-sensitive logic (what may be copied or discarded) from a categorized architecture.

## 2. Architectures as algebra

### Monad algebras: the CDL position [R1]

- An **endofunctor algebra** `F(A) → A` describes how to *consume* a structure. Examples:
  - `1 + A × (−)` (lists) gives a fold, which is a **folding RNN** when the algebra map is parametric.
  - `A + (−)²` (binary trees) gives a **recursive / TreeRNN**.
- An **endofunctor coalgebra** `A → F(A)` describes how to *produce* a structure. `I → O × (−)` gives **Mealy machines**, the semantics of a full RNN cell with output.
- A **monad algebra homomorphism** is a structure-preserving map. For the monad induced by a group action, a homomorphism between algebras is exactly a **G-equivariant map**, which recovers GDL.
- Moving to **Para-valued** (2-categorical) algebras, and to **lax or oplax** variants where diagrams commute only up to a 2-cell, lets weight sharing and approximate structure be expressed.

The authors' reading of the title is: "Categorical Deep Learning is an Algebraic {Theory of All Architectures}". It is a single *language* in which constraints and implementations meet, not a claim of one algebraic theory per architecture.

### Integral transforms and algorithmic alignment

- **GNNs are dynamic programmers** [A1]. Both message passing and DP factor as *pullback → aggregate in a commutative monoid → pushforward* (a polynomial-functor integral transform). This suggests choosing aggregators that match the target algorithm's semiring, for example tropical (min, +) for shortest paths. Tropical Attention [A7] pursues this for attention.
- **Cocycles** [A2]: message functions satisfying a cocycle condition make GNN updates invariant to asynchronous or partial execution.
- **Learnable commutative monoids** [A3]: aggregators that are associative and commutative by construction, sitting between fixed sum/max and expressive but order-dependent RNN aggregators.
- **GCNs as parametric CoKleisli morphisms** [A4]: the adjacency matrix becomes a global context (comonad) rather than a per-layer input.

### Transformers

- Self-attention as a parametric endofunctor in Para(Vect). Stacking layers builds a **free monad**, and positional encodings are monoid actions [A5]. This covers the linear parts only; softmax and LayerNorm are left open.
- The "topos of transformers" [A6] argues that attention's input-dependent weights put Transformers in a topos completion (higher-order logic), whereas CNNs and RNNs sit in a pretopos (first-order).

### Equivariance as naturality

- **CENNs** [E1]: data are functors from a category (of symmetries, relations or contexts) to feature spaces, and layers are **natural transformations**. Groups give GCNNs. Monoids give causal or irreversible structure. Posets and lattices give hierarchy. Graphs give message passing. Sheaves give local-to-global consistency.
- **Copresheaf TNNs** [E2]: each cell of a combinatorial complex gets its own feature space (stalk), with learnable maps along incidences. GNNs, Transformers, sheaf NNs and TNNs are special cases.
- **Rewriting categories** [E3]: morphisms are non-invertible rewrites (proof tactics). This defines *proof equivariance* and *success invariance* for reasoning systems.

### Sheaf neural networks

These replace scalar edge weights with learnable **restriction maps** between node stalks. Diffusion follows the sheaf Laplacian, which can handle heterophily and over-smoothing [S1]. 2026 variants include:

- SPD-valued stalks, which are strictly more expressive [S4]
- E(n)-equivariant matrix-valued transport, which is cheaper than higher-order irreps [S3]
- hierarchical pooling [S5]
- Gaussian sheaves [S6]

## 3. Diagrams and implementation

| Tool | What it does | Ref |
|---|---|---|
| Neural circuit diagrams | Rigorous string-diagram notation with explicit axes for architectures | [D3] |
| FlashAttention on a Napkin | Adds GPU memory hierarchy to diagrams; derives FlashAttention and its IO cost model | [D2] |
| Weaves, Wires, Morphisms (pyncd/tsncd) | Category of broadcasted arrays; algebraic construction → graph → **PyTorch compilation** and rendering | [D1] |
| Graphical einops | Graded-tube calculus for einops; diagrammatic equivariance proofs; masks → preprocessing for sparse attention | [D4] |
| Parametric-lens library | Python implementation of [F2] (MNIST parity with standard tools) | [F3] |

## 4. Cheat-sheet: deep learning concept ↔ categorical concept

| Deep learning | Category theory |
|---|---|
| Layer with weights | Morphism in Para |
| Weight tying, batching | Reparametrisation (2-cell) through copy maps |
| Backprop / chain rule | Lens composition; reverse-derivative category |
| Optimizer | Lens on the parameter port |
| Equivariant layer | Monad-algebra homomorphism; natural transformation |
| Folding RNN / TreeRNN | Endofunctor algebra (fold) |
| Full RNN / automaton | Endofunctor coalgebra (unfold) |
| GNN aggregation | Commutative monoid; integral transform |
| Stacked attention | Free monad on an endofunctor |
| Sheaf NN | Cellular sheaf / copresheaf on a complex |
| Architecture as hypothesis | Coherent theory; models = networks |
| Interpretation of a model | Commuting syntax/semantics square (functorial) |
