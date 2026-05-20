# AI Agent Tools Package

The `backend/app/tools/` directory implements the interfaces that allow Gemini AI agents to query and modify the application database. By exposing structured Python methods, the backend translates agent actions into standard SQL operations.

## Directory Structure

```text
backend/app/tools/
├── mcp_tools.py        # Database manipulation tools and ToolManager
└── __init__.py         # Package constructor
```

## File-by-File Breakdown

### 🛠️ Model Context Protocol (MCP) Tools
*   [mcp_tools.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/tools/mcp_tools.py): Implements database access interfaces designed to be invoked by the AI agents.
    *   **CalendarTool**:
        *   `list_events(days_ahead)`: Returns a list of upcoming calendar events (start/end times, titles, locations) in ISO formats.
        *   `create_event(title, start_time, end_time, location)`: Commits a new `ScheduleEvent` row to the database.
        *   `get_free_slots()`: Simulates slot availability lookup (returns static slots: `09:00-10:00`, `14:00-15:00`, `16:00-17:00`).
    *   **TaskManagerTool**:
        *   `list_tasks(status)`: Fetches tasks from SQLite, optionally filtering by `status` (e.g. pending/completed).
        *   `create_task(title, description, priority)`: Inserts a new task with a default `pending` status.
        *   `update_task_status(task_id, status)`: Sets the status column for a given task ID.
        *   `get_pending_tasks()`: Quick lookup helper returning all pending tasks.
    *   **NotesTool**:
        *   `list_notes()`: Returns all stored notes, truncating content preview to 100 characters.
        *   `create_note(title, content)`: Inserts a new note title and body.
        *   `search_notes(query)`: Performs SQL `LIKE` wildcard searches over title and content columns.
    *   **ToolManager**:
        *   Aggregates the individual tools (`CalendarTool`, `TaskManagerTool`, `NotesTool`) under a single constructor.
        *   Exposes `get_available_tools()`: A registry mapping tool names (e.g., `list_tasks`, `create_calendar_event`) to class methods, used by routers to detail capabilities.

*   [\_\_init\_\_.py](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/app/tools/__init__.py): Package constructor exposing `ToolManager` and its child tools.

## Tool Registry Flow

```text
               Coordinator/Specialist Agent
                            │
                            ▼ (Requests Tool Execution with JSON Arguments)
                     FastAPI Server
                            │
                            ▼ (Resolves tool via ToolManager in mcp_tools.py)
                    Specialist Class 
             (TaskManager/Calendar/NotesTool)
                            │
                            ▼ (Executes SQLAlchemy Commit/Fetch)
                      SQLite Database
```
