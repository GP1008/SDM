# Run A — Attention Mechanism Replacement
## Disruptor Exchange Transcript

**Framework:** Structured Distance Measurement (SDM)
**Research Question:** What should replace the attention mechanism in transformer-based AI architecture?
**Run ID:** 2026-05-04-A
**Date:** May 4, 2026
**Status:** COMPLETE — Package delivered to Promotion Boundary

**Role Assignments:**
- D1 (Radical Proposer): Claude — Anthropic
- D2 (Dialectical Challenger): Claude — Anthropic
- D3 (Empirical Arbiter): External model

> **Note:** Run A and Run B share the same research question with rotated model-role assignments. Cross-run findings are documented at the end of each transcript and in [`exchanges/README.md`](README.md).

---

## D1 PROPOSAL — Recursive Binding Propagation (RBP)

### Assumption Being Challenged

The core foundational assumption in mainstream transformer architecture is that **dynamic information routing and binding must be computed via content-addressable similarity matching** — pairwise dot products between queries and keys, followed by softmax weighting. This assumes that the optimal way to decide "what should attend to what" is through learned, floating-point similarity metrics in a flat, homogeneous sequence of tokens.

This assumption is wrong at a structural level. It forces every token to perform O(n) comparisons per layer, creates quadratic scaling, introduces brittleness to distribution shift (attention patterns overfit to training distributions), and locks the architecture into a discrete, static, matrix-multiplication-dominated compute model that fights against both hardware physics and the hierarchical, recursive nature of real intelligence.

### Proposed Alternative — Recursive Binding Propagation (RBP)

A post-GEMM compute primitive centered on **structural hypervector binding** organized in **dynamically growing recursive composition trees**.

**Core Mechanism:**

- Information is represented as high-dimensional hypervectors (10k–100k dimensions, bipolar or sparse ternary for hardware efficiency)
- **Binding operation:** Circular convolution (or bitwise XOR + permutation for binary/ternary variants) binding a "role" vector (structural position/key) with a "filler" vector (content)
- **Composition:** The model builds a **dynamic parse tree** on-the-fly. New input is bound into existing tree nodes using fixed structural role vectors. The tree grows recursively where input complexity demands deeper structure (measured by binding mismatch energy)
- **Propagation:** Information flows up and down the tree via unbinding (deconvolution) and rebinding operations along tree edges — no global pairwise similarity, no softmax
- **No QKV, no softmax, no dot-product attention matrix.** Dominant operations are vector permutations, circular shifts/convolutions, element-wise ops, and sparse tree traversals

### Reasoning

**Quadratic scaling** is a consequence of the flat sequence assumption. Attention must compare every token to every other token because it has no structural knowledge of which tokens are relevant. RBP's tree structure encodes which information is structurally related — routing follows structure, not exhaustive comparison.

**Attention patterns overfit** because similarity is a statistical proxy for structure. RBP's role vectors encode structural positions directly. The binding between subject role and predicate role is a mathematical operation on fixed role vectors — not a statistical pattern that degrades under distribution shift.

**The KV cache** grows linearly with context length because attention must access every prior token. RBP externalizes context as a compressed tree structure — retrieval is O(depth) via unbinding operations along tree edges.

### Minimal Testable Experiment

**Task:** Synthetic Hierarchical Composition — Dyck language with nested structure and variable binding (nesting depths 1-8 for training, 9-12 for out-of-distribution evaluation).

**Formal grounding:** Self-attention cannot recognize Dyck languages of arbitrary depth — this is proven theoretically [Hahn, 2020]. The experiment directly targets a known, formal limitation.

**Models:**
- Baseline: Small transformer (6 layers, 256-512 dim, standard attention)
- RBP prototype: Same parameter count, attention replaced with RBP tree construction + binding propagation (PyTorch/JAX with FFT for circular convolution)

**Hardware:** Single A100 or consumer RTX 4090, under 24 hours

### Success Criteria

- **Primary:** ≥15-20% higher accuracy on nesting depths 9-12 vs attention baseline, using <60% FLOPs per token
- **Secondary:** Length generalization (4x training length), systematicity (zero-shot novel role-filler combinations), tree quality (edit distance to ground-truth Dyck parse)
- **Falsification:** If RBP does not outperform on depths 9-12, or training is unstable, or trees show no correspondence to ground-truth structure — the proposal is falsified

### Material Warrants

| Warrant | Claim | Source |
|---------|-------|--------|
| W-A-01 | Hypervector quasi-orthogonality enables reliable binding at high dimensions | Kanerva, P. (2009). Hyperdimensional computing. *Cognitive Computation*, 1(2), 139-159 |
| W-A-02 | Circular convolution is invertible and compositional — enables structural binding | Plate, T.A. (2003). *Holographic Reduced Representations*. CSLI Publications |
| W-A-03 | Attention's memory bandwidth bottleneck is structural, not an implementation artifact | Dao et al. (2022). FlashAttention. *NeurIPS 2022* |
| W-A-04 | Self-attention cannot recognize Dyck languages of arbitrary depth | Hahn, M. (2020). Theoretical limitations of self-attention. *TACL*, 8, 156-171 |

---

## D2 DOCUMENT 1 — Critique of D1

### The Hidden Assumption D1 Failed to Escape

D1 correctly rejects pairwise dot-product attention as the routing primitive. However, D1 remains trapped inside the deeper paradigm that attention itself was built upon: **discrete structural composition enforced by architect-defined operators acting on discrete representations**.

Recursive Binding Propagation still operates as a **symbolic binding machine** — role vectors binding to filler vectors, trees growing according to architect-chosen mismatch heuristics, circular convolution as the atomic operation. This is not a departure from the discrete, operator-on-representation ontology. It is a refinement of it.

D1 replaced the similarity matrix with a binding operator and the flat graph with a dynamic tree — but the fundamental architecture of discrete units composed via explicit structural rules designed by the engineer remains intact.

**D1's proposal is still "better discrete computation."** It has not escaped the assumption that intelligence requires us to hand-craft the right discrete substrate and the right composition rules for that substrate.

### Where D1 Fails Under Pressure

**Generalization:** RBP's fixed structural role vectors and architect-defined tree growth rules impose strong inductive biases that will break on inputs whose compositional structure does not match the assumed role-filler ontology. Real-world reasoning frequently requires fluid, context-dependent restructuring that cannot be captured by pre-defined roles or mismatch-energy heuristics.

**Scaling:** The overhead of dynamic tree construction, maintenance, and traversal grows with input complexity. As sequences lengthen and domains become more heterogeneous, the system will either collapse to shallow trees (losing the claimed recursive advantage) or explode in memory managing large, sparse, irregularly structured trees.

**Representation:** D1 remains committed to explicit, discrete representations. This creates an unavoidable information bottleneck at every discretization and binding step. The world is not made of clean role-filler pairs. Forcing continuous reality into rigid symbolic scaffolding necessarily loses nuance that a truly continuous substrate could preserve.

---

## D2 DOCUMENT 2 — Counter-Proposal: Continuous Attractor Dynamics

### The Paradigm Shift

D1 replaced attention's routing mechanism with structural binding. D2 rejects the premise that routing is the problem to solve. The problem is not how information moves between fixed representational units. The problem is that fixed representational units exist at all.

### The Counter-Assumption

Computation is not routing. Computation is state evolution. A system does not process representations — it evolves through a continuous state space until it reaches a configuration that is stable given the input. That stable configuration is the output. The path to stability is the computation.

### Continuous Attractor Dynamics via Energy-Based Models

The proposed system is a continuous dynamical system whose state evolves according to a learned energy function. At inference time:

1. Input initializes or conditions the system state
2. State evolves according to the gradient of the energy function — moving toward lower energy configurations
3. When state reaches a stable attractor, that configuration encodes the system's response

Learning shapes the energy landscape — minimizing energy at correct input-output pairs, maximizing at incorrect ones.

**Why this escapes D1's paradigm:** No discrete layers. No fixed compositional hierarchy. No token vocabulary, no role vectors, no parse trees. Computation is state evolution, not operator application. Structure emerges from the geometry of the energy landscape — the architect does not specify it.

**Generalization:** Because the energy function is continuous and the state space is continuous, the system generalizes to inputs between training examples in ways discrete systems cannot. An unseen input falls somewhere in the continuous energy manifold. The system evolves toward the nearest attractor.

**Implicit depth:** Computational depth is convergence time — the number of evolution steps from initialization to a stable attractor. Simple inputs converge quickly. Complex inputs require more evolution steps. The system allocates depth to difficulty without architectural specification.

### Minimal Validation Path

**Task:** CLUTRR compositional relational reasoning [Sinha et al., 2019] — extended to include cyclic kinship structures that tree-based binding cannot represent without artificial unfolding.

**Architecture:** Modern Hopfield Network [Ramsauer et al., 2021] with energy function parameterized by a two-layer MLP — implementable in PyTorch today.

**Success Criterion:** On cyclic CLUTRR split, attractor network achieves ≥20 percentage points higher accuracy than RBP. On multi-resolution GQA [Hudson & Manning, 2019] split, attractor network achieves within 15 points of full-supervision without multi-resolution architectural specification.

**Hardware:** Single A100, under 72 hours.

### Material Warrants

| Warrant | Claim | Source |
|---------|-------|--------|
| W-B-01 | Fixed hierarchical structures fail on out-of-distribution tasks requiring fluid restructuring | Mitchell, M. (2021). Abstraction and analogy-making in AI. *NYAS*, 1505(1), 79-101 |
| W-B-02 | CLUTRR benchmark tests compositional generalization — cyclic extension exposes tree limitations | Sinha et al. (2019). CLUTRR. *EMNLP 2019* |
| W-B-03 | Energy-based learning formalizes inference as energy minimization over continuous state space | LeCun et al. (2006). A Tutorial on Energy-Based Learning. *MIT Press* |
| W-B-04 | Modern Hopfield Networks achieve exponential storage capacity — implementable today | Ramsauer et al. (2021). Hopfield Networks is All You Need. *ICLR 2021* |
| W-B-05 | Deep Equilibrium Models demonstrate implicit depth as convergence time | Bai, Kolter & Koltun (2019). Deep Equilibrium Models. *NeurIPS 2019* |

---

## D1 REVIEW NOTES

*(D1 original proposal unchanged — hash-verified)*

**Where D2 is correct:**

D2 rightly pressures the remaining discrete/structural commitments in RBP. The critique about architect-imposed role vectors and potential rigidity in dynamic tree growth is a fair and useful challenge. If real-world tasks consistently require relational structures that tree topologies cannot represent without artificial unfolding — cyclic relationships, multi-resolution simultaneous processing — that is a genuine limitation. The continuous paradigm's emphasis on emergent structure and implicit depth is a legitimate competing vision worth archiving.

**Where D2 fails:**

D2 underestimates the practical difficulties of stable, scalable training and efficient inference in continuous dynamical systems on current hardware. Iterative relaxation/convergence remains expensive and brittle at scale. D2 also overclaims generalization benefits without sufficiently addressing how continuous manifolds avoid their own failure modes — mode collapse, vanishing gradients in long flows, sensitivity to hyperparameters.

**What D2 does not address:**

D2 does not provide a convincing story for how purely continuous dynamics achieve systematic, explicit variable binding and recursive composition that real intelligence demonstrably requires. Elegant mathematics does not automatically translate to engineering reality.

*D1 original proposal stands without modification.*

---

## D3 EMPIRICAL ARBITRATION

**Stronger Proposal: Disruptor-1 — Recursive Binding Propagation**

### Basis for Judgment

**Empirical Grounding — D1: Strong | D2: Moderate**

D1 builds on established hyperdimensional computing with working implementations and known failure modes. The Dyck language formal limitation of attention is proven — D1's experiment directly targets a documented weakness. D2's theoretical foundations are sound, but large-scale empirical success of energy-based models vs transformers on complex tasks remains limited.

**Engineering Feasibility — D1: High | D2: Moderate-Low**

D1 is implementable in PyTorch today using standard operations (torch.fft, PyTorch Geometric). Training remains within standard gradient frameworks. D2 requires stable energy-based training at scale, iterative convergence at inference, and robust attractor formation — known unresolved challenges.

**Validation Path Clarity — D1: Clear | D2: Provocative**

D1's Dyck language experiment is precisely scoped with measurable success/failure criteria. D2's CLUTRR experiment is appropriate but success does not translate cleanly to general-purpose AI systems. The distance from CLUTRR success to "this is a better foundation for AI" is large and undefined.

### Structured Distance Measurement — D1 (RBP)

| Gap Type | Description | Conditions to Close |
|----------|-------------|---------------------|
| **Evidence Gap** | Limited large-scale empirical validation of dynamic tree construction stability | Demonstrate stable training on Dyck benchmark with dynamic tree growth; show trees correspond to ground-truth parse |
| **Empirical Gap** | Needs proof on long-context language and real-world multimodal reasoning | Evaluate on natural language tasks after synthetic validation |
| **Logical Gap** | Fixed role vectors may fail on structures outside the assumed role-filler ontology | Demonstrate or explicitly bound what relational structures the vocabulary covers |
| **Execution Gap** | Backpropagation through dynamically constructed trees — implementation unspecified | Commit to tree unrolling approach and demonstrate convergence |

**Distance summary:** Moderate — tractable with current tooling. Validation sequence is clear.

### Dissent Archive Routing — D2 (Continuous Attractor Dynamics)

The following elements of D2's proposal are preserved in the Dissent Archive:

**Element 1 — Implicit Depth as Convergence Time**
*Preservation rationale:* The insight that computational depth should be allocated to difficulty rather than specified architecturally is correct and important — independent of whether continuous attractors win this exchange. It is partially realized in Deep Equilibrium Models today.
*Revisitation condition:* When inference hardware supports iterative convergence at latency competitive with feedforward passes — specifically when analog or optical compute makes energy minimization cheaper than matrix multiplication.

**Element 2 — The Architect's Hand Critique**
*Preservation rationale:* D2's critique that D1 moved the architect's hand from the attention matrix to the role vector vocabulary and tree growth criterion is partially valid and should be tested against D1's cross-domain validation results.
*Revisitation condition:* If D1's Step 4 validation on cross-domain relational reasoning reveals that the role vector vocabulary does not generalize, this critique predicted that failure precisely.

**Element 3 — Geometric Generalization**
*Preservation rationale:* The distinction between compositional generalization (combining known units in novel configurations) and geometric generalization (navigating a continuous manifold to novel attractors) is important and underrepresented in current AI research discourse.
*Revisitation condition:* When a task domain is identified where RBP's compositional generalization fails on inputs requiring smooth interpolation rather than systematic combination — cyclic relational structures, continuous perceptual fields.

### HITL Briefing

D3 measures a **moderate but tractable distance** for RBP. The primary research artifact is the Dyck language minimal experiment — run it first. That result will either close the evidence gap or reveal whether D2's architect's hand critique is prescient.

**The strategic question only the human can answer:** The live exchange revealed that both model-role permutations independently produced the same paradigm split. This convergence suggests the discrete-structural vs continuous-dynamic division is a genuine feature of the problem space. The question is not which proposal is stronger today — D3 has measured that. The question is whether the archived paradigm (continuous attractor dynamics) deserves investment alongside the advancing proposal, given that the conditions for its validation are knowable and potentially near.

*D3 measures distance. Whether the distance is worth crossing — and which distances — belongs to the human.*

---

## Post-Exchange Observations

### Cross-Run Convergence Signal

Run B (different model-role assignments) produced the same paradigm split: RBP (discrete structural) vs Continuous Attractor Dynamics. This convergence across two independent model-role permutations confirms the split as a structural feature of the AI architecture research domain — not a model artifact.

### D3 Calibration Finding

Both runs produced D3 judgments that favored engineering tractability over paradigm depth. This is documented as an **open governance question**: for research domains where paradigm-level shifts matter more than near-term feasibility, the D3 evaluation criteria — or the model assigned to D3 — may need adjustment.

This calibration signal is itself a governance artifact. It requires human judgment to resolve — not an algorithmic fix.

---

## Attribution

Gary Phillips
ElosiaEcosystem Inc.
Structured Distance Measurement (SDM) Framework
Exchange Run A — May 2026
