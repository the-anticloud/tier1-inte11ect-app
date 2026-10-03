# INTE11ECT_APP — Educator's Teaching Guide

## Course Fit: human-computer interaction, AI interfaces, cognitive augmentation systems

## 3-Week Module: Building Intelligence-Augmented Applications

### Week 1: Cognitive Augmentation Architecture
**Lecture Topics:**
- What INTE11ECT_APP provides: context management, memory surfaces, inference routing
- The difference between a smart UI and a truly augmented interface
- How local inference enables privacy-preserving intelligence features
- Latency budgets: when to pre-compute vs. infer on demand

**Lab Exercise:**
```python
# Basic INTE11ECT_APP session with Ollama
from inte11ect import Session, ContextWindow
import ollama

session = Session(
    model="ollama/mistral:7b",
    context_strategy="sliding_window",
    window_size=4096
)
session.add_document("project_notes.txt")
response = session.query("Summarize the key action items from my notes")
print(response.text)
print(f"Context tokens used: {response.context_tokens}")
```

### Week 2: Memory Surfaces and Persistent Context
**Lecture Topics:**
- Short-term vs. long-term memory in AI apps
- Vector store integration for semantic retrieval
- Context compression techniques to stay within model limits
- Building retrieval-augmented generation without cloud APIs

**Lab Exercise:**
```python
from inte11ect import Session, VectorMemory
import chromadb

memory = VectorMemory(
    backend=chromadb.Client(),
    collection="user_context",
    embedding_model="nomic-embed-text"  # local via Ollama
)
session = Session(model="ollama/llama3:8b", memory=memory)
session.remember("User prefers concise bullet-point summaries")
response = session.query("What format should I use for this report?")
print(response.text)
```

### Week 3: Integration with Anticloud Ecosystem
**Lecture Topics:**
- INTE11ECT_APP as a UI layer over PAX inference engines
- Routing queries to specialized PAX modules (PAX_MATH_SOLVER, PAX_REASONING)
- Logging sessions to AIOSS for auditability
- Deployment on SOVEREIGN_OS

**Lab Exercise:**
```python
from inte11ect import Session
from pax_client import PAXRouter
router = PAXRouter(endpoint="localhost:8080")
session = Session(model="pax", pax_router=router)
result = session.query("Solve this integral: ∫x²dx")
print(result.text)
```

## Exam Questions
1. Define the tradeoff between context window size and inference latency in an augmented application. How does INTE11ECT_APP's sliding window strategy address this?
2. Explain why a local vector store is preferable to a cloud embedding service for enterprise deployments. What embedding model would you use with Ollama and why?
3. Sketch the data flow when INTE11ECT_APP routes a math query to PAX_MATH_SOLVER. What protocol is used at each boundary?
