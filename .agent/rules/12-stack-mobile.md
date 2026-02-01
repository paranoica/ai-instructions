# MOBILE AND SYSTEMS ENGINEERING STANDARDS

Activation: Glob(pubspec.yaml, go.mod, **/\*.dart, **/\*.go)

## 1. FLUTTER (DART) STANDARDS

- **Widget Architecture**:
  - Break down large build methods. If a build method exceeds 30 lines, extract parts into private helper methods or separate StatelessWidgets.
  - Prefer `StatelessWidget` over `StatefulWidget` whenever possible. Use state management solutions for complex state.
  - Use `const` constructors everywhere possible to optimize rebuilds.
- **State Management**:
  - Adhere to the chosen pattern in `tech_stack.md` (BLoC, Riverpod, Provider).
  - Keep UI logic separate from Business logic. Widgets should be dumb; logic should live in Cubits/Controllers.
- **Asynchronous Programming**:
  - Use `FutureBuilder` or `StreamBuilder` for UI that depends on async data.
  - Handle all connection states (loading, active, error, done).
- **Style**:
  - Identifiers: `lowerCamelCase` for variables (override convention if needed, but usually `snake_case` for file names).
  - Files: `snake_case` strictly.

## 2. GO (GOLANG) STANDARDS

- **Code Organization**:
  - Follow the Standard Go Project Layout (`cmd/`, `internal/`, `pkg/`).
  - Keep `main` packages minimal. Delegate logic to internal packages.
- **Error Handling Philosophy**:
  - Treat errors as values. Always check the returned error immediately.
  - Use `fmt.Errorf("context: %w", err)` to wrap errors with context.
  - Never use `panic` in library code or HTTP handlers; return errors instead.
- **Concurrency Patterns**:
  - Use `context.Context` for cancellation and timeout propagation in all long-running functions.
  - Avoid sharing memory with Mutexes if Channels can solve the problem.
  - Always handle goroutine lifecycle (use `errgroup` or `WaitGroup` to ensure no goroutine leaks).
- **Style**:
  - Strict `snake_case` for file names.
  - Variable names should be short but descriptive (`ctx`, `mu`, `err`).
  - Run `gofmt` or `goimports` on every save.