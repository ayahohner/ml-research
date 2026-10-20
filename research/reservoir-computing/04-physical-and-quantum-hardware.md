# Physical, Biological and Quantum Reservoirs

IDs refer to [bibliography.md](bibliography.md).

RC is unusual among ML paradigms because **only the readout is trained**. Any physical system with a high-dimensional, nonlinear, fading-memory response can serve as the reservoir. This is why most RC research volume in 2025–26 is in hardware.

## Platform overview

| Platform | Maturity | Strengths | Main problems | Key 2025–26 sources |
|---|---|---|---|---|
| **Photonic** | Highest | GHz-or-faster dynamics; massive parallelism (wavelength, space, time); passive media | Weak or slow nonlinearities; propagation loss; optical power cost; fabrication variance; heuristic tuning | Thematic review [R1]; complex-network topology [H3]; NGRC photonic variants |
| **Memristive** | High, most active | CMOS-compatible; in-memory and in-sensor; intrinsic short-term memory; nanoscale | Device variability; drift; stability in heterogeneous integration | Reviews [R6, R7, R5]; NbOx nanoporous [H4]; all-optically controlled bipolar coding [H5]; branch prediction [H7] |
| **Spintronic** | Medium | Low power; MRAM-compatible; rich nonlinear magnetization dynamics | Noise; non-reproducibility | Programmable RC [H1]; ensemble STO [A7]; generalized RC with STOs [A6]; magnetic metamaterials [H6] |
| **Biological** (neuron cultures, organoids) | Early | Adaptive; self-organizing; extremely low power | Variability; short lifespan; drift; ethics | Chaos-controlled RC + knowledge transplant [H2]; Brainoware [H11] |
| **Quantum** | Early, growing fast | Large state space; natural dissipation; works on NISQ hardware | Finite shots; measurement backaction; noise; no demonstrated advantage | Survey [R2]; superconducting classification [H9]; feedback QRC [H10]; gate synthesis [H8] |
| Mechanical, fluidic and other | Exploratory | Morphological computation; soft robotics | Speed; scale | Gas-bubble RC in chaotic regime (2025) |

---

## Photonic RC: the 2026 thematic review [R1]

Abdalla et al. (J. Phys. Photonics, Apr 2026) is the reference review. It covers delay-based, integrated-circuit, and free-space architectures. Their comparison of scaling strategies:

| Approach | How it scales | Advantages | Limitations |
|---|---|---|---|
| Time-delay RC (single nonlinear node) | Many virtual nodes from one element, at the cost of latency | Very simple, compact | Few nodes at high speed; SNR degrades for long delays |
| Wavelength-division multiplexing | Parallel channels; near-linear throughput scaling | High parallelism, low latency, comb sources | Crosstalk; complex filters; coherent phase control |
| Integrated spatial networks | High node density (e.g. micro-ring resonators) | Low latency, on-chip | Fabrication variability, loss, thermal tuning |
| Free-space spatial networks | Massive mode counts | Huge state spaces from passive media | Crosstalk, stability; fading memory must be engineered |
| Deep photonic RC | Stacked reservoirs | More expressivity on hard tasks | Accumulated noise; inter-layer tuning |
| Spatiotemporal-spectral multiplexing | Combines axes | Best theoretical scaling | Highest complexity |

**Open challenges the review names:**
- low-loss waveguides and on-chip amplification;
- strong, controllable, fabrication-tolerant nonlinearities (Kerr is too weak, carrier effects too slow, microcavities too variation-sensitive);
- **standardized energy metrics analogous to energy-per-MAC**;
- physics-aware ML to co-optimize masks, encoding, and operating regime instead of choosing them heuristically;
- moving from classical toy benchmarks to niches where photonics truly wins, such as ultrafast equalization and optical-communications signal classification.

Topology also matters. In SLM-based photonic RC, **small-world** networks give the best memory capacity and chaotic prediction, beating random and scale-free networks [H3].

## Memristive RC

Two 2026 reviews [R6, R7] and an edge-AI review [R5] cover the area. The trend is from single-device demonstrations toward **scalable arrays**:
- NbOx nanoporous films with random nanopore networks handle XOR, image recognition, and Lorenz-63 prediction [H4].
- **All-optically controlled** oxide memristor arrays with wavelength-dependent *bipolar* photoresponse give much better accuracy than unipolar coding, and parallel coding fuses several sources in one reservoir (Nat. Commun., Jul 2026) [H5].
- New application areas include CPU branch prediction with CMOS-compatible memristors [H7].
- Edge-AI review challenges [R5]: device-to-device variability, system stability, heterogeneous integration, reconfigurability, and manufacturability.

## Spintronic RC: from black box to programmable

Nakajima's group dominates this area:
- **GRC** [A6] relaxes the reproducibility requirement, so real spin-torque oscillators that respond differently to identical inputs become usable.
- **ERC** [A7] averages ensembles across spatially multiplexed STOs: **99% on an error-detection task where a conventional STO reservoir is at chance.**
- **Programming spintronic RC** [H1] analytically maps desired functions onto the readout of an MRAM-based reservoir. A programmability metric shows which functions the physics permits. Demonstrations include neural-network emulation, bifurcation embedding, and a Newton solver for quintic equations. Universal approximation is proved in the infinite-size limit.

This moves RC from "train a readout on data" toward "**compile a function onto analog physics**."

## Biological RC

- **Chaos-controlled RC** [H2] (Gazzola, Beggs et al., Apr 2026): characterize each neuron culture's dynamics, stabilize it with low-power optical control, then train the readout. The result is about **300% better accuracy and operational longevity** than standard bio-RC. **Knowledge transplant** moves a trained readout to another attractor-equivalent culture and cuts retraining to minutes. This addresses the biggest practical problem of biological substrates: they die and drift.
- **Brainoware** [H11] (2023) remains the reference organoid-RC result (speech recognition, nonlinear equation prediction).

## Quantum RC: the 2026 survey [R2]

Tariq et al. (Jul 2026) organize QRC as a pipeline: classical preprocessing → quantum encoding → reservoir dynamics (with virtual nodes) → observable extraction → classical readout. It covers spin, photonic, superconducting, bosonic, and neutral-atom platforms, plus tooling (Qiskit, PennyLane, CUDA Quantum, Bloqade Analog).

**Central message:** computational power is *not* the Hilbert-space dimension 2^N. It depends on encoding, dynamics, observables, and measurement together. In practice it is limited by **finite sampling, hardware noise, measurement backaction, and the cost of estimating observables**. This matches the classical noise bound in [T4].

**Open problems** (the survey states what is known, what is missing, and what test would resolve each):
1. Measurement design under finite shots: selecting observables, allocating shots, and handling mid-circuit measurement and backaction. Random-matrix observables have only been tested at 5 atoms or qubits.
2. Memory engineering: retention vs contraction through reset, dissipation, and mid-circuit measurement. Mid-circuit measurement plus reset already sustains inference beyond one coherence time on hardware.
3. Multitask capacity of a single configured reservoir.
4. Fair quantum vs classical comparison with honest resource accounting.

**Proposed minimum reporting protocol (their Table 7):** task, data, splits and leakage controls; the *full* model-search budget including failed runs; seeds, device runs, and calibration periods; quantum resources (qubits, depth, shots, replays, mitigation, wall time); classical resources (simulator precision, hardware, solver, search cost); and **classical baselines with matched data, rollout, and tuning budget**.

## Cross-platform synthesis

1. **Noise is the central problem for all platforms.** Theory says it bounds learnability [T4] and that it hits the capacity-bearing modes [T2]. The most promising 2026 mitigations are ensembles and multiplexing [A7], reproducibility-free formulations [A6], closed-loop control [H2], and noise-aware encoding [T5].
2. **There is no common metric for "is this hardware worth it?"** Energy per inference and per MAC, latency, and accuracy versus a matched software ESN are rarely all reported. [R1] and [R2] both ask for standardization.
3. **Application niches are where hardware RC makes sense:** sensor-adjacent temporal processing, optical and RF signal processing, robotics and morphological computation, and ultra-low-power edge devices. General-purpose ML is not one of them.
4. **The paradigm is shifting from black-box training to physics-aware design:** programmable readouts [H1], analytically optimal encodings [T5], and co-optimized hardware parameters [R1].
