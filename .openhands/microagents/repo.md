# OpenHands Repository Summary

## 1. Repository Purpose
OpenHands is a platform for AI-powered software development agents. These agents can perform a wide range of tasks that a human developer can, including modifying code, running commands, browsing the web, and calling APIs. The goal is to create autonomous agents that can handle complex software development projects.

## 2. General Setup
The repository includes both a Python backend and a React frontend.

- **To set up the entire repo (frontend and backend):**
  ```bash
  make build
  ```
- **To run the full application for development:**
  ```bash
  export INSTALL_DOCKER=0
  export RUNTIME=local
  make build && make run
  ```
- **Prerequisites for frontend development:**
  - A recent version of NodeJS / NPM.
  - Run `npm install` in the `frontend` directory.

## 3. Repository Structure
The repository is organized into a backend and a frontend:

- **Backend:**
  - Located in the `openhands` directory.
  - Tests are in `tests/unit/test_*.py` and can be run with `poetry run pytest`.
- **Frontend:**
  - Located in the `frontend` directory.
  - Built with React.
  - Tests are run with `npm run test`.
  - Data fetching is managed by TanStack Query, with API client methods in `frontend/src/api`.

## 4. CI Checks
The repository uses GitHub Actions for CI/CD. The main workflows are:
- `lint.yml`: Lints the codebase.
- `lint-fix.yml`: Fixes linting errors automatically.
- `py-unit-tests.yml`: Runs Python unit tests.
- `fe-unit-tests.yml`: Runs frontend unit tests.
- `integration-runner.yml`: Runs integration tests.
- `ghcr-build.yml`: Builds and pushes Docker images to GitHub Container Registry.
- `pypi-release.yml`: Publishes the Python package to PyPI.

Before pushing any changes, it is mandatory to run pre-commit hooks to ensure code quality:
- **For backend changes:** `pre-commit run --config ./dev_config/python/.pre-commit-config.yaml`
- **For frontend changes:** `cd frontend && npm run lint:fix && npm run build ; cd ..`
