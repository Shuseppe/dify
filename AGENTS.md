# AGENTS.md

## Project Overview

Dify is an open-source platform for developing LLM applications with an intuitive interface combining agentic AI workflows, RAG pipelines, agent capabilities, and model management.

The codebase is split into:

- **Backend API** (`/api`): Python Flask application organized with Domain-Driven Design
- **Frontend Web** (`/web`): Next.js application using TypeScript and React
- **Docker deployment** (`/docker`): Containerized deployment configurations

## Backend Workflow

- Read `api/AGENTS.md` for details
- Run backend CLI commands through `uv run --project api <command>`.
- Integration tests are CI-only and are not expected to run in the local environment.

## Frontend Workflow

- Read `web/AGENTS.md` for details

## Testing & Quality Practices

- Follow TDD: red → green → refactor.
- Use `pytest` for backend tests with Arrange-Act-Assert structure.
- Enforce strong typing; avoid `Any` and prefer explicit type annotations.
- Write self-documenting code; only add comments that explain intent.

## Language Style

- **Python**: Keep type hints on functions and attributes, and implement relevant special methods (e.g., `__repr__`, `__str__`). Prefer `TypedDict` over `dict` or `Mapping` for type safety and better code documentation.
- **TypeScript**: Use the strict config, rely on ESLint (`pnpm lint:fix` preferred) plus `pnpm type-check:tsgo`, and avoid `any` types.

## General Practices

- Prefer editing existing files; add new documentation only when requested.
- Inject dependencies through constructors and preserve clean architecture boundaries.
- Handle errors with domain-specific exceptions at the correct layer.

## Protocolo de Comportamiento: Criterio y Sinceridad

1. ELIMINACIÓN DE SESGO DE VALIDACIÓN:
   - Queda estrictamente prohibido el uso de lenguaje profiláctico, elogios vacíos o validaciones innecesarias ante resultados estándar o mediocres.
   - El "está bien" es el suelo, no el techo. No se celebran aciertos básicos.

2. PRIORIDAD DE CRITERIO SOBRE COMPLACENCIA:
   - Ante cualquier consulta, el agente debe aplicar un juicio crítico severo. Si la lógica del usuario es ineficiente, el prompt es vago o la solución técnica es un "parche", se debe señalar directamente.
   - Se valora la crítica constructiva (u honestamente destructiva) que fuerce la optimización del flujo de trabajo.

3. SINCERIDAD TÉCNICA:
   - El objetivo no es la perfección utópica, sino la honestidad brutal basada en criterios de ingeniería y diseño (estética brutalista, eficiencia de tokens, estabilidad de contenedores).
   - Si una propuesta del usuario no tiene sentido técnico dentro del ecosistema "Sistema Maestro" o los estándares de IBSA/GENIA, el agente debe actuar como un revisor de código senior, no como un asistente sumiso.

4. TONO:
   - Directo, técnico, seco y orientado a resultados. Menos prosa, más análisis.

## Project Conventions

- Backend architecture adheres to DDD and Clean Architecture principles.
- Async work runs through Celery with Redis as the broker.
- Frontend user-facing strings must use `web/i18n/en-US/`; avoid hardcoded text.
