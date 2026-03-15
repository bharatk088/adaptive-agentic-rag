# Adaptive Agentic RAG System

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-green)
![LangGraph](https://img.shields.io/badge/LangGraph-AgenticAI-orange)
![Vector DB](https://img.shields.io/badge/Qdrant-VectorDB-purple)
![Streamlit](https://img.shields.io/badge/Streamlit-UI-red)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

An **Agentic Retrieval-Augmented Generation (RAG) system** designed for
intelligent document retrieval, adaptive query routing, and contextual
AI responses.

This project combines **FastAPI, LangGraph, Streamlit, Qdrant, and
MongoDB** to build a full-stack AI chatbot capable of answering
questions from uploaded documents, general knowledge, or real-time web
data.

------------------------------------------------------------------------



------------------------------------------------------------------------

# Project Highlights

  Feature                  Description
  ------------------------ ------------------------------------------------
  Adaptive Query Routing   Automatically decides how to answer a query
  Agentic Workflow         Uses LangGraph for reasoning workflows
  Document RAG             Upload and query PDF/TXT documents
  Vector Search            High-performance similarity search with Qdrant
  Web Search Integration   Real-time knowledge retrieval
  Chat Memory              MongoDB session-based conversation tracking
  API + UI                 FastAPI backend and Streamlit frontend

------------------------------------------------------------------------

## Architecture Overview


flowchart TB
    U[End User] --> S[Streamlit Frontend]

    subgraph FRONTEND[Frontend Layer]
        S1[Chat UI]
        S2[Document Upload]
        S3[Session Handling]
    end

    S --> S1
    S --> S2
    S --> S3

    S --> A[FastAPI Backend]

    subgraph BACKEND[Backend Services]
        A1[Query API]
        A2[Document Upload API]
        A3[Response Handling]
    end

    A --> A1
    A --> A2
    A --> A3

    A --> L[LangGraph Workflow Engine]

    subgraph ORCHESTRATION[Agentic Orchestration]
        L1[Analyze Query]
        L2[Classify Intent]
        L3[Route Request]
        L4[Execute Pipeline]
    end

    L --> L1 --> L2 --> L3 --> L4

    L4 --> P1[RAG Pipeline]
    L4 --> P2[General LLM Pipeline]
    L4 --> P3[Web Search Pipeline]

    subgraph RAGPIPE[RAG Processing]
        R1[Chunked Document Retrieval]
        R2[Vector Similarity Search]
        R3[Relevance Grading]
        R4[Query Rewrite]
        R5[Answer Generation]
    end

    P1 --> R1 --> R2 --> R3 --> R4 --> R5

    subgraph GENPIPE[General Reasoning]
        G1[Direct LLM Response]
    end

    P2 --> G1

    subgraph SEARCHPIPE[Real-Time Search]
        W1[Tavily Search]
        W2[Search Result Synthesis]
    end

    P3 --> W1 --> W2

    R5 --> O[Unified Response Generator]
    G1 --> O
    W2 --> O

    O --> RSP[Final Answer to User]

    Q[(Qdrant)] --> R2
    M[(MongoDB)] --> O

# Key Features

## Adaptive Query Routing

The system classifies queries into three categories:

-   **Index Queries** -- answered from uploaded documents
-   **General Queries** -- answered from LLM knowledge
-   **Search Queries** -- answered using web search

------------------------------------------------------------------------

## Agentic AI Workflow

Using **LangGraph**, the system performs dynamic reasoning steps:

1.  Query analysis
2.  Classification
3.  Retrieval
4.  Relevance grading
5.  Query rewriting
6.  Response generation

------------------------------------------------------------------------

## Retrieval Augmented Generation

The RAG pipeline includes:

-   document ingestion
-   text chunking
-   embeddings generation
-   vector indexing
-   similarity retrieval
-   response synthesis

------------------------------------------------------------------------

## Persistent Chat Memory

Chat sessions are stored in **MongoDB** allowing:

-   session tracking
-   conversation history
-   context-aware responses

------------------------------------------------------------------------

# Technology Stack

  Layer             Technology
  ----------------- ------------
  Backend API       FastAPI
  Workflow Engine   LangGraph
  LLM Framework     LangChain
  Vector Database   Qdrant
  Frontend          Streamlit
  Chat Memory       MongoDB
  Search            Tavily
  Embeddings        OpenAI

------------------------------------------------------------------------

# Project Structure

    adaptive-agentic-rag
    │
    ├── src
    │   ├── api
    │   ├── config
    │   ├── core
    │   ├── db
    │   ├── llms
    │   ├── memory
    │   ├── models
    │   ├── rag
    │   └── tools
    │
    ├── streamlit_app
    │   ├── pages
    │   └── utils
    │
    ├── requirements.txt
    ├── README.md
    └── documentation

------------------------------------------------------------------------

# Installation

## Clone Repository

    git clone https://github.com/bharatk088/adaptive-agentic-rag.git
    cd adaptive-agentic-rag

------------------------------------------------------------------------

## Create Environment

    python -m venv venv

Activate:

Windows

    venv\Scripts\activate

Linux / Mac

    source venv/bin/activate

------------------------------------------------------------------------

## Install Dependencies

    pip install -r requirements.txt

------------------------------------------------------------------------

# Environment Variables

Create `.env`

    OPENAI_API_KEY=your_key
    TAVILY_API_KEY=your_key

    QDRANT_URL=http://localhost:6333
    QDRANT_API_KEY=your_key

    MONGODB_URL=mongodb://localhost:27017
    MONGODB_DB_NAME=adaptive_rag

------------------------------------------------------------------------

# Run Application

## Start Backend

    python -m uvicorn src.main:app --reload --port 8000

API Docs

    http://localhost:8000/docs

------------------------------------------------------------------------

## Start Frontend

    streamlit run streamlit_app/home.py

Web App

    http://localhost:8501

------------------------------------------------------------------------

# Maintainer

**Bharat Kamble**\
GitHub: https://github.com/bharatk088

------------------------------------------------------------------------

# License

MIT License

------------------------------------------------------------------------

# Project Status

Active Development
