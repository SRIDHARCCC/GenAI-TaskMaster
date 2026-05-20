# React Single Page Frontend Application

The `frontend/` directory contains the web interface of the GenAI-TaskMaster application. Built with **Vanilla React** (loaded via scripts to avoid complex compilation steps), it provides a responsive, dark-themed dashboard that connects directly to the FastAPI server.

## Directory Structure

```text
frontend/
├── index.html            # Application skeleton and styling
├── api.js                # Network request utility wrapper
├── app.js                # Root application and primary tab views
├── project_planner.js    # AI-powered project timeline and Kanban
├── workflow_new.js       # Trigger-Condition-Action builder and execution logs
├── data_analysis.js      # Charting dashboard and CSV processor
└── package.json          # Node dependencies and execution scripts
```

## File-by-File Breakdown

### 🎨 Skeleton & Layout Styling
*   [index.html](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/index.html): The main entry document. Key responsibilities:
    *   **External Assets**: Loads Tailwind/custom styling libraries, Google Fonts (Outfit, JetBrains Mono), Chart.js (for analytics), Lucide Icons, and React.
    *   **Premium CSS Stylesheet**: Contains variable tokens for dark/glass aesthetics, custom animations (e.g., `slideUp`, `pulse-glow`), scrollbars, and form fields.
    *   **Mount Point**: Standard `<div id="root">` element.

### 🌐 Network Communication
*   [api.js](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/api.js): Defines the `API` class wrapper around standard browser `fetch` calls.
    *   **Base URL**: Configured to query `localhost:8080/api` or cloud services.
    *   **Methods**: Exposes clean endpoints for `Tasks`, `ScheduleEvents`, `Notes`, `Workflows`, `DashboardStats`, and `ToolStatus` queries.
    *   **Instance**: Instantiates a global `API_CLIENT` shared by all React components.

### 📂 React Components
*   [app.js](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/app.js): Orchestrates navigation sidebar, header states, and core tabs:
    *   **Dashboard Component**: Renders quick metrics, daily productivity completion wheels, a search system, and a built-in Pomodoro focus timer.
    *   **Tasks Component**: Handles task CRUD modifications, categories (e.g., Personal, Health, Work), priority indicators, and task-specific session timers.
    *   **Schedule Component**: Renders a calendar view of scheduled events.
    *   **Notes Component**: Displays note-taking cards, content previews, and keyword filters.
    *   **Root app component**: Exposes the AI Agent status sidebar, connection alerts, and WebSocket duplex audio stream controls for the voice assistant.
*   [project_planner.js](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/project_planner.js):
    *   Generates multi-phase project structures using AI prompts.
    *   Displays schedules across three views: a **Kanban Board** (Todo/InProgress/Done drag states), a Gantt-like **Timeline Chart**, and a checklist **List View**.
*   [workflow_new.js](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/workflow_new.js):
    *   Provides a visual Trigger-Condition-Action automation builder.
    *   Exposes custom nodes and dropdown triggers.
    *   Tracks automation execution history logs.
*   [data_analysis.js](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/data_analysis.js):
    *   Utilizes Chart.js to map task categories, weekly line activity, and status distributions.
    *   Includes a CSV parser utility to upload and preview data arrays.
    *   Generates printable text summary reports.

## Local Development Execution

To start the local development server hosting the frontend assets on port `3000`:
```bash
npm run dev
# under the hood runs: python -m http.server 3000
```
