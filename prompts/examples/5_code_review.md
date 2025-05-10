System Prompt (for Gemini): [Content of `prompts/master/sre_gemini_system_instruction.md`]

User Prompt (for Gemini):
Please review the "Shape Comments MVP" feature implemented on branch `feature/shape-comments-mvp`.
Focus: 
- Backend tRPC procedures for adding/fetching/deleting comments (`src/server/api/routers/commentRouter.ts`).
- Frontend Client Component for displaying and interacting with comments (`src/app/board/[boardId]/_components/ShapeCommentThread.tsx`). Assume this component fetches data using tRPC hooks and handles user input for new comments.
- Any related Server Components that might be passing initial data to `ShapeCommentThread.tsx`.

Context:
- PRD (Shape Comments): [Snippet of relevant user stories US-015 to US-018]
- TDP (Shape Comments): [Snippet of relevant sections from TDP on API design, data model for comments, and Server/Client component strategy for comments UI]
- `docs/technical.md`: [Key patterns for tRPC, Prisma, Next.js App Router components (Server/Client), Tailwind CSS]
- Code Diff: [git diff main...feature/shape-comments-mvp src/server/api/routers/commentRouter.ts src/app/board/[boardId]/_components/ShapeCommentThread.tsx]
- Use `@Docs Next.js App Router`, `@Docs tRPC`, `@Docs Prisma` for framework-specific best practices if needed.

Please provide feedback based on your system instruction checklist. We will then discuss which items need to be addressed and formulate an updated task document.