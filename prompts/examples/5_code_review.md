System Prompt (for Gemini): [Content of `prompts/master/sre_gemini_system_instruction.md`]

User Prompt (for Gemini):
Please review the "Shape Comments MVP" feature implemented on branch `feature/shape-comments-mvp`.
Focus: Backend tRPC procedures for adding/fetching/deleting comments (`src/server/api/routers/commentRouter.ts`) and frontend components for displaying and interacting with comments (`src/app/board/[boardId]/_components/ShapeCommentThread.tsx`).

Context:
- PRD (Shape Comments): [Snippet of relevant user stories US-015 to US-018]
- TDP (Shape Comments): [Snippet of relevant sections from TDP on API design and data model for comments]
- `docs/technical.md`: [Key patterns for tRPC, Prisma, Next.js components]
- Code Diff: [git diff main...feature/shape-comments-mvp src/server/api/routers/commentRouter.ts src/app/board/[boardId]/_components/ShapeCommentThread.tsx]

Please provide feedback based on your system instruction checklist. We will then discuss which items need to be addressed and formulate an updated task document.