# AgentDesk

AgentDesk is a durable AI agent runtime designed for long-running workflows with explicit approval gates, MCP tool integration, and persistent execution traces.

> **Status:** Phase 0 (Foundation) — Minimal configuration, packaging, and testing infrastructure.

---

## Prerequisites

- **Python**: 3.11 or newer
- **Virtual Environment**: Standard `venv`

---

## Quickstart & Local Setup

### 1. Clone & Create Virtual Environment

```bash
cd agentdesk
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install Dependencies

Install the project in editable mode with development dependencies:

```bash
pip install -e ".[dev]"
```

### 3. Configure Environment Variables (Optional)

Copy `.env.example` to `.env` to customize settings:

```bash
cp .env.example .env
```

Safe defaults are provided out of the box so AgentDesk can run locally and offline without external credentials or active API keys.

---

## Configuration Settings

Settings are managed via `pydantic-settings` in `agentdesk.config.Settings`:

| Variable | Default | Description |
| :--- | :--- | :--- |
| `APP_NAME` | `AgentDesk` | Application name identifier |
| `ENVIRONMENT` | `development` | Environment (`development`, `test`, `staging`, `production`) |
| `DATABASE_URL` | `sqlite:///./agentdesk.db` | Database connection URL |
| `MAX_AGENT_STEPS` | `50` | Maximum steps an agent can execute per run |
| `RUN_TIMEOUT_SECONDS` | `300.0` | Maximum execution time in seconds per run |
| `LLM_PROVIDER` | `None` | Optional LLM provider name (e.g., `openai`, `anthropic`) |
| `LLM_API_KEY` | `None` | Optional LLM API key (protected by `SecretStr`) |
| `LLM_MODEL` | `None` | Optional model name |
| `LLM_BASE_URL` | `None` | Optional custom LLM endpoint base URL |

---

## Testing & Quality Assurance

### Run Tests and Coverage

```bash
pytest
```

### Run Linter Checks

```bash
ruff check .
```

### Run Formatter Checks

```bash
ruff format --check .
```

---

## Project Structure

```text
agentdesk/
├── .env.example             # Example environment configuration
├── .gitignore               # Git ignore rules (.env, *.db, venv, caches)
├── .github/
│   └── workflows/
│       └── ci.yml           # GitHub Actions CI workflow (3.11 & 3.12)
├── docs/
│   ├── ARCHITECTURE.md      # Intended system architecture & status
│   └── BUILD_LOG.md         # Phase 0 build log and test records
├── pyproject.toml           # Project metadata, dependencies, tool configs
├── README.md                # Project documentation and quickstart
├── src/
│   └── agentdesk/
│       ├── __init__.py      # Package export
│       └── config.py        # Typed settings and validation
└── tests/
    └── test_config.py       # Configuration and credential safety tests
```

# agentdesk
