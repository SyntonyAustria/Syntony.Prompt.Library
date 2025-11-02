---
title: "Sys.Kernel AI Prompt-Library Index"
author: "Josef Hahnl"
version: "1.0.0"
created: "2025-10-31"
updated: "2025-10-31"
description: "Interactive index and documentation for all Sys.Kernel AI prompts — architecture, diagnostics, testing, performance, and more."
---

# 🧭 Sys.Kernel AI Prompt-Library Index

> *“Architecture is not a collection of code — it’s a covenant of clarity.”*
> — Josef Hahnl

This library defines the **Sys.Kernel AI Framework Prompts** — a unified system for architectural verification, diagnostics, performance optimization, security, and testing.
Each prompt acts as a specialized **AI domain expert**, working in harmony under the **Sys.Kernel.Master.prompt.v4.0** orchestrator.

---

## 🔗 Shared Terminology

All prompts, analyzers, and architectural documents use a **shared semantic foundation**, defined in:

📘 [Sys.Kernel.Glossary.prompt.md](./Sys.Kernel.Glossary.prompt.md)

This glossary unifies the vocabulary of the Sys.Kernel ecosystem —
ensuring every concept, analyzer rule, and design pattern shares the same meaning.

> **Related Concept:** The *Königsweg* principle underpins all definitions — *Clarity · Strength · Dignity.*

---

## 🧱 Core Orchestrator

| Prompt                                                       | Description                                                                                                                              |
|:------------------------------------------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------- |
| [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) | The master orchestration prompt controlling all framework domains — defines hierarchy, analyzers, output schemas, and CI/CD integration. |

---

## ⚙️ Framework Domains

| Domain                          | Prompt                                                                                             | Purpose                                                                                             |
|:------------------------------- |:-------------------------------------------------------------------------------------------------- |:--------------------------------------------------------------------------------------------------- |
| **Architecture & Performance**  | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)       | Core architectural guidance and performance optimization prompt for Sys.Kernel assemblies.          |
| **Thread Safety & Concurrency** | [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md) | Ensures concurrency correctness, lock-free safety, and async integrity.                             |
| **Better Naming**               | [Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md)                         | Enforces naming conventions, semantic consistency, and `.editorconfig`-aligned identifier design.   |
| **Documentation**               | [Sys.Kernel.Documentation.prompt.md](./Sys.Kernel.Documentation.prompt.md)                         | Defines XML doc, DevDoc, and analyzer-clean documentation standards.                                |
| **NUnit Test Generation**       | [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)         | Automates test creation with NUnit 4.4 attributes, Retry/MaxTime, and analyzer safety.              |
| **Diagnostics & Telemetry**     | [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)         | Implements analyzer-clean EventSource telemetry, OpenTelemetry integration, and structured logging. |
| **Security & Safe Defaults**    | [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md)       | Enforces secure-by-default framework behavior, input validation, and cryptographic safety.          |
| **API Stability & Versioning**  | [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)   | Defines Semantic Versioning, deprecation policies, and CI-based API diff verification.              |
| **Architecture Verification**   | [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md) | Enforces layer rules, dependency boundaries, and build determinism using NetArchTest.               |

---

## 🧩 Analyzer Policy (Global)

All prompts operate under the same analyzer suite and style policy:

- `Microsoft.CodeAnalysis.NetAnalyzers`
- `Meziantou.Analyzer`
- `Roslynator.Analyzers`
- `SonarAnalyzer.CSharp`
- `Microsoft.VisualStudio.Threading.Analyzers`
- `NetArchTest.Rules`
- `AsyncFixer`
- `PublicApiAnalyzers`

**Rule:**

> 0 Warnings.
> No `#pragma` suppressions.
> Analyzer-clean by design.

---

## 🧰 Developer Workflow

1. Start with **SysKernel.Master.prompt.v4.0.md** to define context.
2. Invoke specialized prompts for deeper focus:
   - Architecture → Diagnostics → Performance → Security → Versioning.
3. Collect unified JSON + Markdown results via Master schema.
4. Verify in CI/CD pipeline with Analyzer enforcement.
5. Commit prompt results into `/Prompts/Results` for traceability.

---

## 🧮 Validation Metrics

| Category                | Target |
|:----------------------- |:------ |
| Analyzer Warnings       | 0      |
| CI Runtime              | ≤ 60 s |
| Architecture Violations | 0      |
| API Compatibility       | 100 %  |
| Test Coverage           | ≥ 85 % |
| Documentation Coverage  | 100 %  |
| Confidence Score        | ≥ 0.98 |

---

## 📦 Folder Structure

```
/Prompts/
├── SysKernel.Master.prompt.v4.0.md
├── BeastMode31.prompt.v3.1.1.md
├── framework_architecture_performance_test.prompt.v3.1.md
├── Sys.Kernel.Thread.Safety.Concurrency.prompt.md
├── Sys.Kernel.Better.Naming.prompt.md
├── Sys.Kernel.Documentation.prompt.md
├── Sys.Kernel.Nunit.Test.Generation.prompt.md
├── Sys.Kernel.Diagnostics.Telemetry.prompt.md
├── Sys.Kernel.Security.Safe.Defaults.prompt.md
├── Sys.Kernel.API.Stability.Versioning.prompt.md
└── Architecture_Verification.prompt.v3.1.md
```

---

## 🧭 Philosophy

> “The Sys.Kernel Prompt Library is not a tool — it’s a discipline.
>  Each prompt is a principle, each analyzer a mirror, each build a promise.”
>  — Josef Hahnl / Syntony Austria

---

## 📜 License - Copyright

© 2025 Josef Hahnl — *Syntony Austria* - All rights reserved.

💎 For details, visit [https://syntonyblog.wordpress.com/](https://syntonyblog.wordpress.com/)

📧 Contact: [SyntonyAustria@outlook.com](mailto:SyntonyAustria@outlook.com)

***Clarity · Strength · Dignity — life.exe - Syntony - #syntony - #LifeDotExe***

---