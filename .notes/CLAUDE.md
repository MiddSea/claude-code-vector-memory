# Claude Code Vector Memory Project

This is a semantic memory system for Claude Code that gives Claude persistent memory across conversations by indexing and searching session summaries.

## Project Overview

- **Purpose**: Semantic memory system for Claude Code using vector search
- **Technology**: Python, ChromaDB, sentence transformers, vector embeddings
- **Platform**: Cross-platform (Linux/macOS/Windows)

## Development Environment

### Python Environment
- Uses virtual environment in `venv/`
- Python 3.8+ required
- Dependencies managed via `requirements.txt`

### Key Commands
```bash
# Setup
./setup.sh      # Linux/macOS
setup.bat       # Windows

# Search memories
./search.sh "query"    # Linux/macOS
search.bat "query"     # Windows
claude-memory-search "query"  # Global command

# Reindex summaries
python reindex.py
```

### Testing
- Uses pytest framework
- Tests located in `tests/` directory
- Run with: `python -m pytest tests/`

### Code Quality
- Pre-commit hooks configured in `.pre-commit-config.yaml`
- Ruff for linting and formatting (config in `.ruff.toml`)
- Use `python -m ruff check` and `python -m ruff format`

## Project Structure

- `scripts/` - Core Python modules (index_summaries.py, memory_search.py, health_check.py)
- `claude-integration/` - Claude Code integration files
- `claude_summaries/` - Directory for Claude session summaries
- `docs/` - Documentation and troubleshooting guides

## Development Notes

- Main entry points: `search.py`, `reindex.py`, setup scripts
- Vector database stored in `chroma_db/` directory
- Uses semantic search with hybrid scoring (similarity 70%, recency 20%, complexity 10%)
- ChromaDB for vector storage and similarity search
- Rich terminal output for beautiful CLI experience

## Git Workflow

- Main branch: `main`
- Follow commit message conventions from CONTRIBUTING.md
- Include all files in commits (use `git add .`)

## Environment Setup

When working on this project:
1. Activate virtual environment: `source venv/bin/activate` (Linux/macOS) or `venv\Scripts\activate` (Windows)
2. Install dependencies: `pip install -r requirements.txt`
3. Run health check: `python scripts/health_check.py`