---
title: "Introduction to RAGs (Retrieval Augmented Generation)"
seoTitle: "RAGs: Basics of Retrieval Augmented Generation"
seoDescription: "RAG reduces AI hallucinations using indexing, vectorization and chunking, improving AI model reliability"
datePublished: Sat Jun 07 2025 17:23:19 GMT+0000 (Coordinated Universal Time)
cuid: cmbmi6bil000302l4a22p8c6h
slug: introduction-to-rags-retrieval-augmented-generation
tags: python, vector-database, rag, chaiaurcode

---

***Understanding Indexing, Vectorization, Chunking and Why RAGs Matter***

In the world of Generative AI, you might’ve noticed a recurring problem: **LLMs hallucinate.** They confidently generate answers that sound right — but are often wrong or outdated.

That’s where **RAG (Retrieval-Augmented Generation)** comes in. It’s a powerful technique that enhances large language models (LLMs) by combining **information retrieval** with **text generation** — so your model doesn't just guess; it refers.

In this article, we’ll cover the foundational building blocks of RAG:

* What is Indexing?
    
* Why do we perform Vectorization?
    
* Why do RAGs exist?
    
* Why perform Chunking and Overlapping?
    

---

## 🔍 What is Indexing?

**Indexing** is the process of organizing and storing data in a way that makes it **efficiently retrievable** later.

Think of it like creating a searchable catalog of your documents — so when the user asks a question, the system can find the most relevant content *before* generating a response.

In RAG pipelines, indexing typically involves:

* Preprocessing documents
    
* Breaking them into smaller pieces (chunks)
    
* Converting them into vectors (via embeddings)
    
* Storing them in a **vector database** like Pinecone, FAISS, or Weaviate
    

> 📌 In simple terms: **Indexing = Preparing knowledge to be found later.**

---

## 🧠 Why Do We Perform Vectorization?

LLMs can't "understand" raw text like humans do. They work with numbers — specifically, **vectors**.

**Vectorization** is the process of converting a piece of text into a numerical format using **embeddings**.

These embeddings capture the **semantic meaning** of the text. For example:

* “What is AI?” and “Define artificial intelligence” will have similar vectors.
    
* This allows the system to find semantically related content, even if the keywords don’t match.
    

We use pre-trained models like `text-embedding-ada-002` from OpenAI, or open-source models like `sentence-transformers` for this step.

> 📌 Vectorization is what enables **semantic search** — the backbone of RAG retrieval.

---

## 🤔 Why Do RAGs Exist?

Great question.

LLMs are powerful but **limited by their training data and context window**. They:

* Don’t know anything published after their cutoff date
    
* Can hallucinate if unsure
    
* Can’t remember specific company documents or PDFs unless trained on them
    

**RAG solves this.**  
By separating **knowledge retrieval** from **text generation**, RAG allows:

* Real-time access to external documents (docs, databases, APIs)
    
* Factual, grounded responses
    
* Smaller models to perform better without re-training
    

### RAG = Retrieval + Generation

Here’s a simplified flow:

1. User asks a question
    
2. System retrieves relevant documents from a knowledge base (retrieval)
    
3. The retrieved context is passed into the LLM (generation)
    
4. The LLM responds using both its internal knowledge and external context
    

> 📌 RAG lets you “plug in” your own knowledge into an LLM — **without fine-tuning.**

---

## 📦 Why Do We Perform Chunking?

Imagine you upload a 100-page PDF. Should the system treat that entire document as one searchable block?

Of course not.

That’s where **chunking** comes in.

**Chunking** means breaking down long documents into **smaller, more manageable pieces** (e.g., paragraphs, sections).

This:

* Makes search faster
    
* Improves relevance during retrieval
    
* Reduces token overhead during generation
    

Typically, chunks are split by sentence, paragraph or a fixed number of tokens (e.g., 300–500 tokens).

---

## 🔁 Why Perform Overlapping Over Chunking?

Sometimes, chunking by itself **loses context** at the edges of each chunk.

Example:

* Chunk 1 ends with a sentence like “This leads us to the core architecture...”
    
* Chunk 2 starts with “The transformer model has multiple layers...”
    

Without overlap, the model may not understand the connection between the two.

**Overlapping** solves this by ensuring chunks share a few lines/tokens from their neighbors.

This:

* Preserves context continuity
    
* Improves semantic matching
    
* Helps avoid broken or disjointed meaning
    

A typical overlap might be 10–20% of the chunk size.

> 📌 Think of overlapping like giving your model a little memory across the boundaries.

---

## ✅ Summary: Tying It All Together

| Concept | Purpose |
| --- | --- |
| **Indexing** | Organizes data for efficient retrieval |
| **Vectorization** | Converts text into semantic numerical format |
| **RAG** | Enhances LLMs by retrieving external data |
| **Chunking** | Breaks documents into smaller, searchable parts |
| **Overlapping** | Preserves context between chunks |

---

## 🧠 Final Thoughts

RAG is becoming a **foundational pattern in GenAI applications**, from enterprise chatbots to coding agents and document assistants.

If you’re building AI products — don’t just prompt LLMs blindly.  
**Structure your knowledge. Retrieve smart. Generate responsibly.**

Understanding how **indexing**, **vectorization** and **chunking** work under the hood gives you a strong edge in designing scalable, trustworthy AI systems.

Happy building! 🧱⚡