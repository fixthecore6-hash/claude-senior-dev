# Stack-Specific Senior Idioms

Load the relevant section. Skip the rest.

---

## JavaScript / TypeScript

- Prefer `const` → `let`. Never `var`.
- Prefer `??` over `|| ` for nullish defaults
- Use optional chaining: `user?.profile?.avatar`
- Avoid `any`. Use `unknown` + type guard if truly unknown.
- `Promise.all()` for parallel async, not sequential `await`
- Named exports > default exports for tree-shaking
- Don't use `==`; always `===`
- `Array.from` or spread over `Array.prototype.slice.call`
- Error: always `instanceof Error` before accessing `.message`

## React

- One `useState` per independent value; group related state in object
- `useEffect` deps array must be exhaustive or explain why not
- Don't put derived state in `useState` — compute from existing state
- `useMemo`/`useCallback` only when profiling proves need
- Keys must be stable IDs, not array index (unless list is static + never reordered)
- Colocate state as low as possible; lift only when genuinely shared
- `useRef` for values that don't need re-render
- Event handlers: inline `() =>` for simple, extracted for complex or reused

## Next.js

- Server Components by default; add `'use client'` only when needed
- `next/image` for all images — layout shift prevention
- `next/font` for fonts — preloading + CLS
- Route handlers in `app/api/` for API routes
- `generateMetadata` for dynamic SEO
- `loading.tsx` + `Suspense` for streaming
- Don't `fetch` in client component if server component can do it

## Node.js

- Always handle Promise rejections — `.catch()` or try/catch
- Use `async/await`, not `.then().then()` chains
- `process.env` access at module load time, not inside hot functions
- Streams for large files — never `fs.readFileSync` for big data
- `EventEmitter` pattern for loose coupling, not for control flow
- `cluster` or worker threads for CPU-bound; async for I/O-bound

## Python

- `with` for file/resource handling
- List comprehensions over `map`/`filter` for readability
- f-strings over `.format()` or `%`
- `dataclasses` or `pydantic` over raw dicts for typed data
- `pathlib.Path` over `os.path`
- `logging` module over `print` in production code
- Type hints for all public function signatures
- `__all__` to define public API of a module

## SQL

- `SELECT` only the columns you need — never `SELECT *` in production
- Index on columns used in `WHERE`, `JOIN ON`, `ORDER BY`
- Use `EXPLAIN`/`EXPLAIN ANALYZE` before optimizing
- Prefer `EXISTS` over `COUNT(*)` for existence checks
- Avoid `N+1`: use `JOIN` or batch loading
- Transactions for multi-statement mutations
- Parameterized queries always — no string interpolation

## CSS / Tailwind

- Mobile-first: base styles → `md:` → `lg:`
- Use CSS custom properties for design tokens
- Tailwind: `cn()` for conditional classes
- Avoid `!important` — fix specificity instead
- `gap` over margin hacks for flex/grid spacing
- `min-height: 100dvh` not `100vh` on mobile
- Animate only `transform` + `opacity` for GPU compositing

## REST API Design

- Nouns in URLs, not verbs: `/users/123` not `/getUser?id=123`
- HTTP verbs for actions: GET read, POST create, PUT replace, PATCH update, DELETE remove
- 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauth, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable, 500 Server Error
- Return the created/updated resource body, not just a status
- Pagination: cursor-based for large/real-time datasets; offset for admin UIs

## Git

- Commit message: imperative mood — "Add login" not "Added login"
- One logical change per commit
- Feature branches; never commit directly to `main`
- `git rebase -i` to clean history before PR
- `git bisect` to find regression commits
