# Tradebulls Multi-Source RAG Chatbot 📈🤖

> A production-grade, domain-specific Retrieval-Augmented Generation (RAG) system engineered with LangChain Expression Language (LCEL), FAISS, and OpenAI to unify multi-source financial intelligence without hallucinations.

[![Python](https://img.shields.io/badge/Python-3.12-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![LangChain](https://img.shields.io/badge/LangChain-LCEL-green?style=for-the-badge)](https://python.langchain.com)
[![FAISS](https://img.shields.io/badge/FAISS-In--Memory-lightgrey?style=for-the-badge)](https://github.com/facebookresearch/faiss)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-orange?style=for-the-badge&logo=openai)](https://openai.com)
[![Organization](https://img.shields.io/badge/Tradebulls-BFSI%20Domain-darkgreen?style=for-the-badge)](https://www.tradebulls.in/)

---

## 🎯 Overview

Standard Large Language Models (LLMs) suffer from baseline **Knowledge Cutoffs** and **Hallucinations**, making them fundamentally unviable for zero-tolerance banking, financial, and regulatory customer support domains. 

This repository contains the complete technical implementation and engineering documentation for the **Domain-Specific Financial Knowledge Assistant** developed for **Tradebulls Securities Private Limited**. This system harnesses state-of-the-art Generative AI architecture to unify completely disparate, multi-format knowledge structures into a singular conversational engine. It dynamically loads, parses, and searches across:

* **Raw Structural Compliance Data:** Internal corporate text files and SEBI regulatory FAQs concerning Persons with Disabilities (PwD) and account guardianship guidelines.
* **Live Web Scraping Layouts:** Web scrapers extracting investor education workflows directly from Tradebulls blog properties.
* **Automated Multimedia Streams:** Python wrappers that extract audio transcripts programmatically from dynamic stock market tutorial content.
* **Unstructured Layout PDFs:** Daily proprietary market analysis research documents featuring dense technical support/resistance metrics and financial tables.

---

## 🏗️ Architecture & Component Workflow

The engine relies strictly on a disconnected data ingestion lifecycle combined with a synchronous, contextually augmented inference layer to guarantee deterministic execution bounds under strict SEBI regulatory scopes.

```text
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               OFFLINE INDEXING LIFECYCLE                               │
└───────────────────────────────────────────┬────────────────────────────────────────────┘
                                            │ Ingests Data Sources
                                            ▼
 ┌───────────────┐   ┌──────────────────┐   ┌──────────────────────┐   ┌────────────────┐
 │ Raw Text File │   │  WebBaseLoader   │   │YouTubeTranscriptApi  │   │UnstructuredPDF │
 │ (Internal PwD │   │ (Tradebulls Blog │   │  (Video Tutorial     │   │ (Daily Market  │
 │  Compliance)  │   │    Scraping)     │   │     ID Extraction)   │   │ Research Report)│
 └───────┬───────┘   └────────┬─────────┘   └──────────┬───────────┘   └───────┬────────┘
         │                    │                        │                       │
         └────────────────────┼────────────────────────┴───────────────────────┘
                              │ Combines Data Streams Into Universal Documents
                              ▼
               ┌──────────────────────────────┐
               │RecursiveCharacterTextSplitter│ (chunk_size=700, chunk_overlap=100)
               └──────────────┬───────────────┘
                              │ Creates 87 Semantically Complete Text Chunks
                              ▼
               ┌──────────────────────────────┐
               │   text-embedding-3-small     │ (Transforms text into 1536-Dim matrices)
               └──────────────┬───────────────┘
                              │
                              ▼
               ┌──────────────────────────────┐
               │    FAISS Vector Database     │ (Local In-Memory Index-to-Docstore Store)
               └──────────────────────────────┘
                                      
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                         ONLINE RETRIEVAL & INFERENCE PIPELINE                          │
└───────────────────────────────────────────┬────────────────────────────────────────────┘
                                            │ User Query Input Invocation
                                            ▼
                              ┌──────────────────────────────┐
                              │     User Financial Query     │
                              └──────────────┬───────────────┘
                                             │ Vectorized via Embedding Model
                                             ▼
                              ┌──────────────────────────────┐
                              │    FAISS Similarity Search   │ (Cosine Proximity Match, k=4)
                              └──────────────┬───────────────┘
                                             │ Extracts Relevant Knowledge Fragments
                                             ▼
                              ┌──────────────────────────────┐
                              │  System Context Augmentation │ (Injects prompt constraints)
                              └──────────────┬───────────────┘
                                             │ Appends Question + Document Strings
                                             ▼
                              ┌──────────────────────────────┐
                              │   GPT-4o-mini (Temp = 0.2)   │ (Strict Zero-Shot Evaluation)
                              └──────────────┬───────────────┘
                                             │
                                             ▼
                              ┌──────────────────────────────┐
                              │  Grounded Factual Response   │ (No Hallucinations / SEBI Safe)
                              └──────────────────────────────┘
