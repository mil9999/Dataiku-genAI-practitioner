# Dataiku-genAI-practitioner
End-to-end GenAI pipeline built using Dataiku LLM Mesh — sentiment analysis, summarization, translation, and RAG-powered AI agent

# 🏨 Hotel Review GenAI Pipeline — Dataiku Generative AI Practitioner

## 📌 Project Overview
An end-to-end Generative AI pipeline built using Dataiku DSS
and **GPT-5.4** to analyze hotel reviews from TripAdvisor.

This project was completed as part of the 
Dataiku Generative AI Practitioner Certification.

---

## 🏗️ Pipeline Architecture
The Flow consists of the following steps:
tripadvisor_hotel_reviews
↓
[Classify Text Recipe]
↓
reviews_classified
↓
[Summarize Text Recipe]
↓
reviews_summarized
↓
[Prompt Recipe - Translation]
↓
reviews_translated

---

## 🔧 Steps Completed

### 1. Sentiment Classification
- Used Dataiku's **Classify Text** LLM recipe
- Analyzed sentiment of each hotel review
- Output: `positive` or `negative` prediction per review
- Model: GPT-5.4 via Dataiku LLM Mesh

### 2. Text Summarization
- Used Dataiku's **Summarize Text** LLM recipe
- Summarized each review into **2 sentences** in English
- Controlled output length using built-in length settings

### 3. Translation via Prompt Engineering
- Used Dataiku's **Prompt recipe**
- Translated English summaries into French
- Used managed prompt with `{{summary}}` as input variable
- Example prompt:
  > *Translate the following hotel review summary 
  > into French: {{summary}}*

### 4. RAG-Powered AI Travel Agent
- Created a **Dataset Lookup** agent tool
- Configured **CONTAINS** operator to search reviews by keyword
- Built a **Simple Visual Agent** with system prompt
- Tested with queries about staff, cleanliness, and food

---

## 🤖 AI Agent System Prompt
You are a travel assistant who specializes in retrieving
hotel reviews to help travelers select the best places
to stay on their trips. The user will input a question
about hotel experiences (e.g., staff quality, cleanliness,
or food). You are tasked with the following actions:

Search the dataset for reviews matching the query.
Generate a concise summary of the relevant reviews.

In all other cases, respond to the best of your knowledge
and explicitly mention that this answer does not come
from the dataset.
---

## 💡 Key Concepts Learned

| Concept | Description |
|---|---|
| **LLM Mesh** | Dataiku's centralized layer for managing LLM connections |
| **Prompt Engineering** | Designing prompts to get desired outputs from LLMs |
| **RAG** | Retrieval Augmented Generation — augmenting LLMs with custom data |
| **Tokenization** | Converting text into numerical tokens for LLM processing |
| **Zero-shot prompting** | Prompting without examples |
| **Few-shot prompting** | Prompting with examples to guide the model |
| **Knowledge Bank** | Dataiku's vector database for storing embeddings |
| **Temperature** | Controls randomness/creativity of LLM responses |

---

## 🛠️ Tools & Technologies
- **Platform**: Dataiku DSS
- **LLM**: GPT-5.4 (OpenAI via Dataiku LLM Mesh)
- **Dataset**: TripAdvisor Hotel Reviews (Kaggle)
- **Recipes Used**: Classify Text, Summarize Text, Prompt, Embed
- **Agent Type**: Simple Visual Agent with Dataset Lookup tool

---

## 📊 Results

### Sentiment Classification
- 200 hotel reviews classified
- Labels: `positive` / `negative`
- Accuracy aligned well with star ratings

### Summarization
- Each review condensed into 2 sentences
- Language: English

### Translation
- All 200 summaries translated to French
- Example:
  - EN: *"The reviewer had a great stay at Hotel Monaco"*
  - FR: *"Le client a passé un excellent séjour à l'Hôtel Monaco"*

### AI Agent Test Results
| Query | Key Finding |
|---|---|
| Which hotels have very good staff? | Hotel Monaco most praised |
| Are there hotels with cleanliness issues? | Warwick Hotel had repeated complaints |
| What do reviews say about food? | Hotel Monaco food generally positive |

---

## 📜 Certification
**Dataiku Generative AI Practitioner**
Issued: April 2026
Certificate Link: https://verify.skilljar.com/c/wdgir45wiezk
---

## 👤 Author
Milan Thapa
Linkedin: [
](https://www.linkedin.com/in/milan-thapa-30324b332/)
