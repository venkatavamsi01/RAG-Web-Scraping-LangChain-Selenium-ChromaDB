# RAG Automated Web Scraping: LangChain, Selenium, ChromaDB

## Overview

This project implements a Retrieval-Augmented Generation (RAG) pipeline for automated web scraping, enabling the extraction and structured analysis of game rules from multiple online sources. Leveraging LangChain, Selenium, BeautifulSoup, and ChromaDB, the pipeline optimizes query generation, retrieves relevant documents, and generates detailed answers using a 4-bit quantized large language model.

## Features

- **Retrieval-Augmented Generation (RAG):** Combines retrieval from a vector store with language model generation.
- **Automated Web Scraping:** Extracts game rules and related data from websites including GameRules.com, WikiHow.com, and Pagat.com.
- **Structured Output Generation:** Uses a custom prompt with few-shot examples for controlled, structured responses from the LLM.
- **Document Understanding:** Splits and embeds scraped content for robust retrieval and context-aware question answering.
- **Modern Web Extraction:** Utilizes Selenium for dynamic content fetching and BeautifulSoup for HTML parsing.
- **Efficient Inference:** Integrates a quantized language model for enhanced performance and reduced computational overhead.

## Architecture and Workflow

1. **Query Generation:**  
   The user’s natural language query is transformed into optimized, site-specific search terms (for GameRules, WikiHow, and Pagat) using an LLM and a custom prompt template.

2. **Web Scraping and Data Extraction:**  
   - **GameRules.com:** Uses `requests` and BeautifulSoup to locate and fetch the rules.
   - **WikiHow.com:** Uses Selenium to simulate browser behavior, retrieve search result candidates, and extract content.
   - **Pagat.com:** Provides a fallback retrieval strategy when no content is found.

3. **Document Processing and Retrieval:**  
   The scraped content is split into manageable document chunks, embedded using a sentence-transformer model, and stored in a Chroma vector database. LangChain’s retrieval chain then pulls relevant context for question answering.

4. **Answer Generation:**  
   The RAG chain integrates the retrieved contextual chunks with the original query to produce a coherent and detailed answer.