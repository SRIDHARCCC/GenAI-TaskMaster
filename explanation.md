# GenAI-TaskMaster Root Directory

Welcome to **GenAI-TaskMaster**, a full-stack personal assistant application powered by a Multi-Agent AI system using Google Gemini. The project combines a React-based frontend web application and a FastAPI backend server running a SQLite database.

This document serves as an entry point for developers to understand the project structure, configuration files, and automation scripts.

## Directory Structure

```text
GenAI-TaskMaster/
├── backend/            # FastAPI Backend Application (Python)
├── frontend/           # React SPA Frontend Application (Javascript/HTML)
├── .env.example        # Environment variable templates
├── .gcloudignore       # Files to ignore during Google Cloud deployments
├── .gitignore          # Files to ignore in Git version control
├── Procfile            # Process file for Heroku/Cloud deployment
├── app.yaml            # Google App Engine deployment configuration
├── docker-compose.yml  # Docker multi-container runner
├── cloudbuild.yaml     # CI/CD instructions for Google Cloud Build
└── ...                 # Developer guides and helper scripts
```

## Key Files in this Directory

### 📖 Developer & Setup Guides
*   [README.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/README.md): General project landing page. Highlights key features, prerequisites, quick setup commands, and basic screenshots.
*   [START_HERE.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/START_HERE.md): Deep developer onboarding guide with a detailed manifest, code layout description, and step-by-step development roadmap.
*   [ARCHITECTURE.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/ARCHITECTURE.md): Technical breakdown of the multi-agent orchestration, detailing the communication flow between the Coordinator and specialty agents.
*   [AI_INTEGRATION_GUIDE.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/AI_INTEGRATION_GUIDE.md): Explains how Gemini is integrated, how context is managed, and how agents call tools.
*   [AI_ASSISTANT_VOICE_CHAT.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/AI_ASSISTANT_VOICE_CHAT.md) & [VOICE_CHAT_QUICKSTART.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/VOICE_CHAT_QUICKSTART.md): Documentation on voice interaction, describing how the client-side Web Speech API links with the Gemini audio APIs.
*   [GOOGLE_API_SETUP.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/GOOGLE_API_SETUP.md): Instructions for acquiring Google API keys, setting up project billing, and configuring access.
*   [GOOGLE_CLOUD_DEPLOYMENT.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/GOOGLE_CLOUD_DEPLOYMENT.md), [DEPLOYMENT_GUIDE.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/DEPLOYMENT_GUIDE.md), & [DEPLOY_QUICKSTART.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/DEPLOY_QUICKSTART.md): Comprehensive instructions on setting up deployments to Google App Engine and Cloud Run.
*   [TESTING.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/TESTING.md): Overview of unit testing strategies for agents, schemas, and API end-to-end flows.
*   [CLEANUP_GUIDE.md](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/CLEANUP_GUIDE.md): Guidelines for destroying cloud services to avoid accidental cloud costs.

### ⚙️ Deployment & Container Configurations
*   [docker-compose.yml](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/docker-compose.yml): Configures containerized environments for both the backend and frontend to run in synchronization locally.
*   [app.yaml](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/app.yaml): Configures App Engine runtime constraints, environment mappings, and static handlers.
*   [Procfile](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/Procfile): Instructs process runners to execute `uvicorn backend.main:app` upon deployment.
*   [cloudbuild.yaml](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/cloudbuild.yaml) & [cloudbuild-fix.yaml](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/cloudbuild-fix.yaml): Google Cloud Build triggers to automate building Docker containers and rolling out service updates.

### 🛠️ Script Automation Utilities
*   [start-dev.sh](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/start-dev.sh) & [start-dev.bat](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/start-dev.bat): Unix shell and Windows batch launchers that start the FastAPI server and python http.server frontend concurrently on ports 8080 and 3000.
*   [deploy-gcp.sh](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/deploy-gcp.sh) & [deploy-gcp.ps1](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/deploy-gcp.ps1): Automates building Docker images, uploading them to Artifact Registry, and deploying backend containers to Cloud Run.
*   [cleanup.sh](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/cleanup.sh) & [cleanup.ps1](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/cleanup.ps1): Deletes temporary cache directories, local SQLite databases (`tasks.db`), and python build folders (`__pycache__`).
*   [fix-frontend-deployment.ps1](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/fix-frontend-deployment.ps1): Automatically updates backend endpoint target URLs inside the frontend JS files before deployment to match Cloud Run addresses.
*   [check-backend-logs.ps1](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/check-backend-logs.ps1): Streamlines pulling Cloud Run execution log outputs via gcloud CLI.
*   [rebuild-backend.ps1](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/rebuild-backend.ps1): Helper scripts to rebuild local docker images for backend testing.

## Subdirectories Overview

*   [backend/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/backend/explanation.md): FastAPI service handling routing, AI Agent coordination, SQLite databases, and tool orchestration.
*   [frontend/](file:///c:/genai_apac/study_projects/GenAI-TaskMaster/frontend/explanation.md): HTML/CSS/JS frontend application built as a React single page app. It provides a visual scheduler, dashboard, task list, notes manager, AI chat, and workflow builder.
