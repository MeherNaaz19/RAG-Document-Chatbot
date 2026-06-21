# RAG Document Chatbot 📄🤖

A Retrieval-Augmented Generation (RAG) chatbot that answers questions and generates summaries from any PDF document — grounded entirely in the document's content, with built-in hallucination prevention.

---

## 🔄 How It Works

```
PDF Upload → Text Extraction → Chunking → Embeddings → 
FAISS Vector Store → Query → Semantic Retrieval → 
LLM (Llama 3.3 via Groq) → Grounded Answer
```

---
## ✨ Features

- **Document Q&A** — ask any question about the uploaded PDF, get accurate answers grounded only in document content
- **Hallucination prevention** — explicitly prompts the model to say "I don't have that information" rather than guessing
- **Full document summarization** — generates a structured summary covering main topic, key sections, and conclusions
- **Section-specific summarization** — retrieve and summarize any specific topic/section on demand
- **Interactive chat loop** — ask multiple questions in a continuous session

---

