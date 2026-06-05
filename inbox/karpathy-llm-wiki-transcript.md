# Nate Herk — Building an LLM Wiki with Obsidian & Claude Code

**Source:** YouTube video by Nate Herk (Apr 5, 2026)
**Original idea:** Andrej Karpathy's gist on LLM-powered knowledge bases

## Transcript Summary

Andrej Karpathy shared his method for building LLM-powered knowledge bases using nothing but markdown files and Claude Code. This video walks through exactly how to set it up in about 5 minutes using Obsidian as a front end.

### The Core Idea

Modern LLMs are now capable enough to act as an operating system for your files. By keeping everything in human-readable Markdown and letting an autonomous agent manage the connections, you eliminate the need for complex retrieval pipelines, embedding models, and vector indexing. The AI simply acts as a tireless librarian that continuously organizes and retrieves your raw text files.

### The Tech Stack

- **Storage & Frontend:** Obsidian — acts as the UI and the file-system foundation, storing all data as simple, locally hosted `.md` files
- **The Agent:** Claude Code — an agentic command-line tool that acts as the "brain" orchestrating the data
- **The Format:** Raw Markdown with `[[wikilinks]]` for bidirectional linking

### The Execution Workflow

1. **Ingestion:** Drop raw, unstructured data (YouTube transcripts, research articles, notes) into a specific folder in the Obsidian vault
2. **Agentic Structuring:** Prompt Claude Code via the terminal to process the new files. The LLM reads the raw text, extracts key concepts, creates individual markdown files for those specific entities, and automatically injects bidirectional wikilinks to map relationships between files
3. **Querying:** Instead of cosine similarity search, ask the agent a question. The agent uses its tools to search the local directory, read relevant markdown files, traverse linked concepts, and synthesize an answer based on the actual text in the vault

### LLM Wiki vs Traditional RAG

- **No vector database needed** — eliminates Pinecone, Chroma, pgvector, etc.
- **No embedding pipeline** — no chunking, no embedding models, no indexing
- **Full document context** — the LLM reads entire files, not top-k chunks
- **Human-readable storage** — everything is browsable in Obsidian
- **Zero infrastructure** — just local files and a CLI tool
- **Trade-off:** Requires larger context windows, costs more tokens per query

### Key Quotes & Insights

- Karpathy's framing: LLMs as an "operating system" for personal knowledge
- The shift from "retrieve and generate" to "read and synthesize"
- Obsidian's graph view naturally visualizes the knowledge structure the agent builds
- This approach scales better for personal knowledge bases than for enterprise-scale document stores

### Tools Mentioned

- Obsidian (obsidian.md)
- Claude Code (Anthropic)
- Karpathy's gist: https://gist.github.com/karpathy/442a40be7e70f29fea3040eb846d0237
- AI 2027 article: https://ai-2027.com/
