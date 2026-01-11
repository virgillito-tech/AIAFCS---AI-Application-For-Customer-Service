# AI Call Intelligence Platform

> **Enterprise-grade AI platform for call centers**  
> On-premise • Privacy-first • Real-time assistance

---

## 🔍 Overview (EN)

AI Call Intelligence Platform is an **enterprise AI solution for call centers** designed to analyze customer calls, support operators in real time and ensure compliance with company procedures — **without moving sensitive data outside the customer’s infrastructure**.

The platform integrates **speech recognition, speaker diarization, large language models and Retrieval-Augmented Generation (RAG)** to deliver both **post-call analytics** and **live operator guidance**.

> ⚠️ **Source code is not publicly available**  
> This repository intentionally contains documentation only.  
> The software is distributed under a commercial license.

---

## 🔍 Panoramica (IT)

AI Call Intelligence Platform è una **piattaforma di Intelligenza Artificiale per call center**, progettata per analizzare le chiamate, supportare gli operatori in tempo reale e garantire la compliance operativa, **mantenendo tutti i dati all’interno dell’infrastruttura aziendale**.

La soluzione integra **trascrizione vocale, diarizzazione degli interlocutori, Large Language Models e Retrieval-Augmented Generation (RAG)** per fornire sia **analisi post-chiamata** sia **assistenza live all’operatore**.

> ⚠️ **Il codice sorgente non è pubblico**  
> Questo repository contiene esclusivamente documentazione descrittiva.  
> Il software è distribuito commercialmente su licenza.

---

## 🚀 Key Features / Funzionalità principali

### Post-Call Analysis / Analisi post-chiamata
- Automatic speech-to-text transcription
- Speaker diarization (operator / customer)
- Call summary generation
- Keyword extraction
- Automatic CRM field population (call reason)
- Customer sentiment analysis:
  - Positive / Neutral / Negative
  - Urgency detection for negative calls
- Compliance monitoring:
  - Detection of mandatory scripts not read
  - Explicit identification of missing sections

---

### Real-Time Operator Assistance / Supporto live all’operatore
- Live audio stream analysis during the call
- Context-aware suggestions for issue resolution
- Answers generated exclusively from **company documentation**
- Each suggestion includes:
  - Document name
  - Page number
  - Paragraph reference

This enables faster resolution times, improved accuracy and full procedural compliance.

---

## 🧠 AI & Technologies Used

### Speech Recognition
- **OpenAI Whisper**
  - High-accuracy automatic speech recognition (ASR)
  - Multilingual support
  - Optimized for noisy call-center audio

### Speaker Diarization
- **Pyannote.audio**
  - Neural speaker segmentation
  - Separation of operator and customer voices
  - Robust performance on real-world telephone conversations

### Language Understanding & Reasoning
- **Large Language Models (LLMs – LLaMA family)**
  - Conversation summarization
  - Keyword extraction
  - Sentiment classification
  - Compliance verification
  - Semantic understanding of customer issues

### Knowledge Retrieval (RAG)
- **Retrieval-Augmented Generation (RAG)**
- **Vector database (e.g. ChromaDB)**
  - Company PDFs and internal documentation are embedded
  - Semantic search retrieves only relevant passages
  - LLM responses are grounded in verified internal sources

This ensures **accurate, explainable and auditable answers**.

---

## 🏗 Architecture

- Fully **on-premise deployment**
- Uses **customer-owned hardware and GPUs**
- Containerized services (Docker / Kubernetes)
- Local REST and WebSocket APIs
- Designed for integration with:
  - CRM systems
  - CTI / VoIP platforms
  - Custom call-center software

No audio streams, transcripts or sensitive data are sent outside the company network.

---

## 🔐 Privacy & Security

- No external cloud processing of customer data
- End-to-end encrypted communication
- Metadata-only usage monitoring
- Optional air-gapped installation
- Designed to support GDPR and enterprise security requirements

---

## 📄 Licensing & Distribution

The platform is provided as a **commercial on-premise SaaS solution**.

- Monthly subscription model
- Pricing based on:
  - Number of active operators
  - Enabled modules (post-call analysis, live assistance)
- Optional enterprise SLA and custom integrations

> There is **no open-source or free license** for this software.

---

## 🎯 Intended Use / Destinazione d’uso

Designed for:
- Call centers
- Customer support departments
- Enterprises with compliance constraints
- Organizations that cannot adopt cloud-only AI solutions

**Not intended for personal, academic or experimental use.**

---

## 📬 Availability & Contact

The software is available through:
- Direct licensing agreements
- Pilot projects
- Enterprise deployments

For technical details, demos or commercial inquiries:

📧 **Contact:** [your.email@domain.com]

---

## ⚖ Disclaimer

This repository does not include executable code or models.  
Any attempt to replicate, reverse engineer or use the described system without authorization is strictly prohibited.

© All rights reserved.
