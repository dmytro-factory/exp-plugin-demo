---
name: project-context
description: Provides architecture and coding conventions for the Orion project. Use when someone asks about how to build features, structure code, or pick tools for Orion.
---

# Project Orion

Orion is an internal REST API service built with Python 3.12, FastAPI, and SQLAlchemy 2.0. It uses Pydantic v2 for request/response models and Alembic for database migrations. The project follows a layered architecture: routers call services, services call repositories, repositories talk to the database. Never access the database directly from a router. All async work uses `asyncio` — do not use threading or synchronous database calls. Tests use pytest with pytest-asyncio and live in a `tests/` directory mirroring the source structure. When answering questions about how to build something for Orion, default to async endpoints, Pydantic models for validation, and dependency injection via FastAPI's `Depends`.
