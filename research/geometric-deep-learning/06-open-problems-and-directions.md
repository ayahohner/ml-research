# 06 · Open Problems and Directions

## Open problems

1. **When to hard-wire symmetry.** We need a predictive theory, not just case studies, of when architectural equivariance beats learned or relaxed symmetry for a given data budget, compute budget, symmetry-breaking strength and need for out-of-distribution guarantees [E1, E2, E6].
2. **Efficient equivariance.** Tensor products, irrep bookkeeping and optimizer mismatch [E4] still tax equivariant models. Promising routes include block-diagonal or mirror decompositions [E5], kernel co-design [S3], SO(2)/eSCN-style convolutions, and optimizers aware of irrep structure.
3. **Graph foundation models that actually transfer.** Outside PFNs and relational models, GFMs do not yet beat tuned GNNs [F1]. Open questions:
   - What is the right synthetic prior?
   - How should GFMs handle heterogeneous feature spaces?
   - Is "foundation" even the right framing for node classification?
4. **Benchmarks that matter** [R7]. Shared, rigorous benchmarks are needed for combinatorial optimization, chip design, relational data at scale and scientific discovery, with protocols that enforce tuned baselines and compute matching.
5. **Structural generalization.** Models that saturate training distributions fail on refined or rescaled structures [G5]. Size and resolution generalization remains a core weakness.
6. **Long-range interactions.** These appear as over-squashing in graphs [R3, R6] and as electrostatics and dispersion in MLIPs [R9, Q3]. Graph rewiring, global attention and explicit physics (Ewald or latent charges) compete, and no approach is clearly best.
7. **MLIP validation and physics discovery** [R9, Q4, Q6]. How do we validate against experiment [S8]? Can MLIPs extrapolate to genuinely new chemistry? How should data quality and consistency (DFT functional mixing) be balanced against quantity [S2]?
8. **Theory that predicts practice.** Expressivity, generalization and optimization still need full integration [G3, R8]. Theory should explain why PFNs work on graphs and why equivariant optimization differs [E4].
9. **Topological deep learning's value proposition.** It needs tasks where higher-order structure demonstrably helps and that are not solvable by a GNN with the right input encoding [G5].

## Directions to watch (late 2026 → 2027)

- **PFN-ization of graph learning.** Synthetic-prior, in-context models (GraphPFN [F2], KumoRFM-2 [F3]) are likely to become the default baseline, much as TabPFN did for tabular data.
- **Learned symmetry at scale.** Contrastive and multitask equivariance objectives [E2, E6] may let generic Transformer stacks (and their hardware efficiency) take over molecular modeling. EquiformerV3 [S1] and Genie 3 [S10] show equivariant designs are not done yet.
- **Unified propagation theory for GNNs, Transformers and SSMs/RNNs** [R3, G7]. Over-squashing, rank collapse and vanishing gradients are increasingly treated as a single subject. This is a natural bridge to reservoir computing and state-space models (see [`../cross-topic-notes.md`](../cross-topic-notes.md)).
- **Representation auditing.** Platonic or shared latent geometries [S6] could become a standard diagnostic for scientific foundation models.
- **Billion-atom ML-MD** with equivariant kernels [S3] could make ML potentials faster than classical empirical potentials. That would change computational materials science.
- **Wet-lab-validated generative design** [S10, S11]. Evaluation is moving from in-silico metrics to experimental hit rates.

## Practical recommendations (Oct 2026)

| If you are… | Then… |
|---|---|
| Doing node or graph prediction on a new dataset | Start with a **tuned GNN** and **GraphPFN** (or TabPFN on node features plus structural encodings) before bespoke architectures [F1, F2] |
| Predicting on relational databases | Try a relational FM (KumoRFM-2, Relational Transformer) and evaluate on RelBench-style temporal splits [F3–F5] |
| Running atomistic simulation | Use a conservative foundation MLIP (UMA, EquiformerV3, NequIP/Allegro, MACE, PET) and fine-tune on your chemistry. Validate dynamic properties, not just energies [S1–S5] |
| Designing an equivariant model | Budget for throughput: block-diagonal irreps, eSCN-style convolutions, normalized or orthogonalized optimizers [E4, E5] |
| Choosing equivariant vs not | Small data or OOD guarantees → equivariant. Huge data with hardware-efficient training → unconstrained plus explicit symmetry objective. Compare at matched compute [E1, E2] |
| Evaluating anything | Tuned baselines, matched compute, structural-generalization splits, multiple seeds [R7, F1, G5] |
