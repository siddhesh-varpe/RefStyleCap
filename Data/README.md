# Dataset Preparation for RefStyleCap

This document describes the datasets used in the **RefStyleCap: Reference-Guided Style-Aware Image Captioning** framework, including their sources, sizes, intended use, and preparation steps.

---

## 📌 Overview

RefStyleCap uses three complementary datasets to support:

- Visual grounding  
- Semantic grounding  
- Stylistic adaptation  

These datasets span visual data (movie stills), textual data (book corpus), and custom-curated caption paraphrase pairs.

---

## 1️⃣ Harry Potter Movie Stills Dataset

**Source:**  
Official Harry Potter website (HarryPotter.com), formerly known as *Pottermore*

**Content:**  
- Movie stills from all **eight Harry Potter films**  
- Used for domain-specific fine-tuning of BLIP models

**Size:**  
- **1,281 images**

**Train–Test Split:**  
- 60% training  
- 40% testing  
- **520 test images total**  
- **65 images per movie** selected for testing

**Purpose in RefStyleCap:**  
- Visual grounding  
- Domain specialization  
- Improving factual accuracy and relevance of generated captions

---

## 2️⃣ Harry Potter Book Corpus

**Source:**  
Kaggle – *Harry Potter Books Dataset*

**Content:**  
- Full text of the Harry Potter novels

**Size:**  
- **7 text files** (one per book)

**Purpose in RefStyleCap:**  
- Vocabulary learning  
- Semantic grounding  
- Learning literary tone and narrative style  
- Training stylistic adaptation models (BART and FLAN-T5)

---

## 3️⃣ Annotated Caption & Style-Transfer Dataset (Private)

**Source:**  
Custom-curated (Private Dataset)

**Content:**  
- Raw image captions  
- Corresponding Harry Potter–style paraphrases  
- Each pair represents:
  - An original factual caption  
  - A stylistically adapted caption aligned with the Harry Potter literary tone

**Base Version Size:**  
- **1,281 annotated image captions**  
- **5,968 input–target caption pairs**

**Extended Version Size:**  
- **64,766 input–target caption pairs**

**Total Style Pairs:**  
- **70,734 input–target caption pairs**

**Purpose in RefStyleCap:**  
- Training the two-stage **BART-based** stylistic adaptation model  
- Training the prefix-tuned **FLAN-T5** stylistic adaptation model  
- Improving stylistic consistency and narrative alignment

---

## 📊 Dataset Summary

| Reference                        | Dataset Description                                 | Size                          |
|----------------------------------|-----------------------------------------------------|-------------------------------|
| Official HP Website (Pottermore) | Harry Potter Movie Stills (Movies 1–8)              | 1,281 images                  |
| Kaggle                           | Harry Potter Book Corpus                            | 7 text files                  |
| Private Dataset                  | Annotated Captions & Input–Target Style Pairs       | 1,281 captions + 70,734 pairs |

---

## ⚠️ Data Availability & Copyright

Due to copyright and licensing restrictions:

- The **Harry Potter movie stills**  
- The **Harry Potter book corpus**  
- The **annotated caption and style-pair datasets**

are **not redistributed** in this repository. Only few samples are put up for view only purpose.

---

## 📥 How to Obtain the Data

### Movie Stills

- Download from the official Harry Potter website:  
  https://www.harrypotter.com  
  (formerly Pottermore)

---

### Book Corpus

- Available on Kaggle  
- Search for: **"Harry Potter Books Dataset"**  
- Example reference:  
  https://www.kaggle.com/datasets  
  (exact link may vary)

---

### Annotated Captions & Style Pairs (Private Dataset)

This dataset is available **upon reasonable academic request**.

Please contact the authors with:

- Your name and affiliation  
- Intended research use  
- Agreement to non-commercial academic use only

---

## 📬 Contact

For Dataset contact:

- [Sudesh Rani] | [Siddhesh Sanjay Varpe]
- [sudeshrani@pec.edu.in] | [sidvilla1920@gmail.com]
- [Department of Computer Science and Engineering, Punjab Engineering College, Sector 12, Chandigarh - 160012, India]