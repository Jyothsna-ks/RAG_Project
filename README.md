#RAG-Based Customer Support Assistant

 Overview

This project implements a Retrieval-Augmented Generation (RAG) based Customer Support Assistant that answers user queries using information extracted from a PDF knowledge base.

The system combines document retrieval and language generation to provide accurate, context-aware responses. It also includes a Human-in-the-Loop (HITL) mechanism to handle uncertain or complex queries.


What is RAG?

Retrieval-Augmented Generation (RAG) is an AI approach that enhances Large Language Models (LLMs) by retrieving relevant information from external data sources before generating a response.

Instead of relying only on pre-trained knowledge, the system:

1. Retrieves relevant content from a document
2. Uses that context to generate accurate answers


Problem Statement

Traditional chatbots:

- Give generic responses
- Cannot access company-specific documents
- Fail on complex queries

This project solves these issues by:

- Using a PDF knowledge base
- Retrieving relevant information dynamically
- Generating contextual answers

System Architecture

Components:

- Document Loader → Loads PDF data
- Text Chunker → Splits document into smaller parts
- Embedding Model → Converts text into vectors
- Vector Database (ChromaDB) → Stores embeddings
- Retriever → Finds relevant chunks
- LLM → Generates final answers
- LangGraph Workflow → Controls execution flow
- HITL Module → Escalates unresolved queries

 Workflow

1. User sends a query via API
2. System retrieves relevant chunks from the PDF
3. Context is passed to the LLM
4. LLM generates an answer
5. Routing logic decides:
   - Return answer
   - OR escalate to human


Technologies Used

- Python
- LangChain
- LangGraph
- ChromaDB
- FastAPI
- Sentence Transformers

 Features

- PDF-based knowledge retrieval
- Semantic search using embeddings
- Graph-based workflow using LangGraph
- FastAPI backend for interaction
- Human-in-the-Loop escalation
- Context-aware responses

Example Query

Input:

{
  "question": "What is the refund policy?"
}

Output:

{
  "answer": "Refunds are allowed within 7 days of purchase."
}

 Human-in-the-Loop (HITL)

If the system:

- Cannot find relevant context
- Has low confidence
- Encounters ambiguous queries

It escalates the request:

"Escalated to human support."
