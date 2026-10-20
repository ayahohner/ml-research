# Categorical Deep Learning: Research Digest (Oct 2026)

A literature digest of categorical deep learning (CDL), meaning category theory applied to the specification, implementation and analysis of neural networks. Topics:

- learning as composition (lenses, optics, Para)
- architectures as monad/endofunctor algebras
- equivariance generalized beyond groups (categories, sheaves, rewriting categories)
- formal diagrams and compilers
- compositional interpretability

It is weighted toward 2025–26, with the foundational 2017–24 papers for context.

## Contents

| File | What's in it |
|---|---|
| [01-state-of-the-field-2026.md](01-state-of-the-field-2026.md) | **Start here.** The one-paragraph version, five 2025–26 storylines, maturity table |
| [02-frameworks-and-architectures.md](02-frameworks-and-architectures.md) | Para, lenses and optics; monad algebras (RNNs, GDL); integral transforms (GNN ↔ DP); attention as a free monad; CENNs, copresheaves, sheaf NNs; diagram tools; **DL ↔ CT cheat-sheet** |
| [03-theory.md](03-theory.md) | Proved results vs proposed programs; GDL vs CDL comparison; open theoretical questions |
| [04-applications-and-tooling.md](04-applications-and-tooling.md) | Architecture compilers (pyncd), IO-aware derivations, theorem-prover symmetries, interpretability, algorithmic reasoning, sheaves, RL, industry (Symbolica) |
| [05-evidence-and-critiques.md](05-evidence-and-critiques.md) | **Meta-analysis status** (there is none), evidence table with strength ratings, five critiques, a reading checklist |
| [06-open-problems-and-directions.md](06-open-problems-and-directions.md) | Eight open problems, directions to watch, practical recommendations and a reading order |
| [bibliography.md](bibliography.md) | Annotated bibliography (about 50 entries) with IDs (R, F, A, E, S, D, L, C) |
| [papers/](papers/) | 32 open-access arXiv PDFs |

## Method and caveats

- Sources were found through web search on arXiv, NeurIPS, ICML/PMLR, TMLR, Theory and Applications of Categories, the ACT community and the n-Category Café / Azimuth blogs. Searched 2026-10-01.
- Summaries are based on abstracts. Items marked † were also read in part: the CDL position paper, CENNs, Weaves/Wires/Morphisms, compositional interpretability, equivariant attention limits, theorem-proving symmetries and the sheaf benchmark.
- **CDL is a small, theory-heavy field.** "Latest research" means a few dozen papers per year, many of them preprints. Several 2026 items (CENNs, coherent functors, equivariant-attention limits) have a single author or have not been peer reviewed.
- Industry information (Symbolica) comes from public blog commentary [C1] and company pages, not from primary sources.
- **No meta-analysis of CDL exists.** See [05](05-evidence-and-critiques.md).

## Key papers to read in full

1. Gavranović et al., *Position: Categorical Deep Learning is an Algebraic Theory of All Architectures* (ICML 2024): [`papers/arXiv-2402.15332.pdf`](papers/arXiv-2402.15332.pdf)
2. Cruttwell et al., *Categorical Foundations of Gradient-Based Learning* (ESOP 2022): [`papers/arXiv-2103.01931.pdf`](papers/arXiv-2103.01931.pdf)
3. Crescenzi, *Towards a Categorical Foundation of Deep Learning: A Survey* (2024): [`papers/arXiv-2410.05353.pdf`](papers/arXiv-2410.05353.pdf)
4. Abbott & Zardini, *Weaves, Wires, and Morphisms* (TMLR 2026): [`papers/arXiv-2604.07242.pdf`](papers/arXiv-2604.07242.pdf)
5. Maruyama, *Categorical Equivariant Deep Learning* (2025): [`papers/arXiv-2511.18417.pdf`](papers/arXiv-2511.18417.pdf)
6. Olejniczak et al., *What are the Right Symmetries for Formal Theorem Proving?* (2026): [`papers/arXiv-2605.22257.pdf`](papers/arXiv-2605.22257.pdf)
7. Gavranović, *Fundamental Components of Deep Learning* (PhD thesis, 2024): [`papers/arXiv-2403.13001.pdf`](papers/arXiv-2403.13001.pdf)
