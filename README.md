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

```text
+----------------------------------------------------------------------------------+
|                                  END USER                                        |
+----------------------------------------------------------------------------------+
                                         |
                                         v
+----------------------------------------------------------------------------------+
|                             STREAMLIT FRONTEND                                   |
|----------------------------------------------------------------------------------|
|  • Chat UI                                                                       |
|  • Document Upload                                                               |
|  • Session Handling                                                              |
+----------------------------------------------------------------------------------+
                                         |
                                         v
+----------------------------------------------------------------------------------+
|                               FASTAPI BACKEND                                    |
|----------------------------------------------------------------------------------|
|  • Query API                                                                     |
|  • Document Upload API                                                           |
|  • Response Handling                                                             |
+----------------------------------------------------------------------------------+
                                         |
                                         v
+----------------------------------------------------------------------------------+
|                          LANGGRAPH WORKFLOW ENGINE                               |
|----------------------------------------------------------------------------------|
|  1. Analyze Query                                                                |
|  2. Classify Intent                                                              |
|  3. Route Request                                                                |
|  4. Execute Pipeline                                                             |
+----------------------------------------------------------------------------------+
                                         |
          +------------------------------+-----------------------------+
          |                              |                             |
          v                              v                             v
+---------------------------+  +------------------------+  +------------------------+
|       RAG PIPELINE        |  |   GENERAL LLM PIPELINE |  |   WEB SEARCH PIPELINE  |
+---------------------------+  +------------------------+  +------------------------+
| • Chunked Retrieval       |  | • Direct LLM Response  |  | • Tavily Search        |
| • Vector Similarity       |  +------------------------+  | • Search Synthesis     |
| • Relevance Grading       |                              +------------------------+
| • Query Rewrite           |
| • Answer Generation       |
+---------------------------+
          |                              |                             |
          +------------------------------+-----------------------------+
                                         |
                                         v
+----------------------------------------------------------------------------------+
|                           UNIFIED RESPONSE GENERATOR                             |
+----------------------------------------------------------------------------------+
                                         |
                                         v
+----------------------------------------------------------------------------------+
|                              FINAL ANSWER TO USER                                |
+----------------------------------------------------------------------------------+


+------------------------+                           +-----------------------------+
|      QDRANT DB         |-------------------------->|   Vector Similarity Search  |
+------------------------+                           +-----------------------------+

+------------------------+                           +-----------------------------+
|     MONGODB MEMORY     |-------------------------->| Unified Response Generator  |
+------------------------+                           +-----------------------------+

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
