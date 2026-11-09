# Architecture Notes

## Intended workflow
Document ingestion -> text extraction -> chunking -> embeddings -> FAISS retrieval -> local LLM generation -> Streamlit/FastAPI response.

## Current implementation caveat
There are multiple incompatible index implementations. build_index.py writes a pickle tuple, query_engine.py loads a native FAISS index, and retriever.py expects a FAISS-like search method. Consolidate these before claiming one working RAG pipeline.

## Target design
1. Validate local uploads or safely fetch remote documents.
2. Extract page-aware text.
3. Chunk text while retaining source filename, page, and chunk ID.
4. Generate embeddings with a configurable model.
5. Persist vectors and metadata through one vector-store abstraction.
6. Retrieve ranked passages with source metadata.
7. Send the question and clearly delimited untrusted evidence to the LLM.
8. Validate the response and return answer, uncertainty, and citations.

## Principles
- One canonical ingestion and indexing path.
- Reproducible index builds.
- No secrets or private source documents in Git.
- Evidence citations for material claims.
- Explicit abstention when evidence is missing.
- Testable interfaces around embeddings, retrieval, and LLM providers.
