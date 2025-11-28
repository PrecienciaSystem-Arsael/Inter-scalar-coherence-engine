# Inter-Scalar Coherence Engine (ISC Engine)
## ARCHITECTURE — Version 1.2

Internal Engine Name: **PrecienciaEngine v1.2**  
External Product Name: **Inter-Scalar Coherence Engine (ISC Engine)**  
Contact: **precienciasystem@gmail.com**

---

# 1. High-Level Architecture

ISC Engine v1.2 is a **hybrid neural–symbolic structural coherence system**.  
It evaluates text across four scalar layers simultaneously:

1. **Geometric Layer (Encoder v5)** — structure-bearing embeddings  
2. **Dynamic Layer (Engine v4)** — invariance metrics over perturbations  
3. **Topological Layer (Macro-Field v6b)** — 12 symbolic structural domains  
4. **Symbolic Layer (Rules v2)** — explicit reasoning and pattern detection  
5. **Decision Layer (Label Fusion v4)** — final structural classification  

v1.2 is **frozen**, **deterministic**, and validated across:
- **KV-3:** 20/20 correct (100%)  
- **RW-20:** 18/20 correct (~90%)  
- **RW-40:** 35/40 correct (87.5%) — errors isolated to high-polish corporate & obedience frames  

---

# 2. Pipeline (Full Data Flow)

Input Text
│
▼
[1] Encoder v5  — geometric embedding (1024-dim)
→ sim_POS / sim_NEG
→ margin = sim_POS - sim_NEG
│
▼
[2] Engine v4 — invariance dynamics
→ Δκ_cycle          (curvature stability)
→ |∮DoM·dt|         (directional drift)
→ ΔI_reentry        (semantic return deviation)
→ max(0, dH/dt)     (entropy instability)
→ S_sim             (cycle similarity)
→ C (coherence cost)
→ coherence_score = exp(−C)
│
▼
[3] Macro-Field v6b — topology match
→ 12-domain symbolic mapping
→ top_macro + cosine similarity
│
▼
[4] Symbolic Rules v2 — explicit structural reasoning
→ rule activations (POS/NEG/NON indicators)
→ pos_score / neg_score / non_score
→ flags (axis, return, drift, heteronomy…)
│
▼
[5] Label Fusion v4 — final decision logic
→ final_class (POS / NEG / NON)
→ internal_label (Preciencia / Ally / Inverted / Non)
→ public_label (for demos)


---

# 3. Component Specification

## 3.1 Encoder v5 — Geometry of Meaning  
**Path:** `models/preciencia_encoder_v5/`

Base: **multilingual-e5-large**  
Trained on structural corpus v4/v6 (POS, NEG, NON distinctions).  
Output: **1024-dim L2-normalized embedding**.

The encoder *does not classify*.  
It provides structural geometry for invariance testing.

---

## 3.2 Engine v4 — Dynamic Invariance Core  
**Path:** `engine/preciencia_engine_v4.py`  
**Role:** compute invariants that quantify structural coherence under perturbation.

Invariants:

Δκ_cycle          # curvature consistency
|∮DoM·dt|         # accumulated directional drift
ΔI_reentry        # reentry deviation
max(0, dH/dt)     # entropy instability
S_sim             # closed-loop similarity

Coherence cost:

C = λ1·Δκ + λ2·|DoM| + λ3·ΔI + λ4·max(0,dH/dt) + λ5·(1 − S_sim)

Final metric:

λ are FIXED in v1.2.

---

## 3.3 Macro-Field Topology v6b — Symbolic Domains  
**Path:** `preciencia_dataset_v6b.json`

12 macro fields (proportional symbolic topologies):

- **M0** Amor estructural  
- **M1** Artificial-global system  
- **M2** Micro-mechanics / local saturation  
- **M3** Imaginal field  
- **M4** OBS / Soma  
- **M5** Direction-of-Meaning field  
- **M6** Symbolic operation  
- **M7** Proportion ∿  
- **M8** Laws 0–6  
- **M9** Laws 7–10  
- **M10** Laws 11–14  
- **M11** Preciencia core  

Macro selection uses prototype embeddings (cosine distance).

---

## 3.4 Symbolic Rules v2 — Explicit Reasoning Layer  
**Path:** `preciencia_symbolic_rules_v2.py`  
**Function:** `analyze_symbolic_v2(text)`

Rules detect structural patterns not visible to geometry alone:

### POS-oriented
- AxisFirst  
- ReturnClosure  
- ProportionalConstraint  
- InternalValidation  

### NEG-oriented
- Heteronomy  
- AntiStructure  
- OpenLoopDrift  
- QuantumEmotionPseudo  
- CorporateSimulacrum  
- CorporateGuarantee  

### NON-oriented
- MetaphorFloat  
- NonAnchoredSurreal_v2  
- EmptyAbsolutes  

Each rule returns weights:

pos_weight
neg_weight
non_weight

plus symbolic tags and a human-readable description.

Symbolic Layer v2 does **not override** metric-based decisions unless Label Fusion v4 explicitly triggers.

---

## 3.5 Label Fusion v4 — Decision Logic  
**Path:** `engine/preciencia_label_fusion_v4.py`  
**Function:** `fuse_labels_v4()`

Combines:
- Encoder v5 polarity  
- Engine v4 invariance metrics  
- Macro-field domain  
- Symbolic rule scores  

Final outputs:
- **final_class** (POS / NEG / NON — simple polarity)  
- **internal_label** (Preciencia / Structural Ally / Inverted / Non-Structured)  
- **public_label** (external-facing)  

Overrides include:
- **Structural Ally rescue** (for misclassified POS cases with rule-based coherence)  
- **Inverted/Simulacrum override** (heteronomy, drift, pseudo-quantum)  
- **Non-Structured detection** (non_score ≥ 0.7 + no axis/proportion/return)  

v4 ensures **deterministic reproducibility**.

---

# 4. Directory Layout

PrecienciaEngine_v13/
│
├── preciencia_cli_v1_2.py
├── preciencia_api_v1.py
│
├── engine/
│   ├── preciencia_engine_v1_2.py
│   ├── preciencia_engine_v4.py
│   ├── preciencia_eval_bundle_v1.py
│   ├── preciencia_label_fusion_v4.py
│   └── …
│
├── preciencia_symbolic_rules_v2.py
│
├── models/
│   ├── preciencia_encoder_v5/
│   └── preciencia_prototypes_v5.npz
│
├── preciencia_dataset_v6b.json
├── preciencia_eval_kv3_v3.py
├── preciencia_eval_rw20_v1.py
├── preciencia_eval_rw40_v1.py
│
└── README.md / README_dev.md

---

# 5. Architectural Guarantees

### **Reproducibility**
- Encoder v5, Engine v4, Symbolic v2, Fusion v4 are frozen  
- All transforms deterministic  
- KV-3 and RW-40 performance matches published benchmarks  

### **Explainability**
- Symbolic rules show *why* something is NEG/NON  
- Macro-fields show topological alignment  
- Engine metrics quantify exact structural deviation  

### **Inter-Scalar Coherence**
Evaluates structural proportion across:

- local geometry  
- dynamic invariance  
- symbolic topology  
- explicit reasoning  

This makes ISC Engine unlike any standard NLP classifier.

---

# 6. Planned Extensions (v1.3 → v2.0)

- REST API + mini dashboard  
- RW-40 → RW-100 expansion  
- LLM integration (logit filter, output verifier)  
- Expanded symbolic rules for legal/scientific language  
- Encoder v7 (multi-channel structural embeddings)  
- Visualizations for embedding transformations  

---

# 7. Summary

ISC Engine v1.2 is a **frozen, reproducible, hybrid neural–symbolic architecture** capable of detecting:

- proportional coherence  
- structural inversion  
- rhetorical simulacrum  
- non-anchored drift  

across a multi-layer pipeline.

It is designed as a **coherence verification layer** for:  
AI safety, enterprise communication, reasoning engines, and editorial tools.

---

**End of Architecture Document (v1.2)**  
