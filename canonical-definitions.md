# Canonical Definitions
## Structured Distance Measurement Framework

**ElosiaEcosystem Inc. | Gary Phillips**
**Version 1.2 | May 2026**
**License: CC BY-NC 4.0**

> This document defines the precise terminology used throughout the SDM framework. Where any other document conflicts with these definitions, these definitions govern.

---

## 01 — Structured Distance Measurement (SDM)

**Definition:** A non-probabilistic, four-category measurement of the gap between a research proposal and full empirical validation, produced by Disruptor-3 after evaluating both competing proposals against current technological reality.

**The four gap categories:**

| Category | What It Measures |
|----------|-----------------|
| **Evidence Gap** | Distance from existing empirical observations |
| **Empirical Gap** | Experiments required to validate the proposal |
| **Logical Gap** | Internal coherence against established theory |
| **Execution Gap** | Engineering, hardware, and tooling requirements |

**What SDM is not:** SDM is not a probability score. It is not a recommendation. It does not decide whether a proposal is good or bad. It measures how far a proposal is from the conditions required to validate it, and states those conditions explicitly.

**Why the distance is the artifact:** Scientific paradigms change. Hardware evolves. A proposal that is impractical today may become foundational tomorrow. The measured distance — taken at a specific moment against a specific empirical landscape — retains historical value even as everything around it shifts.

---

## 02 — System of Material Knowledge (SMK)

**Definition:** The system-wide governance layer that defines what all agents must do, how they must behave, and what boundaries they must operate within — authored exclusively through deliberate governance decisions, never derived from agent learning.

**Two categories of content:**

- **Governance Documents:** Authored specifications defining the framework itself — role specifications, orchestration constraints, governance standards.
- **Behavioral Mandates:** Governance decisions that change how all agents must operate system-wide.

**The invariant:** SMK is not a product of what agents learn. It is a product of what the system decides must be enforced. SIM accumulates experience. SMK enforces alignment. They do not exchange data.

**What SMK is not:** Not a research database. Not derived from agent outputs. Not updated by validation results or exchange outcomes. Not a source agents consult during active research.

---

## 03 — System of Information Management (SIM)

**Definition:** Per-agent long-term memory — an append-only ledger of validated knowledge outcomes written exclusively through HITL approval events, carrying full provenance chains.

**Properties:**
- Private per agent — no agent reads another agent's SIM
- Append-only — entries are never deleted, only archived when superseded
- HITL-exclusive write — the only event that writes to SIM is an approved HITL decision
- Carries full provenance — every entry includes the complete chain from source to approval

**The invariant:** SIM content can never become SMK content. There is no route, API, promotion path, or HITL action that writes SIM content to the SMK. These are categorically different systems with different authorities.

---

## 04 — Notebook Corpus

**Definition:** Each agent's private, dynamic research environment — an isolated workspace built through active research during each run, operating under zero-trust defaults.

**Properties:**
- Private and isolated — no agent reads another agent's notebook
- Zero-trust — nothing in the notebook is assumed to be true
- Unrestricted intake — agents may research any source type
- Bounded execution — source limits and time bounds enforced by session governance
- 20-session retention — recent sessions available, older sessions archived

**The distinction that matters:** The notebook is fuel, not truth. What becomes truth is only what survives the full agent exchange, empirical arbitration, and explicit human approval.

---

## 05 — Material Warrant

**Definition:** A typed, source-locked, provenance-chained claim record — the minimum viable unit of knowledge that may cross an agent boundary or reach the Promotion Boundary.

**Required fields:**
- `claim_text` — what is being asserted
- `claim_type` — EMPIRICAL / CAUSAL / STRATEGIC / THEORETICAL / REGULATORY
- `source_id` — resolves to a retrievable document in the agent's notebook
- `source_location` — specific location within the source
- `confidence` — VERIFIED / HIGH / MARGINAL / UNVERIFIED
- `provenance_chain` — full lineage from source to assertion
- `agent_id` — which agent generated this warrant
- `exchange_step` — at which exchange step this was produced
- `hitl_approval_id` — populated only after HITL approval

**The rule:** No source, no claim. A claim without a Material Warrant does not cross any agent boundary. It is blocked by the Orchestration Layer and returned for correction. There is no flag-and-pass path.

---

## 06 — Promotion Boundary

**Definition:** The non-bypassable gate between exploration material and validated system memory — crossable only through explicit HITL approval.

**What the boundary separates:**

```
EXPLORATION (everything before the boundary)
  Notebook corpus content
  Exchange proposals and critiques
  D3 judgments and SDM outputs
  
VALIDATED KNOWLEDGE (everything after)
  HITL-approved hypotheses in SIM
  Locked hypotheses in testing pipeline
```

**The invariant:** No automated process can promote material across the Promotion Boundary. Not high confidence scores. Not unanimous model agreement. Not multiple successful exchange runs. HITL approval is the only key.

---

## 07 — Dissent Archive

**Definition:** The permanent, structured preservation system for all non-promoted exchange outputs — including proposals that failed pre-flight, packages that received HITL ARCHIVE decisions, and the losing proposals from completed exchanges.

**Three functions:**

1. **Temporal reference** — ideas assessed as impractical today may become viable as infrastructure evolves; the archive preserves the reasoning and the conditions that blocked each idea
2. **Calibration signal** — patterns in archived proposals reveal systematic tendencies in the system's evaluation criteria
3. **Cross-run analysis** — enables systematic comparison across different model-role permutations

**What the archive is not:** Not a graveyard. Not a failure record. It is a time-delayed research queue whose value grows as the technological landscape shifts.

---

## 08 — Orchestration Layer

**Definition:** The deterministic transport and sequencing infrastructure of the framework — a finite state machine with exactly five permitted functions and a complete prohibition on interpretation.

**Five permitted functions:**
1. Route packages between agents in defined sequence
2. Enforce role order
3. Preserve provenance chain of every output
4. Trigger skill execution at defined points
5. Record movement events to the audit log

**Complete prohibitions:** The Orchestration Layer may not summarize, interpret, filter, rank, reason about, or mutate any content in transit. Any orchestrator that interprets content becomes an undeclared fourth agent — introducing bias that cannot be audited.

**The doctrine:** The Orchestration Layer moves packages. It does not understand them.

---

## 09 — Human-in-the-Loop (HITL)

**Definition:** The non-automatable decision boundary that evaluates structured research artifacts and determines whether they are approved, returned, archived, or escalated — with approval being the only event that triggers system memory updates.

**Four decision types:**

| Decision | What It Does |
|----------|-------------|
| **APPROVE** | Locks hypothesis, triggers SIM write, routes to testing pipeline |
| **RETURN** | Routes package back to specified exchange step with reviewer notes |
| **ARCHIVE** | Routes package to Dissent Archive with optional annotation |
| **ESCALATE** | Holds package pending resolution of a governance concern |

**What only the human can decide:**
- Which measured distances are worth crossing
- Whether novelty outweighs feasibility in strategic context
- Whether the empirical consensus being measured against is itself flawed
- Whether the system's evaluation criteria need recalibration

**The doctrine:** HITL is the only layer that converts validated reasoning into system memory. Everything before it produces candidates. HITL produces truth.

---

## 10 — Behavioral Deviation Risk Model (BDRM)

**Definition:** The domain-agnostic behavioral governance substrate running beneath all system components — a five-layer signal chain that captures behavioral events, detects deviation patterns, compares against defined constraints, produces risk scores, and gates the next action.

**Five layers:**

| Layer | Function | Elosia Expression |
|-------|----------|-------------------|
| **01 Capture** | Track actions, not intent | Common Log of Events |
| **02 Pattern** | Repetition is the signal | Trust scoring + drift detection |
| **03 Compare** | Does this deviate? | Policy validation against SMK |
| **04 Score** | Probability, not verdict | Discrete trust state enums |
| **05 Gate** | Detection without enforcement is incomplete | MicroManager + HITL + Promotion Boundary |

**The founding principle:** The pattern stays the same. The output changes. The same five-layer enforcement pattern that governs agent behavior in a research exchange also governs behavior in financial compliance, healthcare authorization, and enterprise governance. The actor changes. The enforcement pattern does not.

---

## Attribution

Gary Phillips
ElosiaEcosystem Inc.
Canonical Definitions — Structured Distance Measurement Framework
Version 1.2 | May 2026

*Released under CC BY-NC 4.0. Attribution required for all uses.*
