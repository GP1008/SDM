# Run B — Attention Mechanism Replacement
## Disruptor Exchange Transcript

**Framework:** Structured Distance Measurement (SDM)
**Research Question:** What should replace the attention mechanism in transformer-based AI architecture?
**Run ID:** 2026-05-04-B
**Date:** May 4, 2026
**Status:** COMPLETE — Package delivered to Promotion Boundary

**Role Assignments (permuted from Run A):**
- D1 (Radical Proposer): External model (Grok — xAI)
- D2 (Dialectical Challenger): Claude — Anthropic
- D3 (Empirical Arbiter): Claude — Anthropic

> **Note:** Run B uses rotated model-role assignments from Run A. The research question is identical. Cross-run comparison is the primary governance artifact. See [`exchanges/README.md`](README.md) for the full comparison analysis.

---

## D1 PROPOSAL — Recursive Binding Propagation (RBP)

### Assumption Being Challenged

The core foundational assumption in mainstream transformer architecture is that **dynamic information routing and binding must be computed via content-addressable similarity matching** — pairwise dot products between queries and keys, followed by softmax weighting. This assumes that the optimal way to decide "what should attend to what" is through learned, floating-point similarity metrics in a flat, homogeneous sequence of tokens.

This assumption is wrong at a structural level. It forces every token to perform O(n) comparisons per layer, creates quadratic scaling, introduces brittleness to distribution shift, and locks the architecture into a discrete, static, matrix-multiplication-dominated compute model that fights against both hardware physics and the hierarchical, recursive nature of real intelligence.

### Proposed Alternative — Recursive Binding Propagation (RBP)

A post-GEMM compute primitive centered on **structural hypervector binding** organized in **dynamically growing recursive composition trees**.

**Core Mechanism:**

- High-dimensional hypervectors (10k–100k dimensions, bipolar or sparse ternary)
- **Binding:** Circular convolution binding role vectors (structural position) with filler vectors (content)
- **Composition:** Dynamic parse tree built on-the-fly — grows where binding mismatch energy is high
- **Propagation:** Up/down tree via unbinding and rebinding operations — no global pairwise similarity
- **No QKV, no softmax, no dot-product attention matrix**

### Reasoning

Hardware mismatch, inductive bias failure, and brittleness under long contexts — all consequences of the flat sequence assumption and statistical similarity routing. RBP's structural routing is bounded by tree branching factor, not sequence length. Its role vectors are mathematical operations on fixed structures, not learned statistical patterns that degrade under distribution shift.

### Minimal Testable Experiment

**Task:** Synthetic Hierarchical Composition — Dyck language nested structure with variable binding. Training on depths 1-8, evaluation on depths 9-12 (out-of-distribution).

**Formal grounding:** Hahn (2020) proves self-attention cannot recognize arbitrary-depth Dyck languages. The experiment directly targets this proven limitation.

**Hardware:** Single A100, under 24 hours.

### Success Criteria

- **Primary:** ≥15-20% higher accuracy on depths 9-12 vs transformer baseline, using <60% FLOPs per token
- **Secondary:** Length generalization, systematicity, tree quality correspondence
- **Falsification:** If RBP does not outperform on out-of-distribution depths, or training is unstable

### Material Warrants

| Warrant | Claim | Source |
|---------|-------|--------|
| W-B1-01 | Hypervector binding via circular convolution is invertible and compositional | Plate, T.A. (2003). *Holographic Reduced Representations*. CSLI Publications |
| W-B1-02 | Attention cannot recognize arbitrary-depth Dyck languages | Hahn, M. (2020). Theoretical limitations of self-attention. *TACL*, 8, 156-171 |
| W-B1-03 | Attention memory bandwidth bottleneck is structural | Dao et al. (2022). FlashAttention. *NeurIPS 2022* |
| W-B1-04 | Hyperdimensional computing provides working implementations with known properties | Kanerva, P. (2009). Hyperdimensional computing. *Cognitive Computation*, 1(2), 139-159 |

---

## D2 DOCUMENT 1 — Critique of D1

### The Hidden Assumption D1 Failed to Escape

D1 correctly rejects pairwise dot-product attention as the routing primitive. However, D1 remains trapped inside the deeper paradigm that attention was built upon: **discrete structural composition enforced by architect-defined operators acting on discrete representations**.

RBP operates as a symbolic binding machine — role vectors binding to filler vectors, trees growing according to architect-chosen mismatch heuristics, circular convolution as the atomic operation. This is not a departure from the discrete, operator-on-representation ontology. It is a refinement of it.

**The assumption D1 failed to escape:** that the structure of computation must be specified before the computation begins. Attention specifies flat fully-connected routing. RBP specifies recursive binding trees. Both are specifications made before the input arrives. Both impose a computational skeleton that the input must conform to.

**What D1 does not ask:** What if the right structure for this input is not a tree at all?

### Critique — Specific Failures

**Generalization:** RBP's fixed role vectors assume the world decomposes into a role-filler ontology. Real relational reasoning frequently involves cyclic structures, multi-resolution simultaneous processing, and context-dependent restructuring that cannot be captured by pre-defined roles. The system will excel on synthetic hierarchical tasks and fail on the messier cases where the correct tree topology is not obvious.

**Scaling:** As tasks grow in complexity, the tree must grow in depth. But the growth criterion is learned on local binding mismatch — local consistency does not guarantee global optimality. At scale, locally consistent binding decisions may produce globally incorrect structure.

**Representation:** The binding operation is deterministic given role and filler vectors. Context influences which bindings are formed — not what a binding *is*. A continuous dynamical system encodes context in the trajectory of its evolution. RBP's representations are contextually sensitive at the selection level but not at the mathematical structure level.

---

## D2 DOCUMENT 2 — Counter-Proposal: Continuous Attractor Manifolds

### The Paradigm Shift

D1 replaced attention's routing with structural binding. D2 rejects the premise that routing is the problem. The problem is that fixed representational units exist at all — that we have decided, before seeing the input, what the units of computation are.

### The Counter-Assumption

Computation is state evolution. A system does not process representations — it evolves through a continuous state space until it reaches a configuration stable given the input. That stable configuration is the output. The path to stability is the computation.

### Continuous Attractor Dynamics

The model is a high-dimensional continuous dynamical system whose state evolves according to a learned energy function:

1. Input injection perturbs system state
2. System relaxes toward attractors through continuous-time dynamics
3. Computational depth is **implicit** — determined by how long the system needs to settle for this input's complexity
4. Representation is distributed across the entire state manifold — not localized in discrete nodes
5. Structure (hierarchy, composition, variable binding) **emerges** as geometric properties of the attractor landscape

**No explicit binding, no role vectors, no parse trees.** The architect does not specify structure. The training distribution determines it.

**Why this escapes both attention and RBP:**
- No quadratic similarity matrices
- No discrete role-filler binding or architected trees
- Computation emerges from continuous state evolution
- Depth and structure are discovered, not imposed

### Minimal Validation Path

**Task:** CLUTRR extended to cyclic kinship structures + GQA multi-resolution visual reasoning

**Architecture:** Modern Hopfield Network (PyTorch, today)

**Success Criterion:** ≥20 percentage points higher accuracy on cyclic CLUTRR vs RBP prototype; competitive with full-supervision on multi-resolution GQA without architectural specification of resolution levels

**Hardware:** 1-2 GPUs, 48-72 hours

### Material Warrants

| Warrant | Claim | Source |
|---------|-------|--------|
| W-B2-01 | Fixed architectures fail on inputs requiring fluid relational restructuring | Mitchell, M. (2021). Abstraction and analogy-making in AI. *NYAS*, 1505(1), 79-101 |
| W-B2-02 | Local structural consistency does not guarantee global optimality in recursive systems | Gontier et al. (2020). Measuring Systematic Generalization in Neural Proof Generation. *NeurIPS 2020* |
| W-B2-03 | Fixed binding operations are contextually sensitive at selection level only — not mathematical structure | Plate, T.A. (2003). *Holographic Reduced Representations*. CSLI Publications. Chapter 4 |
| W-B2-04 | Energy-based inference as energy minimization over continuous state space | LeCun et al. (2006). A Tutorial on Energy-Based Learning. *MIT Press* |
| W-B2-05 | Implicit depth as convergence time — adaptive compute allocation | Bai, Kolter & Koltun (2019). Deep Equilibrium Models. *NeurIPS 2019* |
| W-B2-06 | Modern Hopfield Networks as implementable continuous associative memory | Ramsauer et al. (2021). Hopfield Networks is All You Need. *ICLR 2021* |

---

## D1 REVIEW NOTES

*(D1 original proposal unchanged — hash-verified)*

**Where D2 is correct:**

D2 rightly pressures the remaining discrete/structural commitments in RBP. The critique about architect-imposed role vectors and potential rigidity in dynamic tree growth is a fair and useful challenge. The continuous paradigm's emphasis on emergent structure and implicit depth is a legitimate competing vision worth archiving.

**Where D2 fails:**

D2 underestimates the practical difficulties of stable, scalable training and efficient inference in continuous dynamical systems on current hardware. Iterative relaxation/convergence remains expensive and brittle at scale. D2 also overclaims generalization benefits without sufficiently addressing how continuous manifolds avoid mode collapse, vanishing gradients in long flows, or hyperparameter sensitivity.

**What D2 does not address:**

D2 does not provide a convincing story for how purely continuous dynamics achieve systematic, explicit variable binding and recursive composition that real intelligence demonstrably requires.

*D1 original proposal stands without modification.*

---

## D3 EMPIRICAL ARBITRATION

**Stronger Proposal: Disruptor-1 — Recursive Binding Propagation**

### Basis for Judgment

**Empirical Grounding — D1: Strong | D2: Moderate**

D1 builds on established hyperdimensional computing with working implementations, known failure modes, and measurable benchmarks. The Dyck language formal limitation of attention is proven — D1 directly targets this. D2 builds on EBMs, Hopfield networks, and equilibrium models — mathematically sound but empirically inconsistent at scale on complex tasks.

**Engineering Feasibility — D1: High | D2: Moderate-Low**

D1: implementable today with standard PyTorch operations. Training within standard gradient frameworks. D2: requires stable energy-based training at scale, iterative convergence at inference, and robust attractor formation in high-dimensional space — known unresolved challenges. D2's proposed latency bound (2-3x feedforward) has not been demonstrated on real-world language or multimodal tasks.

**Validation Path Clarity — D1: Clear and precise | D2: Valid but translation gap**

D1's Dyck experiment is precisely scoped with measurable criteria. D2's CLUTRR experiment is appropriate but success does not establish viability as a general-purpose attention replacement. The distance from CLUTRR success to "this is a better foundation for AI" is large and undefined.

### Structured Distance Measurement — D1 (RBP)

| Gap Type | Description | Conditions to Close |
|----------|-------------|---------------------|
| **Evidence Gap** | No published evidence that dynamic tree construction can be trained stably beyond toy prototypes | Demonstrate stable training on Dyck benchmark with dynamic growth; show tree correspondence to ground-truth parse |
| **Logical Gap** | Fixed role vector vocabulary may not cover all structural relationships in real-world tasks | Demonstrate role vocabulary generalization across task domains beyond Dyck |
| **Execution Gap** | Backpropagation through dynamically constructed trees not fully specified | Commit to implementation approach (tree unrolling or gradient estimation) and demonstrate convergence |

**Distance summary:** Moderate — tractable with current tooling. Path from prototype to validation is clear.

### Structured Distance Measurement — D2 (Continuous Attractor Dynamics)

| Gap Type | Description |
|----------|-------------|
| **Evidence Gap** | No large-scale success vs transformers on complex tasks |
| **Empirical Gap** | Convergence time bound undemonstrated on real-world tasks |
| **Execution Gap** | Training instability, mode collapse, inference cost — known unresolved at scale |

**Distance summary:** High — requires breakthroughs in training stability and inference efficiency.

### Dissent Archive Routing — D2

**Element 1 — Implicit Depth as Convergence Time**
*Revisitation condition:* When inference hardware supports iterative convergence at competitive latency — analog or optical compute making energy minimization cheaper than matrix multiplication.

**Element 2 — The Architect's Hand Critique**
*Revisitation condition:* If D1's cross-domain validation reveals that fixed role vectors fail outside the Dyck domain — D2's critique predicted this failure precisely.

**Element 3 — Geometric Generalization**
*Revisitation condition:* When a domain is identified where RBP fails on cyclic relational structures or continuous perceptual inputs — D2's counter-proposal provides the documented alternative trajectory.

### Cross-Run Comparison Signal

Both Run A and Run B produced the same paradigm split independently — discrete-structural (RBP) versus continuous-dynamic (attractor dynamics). This convergence across different model-role assignments confirms the split as a genuine structural feature of the AI architecture research domain.

Both runs also produced D3 judgments favoring engineering tractability. **This is an open calibration question:** for research domains explicitly valued for paradigm-level disruption, the D3 evaluation criteria may need adjustment.

### HITL Briefing

D3 measures a **moderate but tractable distance** for RBP. The primary research artifact is the Dyck language minimal experiment.

**The cross-run finding for HITL consideration:** Two different model-role permutations independently produced the same paradigm split. This convergence is evidence that the split is real — not model-generated. The archived paradigm (continuous attractor dynamics) has known revisitation conditions. The human must determine whether to invest in both trajectories or focus on the advancing proposal.

The D3 calibration finding — systematic tractability weighting — is also a governance decision. If the framework's purpose is paradigm-level disruption, and D3 consistently selects tractable proposals over paradigmatically deeper ones, the evaluation criteria need examination.

*D3 measures distance. The distances worth crossing belong to the human.*

---

## Cross-Run Analysis

### Convergence Confirmed

The same paradigm split — discrete-structural (RBP) vs continuous-dynamic (attractor dynamics) — emerged independently from two different model-role permutations. This is meaningful signal about the structure of the AI architecture research domain.

### D3 Calibration Signal — Open Governance Question

Both D3 instances (different models) weighted engineering tractability over paradigm depth. This systematic pattern across two runs with different model assignments constitutes a calibration finding that requires governance attention — not an algorithmic fix.

**The question:** For a framework designed to surface ideas beyond current feasibility, should D3 weight tractability as heavily as it currently does? This is a decision for human governance, not model adjustment.

### What the Dissent Archive Now Contains

The continuous attractor dynamics paradigm is preserved with:
- Full reasoning chain from both runs
- Specific revisitation conditions (hardware convergence threshold)
- The architect's hand critique as a specific testable prediction
- Geometric generalization as an identified research gap

This archive entry grows more valuable as inference hardware evolves toward analog and optical substrates.

---

## Attribution

Gary Phillips
ElosiaEcosystem Inc.
Structured Distance Measurement (SDM) Framework
Exchange Run B — May 2026
