# Annotated Bibliography: Categorical Deep Learning

Compiled 2026-10-01. Weighted toward 2025–26, with the foundational 2017–2024 papers the area is built on.
"PDF" means the file is in [`papers/`](papers/). Items marked † were also read in part (introduction, conclusions, key results); the rest are summarized from abstracts.

Tags: `[review]` · `[position]` · `[found]` foundations · `[arch]` architecture theory · `[eq]` equivariance/symmetry · `[sys]` systems/implementation · `[interp]` interpretability · `[lang]` language/LLMs · `[emp]` empirical

---

## Surveys, position papers and theses

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| R1 | † Gavranović, Lessard, Dudzik, von Glehn, Araújo, Veličković — *Position: Categorical Deep Learning is an Algebraic Theory of All Architectures*. The founding CDL paper. It models architectures as **algebras (and coalgebras) of monads/endofunctors valued in the 2-category Para**. This recovers GDL's equivariance constraints as monad-algebra homomorphisms and also covers non-invertible structure (lists → folding RNNs, trees → recursive NNs, Mealy machines → full RNNs). It argues that neither top-down GDL nor bottom-up autodiff frameworks alone can bridge specification and implementation. | ICML 2024 (arXiv 2402.15332) | position, arch | [pdf](papers/arXiv-2402.15332.pdf) |
| R2 | Gavranović — *Fundamental Components of Deep Learning: A category-theoretic approach* (PhD thesis, Strathclyde). Para, lenses/optics, weight tying and batching as Para morphisms, and the foundations of R1. | arXiv 2403.13001, 2024 | found | [pdf](papers/arXiv-2403.13001.pdf) |
| R3 | Shiebler, Gavranović, Wilson — *Category Theory in Machine Learning*. The first survey, covering gradient-based learning, probability, invariance and equivariance. | ACT 2021 (arXiv 2106.07032) | review | [pdf](papers/arXiv-2106.07032.pdf) |
| R4 | Crescenzi — *Towards a Categorical Foundation of Deep Learning: A Survey*. Covers optics for gradient-based learning, categorical algebras and integral transforms (GNNs ↔ algorithms), functors across abstraction levels, and string diagrams for architectures. | arXiv 2410.05353, Oct 2024 | review | [pdf](papers/arXiv-2410.05353.pdf) |
| R5 | Jia, Peng, Yang, Chen — *Category-Theoretical and Topos-Theoretical Frameworks in Machine Learning: A Survey*. Four strands: gradient-based, probabilistic, invariance/equivalence, and (newly surveyed) topos-based learning. | Axioms 14(3):204, 2025 (arXiv 2408.14014) | review | [pdf](papers/arXiv-2408.14014.pdf) |
| R6 | de los Riscos, Corbacho, Arbib — *Towards a Category-theoretic Comparative Framework for AGI* (working paper). Categorical formulations of RL, Universal AI, active inference and schema-based learning for comparing agent architectures. | arXiv 2603.28906, Mar–Jul 2026 | position | [pdf](papers/arXiv-2603.28906.pdf) |
| R7 | Gavranović — *Category_Theory_Machine_Learning* (curated paper list) | GitHub, living | review | [link](https://github.com/bgavran/Category_Theory_Machine_Learning) |

## Foundations: learning as composition (lenses, optics, Para)

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| F1 | Fong, Spivak, Tuyéras — *Backprop as Functor: A compositional perspective on supervised learning*. Learners form a symmetric monoidal category, and gradient descent with backprop is a functor into it. | LICS 2019 (arXiv 1711.10455) | found | [pdf](papers/arXiv-1711.10455.pdf) |
| F2 | Cruttwell, Gavranović, Ghani, Wilson, Zanasi — *Categorical Foundations of Gradient-Based Learning*. **Parametric lenses** plus reverse-derivative categories. Covers Adam, AdaGrad, Nesterov and MSE/softmax-CE losses uniformly, and extends to Boolean and polynomial circuits. | ESOP 2022 (arXiv 2103.01931) | found | [pdf](papers/arXiv-2103.01931.pdf) |
| F3 | Cruttwell, Gavranović, Ghani, Wilson, Zanasi — *Deep Learning with Parametric Lenses*. Extended journal version with a Python implementation; its MNIST results are comparable to standard tools. | arXiv 2404.00408, 2024 | found, sys | [pdf](papers/arXiv-2404.00408.pdf) |
| F4 | Hedges, Rodríguez Sakamoto — *Reinforcement Learning in Categorical Cybernetics*. Bellman operators and major RL algorithms as parametrised optics. | EPTCS 429, 2025 (arXiv 2404.02688) | found | [pdf](papers/arXiv-2404.02688.pdf) |
| F5 | Capucci, Gavranović, Hedges, Rischel — *Towards Foundations of Categorical Cybernetics* | ACT 2021 (arXiv 2105.06332) | found | [link](https://arxiv.org/abs/2105.06332) |
| F6 | Pugh, Grundy, Cirstea, Harris — *Presenting Neural Networks via Coherent Functors*. Dense feed-forward architectures (over floats) as coherent categories whose Set-models are the networks. Inference is precomposition along a coherent functor. Weight fixing and tying (sparse, conv) via 2-coequalizers. Architectures read as *hypotheses about data structure*. | arXiv 2604.15100 (math.CT), Apr 2026 | found, arch | [pdf](papers/arXiv-2604.15100.pdf) |
| F7 | Ramírez Ovalle — *From Categorized Neural Architectures to Subexponential Proof Theory*. Extracts a resource-sensitive (tensorial) sequent calculus from a categorized architecture. | arXiv 2603.28946, Mar 2026 | found | [pdf](papers/arXiv-2603.28946.pdf) |

## Architecture theory: algebras, monads, functors

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| A1 | Dudzik, Veličković — *Graph Neural Networks are Dynamic Programmers*. GNNs and DP share an **integral transform** (pullback → aggregate in a commutative monoid → pushforward), via polynomial functors. Motivates aligning aggregators with semirings such as tropical (min,+). | NeurIPS 2022 (arXiv 2203.15544) | arch | [pdf](papers/arXiv-2203.15544.pdf) |
| A2 | Dudzik, von Glehn, Pascanu, Veličković — *Asynchronous Algorithmic Alignment with Cocycles*. Message functions that satisfy cocycle conditions make GNN updates invariant to asynchronous execution. | LoG 2023 (arXiv 2306.15632) | arch | [pdf](papers/arXiv-2306.15632.pdf) |
| A3 | Ong, Veličković — *Learnable Commutative Monoids for Graph Neural Networks*. Learnable associative-commutative aggregators (O(log n)-depth trees) between sum/max and RNN aggregation. | LoG 2022 (arXiv 2212.08541) | arch | [pdf](papers/arXiv-2212.08541.pdf) |
| A4 | Gavranović, Villani — *Graph Convolutional Neural Networks as Parametric CoKleisli morphisms*. GCNNs factor through Para and Lens over the CoKleisli category of the product comonad; the adjacency becomes a global rather than per-layer parameter. | arXiv 2212.00542, 2022 | arch | [pdf](papers/arXiv-2212.00542.pdf) |
| A5 | O'Neill — *Self-Attention as a Parametric Endofunctor*. Q/K/V maps as a parametric 1-morphism in Para(Vect). Stacked attention is a **free monad**, and positional encodings are monoid actions. Linear parts only: softmax and layer norm are deferred. | arXiv 2501.02931, Jan 2025 | arch | [pdf](papers/arXiv-2501.02931.pdf) |
| A6 | Villani, McBurney — *The Topos of Transformer Networks*. Transformers inhabit a topos completion (higher-order logic), whereas CNNs/RNNs sit in a pretopos. | arXiv 2403.18415, 2024 | arch | [pdf](papers/arXiv-2403.18415.pdf) |
| A7 | Hashemi, Pasque, Teska, Yoshida — *Tropical Attention: Neural Algorithmic Reasoning for Combinatorial Algorithms*. Attention in the tropical (max-plus) semiring as an algebraic-geometric inductive bias for DP-style combinatorial algorithms; aims at sharper, more robust OOD generalization. | arXiv 2505.17190, 2025 | arch, emp | [pdf](papers/arXiv-2505.17190.pdf) |

## Equivariance beyond groups

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| E1 | † Maruyama — *Categorical Equivariant Deep Learning: Category-Equivariant Neural Networks and Universal Approximation Theorems*. Equivariance as **naturality** in topological categories with Radon measures. Proves finite-depth CENNs are dense in continuous equivariant maps. Instantiated for groups/groupoids, posets/lattices, graphs and cellular sheaves; monoids cover irreversible and causal transformations. | arXiv 2511.18417, Nov–Dec 2025 | eq, arch | [pdf](papers/arXiv-2511.18417.pdf) |
| E2 | Hajij, Bastian, …, Papillon et al. — *Copresheaf Topological Neural Networks: A Generalized Deep Learning Framework*. Copresheaves on combinatorial complexes: per-region feature spaces with learnable transport maps. Formally covers GNNs, Transformers, sheaf NNs and TNNs. | NeurIPS 2025 (arXiv 2505.21251) | eq, arch | [pdf](papers/arXiv-2505.21251.pdf) |
| E3 | † Olejniczak, Dimitrov, Huang, Cuenca Grau, Kim, Ceylan — *What are the Right Symmetries for Formal Theorem Proving?* Introduces **rewriting categories**: non-invertible, compositional rewrites induced by tactics. Defines *proof equivariance* and *success invariance*. Shows that state-of-the-art LLM provers violate both; for example, DeepSeek-Prover-V2 success drops from 50% to 4.7% on equivalent statements. Test-time aggregation over equivalent rewritings restores invariance in the limit and improves accuracy at fixed budget. | arXiv 2605.22257, May 2026 | eq, lang, emp | [pdf](papers/arXiv-2605.22257.pdf) |
| E4 | † Ông — *No Equivariant Architecture Covers All Equivariant Attention*. The equivariance locus of multi-head self-attention splits into many Zariski-irreducible components, and any fixed polynomially parametrized architecture covers at most one, so constrained architectures lose expressivity. Ω(C⁶⁴) components for D₄ with 8 heads. | arXiv 2608.30417, Aug 2026 | eq | [pdf](papers/arXiv-2608.30417.pdf) |

## Sheaf neural networks (applied category / topology)

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| S1 | Bodnar, Di Giovanni, Chamberlain, Liò, Bronstein — *Neural Sheaf Diffusion* (background) | NeurIPS 2022 | arch | [link](https://arxiv.org/abs/2202.04579) |
| S2 | † Fiorini, Coppola, Liò — *Benchmarking Sheaf Neural Networks for Inductive Tasks*. The first systematic benchmark: 1,890 runs on 14 inductive datasets. Findings: restriction maps are the dominant choice and general maps are best. Larger stalks add capacity, not reach. Generic architectural components explain more variance than sheaf design. **SNNs transfer but underperform the strongest baselines.** | arXiv 2608.02558, Aug 2026 | emp | [pdf](papers/arXiv-2608.02558.pdf) |
| S3 | Borgi, Severino, Silvestri, Liò — *Equivariant Sheaf Neural Networks: Learning Geometric Transport on Graphs*. Matrix-valued E(n)-equivariant edge transport instead of higher-order irreps, with controlled symmetry relaxation. | arXiv 2608.28853, Aug–Sep 2026 | eq, arch | [pdf](papers/arXiv-2608.28853.pdf) |
| S4 | *Sheaf Neural Networks on SPD Manifolds*. SPD-valued sheaves are strictly more expressive than Euclidean ones. | arXiv 2604.20308, Apr 2026 | arch | [pdf](papers/arXiv-2604.20308.pdf) |
| S5 | Naddeo, Abate, Liò, Toschi, Bianchi — *Hierarchical Pooling for Sheaf Neural Networks (HiSP)* | arXiv 2606.20932, 2026 | arch | [link](https://arxiv.org/abs/2606.20932) |
| S6 | Ribeiro et al. — *Gaussian Sheaf Neural Networks* | arXiv 2605.21435, 2026 | arch | [link](https://arxiv.org/abs/2605.21435) |

## Diagrams, systems and implementation

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| D1 | † Abbott, Zardini — *Weaves, Wires, and Morphisms: Formalizing and Implementing the Algebra of Deep Learning*. Axis-stride and array-broadcasted categories formalize broadcasting. Ships **pyncd / tsncd** with algebraic construction, graph conversion, PyTorch compilation and diagram rendering. | TMLR 08/2026 (arXiv 2604.07242) | sys | [pdf](papers/arXiv-2604.07242.pdf) |
| D2 | Abbott, Zardini — *FlashAttention on a Napkin: A Diagrammatic Approach to Deep Learning IO-Awareness*. Neural circuit diagrams extended with GPU memory hierarchy. Derives FlashAttention and its performance model diagrammatically. | TMLR 03/2025 (arXiv 2412.03317) | sys | [pdf](papers/arXiv-2412.03317.pdf) |
| D3 | Abbott — *Neural Circuit Diagrams: Robust Diagrams for the Communication, Implementation, and Analysis of Deep Learning Architectures* | TMLR 2024 (arXiv 2402.05424) | sys | [pdf](papers/arXiv-2402.05424.pdf) |
| D4 | Wang-Maścianica, Khatri — *Graphical einops: bridging tensor networks and computation graphs*. A proof-enabling graphical calculus for einops-style tensor programs. Grade-naturality turns equivariance proofs into diagram rewrites and attention masks into preprocessing (efficient sparse attention). | arXiv 2605.31485, May 2026 | sys, eq | [pdf](papers/arXiv-2605.31485.pdf) |
| D5 | *Accelerating Machine Learning Systems via Category Theory: Applications to Spherical Attention for Gene Regulatory Networks* | Springer LNCS, 2025 | sys | [link](https://link.springer.com/chapter/10.1007/978-3-032-00686-8_1) |

## Interpretability, language and reasoning

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| L1 | † Gauderis, Dooms, Homer, Ayonrinde, Wiggins — *From Mechanistic to Compositional Interpretability*. A category-theoretic framework in which an interpretation is a commuting syntactic/semantic pair, built on compositionality and minimum description length. Introduces **compressive refinement** and a parsimony criterion under which compression guarantees better explanations. | arXiv 2605.08934, May–Jun 2026 | interp | [pdf](papers/arXiv-2605.08934.pdf) |
| L2 | Bradley, Vigneaux — *The magnitude of categories of texts enriched by language models*. [0,1]-enriched categories of text built from LLM next-token probabilities; their magnitude relates to entropy. | Theory Appl. Categ. 44 (2025) (arXiv 2501.06662) | lang | [pdf](papers/arXiv-2501.06662.pdf) |
| L3 | Bradley, Terilla, Vlassopoulos — *An Enriched Category Theory of Language: From Syntax to Semantics* | La Matematica, 2022 | lang | [link](https://link.springer.com/article/10.1007/s44007-022-00021-2) |
| L4 | *Categorical Homotopy Theory for Large Language Models* | arXiv 2508.10018, 2025 | lang | [link](https://arxiv.org/abs/2508.10018) |
| L5 | Floridi, Jia, Tohmé — *A Categorical Analysis of LLMs and Why LLMs Circumvent the Symbol Grounding Problem* | arXiv 2512.09117, Dec 2025 | lang | [link](https://arxiv.org/abs/2512.09117) |
| L6 | Waseem — *String Diagrams for Quantum Foundations, Computing and NLP* (DisCoCat/DisCoCirc lineage) | arXiv 2605.11417, 2026 | lang | [link](https://arxiv.org/abs/2605.11417) |

## Community and industry context

| # | Item | Date | PDF |
|---|---|---|---|
| C1 | Baez — *Category Theorists in AI* (Azimuth / n-Category Café). Covers Symbolica's pivot to CDL after R1, the $31M Series A, and the subsequent internal conflict and departures of category theorists, including Gavranović. | Feb 2025 | [link](https://johncarlosbaez.wordpress.com/2025/02/08/category-theorists-in-ai/) |
| C2 | Applied Category Theory 2026 (ACT 2026), Tallinn, 6–10 July 2026 | 2026 | [link](https://actconf2026.github.io/) |
| C3 | Symbolica AI (company site) | living | [link](https://www.symbolica.ai/) |
