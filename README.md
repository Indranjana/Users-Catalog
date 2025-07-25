# Hyland Developers Portal

Welcome to the Hyland Developers Portal! This guide will help you set up your local development environment and get the portal running on your machine.

## Local Development Setup

This section covers installing required tools, configuring your environment, and running the portal locally.

### Prerequisites

- **Node.js**: v16.x LTS or higher
- **Yarn**: v1.22.x
- **Git**: v2.30.x or higher
- **Docker & Docker Compose**: v20.x

### Environment Variables

Copy the `.env.yarn.example` file at the project root to create your local `.env`:

```sh
cp .env.yarn.example .env
```

Required variables:

| Variable | Description |
|----------|-------------|
| `POSTGRES_HOST` | PostgreSQL database host |
| `POSTGRES_PORT` | PostgreSQL database port |
| `POSTGRES_USER` | PostgreSQL database username |
| `POSTGRES_PASSWORD` | PostgreSQL database password |
| `JIRA_TOKEN` | JIRA API token for authentication |
| `JIRA_USERNAME` | JIRA username for API authentication |
| `JIRA_API_TOKEN` | JIRA API token (alternative to JIRA_TOKEN) |
| `CONFLUENCE_USERNAME` | Confluence username for API authentication |
| `CONFLUENECE_API_TOKEN` | Confluence API token for authentication |
| `GITHUB_TOKEN` | GitHub token for Actions workflow integration |
| `GITHUB_PUSH_TOKEN` | GitHub token for push operations in catalog automation |
| `BACKSTAGE_API_URL` | Base URL for Backstage API |
| `SONAR_TOKEN` | SonarQube authentication token |
| `RANCHER_API_TOKEN` | Rancher API token for Kubernetes integration |
| `RANCHER_BASE` | Base URL for Rancher API |

### Running the Portal Locally

```sh
# 1. Install dependencies
yarn install

# 2. Start backend services
yarn workspace backend start

# 3. Start the frontend app
yarn workspace app start
```

After both services are running, open http://localhost:3000 in your browser.

Logs will stream to the console; watch for `Server listening on port 7000` and `Frontend running on port 3000`.

## Folder Structure Explained

```
/ (repo root)
├── .env.example          # Template for environment variables
├── packages/
│   ├── app/              # Frontend application (React + Backstage)
│   ├── backend/          # Backend server and plugin registry
│   └── plugins/          # Custom plugins (e.g., automate-catalog-creation)
├── scripts/              # Utility scripts (setup, migrations)
├── docs/                 # Markdown docs and design assets
└── docker-compose.yml    # Docker configuration for local services
```

- **packages/app**: Contains the React-based UI. Edit or extend components here.
- **packages/backend**: Hosts REST API, plugin loading, and database migrations.
- **packages/plugins**: One folder per custom plugin; follow naming conventions (plugin-name-plugin).

By following these steps, you will have a fully functional local instance of the Hyland Developers Portal for development and testing.
