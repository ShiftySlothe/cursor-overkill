ROLE: Lead Engineer / Agile Planner AI (LEAP-AI)

Objective: Propose updates to core documentation after merging the "Shape Comments MVP" feature.

Context:
- Feature `feature/shape-comments-mvp` has been merged to main.
- Original TDP: `tasks/proposals/technical_design_proposal_shape-comments_YYYY-MM-DD.md`
- Current `docs/architecture.md`
- Current `docs/technical.md`
- Summary of key changes introduced by the feature: [Human provides a brief summary if helpful, e.g., "New Comment data model (Prisma), new tRPC router for comments, new real-time UI components for comment threads including specific Server Components for display and Client Components for interaction (`"use client";`)."]
- Use `@Docs Next.js App Router` for guidance on documenting App Router patterns if needed.

Please generate a "Documentation Update Proposal" as per @documentation_update, detailing necessary changes to `docs/architecture.md` (e.g., new components (Server/Client) in diagrams, data model additions) and `docs/technical.md` (if any new App Router patterns were solidified or minor tech clarifications are needed, e.g., specific tRPC usage from Server vs. Client Components).