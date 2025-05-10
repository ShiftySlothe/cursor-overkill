# Product Requirements Document – SaaS App Core Patterns & Boilerplate (v2.0)

**Document Version:** 2.0  
**Date:** YYYY-MM-DD  
**Status:** Draft

---

## 1. Developer Experience & Tooling

### Functional Requirements
- **Code Quality Automation**
  - Enforce linting (ESLint), formatting (Prettier), type checking (TypeScript), and running all tests on every commit using Husky (pre-commit and pre-push hooks).
- **Onboarding Script**
  - Provide a script to set up the local environment, install dependencies, and start all necessary developer experience services (e.g., database, lint, typecheck, test, etc.).
- **Unified DX Command**
  - Provide a single command to start all necessary DX services for development (e.g., database, Next.js, etc.).

### Acceptance Criteria
- Commits are blocked if lint, format, typecheck, or tests fail.
- Onboarding script and unified DX command are documented and work cross-platform (macOS, Linux, Windows).
- Developers can easily set up and start their environment with the provided script/command.

---

## 2. Project Overview
This document defines the requirements for a general-purpose SaaS application boilerplate, designed to accelerate development by providing robust, best-practice-aligned patterns and examples. The boilerplate is built on the T3 stack (Next.js App Router, tRPC, Prisma, NextAuth.js, Tailwind CSS, ShadCN/UI) and is intended to serve as a foundation for most modern SaaS web applications.

---

## 3. Goals and Objectives
- Provide a comprehensive, extensible starting point for SaaS web apps.
- Demonstrate best practices for the T3 stack, referencing:
  - @nextjs_app_router_best_practices.mdc
  - @trpc_best_practices.mdc
  - @prisma_best_practices.mdc
  - @directory_structure.mdc
- Emphasize leveraging existing, well-maintained frameworks and packages (e.g., NextAuth, tRPC, ShadCN/UI) before building custom solutions.
- Enable rapid onboarding and consistent development for new projects and team members.

---

## 4. Target Users
- Developers and teams building SaaS web applications using the T3 stack.
- Projects requiring type safety, scalability, and maintainability from the outset.

---

## 5. Core Requirements
### 5.1 Functional Requirements
- **Authentication & User Management**
  - User registration, login, logout (NextAuth.js)
  - Password reset & email verification (if supported by auth provider)
  - Session management
  - User profile page & editing
- **Frontend Patterns**
  - Layout system (public, authenticated)
  - Protected/authenticated pages (frontend redirect if not logged in)
  - Loading, error, and empty states
  - Notification/toast system
  - Modal/dialog pattern
  - Responsive and accessible UI (Tailwind CSS, ShadCN/UI)
- **API & Data Patterns**
  - tRPC API structure (feature routers, input validation, error handling)
  - Service layer for business logic (separation from API handlers)
  - Pagination, filtering, and sorting (where relevant)
- **Data Fetching & State Management**
  - Query wrappers (handle loading, error, success)
  - Caching strategies (React Query/SWR)
  - Optimistic updates (optional)
- **Onboarding & Help**
  - Onboarding flow/wizard (optional for MVP)
  - In-app help (tooltips, guides)
  - Contact/support form
- **Miscellaneous**
  - File upload (profile pictures, documents)
  - Environment variable management

### 5.2 Non-Functional Requirements
- **Performance:** Fast, responsive UI and API interactions.
- **Usability:** Intuitive, accessible interfaces for all users.
- **Scalability:** Patterns and structure support future growth.
- **Maintainability:** Clear separation of concerns, modular code, and adherence to best practices.
- **Extensibility:** Easy to add new features or swap out components.

---

## 6. Features and Functionality

### 6.1 Authentication & User Management
- **User Story US-001:** As a user, I want to register, log in, and log out securely so that I can access my account.
  - **Acceptance Criteria:**
    - Registration, login, and logout flows are implemented using NextAuth.js.
    - Session is managed securely and persists across reloads.
    - User can view and edit their profile information.

### 6.2 Frontend Patterns
- **User Story US-002:** As a user, I want a consistent layout and navigation experience, with clear feedback for loading and errors.
  - **Acceptance Criteria:**
    - Layout system supports both public and authenticated sections.
    - Pages requiring authentication redirect unauthenticated users to login.
    - Loading, error, and empty states are handled gracefully.
    - Notifications and modals are available as reusable components.
    - UI is responsive and accessible.

### 6.3 API & Data Patterns
- **User Story US-003:** As a developer, I want to build APIs with type safety, validation, and clear separation of business logic.
  - **Acceptance Criteria:**
    - tRPC routers are organized by feature, with input validation via Zod.
    - Service layer is used for business logic, separate from API handlers.
    - Error handling and standardized responses are implemented.
    - Pagination, filtering, and sorting are available where relevant.

### 6.4 Data Fetching & State Management
- **User Story US-004:** As a developer, I want to fetch and mutate data efficiently, with built-in loading and error handling.
  - **Acceptance Criteria:**
    - Query wrappers handle loading, error, and success states.
    - React Query (via tRPC) is used for caching and state management.
    - Optimistic updates are demonstrated where appropriate.

### 6.5 Onboarding & Help
- **User Story US-005:** As a new user, I want onboarding and help resources to get started quickly.
  - **Acceptance Criteria:**
    - Optional onboarding flow/wizard is available.
    - In-app help (tooltips, guides) is accessible.
    - Contact/support form is present.

### 6.6 Miscellaneous
- **User Story US-006:** As a user, I want to upload files (e.g., profile pictures) securely.
  - **Acceptance Criteria:**
    - File upload functionality is implemented and validated.
    - Environment variables are managed securely and documented.

---

## 7. Out of Scope / Future Considerations
- Role-based access control (RBAC)
- User invites
- User audit logs
- Rate limiting/throttling
- Billing & subscription management
- Security & compliance (GDPR, secure headers, etc.)
- Email sending (transactional, notifications)
- Logging & monitoring (Sentry, etc.)

These may be required for future projects and should be considered when extending the boilerplate.

---

## 8. Success Metrics
- Developer onboarding time (time to first feature)
- Time to implement a new core SaaS feature
- User feedback on usability and extensibility
- Adherence to best practices (via code review)

---

## 9. References
- [@nextjs_app_router_best_practices.mdc](../.cursor/rules/core/nextjs_app_router_best_practices.mdc)
- [@trpc_best_practices.mdc](../.cursor/rules/core/trpc_best_practices.mdc)
- [@prisma_best_practices.mdc](../.cursor/rules/core/prisma_best_practices.mdc)
- [@directory_structure.mdc](../.cursor/rules/core/directory_structure.mdc)

---

## 10. Document Version & History
| Version | Date       | Author(s) | Summary of Changes                 |
|---------|------------|-----------|------------------------------------|
| 2.0     | YYYY-MM-DD | PM-AI     | Major update: SaaS core patterns & boilerplate checklist, best practice references, and new structure. | 