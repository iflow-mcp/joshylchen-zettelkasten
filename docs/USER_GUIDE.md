
# User Guide

## What is this?
A Zettelkasten assistant to capture, refine, and connect atomic notes. It stores your notes as Markdown (with YAML frontmatter) and adds AI-assisted workflows (optional).

## Core Concepts
- **Atomic note**: a single idea per note, with a unique `id`, `title`, and optional `summary`.
- **Summary**: A concise summary (max 280 characters) that captures the key points of the note.
- **Links**: typed relationships to other notes (e.g., `supports`, `refines`, `extends`).
- **CEQRC** workflow: Capture → Explain → Question → Refine → Connect.

## Create Your First Note (CLI)
```bash
python -m zettelkasten_assistant.cli new "Cognitive Load" -c "Mental effort needed to use a tool" -t cognitive-science, design
python -m zettelkasten_assistant.cli show 20250101010101
```

## Search (CLI)
```bash
python -m zettelkasten_assistant.cli search "cognitive NEAR/3 load"
python -m zettelkasten_assistant.cli search "effort" --tag cognitive-science
```

## Link Notes (CLI)
```bash
python -m zettelkasten_assistant.cli link 20250101010101 20250102020202 supports
```

## Web API
- Start: `python -m zettelkasten_assistant.server.api` → visit `/docs`
- Create: `POST /notes` with `{title, body, summary?, tags}`
- Generate Summary: `POST /generate-summary` with `{text}`
- Search: `GET /search?q=term` (searches title, body, and summary)
- CEQRC: `POST /notes/{id}/ceqrc`

## Streamlit UI
```bash
streamlit run ui_streamlit.py
```
Use tabs to create/edit, search, and run CEQRC. The interface includes:
- **Summary field** with character counter (280 max)
- **Auto-generate summary** button using AI
- **Search** includes summaries in full-text search
