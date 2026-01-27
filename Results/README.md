# Results and Discussion — RefStyleCap

This document summarizes the experimental results and key findings of the RefStyleCap framework. We evaluate the proposed multi-stage pipeline using:

- Automatic quantitative metrics  
- Sentence-level semantic similarity  
- Lexical diversity measures  
- LLM-as-a-Judge qualitative evaluation  
- Qualitative interpretability analyses  

The goal is to assess how visual grounding, domain fine-tuning, and stylistic adaptation contribute to caption quality.

---

## 1️⃣ Evaluation Overview

We evaluate captions using three complementary perspectives:

### 1. Quantitative Metrics  
Used to measure lexical overlap, fluency, and semantic similarity with reference captions:

- BLEU-4  
- METEOR  
- ROUGE-L  
- BERTScore  
- Cosine similarity using sentence embeddings  

---

### 2. Qualitative Evaluation (LLM-as-a-Judge)

An external large language model (Gemini 2.5 Flash) is used to rate captions on a 1–5 scale using the following criteria:

- Factual Accuracy  
- Fluency & Coherence  
- Depth & Nuance  
- Style Following  
- Lexical Diversity (when applicable)  

---

### 3. Diversity & Richness Metrics

Lexical diversity is measured using:

- Type–Token Ratio (TTR)  
- Distinct-1  
- Distinct-2  
- Entropy  

These metrics quantify vocabulary breadth, phrase-level variation, and information richness.

---

## 2️⃣ Stage-Wise Model Performance

We evaluate captions at multiple stages of the pipeline:

- Raw BLIP models  
- Fine-tuned BLIP models  
- Style-adapted models (BART and FLAN-T5)  

---

### 🔹 Raw BLIP Models

- BLIP-Large consistently outperforms BLIP-Base across most metrics  
- Larger model capacity leads to:
  - Better fluency  
  - Improved factual accuracy  
  - Stronger semantic alignment  

However, both raw variants show:

- Low lexical overlap with reference captions  
- Weak alignment with domain-specific narrative style  

This indicates that pretrained captioning alone is insufficient for narrative-intensive domains.

---

### 🔹 Fine-Tuned BLIP Models

Fine-tuning BLIP on domain-specific image–caption pairs yields consistent improvements:

- Higher BLEU and METEOR scores  
- Improved cosine similarity with reference text  
- More accurate and relevant captions  

These gains show that domain adaptation improves:

- Vocabulary usage  
- Contextual grounding  
- Visual–text alignment  

However, fine-tuning alone does not fully capture:

- Narrative tone  
- Stylistic structure of the target corpus  

---

### 🔹 Style-Adapted Models

The most substantial improvements occur after stylistic adaptation.

#### BART-Based Style Transfer

- Achieves the best overall performance across:
  - Lexical overlap metrics  
  - Semantic similarity  
  - Sentence-level fluency  
- Produces captions that:
  - Match narrative tone  
  - Preserve visual semantics  
  - Exhibit strong lexical and syntactic structure  

This confirms that BART’s denoising-style pretraining is well suited for controlled rewriting and paraphrasing.

---

#### FLAN-T5-Based Style Transfer

- Improves over fine-tuned BLIP in:
  - Semantic similarity  
  - Fluency  
- Performs substantially worse than BART in:
  - Lexical overlap  
  - Narrative coherence  
  - Stylistic consistency  

This suggests that instruction tuning alone offers weaker control over fine-grained narrative style.

---

## 3️⃣ Key Quantitative Findings

Across all evaluated models:

- BLIP-Large > BLIP-Base at every pipeline stage  
- Fine-tuned BLIP > Raw BLIP  
- BART-Style > FLAN-T5-Style > Fine-Tuned BLIP  

Overall conclusions:

- Visual grounding improves correctness  
- Domain fine-tuning improves relevance  
- Style transfer improves narrative alignment  
- BART provides the strongest stylistic control  

---

## 4️⃣ LLM-as-a-Judge Evaluation

The LLM-based evaluator confirms trends observed in quantitative metrics.

### Observed Patterns

- BLIP-Large outperforms BLIP-Base in:
  - Factual accuracy  
  - Fluency  
  - Depth  

- Fine-tuned BLIP variants:
  - Achieve uniformly high scores  
  - Reduce the performance gap between Base and Large  

- BART-based captions:
  - Receive the highest ratings for:
    - Fluency  
    - Style adherence  
    - Factual consistency  

- FLAN-T5:
  - Improves semantics  
  - Shows weaker stylistic control  

---

### Comparison with a State-of-the-Art LLM (Gemini 2.5 Flash)

Compared against Gemini 2.5 Flash:

- The RefStyleCap pipeline:
  - Achieves higher lexical diversity  
  - Produces more expressive captions  
  - Maintains comparable depth and nuance  

- Gemini:
  - Shows stronger fluency  
  - Produces smoother phrasing  
  - Generates less diverse captions  

This supports the design choice of decoupling:

- Visual understanding  
- Linguistic refinement  

The staged design increases expressiveness while preserving semantic fidelity.

---

## 5️⃣ Diversity and Richness Analysis

Lexical diversity analysis supports the pipeline design.

### Observations

- BLIP-Large produces more varied captions than BLIP-Base  
- Fine-tuning:
  - Reduces repetitive phrasing  
  - Increases phrase-level diversity  
- BART:
  - Achieves high entropy and strong bigram diversity  
  - Introduces variation primarily through phrasing rather than excessive vocabulary expansion  

---

### Model-Level Insights

- BLIP-Base Raw:
  - Tends toward repetitive structures  
  - Limited phrase diversity  

- FLAN-T5:
  - Shows high entropy  
  - Weaker phrase stability and coherence  

- BART:
  - Best balance of:
    - Expressiveness  
    - Semantic stability  
    - Stylistic coherence  

---

## 6️⃣ Qualitative Word Distribution Analysis

Word distribution visualizations reveal:

- BLIP-Large uses a broader and more evenly distributed vocabulary  
- Fine-tuned BLIP:
  - Produces more semantically specific terms  
  - Reduces generic word usage  

- BART:
  - Produces well-balanced phrasing  
  - Avoids lexical repetition  
  - Maintains stylistic consistency  

- FLAN-T5:
  - Shows uneven lexical spread  
  - Limited phrase diversity  

These patterns align with both quantitative diversity metrics and LLM-as-a-Judge evaluations.

---

## 7️⃣ Embedding Projection Analysis

Sentence embedding projections show that:

- BART-generated captions form tight clusters near ground-truth references  
- Fine-tuning shifts all models closer to reference distributions  
- BART-Large shows:
  - Strongest semantic alignment  
  - Most compact embedding clusters  

FLAN-T5 embeddings remain more scattered and farther from references, indicating weaker stylistic and semantic consistency.

---

## 8️⃣ Visual Grounding Analysis (Attention Maps)

Attention map analysis explains why BLIP-Large outperforms BLIP-Base.

### Key Observations

- BLIP-Large:
  - Focuses on salient visual regions  
  - Captures fine-grained attributes  
  - Models spatial relationships  

- BLIP-Base:
  - Shows more diffuse attention  
  - Misses subtle but important details  
  - Produces more generic captions  

This provides interpretable evidence that larger model capacity improves:

- Visual grounding  
- Contextual specificity  
- Caption informativeness  

---

## 9️⃣ Summary of Findings

The experimental results support the proposed multi-stage design.

### Core Conclusions

- Scaling BLIP improves visual grounding  
- Domain fine-tuning improves relevance  
- BART-based style transfer enables strong narrative alignment  
- Staged modeling promotes:
  - Lexical diversity  
  - Semantic fidelity  
  - Stylistic expressiveness  

---

## 10️⃣ Final Takeaway

The RefStyleCap framework demonstrates that:

- Separating visual understanding and stylistic adaptation is effective  
- BART is highly suitable for controlled caption rewriting  
- Domain-specific fine-tuning is essential for narrative domains  

The combination of:

- BLIP-Large for visual grounding  
- Domain fine-tuning for relevance  
- BART for stylistic refinement  

consistently produces captions that are:

- Visually accurate  
- Context-aware  
- Stylistically expressive  

---

## 📬 Contact

For result interpretation questions:

- [Sudesh Rani] | [Siddhesh Sanjay Varpe]
- [sudeshrani@pec.edu.in] | [sidvilla1920@gmail.com]
- [Department of Computer Science and Engineering, Punjab Engineering College, Sector 12, Chandigarh - 160012, India]

