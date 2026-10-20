# 04 · Applications and Tooling

CDL's applications in 2026 fall into five areas. They are ordered here by how close each is to practical use.

## 1. Architecture engineering and compilation (most practical)

- **pyncd / tsncd** [D1] (TMLR 08/2026). You write an architecture as a categorical expression over broadcasted arrays, then the tool:
  - converts it to a computation graph
  - compiles it to PyTorch
  - renders a diagram

  The goal is that equivalent formulations, efficient kernels and performance models become *derivable* rather than hand-engineered.
- **IO-aware derivations** [D2]. Neural circuit diagrams with GPU memory levels derive FlashAttention and its transfer-cost model in a few diagrammatic steps. The paper also sketches derivations for matmul and other fused kernels.
- **Graphical einops** [D4]. A proof-enabling diagram calculus for einops-style programs. Practical results: equivariance proofs become diagram rewrites, and attention masks become preprocessing, which yields efficient sparse-attention implementations.
- **Category theory for ML systems** [D5]. Category-guided acceleration of spherical attention for gene regulatory networks.

**Assessment.** This is where CDL most clearly pays off today. It turns informal architecture descriptions into formal objects that can be manipulated, verified and compiled.

## 2. Symmetry for LLM reasoning

**Theorem proving** [E3]. LLM provers solve the same theorem at very different rates depending on surface form. Examples on DeepSeek-Prover-V2 include gcd argument order (98% vs 69%) and algebraic rephrasing (50% vs 4.7%).

- Rewriting categories formalize which rewrites should not matter.
- Test-time aggregation over equivalent rewritings improves robustness *and* accuracy at a fixed inference budget.
- This is a concrete case of a **non-group symmetry** (rewrites are not invertible in general) that gives an empirical gain for frontier-style models.

## 3. Interpretability

- **Compositional interpretability** [L1]. A category-theoretic definition of what it means for an explanation to be faithful (a commuting square between model syntax and behavior) and *simple* (minimum description length). Compressive refinement generalizes current mechanistic decomposition methods. Planned next steps include tensor-network implementations and integration with causal methods.
- **Enriched categories of text** [L2, L3]. LLM probabilities enrich a category of strings. Magnitude and Yoneda-style constructions give semantics-from-statistics invariants.
- **Formal analyses of LLMs**: symbol grounding [L5], homotopy-theoretic views [L4] and DisCoCirc-style compositional NLP [L6]. These are mostly conceptual.

## 4. Algorithmic reasoning

The GNN-as-DP perspective [A1] and its follow-ups (cocycles [A2], learnable monoids [A3], tropical attention [A7]) are CDL's main contribution to **neural algorithmic reasoning**. The design principle is to match the network's aggregation algebra to the algorithm's algebra. It has shaped how this community chooses aggregators and attention semirings. It is a real but niche impact.

## 5. Graph and topological learning

- **Sheaf NNs** [S1–S6]: used for heterophilous graphs, biomedical graphs and geometric transport [S3]. The 2026 inductive benchmark [S2] shows that they transfer but trail the strongest tuned baselines.
- **Copresheaf TNNs** [E2]: a unifying framework with reported gains on tasks that need hierarchical or local sensitivity (NeurIPS 2025).
- **CENNs** [E1]: a design template for poset, lattice or sheaf-structured data (ontologies, taxonomies, local-to-global fields). Experiments are not yet reported.

## 6. Agents and RL

Categorical cybernetics [F4, F5] gives a compositional semantics for RL and game theory as parametrised optics. It is useful for building correct-by-construction compositional agent systems, and research implementations exist (for example the open-games engine). Adoption in mainstream RL is minimal.

## Industry

- **Symbolica AI** [C1, C3] raised about $31M after the 2024 position paper and positioned itself as a CDL company building "structured reasoning" models. In early 2025 the founder reportedly preferred a different (hypergraph) direction, and several category theorists left, including the paper's lead author [C1]. As of Oct 2026 there are no public large-scale CDL model results.
- Other pockets: Google DeepMind (algorithmic reasoning; the R1 co-authors), the Topos Institute and the ACT community [C2], Glasgow (AI verification), UCL/MIT (Abbott & Zardini, DARPA/AFOSR-funded [D1]), Oxford (Ceylan group [E3]) and Cambridge (Liò group, sheaves).
