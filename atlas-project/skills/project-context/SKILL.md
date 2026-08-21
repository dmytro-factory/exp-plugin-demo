---
name: project-context
description: Provides architecture and coding conventions for the Atlas project. Use when someone asks about how to build features, structure code, or pick tools for Atlas.
---

# Project Atlas

Atlas is a customer-facing web application built with React 18, TypeScript, and Vite. It uses Tailwind CSS for styling, React Router for navigation, and TanStack Query for server state. State management is handled with Zustand — do not use Redux or Context for global state. All API calls go through a central `apiClient` module. Components are co-located with their tests using `.test.tsx` files. The project follows a feature-based directory structure under `src/features/`. When answering questions about how to build something for Atlas, default to functional components with hooks, strict TypeScript types (no `any`), and Tailwind utility classes for all styling.
