# Database Models & API Schemas Package

The `backend/app/models/` directory implements the **Data Access Layer** of the application. It contains SQLAlchemy ORM definitions for tables mapping directly to SQLite, alongside Pydantic models to validate API requests and serialize JSON responses.

## Directory Structure

```text
backend/app/models/
├── database.py         # SQLAlchemy ORM database models and engine setup
├── schemas.py          # Pydantic schemas for payload validation
└── __init__.py         # Package constructor
```

## File-by-File Breakdown

### 🗄️ Database & Table Definitions
*   [database.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/models/database.py): Establishes the database engine and maps class models to database tables.
    *   **DB Setup**: Defaults to a local SQLite file named `tasks.db` in the workspace root unless overridden by environment variables.
    *   **declarative_base()**: Initializes the base class (`Base`) for ORM mappings.
    *   **get_db()**: FastAPI dependency provider yielding SQLAlchemy session instances and ensuring connections close cleanly.
    *   **SQLAlchemy Models**:
        *   `Task`: Mapped to `tasks` table. Columns: `id` (PK), `title`, `description`, `status` (defaults to 'pending'), `priority` (defaults to 'medium'), `created_at`, and `updated_at`.
        *   `ScheduleEvent`: Mapped to `schedule_events` table. Columns: `id` (PK), `title`, `description`, `start_time`, `end_time`, `location`, and `created_at`.
        *   `Note`: Mapped to `notes` table. Columns: `id` (PK), `title`, `content`, `created_at`, and `updated_at`.

### 🛡️ Payload Validation Schemas
*   [schemas.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/models/schemas.py): Pydantic validation schemas enforcing data integrity for all endpoint requests.
    *   **Task Schemas**:
        *   `TaskCreate`: Enforces `title` and maps optional string parameters.
        *   `TaskUpdate`: Allows updates to `title`, `description`, `priority`, or `status`.
        *   `TaskResponse`: Serializes DB models including `id`, `created_at`, and `updated_at` timestamps.
    *   **Schedule Event Schemas**:
        *   `ScheduleEventCreate`: Requires `title`, `start_time`, and `end_time` datetimes.
        *   `ScheduleEventResponse`: Extends inputs with primary keys (`id`).
    *   **Note Schemas**:
        *   `NoteCreate` / `NoteUpdate`: Mandates `title` and `content` configurations.
        *   `NoteResponse`: Exposes structured fields along with standard database IDs.
*   [\_\_init\_\_.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/models/__init__.py): Standard Python package initializer. Exposes ORM models and validation schemas.

## Data Lifecycle Diagram

```text
HTTP Client (React) 
       │ 
       ▼ (Validates Payload using Pydantic Schemas)
 FastAPI Router (main.py)
       │
       ▼ (Uses SessionLocal from database.py)
SQLAlchemy Session
       │
       ▼ (Performs query/write mapping to ORM classes)
SQLite Engine (tasks.db)
```
