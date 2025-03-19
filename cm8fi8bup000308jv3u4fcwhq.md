---
title: "What are MCP Servers"
seoTitle: "Understanding MCP Servers"
seoDescription: "MCP Servers enhance LLMs by integrating tools, data access, and context, fostering advanced AI workflows and interactions"
datePublished: Wed Mar 19 2025 05:51:23 GMT+0000 (Coordinated Universal Time)
cuid: cm8fi8bup000308jv3u4fcwhq
slug: what-are-mcp-servers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1742360855542/321c20db-d61e-477e-bb6b-792416492325.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1742363068296/0aaac9ae-62a6-4207-ae39-20bfb2729906.png
tags: ai, anthropic, model-context-protocol, mcp, mcp-server

---

# **MCP Servers :**

[MCP Servers](https://modelcontextprotocol.io/quickstart/server) are essentially regular servers equipped with various tools designed to interact with Large Language Models (LLMs) to perform specific actions beyond simple text prediction. The term **MCP server** is becoming a common way to refer to these servers that facilitate Agentic AI workflows

---

## **Why MCP (** [Model Context Protocol](https://github.com/modelcontextprotocol/servers) ) **?**

[MCP helps you build](https://github.com/modelcontextprotocol/servers) agents and complex workflows on top of LLMs. LLMs frequently need to integrate with data and tools, and MCP provides:

* A growing list of pre-built integrations that your LLM can directly plug into
    
* The flexibility to switch between LLM providers and vendors
    
* Best practices for securing your data within your infrastructure
    

---

## Addressing the Limitations of LLMs

While LLMs like ChatGPT and Gemini are excellent at text prediction and generation, they cannot independently perform actions like sending emails, running database queries, or editing files**.**

MCP servers bridge this gap by providing the necessary tools and *context for LLMs to interact with external systems*

---

## **The Problem of Lack of Standardization**

Before MCP, there wasn't a Standardized Protocol for LLMs to communicate with these external tools. Each tool might have its own way of interacting with a client. **MCP aims to Establish these standards and protocols** for communication between clients, MCP servers, and LLMs

---

## **Client-MCP Server Interaction**

Clients, which can be applications like Cursor, Windsurf, games or even software like Premiere Pro, communicate with MCP servers

Initially, these servers were just regular servers with specific functionalities, *but now they are increasingly referred to as MCP servers*

---

## **Providing Context is Crucial**

* LLMs require context to understand the user's intent and perform tasks effectively**.** MCP servers play a vital role in providing this context to the LLM
    
* This context can include relevant files, database schemas, or access to specific data sources
    

**Methods of Providing Context :** Anthropic, the creator of the MCP concept, outlines several ways to provide context

1. **Tools :** These are essentially functions on the server that can fetch data or perform actions
    
2. **Resources :** These can be files (like CSV, JavaScript, TypeScript) that are sent along with the function call to provide additional context
    
3. **Sampling :** This involves using different LLMs for different parts of a task and allowing them to share context
    
4. **Prompts :** Enhancing the user's initial prompt to provide more detailed instructions to the LLM
    

---

## **MCP as a Protocol and Standard**

MCP is not a specific software, but rather a *set of standards and protocols that define how different components should interact*. This is similar to how web standards (like HTTPS) and API standards (like REST)

---

## **Stateful Nature (Currently)**

MCP servers are described as stateful, meaning they maintain some information between requests. However, the speaker questions whether this stateful nature is always necessary and suggests the possibility of stateless MCP servers in the future

---

## **Communication Methods**

MCP servers can communicate with clients using *Server-Sent Events or traditional Message Endpoints similar to REST APIs*

---

## **Conclusion**

MCP servers represent a significant architectural pattern that enables the creation of more capable and practical AI agents by providing a structured and standardized way for LLMs to interact with the complex world of software and data

If you found this blog post helpful, please consider sharing it with others who might benefit. You can also follow me for more content on JavaScript, React.js, Next.js, and other web Development, AI topics.

For *Paid collaboration*, *Web Development freelancing* *work*, mail me at: [**krishdesai044@gmail.com**](mailto:krishdesai044@gmail.com)

Connect with me on [**Twitter**](https://x.com/DKB972), [**LinkedIn**](https://www.linkedin.com/in/krishdesai117/), and [**GitHub**](https://github.com/dkcoder02).

Thank you for Reading

Happy Coding