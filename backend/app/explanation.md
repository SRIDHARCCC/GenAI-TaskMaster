# Backend Core Application Package

The `backend/app/` directory is the core Python package containing the application logic. It structures databases, schema models, tools, and multi-agent systems into reusable modules.

## Directory Structure

```text
backend/app/
├── agents/             # Multi-Agent orchestrators & specialists
├── database/           # Database module package structure
├── models/             # SQLAlchemy ORM and Pydantic models
├── tools/              # Tools invoked by AI agents (DB wrappers)
└── __init__.py         # Package constructor
```

## Key Files in this Directory

*   [\_\_init\_\_.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/__init__.py): Standard Python package initializer. It exposes `app` module boundaries, making sub-directories (`agents`, `database`, `models`, `tools`) importable across the server.

## Subdirectories

1.  [agents/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/agents/explanation.md): Houses the role-based conversational AI agents (Coordinator, Task Executor, Schedule Manager) powered by Gemini.
2.  [database/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/database/explanation.md): Package folder hosting database modules.
3.  [models/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/models/explanation.md): Defines SQLAlchemy entities mapped to tables in SQLite, alongside Pydantic models for request and response validation.
4.  [tools/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/tools/explanation.md): Defines database query wrappers that are translated into tool definitions for the Gemini agent loop.
