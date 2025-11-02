<!--- ***************************************************************************************************************************************************************** --->
<!--- <copyright file="README.md" company="J.P.Hahnl"> --->
<!---     Copyright © 2017 - 2025 by Josef Hahnl — Syntony Austria — All rights reserved. --->
<!--- </copyright> --->
<!--- <author>Hahnl - hahnl</author> --->
<!--- <email>SyntonyAustria@outlook.com</email> --->
<!--- <date>02.11.2025 11:41:10</date> --->
<!--- <information solution="Syntony.Prompt.Library" project="Miscellaneous Files" framework="<unknown>" kind="{66A2671D-8FB5-11D2-AA7E-00C04F688DDE}is unknown"> --->
<!---     <file type=".md" created="02.11.2025 09:44:04" modified="02.11.2025 11:41:10" lastAccess="02.11.2025 11:41:10"> --->
<!---         D:\Syntony\CommonProperties\Prompts\README.md --->
<!---     </file> --->
<!---     <lineStatistics total="179" contentLines="128" blankLines ="51" codeLines="128" codeRatio="71.51 %" allCommentLines="15" commentLines="15" headerLines="15"/> --->
<!---     <language>MARKDOWN</language> --->
<!--- </information> --->
<!--- ***************************************************************************************************************************************************************** --->
# 🧠 Sys.Kernel Framework

**A Unified Architecture for C# 13 / .NET 9**
*Built with Clarity · Strength · Dignity*

---

![Syntony Framework — Clarity · Strength · Dignity](./Assets/Syntony.png)

---

## 🌌 Vision

**Sys.Kernel** is not just a framework — it’s a principle.
It redefines how .NET systems are structured, verified, and evolved.
Every layer, every analyzer, every build step serves one goal:

> **To bring discipline, determinism, and dignity back to software architecture.**

This repository contains both the **Sys.Kernel framework** itself and the **AI prompt library** that designs, verifies, and documents it — an end-to-end ecosystem for next-generation C# development.

---

## 🧱 Core Concept

Sys.Kernel is a *layered, analyzer-clean, runtime-verified framework* written for **C# 13 / .NET 9**.

### Architectural Model

```
Sdk → Core → Runtime → Diagnostics → Development
                ↑
             (Tests)
```

| Layer                  | Description                                                                                                                                                     |
|:---------------------- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Kernel.Sdk**         | The self-describing SDK layer. Defines attributes, constants, exceptions, and T4/MSBuild-generated metadata. Serves as the interface to the build and compiler. |
| **Kernel.Core**        | Extends Sdk with functional primitives, immutables, and runtime-safe abstractions.                                                                              |
| **Kernel.Runtime**     | Execution engine of Sys.Kernel — service hosting, configuration, dependency injection, and lifecycle management.                                                |
| **Kernel.Diagnostics** | Logging, tracing, EventSource, and OpenTelemetry integration.                                                                                                   |
| **Kernel.Development** | Analyzers, templates, and tooling for VS and CI/CD environments.                                                                                                |
| **Kernel.Tests**       | Verification suite for architecture, performance, security, and stability.                                                                                      |

---

## ⚙️ Technology Stack

- **Language:** C# 13
- **Framework:** .NET 9
- **Build System:** MSBuild + deterministic builds
- **Testing:** NUnit 4.4
- **Code Analysis:**
  - `Meziantou.Analyzer`
  - `Microsoft.CodeAnalysis.NetAnalyzers`
  - `Roslynator.Analyzers`
  - `SonarAnalyzer.CSharp`
  - `NetArchTest.Rules`
  - `AsyncFixer`
  - `PublicApiAnalyzers`

All projects must compile with **0 analyzer warnings**.
No `#pragma` suppressions — ever.

---

## 🧩 Included Prompts

This repository also includes the **Sys.Kernel AI Prompt Library** — a structured set of domain-specific prompts that orchestrate architecture, diagnostics, and framework evolution using AI-assisted analysis.

| Prompt                                                                                             | Purpose                                                         |
|:-------------------------------------------------------------------------------------------------- |:--------------------------------------------------------------- |
| [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)                                       | Master orchestration prompt integrating all sub-domains.        |
| [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md) | Validates layering, dependencies, and modular integrity.        |
| [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)   | Enforces SemVer, API stability, and changelog compliance.       |
| [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md)       | Defines secure-by-default patterns and cryptography standards.  |
| [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)         | Establishes structured EventSource telemetry and observability. |
| [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)         | Generates NUnit 4.4 tests with retry/timeouts.                  |
| [Sys.Kernel.Documentation.prompt.md](./Sys.Kernel.Documentation.prompt.md)                         | Enforces XML + DevDoc consistency.                              |
| [Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md)                         | Governs identifier and naming consistency.                      |
| [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md) | Ensures concurrency correctness and lock-free safety.           |

A complete overview is available in the
📖 [Sys.Kerne.Prompt.Library.Index.prompt.md](./Sys.Kerne.Prompt.Library.Index.prompt.md)

---

## 🧮 CI/CD Integration

Every commit is automatically verified via GitHub Actions:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Build
        run: dotnet build --configuration Release --deterministic
      - name: Test
        run: dotnet test --filter Category!=Integration
      - name: Analyzer Validation
        run: dotnet format analyzers --verify-no-changes
      - name: Architecture Rules
        run: dotnet test --filter Category=Architecture
```

---

## 🧠 Design Principles

1. **Analyzer-Clean by Design**
   Every commit is a promise of quality.
   Warnings are signals of broken clarity.

2. **Self-Describing Architecture**
   Build metadata and SDK generation ensure transparency between the developer, build system, and runtime.

3. **Runtime Minimalism**
   Each layer serves one purpose — no reflection magic, no hidden coupling.

4. **Deterministic Builds**
   Every artifact can be reproduced exactly, ensuring consistency across environments.

5. **The Königsweg**

   - **Clarity** → Know what your code means.
   - **Strength** → Make it resilient, measurable, and testable.
   - **Würde (Dignity)** → Build with intention and respect for complexity.

---

## 🧭 Philosophy

> “A framework should not just run — it should *reveal* its structure.
>  Sys.Kernel is a living mirror of the system that builds it.”
>  — *Josef Hahnl, Syntony Austria*

---

## 🔗 Shared Terminology

Sys.Kernel maintains a **shared glossary** that defines its core terms, principles, and analyzer language.

📘 See [Sys.Kernel.Glossary.prompt.md](./Sys.Kernel.Glossary.prompt.md)

It ensures linguistic and philosophical coherence across prompts, analyzers, and documentation —
bridging AI semantics and human clarity.

> *“Meaning precedes precision.”* — *Sys.Kernel Design Philosophy*

---

## 📜 License - Copyright

© 2025 Josef Hahnl — *Syntony Austria* - All rights reserved.

💎 For details, visit [https://syntonyblog.wordpress.com/](https://syntonyblog.wordpress.com/)

📧 Contact: [SyntonyAustria@outlook.com](mailto:SyntonyAustria@outlook.com)

***Clarity · Strength · Dignity — life.exe - Syntony - #syntony - #LifeDotExe***

---