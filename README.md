# README: COMP 3610 Assignment 3 - LLM Applications & Distributed Computing

## Project Overview
This project involves building a complete **intelligent data analytics system** that combines large-scale data processing with AI-powered knowledge retrieval. The application processes structured **NYC Yellow Taxi Trip Records** using **Apache Spark** and integrates a **Retrieval-Augmented Generation (RAG)** pipeline built over a curated corpus of urban transportation policy documents.

The final system features a unified natural language interface that routes user queries to the appropriate backend: structured data analytics, unstructured document retrieval, or a hybrid of both.

---

## Technical Stack
- **Distributed Computing:** PySpark (DataFrame API & Spark SQL)
- **Document Processing:** PyPDF or LangChain loaders
- **Embeddings:** `sentence-transformers` (`all-MiniLM-L6-v2`)
- **Vector Database:** ChromaDB (Persistent)
- **LLM Access:** Course LLM server or accessible API
- **Text Splitting:** LangChain `RecursiveCharacterTextSplitter`

---

## Key Components

### Part 1: Distributed Data Processing (Spark)
- **Data Engineering:** Cleaning null values and filtering invalid trips (e.g., zero distance, negative fares, or dropoff before pickup)
- **Feature Engineering:** Creating columns for trip duration, speed (mph), pickup time metadata, and tip percentages
- **Analytics:** Using Spark SQL and window functions to rank pickup locations and analyze trip patterns
- **Optimization:** Implementing caching and partitioned Parquet writes for performance tuning

### Part 2: RAG Pipeline
- **Ingestion:** Extracting text from 5–10 curated NYC transportation policy PDFs
- **Chunking:** Splitting text into segments (1000 characters) with overlap for context retention
- **Retrieval:** Storing embeddings in ChromaDB to retrieve relevant context for user queries
- **Evaluation:** Assessing retrieval and answer quality using a manually verified test set of 10 question-answer pairs

### Part 3: Integrated Application
- **Query Router:** An LLM-powered router that classifies questions as **DATA**, **DOCUMENT**, or **HYBRID** using structured JSON output
- **Data Query Handler:** Translates natural language into Spark SQL, executes it, and synthesizes a final answer
- **End-to-End Demo:** A complete flow showing query classification, routing decisions, and combined responses for hybrid queries

---

## Repository Structure
The project follows the required organizational structure:
- `assignment3.ipynb`: Main notebook with all code, outputs, and technical narrative
- `docs/`: Directory containing the curated PDF document corpus
- `requirements.txt`: List of all Python dependencies
- `README.md`: Setup instructions and project description
- `.gitignore`: Configured to exclude large data files, `chroma_db/`, and caches

---

## Setup & Installation
1. **Clone the repository** and ensure the `docs/` folder is populated with the relevant PDFs
2. **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```