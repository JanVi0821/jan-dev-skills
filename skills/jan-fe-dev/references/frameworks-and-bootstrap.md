# Framework Selection and Bootstrap

Read this file completely before scaffolding a new frontend project.

## Selection contract

Present the following options and let the user choose:

| Project need | Recommended framework | Explain to the user |
|---|---|---|
| Public pages requiring SEO | Astro | Content-first output, static generation, and minimal client JavaScript suit SEO-focused sites. |
| Local toy, prototype, or demo | React or Vue | Both are sufficient; choose according to the user's preference or surrounding ecosystem. |
| Frontend/backend integration or complex enterprise application | Next.js | Integrated routing, server capabilities, and application conventions suit larger full-stack systems. |

SEO makes Astro the recommendation, not an automatic selection. Always show the options and wait for an explicit choice. If requirements point to different rows, explain the trade-off instead of silently deciding.

## Package mapping

Use the project's selected package manager and current compatible releases. Check current official scaffold and Tailwind instructions rather than copying stale version-specific commands.

| Framework | State management | Server-state query | Schema validation |
|---|---|---|---|
| React | Zustand | `@tanstack/react-query` | Zod |
| Vue | Pinia | `@tanstack/vue-query` | Zod |
| Next.js | Zustand | `@tanstack/react-query` | Zod |
| Astro with React islands | Nano Stores with React bindings | `@tanstack/react-query` | Zod |
| Astro with Vue islands | Nano Stores with Vue bindings | `@tanstack/vue-query` | Zod |
| Astro without a UI renderer | Nano Stores | `@tanstack/query-core` | Zod |

When Astro needs interactive islands and the renderer is not known, ask whether React or Vue will power them before installing bindings.

## Mandatory bootstrap order

1. Scaffold the user-selected framework with TypeScript enabled.
2. Confirm repository boundaries, then initialize Git for a standalone project. Do not create a nested repository inside an intended parent repository without confirmation.
3. Create `.env` and `.env.example`; add `.env` to `.gitignore`. Put names and safe sample values in the example, never real secrets.
4. Install and configure Tailwind using the current official integration for the chosen framework.
5. Create global theme tokens and baseline utility/component classes in the global styles layer. Keep colors, typography, spacing, radii, and surface defaults centralized.
6. Install the mapped state-management package and establish its minimal provider/plugin wiring when the framework requires it.
7. Install the mapped TanStack Query package and establish its minimal provider/plugin wiring when required.
8. Install Zod for runtime schema validation and inferred TypeScript types.
9. Create the shared directories and root `test/` structure specified in `project-conventions.md`.
10. Generate `favicon.svg` from the first visible alphanumeric character of the project name, preserving its original letter case where practical. Use a simple readable SVG, wire it into the framework's favicon mechanism, and remove or replace the starter favicon reference.
11. Add or merge the correct agent instruction file using `project-conventions.md`.
12. Run the available lint, typecheck, test, and production-build commands.

## Favicon acceptance criteria

- The SVG contains the correct project initial as text or an outlined path.
- Foreground and background have accessible contrast.
- The document head or framework metadata points to the new asset.
- No starter favicon remains active.
