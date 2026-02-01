# WEB STACK ENGINEERING STANDARDS

Activation: Glob(package.json, tsconfig.json, **/\*.ts, **/_.tsx, \*\*/_.js)

## 1. NEXT.JS APP ROUTER ARCHITECTURE

- **Server Components by Default**: All components in `app/` are React Server Components (RSC) unless explicitly marked. Do not import client-specific logic (hooks, window object) into RSCs.
- **Client Component Boundary**: Use `'use client'` directive strictly at the top of the file. Minimize the scope of Client Components to the leaves of the render tree (buttons, inputs, interactive elements).
- **Data Fetching Strategy**:
  - Perform data fetching directly in Server Components using `async/await`.
  - Use `fetch` with `next: { revalidate: ... }` for caching policies.
  - Use `React.cache()` to deduplicate requests within a single render pass.
  - Avoid `useEffect` for data fetching; this is an anti-pattern in App Router.
- **File Structure**:
  - `page.tsx`: The UI for a route.
  - `layout.tsx`: Shared UI for a segment and its children.
  - `loading.tsx`: The Suspense fallback UI.
  - `error.tsx`: Error boundary UI.
  - `not-found.tsx`: 404 UI.
  - `route.ts`: API Route handlers (GET, POST, etc.).

## 2. REACT PERFORMANCE AND BEST PRACTICES

- **Rendering Optimization**:
  - **Defer State Reads**: Do not subscribe to context or store state if you only need it inside an event handler. Read it at the point of usage.
  - **Narrow Dependencies**: In `useEffect` or `useMemo`, depend only on the specific primitive values needed, not entire objects.
  - **Stable References**: Wrap functions passed as props to optimized children in `useCallback`.
- **State Management**:
  - **Functional Updates**: Always use `set_state(prev => ...)` when the new state depends on the old state.
  - **Derived State**: Calculate values during render (`const is_active = id === active_id`) rather than syncing them in `useEffect`.
- **Keys**: Always provide a stable, unique `key` prop for lists. Never use the array index as a key if the list can be reordered.

## 3. TYPESCRIPT STRICT TYPE SAFETY

- **No Implicit Any**: The usage of `any` is strictly prohibited. It defeats the purpose of TypeScript.
- **Unknown over Any**: If a type is truly dynamic, use `unknown` and perform runtime type narrowing (guards) before usage.
- **Generics**: Use generics for reusable components and functions. Constrain generics (`<T extends BaseEntity>`) to ensure type safety.
- **Type Assertions**: Avoid `as Type` assertions. Use type predicates (`isUser(obj)`) or Zod schema validation to prove types at runtime.
- **Utility Types**: Leverage `Pick`, `Omit`, `Partial`, `Readonly`, and `ReturnType` to avoid code duplication.

## 4. CODE STYLE ENFORCEMENT

- **Reference**: `.agent/artifacts/conventions.md`
- **Variable Naming**: ALL internal variables, functions, and file names must be `snake_case`.
  - _Correct_: `const user_data = ...`
  - _Incorrect_: `const userData = ...`
  - _Exception_: React Component names (exported) must be `PascalCase` per library requirement, but their internal logic must use `snake_case`.
- **Indentation**: Tabs (width 4).
- **Quotes**: Double quotes `"`.
- **Cleanliness**: Zero comments. Zero console logs.

## 5. RESPONSIVE & PERFORMANCE STANDARDS (MANDATORY)

- **Mobile-First Strategy**:
  - All CSS must be written for Mobile (`base`) first, then scaled up using breakpoints (`sm:`, `md:`, `lg:`).
  - **Forbidden**: Fixed widths (e.g., `width: 1200px`). Use max-width with percentages or `rem`.
  - **Touch Targets**: All interactive elements must be at least 44x44px on touch devices.
- **Performance Optimization**:
  - **Images**: ALWAYS use optimized components (`next/image`) with strict sizing/aspect ratio.
  - **Fonts**: Use self-hosted or optimized loaders (`next/font`).
  - **Core Web Vitals**: Code must optimize for LCP (Loading speed) and CLS (Visual stability - always define dimensions for media).
  - **Code Splitting**: Lazy load heavy components (`next/dynamic` or `React.lazy`).