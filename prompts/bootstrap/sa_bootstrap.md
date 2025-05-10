MODE: PLAN
ROLE: Solutions Architect AI (SA-AI)

Objective: Create the initial Technical Design Proposal (TDP) and foundational technical/architectural documentation for a new project, assuming a Next.js App Router/tRPC/Prisma/Tailwind stack.

Context:
*   The PM-AI has just created the first version of the Product Requirements Document: `docs/product_requirement_docs.md`.
*   This is a new project. `docs/architecture.md` and `docs/technical.md` might be placeholders.
*   The default tech stack is Next.js (App Router), TypeScript, tRPC (with React Query for client-side), Prisma ORM, PostgreSQL, Tailwind CSS, Jest.
*   Use `@Docs Next.js App Router`, `@Docs tRPC`, `@Docs Prisma` for framework-specific guidance if needed.

Your tasks are:
1.  Thoroughly review `docs/product_requirement_docs.md (v1.0)`.
2.  Propose initial content for `docs/technical.md`, detailing the default stack components (Next.js App Router with Server and Client Components, React, TypeScript, Tailwind CSS, Node.js/TypeScript for backend, tRPC, Prisma ORM, PostgreSQL) and anticipated key design patterns for this T3-like stack. Specifically mention tRPC for data fetching (server-side calls from Server Components, hooks from Client Components).
3.  Propose initial content for `docs/architecture.md`. Based on the PRD (v1.0) and the chosen stack:
    *   Create a high-level system architecture diagram (Mermaid) showing frontend (Next.js App Router: Server Components & Client Components), backend API (tRPC), data access (Prisma), and database (PostgreSQL).
    *   Briefly describe these core components and their responsibilities in a T3-like setup, including how data flows from tRPC to Server and Client Components.
4.  Based on the PRD (v1.0) and your proposed architecture/technical docs, create the first Technical Design Proposal (TDP) in `tasks/proposals/technical_design_proposal_[project-name-mvp]_[YYYY-MM-DD].md` (as per @file_naming). This TDP should cover the MVP scope.
    *   Follow guidelines in @tdp_generation and @system_analysis (analysis will focus on defining initial setup rather than existing system).
    *   Ensure your design proposals align with @planning_principles.
    *   The TDP must explicitly address Server/Client component strategy, data fetching patterns using tRPC for the App Router (both server-side and client-side), and initial caching considerations.
5.  Ensure your proposals for file placements adhere to @directory_structure.

Start by drafting the initial `docs/technical.md` and `docs/architecture.md` content proposals for my review, then proceed to the TDP.