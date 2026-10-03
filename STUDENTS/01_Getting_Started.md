# INTE11ECT_APP — Student Getting Started

## What You'll Build
A context-aware AI application that remembers your documents, answers questions about them, and routes complex queries to specialized PAX modules — no cloud required.

## Prerequisites
- Python 3.10+
- Ollama installed
- Basic understanding of APIs and JSON

## Install
```bash
ollama pull mistral:7b
ollama pull nomic-embed-text
pip install inte11ect chromadb
```

## First Working Example
```python
from inte11ect import Session

session = Session(
    model="ollama/mistral:7b",
    context_strategy="sliding_window",
    window_size=4096
)

# Load a document into context
session.add_document("README.md")

response = session.query("What are the main features described in this document?")
print(response.text)
print(f"Tokens used: {response.context_tokens}")
```

## Add Persistent Memory
```python
from inte11ect import Session, VectorMemory
import chromadb

memory = VectorMemory(
    backend=chromadb.Client(),
    collection="my_docs",
    embedding_model="nomic-embed-text"
)

session = Session(model="ollama/mistral:7b", memory=memory)
session.add_document("project_notes.txt")
session.add_document("meeting_summary.txt")

answer = session.query("What action items came out of the last meeting?")
print(answer.text)
```

## On Kaggle (loiskleinner account, T4 GPU)
```python
# Cell 1: Setup
!pip install inte11ect chromadb
!curl -fsSL https://ollama.ai/install.sh | sh
!ollama serve &
import time; time.sleep(5)
!ollama pull mistral:7b && ollama pull nomic-embed-text
```

## What's Next
- Try `session.remember()` to store facts across sessions
- Explore routing queries to PAX_MATH_SOLVER for math problems
- See EDUCATORS guide for architecture details
