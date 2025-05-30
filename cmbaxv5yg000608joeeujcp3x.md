---
title: "How I Built My First AI Product: A Persona-Based Chatbot Inspired by Hitesh Choudhary & Piyush Garg"
seoTitle: "Building My First Persona-Based AI Chatbot"
seoDescription: "Explore how I built a persona-based AI chatbot, inspired by tech mentors, using prompt engineering and open-source tools"
datePublished: Fri May 30 2025 15:09:18 GMT+0000 (Coordinated Universal Time)
cuid: cmbaxv5yg000608joeeujcp3x
slug: how-i-built-my-first-ai-product-a-persona-based-chatbot-inspired-by-hitesh-choudhary-and-piyush-garg
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1748617689876/40aed27a-9139-4883-8770-2ee85a392a6e.webp
tags: ai, python, chaiaurcode

---

> “Don’t just learn AI—build with it.” That’s what I kept telling myself before starting my first real AI product. In this blog, I’ll walk you through how I built a persona-based chatbot that mimics the tone, language and behavior of two of my favorite tech mentors — **Hitesh Choudhary** and **Piyush Garg**.

This was more than just a side project. It was a learning journey — about **prompt engineering**, **persona modeling** and bringing together open-source tools to make something genuinely useful.

---

## 🚀 The Idea: Bringing Tech Mentors to Chat

I often wished I could get personal advice from developers I look up to. What would Hitesh Choudhary say about choosing a tech stack? How would Piyush Garg explain IAM roles in AWS?

That’s when the idea hit me — *what if I could build an AI that talks like them?*

A **persona-based chatbot** that doesn’t just answer questions, but does it like ***them*** — with their tone, values and favorite metaphors.

---

## 🧠 Learning the Core: Prompt Engineering

Before building anything, I immersed myself in **prompt engineering**. Here’s a breakdown of the techniques I learned and used:

### 1\. 📌 System Prompting

I started by defining a **system prompt** that sets the tone and behavior of the chatbot. Example:

```python
You are Hitesh Choudhary, an experienced software engineer and educator. You explain complex tech topics using real-world analogies, humor, and motivation.
```

This alone dramatically changed the model’s response style.

### 2\. ✍️ Writing Better Prompts

Key learnings:

* Use **clear instructions**
    
* Define **roles** explicitly (e.g., “Act as…”)
    
* Add **constraints** or goals (e.g., “Keep answers under 100 words.”)
    
* Avoid ambiguity (clarify context wherever possible)
    

### 3\. 📚 Prompt Formats: Alpaca, ChatML & Inst

I experimented with different formats:

* **Alpaca Prompt** (used in instruction-tuned models):
    
    ```python
    ### Instruction:
    Explain the concept of recursion.
    
    ### Response:
    ```
    
* **ChatML** (used in OpenAI chat models):
    
    ```python
    jsonCopyEdit[
      {"role": "system", "content": "You are Hitesh Choudhary..."},
      {"role": "user", "content": "What is Docker?"}
    ]
    ```
    
* **Inst Format** (used in LLaMA-style models):
    
    ```python
    <s>[INST] <<SYS>> You are... <</SYS>> What is Git? [/INST]
    ```
    

Each format has its strengths depending on the model backend.

### 4\. 🧪 Zero-Shot Prompting

I began with **zero-shot prompts** — just a single user instruction. Surprisingly, this worked well for basic FAQs but lacked personality depth.

### 5\. 🧵 Chain-of-Thought Prompting

To help the model **think step by step**, I used prompts like:

> "Explain the concept of OAuth2. First explain what problem it solves, then describe how the flow works."

This improved the logical flow of answers significantly.

### 6\. 🎯 Few-Shot Prompting

Finally, I added a few real examples of how the personas would respond:

```python
### Instruction:
How should I start learning AWS?

### Response (Hitesh):
Start with IAM roles and EC2. Break things. Watch the logs. AWS is a beast, but you’ll tame it one service at a time.
```

This helped the chatbot **"learn the style"** from just a few examples.

---

## ⚙️ Tech Stack

Here’s what I used to build the chatbot:

* **Backend**: Python
    
* **AI Model**: OpenAI’s GPT-3.5 via API (you can easily swap it with open-source models like Mistral or LLaMA)
    
* **Prompt Management**: Custom prompt templates for each persona
    
* **Source Code**: [GitHub - Persona AI Bot](#)
    

---

## 🧩 Real-World Use Cases

This chatbot architecture can be extended to:

* **EdTech Assistants**: Emulate teachers or domain experts
    
* **Corporate Training**: Create internal knowledge agents in a company’s tone
    
* **Customer Support**: Bots that align with brand voice
    
* **Entertainment**: Chat like Sherlock Holmes, Tony Stark, or even a fictional CTO!
    

---

## 📉 Challenges I Faced

1. **Tone Drift**: Sometimes the chatbot forgot who it was. I fixed this by reinforcing persona traits in every system prompt.
    
2. **Overfitting to Examples**: Few-shot prompts made it too rigid. I balanced between dynamic and static styles.
    

---

## 📚 Lessons Learned

* Prompting is both an **art and science** — every word matters.
    
* Personas aren’t just about tone — they need context, values and constraints.
    
* Start simple. Iterate fast. Measure responses like you would any UX component.
    

---

## 🧑‍💻 How You Can Build Your Own

Want to build your own persona chatbot? Here’s a mini roadmap:

1. Define your **persona** clearly.
    
2. Choose an AI model (OpenAI API, Ollama, Claude).
    
3. Design a **system prompt** that sets the tone.
    
4. Choose between **zero-shot, few-shot** and **chain-of-thought** prompting.
    
5. Use open-source UI libraries like Shadcn/UI to rapidly build your frontend.
    
6. Add personalization and deploy 🚀
    

---

## ☕ Final Thoughts

Building this AI product taught me how **prompting is programming** — but in natural language. If you’re a developer dreaming of working with AI. You need curiosity, clarity and the courage to build something imperfect and keep improving it.

Inspired by mentors, powered by open-source and shaped by hundreds of failed prompts — this chatbot is just the beginning.

---

### 🔗 GitHub Repository

[**Persona AI Bot – Source Code**](https://github.com/dkcoder02/Persona-ai-bot)

#**Chaiaurcode #ai #ai-product #python**