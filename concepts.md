# Concepts Behind This Project

This file explains the key technologies and ideas used in this project.

---

## What is RAG?

RAG stands for Retrieval-Augmented Generation. The basic idea is that LLMs (like ChatGPT or Llama) are great at generating text, but they don't know anything about *your* specific documents. They were trained on general internet data — they can't answer questions about a PDF you just uploaded.

RAG solves this by doing two things before generating an answer:
1. **Retrieve** — find the most relevant parts of your document
2. **Augment** — add those parts to the prompt so the LLM has context

Without RAG, if you asked "What did the report say about load balancing?", the LLM would either make something up or say it doesn't know. With RAG, it actually reads the relevant section and answers from that.

---
