# GenAI-TaskMaster Backend Server

The backend directory contains the server-side architecture of the GenAI-TaskMaster application. Built on **FastAPI**, it exposes a RESTful API and WebSocket endpoints for AI orchestration, database management, and voice assistant operations.

## Directory Structure

```text
backend/
├── app/                  # Main Python package for application logic
├── Dockerfile            # Local development Docker configuration
├── Dockerfile.prod       # Production-ready Docker configuration
├── main.py               # Server entry point and API definitions
├── requirements.txt      # Python dependencies
├── reset_db.py           # Database purge utility script
├── start_backend.py      # Server development launcher
└── test_*.py             # Quality assurance and validation scripts
```

## Main Files in this Directory

### 🚀 Server Entry Points
*   [main.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/main.py): The heart of the FastAPI backend. It manages:
    *   **FastAPI Setup**: Initializes the app, CORS middleware configurations, and routing.
    *   **Startup Tasks**: Validates the presence of `GEMINI_API_KEY`, initializes database engine, and populates tables.
    *   **REST API Endpoints**: Exposures of `/api/tasks`, `/api/schedule`, `/api/notes`, `/api/workflow`, `/api/tools/available`, and `/api/agents/status`.
    *   **WebSocket Interface**: Implements `/api/voice-chat` to manage live duplex voice data streaming.
*   [start_backend.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/start_backend.py): Simple development helper that boots the server on port 8080 using `uvicorn.run("main:app", host="0.0.0.0", port=8080, reload=True)`.

### 📦 Setup & Dependencies
*   [requirements.txt](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/requirements.txt): Lists necessary packages for operation:
    *   `fastapi` & `uvicorn`: Web framework and server.
    *   `sqlalchemy`: SQL toolkit and ORM.
    *   `google-generativeai`: Google Gemini integration.
    *   `websockets`: WebSocket server handling.
    *   `python-dotenv`: Environment variable handling.
*   [Dockerfile](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/Dockerfile): Containerizes the FastAPI application for development, mounting the local directory and running Uvicorn.
*   [Dockerfile.prod](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/Dockerfile.prod): Heavyweight container setup for production deployments (e.g. GCP Cloud Run). Uses a multi-worker production configuration.

### 🧪 Tests & DB Helpers
*   [reset_db.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/reset_db.py): Drops all tables in `tasks.db` and recreates them fresh.
*   [test_setup.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/test_setup.py): Smoke tests database connections, schema validation, and creates tables if they are missing.
*   [test_ai_response.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/test_ai_response.py): Validates single-turn connection to Google Gemini API.
*   [test_ai_multiple.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/test_ai_multiple.py): Evaluates multi-turn chat loops and coordinator behaviors.
*   [test_schedule_create.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/test_schedule_create.py): Validates calendar event insertion into SQLite using mock database sessions.

## Subdirectories

*   [app/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/explanation.md): The core application logic modules.
