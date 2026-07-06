# LS2026
## Capstone: Multi-Agent AI for Maintenance Operations

**Overview**
This project implements an automated, multi-agent AI system to triage, diagnose, and plan maintenance for mechanical equipment. By bridging core mechanical engineering domain knowledge with advanced LLM workflows, the system processes equipment alerts (such as vibration anomalies or temperature spikes in motor-pump assemblies) and generates actionable repair plans. 

**Core Architecture**
The workflow is orchestrated using LangGraph, which routes equipment alerts through four specialized agents:
*   **Triage Agent:** Classifies the severity (low, medium, high) and fault category of the incoming alert.
*   **Diagnostic Agent (RAG):** Uses Retrieval-Augmented Generation to search a local vector database of mechanical failure modes (e.g., bearing wear, seal leakage, shaft misalignment) to identify root causes and assign confidence scores.
*   **Planning Agent (MCP):** Connects to a simulated Model Context Protocol (MCP) server to check spare parts inventory, technician availability, and work-order history.
*   **Report Agent:** Compiles the findings into a concise, actionable summary for shift supervisors, bypassing complex diagnostics for low-severity cosmetic issues.

**Tech Stack**
*   LangGraph & LangChain
*   Llama 3.1 & Nomic-Embed-Text (via local Ollama instance)
*   ChromaDB (Vector store for RAG)
*   Model Context Protocol (FastMCP)

**Setup and Execution**
1.  Ensure a local Ollama server is running and the necessary models are pulled (`ollama pull llama3.1` and `ollama pull nomic-embed-text`).
2.  Install the required Python dependencies: `langgraph`, `langchain`, `langchain-ollama`, `mcp`, `chromadb`, and `pydantic`.
3.  Run `Capstone.ipynb` in a Jupyter or Colab environment. The notebook will automatically write the sample diagnostic documents and build the ChromaDB vector store.
4.  The notebook also generates `mcp_server.py`, a simulated live database that the Planning Agent queries for inventory and scheduling. 

**Author**
Sabarish S.
