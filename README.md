# Assignment 3: NYC Taxi Analytics & RAG Pipeline

## Project Overview
This repository contains an end-to-end Data + AI application built to analyze New York City Taxi & Limousine Commission (TLC) data. It integrates a PySpark-driven structured data pipeline with a Retrieval-Augmented Generation (RAG) pipeline for unstructured policy documents, unified by an intelligent LLM query router.

## Architecture Breakdown

### Part 1: Large-Scale Data Processing (PySpark)
* Ingests and caches million-row NYC Taxi Parquet datasets.
* Executes complex SQL aggregations and window functions to extract trip statistics, fare averages, and top revenue locations.

### Part 2: Unstructured Knowledge Retrieval (LangChain & ChromaDB)
* Programmatically downloads official TLC policy PDFs (e.g., Green Rides Initiative, Accessibility Rules).
* Processes documents using a `RecursiveCharacterTextSplitter` optimized for 1000-character chunks with a 200-character overlap.
* Visualizes chunk distribution using `matplotlib`.
* Embeds text using HuggingFace's `all-MiniLM-L6-v2` and persists vectors in a local ChromaDB instance.

### Part 3: Intelligent Query Routing (LLM Integration)
* Utilizes a customized LLM agent to classify incoming natural language questions.
* Routes queries to the Spark SQL engine (`DATA`), the Vector Database (`DOCUMENT`), or synthesizes insights from both (`HYBRID`) to answer complex urban analytics questions.

## Setup Instructions
To run this notebook locally or in Google Colab, you must provide a valid API key.

1. Clone this repository to your local machine or Google Colab environment.
2. Install the required dependencies by running `pip install -r requirements.txt`.
3. Create `api_key.txt`.
4. Open `api_key.txt` and paste your API key inside on a single line (no extra spaces or quotes).
5. Execute the Jupyter Notebook (`assignment3.ipynb`).

## File Structure
* `assignment3.ipynb`: The main notebook containing all PySpark, RAG, and routing logic.
* `requirements.txt`: Python package dependencies.
* `.gitignore`: Repository rules to prevent uploading credentials, raw Parquet files, or local databases.
* `api_key.txt`: Create this file for secure API key loading.
* `docs/`: Contains 7 curated pdf documents. (Code for programmatic download included, however it is commented out as one pdf site increased security to prevent scraping)

#### AI Disclosure:
Artificial intelligence tools such as Google Gemini were used during the development of this project to assist with programming support, syntax debugging, and the final presentation of results. Specifically, Gemini was used to assist with output formatting; including structuring console print statements for readability, and organizing the repository documentation (`README.md` and `.gitignore`).

All architectural design choices, PySpark SQL query logic, RAG pipeline implementation, and analytical conclusions were independently developed and executed. The AI tools served solely as a supplementary aid for formatting and technical troubleshooting, and were not used as a substitute for performing the core data engineering or analysis.
