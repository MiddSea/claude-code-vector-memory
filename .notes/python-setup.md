# Python Setup for Claude Code Vector Memory

## Issue Encountered
The setup script failed with:
```
❌ Error: Command 'pip install --upgrade pip' returned non-zero exit status 127.
/bin/sh: pip: command not found
```

## Root Cause
The setup script wasn't activating the virtual environment before running pip commands.

## System Status
- ✅ Python 3.13.5 installed via Homebrew (`/opt/homebrew/bin/python3`)
- ✅ Virtual environment exists in `venv/`
- ✅ pip 25.1.1 available inside venv
- ❌ Setup script doesn't activate venv properly

## Manual Setup Process

### 1. Activate Virtual Environment
```bash
source venv/bin/activate
```

### 2. Upgrade pip
```bash
pip install --upgrade pip
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Verify Installation
```bash
python scripts/health_check.py
```

### 5. Test Search
```bash
python search.py "test query"
```

## Environment Details
- **OS**: macOS (Darwin 24.6.0)
- **Python**: 3.13.5 (Homebrew installation)
- **pip**: 25.1.1 (in venv)
- **Shell**: zsh

## Recommended Fix for setup.sh
The setup script should properly activate the virtual environment:

```bash
#!/bin/bash
# Activate virtual environment
source venv/bin/activate || {
    echo "❌ Failed to activate virtual environment"
    exit 1
}

# Then run pip commands
pip install --upgrade pip
pip install -r requirements.txt
```

## Successful Manual Setup ✅

### What We Did
1. **Diagnosed the issue**: Setup script wasn't activating virtual environment
2. **Manual activation**: `source venv/bin/activate`
3. **Upgraded pip**: `pip install --upgrade pip` (25.1.1 → 25.2)
4. **Installed dependencies**: `pip install -r requirements.txt` ✅
5. **Health check passed**: ✅ Model loaded, 384 dimensions, 2055ms test time
6. **Search test**: Expected failure (no indexed summaries yet)

### Status
- ✅ Python 3.13.5 working
- ✅ Virtual environment activated correctly
- ✅ All dependencies installed successfully
- ✅ Embedding model (384d) loads and works
- ✅ System ready for indexing summaries

### Next Steps
1. Index some Claude summaries: `python reindex.py`
2. Test search functionality: `python search.py "query"`
3. Fix setup script for future use
4. Create MiddSea fork on GitHub