ROLE: Lead Engineer / Agile Planner AI (LEAP-AI)

Objective: Plan Sprint 3, focusing on implementing the "Shape Comments MVP" feature.

Context Files:
- tasks/proposals/technical_design_proposal_shape-comments_YYYY-MM-DD.md (approved TDP, which should detail Server/Client component strategy and tRPC usage)
- docs/product_requirement_docs.md (User Stories US-015 to US-018 for Shape Comments)
- tasks/epics_plan.md (update Epic "Real-time Collaboration Enhancements")
- src/ (for identifying reusable code for real-time aspects, UI components - Server or Client)
- docs/architecture.md (Next.js App Router context)
- docs/technical.md (Next.js App Router context)
- Use `@Docs Next.js App Router`, `@Docs tRPC` for framework-specific planning considerations if needed.

Tasks:
1.  Update `tasks/epics_plan.md`.
2.  Create `tasks/sprints/sprint_YYYY-MM-DD_shape-comments-mvp.md`.
3.  Create `tasks/sprints/sprint_YYYY-MM-DD_shape-comments-mvp/be_tasks.md` and `fe_tasks.md` with detailed, dependent tasks for implementing the MVP of Shape Comments.
    *   **For FE tasks:** Ensure descriptions specify if a component is a Server Component or Client Component, and how it should fetch/mutate data via tRPC (e.g., "Create Server Component `CommentList.tsx` to display comments, fetching data via server-side tRPC call `api.comments.getComments.query()`" or "Create Client Component `AddCommentForm.tsx` using `api.comments.addComment.useMutation()` hook").
    *   **For BE tasks:** Detail tRPC procedure requirements.
4.  Identify and list reusable code components (Server/Client components, utilities, tRPC procedures) as per @planning (LEAP-AI rule).
5.  Initialize `tasks/active_context.md` for this sprint.
6.  Propose a feature branch name (e.g., `feature/shape-comments-mvp`).
Follow @planning (LEAP-AI rule) and @active_context_management.