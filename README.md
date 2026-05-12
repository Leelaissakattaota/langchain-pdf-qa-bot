# 📑 PDF RAG Chatbot — LangChain + IBM Watsonx + Gradio

![Language](https://img.shields.io/badge/Language-Python%203.11-3776AB?style=flat-square&logo=python&logoColor=white)
![LLM](https://img.shields.io/badge/LLM-Mistral%20Small%203.1%2024B-FF6B35?style=flat-square)
![LLM](https://img.shields.io/badge/LLM-IBM%20Granite%203.3%208B-052FAD?style=flat-square&logo=ibm&logoColor=white)
![Embeddings](https://img.shields.io/badge/Embeddings-IBM%20Slate%2030M-6A0DAD?style=flat-square)
![VectorDB](https://img.shields.io/badge/VectorDB-ChromaDB-2E7D32?style=flat-square)
![UI](https://img.shields.io/badge/UI-Gradio-FF7C00?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

---

## 📌 Project Overview

**PDF Q&A RAG chatbot** powered by IBM Watsonx — upload any PDF and 
ask questions about its content. Uses **Mistral Small 3.1 24B** as 
the LLM, **IBM Slate 30M** for embeddings, **ChromaDB** as the vector 
store, and **Gradio** for the web interface.

Part of the **IBM RAG & Agentic AI Professional Certificate** — 
demonstrates a complete, production-style RAG pipeline from document 
upload to grounded answer generation.

**Domain:** RAG — PDF Document Q&A  
**LLM:** mistralai/mistral-small-3-1-24b-instruct-2503 (IBM Watsonx)  
**Embeddings:** ibm/slate-30m-english-rtrvr (IBM Watsonx)  
**Vector Store:** ChromaDB  
**UI:** Gradio  

---

## 📂 Project Structure

```
langchain-pdf-qa-bot/
│
├── qabot.py              # Main RAG pipeline + Gradio UI
├── llm_chat.py           # Standalone Gradio chatbot (Granite 3.3 / Mistral)
├── common_input_types.py # Gradio input component demos
├── gradio_demo.py        # Basic Gradio text-combine demo
└── README.md
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| LLM (RAG) | Mistral Small 3.1 24B (IBM Watsonx) |
| LLM (Chat) | IBM Granite 3.3 8B (IBM Watsonx) |
| Embeddings | IBM Slate 30M English Retriever (Watsonx) |
| PDF Loader | PyPDFLoader (LangChain Community) |
| Text Splitter | RecursiveCharacterTextSplitter |
| Vector Store | ChromaDB |
| QA Chain | LangChain RetrievalQA ("stuff" chain) |
| UI | Gradio |

---

## 🚀 Full RAG Pipeline

```python
# 1. Load PDF
loader = PyPDFLoader(file)
loaded_document = loader.load()

# 2. Split into chunks
chunks = RecursiveCharacterTextSplitter(
    chunk_size=1000, chunk_overlap=50
).split_documents(loaded_document)

# 3. Embed with IBM Slate 30M + store in ChromaDB
embedding_model = WatsonxEmbeddings(
    model_id="ibm/slate-30m-english-rtrvr", ...)
vectordb = Chroma.from_documents(chunks, embedding_model)

# 4. LLM — Mistral Small 3.1 24B
llm = WatsonxLLM(model_id="mistralai/mistral-small-3-1-24b-instruct-2503", ...)

# 5. RetrievalQA chain
qa = RetrievalQA.from_chain_type(
    llm=llm, chain_type="stuff",
    retriever=vectordb.as_retriever()
)

# 6. Answer query
response = qa.invoke(query)['result']
```

---

## 🖥️ Gradio Interface

```python
rag_application = gr.Interface(
    fn=retriever_qa,
    inputs=[
        gr.File(label="Upload PDF File", file_types=['.pdf']),
        gr.Textbox(label="Input Query", placeholder="Type your question here...")
    ],
    outputs=gr.Textbox(label="Output"),
    title="RAG Chatbot with IBM watsonx"
)
rag_application.launch(server_name="127.0.0.1", server_port=7860)
```

---

## 🎓 Skills Demonstrated

- End-to-end PDF RAG pipeline — load → split → embed → retrieve → answer
- IBM Watsonx Mistral Small 3.1 24B for grounded Q&A
- IBM Slate 30M English Retriever embeddings (`WatsonxEmbeddings`)
- PyPDFLoader for PDF ingestion
- `RecursiveCharacterTextSplitter` (1000 chars, 50 overlap)
- ChromaDB vector store from documents
- LangChain `RetrievalQA` with "stuff" chain
- Gradio File + Textbox inputs for PDF upload + question
- Standalone Gradio chatbot (llm_chat.py — Granite 3.3 / Mistral)
- Gradio component demos (Slider, Dropdown, CheckboxGroup, Radio)

---

## 📜 Certifications

| Certification | Issuer | Platform |
|---|---|---|
| IBM Data Science Professional Certificate | IBM | Coursera |
| IBM Generative AI Professional Certificate | IBM | Coursera |
| IBM RAG and Agentic AI Professional Certificate | IBM | Coursera |

---

## 🤝 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Leela%20A-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/leela-a)
[![Gmail](https://img.shields.io/badge/Gmail-attotaleelaissak@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:attotaleelaissak@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-Leelaissakattaota-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Leelaissakattaota)
