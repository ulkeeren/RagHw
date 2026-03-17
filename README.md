# LogRAG: Retrieval-Augmented Log Analysis with LangChain and Pinecone

## Overview
LogRAG is a notebook-based project that explores retrieval-augmented generation (RAG) for log analysis. The project ingests Apache-style log files, converts them into vector embeddings, stores them in Pinecone, and enables natural-language querying over the indexed logs using LangChain and OpenAI models.

The main goal is to investigate whether operational log data can be searched and interpreted through a semantic retrieval pipeline instead of relying only on manual filtering or keyword-based search.

## Features
- Loads Apache-format log files from a local directory
- Splits log documents into smaller chunks for retrieval
- Generates embeddings using OpenAI embeddings
- Stores vectorized log chunks in Pinecone
- Supports semantic similarity search over logs
- Uses LangChain RetrievalQA for natural-language question answering on top of retrieved log entries

## Workflow
1. Generate or collect Apache-style log data
2. Load `.log` files with `DirectoryLoader`
3. Split logs into smaller chunks using `RecursiveCharacterTextSplitter`
4. Create embeddings with OpenAI
5. Store document embeddings in Pinecone
6. Query the vector store using natural language
7. Pass retrieved context into a LangChain QA chain

## Example Query
Example question used in the notebook:

`What's the IP address that posted a PUT command in 04/Sep/2024:03:08:37`

This demonstrates how the pipeline can be used to retrieve operational details from logs with natural-language input instead of manually scanning raw entries.

## Tech Stack
- Python
- LangChain
- Pinecone
- OpenAI Embeddings
- OpenAI Chat Models
- Pandas / NumPy
- Unstructured / NLTK

## Project Structure
- `langchain_pinecone_rag.ipynb` — main notebook containing data loading, embedding, vector storage, retrieval, and QA experiments

## Notes
This project uses generated Apache log files as the data source and serves as an exploratory prototype for LLM-assisted log analysis.

Credentials such as API keys should be provided through environment variables or a local secrets manager and should not be stored in the repository.

## Future Improvements
- Add structured metadata filtering for timestamp, HTTP method, and status code
- Improve prompt design for more reliable log-grounded answers
- Build a lightweight UI for interactive querying
- Compare RAG-based querying with rule-based or SQL-like log search approaches
- Evaluate retrieval quality on more realistic production logs
