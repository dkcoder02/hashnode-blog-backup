---
title: "Understanding Generative AI: A Beginner’s Guide to Tokenization and Vector Embeddings"
seoTitle: "Generative AI: Intro to Tokenization & Embeddings"
seoDescription: "Learn about Generative AI, tokenization, and vector embeddings. Discover how these concepts help models understand and generate text effectively"
datePublished: Tue May 27 2025 08:20:09 GMT+0000 (Coordinated Universal Time)
cuid: cmb68xfpb000z09jm181jh52b
slug: understanding-generative-ai-a-beginners-guide-to-tokenization-and-vector-embeddings
tags: ai, python, tokenization, generative-ai, vector-embeddings, chaiaurcode

---

## **What is Gen AI?**

**Generative artificial intelligence**, also known as generative AI or gen AI for short, is a type of AI that can *create new content and ideas, including conversations, stories, images, videos and music*. It can learn human language, programming languages, art, chemistry, biology or any complex subject matter. It reuses what it knows to solve new problems.

**For example**, it can learn English vocabulary and create a poem from the words it processes.

Your organization can use generative AI for various purposes, like chatbots, media creation, product development and design.

List of Gen AI LLM Models :

* OpenAI
    
* Anthropic
    
* Google
    
* Deepseek
    
* Alibaba
    

---

## What is Tokenization?

**Tokenization** is the process of converting input text (such as a sentence or paragraph) into smaller pieces called **tokens**, which are the fundamental units that AI models process.

### What is a Token?

A **token** is **word**, **part of a word** or **character** (depending on LLM which tokenizer used).

For example,

```plaintext
Input_token="I love coding and write code."
output_token=["I", " love", " coding", " and", " write", " code", "."]
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748332503418/97d1aee4-0db2-45c8-b0b8-8531ad55f9c2.png align="center")

---

**Why Tokenization Matters in GenAI**?

Generative AI models (like GPT, LLaMA, Claude) do not understand raw text directly.

1. **Tokenize** the text.
    
2. Convert tokens to **numerical numbers.**
    
3. Process these numbers using deep learning models.
    
4. Generate output tokens, *which are then converted back to readable text* (**detokenized**).
    

---

## What is Vector Embeddings?

A **vector embedding** is a **dense, continuous, fixed-size vector** (e.g., 512 or 768 dimensions) that captures the **semantic meaning** of the input.

For example:

* The word *"king"* might be represented as a 768 dimensional vector:
    
    ```plaintext
    [0.12, -0.84, ..., 0.09]
    ```
    
    Words like *"queen"*, *"royalty"* and *"monarch"* would have **similar vectors**, meaning they are **close together** in the vector space.
    

### Why Are Embeddings Important?

* Understand **similarity** between words or sentences.
    
* Perform **semantic search**.
    
* Enable **recommendation systems**.
    

---

**How to create Vector Embeddings in python using openai LLM Model**:

```python
from dotenv import load_dotenv
from openai import OpenAI

load_dotenv()

client = OpenAI()

text = "java better then javascript"

response = client.embeddings.create(
    model="text-embedding-3-small",
    input=text
)

print("Vector Embeddings", response)
print(len(response.data[0].embedding))
```

---

**Quick Summary**

the process of breaking text into tokens for AI processing and vector embeddings, which capture semantic meanings in dense vectors. These concepts are crucial for understanding word similarity, semantic searches. The article also touches on creating vector embeddings using the OpenAI LLM model.

Thank you