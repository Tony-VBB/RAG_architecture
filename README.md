# End-to-End RAG Architecture

A clean, modular implementation of a Retrieval-Augmented Generation (RAG) architecture built with LangChain, SentenceTransformers, ChromaDB, and Groq LLM.

## Architecture Overview

```
Corpus Data (.txt)
       │
       ▼
Document Loader (TextLoader)
       │
       ▼
Text Splitter (RecursiveCharacterTextSplitter)
       │
       ▼
Embedding Model (SentenceTransformer: all-MiniLM-L6-v2)
       │
       ▼
Vector Database (ChromaDB PersistentClient)
       │
       ▼
Retriever (Semantic Query Ranking & Similarity Thresholding)
       │
       ▼
Augmented Generation (ChatGroq: llama-3.1-8b-instant)
```

## Setup & Installation

1. **Install Dependencies:**
   ```bash
   pip install langchain langchain-community langchain-text-splitters chromadb sentence-transformers langchain-groq python-dotenv
   ```

2. **Configure API Key:**
   - Copy `.env.example` to `.env`:
     ```bash
     cp .env.example .env
     ```
   - Add your Groq API key:
     ```env
     GROQ_API_KEY=gsk_your_key_here
     ```

3. **Run Notebook:**
   - Open and run [Untitled15.ipynb](Untitled15.ipynb).
