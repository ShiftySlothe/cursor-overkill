# AI-Assisted Development Workflow Guide (Next.js App Router)

## 1. Introduction

Welcome to the AI-Assisted Development Workflow! This system is designed to leverage multiple AI personas to streamline project planning, design, implementation, and review for modern web applications, while maintaining high standards for code quality and documentation. This document serves as your guide to understanding and utilizing this workflow.

**Your Role as the Human Orchestrator:**
You are the project lead, primary decision-maker, and the orchestrator of the AI team. You will:
*   Initiate each phase and AI role.
*   Provide essential input, context, and clarification.
*   Review and approve AI-generated artifacts (PRDs, TDPs, plans, code proposals).
*   Perform tasks AIs cannot, such as final Git operations, complex E2E testing, manual QA, and direct file system manipulation.
*   Curate and maintain the AI's guiding rules and knowledge base within the `.cursor/` directory.

**Target Technology Stack (Opinionated):**
This workflow is currently optimized for projects using:
*   **Frontend:** Next.js (App Router with Server and Client Components), React, TypeScript, Tailwind CSS, **ShadCN/UI** (as the primary UI component library).
*   **Backend:** Node.js/TypeScript, tRPC (for API layer and data fetching), Prisma ORM.
*   **Database:** PostgreSQL.
*   **Unit Testing:** Jest.
*   **Version Control:** Git (feature-branch workflow).

Refer to `docs/technical.md` (once generated) for project-specific details. Core technology best practices are centralized in rule files like `@nextjs_app_router_best_practices.mdc`, `@prisma_best_practices.mdc`, and `@trpc_best_practices.mdc`.

## 2. Core Principles of the Workflow

*   **Phase-Driven Development:** A structured progression from idea to implemented feature.
*   **AI Role Specialization:** Each AI persona has a distinct focus (see section 3).
*   **Server and Client Component Model:** Development leverages the Next.js App Router's distinction between Server Components and Client Components, guided by `@nextjs_app_router_best_practices.mdc`.
*   **tRPC for Data Flow:** tRPC is the primary mechanism for API communication and data fetching, with detailed usage patterns defined in `@trpc_best_practices.mdc` and integrated with App Router patterns from `@nextjs_app_router_best_practices.mdc`.
*   **Centralized Memory & Knowledge:** All project context, plans, and AI guidance reside in `docs/`, `tasks/`, and `.cursor/` respectively. Key files, including core best practices and organizational rules like `@directory_structure.mdc` and `@file_naming.mdc`, are interlinked using Cursor's `@filename` syntax within AI rules and prompts.
*   **Test-Driven Development (TDD):** IE-AIs propose and write unit tests before or alongside implementation code, guided by @tdd.
*   **Human-in-the-Loop:** You provide approvals, make critical decisions, and manage the overall flow.
*   **Living Documentation:** Project documents are continuously updated to reflect the current state, guided by @memory and incorporating App Router architectural decisions.

## 3. AI Roles & Invocation

Each AI role is invoked by providing its master prompt (from `prompts/master/`) to Cursor. These master prompts are concise and primarily serve to define the AI's role and point to detailed operational and best-practice rules within the `.cursor/rules/` directory. Relevant context files (e.g., PRD, TDP, task files) are also provided as needed.

1.  **Product Manager AI (PM-AI)**
    *   **Master Prompt:** `prompts/master/pm_ai_master.md`
    *   **Responsibilities:** Elicits requirements, generates/updates `docs/product_requirement_docs.md`, archives old PRDs.
    *   **Key Rules Referenced:** @prd_generation, @requirement_elicitation, @directory_structure, @file_naming.
2.  **Solutions Architect AI (SA-AI)**
    *   **Master Prompt:** `prompts/master/sa_ai_master.md`
    *   **Responsibilities:** Analyzes PRD, designs high-level technical solution for the Next.js App Router, generates Technical Design Proposal (TDP).
    *   **Key Rules Referenced:** @tdp_generation, @system_analysis, @planning_principles, @nextjs_app_router_best_practices, @prisma_best_practices, @trpc_best_practices, @directory_structure, @file_naming.
3.  **Lead Engineer / Agile Planner AI (LEAP-AI)**
    *   **Master Prompt:** `prompts/master/leap_ai_master.md`
    *   **Responsibilities:** Creates/updates epics plan, sprint plans, detailed role-specific task lists (BE/FE). Initializes active context. Proposes Git branches. Proposes updates to core documentation post-merge.
    *   **Key Rules Referenced:** @planning (from `.cursor/rules/leap_ai/`), @active_context_management, @planning_principles, @git_workflow, @documentation_update, @nextjs_app_router_best_practices, @prisma_best_practices, @trpc_best_practices, @directory_structure, @file_naming.
4.  **Backend Engineer AI (BE-AI)**
    *   **Master Prompt:** `prompts/master/be_ai_master.md`
    *   **Responsibilities:** Implements backend tasks (tRPC, Prisma). Writes Jest unit tests. Proposes commits.
    *   **Key Rules Referenced:** @backend, @common, @tdd, @implement_principles, @debug_procedures, @git_workflow, @trpc_best_practices, @prisma_best_practices, @directory_structure, @file_naming.
5.  **Frontend Engineer AI (FE-AI)**
    *   **Master Prompt:** `prompts/master/fe_ai_master.md`
    *   **Responsibilities:** Implements frontend tasks (Next.js App Router - Server/Client Components, Tailwind, ShadCN/UI, tRPC integration). Writes Jest unit tests. Proposes commits.
    *   **Key Rules Referenced:** @frontend, @common, @tdd, @implement_principles, @debug_procedures, @git_workflow, @nextjs_app_router_best_practices, @trpc_best_practices, @directory_structure, @file_naming.
6.  **Senior Review Engineer (SRE-Gemini - External LLM)**
    *   **System Instruction:** `prompts/master/sre_gemini_system_instruction.md` (Use this when interacting with Gemini).
    *   **Responsibilities:** Reviews code for quality, adherence to standards (including core best practices like @nextjs_app_router_best_practices, @prisma_best_practices, @trpc_best_practices, and project conventions from @directory_structure), correctness. Provides feedback for revisions.

## 4. Step-by-Step Development Workflow

**Phase 0: Project Setup (If New Project)**
1.  **You:** Create the base directory structure (ideally matching @directory_structure).
2.  **You:** Populate `.cursor/` with all rule files (`.mdc`) and `prompts/` with master/bootstrap prompts.
3.  **You:** Invoke **PM-AI** using `prompts/bootstrap/pm_bootstrap.md` and your project idea.
    *   PM-AI creates initial `docs/product_requirement_docs.md` and placeholder docs, guided by @prd_generation and @directory_structure.
4.  **You:** Review and approve PM-AI's output.
5.  **You:** Invoke **SA-AI** using `prompts/bootstrap/sa_bootstrap.md`.
    *   SA-AI creates initial `docs/technical.md`, `docs/architecture.md`, and the first TDP, guided by @tdp_generation and relevant core best practice documents.
6.  **You:** Review and approve SA-AI's output. Now proceed to Phase 1 for the first feature.

**Phase 1: Product Definition (New Feature or Iteration)**
1.  **You:** Provide a feature idea or update request to **PM-AI**.
2.  PM-AI: Elicits requirements, generates/updates `docs/product_requirement_docs.md` per @prd_generation.
3.  **You:** Review and approve the PRD.

**Phase 2: Solution Architecture**
1.  **You:** Provide the approved PRD to **SA-AI**.
2.  SA-AI: Analyzes and generates a Technical Design Proposal (TDP) per @tdp_generation, referencing core best practices.
3.  **You:** Review and approve the TDP.

**Phase 3: Detailed Planning (Sprint Setup)**
1.  **You:** Provide the approved TDP to **LEAP-AI**.
2.  LEAP-AI: Updates epics, creates sprint plan and detailed task lists per @planning. Initializes `tasks/active_context.md` per @active_context_management. Proposes a feature branch name per @git_workflow.
3.  **You:** Review and approve plans. Create the Git feature branch.

**Phase 4: Implementation (Sprint Execution)**
1.  **You:** Assign "Open" tasks from `be_tasks.md` to **BE-AI** and from `fe_tasks.md` to **FE-AI**.
2.  BE-AI/FE-AI:
    *   Understand task context, guided by their master prompt's references (e.g., to @common, @implement_principles, @nextjs_app_router_best_practices, etc.).
    *   Follow TDD (@tdd).
    *   Implement code according to App Router patterns and other best practices.
    *   Update task status in their respective task files and `tasks/active_context.md`.
    *   Propose commits per @git_workflow.
3.  **You:** Execute Git commits and push the feature branch.
4.  Repeat for all tasks in the sprint, respecting dependencies.

**Phase 5: Code Review**
1.  **You:** When a feature is substantially complete, prepare the code diff or relevant files.
2.  **You:** Interact with **SRE-Gemini** using its system instruction and provide code/context, including references to key best practice documents.
3.  SRE-Gemini: Provides review feedback.
4.  **You:** Discuss feedback, agree on changes.
5.  SRE-Gemini/You: Formulate revision tasks.
6.  **You:** Create/update tasks. Loop back to Phase 4 for revisions.

**Phase 6: QA & Merge**
1.  **You:** After review feedback is addressed, perform manual QA and E2E testing.
2.  **You:** If QA passes, merge the feature branch per @git_workflow.

**Phase 7: Post-Merge Documentation Update**
1.  **You:** Task **LEAP-AI** to propose updates for `docs/architecture.md` and `docs/technical.md` as per @documentation_update.
2.  **You:** Review LEAP-AI's proposals and manually update the official documents.

## 5. Key Memory Files Overview

A comprehensive map of all documents and their purpose can be found in @memory (which itself references @directory_structure and @file_naming). This includes:

*   **`.cursor/`:** AI rules, prompts, and knowledge base.
    *   `rules/core/`: Centralized best practices (@nextjs_app_router_best_practices, @prisma_best_practices, @trpc_best_practices), organizational rules (@directory_structure, @file_naming), and general principles (@general_ai_rules, @implement_principles, @debug_procedures, @planning_principles).
    *   `rules/[role_name]/`: Role-specific operational rules (e.g., @prd_generation for PM-AI).
    *   `rules/processes/`: Rules for common procedures (e.g., @git_workflow, @documentation_update).
    *   `rules/knowledge_capture/`: Living documents for project learning (@lessons_learned, @error_documentation).
*   **`docs/`:** Core project definition (PRD, Architecture, Technical).
*   **`tasks/`:** Planning artifacts (Proposals, Epics, Sprints, Task Lists, Active Context).
*   **`src/`:** Application source code, structured per @directory_structure and implementing patterns from core best practice documents.

## 6. Integrating into an Existing Project

1.  **Setup:** Copy `.cursor/` (with all sub-rules) and `prompts/` directories into your project. Create `docs/`, `tasks/` (with subdirectories) per @directory_structure if they don't exist. Ensure your project uses the Next.js App Router.
2.  **Baseline Documentation (Iterative):**
    *   Use **PM-AI** (guided by @prd_generation) to analyze parts of your existing application and generate an initial `docs/product_requirement_docs.md`.
    *   Use **SA-AI** (guided by @tdp_generation and core best practices like @nextjs_app_router_best_practices) to analyze the codebase and PRD to create initial drafts of `docs/architecture.md` and `docs/technical.md`. This requires significant human guidance.
3.  **Start Small:** Apply the full workflow (Phases 1-7) to a single new, well-contained feature.
4.  **Adapt Rules:** Modify rules in `.cursor/rules/` (especially IE-AI rules and potentially @directory_structure) to fit your project's existing conventions, using @rule_update_procedure.

## 7. Maintaining the System

*   **Rule Updates:** When AIs suggest rule changes via @rule_update_procedure, review and apply them manually. Pay special attention to keeping core best practice documents (e.g., `@nextjs_app_router_best_practices.mdc`) up-to-date with evolving framework features.
*   **Knowledge Capture:** Regularly review and curate suggestions for @lessons_learned and @error_documentation.
*   **Feedback:** Your feedback to the AIs during their tasks is crucial for them to "learn" and adapt within the boundaries of their (now more referenced) rules.

This AI-assisted workflow aims to be a powerful co-pilot system. Consistent application of these processes and diligent human oversight will lead to efficient and high-quality Next.js App Router development.