# Concepts Behind This Project

This file explains the key technologies and ideas used in this project.

---

## What is RAG?

RAG stands for Retrieval-Augmented Generation. The basic idea is that LLMs (like ChatGPT or Llama) are great at generating text, but they don't know anything about *your* specific documents. They were trained on general internet data and they can't answer questions about a PDF you just uploaded.

RAG solves this by doing two things before generating an answer:
1. **Retrieve** — find the most relevant parts of your document
2. **Augment** — add those parts to the prompt so the LLM has context

Without RAG, if you asked "What did the report say about Electronic Health Records?", the LLM would either make something up or say it doesn't know. With RAG, it actually reads the relevant section and answers from that.

---

## What is an LLM?

LLM = Large Language Model. It's a neural network trained on massive amounts of text data to understand and generate human language. It works by predicting the next word/token given everything before it.

Models like Llama 3.3 (which I used here) are open-source LLMs that anyone can use. The "70B" means 70 billion parameters — basically the number of weights the model learned during training. More parameters generally means smarter, but also slower and more expensive to run.

The key thing is — LLMs are incredibly capable, but they hallucinate. They generate some random text even when they don't know the answer. That's why grounding them with retrieved context (RAG) is so important.

---

## What is Groq?

They offer a free API to run models like Llama 3.3 — which is what I used in this project.

---
