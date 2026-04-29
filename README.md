# YouTube RAG-based Chatbot
A Retrieval-Augmented Generation (RAG) system built with LangChain that allows users to interact with any YouTube video transcript.

## Technical Overview
This project implements a modular RAG pipeline to solve the problem of LLM hallucinations. By grounding the model in specific, verified video transcripts, the system ensures factually accurate responses tailored to proprietary or real-time content.

## The Technical Pipeline
1. **Indexing**: 
   - Extracts raw captions via `youtube-transcript-api`.
   - Chunks text using `RecursiveCharacterTextSplitter` (1000 chars, 200 overlap).
   - Generates 1536-dimensional vectors using OpenAI’s `text-embedding-3-small`.
2. **Retrieval**: Uses **FAISS** (Facebook AI Similarity Search) to find the most relevant context via semantic search.
3. **Augmentation**: Injects context into a custom prompt template to ground the LLM's responses.
4. **Generation**: Produces final answers using the `gpt-4o-mini` model orchestrated through **LangChain Expression Language (LCEL)**.

## Tech Stack
- **Framework**: LangChain
- **LLM**: OpenAI GPT-4o-mini
- **Vector Database**: FAISS
- **Language**: Python
