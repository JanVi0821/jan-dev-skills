# Frontend Project Conventions

Read this file completely before creating or restructuring project files.

## Dependency and component reuse

1. Inspect installed dependencies and the existing design system before implementation.
2. Use a maintained third-party component or library when it already solves the requirement and is compatible with the project. Do not reimplement equivalent components or business utilities.
3. Prefer icons from the project's component or icon library.
4. When no suitable icon exists, place the custom SVG component or asset under the shared icon directory, such as `src/components/icons/`. Never inline a custom SVG in business or page code.
5. Do not add a competing library when an installed library already covers the need.

## Source structure

Create these shared directories under `src/` when the framework uses `src/`:

```text
src/
├── components/
│   ├── icons/
│   └── ui/
├── hooks/
├── layouts/
├── styles/
└── utils/
test/
```

- Put globally reused components in `src/components/`.
- Put shadcn, React Bits, Radix UI, and equivalent low-level UI primitives in `src/components/ui/`. Keep them independent of business components.
- Give every page its own folder. Put page-only components beside that page.
- Use `index` as the page entry where the router supports it. Preserve required framework filenames such as Next.js `page.tsx` or Astro `index.astro`; do not break file-based routing to enforce a naming preference.
- Use Tailwind for styling first. Add `*.module.scss` only when Tailwind cannot express the required style cleanly.
- Keep all test files and test-only scripts under the repository-root `test/` directory. Never colocate tests at the same level as business code or place them under `src/`.

Adapt aliases and framework-owned directories without changing these ownership boundaries.

## Agent instruction files

Use the instruction file recognized by the active environment:

| Environment | Project instruction file |
|---|---|
| Codex | `AGENTS.md` |
| Claude Code | `CLAUDE.md` |
| Gemini | `GEMINI.md` |
| Another agent | Use its documented project-level instruction filename; ask when uncertain |

Create the file at the project root when absent. When present, preserve unrelated instructions and merge the following rules without duplication:

- Reuse compatible third-party components and libraries instead of rebuilding them.
- Use the existing icon library first; keep custom SVG icons in the shared icon directory and out of business code.
- Maintain shared `hooks`, `components`, `utils`, `layouts`, and `styles` modules under `src/`.
- Keep UI primitives in `components/ui/` and separate from business components.
- Organize every page in its own folder with page-only components beside it; respect framework-reserved route entry filenames.
- Prefer Tailwind; use module SCSS only when Tailwind is insufficient.
- Keep tests and test-only scripts under root `test/`, never beside business code.

## Existing-project migration

1. Record the current lint, typecheck, test, and build baseline.
2. Map current files to the target ownership boundaries before moving anything.
3. Move one coherent area at a time and update imports immediately.
4. Preserve public APIs and framework route behavior unless the user requested a breaking change.
5. Run the narrowest relevant checks after each coherent move, then the full available verification suite.
