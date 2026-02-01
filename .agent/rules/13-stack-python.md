# PYTHON ENGINEERING STANDARDS

Activation: Glob(requirements.txt, pyproject.toml, Pipfile, \*_/_.py)

## 1. ARCHITECTURE & STYLE

- **Style Guide**:
  - Strict adherence to PEP 8 logic, BUT enforced via `.agent/artifacts/conventions.md` (Tabs 4, snake_case).
  - Docstrings (`"""..."""`) are allowed for public modules/functions ONLY. No inline comments.
- **Project Structure**:
  - `src/`: Application source code.
  - `tests/`: pytest modules.
  - `__init__.py`: Keep minimal.

## 2. TYPE SAFETY (STRICT)

- **Typing**: Use the `typing` module for everything.
  - Arguments and return values MUST be typed. `def my_func(a: int) -> str:`
  - No `Any`. Use `Optional`, `Union`, or `TypeVar`.
- **Validation**: Use `Pydantic` models for data validation where applicable.

## 3. ASYNC & CONCURRENCY

- **AsyncIO**: Prefer `async/await` over `threading` for I/O bound tasks.
- **Event Loop**: Be mindful of blocking calls. Offload CPU tasks to `multiprocessing`.

## 4. DEPENDENCY MANAGEMENT

- **Virtual Env**: Always assume operation inside a venv.
- **Lockfiles**: Prefer `poetry.lock` or `uv.lock` if available.