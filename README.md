# AI-Assisted Development Workflow Guide (Next.js App Router)

## 1. Introduction

Welcome to the AI-Assisted Development Workflow! This system is designed to leverage multiple AI personas to streamline project planning, design, implementation, and review for modern web applications, while maintaining high standards for code quality and documentation. This document serves as your guide to understanding and utilizing this workflow.

**Your Role as the Human Orchestrator:**
You are the project lead, primary decision-maker, and the orchestrator of the AI team. You will:
*   Initiate each phase and AI role.
*   Provide essential input, context, and clarification.
*   Review and approve AI-generated artifacts (PRDs, TDPs, plans, code proposals).
*   Perform tasks AIs cannot, such as final Git operations, complex E2E testing, manual QA, and direct file system manipulation.
*   Curate and maintain the AI's guiding rules and knowledge base (`.cursor/` directory).

**Target Technology Stack (Opinionated):**
This workflow is currently optimized for projects using:
*   **Frontend:** Next.js (App Router with Server and Client Components), React, TypeScript, Tailwind CSS
*   **Backend:** Node.js/TypeScript, tRPC (for API layer and data fetching), Prisma ORM
*   **Database:** PostgreSQL
*   **Unit Testing:** Jest
*   **Version Control:** Git (feature-branch workflow)
Refer to `docs/technical.md` (once generated) for project-specific details and `@nextjs_app_router_best_practices.mdc` for core Next.js App Router guidelines.

## 2. Core Principles of the Workflow

*   **Phase-Driven Development:** A structured progression from idea to implemented feature.
*   **AI Role Specialization:** Each AI persona has a distinct focus (see section 3).
*   **Server and Client Component Model:** Development leverages the Next.js App Router's distinction between Server Components (default, for server-rendered UI and data fetching) and Client Components (`"use client";` for interactivity).
*   **tRPC for Data Flow:** tRPC is the primary mechanism for API communication and data fetching, utilized by both Server Components (direct server-side calls) and Client Components (via `@trpc/react-query` hooks).
*   **Centralized Memory & Knowledge:** All project context, plans, and AI guidance reside in `docs/`, `tasks/`, and `.cursor/` respectively. Key files, including `@nextjs_app_router_best_practices.mdc`, are interlinked using Cursor's `@filename` syntax within AI rules and prompts.
*   **Test-Driven Development (TDD):** IE-AIs propose and write unit tests before or alongside implementation code, guided by @tdd.
*   **Human-in-the-Loop:** You provide approvals, make critical decisions, and manage the overall flow.
*   **Living Documentation:** Project documents are continuously updated to reflect the current state, guided by @memory and incorporating App Router architectural decisions.

## 3. AI Roles & Invocation

Each AI role is invoked by providing its master prompt (from `prompts/master/`) to Cursor, along with any necessary context files (e.g., PRD, TDP, specific task files, and relevant parts of `@nextjs_app_router_best_practices.mdc`).

1.  **Product Manager AI (PM-AI)**
    *   **Master Prompt:** `prompts/master/pm_ai_master.md`
    *   **Responsibilities:** Elicits requirements, generates/updates `docs/product_requirement_docs.md` (@prd_generation), archives old PRDs.
    *   **Key Rules:** @prd_generation, @requirement_elicitation.
2.  **Solutions Architect AI (SA-AI)**
    *   **Master Prompt:** `prompts/master/sa_ai_master.md`
    *   **Responsibilities:** Analyzes PRD, designs high-level technical solution within the Next.js App Router framework, generates Technical Design Proposal (TDP) in `tasks/proposals/`. TDPs must detail Server/Client component strategy and tRPC data fetching patterns.
    *   **Key Rules:** @tdp_generation, @system_analysis, @planning_principles, @nextjs_app_router_best_practices.
3.  **Lead Engineer / Agile Planner AI (LEAP-AI)**
    *   **Master Prompt:** `prompts/master/leap_ai_master.md`
    *   **Responsibilities:** Creates/updates `tasks/epics_plan.md`, sprint plans (`tasks/sprints/sprint_[...].md`), detailed role-specific task lists (`be_tasks.md`, `fe_tasks.md`). FE tasks will specify Server/Client component types and tRPC usage. Initializes `tasks/active_context.md`. Proposes Git branches. Proposes updates to `docs/architecture.md` & `docs/technical.md` post-merge to reflect App Router implementations.
    *   **Key Rules:** @planning (from `.cursor/rules/leap_ai/`), @active_context_management, @planning_principles, @git_workflow, @documentation_update, @nextjs_app_router_best_practices.
4.  **Backend Engineer AI (BE-AI)**
    *   **Master Prompt:** `prompts/master/be_ai_master.md`
    *   **Responsibilities:** Implements backend tasks using tRPC (procedures called by Server/Client components or Server Actions), Prisma, etc. Writes Jest unit tests. Proposes commits.
    *   **Key Rules:** @backend (opinionated IE-AI rule), @common (IE-AI rule), @tdd, @implement_principles, @debug_procedures, @git_workflow, @trpc_best_practices, @prisma_best_practices.
5.  **Frontend Engineer AI (FE-AI)**
    *   **Master Prompt:** `prompts/master/fe_ai_master.md`
    *   **Responsibilities:** Implements frontend tasks using Next.js App Router (Server and Client Components), React, Tailwind. Integrates with tRPC (server-side calls in Server Components, hooks in Client Components). Writes Jest unit tests for complex logic. Proposes commits.
    *   **Key Rules:** @frontend (opinionated IE-AI rule), @common (IE-AI rule), @tdd, @implement_principles, @debug_procedures, @git_workflow, @nextjs_app_router_best_practices, @trpc_best_practices.
6.  **Senior Review Engineer (SRE-Gemini - External LLM)**
    *   **System Instruction:** `prompts/master/sre_gemini_system_instruction.md` (Use this when interacting with Gemini).
    *   **Responsibilities:** Reviews code for quality, adherence to standards (including App Router best practices), correctness. Provides feedback for revisions.

## 4. Step-by-Step Development Workflow

**Phase 0: Project Setup (If New Project)**
1.  **You:** Create the base directory structure as per @directory_structure.
2.  **You:** Populate `.cursor/` with all rule files (`.mdc`) including `@nextjs_app_router_best_practices.mdc`, and `prompts/` with master/bootstrap prompts.
3.  **You:** Invoke **PM-AI** using `prompts/bootstrap/pm_bootstrap.md` and your project idea.
    *   PM-AI creates initial `docs/product_requirement_docs.md` and placeholder docs.
4.  **You:** Review and approve PM-AI's output.
5.  **You:** Invoke **SA-AI** using `prompts/bootstrap/sa_bootstrap.md`.
    *   SA-AI creates initial `docs/technical.md` (App Router focused), `docs/architecture.md` (App Router focused), and the first TDP (App Router focused).
6.  **You:** Review and approve SA-AI's output. Now proceed to Phase 1 for the first feature.

**Phase 1: Product Definition (New Feature or Iteration)**
1.  **You:** Provide a feature idea or update request to **PM-AI**.
2.  PM-AI: Elicits requirements, generates/updates `docs/product_requirement_docs.md`.
3.  **You:** Review and approve the PRD.

**Phase 2: Solution Architecture**
1.  **You:** Provide the approved PRD to **SA-AI**.
2.  SA-AI: Analyzes and generates a Technical Design Proposal (TDP) in `tasks/proposals/`, detailing Server/Client component strategy, tRPC data flow, etc., adhering to @nextjs_app_router_best_practices.
3.  **You:** Review and approve the TDP.

**Phase 3: Detailed Planning (Sprint Setup)**
1.  **You:** Provide the approved TDP to **LEAP-AI**.
2.  LEAP-AI: Updates `tasks/epics_plan.md`. Creates a sprint plan and detailed `be_tasks.md` & `fe_tasks.md`. FE tasks will specify Server/Client component types and their tRPC interaction methods. Initializes `tasks/active_context.md`. Proposes a feature branch name.
3.  **You:** Review and approve plans. Create the Git feature branch as per @git_workflow.

**Phase 4: Implementation (Sprint Execution)**
1.  **You:** Assign "Open" tasks from `be_tasks.md` to **BE-AI**.
2.  **You:** Assign "Open" tasks from `fe_tasks.md` to **FE-AI**.
3.  BE-AI/FE-AI:
    *   Understand task context (@common, @implement_principles, @nextjs_app_router_best_practices).
    *   Follow TDD (@tdd).
    *   Implement code according to App Router patterns (Server/Client Components, tRPC usage).
    *   Update task status in their respective task files and briefly in `tasks/active_context.md`.
    *   Propose commits (@git_workflow).
4.  **You:** Execute Git commits and push the feature branch.
5.  Repeat for all tasks in the sprint, respecting dependencies.

**Phase 5: Code Review**
1.  **You:** When a feature is substantially complete on its branch, prepare the code diff or relevant files.
2.  **You:** Interact with **SRE-Gemini** using `prompts/master/sre_gemini_system_instruction.md` and provide code/context.
3.  SRE-Gemini: Provides review feedback, checking against @nextjs_app_router_best_practices.
4.  **You:** Discuss feedback with SRE-Gemini, agree on changes.
5.  SRE-Gemini/You: Formulate revision tasks.
6.  **You:** Create/update tasks in the IE-AI's task file. Loop back to Phase 4 for revisions.

**Phase 6: QA & Merge**
1.  **You:** After review feedback is addressed, perform manual QA and E2E testing based on PRD acceptance criteria.
2.  **You:** If QA passes, merge the feature branch into `main` (or dev branch) following @git_workflow.

**Phase 7: Post-Merge Documentation Update**
1.  **You:** Task **LEAP-AI** to propose updates for `docs/architecture.md` and `docs/technical.md` as per @documentation_update, reflecting the merged App Router feature.
2.  **You:** Review LEAP-AI's proposals and manually update the official documents.

## 5. Key Memory Files Overview

A comprehensive map of all documents and their purpose can be found in @memory. This includes:
*   **`.cursor/`:** AI rules, prompts, and knowledge base (@lessons_learned, @error_documentation).
    *   `rules/core/nextjs_app_router_best_practices.mdc`: Central guide for Next.js App Router development.
*   **`docs/`:** Core project definition (PRD, Architecture, Technical - all App Router focused).
*   **`tasks/`:** Planning artifacts (Proposals, Epics, Sprints, Task Lists, Active Context).
*   **`src/`:** Application source code, structured for Next.js App Router (`app/` dir, Server/Client Components).

## 6. Integrating into an Existing Project

1.  **Setup:** Copy `.cursor/` (including `@nextjs_app_router_best_practices.mdc`) and `prompts/` directories into your project. Create `docs/`, `tasks/` (with subdirectories) if they don't exist. Ensure your project uses the Next.js App Router.
2.  **Baseline Documentation (Iterative):**
    *   Use **PM-AI** to analyze parts of your existing application and generate an initial `docs/product_requirement_docs.md`.
    *   Use **SA-AI** (guided by @nextjs_app_router_best_practices) to analyze the codebase and the generated PRD to create initial drafts of `docs/architecture.md` and `docs/technical.md`, reflecting App Router patterns. This will require significant human guidance and review.
3.  **Start Small:** Apply the full workflow (Phases 1-7) to a single new, well-contained feature.
4.  **Adapt Rules:** Modify rules in `.cursor/rules/` (especially @directory_structure and IE-AI rules) to fit your project's existing conventions, using @rule_update_procedure.

## 7. Maintaining the System

*   **Rule Updates:** When AIs suggest rule changes via @rule_update_procedure, review and apply them manually. Pay special attention to keeping `@nextjs_app_router_best_practices.mdc` up-to-date with evolving Next.js features.
*   **Knowledge Capture:** Regularly review and curate suggestions for @lessons_learned and @error_documentation.
*   **Feedback:** Your feedback to the AIs during their tasks is crucial for them to "learn" and adapt within the boundaries of their rules.

This AI-assisted workflow aims to be a powerful co-pilot system. Consistent application of these processes and diligent human oversight will lead to efficient and high-quality Next.js App Router development.