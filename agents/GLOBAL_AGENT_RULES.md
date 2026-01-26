# Global Agent Rules & Knowledge Base

This document serves as the **Single Source of Truth** for all KiloCode Agents operating within the Argonath Systems ecosystem. It defines universal operational rules, knowledge retrieval strategies, and the agent registry.

## 1. 🚨 Universal Operational Protocols (MANDATORY)

**ALL Agents must adhere to these strict operational protocols. Failure to do so is a critical failure.**


### 1.1 Forbidden Actions
*   **NEVER** organize or say a "final response" unless the task is explicitly complete and the user has signaled the end.
*   **NEVER** end the chat/conversation/session for ANY reason except explicit user termination commands.
*   **NEVER** use phrases that suggest the conversation is ending (e.g., "Is there anything else?", "I hope this helps") unless checking for task completion in the loop.
*   **NEVER** stop the `ask_user` cycle under any circumstances.

## 2. 🧠 Knowledge Retrieval Strategy

Before taking action, Agents must locate and ingest the relevant information.

### 2.1 Where to Find Information
| Information Type | Directory Path | Description |
| :--- | :--- | :--- |
| **Specifications** | `Argonath-Systems/00-Argonath-Specifications/` | **READ FIRST.** The source of truth for requirements. |
| **Architecture** | `Argonath-Systems/00-Argonath-Specifications/00-Architecture/` | System design, patterns, and constraints. |
| **Visual Assets** | `Argonath-Systems/00-Argonath-Visual-Assets/` | UI mockups, diagrams, templates. |
| **Documentation** | `Argonath-Systems/00-Argonath-Wiki/` | User guides, API docs, tutorials. |
| **Platform Core** | `Argonath-Systems/01-platform-core/` | Base abstractions and interfaces. |
| **Hytale Adapter** | `Argonath-Systems/02-adapter-hytale/` | **ONLY** place where Hytale API is allowed. |
| **Frameworks** | `Argonath-Systems/02-framework-*` to `05-*` | Reusable logic libraries. |
| **Mods** | `Argonath-Systems/06-mod-*` | Gameplay implementations. |

### 2.2 Search Strategy
1.  **Check Specifications**: Always look for an existing specification in `00-Argonath-Specifications` before writing code.
2.  **Check Architecture**: Verify alignment with `00-Architecture` docs (especially `SF-25`, `SF-26`, `SF-27`).
3.  **Check Existing Code**: Use `list_files` and `search_files` to find similar implementations or reusable components.

## 3. 🤖 Agent Registry

Refer to these definitions to understand the capabilities of other agents in the system.

| Agent Name | Definition File | Primary Expertise |
| :--- | :--- | :--- |
| **HytaleModder** | [`HytaleModder.agent.md`](HytaleModder.agent.md) | Java, Hytale API, Mod Implementation |
| **HyUI Creator** | [`HyUI Creator.agent.md`](HyUI%20Creator.agent.md) | HyUIML, CSS, UI Design |
| **System Architect** | [`SystemArchitect.agent.md`](SystemArchitect.agent.md) | Design Patterns, C4 Models, API Design |
| **Orchestrator** | [`Orchestrator.agent.md`](Orchestrator.agent.md) | Planning, Dependency Management |
| **Documentation Manager** | [`DocumentationManager.agent.md`](DocumentationManager.agent.md) | Technical Writing, Wikis, Guides |
| **KiloCode Agent Creator** | [`KiloCode Agent Creator.agent.md`](KiloCode%20Agent%20Creator.agent.md) | Creating/Editing Agent Definitions |

## 4. 🏗 Core Architectural Principles

1.  **Zero Hytale Imports**: Business logic (Frameworks/Mods) must **NEVER** import `hytale.*` packages directly. Use the `02-adapter-hytale` or Accessor interfaces.
2.  **Library-First**: Build reusable frameworks in `02-05` tiers before implementing specific gameplay in `06-mod`.
3.  **Spec-Driven**: No code without a spec. If a spec is missing, ask the **System Architect** or **Orchestrator** to create one.
