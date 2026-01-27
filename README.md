# RefStyleCap: Reference-Guided Style-Aware Image Captioning

This repository contains the official implementation of:

> **RefStyleCap: Reference-Guided Style-Aware Image Captioning**  
> *Authors:* [Siddhesh Sanjay Hemangi Varpe, Sudesh Rani, Mayank Gupta]   
> [Paper PDF] | [Dataset]

---

## 🔍 Overview

Image captioning methods have evolved from traditional CNN–RNN architectures to transformer-based vision–language models, shifting emphasis from basic descriptive accuracy toward stylistic control and contextual awareness. Despite these advances, generating captions that are both image-grounded and stylistically aligned with narrative-intensive domains remains challenging.

This paper introduces **RefStyleCap**, a **reference-guided, style-aware image captioning framework**, evaluated on the **Harry Potter universe** as a highly constrained narrative domain.

RefStyleCap is a **multi-stage pipeline** consisting of:

1. **Visual Grounding**  
   Baseline captions are generated using different variants of pre-trained **BLIP** models. These are then fine-tuned on **domain-specific movie stills** to improve factual accuracy and visual relevance.

2. **Domain Specialization**  
   BLIP models are further adapted using Harry Potter movie frames and related metadata to better capture domain-specific visual semantics.

3. **Stylistic Adaptation**  
   The fine-tuned captions are transformed to match the **literary tone of the Harry Potter novels** using:
   - A **two-stage adapted BART** (Bidirectional and Auto-Regressive Transformers) model  
   - A **prefix-tuned FLAN-T5** (Finetuned Language Net) model  
   Both models are trained on the book corpus.

4. **Reference Validation**  
   Caption consistency is checked against narrative references to evaluate alignment with the story context.

---

## ✨ Key Contributions

- A **systematic, multi-stage pipeline** for reference-guided stylistic captioning  
- Integration of **visual grounding + literary style transfer + narrative validation**  
- Domain-specific fine-tuning of BLIP for improved factual relevance  
- Two stylistic adaptation strategies: **BART-based** and **FLAN-T5-based**  
- Hybrid evaluation using:
  - Lexical metrics (e.g., METEOR)  
  - Semantic similarity (sentence embeddings)  
  - Qualitative analysis  
  - LLM-as-a-Judge framework  

---

## 📊 Results

The proposed RefStyleCap framework consistently outperforms baseline and intermediate models.

| Our Model                      | METEOR ↑ | Cosine Similarity ↑  |
| **RefStyleCap (BART)**         | **50.95**| **61.58**            |

**Key Observation:**  
The **BART-based stylistic adaptation** variant achieves the best overall performance, demonstrating that reference-based stylistic transfer in a structured pipeline produces captions that are:

- Visually accurate  
- Context-aware  
- Stylistically expressive  

---
