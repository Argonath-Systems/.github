# Argonath Systems AI Agent Definitions

This directory contains specialized AI agent definitions for the Argonath Systems project. Each agent has specific expertise and responsibilities within the ecosystem.

## Available Agents

### 1. **HytaleModder** ([HytaleModder.agent.md](HytaleModder.agent.md))
**Expertise**: Hytale mod development, platform-agnostic architecture, framework implementation

**Responsibilities**:
- Implement frameworks and mods following architectural principles
- Enforce "Zero Hytale Imports" rule in business logic
- Use Accessor Pattern for game engine interaction
- Write tests and maintain changelogs
- Ensure platform-agnostic design

**When to use**:
- Implementing new frameworks or mods
- Adding features to existing modules
- Fixing bugs in business logic
- Creating unit tests

**Key Directories**:
- `02-framework-*` to `05-framework-*`: Framework implementations
- `06-mod-*`: Gameplay mods
- `02-adapter-hytale`: Hytale API integration

---

### 2. **HyUI Creator** ([HyUI Creator.agent.md](HyUI Creator.agent.md))
**Expertise**: HyUI framework, UI/UX design, HyUIML markup, CSS styling

**Responsibilities**:
- Create HyUIML templates for UI screens
- Design and style UI components
- Validate and render UI mockups
- Follow Lord of the Rings/High Fantasy theme
- Use AI iteration workflow (validate → render → analyze → iterate)

**When to use**:
- Creating new UI screens
- Designing HUD elements
- Building interactive widgets
- Styling UI components

**Key Directories**:
- `00-Argonath-Visual-Assets/ui-mockups`: UI templates and mockups
- `05-framework-ui`: HyUI framework implementation

---

### 3. **Documentation Manager** ([DocumentationManager.agent.md](DocumentationManager.agent.md))
**Expertise**: Technical writing, API documentation, user guides, tutorials

**Responsibilities**:
- Maintain documentation quality and accuracy
- Generate API reference documentation
- Create tutorials and user guides
- Keep documentation synchronized with code
- Enforce documentation standards

**When to use**:
- Updating API documentation
- Creating user guides
- Writing tutorials
- Documenting new features
- Maintaining changelogs

**Key Directories**:
- `00-Argonath-Wiki`: Main documentation hub
- `00-Argonath-Specifications`: Domain specifications
- Module-level `README.md` and `CHANGELOG.md` files

---

### 4. **Orchestrator/Planner** ([Orchestrator.agent.md](Orchestrator.agent.md))
**Expertise**: Strategic planning, multi-phase project coordination, dependency management

**Responsibilities**:
- Break complex requests into actionable plans
- Coordinate work across multiple modules
- Identify dependencies and risks
- Create implementation roadmaps
- Ensure architectural alignment

**When to use**:
- Planning large features
- Complex multi-module changes
- Refactoring projects
- Breaking change planning
- Cross-cutting concerns

**Output**: Detailed implementation plans with phases, tasks, and dependencies

---

### 5. **System Architect** ([SystemArchitect.agent.md](SystemArchitect.agent.md))
**Expertise**: Software architecture, design patterns, system design, API design

**Responsibilities**:
- Enforce architectural principles
- Make critical design decisions
- Design abstractions and interfaces
- Review architectural compliance
- Maintain C4 architecture documentation

**When to use**:
- Designing new modules or frameworks
- Making architectural decisions
- Reviewing design for compliance
- Refactoring for better architecture
- Resolving design conflicts

**Key Directories**:
- `00-Argonath-Specifications/00-Architecture`: Architecture documentation
- C4 model diagrams and design docs

---

## Argonath Multi-Repo Structure

All agents are aware of the new Argonath Systems multi-repository structure:

```
D:\Gaming\Argonath-Systems\
├── .github/agents/                     # This directory - Agent definitions
│
├── 00-Argonath-Wiki/                  # Documentation hub
├── 00-Argonath-Specifications/        # Domain specifications (L1/L2/L3)
├── 00-Argonath-External-Docs/         # Third-party docs (Hytale SDK, HyUI)
├── 00-Argonath-Visual-Assets/         # Diagrams, UI mockups, templates
├── 00-Argonath-Samples/               # Code examples
│
├── 01-platform-core/                  # Platform abstractions
├── 01-platform-sdk/                   # Development SDK
│
├── 02-adapter-hytale/                 # Hytale integration (ONLY hytale.* imports)
├── 02-adapter-mod-api/                # Generic mod API adapter
├── 02-framework-accessor/             # Accessor pattern framework
├── 02-framework-core/                 # Core utilities
│
├── 03-framework-config/               # Configuration system
├── 03-framework-storage/              # Data persistence
├── 03-framework-text-styling/         # Text formatting
│
├── 04-framework-condition/            # Condition system
├── 04-framework-npc/                  # NPC framework
├── 04-framework-objective/            # Objective tracking
├── 04-framework-currency/             # Economy framework
├── 04-framework-stats/                # Stats system
│
├── 05-framework-quest/                # Quest framework
├── 05-framework-ui/                   # UI framework
│
├── 06-mod-*/                          # Gameplay mods
│
├── bundle-core/                       # Core bundle
├── bundle-quest/                      # Quest bundle
│
└── justfile                           # Build automation
```

## Core Architectural Principles

All agents enforce these principles:

1. **Zero Hytale Imports in Business Logic**
   - Business logic (frameworks, mods) is platform-agnostic
   - Hytale API usage restricted to `02-adapter-hytale`
   - Use Accessor Pattern for game engine interaction

2. **Module Dependency Hierarchy**
   - Tier 0: Platform (`01-platform-*`)
   - Tier 1: Adapters (`02-adapter-*`)
   - Tier 2-3: Frameworks (`02-framework-*` to `05-framework-*`)
   - Tier 4: Mods (`06-mod-*`)
   - Tier 5: Bundles (`bundle-*`)
   - Lower tiers cannot depend on higher tiers

3. **Specification-Driven Development**
   - Specifications exist before implementation
   - L1 (Business), L2 (Functional), L3 (Technical) requirements
   - Update specs when gaps found

4. **Library-First Approach**
   - Build reusable frameworks before mods
   - Avoid duplication
   - Catalog libraries in specifications

## Agent Collaboration

Agents work together on complex tasks:

- **Orchestrator** creates implementation plan
- **System Architect** reviews design decisions
- **HytaleModder** implements code
- **HyUI Creator** builds UI components
- **Documentation Manager** updates documentation

## Usage

When invoking an agent, clearly state:
1. The task or goal
2. Affected modules/domains
3. Any constraints or requirements
4. Expected deliverables

Example:
```
"HytaleModder: Implement a mount framework in 04-framework-mount. 
Requirements: Support multiple mount types, speed bonuses, and summoning.
Must be platform-agnostic and use Accessor Pattern."
```

---

**Last Updated**: January 26, 2026  
**Version**: 1.0.0  
**Project**: Argonath Systems
