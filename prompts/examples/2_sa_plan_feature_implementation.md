ROLE: Solutions Architect AI (SA-AI)

Objective: Create a Technical Design Proposal (TDP) for the "Shape Comments" feature.

Context Files:
- docs/product_requirement_docs.md (relevant sections for Shape Comments)
- docs/architecture.md (current version, detailing Next.js App Router setup)
- docs/technical.md (current version, detailing Next.js App Router patterns, tRPC, Prisma)
- app/src (for context on existing components/services, especially real-time collaboration parts, Server/Client components in `app/srcapp/`, `app/srccomponents/`, existing tRPC routers in `app/srcserver/api/routers/`)
- Use `@Docs Next.js App Router`, `@Docs tRPC` for framework-specific guidance if needed.

Please generate the TDP following @tdp_generation and @system_analysis. Pay specific attention to:
1.  **Component Strategy:** Clearly define which UI parts will be Server Components and which will be Client Components (`"use client";`).
2.  **Data Modeling:** Propose data models for comments (Prisma).
3.  **API Design (tRPC):** Design tRPC procedures for adding/fetching comments.
4.  **Data Fetching:**
    *   How Server Components will fetch/display comment data (e.g., direct tRPC server-side calls).
    *   How Client Components will interact with comment data (e.g., tRPC hooks for mutations and fetching if needed, initial data patterns).
5.  **Real-time Synchronization Aspects:** How comments will be updated in real-time for collaborators.