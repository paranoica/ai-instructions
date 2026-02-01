# RUST ENGINEERING STANDARDS

Activation: Glob(Cargo.toml, \*_/_.rs)

## 1. CORE PHILOSOPHY

- **Safety**: No `unsafe` blocks unless explicitly authorized by user.
- **Error Handling**:
  - Panic is forbidden in library code. Return `Result<T, E>`.
  - Use `?` operator for error propagation.
  - Use `thiserror` for libraries and `anyhow` for applications.

## 2. STYLE & IDIOMS

- **Formatting**: Adhere to `conventions.md` (Tabs 4, snake_case).
  - _Note_: Rust uses snake_case by default for functions/vars, so this aligns perfectly.
- **Clippy**: Code must pass `cargo clippy` without warnings.
- **Ownership**: Prefer borrowing (`&T`) over cloning (`.clone()`) to minimize allocation overhead.

## 3. ARCHITECTURE

- **Modules**: Keep `main.rs` or `lib.rs` minimal. Use a clear module hierarchy.
- **Traits**: Define behavior via Traits before implementing Structs.