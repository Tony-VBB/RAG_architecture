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

## Future Works & Roadmap

- [ ] **Hybrid Retrieval (Dense + Sparse Search):** Combine dense semantic vectors (SentenceTransformers) with sparse keyword retrieval (BM25) using Reciprocal Rank Fusion (RRF) to improve retrieval recall on exact keywords and jargon.
- [ ] **Cross-Encoder Re-Ranking:** Integrate a second-stage re-ranking model (e.g., `cross-encoder/ms-marco-MiniLM-L-6-v2` or Cohere Rerank) to re-order top-k retrieved chunks before feeding into the LLM context.
- [ ] **Contextual & Semantic Chunking:** Move beyond fixed character splitting to semantic chunking, recursive boundary splitting, or parent-child retrieval (indexing small chunks for search, returning larger context windows for generation).
- [ ] **Agentic RAG & Query Transformation:** Implement Query Expansion, Multi-Query Generation, and HyDE (Hypothetical Document Embeddings), alongside Self-RAG / Corrective RAG (CRAG) for self-reflection and hallucination checks.
- [ ] **Multi-Format Ingestion Pipeline:** Extend loaders to support complex PDFs (with tables and figures), DOCX, PPTX, and OCR for scanned documents using tools like Unstructured or PyMuPDF.
- [ ] **Conversational Memory:** Add multi-turn dialogue history and query re-writing for conversational Q&A interactions.
- [ ] **Automated Evaluation & Observability:** Integrate RAG evaluation frameworks such as RAGAS or TruLens to measure faithfulness, context precision, and answer relevance, along with LangSmith/Phoenix for tracing.
- [ ] **Production API & UI:** Wrap the pipeline in a FastAPI asynchronous backend service and create an interactive user interface using Streamlit or Next.js.
