---
layout: page
title: RAG Question Answering System
description: FastAPI, LangChain, ChromaDB, Python, Streamlit
importance: 3
category: work
github: https://github.com/jackyToras/mistral-rag-system
website: https://qnaragsystem.streamlit.app/
---

Large Language Models (LLMs) are powerful but they have a fundamental limitation — they only know what they were trained on. Ask an LLM about your company's internal documents, a research paper published last week, or your own PDF files, and it either hallucinates an answer or admits it doesn't know. Retrieval-Augmented Generation (RAG) solves this by giving the LLM a memory — at inference time, it retrieves the most relevant chunks of your documents and feeds them as context to the model, grounding its responses in real data.

**What's Actually Happening — The Full Pipeline:**

**Document Ingestion:** The user uploads a PDF through the Streamlit interface. The system extracts raw text from the PDF, then splits it into overlapping chunks of configurable size. Chunking is critical — too large and the chunks carry too much noise, too small and they lose context. Overlapping chunks ensure no information is lost at chunk boundaries.

**Embedding Generation:** Each text chunk is passed through an embedding model which converts it into a high-dimensional vector — a numerical representation that captures the semantic meaning of the text. Similar meaning = similar vectors. This is the foundation of semantic search.

**Vector Storage in ChromaDB:** The generated embeddings are stored in ChromaDB — a vector database optimized for fast similarity search. ChromaDB persists these vectors so you don't need to re-embed documents on every query.

**Query Processing:** When the user asks a question, the question itself is embedded using the same embedding model. ChromaDB performs a cosine similarity search — finding the top-K chunks whose embeddings are most similar to the question embedding. These are the most semantically relevant pieces of your documents.

**Context-Augmented Generation:** The retrieved chunks are injected into a carefully engineered prompt template alongside the user's question. This combined prompt is sent to the LLM. The model now has real document context — it answers based on what's actually in your PDFs, not hallucinated knowledge.

**FastAPI Backend:** The entire pipeline is exposed through FastAPI REST endpoints — document ingestion endpoint and query endpoint — making it trivially integratable into any frontend or external system.

**Streamlit Frontend:** A clean, interactive UI allows users to upload documents, ask questions in a chat interface, and see responses with source references in real time.
