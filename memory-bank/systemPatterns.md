# System Patterns

## System Architecture
The project is a SvelteKit application, as indicated by `svelte.config.js`, `vite.config.ts`, and the `src/routes` directory structure. It uses TypeScript, evidenced by `tsconfig.json` and `.ts` file extensions. Drizzle ORM is used for database interactions, configured in `drizzle.config.ts` and with schema defined in `src/lib/server/db/schema.ts`.

Key architectural components:
-   **Frontend:** Svelte components located in `src/lib/components/` and `src/routes/`.
-   **Backend/Server-side Logic:** Likely within `src/lib/server/` and `+page.server.ts` or `+server.ts` files in `src/routes/`.
-   **Database:** PostgreSQL, as specified by the `dialect: 'postgresql'` in `drizzle.config.ts`. The connection URL is managed via the `DATABASE_URL` environment variable.
-   **Authentication:** Lucia Auth seems to be implemented, suggested by `src/lib/server/auth.ts` and route paths like `src/routes/demo/lucia/`.
-   **Styling:** Tailwind CSS is used, configured in `tailwind.config.ts` and `postcss.config.js`, with base styles in `src/app.css`.
-   **Build/Development:** Vite is the build tool (`vite.config.ts`), and Bun is the package manager/runtime (`bun.lockb`).
-   **Linting/Formatting:** ESLint (`eslint.config.js`) and Prettier (`.prettierrc`, `.prettierignore`) are used for code quality.

## Key Technical Decisions
1.  **Environment Variable Management:** The `DATABASE_URL` is sourced from `process.env`. The initial error indicated a problem with Node.js type definitions for `process`, which was addressed by installing `@types/node`. A check `if (!process.env.DATABASE_URL) throw new Error('DATABASE_URL is not set');` exists in `drizzle.config.ts` to ensure this variable is present.
2.  **ORM Choice:** Drizzle ORM is chosen for database abstraction.
3.  **Framework Choice:** SvelteKit provides the full-stack framework.
4.  **Memory Bank System:** A deliberate decision to implement a structured markdown-based Memory Bank to ensure project context is maintained for the AI engineer (Cline). This includes core files like `projectbrief.md`, `productContext.md`, `systemPatterns.md`, `techContext.md`, `activeContext.md`, and `progress.md`.
5.  **Project Intelligence File:** `.clinerules` will be used to store learned patterns and preferences.

## Design Patterns in Use
-   **Environment Configuration:** Using `.env` files (implied by `process.env.DATABASE_URL` and `.env.example`) for managing environment-specific settings.
-   **MVC/MVVM-like Structure (SvelteKit):** Routes define pages/endpoints, Svelte components handle the view, and server-side files (`+page.server.ts`, `+server.ts`) handle logic and data.
-   **Schema-first Database Design:** `src/lib/server/db/schema.ts` defines the database structure for Drizzle.
-   **Modular Components:** UI elements are likely organized into reusable Svelte components (e.g., `src/lib/components/ui/`).

## Component Relationships
-   `drizzle.config.ts` depends on `process.env.DATABASE_URL` for its `dbCredentials`.
-   The application's database operations (via Drizzle ORM, initialized in `src/lib/server/db/index.ts`) rely on the schema defined in `src/lib/server/db/schema.ts`.
-   SvelteKit routes in `src/routes/` will render Svelte components and may interact with server-side logic that uses the database via `src/lib/server/db/index.ts` and authentication via `src/lib/server/auth.ts`.
