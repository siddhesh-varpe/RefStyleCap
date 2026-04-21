# RefStyleCap: Reference-Guided Style-Aware Image Captioning

> **Official implementation of:**
> RefStyleCap: Reference-Guided Style-Aware Image Captioning
>
> *Authors:* Siddhesh Sanjay Hemangi Varpe · Sudesh Rani · Mayank Gupta

![NLP](https://img.shields.io/badge/Domain-NLP%20%26%20Computer%20Vision-purple?style=flat-square)
![Style Transfer](https://img.shields.io/badge/Task-Style--Aware%20Captioning-teal?style=flat-square)
![Models](https://img.shields.io/badge/Models-BLIP%20%7C%20BART%20%7C%20FLAN--T5-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Research-orange?style=flat-square)

📄 [Paper PDF](#) · 📦 [Dataset](#)

---

## Overview

Image captioning has evolved from basic CNN–RNN architectures to transformer-based vision–language models, shifting emphasis from descriptive accuracy toward stylistic control and contextual awareness. Yet generating captions that are both image-grounded **and** stylistically aligned with narrative-intensive domains remains a hard, unsolved problem.

**RefStyleCap** is a **reference-guided, style-aware image captioning framework** that tackles this challenge head-on — evaluated on the **Harry Potter universe** as a highly constrained narrative domain.

The core idea: rather than generating generic descriptions, RefStyleCap produces captions that read as if written by the author of the story — visually accurate, contextually aware, and stylistically expressive.

---

## Pipeline

RefStyleCap is a **4-stage multi-model pipeline**:

![Image](SimpleVSProposed1.drawio.png)

---

## Key Contributions

- A **systematic, multi-stage pipeline** for reference-guided stylistic image captioning
- Integration of **visual grounding + literary style transfer + narrative validation** in a single framework
- Domain-specific fine-tuning of BLIP on Harry Potter movie frames for improved factual relevance
- Two stylistic adaptation strategies: **BART-based** (two-stage) and **FLAN-T5-based** (prefix-tuned)
- Hybrid evaluation using lexical metrics, semantic similarity, qualitative analysis, and an **LLM-as-a-Judge** framework

---

## Results

The RefStyleCap framework consistently outperforms baseline and intermediate models across all evaluation metrics.

| Model | METEOR ↑ | Cosine Similarity ↑ |
|-------|----------|----------------------|
| **RefStyleCap (BART)** | **50.95** | **61.58** |

The **BART-based stylistic adaptation** variant achieves the best overall performance, demonstrating that reference-based stylistic transfer in a structured pipeline produces captions that are:

- Visually accurate
- Context-aware
- Stylistically expressive

---

## Evaluation Methods

| Method | Purpose |
|--------|---------|
| **METEOR** | Lexical alignment with reference captions |
| **Cosine Similarity** | Semantic closeness via sentence embeddings |
| **Qualitative Analysis** | Human assessment of style and fluency |
| **LLM-as-a-Judge** | Automated scoring of stylistic quality and alignment |

---

## Models Used

| Model | Role |
|-------|------|
| **BLIP / BLIP-Large** | Visual grounding — baseline caption generation |
| **Fine-tuned BLIP** | Domain specialization on HP movie stills |
| **BART** | Two-stage stylistic adaptation |
| **FLAN-T5** | Prefix-tuned stylistic adaptation |

---

## Citation

If you use this work, please cite:

```bibtex
@article{refstylecap2024,
  title     = {RefStyleCap: Reference-Guided Style-Aware Image Captioning},
  author    = {Varpe, Siddhesh Sanjay Hemangi and Rani, Sudesh and Gupta, Mayank},
  year      = {2024}
}
```

---

## Authors

| Name | Contact |
|------|---------|
| Siddhesh Sanjay Hemangi Varpe | — |
| Sudesh Rani | — |
| Mayank Gupta | — |

---

*Research project · More details coming soon*
