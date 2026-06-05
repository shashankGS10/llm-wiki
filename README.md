# LLM Wiki

A local, agent-driven knowledge base using plain Markdown files and Claude Code — no vector databases, no embeddings, no complex RAG pipelines.

Based on [Andrej Karpathy's LLM Wiki concept](https://gist.github.com/karpathy/442a40be7e70f29fea3040eb846d0237).

## How It Works

1. **Drop** raw content (transcripts, articles, notes) into `inbox/`
2. **Run** `claude` in this directory and ask it to ingest
3. **Query** your knowledge base by asking questions — the agent reads files, follows wikilinks, and synthesizes answers

## Stack

| Layer | Tool |
|-------|------|
| Storage & UI | [Obsidian](https://obsidian.md) |
| Agent | [Claude Code](https://docs.anthropic.com/en/docs/claude-code) |
| Format | Markdown + `[[wikilinks]]` |

## Setup

```bash
# 1. Clone this repo
git clone <your-repo-url>
cd llm-wiki

# 2. Open in Obsidian
# File → Open Vault → select this folder

# 3. Drop content into inbox/
cp my-transcript.md inbox/

# 4. Run Claude Code
claude
# Then: "Ingest the new files in inbox/"
```

## Vault Structure

```
inbox/       → Raw, unprocessed content
wiki/        → Structured, interlinked knowledge pages
templates/   → Markdown templates for consistency
CLAUDE.md    → Agent instructions
```

## Why Not Traditional RAG?

| Traditional RAG | LLM Wiki |
|----------------|----------|
| Chunk → embed → vector DB → cosine search | Agent reads files directly |
| Needs infrastructure (Pinecone, Chroma, etc.) | Just local `.md` files |
| Lossy retrieval (top-k chunks) | Full document context |
| Complex pipeline to maintain | Zero maintenance |
| Opaque similarity scores | Human-readable wikilinks |

## Demo

> _See the Loom walkthrough: [link TBD]_

## License

MIT
