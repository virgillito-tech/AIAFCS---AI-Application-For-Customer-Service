# AIAFCS - AI Application For Customer Service

![Status](https://img.shields.io/badge/Status-Proprietary%20%2F%20Commercial-blue)
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![AI](https://img.shields.io/badge/GenAI-LLM%20%26%20RAG-orange)
![Type](https://img.shields.io/badge/Focus-RealTime%20Assistance-green)

> ⚠️ **DISCLAIMER:** Questo repository funge da **vetrina tecnica** (Showcase) per il progetto *AIAFCS*. Poiché il software è un prodotto proprietario attualmente in fase di commercializzazione, il codice sorgente completo non è pubblico. Questa documentazione illustra l'architettura, lo stack tecnologico e le logiche ingegneristiche implementate.

---

## 🚀 Visione del Progetto

**AIAFCS** è una piattaforma *full-stack* di assistenza intelligente progettata per rivoluzionare i contact center. Il sistema agisce come un "copilota" per l'operatore, ascoltando le chiamate in tempo reale per fornire suggerimenti tecnici, monitorare la conformità allo script e automatizzare il lavoro di data-entry.

L'obiettivo è triplice: **ridurre l'AHT** (Average Handle Time), **garantire la compliance** legale/procedurale e **fornire analytics avanzati** ai supervisori.

### 🎥 Anteprima
*(Spazio riservato per GIF animata o Screenshot della Dashboard)*
![Dashboard Placeholder](https://via.placeholder.com/800x400?text=Inserire+qui+Screenshot+della+Dashboard+Operatore)

---

## 🏗️ Flusso Architetturale

Il sistema gestisce due fasi distinte: l'assistenza durante la chiamata (Live) e l'analisi successiva (Post-Call).

### 🔴 FASE 1: Live Call (Real-Time)
Il flusso dati deve garantire una latenza minima (<200ms) per essere utile all'operatore.

> **Input Audio (VoIP)** 🎤
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️ *WebSocket Stream*
> **Speech-to-Text Engine** ⚡ (Trascrizione Live)
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **CORE ORCHESTRATOR** 🧠
> &nbsp;&nbsp;&nbsp;&nbsp;↙️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️
> **RAG Engine** 📚&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Script Validator** 📋
> *(Cerca nei manuali)*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*(Verifica passaggi obbligatori)*
> &nbsp;&nbsp;&nbsp;&nbsp;⬇️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **Suggerimenti AI** 💡&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Alert Compliance** ⚠️
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↙️
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**DASHBOARD OPERATORE** 🖥️

### 🟢 FASE 2: Post Call (Analisi & Supervisione)
Avviene in asincrono appena la chiamata termina.

> **Fine Chiamata** 🛑
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⬇️
> **LLM Supervisor Agent** 🕵️
> *(Analisi completa della trascrizione)*
> &nbsp;&nbsp;&nbsp;&nbsp;↙️&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;↘️
> **Automazione CRM** 💾&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Supervisor Dashboard** 📊
> *(Auto-fill ticket)*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*(Scoring & Sentiment)*

---

## 🛠️ Stack Tecnologico

Il progetto integra tecnologie di elaborazione del linguaggio naturale all'avanguardia con un'architettura backend solida.

* **Core Logic:** `Python 3.10+` 
* **AI Orchestration:** `LangChain`
* **LLM & Inference:** `OpenAI GPT-4o` / `Meta Llama 3` (Configurabile per Local Deployment)
* **Vector Database:** `ChromaDB`(per la ricerca semantica nei manuali)
* **Backend API:** `FastAPI`, `WebSockets` (comunicazione client-server real-time)
* **Frontend:** [Streamlit]

---

## ⚡ Funzionalità Chiave

### 1. Trascrizione & RAG in Tempo Reale
Il sistema ascolta la conversazione e interroga costantemente la Knowledge Base aziendale (PDF, Docs).
* **Vantaggio:** L'operatore riceve la soluzione tecnica corretta sul monitor, corredata da fonti cliccabili, **prima** ancora di doverla cercare manualmente. Riduce i tempi morti e l'imbarazzo dell'attesa.

### 2. Controllo Script (Compliance Check)
Un motore di regole NLP analizza il flusso del dialogo per verificare l'aderenza agli standard aziendali.
* **Funzionamento:** Il sistema "spunta" in tempo reale una checklist visiva (es. *"Saluto iniziale"*, *"Lettura Privacy"*, *"Proposta Commerciale"*).
* **Alert:** Se l'operatore sta per chiudere la chiamata dimenticando un passaggio critico (es. il disclaimer legale), riceve un **alert visivo immediato**.

### 3. Fase Post-Chiamata di Supervisione (QA Automation)
Al termine dell'interazione, un Agente AI specializzato ("Il Supervisore") rilegge l'intera trascrizione.
* **Scoring Automatico:** Assegna un voto (0-100) basato su parametri oggettivi: cortesia, risoluzione tecnica, rispetto dello script.
* **Sentiment Analysis:** Mappa l'andamento emotivo del cliente (es. da "Arrabbiato" a "Soddisfatto").
* **Supervisor Dashboard:** I manager visualizzano le performance aggregate del team senza dover riascoltare ore di registrazioni.

### 4. Automazione CRM
Eliminazione totale del *After Call Work* (ACW) manuale.
* Il sistema genera un riassunto strutturato della chiamata, classifica il motivo del contatto e **popola automaticamente** i campi del software CRM.

---

## 🧠 Sfide Tecniche Affrontate

Lo sviluppo di AIAFCS ha richiesto la risoluzione di problemi ingegneristici complessi:

* **Gestione della Latenza:** Ottimizzazione del pipeline WebSocket per mantenere il ritardo trascrizione-suggerimento sotto i 200ms.
* **State Management nel NLP:** Creazione di una macchina a stati per tracciare l'avanzamento dello script in un flusso di conversazione naturale e non strutturato.
* **Allucinazioni AI:** Implementazione di guardrail rigorosi ("Strict RAG") per impedire al modello di inventare procedure non presenti nei manuali ufficiali.

---

## 📬 Contatti

Sono disponibile per **demo live** del software e per approfondire i dettagli architetturali in sede di colloquio.

**Ing. [Francesco Virgillito]**
* 🌐 **LinkedIn:** [www.linkedin.com/in/francesco-virgillito-291818210]
* 📧 **Email:** [francescovirgillito97@gmail.com]
* 💻 **GitHub Portfolio:** [https://github.com/virgillito-tech]

---
*Copyright © 2026 - Tutti i diritti riservati. L'utilizzo non autorizzato di testi o logiche descritte è proibito.*
