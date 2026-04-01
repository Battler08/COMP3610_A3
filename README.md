# README: COMP 3610 Assignment 3 - LLM Applications & Distributed Computing

## Project Overview
[cite_start]This project involves building a complete **intelligent data analytics system** that combines large-scale data processing with AI-powered knowledge retrieval[cite: 8]. [cite_start]The application processes structured **NYC Yellow Taxi Trip Records** using **Apache Spark** and integrates a **Retrieval-Augmented Generation (RAG)** pipeline built over a curated corpus of urban transportation policy documents[cite: 9, 13, 14].

[cite_start]The final system features a unified natural language interface that routes user queries to the appropriate backend: structured data analytics, unstructured document retrieval, or a hybrid of both[cite: 112].

---

## Technical Stack
* [cite_start]**Distributed Computing:** PySpark (DataFrame API & Spark SQL)[cite: 178].
* [cite_start]**Document Processing:** PyPDF or LangChain loaders[cite: 178].
* [cite_start]**Embeddings:** `sentence-transformers` (`all-MiniLM-L6-v2`)[cite: 178].
* [cite_start]**Vector Database:** ChromaDB (Persistent)[cite: 167, 178].
* [cite_start]**LLM Access:** Course LLM server or accessible API[cite: 178].
* [cite_start]**Text Splitting:** LangChain `RecursiveCharacterTextSplitter`[cite: 178].

---

## Key Components

### Part 1: Distributed Data Processing (Spark)
* [cite_start]**Data Engineering:** Cleaning null values and filtering invalid trips (e.g., zero distance, negative fares, or dropoff before pickup)[cite: 32, 33].
* [cite_start]**Feature Engineering:** Creating columns for trip duration, speed (mph), pickup time metadata, and tip percentages[cite: 36, 37, 38].
* [cite_start]**Analytics:** Using Spark SQL and window functions to rank pickup locations and analyze trip patterns[cite: 46, 50].
* [cite_start]**Optimization:** Implementing caching and partitioned Parquet writes for performance tuning[cite: 60, 61].

### Part 2: RAG Pipeline
* [cite_start]**Ingestion:** Extracting text from 5–10 curated NYC transportation policy PDFs[cite: 72, 73].
* [cite_start]**Chunking:** Splitting text into segments (1000 characters) with overlap for context retention[cite: 79, 80].
* [cite_start]**Retrieval:** Storing embeddings in ChromaDB to retrieve relevant context for user queries[cite: 82, 91].
* [cite_start]**Evaluation:** Assessing retrieval and answer quality using a manually verified test set of 10 question-answer pairs[cite: 99, 101, 102].

### Part 3: Integrated Application
* [cite_start]**Query Router:** An LLM-powered router that classifies questions as **DATA**, **DOCUMENT**, or **HYBRID** using structured JSON output[cite: 114, 119].
* [cite_start]**Data Query Handler:** Translates natural language into Spark SQL, executes it, and synthesizes a final answer[cite: 127, 128, 130].
* [cite_start]**End-to-End Demo:** A complete flow showing query classification, routing decisions, and combined responses for hybrid queries[cite: 135, 136, 137].

---

## Repository Structure
[cite_start]The project follows the required organizational structure[cite: 161, 173]:
* [cite_start]`assignment3.ipynb`: Main notebook with all code, outputs, and technical narrative[cite: 151, 173].
* [cite_start]`docs/`: Directory containing the curated PDF document corpus[cite: 75, 173].
* [cite_start]`requirements.txt`: List of all Python dependencies[cite: 157, 173].
* [cite_start]`README.md`: Setup instructions and project description[cite: 157, 174].
* [cite_start]`.gitignore`: Configured to exclude large data files, `chroma_db/`, and caches[cite: 158, 175].

---

## Setup & Installation
1.  [cite_start]**Clone the repository** and ensure the `docs/` folder is populated with the relevant PDFs[cite: 75].
2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```