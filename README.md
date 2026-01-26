# Argonath Systems

> **Platform-Agnostic Framework Ecosystem for Hytale Mod Development**

[![Website](https://img.shields.io/badge/Website-argonath--systems.github.io-blue?logo=github-pages)](https://argonath-systems.github.io/00-Argonath-Wiki)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-7289DA?logo=discord&logoColor=white)](https://discord.gg/RK3MtpyH)
[![GitHub](https://img.shields.io/badge/GitHub-Argonath--Systems-181717?logo=github)](https://github.com/orgs/Argonath-Systems/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-25-orange?logo=java)](https://openjdk.org/)

---

## 🌟 Vision

Argonath Systems provides a **modular, platform-agnostic architecture** for creating rich, quest-driven experiences in Hytale. Our framework ecosystem enables developers to build sophisticated mods without coupling to the volatile Hytale Alpha API.

### Core Principles

- **🎯 Zero Platform Coupling** - Business logic never imports Hytale classes
- **🧩 Modular Architecture** - Use only what you need
- **🔄 Alpha-Resilient** - Isolate API changes to adapter layer
- **🧪 Testable** - Mock interfaces for unit testing
- **📚 Library-First** - Build reusable components

---

## 📦 Repository Structure

### Platform Layer (01-xx)

| Repository | Description | Status |
|------------|-------------|--------|
| [**01-platform-core**](https://github.com/Argonath-Systems/01-platform-core) | Root Maven POM with shared configuration | ✅ Stable |
| [**01-platform-sdk**](https://github.com/Argonath-Systems/01-platform-sdk) | Core platform interfaces and abstractions | ✅ Stable |

### Adapter Layer (02-adapter-xx)

| Repository | Description | Status |
|------------|-------------|--------|
| [**02-adapter-hytale**](https://github.com/Argonath-Systems/02-adapter-hytale) | Hytale API implementation (ONLY module with Hytale imports) | ⚠️ Alpha |

### Framework Layer (02-05-framework-xx)

| Repository | Description | Status |
|------------|-------------|--------|
| [**02-framework-accessor**](https://github.com/Argonath-Systems/02-framework-accessor) | Platform-agnostic accessor interfaces | ✅ Stable |
| [**02-framework-core**](https://github.com/Argonath-Systems/02-framework-core) | Common utilities (WeightedSelector, RateLimiter, etc.) | ✅ Stable |
| [**03-framework-text-styling**](https://github.com/Argonath-Systems/03-framework-text-styling) | Rich text, i18n, MiniMessage parser | ✅ Stable |
| [**04-framework-condition**](https://github.com/Argonath-Systems/04-framework-condition) | Composable condition evaluation engine | ✅ Stable |
| [**04-framework-npc**](https://github.com/Argonath-Systems/04-framework-npc) | NPC management and dialog system | 🚧 Development |
| [**04-framework-objective**](https://github.com/Argonath-Systems/04-framework-objective) | Quest objective tracking (kill, gather, explore) | ✅ Stable |
| [**05-framework-quest**](https://github.com/Argonath-Systems/05-framework-quest) | Complete quest lifecycle management | ✅ Stable |
| [**05-framework-ui**](https://github.com/Argonath-Systems/05-framework-ui) | User interface framework | 🚧 Development |

### Mod Layer (06-xx)

| Repository | Description | Status |
|------------|-------------|--------|
| [**06-mod-quest-tracker**](https://github.com/Argonath-Systems/06-mod-quest-tracker) | Quest tracking HUD overlay | 📋 Spec Ready |

### Bundles

| Repository | Description | Status |
|------------|-------------|--------|
| [**bundle-core**](https://github.com/Argonath-Systems/bundle-core) | Essential frameworks uber-JAR | ✅ Stable |
| [**bundle-quest**](https://github.com/Argonath-Systems/bundle-quest) | Complete quest system uber-JAR | ✅ Stable |

---

## 🚀 Quick Start

### For Players

1. **Download Bundles** from CurseForge:
   - [Mithril Forge - Core Library](https://curseforge.com/hytale/mods/mithril-forge-core) (Required)
   - [The Fellowship - Quest System](https://curseforge.com/hytale/mods/fellowship-quest-system) (Optional)

2. **Install** to `Hytale/UserData/Mods/`

3. **Restart** your Hytale server

### For Developers

**Option 1: Use Bundles (Recommended for most projects)**

```xml
<dependency>
    <groupId>com.argonathsystems.bundle</groupId>
    <artifactId>argonath-core-bundle</artifactId>
    <version>1.0.0-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

**Option 2: Fine-Grained Dependencies**

```xml
<dependency>
    <groupId>com.argonathsystems.framework</groupId>
    <artifactId>accessor-api</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>com.argonathsystems.framework</groupId>
    <artifactId>quest-framework</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>
```

**Build Example Mod:**

```bash
git clone https://github.com/Argonath-Systems/01-platform-core
cd 01-platform-core
mvn clean install
```

---

## 📚 Documentation

- **🌐 [Documentation Website](https://argonath-systems.github.io/00-Argonath-Wiki)** - Main landing page with guides and tutorials
- **📖 [Complete Wiki](https://github.com/Argonath-Systems/00-Argonath-Wiki)** - Comprehensive guides and API reference
- **🏗️ [Architecture Guide](https://argonath-systems.github.io/00-Argonath-Wiki/docs/architecture/overview.html)** - System design and principles
- **🎓 [Quick Start Tutorial](https://argonath-systems.github.io/00-Argonath-Wiki/docs/getting-started/quick-start.html)** - Build your first mod in 5 minutes
- **🧩 [API Reference](https://argonath-systems.github.io/00-Argonath-Wiki/docs/api/)** - Complete API documentation

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    YOUR MOD                             │
│         (Business Logic - Zero Hytale Imports)          │
└────────────────────┬────────────────────────────────────┘
                     │ Uses Interfaces
┌────────────────────▼────────────────────────────────────┐
│              FRAMEWORK LAYER                            │
│  Quest│Objective│Condition│NPC│UI│Storage│Text          │
└────────────────────┬────────────────────────────────────┘
                     │ Uses Accessor API
┌────────────────────▼────────────────────────────────────┐
│              ACCESSOR API (Interfaces Only)             │
│  Player│Entity│Item│World│Event│UI│Command              │
└────────────────────┬────────────────────────────────────┘
                     │ Implemented by
┌────────────────────▼────────────────────────────────────┐
│              HYTALE ADAPTER                             │
│         (ONLY module with Hytale imports)               │
└────────────────────┬────────────────────────────────────┘
                     │ Calls
┌────────────────────▼────────────────────────────────────┐
│              HYTALE SERVER API                          │
└─────────────────────────────────────────────────────────┘
```

This architecture ensures that when Hytale's API changes (and it will during Alpha), only the `02-adapter-hytale` module needs updates. Your business logic remains stable.

---

## 🤝 Contributing

We welcome contributions! See our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Setup

```bash
# Clone the organization's repositories
git clone https://github.com/Argonath-Systems/01-platform-core
git clone https://github.com/Argonath-Systems/02-framework-accessor
# ... clone other repos as needed

# Build all frameworks
cd 01-platform-core
mvn clean install

cd ../02-framework-accessor
mvn clean install

# Or use our justfile (if available)
just build-all
```

### Code Standards

- **Java 25** with preview features
- **Zero Hytale Imports** in framework/mod code (except adapters)
- **JUnit 5** for testing
- **Mockito** for mocking accessor interfaces
- Follow existing code style

---

## 💬 Community & Support

- 🌐 **[Documentation Website](https://argonath-systems.github.io/00-Argonath-Wiki)** - Main hub for all documentation
- 💬 **[Discord Server](https://discord.gg/RK3MtpyH)** - Chat, support, and discussions
- 🐛 **[Issue Tracker](https://github.com/orgs/Argonath-Systems/issues)** - Bug reports and feature requests
- 📖 **[GitHub Discussions](https://github.com/orgs/Argonath-Systems/discussions)** - Q&A and ideas
- 📚 **[Wiki Repository](https://github.com/Argonath-Systems/00-Argonath-Wiki)** - Documentation source

---

## 📄 License

All Argonath Systems projects are licensed under the [MIT License](LICENSE), making them free and open-source.

Bundles distributed on CurseForge may include optional monetization features while maintaining free access to all core functionality.

---

## 🌐 Ecosystem

Part of the larger **Lord of the Tales** project - a Lord of the Rings themed server implementation for Hytale.

- **Main Project:** [Lord of the Tales](https://github.com/LordOfTheTales)
- **Web UI Editor:** [HyQuestUI](https://github.com/HyQuestUI)
- **UI Library:** [HyUI](https://github.com/HyUI)

---

## 🙏 Acknowledgments

Built with modern Java practices and inspired by proven architectural patterns from enterprise software development.

**Technology Stack:**
- Java 25 (Preview Features)
- Maven 3.9+
- JUnit 5
- Mockito
- SLF4J

---

<div align="center">

**[Get Started](https://argonath-systems.github.io/00-Argonath-Wiki/docs/getting-started/quick-start.html)** • 
**[Documentation](https://argonath-systems.github.io/00-Argonath-Wiki)** • 
**[Discord](https://discord.gg/RK3MtpyH)** • 
**[GitHub](https://github.com/orgs/Argonath-Systems/)**

Made with ⚔️ for the Hytale community

</div>
