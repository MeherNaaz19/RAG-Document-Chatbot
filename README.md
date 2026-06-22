# RAG Document Chatbot 📄🤖

A Retrieval-Augmented Generation (RAG) chatbot that answers questions and generates summaries from any PDF document grounded entirely in the document's content, with built-in hallucination prevention.

---

## 🔄 How It Works

```
PDF Upload → Text Extraction → Chunking → Embeddings → 
FAISS Vector Store → Query → Semantic Retrieval → 
LLM (Llama 3.3 via Groq) → Grounded Answer
```

---
## ✨ Features

- **Document Q&A** : ask any question about the uploaded PDF, get accurate answers grounded only in document content
- **Hallucination prevention** : explicitly prompts the model to say "I don't have that information" rather than guessing
- **Full document summarization** : generates a structured summary covering main topic, key sections, and conclusions
- **Section-specific summarization** : retrieve and summarize any specific topic/section on demand
- **Interactive chat loop** : ask multiple questions in a continuous session

---

## 🛠️ Tech Stack

- **PDF Extraction** — pdfplumber
- **Text Chunking** — LangChain (RecursiveCharacterTextSplitter)
- **Embeddings** — sentence-transformers (`all-MiniLM-L6-v2`) —> runs locally, no API
- **Vector Search** — FAISS (Facebook AI Similarity Search)
- **LLM** — Llama 3.3 70B via Groq API

---

## 📌 Pipeline Breakdown

| Step | Tool | Purpose |
|---|---|---|
| 1. Extract | pdfplumber | Pull readable text from PDF pages |
| 2. Chunk | LangChain | Split into 500-char chunks with 50-char overlap |
| 3. Embed | sentence-transformers | Convert each chunk into a 384-dim vector |
| 4. Store | FAISS | Index vectors for fast similarity search |
| 5. Retrieve | FAISS search | Find top-k most relevant chunks for a query |
| 6. Generate | Groq + Llama 3.3 | Synthesize a grounded answer from retrieved context |

---

## ▶️ How to Run

1. Open notebook in **Google Colab**
2. Install dependencies (first few cells handle this)
3. Upload any PDF when prompted
4. Get a free Groq API key from [console.groq.com](https://console.groq.com)
5. Replace `"YOUR_GROQ_API_KEY"` in the notebook with your key
6. Run all cells —
   ```
   Note: use the interactive loop at the end to chat with your document
   ```
---

## 🔮 Future Enhancements

- RAG-based chunking strategy for very long documents (multi-stage map-reduce summarization)
- Support for multiple PDFs in a single session
- Persistent vector store instead of in-memory FAISS index
- Web UI (Streamlit) for non-technical usage

---

## 💭 Key Learnings

- Embeddings capture semantic meaning, enabling retrieval even when query wording differs from document phrasing
- Retrieval quality directly determines generation quality - vague queries return less relevant chunks
- Explicit grounding instructions are essential to prevent LLM hallucination in RAG pipelines
- Chunk size and overlap involve a precision-vs-context tradeoff that affects retrieval accuracy

---

*Author: Meher Naaz*

