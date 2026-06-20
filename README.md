# 🚀 Enterprise Policy Q&A Assistant (RAG-APP-IIT)

An end-to-end Retrieval-Augmented Generation (RAG) system built with LangChain 1.x, OpenAI Embeddings, and ChromaDB to query corporate policies and synthesize answers with document-level citations.

---

## 📋 Table of Contents
*   [📖 Project Overview](#-project-overview)
*   [✨ Features](#-features)
*   [📂 Project Structure](#-project-structure)
*   [⚡ Quick Start Guide](#-quick-start-guide)
*   [🧠 In-Depth Design & Architecture](#-in-depth-design--architecture)
*   [🛠️ Technology Stack](#️-technology-stack)
*   [📝 License](#-license)

---

## 📖 Project Overview
This repository provides a fully functional, localized RAG pipeline designed to ingest structured markdown policies (e.g., Return, Refund, Shipping, and Cancellation Guidelines) and convert them into a local vector database. Users can query this database through an interactive command-line interface, receiving responses directly grounded in the stored policies, along with citations of the source files.

---

## ✨ Features
*   **Semantic Search**: Utilizes OpenAI's `text-embedding-3-small` model to understand query intent (e.g. matching "money back" to the "Refund Policy").
*   **Grounded Generation**: Feeds exact retrieved context passages to `gpt-4o-mini` with strict instructions to prevent hallucinations.
*   **Automated Source Citation**: Every generated response includes reference links indicating the source document and page/header.
*   **Local Vector DB Persistence**: Uses ChromaDB to save vector indexes locally to disk for instant querying.
*   **Bootstrap Utility**: A helper script to quickly create a mock policy corpus for testing.

---

## 📂 Project Structure
```
RAG-APP-IIT/
├── policies/                           # Generated Corporate Policy Corpus
│   ├── cancellation_policy.md          # Cancellation rules (pre/post-shipping)
│   ├── refund_policy.md                # Refund timelines and COD banking info
│   ├── return_policy.md                # Return windows (electronics vs general)
│   ├── shipping_policy.md              # Shipping times, attempts, and schedules
│   └── warranty_policy.md              # Hardware and appliance warranties
├── requirements.txt                    # Python Dependencies
├── create_sample_corpus.py             # Script to generate mock markdown files
├── ingest.py                           # Ingestion pipeline script
├── README.md                           # Repository landing page (This file)
├── pioneers.md                         # Listing of AI/RAG domain pioneers and contributors
└── RAG_APP_IIT_Documentation.md       # In-depth technical architecture manual
```

---

## ⚡ Quick Start Guide

### 1. Prerequisites
Ensure you have Python 3.9+ installed on your system.

### 2. Setup the Repository
Clone the repository and navigate into the project folder:
```bash
git clone https://github.com/AyushSahoo19/RAG-APP-IIT.git
cd RAG-APP-IIT
```

### 3. Install Dependencies
Install all required libraries:
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
Create a `.env` file in the root directory and add your OpenAI API key:
```env
OPENAI_API_KEY=your-actual-openai-api-key-here
```

### 5. Generate the Sample Corpus
Run the bootstrapping script to create the `policies/` folder with mock data:
```bash
python create_sample_corpus.py
```

### 6. Index & Run Ingestion
Run the ingestion script to process documents, chunk them, generate embeddings, and persist the local Chroma vector index:
```bash
python ingest.py
```

---

## 🧠 In-Depth Design & Architecture

For a comprehensive explanation of the RAG pipeline mechanics, please refer to the detailed guide:
👉 **[RAG_APP_IIT_Documentation.md](file:///c:/Users/ayush/OneDrive/Desktop/AI%20ML%20IIT%20Mandi/01_Daily_Lectures_IIT_Mandi/03_Special_Classes/Industry%20Session%205/Coding%20Files%20&%20Projects/RAG-APP-IIT/RAG_APP_IIT_Documentation.md)**

This companion document includes:
*   Offline ingestion and online retrieval flowcharts (Mermaid and ASCII).
*   Comparative tables for text chunking methods and vector databases.
*   Mathematical formulas for **Cosine Similarity**, **L2 Euclidean Distance**, and **RRF (Reciprocal Rank Fusion)**.
*   Advanced techniques like **HyDE (Hypothetical Document Embeddings)** and **Cross-Encoder Reranking**.

A list of domain pioneers and core contributors is documented in:
👉 **[pioneers.md](file:///c:/Users/ayush/OneDrive/Desktop/AI%20ML%20IIT%20Mandi/01_Daily_Lectures_IIT_Mandi/03_Special_Classes/Industry%20Session%205/Coding%20Files%20&%20Projects/RAG-APP-IIT/pioneers.md)**

---

## 🛠️ Technology Stack
*   **Orchestration**: LangChain (Modular 1.x structure)
*   **LLM Model**: ChatOpenAI (`gpt-4o-mini`)
*   **Embedding Model**: OpenAIEmbeddings (`text-embedding-3-small`)
*   **Vector Store**: ChromaDB (SQLite-based persistent backend)
*   **Data Parsing**: LangChain Document Loaders & Splitters

---

## 📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
