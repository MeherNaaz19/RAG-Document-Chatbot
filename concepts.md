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

---# Concepts Behind This Project

This file explains the key technologies and ideas used in this project — written from my understanding after building it.

---

## What are Embeddings?

Computers can't directly compare text , they need numbers. Embeddings convert text into a list of numbers (a vector) that captures its meaning.

Similar meanings end up as similar numbers. So "password strength" and "secure passwords" would have very close vectors, even though the words are different. This is what makes semantic search possible — you're not matching keywords, you're matching meanings.

In this project I used `all-MiniLM-L6-v2` from the `sentence-transformers` library. It converts any text into a 384-dimensional vector (a list of 384 numbers). It runs completely locally on CPU, no API needed.

---
## What is FAISS?

FAISS stands for Facebook AI Similarity Search. It's a library that stores vectors and lets you search through them extremely fast.

Think of it like a database, but instead of searching for exact matches, it searches for the *closest* matches based on vector distance. When you ask a question, FAISS finds the document chunks whose vectors are closest to your question's vector , those are the most semantically relevant chunks.

I used `IndexFlatL2` which calculates Euclidean distance between vectors. It's the simplest index type — good for small datasets like the 50-100 chunks we get from a typical PDF.

---

## What is LangChain?

LangChain is a framework for building applications with LLMs. It has a lot of utilities that make common LLM tasks easier.

In this project I only used one part of it `RecursiveCharacterTextSplitter`. This splits long text into smaller chunks in a smart way. Instead of just cutting at exactly 500 characters, it tries to split at natural boundaries - paragraph breaks first, then sentence breaks, then word breaks. This keeps chunks more readable and meaningful than dumb character splitting.

---

## What is pdfplumber?

PDFs aren't plain text files they're complex binary files with fonts, layouts, images, and metadata mixed in. You can't just open a PDF and read it like a text file.

`pdfplumber` is a Python library that handles all that complexity. It goes through each page, extracts the actual text content, and returns it as a clean string. It works well for text-based PDFs. If the PDF is scanned (just images of pages), it can't extract text.

---
