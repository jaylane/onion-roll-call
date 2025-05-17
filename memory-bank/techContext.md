# Tech Context

## Technologies Used
-   **Programming Language:** TypeScript (see `tsconfig.json`, `*.ts` files)
-   **Framework:** SvelteKit (see `svelte.config.js`, `vite.config.ts`, `src/routes/`)
-   **Database ORM:** Drizzle ORM (see `drizzle.config.ts`, `src/lib/server/db/schema.ts`)
-   **Database:** PostgreSQL (specified in `drizzle.config.ts` as `dialect: 'postgresql'`)
-   **Authentication:** Lucia Auth (inferred from `src/lib/server/auth.ts` and demo routes)
-   **Styling:** Tailwind CSS (see `tailwind.config.ts`, `postcss.config.js`, `src/app.css`)
-   **Build Tool:** Vite (see `vite.config.ts`)
-   **Package Manager/Runtime:** Bun (see `bun.lockb`)
-   **Linting:** ESLint (see `eslint.config.js`)
-   **Formatting:** Prettier (see `.prettierrc`, `.prettierignore`)
-   **Node.js Types:** `@types/node` (installed to resolve `process` related errors)
-   **UI Components (potential):** `components.json` might indicate usage of a component library like Shadcn UI or similar, given the `src/lib/components/ui/` directory.

## Development Setup
-   **Environment Variables:** A `.env` file is required, primarily for `DATABASE_URL`. An example is provided in `.env.example`.
-   **Installation:** Dependencies are managed by Bun. `bun install` would be the command to install them.
-   **Running Development Server:** Typically `bun run dev` for SvelteKit/Vite projects.
-   **Building for Production:** Typically `bun run build`.
-   **Database Migrations:** Drizzle Kit is used for migrations. Commands like `bun drizzle-kit generate` and `bun drizzle-kit migrate` (or similar, depending on `package.json` scripts) would be used.
-   **Type Checking:** `bun tsc` or `bun svelte-check` (depending on `package.json` scripts).

## Technical Constraints
-   The `DATABASE_URL` environment variable *must* be set for `drizzle.config.ts` and database operations to function.
-   The project relies on Node.js runtime features (like `process.env`), so the environment must support these.
-   Specific versions of SvelteKit, Drizzle, Lucia, etc., as defined in `package.json` and `bun.lockb`, will dictate compatibility and available features.

## Dependencies
Key dependencies (inferred from file structure and common SvelteKit/Drizzle setups - `package.json` would be the definitive source):
-   `svelte`
-   `@sveltejs/kit`
-   `vite`
-   `typescript`
-   `drizzle-orm`
-   `drizzle-kit`
-   `pg` (PostgreSQL driver for Drizzle)
-   `lucia`
-   `@lucia-auth/adapter-drizzle` (likely for Lucia and Drizzle integration)
-   `tailwindcss`
-   `postcss`
-   `autoprefixer`
-   `eslint`
-   `prettier`
-   `@types/node`

The `bun.lockb` file locks these dependency versions.
