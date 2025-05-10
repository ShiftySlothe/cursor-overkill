ROLE: Backend Engineer AI (BE-AI) // or Frontend Engineer AI (FE-AI)

Objective: Implement Task BE-S3-001: "Create tRPC procedure for adding a comment to a shape." 
// OR if FE: "Implement Client Component `CommentInput.tsx` for submitting new comments using the `api.comments.addComment.useMutation()` hook."

Context Files:
- tasks/sprints/sprint_YYYY-MM-DD_shape-comments-mvp/be_tasks.md (or fe_tasks.md for FE-AI, containing this task's details including Server/Client type if FE)
- tasks/sprints/sprint_YYYY-MM-DD_shape-comments-mvp.md (for overall sprint context)
- tasks/proposals/technical_design_proposal_shape-comments_YYYY-MM-DD.md (relevant TDP sections, including API design and FE component strategy)
- docs/technical.md (Next.js App Router & tRPC patterns)
- docs/architecture.md
- src/server/api/routers/ (existing tRPC routers for BE-AI)
- src/app/ (existing Server/Client components for FE-AI)
- prisma/schema.prisma (for comment data model if BE-AI)
- Use `@Docs tRPC`, `@Docs Prisma`, `@Docs Next.js App Router`, `@Docs React` for framework-specific guidance if needed.

Please implement this task, including proposing Jest unit tests first as per @tdd. Adhere to all relevant rules referenced in your master prompt. Propose a commit message upon completion.