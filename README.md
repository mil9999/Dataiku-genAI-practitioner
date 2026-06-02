# 🏨 Hotel Review Sentiment Analyser — GenAI Pipeline on Dataiku

A Generative AI pipeline built on **Dataiku DSS** that transforms raw, unstructured TripAdvisor hotel reviews into structured business intelligence — using LLM-powered sentiment classification, summarisation, translation, and an interactive AI travel agent.

**Author:** Milan Thapa

---

## 📌 Project Overview

Raw customer reviews are one of the richest sources of business insight — but they're noisy, unstructured, and hard to scale manually. This project automates the full journey from raw review text to actionable intelligence using a multi-step GenAI pipeline in Dataiku, powered by **GPT-5.4**.

The pipeline answers questions like:
- Is this review positive or negative?
- What is the reviewer actually saying, in plain English?
- Can a traveller ask a natural language question and get a data-backed answer about which hotel to stay at?

---

## 🔁 Pipeline Flow

![Dataiku Flow](flow_screenshot.png)

```
tripadvisor_hotel_reviews
        │
        ▼
[LLM Classification]
        │
        ▼
reviews_classified
        │
        ▼
[LLM Summarisation]
        │
        ▼
reviews_summarized
       ├──────────────────────────────▶ [LLM Translation → French]
       │                                        │
       │                                        ▼
       │                               reviews_translated
       │
       └──────────────────────────────▶ HotelReviewAgent (GPT-5.4)
```

---

## ⚙️ Pipeline Steps

### 1. Input — `tripadvisor_hotel_reviews`
- 200 real TripAdvisor hotel reviews
- Columns: `Review` (raw text), `Rating` (1–5 stars)
- Reviews are unstructured, noisy, and occasionally multilingual

### 2. LLM Classification → `reviews_classified`
- Each review is passed through a **GPT-5.4 prompt** to classify sentiment
- Output: `prediction` (positive / negative), `prediction_score`
- Adds structured sentiment signal to every review at scale

| Review (excerpt) | Rating | Prediction |
|---|---|---|
| "cozy stay rainy city husband spent 7 nights..." | 5 | positive |
| "ok nothing special charge diamond member hilton..." | 2 | negative |
| "nice rooms not 4* experience hotel monaco..." | 3 | negative |

### 3. LLM Summarisation → `reviews_summarized`
- Each review is summarised into a clean, readable sentence by the LLM
- Turns messy tokenised text into structured, human-readable summaries
- Output: `summary` column added to dataset

| Raw Review (excerpt) | Summary |
|---|---|
| "unique great stay wonderful time hotel mona..." | The reviewer had an excellent stay at Hotel Monaco... |
| "horrible customer service hotel stay february..." | The reviewer describes a terrible stay at Hotel Mon... |
| "great stay great stay went seahawk game aweso..." | The reviewer had a great stay, praising the huge ro... |

### 4. LLM Translation → `reviews_translated`
- Summarised reviews are translated into **French** using the LLM
- Output: `llm_output` column with French translations
- Demonstrates multilingual capability for international hospitality use cases

| English Summary | French Translation |
|---|---|
| The writer and her husband stayed seven nights in... | L'auteure et son mari ont séjourné sept nui... |
| The reviewer had a generally pleasant anniversary... | Le client a globalement passé un agréable... |

### 5. HotelReviewAgent — AI Travel Assistant
- A **Dataiku AI Agent** powered by GPT-5.4
- Uses **Dataset Lookup** as a tool to search the reviews in real time
- Answers natural language questions from travellers about hotel experiences

**Example interaction:**
> 💬 *"Which is the best cheapest hotel with great service?"*
>
> 🤖 *"From the dataset reviews, the strongest match for great service is **Hotel Monaco**. Multiple reviews praise the staff as friendly, efficient, and excellent. Guests mention exceptional service from front desk, concierge, and housekeeping..."*

---

## 📊 Dataset Summary

| Property | Value |
|---|---|
| Source | TripAdvisor hotel reviews |
| Total reviews | 200 |
| Rating range | 1–5 stars |
| Positive reviews | ~60% |
| Negative reviews | ~40% |
| Pipeline outputs | 3 datasets + 1 AI agent |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **Dataiku DSS** | Pipeline orchestration & flow management |
| **GPT-5.4** | Classification, summarisation, translation, agent |
| **Dataset Lookup** | Agent tool for real-time review retrieval |
| **Python** | Data preparation & recipe logic |

---

## 🗂️ Repository Structure

```
hotel-review-sentiment-analyser/
├── README.md                        # Project documentation
├── flow_screenshot.png              # Dataiku pipeline flow diagram
├── screenshots/
│   ├── reviews_classified.png       # Classification output
│   ├── reviews_summarized.png       # Summarisation output
│   ├── reviews_translated.png       # Translation output
│   └── hotel_review_agent.png       # Agent interaction demo
└── data/
    └── tripadvisor_hotel_reviews.csv  # Input dataset
```

---

## 💡 Key Takeaways

- LLMs can classify, summarise, and translate unstructured text **at scale** with no manual labelling
- A **-0.0x correlation** between star rating and sentiment prediction shows the LLM captures nuance beyond simple scores (a 4-star review can still be "negative" in tone)
- Agentic AI on top of structured review data enables **conversational business intelligence** — a step beyond dashboards

---

## 👨‍💻 About

Hi, I'm **Milan Thapa** — MSc Business Analytics student at NEOMA Business School. I build end-to-end data and AI projects that turn raw information into real decisions.

📧 [milan.thapa.24@neoma-bs.com](mailto:milan.thapa.24@neoma-bs.com)
💼 [LinkedIn](https://linkedin.com/in/milan-thapa-30324b332)
🐙 [GitHub](https://github.com/mil9999)
🌐 [Portfolio](https://mil9999.github.io)

---

💡 If you found this useful, feel free to star ⭐ the repo!
