# Text-based Scalable Deep Generative Modelling

This repository is for a dissertation project on **scalable deep generative modelling for text**.  
The core aim is to design and evaluate a state-of-the-art generative model that balances:
- sample quality,
- diversity,
- generation speed,
- and scalability to larger datasets / model sizes.

---

## 1) Project Description

Deep generative models (Flows, VAEs, AR models, DDPMs, GANs) learn data distributions with different trade-offs in:
- training and inference cost,
- mode coverage and diversity,
- controllability,
- and architectural constraints.

This project focuses on **text-based generation**, with two possible directions:
1. **Theoretical direction**: study objective functions, inductive biases, and symmetry/structure constraints that improve scaling behavior.
2. **Applied direction**: build a practical model stack inspired by recent ICLR/NeurIPS/ICML work and demonstrate strong results on text datasets.

---

## 2) Literature Review

### 2.1 Background: Families of Deep Generative Models

The review paper by Bond-Taylor et al. (2021) provides a unified comparison of:
- **VAEs**: stable training and fast sampling, but often blurrier generations and ELBO gap limitations.
- **GANs**: high perceptual fidelity but training instability and mode collapse risks.
- **Normalizing Flows**: exact likelihood and invertibility, but architectural constraints and memory/computation trade-offs.
- **Autoregressive (AR) Models**: strong likelihood modelling and text quality, but sequential decoding can be slow.
- **Energy-Based Models**: flexible formulations, but sampling and training can be expensive.

**Key implication**: no single family dominates on all axes; practical systems often require hybridization or objective-level innovation.

### 2.2 Scalability Challenge in Text Generation

For text generation, scaling bottlenecks are usually caused by:
- long-context dependence,
- token-by-token decoding latency,
- memory growth with model depth/width,
- and optimization instability at larger batch/model scales.

Recent trends suggest that scalability improves when architecture, training objective, and sampling procedure are co-designed (instead of optimizing only one component).

### 2.3 Diffusion / Flow-Matching Trend

Modern diffusion and flow-matching frameworks are increasingly explored for discrete or continuous text representations due to:
- better controllability of generation trajectory,
- potential parallelism in denoising steps,
- and compatibility with distillation / acceleration techniques.

However, they still face efficiency barriers compared with strong autoregressive baselines unless acceleration methods are integrated.

### 2.4 Gaps to Address

From the current literature, important open questions remain:
1. How to retain AR-level quality while improving sampling throughput.
2. How to evaluate quality-diversity-efficiency jointly rather than with a single metric.
3. How to make training/inference costs reproducible and comparable across model families.

This project targets these gaps via a unified benchmark and a scalable model design.

---

## 3) Reference

- Bond-Taylor, S., Leach, A., Long, Y., & Willcocks, C. G. (2021).  
  **Deep Generative Modelling: A Comparative Review of VAEs, GANs, Normalizing Flows, Energy-Based and Autoregressive Models**.  
  URL: https://arxiv.org/pdf/2103.04922.pdf

---

## 4) Project Plan

## Phase 1 — Scoping & Reading (Week 1-2)

**Goals**
- Finalize research question and hypothesis for scalable text generation.
- Build annotated reading list (ICLR/NeurIPS/ICML + core survey papers).
- Define target benchmark datasets and compute budget.

**Deliverables**
- Problem statement (1 page).
- Literature matrix (model family × quality × speed × compute).

## Phase 2 — Baseline Reproduction (Week 3-4)

**Goals**
- Reproduce at least two strong baselines (e.g., AR transformer + diffusion/flow baseline).
- Standardize preprocessing, tokenization, and evaluation pipeline.

**Deliverables**
- Reproducible training scripts/configs.
- Baseline table with quality and efficiency metrics.

## Phase 3 — New Model Design (Week 5-7)

**Goals**
- Propose scalable architecture/objective (or hybrid inference scheme).
- Implement training and sampling pipeline with profiling hooks.

**Deliverables**
- Model spec and ablation plan.
- Initial results on a small benchmark split.

## Phase 4 — Full Experiments & Ablations (Week 8-10)

**Goals**
- Run full-scale experiments and ablations.
- Compare against baselines under matched compute settings.

**Deliverables**
- Main results table.
- Ablation studies (objective, depth/width, sampling steps, distillation/acceleration).

## Phase 5 — Analysis & Robustness (Week 11)

**Goals**
- Analyze trade-offs: quality vs diversity vs throughput vs memory.
- Test robustness across dataset domains and sequence lengths.

**Deliverables**
- Error analysis and failure-case taxonomy.
- Robustness appendix material.

## Phase 6 — Writing & Finalization (Week 12)

**Goals**
- Consolidate methodology, experiments, and discussion.
- Finalize dissertation narrative and reproducibility checklist.

**Deliverables**
- Final dissertation draft.
- Clean code release notes and experiment logs.

---

## 5) Anticipated Outcomes

- A deep generative model that generates **high-quality text samples** efficiently.
- Clear evidence of scalability improvements (quality-speed-compute trade-off).
- Reproducible benchmark and ablation framework for future extension.

---

## 6) Requirements / Prerequisites

- Prior completion (or current enrollment) in an advanced deep learning module (e.g., L3 Deep Learning).
- Equivalent background acceptable (MISCADA route): strong foundations in statistics, calculus, and geometry.

---

## 7) Keywords

- GANs
- Flow Matching
- DDPMs
- Variational Autoencoders
- Autoregressive Models
- Text Generation
- Scalable Deep Learning
