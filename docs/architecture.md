# Project Architecture

**Version:** 1.0
**Date:** YYYY-MM-DD (To be filled by SA-AI during initial design)

## 1. Overview
This document describes the high-level system architecture for this project. It is built using the Next.js App Router and follows principles similar to the T3 Stack, emphasizing type safety, developer experience, and a clear separation of concerns between frontend and backend components.

## 2. Core Components & Data Flow

The system architecture is composed of the following key components:

*   **Frontend (Next.js App Router):**
    *   Built with Next.js and React, utilizing the App Router for file-system-based routing and layout management.
    *   Employs **Server Components** for server-side rendering, direct data fetching (via tRPC server-side calls), and reducing client-side JavaScript.
    *   Uses **Client Components** (`"use client;"`) for interactivity, state management, lifecycle effects, and browser-only APIs.
    *   Styling is handled by Tailwind CSS, with UI elements primarily sourced from **ShadCN/UI**.
*   **API Layer (tRPC):**
    *   Provides a type-safe API for communication between the frontend (both Server and Client Components) and the backend.
    *   Defined in `src/server/api/`, with the root router in `root.ts` and individual feature routers in `routers/`.
*   **Backend Logic (Node.js/TypeScript):**
    *   tRPC resolvers and any additional business logic are written in TypeScript and execute in a Node.js environment on the server.
*   **Data Access Layer (Prisma):**
    *   Prisma ORM facilitates type-safe interactions with the PostgreSQL database. The Prisma client is typically instantiated in `src/server/db.ts`.
*   **Database (PostgreSQL):**
    *   The primary relational database for storing application data. Schema is defined in `prisma/schema.prisma`.
*   **Authentication (NextAuth.js):**
    *   Handles user authentication and session management, configured in `src/server/auth/`.

### 2.1 System Architecture Diagram (High-Level)

```mermaid
graph TD
    UserBrowser["User's Browser"] --> NextJsApp[Next.js Application (App Router)];

    subgraph NextJsApp["Next.js Application"]
        direction LR
        ServerComponents["Server Components (RSC)"]
        ClientComponents["Client Components ('use client')"]
    end

    ServerComponents -- "tRPC Server Caller (~/trpc/server)" --> TRPCServer[tRPC Backend];
    ClientComponents -- "tRPC React Hooks (~/trpc/react)" --> TRPCAPIEndpoint["/api/trpc HTTP Endpoint"];
    TRPCAPIEndpoint --> TRPCServer;

    subgraph TRPCServer["tRPC Backend (Node.js)"]
        direction TB
        AppRouter["App Router (root.ts)"] --> FeatureRouters["Feature Routers"];
        FeatureRouters -- "Procedures & Resolvers" --> PrismaClient["Prisma Client (db.ts)"];
    end

    PrismaClient -- SQL --> PostgreSQLDB[(PostgreSQL Database)];
    TRPCServer -- "Session via Context" --> NextAuth[NextAuth.js];

    style UserBrowser fill:#f9f,stroke:#333,stroke-width:2px
    style NextJsApp fill:#ccf,stroke:#333,stroke-width:2px
    style TRPCServer fill:#cfc,stroke:#333,stroke-width:2px
    style PostgreSQLDB fill:#f80,stroke:#333,stroke-width:2px

### 2.2 Data Flow
*   **Server Components:** Fetch data on the server using the tRPC server-side caller (`api` from `~/trpc/server`).
*   **Client Components:** Fetch data or perform mutations using tRPC React Query hooks (`api` from `~/trpc/react`), which call the `/api/trpc` endpoint. Initial data can be passed as props from parent Server Components.
*   **Mutations:** Triggered from Client Components or Server Actions, processed by tRPC procedures, which use Prisma to update the database.

## 3. Further Details
This architecture will be further detailed in Technical Design Proposals (TDPs) for specific features. Refer to `@directory_structure` for file locations and `@nextjs_app_router_best_practices` for component model guidance.