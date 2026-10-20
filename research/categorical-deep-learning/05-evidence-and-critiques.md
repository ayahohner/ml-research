# 05 · Evidence and Critiques

## Is there a meta-analysis?

**No.** No meta-analysis, systematic review with pooled effects, or shared benchmark exists for categorical deep learning as of October 2026. The field is overwhelmingly **theoretical and formal**:

- most papers prove a representation theorem or give a framework, not a benchmark result
- the four surveys [R3, R4, R5, R7] are narrative literature reviews
- the empirical evidence that exists is scattered across adjacent areas (sheaf NNs, algorithmic reasoning, theorem proving)

## 1. Evidence table

| Claim | Evidence | Strength |
|---|---|---|
| Lenses/optics give a faithful, implementable semantics of gradient learning | Library reaches MNIST parity with standard tools [F3] | ✅ Shown, small scale |
| Categorical formalisms can compile to real frameworks and derive efficient kernels | pyncd → PyTorch [D1]; FlashAttention derived diagrammatically [D2]; sparse attention from graphical einops [D4] | ✅ Shown |
| Non-group symmetries matter for frontier models | LLM theorem-prover success varies 50% → 4.7% under equivalent rewrites; test-time symmetrization helps [E3] | ✅ Shown on one task family |
| Monad-algebra view subsumes GDL | Proved [R1] | ✅ Proved (descriptive) |
| Category-equivariant nets are universal approximators | Proved [E1] | ✅ Proved; no experiments |
| Hard-wired equivariant attention is too rigid | Proved for one MHSA layer [E4] | ✅ Proved (scope: single layer) |
| Algebraically aligned aggregators improve algorithmic reasoning | Improvements on CLRS-style and DP tasks [A1–A3, A7] | ◑ Moderate, task-specific |
| Sheaf NNs beat GNNs | Transductive heterophily gains [S1]; **inductive benchmark: SNNs trail the strongest baselines; generic components matter more than sheaf design** [S2] | ◑ Mixed / ✗ inductively |
| Copresheaf TNNs beat baselines | Reported gains on hierarchical and local tasks [E2] | ◑ Single paper |
| CDL yields *new* architectures that beat the state of the art at scale | None published | ✗ Not shown |
| CDL-based structured models need less data and compute | Commercial claim [C3]; no public results | ✗ Not shown |

## 2. Critiques

1. **Descriptive vs generative.** The most common criticism is that CDL *re-describes* existing architectures elegantly but has not yet *produced* an architecture that practitioners adopt because of the theory. GDL earned its standing through CNN/GNN/e3nn recipes and science applications. CDL has no equivalent success yet. Its 2026 compilers [D1] are the first step toward one.
2. **Abstraction cost.** Category theory has a steep learning curve, and mainstream frameworks (PyTorch, JAX) do not expose categorical structure [R4, R5]. This limits who can contribute and slows the feedback loop with experiments.
3. **Missing pieces of the model.** Many treatments cover linear layers and composition but leave out softmax, normalization and gating [A5], or say nothing about generalization and optimization (see [03-theory.md](03-theory.md)).
4. **Rigidity vs learned structure.** The 2026 GDL evidence shows learned symmetry often rivals hard-wired symmetry at scale. [E4] proves that fixed equivariant attention architectures lose expressivity. This cuts against any program whose main output is *more* hard constraints. CDL's best answer is the lax/approximate algebra direction [R1] and test-time symmetrization [E3], neither of which is yet developed quantitatively.
5. **Sociology and hype.** The Symbolica episode [C1] showed the risk of over-promising: a position paper turned into a funding narrative, then internal disagreement and departures. Commentators in the community stress that compelling, *predictive* categorical theories of learning remain scarce.

## 3. Reading CDL papers: a checklist

- Is the result **descriptive** (X can be expressed as Y) or **constructive/predictive** (do Y and you get a better or verifiably correct X)?
- Does the formalism handle the **nonlinear** and **normalization** parts of the architecture?
- Are there **experiments**, and do they compare against **tuned** baselines? (See the GDL lessons in [`../geometric-deep-learning/05-benchmarks-and-evidence.md`](../geometric-deep-learning/05-benchmarks-and-evidence.md).)
- Is there **code** that compiles to a standard framework?
- For symmetry claims: is the symmetry **exact** in the data, or only approximate?
