# AIAFCS - AI Application For Customer Service

![Status](https://img.shields.io/badge/Status-Proprietary%20%2F%20Commercial-blue)
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![AI](https://img.shields.io/badge/GenAI-LLM%20%26%20RAG-orange)
![Module](https://img.shields.io/badge/Module-Supervisor%20Analytics-red)

> **Nota:** Questo repository funge da **vetrina tecnica** per il progetto *AIAFCS*. Poiché il software è attualmente in fase di commercializzazione/licensing, il codice sorgente completo è privato. Questo documento illustra l'architettura, le sfide tecniche risolte e le funzionalità del sistema.

---

## 🚀 Panoramica del Progetto

**AIAFCS** è una piattaforma *full-stack* di assistenza intelligente progettata per ottimizzare l'intero ciclo di vita dell'interazione Customer Service. Il sistema non si limita a supportare l'operatore, ma garantisce la qualità del servizio attraverso il monitoraggio della compliance e offre strumenti di analisi avanzata per i supervisori.

Il sistema opera su tre livelli temporali:
1.  **Real-Time Assistance:** Suggerimenti tecnici e risposte basate su manuali.
2.  **Real-Time Script Compliance:** Verifica istantanea del rispetto delle procedure di conversazione.
3.  **Post-Call Supervision:** Analisi automatica, valutazione e reportistica per i manager.

### 🎥 Demo / Screenshot


---

## 🏗️ Architettura del Sistema

L'architettura gestisce flussi di dati paralleli per l'assistenza all'operatore e il controllo qualità.

```mermaid
graph TD
    subgraph "Live Call Phase"
    A[Audio Input (VoIP)] -->|Stream WebSocket| B(Speech-to-Text Engine)
    B -->|Text Stream| C{Core Orchestrator}
    C -->|Semantic Search| D[RAG Engine / Vector DB]
    D -->|Context| E[LLM Agent - Helper]
    C -->|Compliance Check| F[Script Validator Engine]
    E --> G[Operator Dashboard (Suggestions)]
    F --> G[Operator Dashboard (Alerts/Script)]
    end

    subgraph "Post Call Phase"
    H[End Call] --> I[Data Aggregator]
    I --> L[LLM Agent - Supervisor]
    L --> M[Supervisor Dashboard]
    L --> N[CRM Auto-Fill]
    end


Stack Tecnologico

Core: Python, AsyncIO

AI Framework: LangChain, LlamaIndex

LLM & Embeddings: OpenAI GPT-4o / Meta Llama 3 (Local Deployment)

Vector Database: ChromaDB / Pinecone

Frontend: [Inserire framework, es. Streamlit / React / Vue]

Backend: FastAPI / WebSockets


⚡ Funzionalità Chiave
1. Trascrizione & RAG in Tempo Reale

Il sistema ascolta la conversazione e interroga la Knowledge Base aziendale.

Vantaggio: L'operatore riceve la soluzione tecnica (con riferimenti ai manuali PDF) prima ancora di doverla cercare manualmente.

2. Controllo Script (Compliance Check)

Un modulo dedicato analizza il flusso della conversazione per verificare che l'operatore segua lo script obbligatorio.

Funzionamento: Il sistema spunta in tempo reale le fasi completate (es. "Saluto iniziale", "Lettura Privacy", "Tentativo di Upselling").

Alert: Se l'operatore dimentica un passaggio critico (es. disclaimer legale), il sistema invia un alert visivo immediato.

3. Fase Post-Chiamata di Supervisione (QA Automation)

Al termine della chiamata, un Agente AI "Supervisore" analizza l'intera trascrizione.

Scoring Automatico: Assegna un voto alla chiamata basandosi su parametri predefiniti (cortesia, efficacia tecnica, rispetto dello script).

Sentiment Analysis: Mappa l'andamento emotivo del cliente durante la chiamata.

Supervisor Dashboard: I manager possono vedere a colpo d'occhio le performance del team senza dover riascoltare ore di registrazioni audio.

4. Automazione CRM

Eliminazione del After Call Work (ACW) manuale. Il sistema riassume la chiamata, classifica il ticket e popola i campi del CRM automaticamente.
