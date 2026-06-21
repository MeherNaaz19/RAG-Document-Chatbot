# RAG Document Chatbot 📄🤖

A Retrieval-Augmented Generation (RAG) chatbot that answers questions and generates summaries from any PDF document — grounded entirely in the document's content, with built-in hallucination prevention.

---

## 🔄 How It Works

```
PDF Upload → Text Extraction → Chunking → Embeddings → 
FAISS Vector Store → Query → Semantic Retrieval → 
LLM (Llama 3.3 via Groq) → Grounded Answer
```

