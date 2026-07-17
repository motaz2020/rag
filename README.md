# 🚀 Mini-RAG Platform

> A production-ready Retrieval-Augmented Generation (RAG) platform built with FastAPI, supporting multiple LLM providers, pluggable vector databases, asynchronous document processing, semantic search, and enterprise-grade observability.

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-Async_API-009688)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT-success)
![Cohere](https://img.shields.io/badge/Cohere-Command_R+-blueviolet)
![PGVector](https://img.shields.io/badge/PGVector-Supported-orange)
![Qdrant](https://img.shields.io/badge/Qdrant-Supported-red)
![Docker](https://img.shields.io/badge/Docker-Compose-blue)
![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-orange)
![Grafana](https://img.shields.io/badge/Grafana-Dashboard-yellow)

---

# Overview

Mini-RAG is a modular Retrieval-Augmented Generation (RAG) platform designed for intelligent document question answering.

The system supports document ingestion, chunking, embedding generation, semantic retrieval, and LLM-powered response generation through a provider-agnostic architecture. Built using asynchronous FastAPI services, Factory Patterns, and interchangeable providers, it enables flexible deployment with multiple AI models and vector databases while maintaining clean software architecture.

---

# Architecture

```
                User
                  │
                  ▼
            FastAPI REST API
                  │
      ┌───────────┴───────────┐
      │                       │
Document Upload          User Question
      │                       │
      ▼                       ▼
Document Processing     Query Embedding
      │                       │
      ▼                       ▼
Chunk Generation     Semantic Vector Search
      │                       │
      └───────────┬───────────┘
                  ▼
          Retrieved Context
                  │
                  ▼
          Prompt Construction
                  │
                  ▼
          LLM Answer Generation
                  │
                  ▼
           Grounded Response
```

---

# Key Features

| Feature | Description |
|----------|-------------|
| Multi-LLM Support | OpenAI and Cohere providers with configurable generation and embedding backends |
| Dual Vector Database | PGVector and Qdrant using a provider-agnostic Factory Pattern |
| Semantic Retrieval | Embedding-based similarity search over indexed document chunks |
| Async Architecture | Fully asynchronous FastAPI, SQLAlchemy, and async PostgreSQL stack |
| Document Processing | PDF and TXT ingestion with automatic chunk generation |
| Provider Abstraction | Switch LLMs or vector databases without changing application logic |
| Production Monitoring | Prometheus metrics and Grafana dashboards |
| Docker Deployment | Complete 8-service Docker Compose environment |
| OpenAPI | Interactive Swagger documentation |

---

# Tech Stack

## Backend

- FastAPI
- SQLAlchemy 2.0
- AsyncPG
- Alembic

## AI / NLP

- OpenAI GPT
- Cohere Command R+
- LangChain
- Embedding Models

## Vector Databases

- PostgreSQL + PGVector
- Qdrant

## Infrastructure

- Docker Compose
- Nginx
- Prometheus
- Grafana

---

# RAG Workflow

1. Upload PDF or TXT documents

2. Parse document content

3. Split into semantic chunks

4. Generate embeddings

5. Store vectors inside PGVector or Qdrant

6. Embed user query

7. Perform semantic similarity search

8. Retrieve relevant chunks

9. Generate context-aware responses

---

# Quick Start

```bash
git clone https://github.com/motaz2020/rag

cd rag

pip install -r requirements.txt
```

Create

```bash
.env
```

Configure

- OpenAI or Cohere API Keys
- PostgreSQL credentials
- Vector Database backend

Run locally

```bash
uvicorn main:app --reload
```

or

```bash
docker compose up --build -d
```

Swagger

```
http://localhost:8000/docs
```

---

# API

| Method | Endpoint | Description |
|----------|----------|-------------|
| POST | /data/upload | Upload documents |
| POST | /data/process | Generate chunks |
| POST | /nlp/index/push | Generate embeddings |
| GET | /nlp/index/info | Collection information |
| POST | /nlp/index/search | Semantic search |
| POST | /nlp/index/answer | RAG answer generation |

---

# Infrastructure

Docker Compose provisions **8 integrated services**:

- FastAPI
- PostgreSQL + PGVector
- Qdrant
- Nginx
- Prometheus
- Grafana
- PostgreSQL Exporter
- Node Exporter

---

# Project Structure

```
src/
│
├── controllers/
├── routes/
├── models/
├── stores/
│   ├── llm/
│   ├── vectordb/
│   └── templates/
├── helpers/
├── utils/
└── main.py
```

---

# Design Highlights

- Provider-Agnostic Architecture
- Factory Pattern
- Async Processing
- Modular Controllers
- Configurable AI Providers
- Configurable Vector Databases
- Clean Layered Architecture
- Production-ready Monitoring
