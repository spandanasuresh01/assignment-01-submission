## Export Software Frontend

Built on top of [fe-zen-arch](git@github.com:shivamkj/fe-zen-arch.git) — the core shared architecture for B2B SaaS frontends.

### Libraries

- **React** [Docs](https://react.dev/reference/react)
- **Tailwind CSS** [Docs](https://tailwindcss.com/docs/installation)
- **React Query** [Docs](https://tanstack.com/query/latest/docs/framework/react/overview)
- **React Hook Form** [Docs](https://www.react-hook-form.com/get-started)
- **Zustand** [Docs](https://zustand.docs.pmnd.rs/)

### Setup

```bash
pnpm install   # fe-zen-arch is included as a git submodule, init it first if missing
pnpm dev       # dev server on port 5173
pnpm lint      # prettier + tsc + eslint (fe-zen-arch lint pipeline)
pnpm build     # production build
```

### Notes

- `core`, `ui`, `auth`, `icons` are fe-zen-arch workspace packages, aliased via tsconfig paths & vite aliases.
- Forms are built directly with `useForm` from `core/form` + `Form` / `SubmitButton` from `core/form/components` — no generic form templates.
- Routing uses fe-zen-arch's zustand router: routes defined in `src/shared/routes.tsx`, paths in `src/shared/route-paths.ts`.
- Auth uses the fe-zen-arch auth module (routes, interceptors, login pages) out of the box.
- API base URL comes from `PUBLIC_API_URL` (`.env`).
- Don't use react-query mutation for react-hook-form submit handler.
- For HMR (hot refresh), the file must export only react component, and not any other constant or object.
- While most input elements use `...register('name')`, custom elements like select require `<Select<T> name="name" />` instead.
## AI Usage & Approach

AI tools were used as development assistants during the refactoring process to help understand the existing codebase, identify opportunities for improving component organization, and review implementation approaches.

### Approach

* Inspected the existing Shipping Bill form and its related services, models, and components.
* Refactored the form submission flow to provide clearer local-save and server-synchronization feedback.
* Improved the form's submit button behavior by using the existing loading-aware submit component.
* Updated the Vite configuration and build script to support the Windows development environment.
* Retained the existing project dependencies and used the available service abstractions.

### Validation

* Installed project dependencies.
* Ran the production build using `pnpm build`.
* Verified that the production build completed successfully.
* Reviewed the Git diff and checked for whitespace errors.

AI-generated suggestions were reviewed and adapted to the existing codebase. The final implementation should be reviewed and tested by the developer to ensure that the behavior meets the assignment requirements.
