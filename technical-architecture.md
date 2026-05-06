# Technical Architecture Overview
## Structured Distance Measurement Framework

**ElosiaEcosystem Inc. | Gary Phillips**
**Version 1.0 | May 2026**
**License: CC BY-NC 4.0 (Conceptual layer)**

> This document describes the conceptual architecture of the SDM framework at the level required to understand how the system operates. Implementation details of the operational substrate remain proprietary. See [LICENSING.md](../LICENSING.md) for the boundary.

---

## The Information Lifecycle

The SDM framework is a governed cartographic instrument. Information moves through it in one direction — from raw exploration toward validated memory — and can only cross each boundary under specific conditions.

```
RAW SOURCE
  (any material — academic, fringe, preprint, contested)
        ↓ agent research
NOTEBOOK CORPUS
  (private per agent — zero trust — exploration fuel only)
        ↓ structured into proposals via Disruptor Exchange
EXCHANGE PACKAGE
  (D1 proposal + D2 critique + D2 counter + D1 notes + D3 judgment)
        ↓ automated pre-flight verification
PROMOTION BOUNDARY
  (non-bypassable — HITL only)
        ↓ HITL APPROVE decision only
VALIDATED MEMORY (SIM)
  (per-agent — append-only — full provenance chain)
```

**Two zones separated by the Promotion Boundary:**

| Zone | Character | Authority |
|------|-----------|-----------|
| Exploration | Zero-trust, unrestricted intake, fuel not truth | None — everything is skeptical input |
| Validated | Append-only, HITL-approved, provenance-locked | HITL approval event only |

Nothing crosses from exploration to validated without passing through the complete exchange loop and explicit human approval.

---

## Platform Layer Map

```
┌─────────────────────────────────────────────────────────┐
│                SMK — Governance Layer                    │
│  Role boundaries · Behavioral mandates · Policy book     │
│  Read at init · Consulted on drift · Never during research│
└─────────────────────────────────────────────────────────┘
         ↓ read at initialization
┌──────────────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
│  DISRUPTOR-1  │   │  DISRUPTOR-2  │   │  DISRUPTOR-3  │   │     HITL     │
│Radical Proposer│   │  Dialectical  │   │  Empirical    │   │  Human       │
│               │   │  Challenger   │   │  Arbiter      │   │  Reviewer    │
│Private Notebook│→  │Private Notebook│→  │Full Package   │→  │Full Package  │
│SIM read (init)│   │SIM read (init)│   │               │   │              │
└──────────────┘   └──────────────┘   └──────────────┘   └──────────────┘
         ↕                  ↕                  ↕                  ↕
┌─────────────────────────────────────────────────────────────────────────┐
│              ORCHESTRATION LAYER                                         │
│  Route · Enforce sequence · Preserve provenance · Trigger · Record       │
│  ZERO interpretation · ZERO mutation · ZERO summarization                │
└─────────────────────────────────────────────────────────────────────────┘
         ↓                                    ↓                  ↓
┌──────────────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
│   NOTEBOOK   │   │  PROMOTION   │   │     SIM      │   │   DISSENT    │
│   CORPUS     │   │  BOUNDARY    │   │  (per agent) │   │   ARCHIVE    │
│  Zero trust  │   │  Pre-flight  │   │  Validated   │   │  Non-promoted│
│  Exploration │   │  HITL only   │   │  Memory      │   │  Outputs     │
└──────────────┘   └──────────────┘   └──────────────┘   └──────────────┘
         ↕                  ↕                  ↕                  ↕
┌─────────────────────────────────────────────────────────────────────────┐
│              BDRM ENFORCEMENT SUBSTRATE                                  │
│  Capture → Pattern → Compare → Score → Gate                              │
│  "The pattern stays the same. The output changes."                       │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## The Disruptor Exchange — Five-Step Loop

The exchange is not a conversation. It is a structured adversarial process with defined inputs, defined outputs, and defined verification criteria at each step.

```
STEP 1 — D1 PROPOSAL
  Input:   Research question + notebook corpus + SIM (read-only at init)
  Output:  Assumption challenged + proposed alternative +
           minimal experiment + success/failure criteria +
           Material Warrants for every claim
  Gate:    Orchestration Layer verifies warrant completeness
           before Step 2 begins

STEP 2 — D2 REVIEW + COUNTER-PROPOSAL
  Input:   D1 proposal (complete)
  Output:  DOCUMENT 1: Critique (assumption D1 failed to escape)
           DOCUMENT 2: Counter-proposal (competing paradigm)
           These are separate documents — not one merged output
  Gate:    Semantic distance check between D1 and D2 outputs
           (convergence below threshold = protocol violation)

STEP 3 — D1 REVIEW NOTES
  Input:   D2 critique + D2 counter-proposal
  Output:  Review notes — not a rewrite
           D1 original proposal: UNCHANGED (hash-verified)
  Gate:    Hash comparison confirms D1 proposal unmodified
           Any modification = protocol violation, run suspended

STEP 4 — PACKAGE ASSEMBLY
  Actor:   Orchestration Layer only
  Action:  Collect all outputs from Steps 1-3 intact
           Generate exchange hash
           Attach session metadata and warrant records
  Constraint: Zero interpretation. Zero modification.
              The package contains exactly what agents produced.

STEP 5 — D3 EMPIRICAL ARBITRATION
  Input:   Complete assembled package
  Output:  Stronger proposal identified
           Basis for judgment against three criteria
           Structured Distance Measurement (SDM)
           Dissent routing instructions
           HITL briefing (plain language — not a recommendation)
  Constraint: No synthesis. No hybrid. D3 judges — it does not create.
```

---

## The Three Evaluation Criteria (D3)

D3 evaluates both proposals against three criteria. Every element of D3's judgment must be traceable to one of these three.

| Criterion | What It Measures |
|-----------|-----------------|
| **Empirical Grounding** | Is the proposal grounded in current research? Do Material Warrants resolve to real sources? Does it accurately characterize the current state of the field? |
| **Engineering Feasibility** | Can it be implemented with current hardware and tooling? If not, what specific capabilities are missing? Is the gap scale, missing primitives, or physics constraints? |
| **Testability of Validation Path** | Is the minimal experiment actually minimal? Can it run with current resources? Does the success criterion confirm the core claim or something adjacent to it? |

---

## The Orchestration Layer — What It Is and Is Not

The Orchestration Layer is the most misunderstood component of the framework. It is not a coordinator. It is not a manager. It is a deterministic finite state machine.

**Five permitted functions — exhaustive:**

| Function | Description |
|----------|-------------|
| Route | Move packages between components in defined sequence |
| Enforce | Verify step completion before next step begins |
| Preserve | Append routing records to provenance chain |
| Trigger | Invoke skills at defined points with defined inputs |
| Record | Log every action to the audit trail |

**Complete prohibitions:**

The Orchestration Layer may not:
- Summarize any content
- Interpret any content
- Filter any content
- Rank any content
- Reason about any content
- Modify any field in any package

> Any orchestrator that interprets content becomes an undeclared fourth agent introducing unauditable bias. The orchestrator moves reasoning artifacts. It does not understand them.

---

## The Human-in-the-Loop Boundary

The HITL layer is not a reviewer of system outputs. It is the system's most consequential component — the only boundary that converts validated reasoning into system memory.

**What HITL receives:**

The complete exchange package — not a summary, not a recommendation. The human receives:
- Both proposals with full reasoning chains
- The complete cross-review record
- The empirical arbitration and SDM
- All Material Warrants with provenance chains
- The pre-flight verification results

**The four non-delegable decisions:**

These decisions are explicitly reserved for human judgment because they require strategic context the system does not have access to:

1. Which measured distances are worth crossing (depends on resources, timing, organizational priorities)
2. Whether paradigm depth outweighs near-term feasibility (contextual, not algorithmic)
3. Whether the measured consensus is itself correct (the human is the check on D3's empirical anchoring)
4. Whether the system's evaluation criteria need recalibration (only the human can identify and act on systematic patterns)

---

## Memory Architecture

### SIM — Per-Agent Validated Memory

```
/sim/{agent_id}/
  active/          ← current validated knowledge
    {entry_id}.json
  archive/         ← superseded entries (markdown)
    {entry_id}_{date}.md
  index.json       ← append-only entry index
  integrity.json   ← SHA-256 hash chain
```

**Key properties:**
- Append-only — no deletion ever
- HITL-exclusive writes — the only write source
- Per-agent isolation — no cross-agent reads
- Full provenance — every entry carries complete chain

### SMK — System-Wide Governance

```
/smk/
  governance/      ← framework specifications
  behavioral-mandates/  ← how agents must behave
  amendment-log/   ← every change recorded before it takes effect
```

**Key properties:**
- Never derived from agent learning
- Updated only through governance amendments
- Read at initialization — not during research
- SIM-to-SMK transfer: architecturally impossible

---

## Behavioral Governance — BDRM

Running beneath every system component is the Behavioral Deviation Risk Model — a five-layer enforcement substrate that monitors behavior, detects deviation, compares against policy, produces risk scores, and gates actions.

```
LAYER 01 — CAPTURE
  Every action logged in real time
  Append-only audit spine
  No action is uncaptured

LAYER 02 — PATTERN
  Repetition is the signal
  Frequency analysis across runs
  Velocity detection for accelerating deviation

LAYER 03 — COMPARE
  Observed patterns vs defined constraints
  Not "is this bad?" — "does this deviate?"
  Policy-based, objective, binary at event level

LAYER 04 — SCORE
  Discrete auditable states (not opaque floats)
  TRUSTED → STABLE → DEGRADED → UNTRUSTED
  Every state traceable to observable behavioral events

LAYER 05 — GATE
  Fires before next action
  Proportional response to risk level
  HIGH and CRITICAL: human authorization required
  No automated recovery from CRITICAL
```

**The founding principle:**
> The pattern stays the same. The output changes.

The same five-layer pattern governs AI agents in a research exchange, servicers in mortgage compliance, providers in healthcare authorization, and employees in enterprise governance. The enforcement substrate is domain-agnostic. Only the vocabulary changes.

---

## Role Permutation

A single exchange run assigns one model to each Disruptor role. After the run completes, model assignments rotate — so that the model acting as D1 in Run A acts as D2 or D3 in Run B.

**Why this matters:**

- Separates model bias from role bias
- Generates cross-run signal about model-role interaction
- When different models produce structurally similar proposals in the same role, that convergence is evidence about the problem — not the model

**The validation finding:**

Live runs on attention mechanism replacement demonstrated this. Two different model-role permutations independently produced the same paradigm split — discrete-structural vs continuous-dynamic computation. That cross-run convergence confirmed the split as a genuine feature of the problem space, not a model artifact.

---

## Attribution

Gary Phillips
ElosiaEcosystem Inc.
Technical Architecture Overview — Structured Distance Measurement Framework
Version 1.0 | May 2026

*Conceptual architecture released under CC BY-NC 4.0.*
*Operational substrate implementation details are proprietary.*
*See [LICENSING.md](../LICENSING.md) for complete terms.*
