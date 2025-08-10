# Generate a Production-Ready FastAPI Skeleton

You are an expert Python backend engineer. Generate a production-ready FastAPI project skeleton with the following requirements. Output complete, runnable code files with correct imports and paths, and include a project tree. Prefer Python 3.11+, FastAPI latest, Pydantic v2, and uvicorn.

## Project Goals

* Clean, modular structure with routers, dependencies, settings, and tests.
* Health endpoints: `/healthz` (basic), `/readyz` (readiness), `/livez` (liveness).
* Nice OpenAPI/Swagger at `/docs` and ReDoc at `/redoc`, with custom metadata.
* Robust logging, error handling, and startup/shutdown hooks.
* Minimal but meaningful tests and Dockerization.

## Deliverables

* Project tree (with files).
* All source files (full content).
* Quickstart instructions (install, run, test).
* (Optional) Dockerfile and simple CI note.

## Architecture & Conventions

* Package name: `app/`
* Entry point: `app/main.py`
* Routers under `app/api/` with versioning: `app/api/v1/`
* Settings via pydantic-settings in `app/core/config.py`
* Logging config in `app/core/logging.py` using logging with JSON-ish format.
* Lifespan events (startup/shutdown) in `main.py` or `app/core/lifespan.py`
* Dependencies in `app/core/deps.py`
* Error handlers in `app/core/errors.py` (handle HTTPException, validation errors, 500 fallback)
* Types fully annotated; docstrings for public functions.
* Use ruff/black style (even if not adding config files).
* Use `uvicorn[standard]` for local run.

## Endpoints

* `GET /` → simple service info JSON with version and uptime.
* `GET /healthz` → returns `{status:"ok"}` (always ok if app is up).
* `GET /livez` → returns `{alive:true}` (use an in-memory flag or uptime check).
* `GET /readyz` → returns readiness (simulate a dependency check with a toggle or a quick async check).
* `GET /api/v1/ping` → `{pong:true}`
* Add one sample resource router (e.g., items) with:

  * `GET /api/v1/items` (list with pagination params: `limit`, `offset`)
  * `POST /api/v1/items` (validate with Pydantic model)
  * Include response models and examples.

## OpenAPI / Docs

* App metadata: title, description, version, terms URL, contact, license.
* Tags and examples on endpoints.
* Enable both Swagger (`/docs`) and ReDoc (`/redoc`).
* Optional: API key header security scheme example for future use (not enforced yet).

## Config & Env

* Settings class with fields: `ENV`, `DEBUG`, `APP_NAME`, `APP_VERSION`, `LOG_LEVEL`, `API_V1_PREFIX`, `CORS_ORIGINS` (list), `READINESS_DELAY_MS` (int).
* Load from env using pydantic-settings; include `.env.example`.

## Middleware

* CORS (configurable), GZip, and a simple request ID (generate UUID per request using state or header).
* Access log middleware (log method, path, status, duration ms, request\_id).

## Logging

* Structured logs (one-line JSON-ish): timestamp, level, msg, request\_id (if present), path, method, status, duration.
* Make sure unhandled exceptions are logged once (no double logging).

## Errors

* Custom handlers:

  * HTTPException → JSON with detail, status\_code, request\_id.
  * Validation errors → list of errors with locations.
  * 500 fallback → hides internals in non-DEBUG.

## Testing

* pytest setup with at least:

  * Test for `/healthz`, `/livez`, `/readyz` (ready may need a small wait or mocked dep).
  * Test for `GET /api/v1/items` and `POST /api/v1/items`.
* Use `httpx.AsyncClient` with `lifespan="on"` for integration-style tests.

## Tooling & Run

* `pyproject.toml` with deps:

  * `fastapi`, `uvicorn[standard]`, `pydantic`, `pydantic-settings`, `python-multipart` (optional), `httpx`, `pytest`, `pytest-asyncio`, `anyio`.
* `Makefile` targets: `run`, `test`, `lint` (placeholder).
* `Dockerfile` (multi-stage) and `.dockerignore`.
* `README.md` with quickstart.

## Example Project Tree (adjust as needed)

arduino
Copy
Edit

```
fastapi-skeleton/
  app/
    __init__.py
    main.py
    core/
      __init__.py
      config.py
      logging.py
      deps.py
      errors.py
    api/
      __init__.py
      v1/
        __init__.py
        router.py
        items.py
  tests/
    __init__.py
    test_health.py
    test_items.py
  .env.example
  pyproject.toml
  README.md
  Dockerfile
  .dockerignore
  Makefile
```

## Implementation Notes

* Use lifespan context manager (`@asynccontextmanager`) to set start time and readiness flag.
* Store `app.state.start_time`, `app.state.ready = True/False`.
* Add middleware to inject `request_id` into `request.state.request_id`, echo header `X-Request-ID`.
* In `/readyz`, report ready only if `app.state.ready` and simulated dependency check passes (e.g., elapsed time > `READINESS_DELAY_MS`).
* Use Pydantic v2 `BaseModel` and `field_serializer` if needed. Response models in endpoints.

## Output Format

* First: the project tree.
* Then: each file’s full content using fenced code blocks with file paths in the code fence info line, e.g.:

python
Copy
Edit

```python
# app/main.py
<code here>
```

* Finish with quickstart commands to run and test.
