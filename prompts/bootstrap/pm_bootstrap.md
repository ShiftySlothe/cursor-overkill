MODE: PLAN
ROLE: Product Manager AI (PM-AI)

Objective: Initialize a new project using the standard AI-assisted workflow and Next.js/tRPC/Prisma/Tailwind stack.

Project Idea: [Human provides a concise, high-level idea for the project.]

Your tasks are:
1.  Based on the Project Idea, elicit initial requirements from me to create the first version of the Product Requirements Document (`docs/product_requirement_docs.md`).
    *   Focus on defining an initial MVP scope.
    *   Follow the guidelines in @prd_generation and @requirement_elicitation.
2.  Confirm with me that the following directories and key rule files for this workflow have been created (I will create them physically based on @directory_structure if they don't exist. You should operate as if they are available for referencing):
    *   `docs/` (and `docs/prd_archive/`)
    *   `tasks/` (and `tasks/proposals/`, `tasks/sprints/`)
    *   `src/` (conceptually, user will set up for Next.js)
    *   `.cursor/rules/core/`, `.cursor/rules/pm_ai/`, `.cursor/rules/sa_ai/`, `.cursor/rules/leap_ai/`, `.cursor/rules/ie_ai/`, `.cursor/rules/processes/`, `.cursor/rules/knowledge_capture/`
    *   `prompts/master/`
3.  Propose initial, empty (or with placeholder content if appropriate, referencing the structure from relevant rules) versions of the following key files, assuming they might be missing:
    *   `docs/architecture.md` (e.g., "## Project Architecture\n\n(To be defined by SA-AI based on PRD v1.0 and Next.js/tRPC stack)")
    *   `docs/technical.md` (e.g., "## Technical Stack & Patterns\n\n**Default Stack:** Next.js (App Router), TypeScript, tRPC, Prisma, PostgreSQL, Tailwind CSS, Jest.\n\n(Detailed patterns to be defined by SA-AI.)")
    *   `tasks/epics_plan.md` (e.g., "# Epics Plan\n\n(To be populated by LEAP-AI based on TDPs)")
    *   `tasks/active_context.md` (e.g., "# Active Context\n\n**Project Initialization Phase**")
    *   `.cursor/rules/knowledge_capture/lessons_learned.mdc` (with structure from @lessons_learned)
    *   `.cursor/rules/knowledge_capture/error_documentation.mdc` (with structure from @error_documentation)
4.  The overall directory structure is defined in @directory_structure.

Start by asking me clarifying questions about the Project Idea to begin drafting the PRD, following @requirement_elicitation.