# domiatek-infra

Workflows CI/CD reutilizables para todos los repos de Domiatek.

## Workflows disponibles

| Workflow | Stack | Repos que lo usan |
|----------|-------|-------------------|
| `flutter-ci.yml` | Flutter 3.24 / Java 17 | RalloApp, proges-app |
| `node-ci.yml` | Node.js 20 | erp-domiatek, app-energia |
| `nextjs-ci.yml` | Next.js / Node.js 20 | web-domiatek |
| `pr-checks.yml` | Quality gate | Todos los repos |

## Cómo usar en un repo

```yaml
# .github/workflows/ci.yml
name: CI
on:
  pull_request:
    branches: [develop, main]
jobs:
  build:
    uses: Domiatek/domiatek-infra/.github/workflows/flutter-ci.yml@main
    secrets: inherit
```

## Secrets requeridos (org-level)

| Secret | Descripción |
|--------|-------------|
| `PROJECT_PAT` | GitHub PAT con permisos de org |
| `ANTHROPIC_API_KEY` | Clave Anthropic para agentes |
| `GOOGLE_SERVICES_JSON` | Firebase config para apps Flutter |
