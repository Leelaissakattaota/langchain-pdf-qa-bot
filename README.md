# 🤖 LangChain PDF Q&A Bot with IBM watsonx

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![IBM watsonx.ai](https://img.shields.io/badge/AI-IBM%20watsonx-052FAD?logo=ibm&logoColor=white)
![LangChain](https://img.shields.io/badge/Orchestration-LangChain-1C3C3C?logo=langchain&logoColor=white)
![Gradio](https://img.shields.io/badge/Frontend-Gradio-FF7C00?logo=gradio&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Project Overview

This project is a **Retrieval-Augmented Generation (RAG)** application capable of reading, understanding, and answering questions from PDF documents.

It leverages **IBM watsonx.ai** for the Large Language Model (LLM) and **LangChain** to handle document processing and retrieval. [cite_start]The user interface is built with **Gradio**, making it easy to upload files and chat with your data[cite: 7, 8, 36].

## 🚀 Key Features

* **📄 Document Ingestion:** Upload any PDF document directly through the UI.
* **🧠 Intelligent Retrieval:** Uses `RecursiveCharacterTextSplitter` and `ChromaDB` to find the most relevant answers.
* **🤖 Powered by IBM watsonx:** Utilizes the `mistral-small` model (via Watsonx) for high-quality natural language generation.
* **💬 Interactive Chat:** Simple, user-friendly web interface powered by Gradio[cite: 37].

## 🛠️ Tech Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Language** | ![Python](https://img.shields.io/badge/-Python-black?logo=python) | Core programming language. |
| **LLM Provider** | **IBM watsonx.ai** | Provides the Foundation Model (Mistral/Granite). |
| **Orchestration** | **LangChain** | Manages the RAG pipeline and chains. |
| **Vector Store** | **ChromaDB** | Stores document embeddings for fast search. |
| **Interface** | **Gradio** | Web-based UI for file upload and chat. |

## 📂 File Structure

- `qabot.py`: The main application script containing the logic for the LLM, retriever, and Gradio interface[cite: 55].

## ⚡ How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Leelaissakattaota/langchain-pdf-qa-bot.git](https://github.com/Leelaissakattaota/langchain-pdf-qa-bot.git)
    cd langchain-pdf-qa-bot
    ```

2.  **Install dependencies:**
    ```bash
    pip install gradio ibm-watsonx-ai langchain-ibm langchain-community chromadb pypdf
    ```

3.  **Run the application:**
    ```bash
    python qabot.py
    ```

4.  **Open the App:**
    Click the local URL provided in the terminal (usually `http://127.0.0.1:7860`).

---
*Created as part of the IBM RAG and Agentic AI Lab.*
