# AIAFCS - AI Application For Customer Service

![Status](https://img.shields.io/badge/Status-Proprietary%20%2F%20Commercial-blue)
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![AI](https://img.shields.io/badge/GenAI-LLM%20%26%20RAG-orange)
![Type](https://img.shields.io/badge/Focus-RealTime%20Assistance-green)

> ⚠️ **DISCLAIMER:** This repository serves as a **technical showcase** for the *AIAFCS* project. Since the software is a proprietary product currently under commercialization, the full source code is not public. This documentation illustrates the architecture, technology stack, and engineering logic implemented.

---

## 🚀 Project Vision

**AIAFCS** is a *full-stack* intelligent assistance platform designed to revolutionize contact centers. The system acts as a "copilot" for the operator, listening to calls in real-time to provide technical suggestions, monitor script compliance, and automate data-entry tasks.

The goal is threefold: **reduce AHT** (Average Handle Time), **ensure legal/procedural compliance**, and **provide advanced analytics** to supervisors.

### 🎥 Preview
*(Space reserved for Animated GIF or Dashboard Screenshot)*
![Dashboard Placeholder](https://via.placeholder.com/800x400?text=Insert+Operator+Dashboard+Screenshot+Here)

---

## 🏗️ Architectural Flow

The system manages two distinct phases: Live Assistance (during the call) and Post-Analysis (after the call).

### 🔴 PHASE 1: Live Call (Real-Time)
The data flow must guarantee minimum latency (<200ms) to be useful to the operator.

> **Audio Input (VoIP)** 🎤
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️ *WebSocket Stream*
> **Speech-to-Text Engine** ⚡ (Live Transcription)
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **CORE ORCHESTRATOR** 🧠
> &nbsp;&nbsp;&nbsp;&nbsp;↙️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️
> **RAG Engine** 📚&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Script Validator** 📋
> *(Retrieval from Manuals)*&nbsp;&nbsp;&nbsp;&nbsp;*(Mandatory Steps Check)*
> &nbsp;&nbsp;&nbsp;&nbsp;⬇️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **AI Suggestions** 💡&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Compliance Alerts** ⚠️
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↙️
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OPERATOR DASHBOARD** 🖥️

### 🟢 PHASE 2: Post Call (Analysis & Supervision)
Occurs asynchronously as soon as the call ends.

> **End Call** 🛑
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **LLM Supervisor Agent** 🕵️
> *(Full Transcription Analysis)*
> &nbsp;&nbsp;&nbsp;&nbsp;↙️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️
> **CRM Automation** 💾&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Supervisor Dashboard** 📊
> *(Auto-fill ticket)*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*(Scoring & Sentiment)*

---

## 🛠️ Tech Stack

The project integrates cutting-edge Natural Language Processing technologies with a solid backend architecture.

* **Core Logic:** `Python 3.10+`
* **AI Orchestration:** `LangChain`
* **LLM & Inference:** `OpenAI GPT-4o` / `Meta Llama 3` (Configurable for Local Deployment)
* **Vector Database:** `ChromaDB` (for semantic search in manuals)
* **Backend API:** `FastAPI`, `WebSockets` (real-time client-server communication)
* **Frontend:** [Streamlit]

---

## ⚡ Key Features

### 1. Real-Time Transcription & RAG
The system listens to the conversation and constantly queries the corporate Knowledge Base (PDFs, Docs).
* **Benefit:** The operator receives the correct technical solution on the monitor, accompanied by clickable sources, **before** even having to search for it manually. This reduces dead air and wait times.

### 2. Script Compliance Check
An NLP rule engine analyzes the dialogue flow to verify adherence to company standards.
* **How it works:** The system "checks off" a visual checklist in real-time (e.g., *"Initial Greeting"*, *"Privacy Policy Reading"*, *"Sales Proposal"*).
* **Alert:** If the operator is about to close the call while forgetting a critical step (e.g., the legal disclaimer), they receive an **immediate visual alert**.

### 3. Post-Call Supervision Phase (QA Automation)
At the end of the interaction, a specialized AI Agent ("The Supervisor") reviews the entire transcription.
* **Automatic Scoring:** Assigns a score (0-100) based on objective parameters: politeness, technical resolution, script adherence.
* **Sentiment Analysis:** Maps the customer's emotional trend (e.g., from "Angry" to "Satisfied").
* **Supervisor Dashboard:** Managers view the team's aggregated performance without having to listen to hours of recordings.

### 4. CRM Automation
Total elimination of manual *After Call Work* (ACW).
* The system generates a structured summary of the call, classifies the reason for contact, and **automatically populates** the CRM software fields.

---

## 🧠 Technical Challenges Solved

Developing AIAFCS required solving complex engineering problems:

* **Latency Management:** Optimization of the WebSocket pipeline to keep transcription-to-suggestion delay under 200ms.
* **NLP State Management:** Creation of a finite state machine to track script progress within a natural, unstructured conversation flow.
* **AI Hallucinations:** Implementation of rigorous guardrails ("Strict RAG") to prevent the model from inventing procedures not present in official manuals.

---

## 📬 Contact

I am available for **live demos** of the software and to discuss architectural details during an interview.

**Eng. [Francesco Virgillito]**
* 🌐 **LinkedIn:** [(https://www.linkedin.com/in/francesco-virgillito-291818210/)]
* 📧 **Email:** [francescovirgillito97@gmail.com]
* 💻 **GitHub Portfolio:** [(https://github.com/virgillito-tech)]

---
*Copyright © 2026 - All rights reserved. Unauthorized use of the text or logic described herein is prohibited.*
