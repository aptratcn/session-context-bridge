# Context Templates

Ready-to-use context file templates for different project types. Copy the template that matches your project, fill in the brackets, and drop it in your project root or `.ai/` directory.

---

## Web Application

```markdown
# Project Context

## Overview
- **Name:** [Project Name]
- **Type:** Web Application
- **Description:** [One-sentence description of what this app does]
- **Status:** [Active development / Maintenance / Production]

## Tech Stack
- **Frontend:** [React 18 / Vue 3 / Svelte / etc.]
- **Backend:** [Node.js / Python Flask / Go / etc.]
- **Database:** [PostgreSQL / MongoDB / SQLite / etc.]
- **Auth:** [JWT / OAuth2 / Session-based / etc.]
- **Hosting:** [Vercel / AWS / Self-hosted / etc.]

## Architecture
- **Pattern:** [REST API / GraphQL / SSR / etc.]
- **State management:** [Redux / Pinia / Zustand / etc.]
- **Key directories:**
  - `src/components/` — UI components
  - `src/pages/` — Route-level views
  - `src/api/` — API client functions
  - `src/utils/` — Shared utilities
  - `src/types/` — TypeScript type definitions

## API Endpoints
| Method | Path | Description |
|--------|------|-------------|
| GET | /api/items | List all items |
| POST | /api/items | Create an item |
| GET | /api/items/:id | Get single item |

## Environment Variables
- `DATABASE_URL` — Connection string for the database
- `JWT_SECRET` — Secret for signing tokens
- `NODE_ENV` — development | production | test

## Development
- **Install:** `npm install`
- **Dev server:** `npm run dev`
- **Build:** `npm run build`
- **Test:** `npm test`
- **Lint:** `npm run lint`

## Conventions
- [Coding style, naming conventions, commit message format]
- [Any project-specific rules]

## Known Issues
- [Current bugs or technical debt items]
```

---

## CLI Tool

```markdown
# Project Context

## Overview
- **Name:** [Tool Name]
- **Type:** CLI Tool
- **Description:** [One-sentence description]
- **Status:** [Active development / Published / Experimental]

## Tech Stack
- **Language:** [Rust / Go / Python / Node.js / etc.]
- **CLI framework:** [Clap / Cobra / Click / Commander / etc.]
- **Distribution:** [npm / cargo / brew / pip / etc.]

## Commands
| Command | Description | Example |
|---------|-------------|---------|
| `init` | Initialize a new project | `tool init --name myapp` |
| `build` | Build the project | `tool build --release` |
| `deploy` | Deploy to target | `tool deploy --env staging` |

## Key Directories
- `src/` — Source code
- `src/commands/` — Command implementations
- `src/config/` — Configuration handling
- `src/utils/` — Shared utilities
- `tests/` — Integration tests

## Configuration
- Config file: `~/.toolrc` or `.tool.json` in project root
- Environment variables: `TOOL_DEBUG=1` for verbose output

## Development
- **Build:** `cargo build` / `go build` / `npm run build`
- **Test:** `cargo test` / `go test ./...` / `npm test`
- **Install locally:** `cargo install --path .` / `go install`

## Release Process
1. Update version in `Cargo.toml` / `package.json`
2. Update `CHANGELOG.md`
3. Tag: `git tag v1.2.3`
4. Push tag: `git push --tags`
5. CI publishes to [registry]

## Conventions
- [Command naming style]
- [Error message format]
- [Exit code conventions]
```

---

## API / Microservice

```markdown
# Project Context

## Overview
- **Name:** [Service Name]
- **Type:** API / Microservice
- **Description:** [One-sentence description of what this service provides]
- **Status:** [Active development / Production / Deprecated]

## Tech Stack
- **Language:** [Python / Go / TypeScript / etc.]
- **Framework:** [FastAPI / Gin / Express / etc.]
- **Database:** [PostgreSQL / MySQL / DynamoDB / etc.]
- **Cache:** [Redis / Memcached / None]
- **Message Queue:** [RabbitMQ / SQS / Kafka / None]
- **Deployment:** [Docker + K8s / ECS / Lambda / etc.]

## API Contract
- **Base URL:** `https://api.example.com/v1`
- **Auth:** Bearer token in `Authorization` header
- **Format:** JSON

## Endpoints
| Method | Path | Description | Auth |
|--------|------|-------------|------|
| POST | /auth/login | Get access token | No |
| GET | /users | List users | Yes |
| GET | /users/:id | Get user | Yes |
| PUT | /users/:id | Update user | Yes |

## Data Models
```
User {
  id: UUID
  email: string (unique)
  name: string
  role: "admin" | "member"
  created_at: timestamp
}
```

## Dependencies
| Service | Purpose | Endpoint |
|---------|---------|----------|
| Auth Service | Token validation | auth.internal:8080 |
| Notification Service | Send alerts | notify.internal:8081 |

## Environment Variables
| Variable | Description | Required |
|----------|-------------|----------|
| DATABASE_URL | DB connection string | Yes |
| REDIS_URL | Cache connection | No |
| JWT_PUBLIC_KEY | Key for token validation | Yes |
| PORT | Server port (default: 3000) | No |

## Development
- **Run:** `docker-compose up` or `npm run dev`
- **Test:** `npm test` / `pytest`
- **Migrate:** `npm run db:migrate`
- **API docs:** `http://localhost:3000/docs` (Swagger/OpenAPI)

## Health Checks
- `GET /health` — Returns `{ "status": "ok" }`
- `GET /ready` — Checks DB connection + dependencies
```

---

## Library / Package

```markdown
# Project Context

## Overview
- **Name:** [Package Name]
- **Type:** Library / Package
- **Description:** [One-sentence description of what this library does]
- **Status:** [Active / Stable / Maintenance]

## Tech Stack
- **Language:** [TypeScript / Python / Rust / etc.]
- **Runtime:** [Node.js 18+ / Python 3.10+ / etc.]
- **Build tool:** [tsup / setuptools / cargo / etc.]

## Public API
```typescript
// Core exports
export function createClient(config: ClientConfig): Client
export function processData(input: Input): Output
export class CustomError extends Error
```

## Key Directories
- `src/` — Source code
- `src/core/` — Core logic
- `src/types/` — Type definitions
- `src/utils/` — Internal utilities
- `tests/` — Test files
- `examples/` — Usage examples

## Design Principles
- [Immutability by default / zero dependencies / etc.]
- [Error handling strategy: exceptions vs Result types]
- [Backwards compatibility policy]

## Development
- **Install:** `npm install`
- **Build:** `npm run build`
- **Test:** `npm test`
- **Lint:** `npm run lint`
- **Type check:** `npm run typecheck`

## Release
- **Version:** Semantic versioning (semver)
- **Changelog:** `CHANGELOG.md`
- **Publish:** `npm publish` / `cargo publish`

## Compatibility
- **Node.js:** >=18.0.0
- **Browser:** Yes / No
- **Bundler:** ESM + CJS dual output

## Conventions
- [Naming: camelCase for functions, PascalCase for types]
- [Export style: named exports, no default exports]
- [Test style: describe/it with AAA pattern]
```

---

## Data Pipeline / ETL

```markdown
# Project Context

## Overview
- **Name:** [Pipeline Name]
- **Type:** Data Pipeline / ETL
- **Description:** [One-sentence description of data flow]
- **Status:** [Active / Production / Experimental]

## Tech Stack
- **Orchestration:** [Airflow / Prefect / Dagster / Cron / etc.]
- **Processing:** [Spark / dbt / Python / etc.]
- **Storage:** [S3 / BigQuery / Snowflake / etc.]
- **Language:** [Python / SQL / Scala / etc.]

## Pipeline Stages
```
[Source] → Extract → Transform → Validate → Load → [Destination]
   │           │          │          │         │
   │           │          │          │         └─ Write to [target]
   │           │          │          └─ Schema + quality checks
   │           │          └─ Clean, normalize, enrich
   │           └─ Read from [source]
   └─ [API / Database / Files / Stream]
```

## Schedules
| Pipeline | Schedule | SLA | Alert |
|----------|----------|-----|-------|
| daily_sync | 06:00 UTC | 1 hour | Slack #data-alerts |
| hourly_agg | Every hour | 15 min | PagerDuty |
| weekly_report | Monday 09:00 | 4 hours | Email |

## Data Quality Checks
- Row count within expected range (±10%)
- No null values in required columns
- Referential integrity with upstream tables
- Freshness: data timestamp < 24h old

## Key Directories
- `dags/` — Airflow DAGs / pipeline definitions
- `transforms/` — SQL / dbt models
- `scripts/` — Utility scripts
- `tests/` — Data quality tests

## Environment Variables
| Variable | Description |
|----------|-------------|
| SOURCE_DB_URL | Upstream database connection |
| WAREHOUSE_URL | Data warehouse connection |
| S3_BUCKET | Raw data bucket |
| AIRFLOW_HOME | Airflow config directory |

## Monitoring
- **Dashboard:** [Grafana / Metabase URL]
- **Alerts:** [Slack channel / PagerDuty service]
- **Logs:** [CloudWatch / ELK / etc.]

## Common Issues
- [Source API rate limiting → add backoff retry]
- [Schema drift → add schema validation step]
- [Late arriving data → configurable lookback window]
```

---

## Monorepo

```markdown
# Project Context

## Overview
- **Name:** [Monorepo Name]
- **Type:** Monorepo
- **Description:** [What products/services live here]
- **Status:** [Active development]

## Workspace Structure
```
/
├── apps/
│   ├── web/          — [Frontend app description]
│   ├── api/          — [Backend service description]
│   └── worker/       — [Background job description]
├── packages/
│   ├── ui/           — Shared UI components
│   ├── config/       — Shared configuration
│   ├── types/        — Shared TypeScript types
│   └── utils/        — Shared utilities
├── infra/            — Infrastructure as code
└── docs/             — Documentation
```

## Build Tool
- **Tool:** [Turborepo / Nx / Lerna / etc.]
- **Package manager:** [pnpm / yarn / npm]

## Key Commands
| Command | Description |
|---------|-------------|
| `pnpm install` | Install all dependencies |
| `pnpm build` | Build all packages/apps |
| `pnpm test` | Run all tests |
| `pnpm lint` | Lint all packages |
| `pnpm --filter web dev` | Run dev server for web app only |

## Dependency Graph
```
apps/web → packages/ui, packages/config, packages/types
apps/api → packages/types, packages/utils
apps/worker → packages/types, packages/utils
packages/ui → packages/types
```

## Deployment
| App | Platform | Trigger |
|-----|----------|---------|
| web | Vercel | Push to main |
| api | ECS | Tag release |
| worker | ECS | Tag release |

## Conventions
- [Shared ESLint config in packages/config]
- [All packages use TypeScript strict mode]
- [Changesets for versioning]
```

---

## Usage Tips

1. **Copy the template** that best matches your project type
2. **Fill in all `[brackets]`** with your actual values
3. **Delete sections** that don't apply to your project
4. **Add custom sections** for project-specific needs
5. **Keep it updated** — review monthly, update when architecture changes

### Where to Place It
- Root of project: `PROJECT_CONTEXT.md` or `AI_CONTEXT.md`
- AI-specific directory: `.ai/context.md`
- Documentation: `docs/context.md`

### Why This Matters
When an AI assistant has context about your project, it can:
- Generate code that matches your conventions
- Suggest appropriate solutions for your tech stack
- Avoid recommending patterns that conflict with your architecture
- Understand your constraints and requirements without repeated explanations
