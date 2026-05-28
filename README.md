# InfraPilot

InfraPilot is an AI-native infrastructure engineering assistant that analyzes GitHub repositories and generates architecture, dependency, and infrastructure insights using the Claude Agent API.

The goal of InfraPilot is to help engineers quickly understand unfamiliar codebases by automatically analyzing repository structure, services, dependencies, and system relationships.

---

## High Level Design

<img width="916" height="760" alt="InfraPilot High Level Design" src="https://github.com/user-attachments/assets/eb6e09bf-3222-40d1-b747-93898d5ef73c" />

---

## How It Works

1. User submits a GitHub repository URL.
2. The repository URL is validated.
3. An ingestion event is published to Kafka.
4. A consumer creates an ingestion job and clones the repository.
5. Repository metadata and files are analyzed.
6. Relevant repository context is sent to the Claude Agent API.
7. Claude generates architecture and dependency insights.
8. Reports are stored and returned to the user.

---

## Features

- GitHub repository ingestion
- Event-driven processing with Kafka
- Repository structure analysis
- Dependency analysis
- AI-powered architecture insights
- Infrastructure report generation
- Job status tracking

---

## Tech Stack

### Backend
- Go
- Python

### AI
- Claude Agent API

### Messaging
- Kafka

### Database
- PostgreSQL

### Caching
- Redis

### Infrastructure
- Docker

### Frontend
- Next.js

---

## API Endpoints

### Upload Repository

```http
POST /upload
```

### Get Job Status

```http
GET /jobs/{job_id}
```

### Get Repository Reports

```http
GET /repositories/{repository_id}/reports
```

### Get Report

```http
GET /reports/{report_id}
```

---

## Database Schema

### User
- user_id
- username

### Repository
- id
- user_id
- github_url
- repo_name
- status

### IngestionJob
- job_id
- repository_id
- status
- started_at
- completed_at

### RepoFile
- id
- repository_id
- path
- language

### Report
- id
- repository_id
- report_type
- report_text

### Insight
- id
- report_id
- category
- insight_text

---

## Future Work

- Private repository support
- GitHub OAuth integration
- Interactive repository chat
- Architecture visualization
- Historical repository analysis
