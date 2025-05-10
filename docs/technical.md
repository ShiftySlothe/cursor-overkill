# Technical Stack & Patterns

**Version:** 1.0
**Date:** YYYY-MM-DD (To be filled by SA-AI during initial design)

## 1. Overview
This document details the primary technologies, libraries, and established patterns for the project. Adherence to these standards is crucial for consistency and maintainability.

## 2. Core Technology Stack

*   **Language:** **TypeScript** (Strict mode, used across frontend and backend).
*   **Frontend Framework:** **Next.js (App Router)**
    *   Utilizes Server Components and Client Components (`"use client;"`).
    *   Routing is file-system based within the `src/app/` directory.
    *   Reference: `@nextjs_app_router_best_practices.mdc`.
*   **UI Library:** **React**
*   **Styling:** **Tailwind CSS**
*   **UI Component Source:** **ShadCN/UI**
    *   Primary source for UI components, expected to be integrated into `src/components/ui/`.
    *   Custom components require justification and should align stylistically.
*   **API Layer:** **tRPC**
    *   End-to-end type-safe APIs.
    *   Server setup in `src/server/api/trpc.ts` and `root.ts`. Client setup in `src/trpc/`.
    *   Reference: `@trpc_best_practices.mdc`.
*   **Backend Runtime:** **Node.js**
*   **Database ORM:** **Prisma**
    *   Schema in `prisma/schema.prisma`. Client in `src/server/db.ts`.
    *   Reference: `@prisma_best_practices.mdc`.
*   **Database:** **PostgreSQL**
*   **Authentication:** **NextAuth.js**
    *   Configuration in `src/server/auth/config.ts`.
    *   Prisma Adapter for database session/user storage.
*   **State Management (Client Components):**
    *   Primarily local React state (`useState`, `useReducer`).
    *   React Query (via tRPC) for server state caching and synchronization.
    *   Global client state solutions (e.g., Zustand, Jotai) to be considered only if essential and approved.
*   **Form Handling:**
    *   Combination of client-side logic with tRPC mutations and Next.js Server Actions (which may call tRPC mutations).
    *   Input validation with Zod.
*   **Unit Testing:** **Jest**
    *   Using `@testing-library/react` for frontend components.
    *   TDD principles are encouraged, guided by `@tdd.mdc`.
*   **Environment Variables:** Managed via `@t3-oss/env-nextjs` (`src/env.js`).
*   **Linting & Formatting:** ESLint and Prettier (configurations in project root).

## 3. Key Design Patterns & Conventions

*   **Component Model:** Strict adherence to Next.js App Router's Server and Client Component distinction. Client Components should be pushed to the leaves of the tree where possible.
*   **Data Fetching:**
    *   Server Components: Use server-side tRPC calls (e.g., `api.procedure.query()` from `~/trpc/server`).
    *   Client Components: Use tRPC hooks (e.g., `api.procedure.useQuery()` from `~/trpc/react`).
*   **API Design:** tRPC procedures with Zod for input validation. Use `publicProcedure` and `protectedProcedure` appropriately.
*   **Database Operations:** All database interactions via Prisma client, following best practices for queries, relations, and migrations.
*   **Directory Structure:** Adherence to `@directory_structure.mdc`.
*   **File Naming:** Adherence to `@file_naming.mdc`.
*   **Git Workflow:** Feature branching model, as per `@git_workflow.mdc`.

This document serves as a living reference and will be updated as the project evolves and new technical decisions are made.