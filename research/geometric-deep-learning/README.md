# Geometric Deep Learning: Research Digest (Oct 2026)

A literature digest of the latest geometric deep learning (GDL) research: equivariant networks, GNNs and graph transformers, graph and relational foundation models, topological deep learning, and the scientific applications (MLIPs, proteins, weather). It is weighted toward 2026, with key 2025 work and foundational papers for context.

## Contents

| File | What's in it |
|---|---|
| [01-state-of-the-field-2026.md](01-state-of-the-field-2026.md) | **Start here.** The one-paragraph version, five 2025–26 storylines, maturity by application area |
| [02-architectures.md](02-architectures.md) | The 5G blueprint, the common GNN layer equation, graph transformers, equivariant 3D networks (EquiformerV3, NequIP/Allegro, DPA4C), GFMs and PFNs, relational DL, TDL, weather and protein architectures |
| [03-theory.md](03-theory.md) | Expressivity (WL, uniform), Rademacher generalization, over-smoothing and over-squashing ↔ Transformer rank collapse, optimizing equivariant nets, hard vs learned symmetry, Platonic representations |
| [04-applications.md](04-applications.md) | Foundation MLIPs and the six open questions, protein design (La-Proteina, Genie 3), weather (AIFS, GraphCast lineage), relational databases, combinatorial optimization |
| [05-benchmarks-and-evidence.md](05-benchmarks-and-evidence.md) | **Meta-analysis status** (there is none), equivariance-vs-augmentation evidence table, fair GFM evaluation, the benchmark-crisis claims checked against the evidence, MLIP evaluation, reading caveats |
| [06-open-problems-and-directions.md](06-open-problems-and-directions.md) | Nine open problems, directions to watch, practical recommendations |
| [bibliography.md](bibliography.md) | Annotated bibliography (about 60 entries) with IDs used throughout (R, G, F, E, S) |
| [papers/](papers/) | 29 open-access PDFs (arXiv preprints and one bioRxiv preprint) |

## Method and caveats

- Sources were found through web search on arXiv, OpenReview, bioRxiv, Nature MI, ACM, TMLR, ECMWF and the Matbench Discovery leaderboard. Searched 2026-10-01.
- Summaries are based on abstracts. Items marked † in the bibliography were also read in part (conclusions and results): the benchmark position paper, equivariance at scale, the fair GFM evaluation, and the six MLIP questions.
- **Many 2026 items are preprints** (DPA4C, NequIP/Allegro FMs, Equivariance Breaks the LR, KumoRFM-2, the common layer equation). Check for published versions.
- Paywalled or bot-protected items (ACM graph-transformer survey, the Nature MI version of the Platonic MLIPs paper, OpenReview pages) are linked but were not downloaded. Arxiv versions are used where they exist.
- **No formal quantitative meta-analysis of GDL exists.** [05](05-benchmarks-and-evidence.md) collects the closest substitutes.

## Key reviews to read in full

1. Bronstein et al., *Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges* (2021), the foundational text: [`papers/arXiv-2104.13478.pdf`](papers/arXiv-2104.13478.pdf)
2. Sáez de Ocáriz Borde & Bronstein, *Mathematical Foundations of Geometric Deep Learning* (2025): [`papers/arXiv-2508.02723.pdf`](papers/arXiv-2508.02723.pdf)
3. Bechler-Speicher et al., *Position: Graph Learning Will Lose Relevance Due To Poor Benchmarks* (ICML 2025): [`papers/arXiv-2502.14546.pdf`](papers/arXiv-2502.14546.pdf)
4. Creed et al., *Six Open Questions in MLIP Foundation Models* (2026): [`papers/arXiv-2606.07327.pdf`](papers/arXiv-2606.07327.pdf)
5. Brehmer et al., *Does equivariance matter at scale?* (TMLR 2025): [`papers/arXiv-2410.23179.pdf`](papers/arXiv-2410.23179.pdf)
6. Platonov et al., *A Fair Evaluation of Graph Foundation Models for Node Property Prediction* (2026): [`papers/arXiv-2606.24509.pdf`](papers/arXiv-2606.24509.pdf)
7. Wang et al., *Graph Foundation Models: A Comprehensive Survey* (2025): [`papers/arXiv-2505.15116.pdf`](papers/arXiv-2505.15116.pdf)
