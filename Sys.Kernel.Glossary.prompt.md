---
title: "Sys.Kernel Framework Glossary"
author: "Josef Hahnl"
version: "1.0.0"
tags: ["Glossary", "Terminology", "Reference", "Documentation", "Sys.Kernel", "C# 13", ".NET 9"]
created: "2025-11-01"
updated: "2025-11-01"
description: "The authoritative glossary defining all terminology, concepts, and patterns used throughout the Sys.Kernel AI Prompt Library and framework implementation. Serves as the single source of truth for semantic consistency."
---

# 📖 Sys.Kernel Framework Glossary

> *"Clarity begins with shared language. Every term carries meaning; every pattern reflects intention.  
> Order begins with shared meaning."*  
> — Josef Hahnl, Syntony Austria

This glossary defines the **canonical terminology** used across all Sys.Kernel prompts, codebase, and documentation.  
When terms conflict or require clarification, this document serves as the **authoritative reference**.

**Purpose:**
- Ensure semantic consistency across all framework components
- Provide quick reference for developers and AI prompts
- Serve as the semantic backbone for architecture, performance, testing, and documentation
- Enable bidirectional traceability between concepts and implementations

---

## 🎯 How to Use This Glossary

### Structure
The glossary is organized into thematic sections:
1. **Quick Reference Table** - Concise definitions for rapid lookup
2. **Detailed Definitions** - In-depth explanations with examples, anti-patterns, and code samples
3. **Cross-References** - Links to related terms and primary prompts

### Navigation
- Use the Quick Reference Table for fast lookups
- Follow hyperlinks to detailed definitions for comprehensive understanding
- Check Primary Prompt references for authoritative implementation guidance
- Review cross-references to understand related concepts

### Conventions
- **Bold terms** are defined entries
- *Italic text* represents philosophical concepts
- `Code blocks` show implementation examples
- ✅ indicates correct patterns
- ❌ indicates anti-patterns

---

## 📋 Quick Reference Table

Core terms with concise definitions and prompt references:

| Term | Definition | Primary Prompt |
|:--|:--|:--|
| **[Königsweg](#königsweg)** | Framework philosophy: *Clarity · Strength · Dignity* | [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) |
| **[Klarheit](#klarheit-clarity)** | Code self-documents its intent and architecture | [Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md) |
| **[Stärke](#stärke-strength)** | Resilient, performant, deterministic systems | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[Würde](#würde-dignity)** | Intentional design respecting maintainers | All prompts |
| **[Analyzer-Clean](#analyzer-clean)** | Zero warnings from all configured analyzers | [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) |
| **[Analyzer Discipline](#analyzer-discipline)** | Analyzers are binding, not advisory | [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) |
| **[Layered Architecture](#layered-architecture)** | Strict hierarchical dependency model: Sdk→Core→Runtime→Diagnostics | [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md) |
| **[SDK Foundation](#sdk-foundation)** | Build-time metadata layer (Kernel.Sdk) | [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md) |
| **[Null Object Pattern](#null-object-pattern)** | Intentional emptiness with deterministic no-op behavior | [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md) |
| **[Deterministic Build](#deterministic-build)** | Byte-identical outputs from identical inputs | [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) |
| **[Runtime Determinism](#runtime-determinism)** | Identical inputs produce identical runtime results | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[AAA Pattern](#aaa-pattern)** | Arrange-Act-Assert test structure | [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md) |
| **[Test Categories](#test-categories)** | Classification for CI/CD filtering (Short, Architecture, Performance, etc.) | [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md) |
| **[Secure-by-Default](#secure-by-default)** | Default state is secure; explicit opt-out required | [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md) |
| **[Immutable Core](#immutable-core)** | Shared data read-only after construction | [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md) |
| **[STRIDE](#stride-threat-model)** | Threat categorization framework | [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md) |
| **[GC Pressure](#gc-pressure)** | Frequency and volume of garbage collection | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[Hot Path](#hot-path)** | Performance-critical frequently-executed code | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[AOT-Friendly](#aot-friendly)** | Compatible with Ahead-of-Time compilation | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[EventSource](#eventsource)** | Structured high-performance ETW logging | [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md) |
| **[EventSource Discipline](#eventsource-discipline)** | Analyzer-clean structured telemetry | [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md) |
| **[ActivitySource](#activitysource)** | OpenTelemetry distributed tracing | [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md) |
| **[Structured Logging](#structured-logging)** | Message templates with typed parameters | [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md) |
| **[SemVer](#semver-semantic-versioning)** | MAJOR.MINOR.PATCH versioning scheme | [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md) |
| **[Semantic Version Integrity](#semantic-version-integrity)** | SemVer with PublicApiAnalyzer verification | [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md) |
| **[Public API Surface](#public-api-surface)** | All public/protected types and members | [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md) |
| **[Confidence Score](#confidence-score)** | AI analysis certainty (0.0-1.0) | [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md) |
| **[Thread Safety Principle](#thread-safety-principle)** | Lock-free, idempotent, async-safe resources | [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md) |
| **[Lock Hierarchy](#lock-hierarchy)** | Global lock ordering to prevent deadlocks | [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md) |
| **[Lock-Free](#lock-free)** | Atomic operations instead of locks | [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md) |
| **[Member Ordering](#member-ordering)** | 11-step type member declaration sequence | [Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md) |
| **[EditorConfig Compliance](#editorconfig-compliance)** | Adherence to project-wide style rules | [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md) |
| **[XML Documentation](#xml-documentation)** | Structured IntelliSense comments | [Sys.Kernel.Documentation.prompt.md](./Sys.Kernel.Documentation.prompt.md) |
| **[DevDoc](#devdoc)** | Internal maintainer documentation | [Sys.Kernel.Documentation.prompt.md](./Sys.Kernel.Documentation.prompt.md) |

---

## 🎯 Core Philosophy Terms

### Königsweg
**Origin:** German, "The Royal Way" or "King's Path"  
**Etymology:** From your book *"Klarheit · Stärke · Würde: Auf dem Königsweg"*

**Definition:**  
The foundational philosophy of Sys.Kernel, embodying three inseparable core principles that guide every architectural, performance, and quality decision:

- **Klarheit (Clarity):** Code and architecture that reveals intent without ambiguity
- **Stärke (Strength):** Resilient, performant, and deterministic systems
- **Würde (Dignity):** Respect for complexity, intentional design, and professional craftsmanship

**Usage Context:**  
Referred to throughout all prompts as the ultimate decision-making principle. When trade-offs arise, Königsweg provides the framework for resolution.

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**Example Application:**
> "This refactoring follows the Königsweg principle by:  
> - Making the dependency chain explicit (Clarity)  
> - Removing allocations from the hot path (Strength)  
> - Maintaining API elegance and backward compatibility (Würde)"

**See Also:** [Klarheit](#klarheit-clarity), [Stärke](#stärke-strength), [Würde](#würde-dignity)

---

### Klarheit (Clarity)

**Definition:**  
The principle that code should be **self-documenting** and **architecturally transparent**. Every identifier, every layer boundary, and every API contract should reveal its purpose without requiring deep investigation or external documentation.

**Core Tenet:**  
*"If you need a comment to explain what the code does, the code is unclear."*

**Manifestations in Sys.Kernel:**
- Clear naming conventions (no abbreviations unless domain-standard like `IO`, `XML`, `CPU`)
- Explicit dependency graphs with zero circular references
- Self-describing SDK layer with build-time metadata generation
- XML documentation that **enhances** understanding, not replaces it
- Layered architecture with unambiguous boundaries
- Type names that reveal their responsibility

**Anti-Patterns (Violations of Klarheit):**
- Hidden coupling through static mutable state
- Magic numbers or undocumented constants
- Ambiguous method names (`Process()`, `Handle()`, `DoWork()`)
- Implicit dependencies (reflection-based service location)
- Cryptic abbreviations (`ProcessMsgQFast()`)
- Over-clever code that requires mental gymnastics

**Metrics:**
- Can a new developer understand the code path in < 5 minutes?
- Are dependencies explicit in constructors/method signatures?
- Does the type name match its actual responsibility?

**Primary Prompts:**  
[Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md)  
[Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md)

**Example - Unclear vs. Clear:**
```csharp
// ❌ Lacks Klarheit
public class Handler
{
    public void Process(object data) 
    {
        var x = Config.Get("timeout");
        // ... what does this handle?
    }
}

// ✅ Embodies Klarheit
public sealed class ConfigurationReloadHandler
{
    private readonly TimeSpan _reloadTimeout;
    
    public ConfigurationReloadHandler(TimeSpan reloadTimeout)
    {
        _reloadTimeout = reloadTimeout;
    }
    
    public void HandleReloadRequest(ConfigurationReloadRequest request)
    {
        // Intent is immediately clear
    }
}
```

**See Also:** [Better Naming](#member-ordering), [SDK Foundation](#sdk-foundation)

---

### Stärke (Strength)

**Definition:**  
The principle that systems must be **robust under stress**, **performant under load**, and **deterministic in behavior**. Strength is measured by resilience and consistency, not just initial correctness.

**Core Tenet:**  
*"Strong systems fail gracefully and perform predictably, even at their limits."*

**Manifestations in Sys.Kernel:**
- **Zero-allocation hot paths** using `Span<T>` and `stackalloc`
- **Deterministic build outputs** (byte-for-byte reproducibility)
- **Thread-safe concurrent operations** without hidden race conditions
- **Graceful degradation** under resource constraints
- **Comprehensive test coverage** (≥85% with edge cases)
- **Performance regression detection** in CI/CD
- **Memory leak prevention** through proper disposal patterns

**Quantitative Metrics:**
| Metric | Target | Measurement Tool |
|:---|:---|:---|
| GC Pressure | Low (< 1% CPU) | PerfView, dotMemory |
| Lock Contention | None | ETW, ThreadPool monitoring |
| Memory Leaks | Zero | dotMemory, leak detection tests |
| Performance Regression | ≤ 2% | BenchmarkDotNet baselines |
| Test Coverage | ≥ 85% | Coverlet, dotCover |
| Uptime | 99.9% | Telemetry, health checks |

**Anti-Patterns (Violations of Stärke):**
- Unhandled exceptions that crash the process
- Hidden allocations in hot paths
- Blocking I/O on thread pool threads
- Unbounded collection growth
- No retry logic for transient failures
- Performance regressions merged to main

**Primary Prompts:**  
[Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)  
[Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md)

**Example - Weak vs. Strong:**
```csharp
// ❌ Lacks Stärke (allocates, not thread-safe, no error handling)
public class Cache
{
    private Dictionary<string, string> _data = new();
    
    public string Get(string key)
    {
        return _data[key]; // Throws if key missing
    }
}

// ✅ Embodies Stärke (concurrent, graceful, no allocations in hot path)
public sealed class ThreadSafeCache
{
    private readonly ConcurrentDictionary<string, string> _data = new();
    
    public bool TryGet(string key, [NotNullWhen(true)] out string? value)
    {
        return _data.TryGetValue(key, out value);
    }
    
    public string GetOrAdd(string key, Func<string, string> factory)
    {
        return _data.GetOrAdd(key, factory);
    }
}
```

**See Also:** [GC Pressure](#gc-pressure), [Hot Path](#hot-path), [Thread Safety](#thread-safety-principle)

---

### Würde (Dignity)

**Definition:**  
The principle that even in the face of complexity, design must remain **intentional**, **respectful**, and **elegant**. Code written with dignity acknowledges the humans who will maintain it, the systems that depend on it, and the users who trust it.

**Core Tenet:**  
*"Every line of code is a message to future maintainers. Write with respect."*

**Manifestations in Sys.Kernel:**
- **Null Object Pattern:** "Even nothingness should act with dignity"
- **Graceful error handling** with actionable messages
- **API design** that guides users toward correct usage (pit of success)
- **Documentation** that respects the reader's intelligence
- **No suppressions** without understanding root cause
- **Thoughtful abstractions** that hide complexity without magic
- **Professional naming** that honors domain language

**Philosophical Aspects:**
- Dignity toward **users:** APIs that prevent misuse
- Dignity toward **maintainers:** Code that teaches as it's read
- Dignity toward **complexity:** Acknowledging hard problems honestly
- Dignity toward **failure:** Errors that help rather than frustrate

**Anti-Patterns (Violations of Würde):**
- Suppressing analyzer warnings with `#pragma` without investigation
- "Quick fixes" that introduce technical debt
- Copy-paste code without comprehension
- Treating exceptions as control flow
- Cryptic error messages (`Error: -1`)
- APIs that invite misuse (unclear ownership, hidden state)
- Condescending comments (`// Obviously, this...`)

**Primary Prompts:**  
All prompts embody this principle implicitly, especially:  
[Sys.Kernel.Documentation.prompt.md](./Sys.Kernel.Documentation.prompt.md)  
[Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md)

**Example - Undignified vs. Dignified:**
```csharp
// ❌ Lacks Würde
public class Thing
{
    public void DoIt(string x) 
    {
        try 
        {
            // stuff
        } 
        catch 
        {
            // ignore
        }
    }
}

// ✅ Embodies Würde
/// <summary>
/// Reloads the service configuration from the specified source.
/// </summary>
/// <param name="configurationSource">The source from which to load configuration.</param>
/// <exception cref="ArgumentNullException">Thrown when <paramref name="configurationSource"/> is null.</exception>
/// <exception cref="ConfigurationLoadException">
/// Thrown when the configuration format is invalid or the source is inaccessible.
/// Includes detailed error information for troubleshooting.
/// </exception>
/// <remarks>
/// This operation is thread-safe and can be called concurrently.
/// Existing services continue using cached configuration during reload.
/// </remarks>
public void ReloadConfiguration(IConfigurationSource configurationSource)
{
    ArgumentNullException.ThrowIfNull(configurationSource);
    
    try
    {
        var newConfig = configurationSource.Load();
        ApplyConfiguration(newConfig);
    }
    catch (IOException ioEx)
    {
        throw new ConfigurationLoadException(
            $"Failed to access configuration source '{configurationSource.Name}'. " +
            "Ensure the source is accessible and the application has read permissions.",
            ioEx);
    }
}
```

**See Also:** [Null Object Pattern](#null-object-pattern), [XML Documentation](#xml-documentation)

---

## 🧱 Architectural Terms

### Analyzer-Clean

**Definition:**  
Code that compiles with **zero warnings** from all configured Roslyn analyzers and produces no style violations in `.editorconfig`. This is not a goal—it's a **mandatory requirement** across the entire Sys.Kernel framework.

**Requirement Level:** **MANDATORY** (CI/CD fails on any violation)

**Philosophy:**  
> "Analyzer warnings are not suggestions—they are violations of architectural principles."

**Covered Analyzers:**
| Analyzer | Focus Area |
|:---|:---|
| `Meziantou.Analyzer` | Best practices, performance, correctness |
| `Microsoft.CodeAnalysis.NetAnalyzers` | Framework usage, security, reliability |
| `Roslynator.Analyzers` | Code quality, readability, maintainability |
| `SonarAnalyzer.CSharp` | Bug detection, code smells, security |
| `AsyncFixer` | Async/await anti-patterns |
| `Microsoft.VisualStudio.Threading.Analyzers` | Threading correctness, deadlock prevention |
| `NetArchTest.Rules` | Architectural boundary enforcement |
| `Microsoft.CodeAnalysis.PublicApiAnalyzers` | API surface tracking |

**Enforcement Mechanisms:**
1. **Build-time:** `TreatWarningsAsErrors=true` in all projects
2. **CI/CD:** Pipeline fails on any analyzer warning
3. **Pre-commit:** Git hooks validate analyzer cleanliness
4. **Code review:** Automated checks block PR merge

**Prohibition:**  
❌ **No** `#pragma warning disable` suppressions  
❌ **No** `.editorconfig` severity overrides to hide warnings  
❌ **No** "temporary" warning suppressions

**Exception Process:**  
If an analyzer produces a false positive:
1. Document the reasoning thoroughly
2. File an issue with the analyzer maintainer
3. Add to global suppression file (`.globalconfig`) with justification
4. Review suppression quarterly

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**Example:**
```csharp
// ❌ NOT Analyzer-Clean
public async Task<string> GetDataAsync()
{
    return await File.ReadAllTextAsync("data.txt"); // CA2007: ConfigureAwait missing
}

// ✅ Analyzer-Clean
public async Task<string> GetDataAsync()
{
    return await File.ReadAllTextAsync("data.txt").ConfigureAwait(false);
}
```

**Validation Command:**
```bash
dotnet build --configuration Release --warnaserror
dotnet format analyzers --verify-no-changes
```

**See Also:** [Analyzer Discipline](#analyzer-discipline), [EditorConfig Compliance](#editorconfig-compliance)

---

### Analyzer Discipline

**Definition:**  
The Sys.Kernel principle that analyzers are **binding constraints**, not advisory suggestions. Every analyzer warning represents a violation of architectural, performance, or quality principles.

**Core Tenet:**  
*"If the analyzer says it's wrong, it is wrong—regardless of whether the code 'works'."*

**Rationale:**
- Analyzers encode decades of .NET best practices
- Warnings today become bugs tomorrow
- Suppressing warnings hides technical debt
- Clean code enables better AI analysis and generation

**Cultural Aspects:**
- Developers take **pride** in zero-warning code
- Code reviews focus on **why** code is correct, not whether it compiles
- New analyzer rules trigger **learning sessions**, not suppression
- Framework evolution includes **analyzer upgrades**

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**See Also:** [Analyzer-Clean](#analyzer-clean), [Königsweg](#königsweg)

---

### Layered Architecture

**Definition:**  
Sys.Kernel's strict hierarchical structure where each layer depends **only** on layers below it—never above or sideways. This creates a **directed acyclic graph** (DAG) of dependencies, enforced at build time and validated in CI.

**Architectural Principle:**  
*"Dependencies flow downward, abstractions bubble upward."*

**Layer Hierarchy:**
```
┌─────────────────────────────────────────┐
│           Development Layer             │  (Tooling, excluded from release)
│      Syntony.Kernel.Development       │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│          Diagnostics Layer              │  (Observability)
│     Syntony.Kernel.Diagnostics        │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│           Runtime Layer                 │  (Execution engine)
│      Syntony.Kernel.Runtime           │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│            Core Layer                   │  (Primitives)
│       Syntony.Kernel.Core             │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│          SDK Foundation                 │  (Metadata)
│        Syntony.Kernel.Sdk             │
└─────────────────────────────────────────┘

              ┌──────────────┐
              │    Tests     │  (Observer, no dependents)
              │ Kernel.Tests │
              └──────────────┘
```

**Layer Definitions:**

| Layer | Namespace Prefix | Dependencies | Purpose | Contents |
|:---|:---|:---|:---|:---|
| **Kernel.Sdk** | `Syntony.Kernel.Sdk` | BCL only | Build-time metadata | Attributes, constants, base exceptions, T4 outputs |
| **Kernel.Core** | `Syntony.Kernel.Core` | Sdk | Runtime primitives | Immutables, value objects, functional constructs |
| **Kernel.Runtime** | `Syntony.Kernel.Runtime` | Core | Execution engine | DI, configuration, service hosting, lifecycle |
| **Kernel.Diagnostics** | `Syntony.Kernel.Diagnostics` | Runtime | Observability | EventSource, logging, OpenTelemetry |
| **Kernel.Development** | `Syntony.Kernel.Development` | All (internal) | Developer tooling | Analyzers, templates, VS integration |
| **Kernel.Tests** | `Syntony.Kernel.Tests` | All (observer) | Validation | Unit tests, integration tests, NetArchTest |

**Enforcement Mechanisms:**
1. **NetArchTest rules** validate dependencies in CI
2. **Project references** explicitly define allowed dependencies
3. **Namespace conventions** make violations obvious
4. **Architecture tests** fail build on circular references

**Benefits:**
- **Compile-time safety:** Invalid references prevented by MSBuild
- **Clear mental model:** Developers know where code belongs
- **Testability:** Lower layers testable without upper layers
- **Modularity:** Layers can be updated independently (within SemVer)

**Primary Prompt:** [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md)

**Validation Example:**
```csharp
[Test, Category(TestCategory.Architecture)]
public void Core_ShouldOnlyDependOn_Sdk()
{
    var result = Types.InAssembly("Syntony.Kernel.Core")
        .Should().OnlyHaveDependenciesOn(
            "Syntony.Kernel.Sdk",
            "System",
            "System.*")
        .GetResult();
    
    Assert.That(result.IsSuccessful, Is.True);
}
```

**See Also:** [SDK Foundation](#sdk-foundation), [Architecture Verification Prompt](./Sys.Kernel.Architecture.Verification.prompt.md)

---

### SDK Foundation

**Definition:**  
The `Kernel.Sdk` assembly serves as the **self-describing metadata layer** containing all attributes, constants, identifiers, and base exceptions used by the framework. It is the **interface to the build system** and the **contract between developer and compiler**.

**Architectural Position:**  
The SDK is the **bottom of the dependency chain**—all other layers depend on it, but it depends only on BCL.

**Purpose:**
1. **Build-time contract** between compiler and framework
2. **T4/Source Generator integration point** for compile-time code generation
3. **Zero runtime dependencies** (only `System.*` from BCL)
4. **Defines the interface** to the framework (what developers import)
5. **Attribute authority** (all framework attributes originate here)

**Key Principle:**  
> "All attributes and base types **originate** from Sdk; other layers **extend** but **never redefine** them."

**Contents:**
| Category | Examples |
|:---|:---|
| **Attributes** | `[KernelComponent]`, `[NullObject]`, `[PerformanceCritical]` |
| **Constants** | `KernelVersion`, `FrameworkName`, error codes |
| **Base Exceptions** | `KernelException`, `ConfigurationException` |
| **Identifiers** | Component IDs, event IDs, diagnostic codes |
| **T4 Templates** | Compile-time metadata generation |

**Primary Prompt:** [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md)

**Example:**
```csharp
// ========================================
// Kernel.Sdk: Defines the attribute
// ========================================
namespace Syntony.Kernel.Sdk;

[AttributeUsage(AttributeTargets.Class, Inherited = false)]
public sealed class KernelComponentAttribute : Attribute
{
    public string ComponentId { get; }
    
    public KernelComponentAttribute(string componentId)
    {
        ArgumentException.ThrowIfNullOrWhiteSpace(componentId);
        ComponentId = componentId;
    }
}

// ========================================
// Kernel.Core: Extends usage
// ========================================
namespace Syntony.Kernel.Core;

[KernelComponent("ServiceRegistry")]
public sealed class ServiceRegistry 
{
    // Implementation
}
```

**Anti-Pattern:**
```csharp
// ❌ WRONG: Redefining attributes in Core
namespace Syntony.Kernel.Core;

// This violates SDK Foundation principle
public sealed class CoreComponentAttribute : Attribute { }
```

**See Also:** [Layered Architecture](#layered-architecture)

---

### Null Object Pattern

**Definition:**  
A design pattern where every interface or abstract type has a corresponding **"Null" implementation** that provides safe, intentional, analyzer-clean no-op behavior. This eliminates null checks throughout the codebase.

**Philosophy:**  
> "Even nothingness should act with dignity." — Sys.Kernel Design Principle

**Purpose:**
1. **Eliminate null checks** in client code
2. **Provide predictable behavior** in absence of real implementation
3. **Enforce intentionality**—`null` is ambiguous; `NullLogger` is explicit
4. **Enable composition** without branching logic
5. **Satisfy analyzer requirements** (nullable reference types)

**Implementation Rules:**
1. Null Object classes are **sealed** (no inheritance allowed)
2. Implemented as **singleton** via static `Instance` property
3. Marked with `[NullObject]` attribute from SDK
4. **Private constructor** prevents external instantiation
5. All methods are **no-op** but **safe to call**

**Primary Prompt:** [Sys.Kernel.Architecture.Verification.prompt.md](./Sys.Kernel.Architecture.Verification.prompt.md)

**Complete Example:**
```csharp
// ========================================
// Interface definition
// ========================================
public interface ILogger
{
    void Log(LogLevel level, string message);
    void LogException(Exception exception);
}

// ========================================
// Null Object implementation
// ========================================
[NullObject]
public sealed class NullLogger : ILogger
{
    /// <summary>
    /// Singleton instance of the null logger.
    /// </summary>
    public static readonly ILogger Instance = new NullLogger();
    
    // Private constructor prevents external instantiation
    private NullLogger() { }
    
    /// <summary>
    /// No-op: logging is silently ignored.
    /// </summary>
    public void Log(LogLevel level, string message) 
    { 
        // Intentional no-op
    }
    
    /// <summary>
    /// No-op: exception logging is silently ignored.
    /// </summary>
    public void LogException(Exception exception) 
    { 
        // Intentional no-op
    }
}

// ========================================
// Usage - always safe, no null checks
// ========================================
public class ServiceHost
{
    private readonly ILogger _logger;
    
    public ServiceHost(ILogger? logger = null)
    {
        // Null coalescing ensures we always have a valid logger
        _logger = logger ?? NullLogger.Instance;
    }
    
    public void Start()
    {
        // Safe to call without null check
        _logger.Log(LogLevel.Information, "Service starting");
        
        // No branching needed
        ProcessRequest();
    }
    
    private void ProcessRequest()
    {
        // Logger is never null
        _logger.Log(LogLevel.Debug, "Processing request");
    }
}
```

**NetArchTest Validation:**
```csharp
[Test, Category(TestCategory.Architecture)]
public void NullObject_Classes_Must_Be_Sealed_And_Singleton()
{
    var result = Types.InCurrentDomain()
        .That().HaveNameStartingWith("Null")
        .Or().HaveCustomAttribute(typeof(NullObjectAttribute))
        .Should().BeSealed()
        .And().HaveStaticFieldOfType("Instance")
        .GetResult();
    
    Assert.That(result.IsSuccessful, Is.True, 
        "Null Object pattern violation detected");
}
```

**Benefits:**
| Principle | Benefit |
|:---|:---|
| **Klarheit** | No ambiguous null checks—every call has meaning |
| **Stärke** | Predictable runtime paths, fewer exceptions |
| **Würde** | Even absence behaves gracefully—intentional silence |

**Design Note:**  
The Null Object Pattern is now an **architectural invariant** of Sys.Kernel:  
> Every component exists—even when it does nothing.

**See Also:** [Würde](#würde-dignity), [Analyzer-Clean](#analyzer-clean)

---

### Deterministic Build

**Definition:**  
A build process that produces **byte-identical outputs** when given identical inputs, regardless of build environment, timestamp, or machine-specific settings.

**Purpose:**
- **Reproducible release artifacts** (security auditing)
- **Build verification** (detect tampering)
- **Build caching optimization** (distributed builds)
- **Compliance requirements** (regulatory environments)

**Requirements:**
1. No timestamps embedded in binaries
2. No machine-specific paths in PDB files
3. No GUID generation at build time
4. Consistent assembly ordering
5. Stable file hashes

**Implementation:**
```xml
<PropertyGroup>
  <!-- Enable deterministic compilation -->
  <Deterministic>true</Deterministic>
  
  <!-- CI/CD mode (embeds git commit info) -->
  <ContinuousIntegrationBuild>true</ContinuousIntegrationBuild>
  
  <!-- Embed PDB in assembly -->
  <DebugType>embedded</DebugType>
  
  <!-- Reproducible source paths -->
  <PathMap>$(MSBuildProjectDirectory)=/src/</PathMap>
</PropertyGroup>
```

**Verification:**
```bash
# Build twice and compare
dotnet build --configuration Release
cp bin/Release/net9.0/Kernel.dll build1.dll

dotnet clean
dotnet build --configuration Release
cp bin/Release/net9.0/Kernel.dll build2.dll

# Should be byte-identical
sha256sum build1.dll build2.dll
```

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**See Also:** [Runtime Determinism](#runtime-determinism)

---

### Runtime Determinism

**Definition:**  
Guarantee that **identical inputs produce identical runtime results**, enforced through deterministic builds, reproducible environments, and elimination of non-deterministic operations.

**Scope:**
- Algorithm outputs
- Test results
- Performance characteristics
- Error conditions

**Non-Deterministic Operations to Avoid:**
- `Random` without fixed seed (use `RandomNumberGenerator` or seeded `Random`)
- Unordered dictionary iteration (use `SortedDictionary` or explicit ordering)
- `DateTime.Now` for business logic (use injected `ITimeProvider`)
- Parallel operations without deterministic aggregation
- Reflection without sorted member enumeration

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**Example:**
```csharp
// ❌ Non-deterministic
public int GetRandomValue()
{
    return new Random().Next(); // Different every call
}

// ✅ Deterministic (for testing)
public int GetRandomValue(int seed)
{
    return new Random(seed).Next(); // Reproducible
}

// ✅ Deterministic (for production crypto)
public byte[] GenerateKey()
{
    var key = new byte[32];
    RandomNumberGenerator.Fill(key); // Cryptographically random
    return key;
}
```

**See Also:** [Deterministic Build](#deterministic-build), [Stärke](#stärke-strength)

---

## 🧪 Testing Terms

### AAA Pattern

**Definition:**  
**Arrange-Act-Assert**, the standard structure for all unit tests in Sys.Kernel. This pattern enforces clarity and testability by separating test phases.

**Structure:**
```csharp
[Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]
public void MethodName_Condition_ExpectedBehaviorTest()
{
    // ============================================
    // ARRANGE: Set up test data and dependencies
    // ============================================
    var sut = new SystemUnderTest();
    var input = new InputData("test-value");
    var expectedOutput = new ExpectedResult(42);
    
    // ============================================
    // ACT: Execute the method being tested
    // ============================================
    var actualOutput = sut.MethodUnderTest(input);
    
    // ============================================
    // ASSERT: Verify the outcome
    // ============================================
    Assert.That(actualOutput, Is.Not.Null);
    Assert.That(actualOutput.Value, Is.EqualTo(expectedOutput.Value));
    Assert.Pass(TestMessage.TestPassed);
}
```

**Phase Definitions:**

**1. Arrange:**
- Set up test data (inputs, expected outputs)
- Configure mocks/stubs/fakes
- Initialize system under test (SUT)
- Establish preconditions
- **Keep minimal**—only what's needed for this test

**2. Act:**
- Execute **one** method call (the behavior under test)
- Capture the result
- **Keep single-line** when possible
- **No assertions** in Act section

**3. Assert:**
- Verify postconditions
- Check return values, state changes, side effects
- Use constraint model (see below)
- **Always end with** `Assert.Pass(TestMessage.TestPassed)`

**Requirements:**
1. **Clear separation** between Arrange/Act/Assert (use comments or whitespace)
2. **Single logical assertion** (multiple `Assert.That` calls OK if testing same concept)
3. **Minimal logic** in Arrange—prefer helper methods
4. **Always end with** `Assert.Pass(TestMessage.TestPassed)`
5. **Use constraint model:**
   ```csharp
   Assert.That(actual, Is.EqualTo(expected));        // ✅
   Assert.AreEqual(expected, actual);                 // ❌ Classic model
   ```

**Primary Prompt:** [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

**Anti-Pattern:**
```csharp
// ❌ No clear AAA separation, multiple acts, unclear intent
[Test]
public void Test1()
{
    var x = new Thing();
    x.DoSomething();
    Assert.That(x.Value, Is.EqualTo(5));
    x.DoSomethingElse();
    Assert.That(x.State, Is.EqualTo("done"));
}
```

**See Also:** [Test Categories](#test-categories), [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

---

### Test Categories

**Definition:**  
Classification system for organizing and filtering tests in CI/CD pipelines using the `[Category]` attribute.

**Standard Categories:**
```csharp
public static class TestCategory
{
    /// <summary>Fast unit tests (< 1 second).</summary>
    public const string Short = nameof(Short);
    
    /// <summary>NetArchTest architecture validation.</summary>
    public const string Architecture = nameof(Architecture);
    
    /// <summary>BenchmarkDotNet performance tests.</summary>
    public const string Performance = nameof(Performance);
    
    /// <summary>Cross-component integration tests.</summary>
    public const string Integration = nameof(Integration);
    
    /// <summary>Security and vulnerability tests.</summary>
    public const string Security = nameof(Security);
    
    /// <summary>Thread-safety and concurrency tests.</summary>
    public const string Concurrency = nameof(Concurrency);
    
    /// <summary>API compatibility and versioning tests.</summary>
    public const string Versioning = nameof(Versioning);
    
    /// <summary>Logging and telemetry validation.</summary>
    public const string Diagnostics = nameof(Diagnostics);
}
```

**Usage:**
```csharp
[Test, Category(TestCategory.Performance), MaxTime(30000)]
public void Logging_HasLowAllocationOverhead_Test()
{
    // BenchmarkDotNet performance validation
}

[Test, Category(TestCategory.Security), Retry(TestRetry.Min)]
public void Cryptography_UsesSecureRandomNumberGenerator_Test()
{
    // Security validation
}
```

**CI/CD Filtering:**
```bash
# Run only unit tests
dotnet test --filter "Category=Short"

# Run everything except integration tests
dotnet test --filter "Category!=Integration"

# Run security and architecture tests
dotnet test --filter "Category=Security|Category=Architecture"

# Pre-merge validation (fast tests only)
dotnet test --filter "Category=Short|Category=Architecture"
```

**Pipeline Strategy:**
| Stage | Categories | Timeout | Frequency |
|:---|:---|:---|:---|
| **Pre-commit** | Short | 30s | Every commit |
| **PR validation** | Short, Architecture | 2m | Every PR |
| **Main build** | All except Performance | 5m | Every merge |
| **Nightly** | All including Performance | 30m | Daily |

**Primary Prompt:** [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

**See Also:** [Test Timeouts](#test-timeouts), [AAA Pattern](#aaa-pattern)

---

### Test Timeouts

**Definition:**  
Maximum execution time allowed for different test categories before automatic failure, configured via `[MaxTime]` attribute.

**Standard Timeouts (milliseconds):**
```csharp
public static class TestTimeout
{
    /// <summary>Unit tests: 1 second maximum.</summary>
    public const int UnitTest = 1000;
    
    /// <summary>Integration tests: 5 seconds maximum.</summary>
    public const int IntegrationTest = 5000;
    
    /// <summary>Performance benchmarks: 30 seconds maximum.</summary>
    public const int PerformanceTest = 30000;
    
    /// <summary>Architecture validation: 10 seconds maximum.</summary>
    public const int ArchitectureTest = 10000;
}
```

**Rationale:**
- **Prevent infinite loops** and hangs in test suite
- **Enforce performance discipline** (slow tests indicate problems)
- **Enable fast feedback** in CI/CD
- **Detect regressions** in test execution time

**Usage:**
```csharp
[Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest)]
public void FastOperation_CompletesQuickly_Test()
{
    // Must complete in < 1000ms
}

[Test, Category(TestCategory.Integration), MaxTime(TestTimeout.IntegrationTest)]
public async Task ExternalService_Responds_Test()
{
    // Must complete in < 5000ms
}
```

**Timeout Violations:**
If a test exceeds its timeout:
1. Test **fails immediately** (NUnit kills the test)
2. CI/CD marks build as failed
3. Investigation required before merge
4. Either fix performance or recategorize test

**Primary Prompt:** [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

**See Also:** [Test Categories](#test-categories), [Test Retry Policy](#test-retry-policy)

---

### Test Retry Policy

**Definition:**  
Automatic retry configuration for handling transient test failures using the `[Retry]` attribute.

**Standard Retry Counts:**
```csharp
public static class TestRetry
{
    /// <summary>Minimum retry: 2 attempts (3 total runs).</summary>
    public const int Min = 2;
    
    /// <summary>Maximum retry for flaky tests: 5 attempts.</summary>
    public const int Max = 5;
}
```

**When to Use:**
- ✅ Integration tests with external dependencies
- ✅ Timing-sensitive concurrency tests
- ✅ File system operations (locks, timing)
- ✅ Network I/O (DNS, connection establishment)
- ❌ **Never** for unit tests (indicates poor test design)

**Usage:**
```csharp
[Test, Category(TestCategory.Integration), Retry(TestRetry.Min)]
public async Task ExternalApi_ReturnsValidData_Test()
{
    // May fail transiently due to network
    // Will retry up to 2 times (3 total attempts)
}

[Test, Category(TestCategory.Concurrency), Retry(TestRetry.Max)]
public void ThreadPool_HandlesConcurrentRequests_Test()
{
    // Timing-sensitive, may need multiple attempts
}
```

**Anti-Pattern:**
```csharp
// ❌ Unit test should NOT need retry
[Test, Category(TestCategory.Short), Retry(TestRetry.Min)]
public void Add_TwoNumbers_ReturnsSum_Test()
{
    Assert.That(Calculator.Add(2, 2), Is.EqualTo(4));
}
```

**Philosophy:**  
If a unit test needs retry, it's either:
1. Not a unit test (has external dependencies)
2. Testing non-deterministic behavior
3. Poorly written (race conditions in test code)

**Primary Prompt:** [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

**See Also:** [Test Categories](#test-categories), [Runtime Determinism](#runtime-determinism)

---

### TestMessage Constants

**Definition:**  
Standardized test result messages for consistency across the test suite.

**Standard Messages:**
```csharp
public static class TestMessage
{
    /// <summary>Standard success message for all passing tests.</summary>
    public const string TestPassed = "Test passed successfully";
    
    /// <summary>Test skipped due to unmet preconditions.</summary>
    public const string TestSkipped = "Test skipped: precondition not met";
    
    /// <summary>Test result inconclusive (neither pass nor fail).</summary>
    public const string TestInconclusive = "Test result inconclusive";
}
```

**Mandatory Usage:**  
**Every test must end with:**
```csharp
Assert.Pass(TestMessage.TestPassed);
```

**Rationale:**
- Explicit success signal (not just "didn't throw")
- Consistent test output across entire suite
- Easier CI/CD parsing
- Clear indication test completed all assertions

**Primary Prompt:** [Sys.Kernel.Nunit.Test.Generation.prompt.md](./Sys.Kernel.Nunit.Test.Generation.prompt.md)

**See Also:** [AAA Pattern](#aaa-pattern)

---

## 🔒 Security Terms

### Secure-by-Default

**Definition:**  
Framework design principle where the **default configuration and behavior prioritize security** without requiring explicit hardening by users. Insecure options require explicit opt-in.

**Philosophy:**  
> "Make the right thing the easy thing. Make the wrong thing hard."

**Examples in Sys.Kernel:**
| Component | Secure Default | Insecure Alternative (requires opt-in) |
|:---|:---|:---|
| **File I/O** | `FileShare.Read` | `FileShare.ReadWrite` |
| **HTTP Client** | TLS 1.3 minimum | TLS 1.0/1.1 (disabled) |
| **Random Numbers** | `RandomNumberGenerator` | `Random` (disallowed) |
| **Configuration** | Immutable after load | Mutable (disallowed) |
| **Reflection** | Disabled by default | Whitelist required |
| **Serialization** | Type validation | Unrestricted (disallowed) |
| **Logging** | PII redaction enabled | Raw logging (opt-in) |

**Implementation Pattern:**
```csharp
// ✅ Secure by default
public sealed class FileService
{
    public FileStream OpenFile(string path)
    {
        // Default: read-only, no sharing
        return File.Open(path, FileMode.Open, FileAccess.Read, FileShare.Read);
    }
    
    // Insecure option requires explicit intent
    public FileStream OpenFileUnsafe(string path, FileShare shareMode)
    {
        ArgumentOutOfRangeException.ThrowIfEqual(shareMode, FileShare.ReadWrite);
        // Explicit opt-in required
        return File.Open(path, FileMode.Open, FileAccess.ReadWrite, shareMode);
    }
}
```

**Primary Prompt:** [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md)

**See Also:** [Immutable Core](#immutable-core), [STRIDE](#stride-threat-model)

---

### Immutable Core

**Definition:**  
Architectural principle where **shared data structures are read-only after construction**, eliminating entire classes of concurrency bugs and security vulnerabilities.

**Core Tenet:**  
*"Immutability is the ultimate thread safety."*

**Benefits:**
| Category | Benefit |
|:---|:---|
| **Thread Safety** | No synchronization needed—reads always safe |
| **Security** | Configuration can't be tampered after load |
| **Testing** | Predictable state—no hidden mutations |
| **Performance** | No defensive copying required |
| **Reasoning** | Code behavior independent of call order |

**Implementation Patterns:**

**1. Immutable Records:**
```csharp
// ✅ Immutable configuration
public sealed record DatabaseConfiguration
{
    public required string ConnectionString { get; init; }
    public required int Timeout { get; init; }
    public required bool EnablePooling { get; init; }
}

// Usage
var config = new DatabaseConfiguration
{
    ConnectionString = "...",
    Timeout = 30,
    EnablePooling = true
};
// config.Timeout = 60; // ❌ Compile error - cannot modify
```

**2. Immutable Collections:**
```csharp
// ✅ Immutable list
public ImmutableArray<string> AllowedHosts { get; }

// ✅ Initialization
AllowedHosts = ImmutableArray.Create("localhost", "example.com");

// ❌ Cannot modify
// AllowedHosts.Add("evil.com"); // Compile error
```

**3. Builder Pattern (for complex construction):**
```csharp
public sealed class ConfigurationBuilder
{
    private string? _connectionString;
    private int _timeout = 30;
    
    public ConfigurationBuilder WithConnectionString(string value)
    {
        _connectionString = value;
        return this;
    }
    
    public Configuration Build()
    {
        return new Configuration(_connectionString!, _timeout);
    }
}

public sealed class Configuration
{
    public string ConnectionString { get; }
    public int Timeout { get; }
    
    internal Configuration(string connectionString, int timeout)
    {
        ConnectionString = connectionString;
        Timeout = timeout;
    }
}
```

**Anti-Patterns:**
```csharp
// ❌ Mutable shared state
public static List<string> GlobalCache = new(); // NEVER

// ❌ Public setters on shared objects
public class Configuration
{
    public string ConnectionString { get; set; } // BAD
}
```

**Primary Prompts:**  
[Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md)  
[Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md)

**See Also:** [Thread Safety Principle](#thread-safety-principle), [Stärke](#stärke-strength)

---

### STRIDE Threat Model

**Definition:**  
Security analysis framework categorizing threats into six types, used throughout Sys.Kernel for threat modeling and security testing.

**Acronym:** **S**poofing · **T**ampering · **R**epudiation · **I**nformation Disclosure · **D**enial of Service · **E**levation of Privilege

**Threat Categories with Sys.Kernel Mitigations:**

| Threat | Description | Examples | Sys.Kernel Mitigation |
|:---|:---|:---|:---|
| **Spoofing** | Identity forgery, impersonation | Fake authentication tokens, spoofed sender | Signature validation, certificate pinning, trusted configuration paths |
| **Tampering** | Unauthorized data modification | Modified config files, altered messages | Immutable service collections, integrity checks, read-only defaults |
| **Repudiation** | Denying actions taken | Deleted logs, missing audit trail | ActivityId correlation in all EventSource events, immutable logs |
| **Information Disclosure** | Unauthorized data access | Leaked secrets in logs, exposed PII | PII redaction in structured logging, credential encryption |
| **Denial of Service** | Resource exhaustion | Unbounded queues, memory leaks, CPU spikes | Size limits, circuit breakers, timeout policies, backpressure |
| **Elevation of Privilege** | Unauthorized access escalation | Reflection abuse, code injection | Reflection disabled by default, type whitelisting, least privilege |

**Application in Development:**

**1. Design Phase:**
- Run STRIDE analysis on each component
- Document threats and mitigations
- Update threat model as architecture evolves

**2. Code Review:**
```csharp
// Reviewer asks: "What STRIDE threats does this address?"

// ✅ Addresses Tampering + Information Disclosure
public sealed record SecureConfiguration
{
    [SensitiveData] // Redacted in logs
    public required string ApiKey { get; init; } // Immutable (Tampering)
    
    public required string Endpoint { get; init; }
}
```

**3. Testing:**
```csharp
[Test, Category(TestCategory.Security)]
public void Logging_DoesNotLeakSensitiveData_Test() // Information Disclosure
{
    var config = new SecureConfiguration 
    { 
        ApiKey = "secret-key-12345",
        Endpoint = "https://api.example.com"
    };
    
    var logOutput = CaptureLogOutput(() => _logger.LogConfiguration(config));
    
    Assert.That(logOutput, Does.Not.Contain("secret-key-12345"));
    Assert.That(logOutput, Does.Contain("[REDACTED]"));
}

[Test, Category(TestCategory.Security)]
public void Queue_EnforcesSizeLimit_Test() // Denial of Service
{
    var queue = new BoundedQueue<string>(maxSize: 100);
    
    for (int i = 0; i < 100; i++)
        queue.Enqueue($"Item {i}");
    
    Assert.Throws<QueueFullException>(() => queue.Enqueue("Overflow"));
}
```

**Primary Prompt:** [Sys.Kernel.Security.Safe.Defaults.prompt.md](./Sys.Kernel.Security.Safe.Defaults.prompt.md)

**See Also:** [Secure-by-Default](#secure-by-default), [Test Categories](#test-categories)

---

## ⚡ Performance Terms

### GC Pressure

**Definition:**  
The frequency and volume of garbage collection events caused by heap allocations. High GC pressure degrades performance and increases latency unpredictability.

**Classification:**
| Level | CPU in GC | Gen-0/s | Gen-2/Month | Characteristics |
|:---|:---|:---|:---|:---|
| **Low** | < 1% | < 100 | < 10 | Ephemeral-only, sub-millisecond pauses |
| **Medium** | 1-5% | 100-1000 | 10-100 | Occasional Gen-1, millisecond pauses |
| **High** | > 5% | > 1000 | > 100 | Frequent Gen-2/LOH, multi-millisecond pauses |

**Measurement:**
```bash
# PerfView
PerfView.exe collect -GCOnly MyApp.exe

# dotMemory
dotMemory.exe profile MyApp.exe

# Built-in counters
dotnet-counters monitor --process-id $(pidof MyApp) \
  System.Runtime[gen-0-gc-count,gen-1-gc-count,gen-2-gc-count]
```

**Mitigation Strategies:**

**1. Stack Allocation:**
```csharp
// ❌ Heap allocation
byte[] buffer = new byte[256]; // Gen-0

// ✅ Stack allocation
Span<byte> buffer = stackalloc byte[256]; // No GC
```

**2. Object Pooling:**
```csharp
// ✅ Reuse buffers
private static readonly ArrayPool<byte> s_pool = ArrayPool<byte>.Shared;

public void Process()
{
    byte[] buffer = s_pool.Rent(4096);
    try
    {
        // Use buffer
    }
    finally
    {
        s_pool.Return(buffer);
    }
}
```

**3. ValueTask for async:**
```csharp
// ❌ Always allocates Task
public async Task<int> GetValueAsync() => 42;

// ✅ No allocation when synchronous
public async ValueTask<int> GetValueAsync() => 42;
```

**4. Avoid LINQ in hot paths:**
```csharp
// ❌ Multiple allocations
var result = items.Where(x => x.IsActive)
                  .Select(x => x.Value)
                  .ToList();

// ✅ Single allocation
var result = new List<int>(items.Count);
foreach (var item in items)
{
    if (item.IsActive)
        result.Add(item.Value);
}
```

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**See Also:** [Hot Path](#hot-path), [Allocation Type](#allocation-type)

---

### Allocation Type

**Definition:**  
Classification of where memory is allocated and its lifetime characteristics, critical for understanding GC impact.

**Categories:**

| Type | Location | Lifetime | GC Cost | When to Use |
|:---|:---|:---|:---|:---|
| **Stack-only** | Stack | Method scope | **Zero** (no GC) | Hot paths, small buffers (< 1 KB) |
| **Ephemeral** | Gen-0 heap | Short-lived (< 1s) | **Low** (fast collection) | Request-scoped objects |
| **Intermediate** | Gen-1 heap | Medium-lived (1s-1m) | **Medium** | Session-scoped caches |
| **Cached** | Gen-2 heap | Long-lived (> 1m) | **High** (rare collection) | Singletons, global state |
| **LOH** | Large Object Heap | Large objects (> 85 KB) | **Very High** (compaction cost) | Buffers, images, datasets |

**Decision Tree:**
```
Is size < 1 KB AND lifetime = method scope?
  ├─ Yes → Stack (stackalloc, Span<T>)
  └─ No → Is it short-lived (< 1 second)?
      ├─ Yes → Ephemeral (Gen-0)
      └─ No → Is it long-lived (> 1 minute)?
          ├─ Yes → Cached (Gen-2, consider pooling)
          └─ No → Intermediate (Gen-1)

Is size > 85 KB?
  └─ Yes → LOH (use ArrayPool to avoid)
```

**Examples:**
```csharp
// Stack-only (0 bytes allocated)
public int ComputeChecksum(ReadOnlySpan<byte> data)
{
    Span<byte> temp = stackalloc byte[64];
    // ... computation ...
    return checksum;
}

// Ephemeral (Gen-0)
public string ProcessRequest(string input)
{
    var result = new StringBuilder(); // Gen-0
    // ... short-lived processing ...
    return result.ToString(); // Gen-0
}

// Cached (Gen-2)
public sealed class ServiceRegistry
{
    private static readonly ConcurrentDictionary<string, object> s_cache = new();
    // Lives for application lifetime
}

// LOH (avoid!)
public byte[] LoadLargeFile(string path)
{
    return File.ReadAllBytes(path); // > 85 KB = LOH
}

// LOH mitigation
public void ProcessLargeFile(string path)
{
    byte[] buffer = ArrayPool<byte>.Shared.Rent(1_000_000);
    try
    {
        int bytesRead = File.OpenRead(path).Read(buffer);
        // Process buffer
    }
    finally
    {
        ArrayPool<byte>.Shared.Return(buffer);
    }
}
```

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**See Also:** [GC Pressure](#gc-pressure), [Hot Path](#hot-path)

---

### Hot Path

**Definition:**  
Code executed **frequently** or in **performance-critical scenarios** where even microsecond optimizations matter. Typically called thousands to millions of times per second.

**Identification:**
- Part of request processing pipeline
- Inside tight loops
- Real-time or low-latency requirements
- Profiler shows > 5% CPU time

**Optimization Rules for Hot Paths:**

| Rule | Technique | Example |
|:---|:---|:---|
| **1. Zero allocations** | `Span<T>`, `stackalloc` | `Span<byte> buffer = stackalloc byte[256];` |
| **2. Avoid virtual dispatch** | Sealed classes, static methods | `public sealed class FastParser` |
| **3. No LINQ** | For loops, manual iteration | `for (int i = 0; i < count; i++)` |
| **4. Inline small methods** | `[MethodImpl]` attribute | `[MethodImpl(MethodImplOptions.AggressiveInlining)]` |
| **5. Use ValueTask** | Avoid Task allocation | `public ValueTask<int> GetAsync()` |
| **6. Bounds check elimination** | Safe patterns, JIT helps | Use `.Length` instead of repeated checks |
| **7. Profile constantly** | BenchmarkDotNet | Measure, don't guess |

**Example:**
```csharp
// ❌ NOT optimized for hot path
public string FormatMessage(string template, params object[] args)
{
    return string.Format(template, args); // Allocates array + boxing
}

// ✅ Hot path optimized
[MethodImpl(MethodImplOptions.AggressiveInlining)]
public void FormatMessage(
    ReadOnlySpan<char> template,
    Span<char> destination,
    int value,
    out int written)
{
    // No allocations, direct span manipulation
    value.TryFormat(destination, out written);
}
```

**Benchmarking:**
```csharp
[MemoryDiagnoser]
public class FormattingBenchmarks
{
    [Benchmark]
    public string StringFormat()
    {
        return string.Format("Value: {0}", 42);
    }
    
    [Benchmark]
    public string SpanFormat()
    {
        Span<char> buffer = stackalloc char[128];
        42.TryFormat(buffer, out int written);
        return new string(buffer.Slice(0, written));
    }
}

// Results:
// StringFormat: 87.23 ns, 168 B allocated
// SpanFormat:   12.45 ns,   0 B allocated  ← 7x faster, 0 allocations
```

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**See Also:** [GC Pressure](#gc-pressure), [AOT-Friendly](#aot-friendly)

---

### AOT-Friendly

**Definition:**  
Code compatible with **Ahead-of-Time (AOT) compilation**, where IL is compiled to native code before runtime, eliminating JIT overhead.

**Benefits:**
- **Faster startup** (no JIT compilation needed)
- **Lower memory usage** (no JIT bookkeeping)
- **Better performance** (optimized native code)
- **Smaller deployment** (trimming removes unused code)
- **iOS/Android support** (platforms without JIT)

**Requirements:**

**❌ Prohibited (breaks AOT):**
- `Reflection.Emit` (runtime code generation)
- Dynamic assembly loading
- Unattributed generics (needs static analysis)
- Implicit reflection (use source generators instead)
- `dynamic` keyword
- COM interop (Windows-specific)

**✅ AOT-Compatible:**
```csharp
// ✅ Source generators instead of reflection
[JsonSerializable(typeof(Configuration))]
public partial class ConfigurationContext : JsonSerializerContext { }

var config = JsonSerializer.Deserialize<Configuration>(
    json,
    ConfigurationContext.Default.Configuration);

// ✅ Explicit generic constraints
public void Process<T>(T value) where T : IProcessable
{
    value.Process(); // AOT can see this call
}

// ✅ Static abstract interfaces (C# 11+)
public interface IParser<TSelf> where TSelf : IParser<TSelf>
{
    static abstract TSelf Parse(string input);
}
```

**Validation:**
```bash
# Publish with AOT
dotnet publish -c Release -r linux-x64 /p:PublishAot=true

# Check for warnings
# IL3050: Reflection usage
# IL2026: Requires dynamic code
```

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**See Also:** [Hot Path](#hot-path), [Deterministic Build](#deterministic-build)

---

## 📊 Diagnostics Terms

### EventSource

**Definition:**  
.NET's structured logging infrastructure providing **high-performance ETW (Event Tracing for Windows)** integration with minimal allocation overhead.

**Sys.Kernel Standard:**
```csharp
[EventSource(Name = "Syntony.Kernel.Diagnostics")]
public sealed class SysKernelEventSource : EventSource
{
    public static readonly SysKernelEventSource Log = new();
    
    private SysKernelEventSource() : base(EventSourceSettings.EtwSelfDescribingEventFormat)
    {
    }
    
    [Event(1, Level = EventLevel.Informational, Message = "Service {0} started")]
    public void ServiceStarted(string serviceName)
    {
        WriteEvent(1, serviceName);
    }
    
    [Event(2, Level = EventLevel.Error, Message = "Service {0} failed: {1}")]
    public void ServiceFailed(string serviceName, string error)
    {
        WriteEvent(2, serviceName, error);
    }
    
    [NonEvent]
    public void ServiceFailedWithException(string serviceName, Exception ex)
    {
        // Convert exception to string for ETW
        ServiceFailed(serviceName, ex.ToString());
    }
}
```

**Performance Characteristics:**
- **Allocation:** < 128 bytes per event
- **Latency:** < 3 microseconds to WriteEvent
- **Throughput:** > 100,000 events/second
- **Overhead:** < 1% CPU when listeners attached

**Benefits:**
- Native Windows integration (no external dependencies)
- PerfView compatibility
- EventPipe support (cross-platform)
- Structured data (not just strings)
- Dynamic enable/disable (no performance hit when off)

**Usage:**
```csharp
// Logging
SysKernelEventSource.Log.ServiceStarted("ConfigurationService");

// Collection (PerfView)
PerfView.exe collect -providers "*Syntony.Kernel.Diagnostics" MyApp.exe

// Collection (dotnet-trace)
dotnet-trace collect --process-id $(pidof MyApp) \
  --providers Syntony.Kernel.Diagnostics
```

**Primary Prompt:** [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)

**See Also:** [EventSource Discipline](#eventsource-discipline), [Structured Logging](#structured-logging)

---

### EventSource Discipline

**Definition:**  
The Sys.Kernel principle that all telemetry uses **analyzer-clean EventSource design** with no dynamic string formats, ensuring type safety and performance.

**Rules:**
1. **No string interpolation** in Event methods
2. **Use parameters**, not formatted strings
3. **Mark with [Event]** attribute
4. **Deterministic event IDs** (no gaps, sequential)
5. **Meaningful event names** (verb + object)
6. **Appropriate log levels** (Verbose < Informational < Warning < Error < Critical)

**Example:**
```csharp
// ❌ Violates EventSource Discipline
[Event(1)]
public void Log(string message)
{
    WriteEvent(1, $"Processing: {message}"); // String interpolation!
}

// ✅ Follows EventSource Discipline
[Event(1, Level = EventLevel.Informational, Message = "Processing item {0}")]
public void ProcessingItem(string itemName)
{
    WriteEvent(1, itemName);
}
```

**Primary Prompt:** [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)

**See Also:** [EventSource](#eventsource), [Structured Logging](#structured-logging)

---

### ActivitySource

**Definition:**  
OpenTelemetry-compatible distributed tracing API for correlating operations across service boundaries using W3C Trace Context standard.

**Sys.Kernel Standard:**
```csharp
public sealed class TracedService
{
    private static readonly ActivitySource s_activitySource = 
        new("Syntony.Kernel.Diagnostics", "1.0.0");
    
    public async Task ProcessRequestAsync(string requestId)
    {
        using var activity = s_activitySource.StartActivity("ProcessRequest");
        activity?.SetTag("request.id", requestId);
        activity?.SetTag("service.name", "ConfigurationService");
        
        try
        {
            await DoWorkAsync();
            activity?.SetStatus(ActivityStatusCode.Ok);
        }
        catch (Exception ex)
        {
            activity?.SetStatus(ActivityStatusCode.Error, ex.Message);
            activity?.RecordException(ex);
            throw;
        }
    }
}
```

**Benefits:**
- **Distributed tracing** across services
- **Automatic context propagation** (HTTP headers, message queues)
- **OpenTelemetry compatibility** (Jaeger, Zipkin, Grafana)
- **W3C Trace Context** standard
- **Performance:** Near-zero overhead when no listeners

**Visualization:**
```
Trace ID: 4bf92f3577b34da6a3ce929d0e0e4736
│
├─ Span: ProcessRequest (200ms)
│  ├─ Span: LoadConfiguration (50ms)
│  ├─ Span: ValidateSchema (30ms)
│  └─ Span: ApplySettings (120ms)
│     └─ Span: RestartService (100ms)
```

**Primary Prompt:** [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)

**See Also:** [EventSource](#eventsource), [Structured Logging](#structured-logging)

---

### Structured Logging

**Definition:**  
Logging approach using **message templates** and **strongly-typed parameters** instead of string concatenation, enabling queryable log data.

**Pattern:**
```csharp
// ❌ String concatenation (unqueryable)
logger.Log("User " + userId + " logged in from " + ipAddress);

// ❌ String interpolation (unqueryable)
logger.Log($"User {userId} logged in from {ipAddress}");

// ✅ Structured logging (queryable)
logger.Log("User {UserId} logged in from {IpAddress}", userId, ipAddress);

// Query in log aggregator:
// SELECT * FROM logs WHERE UserId = '12345'
// SELECT * FROM logs WHERE IpAddress LIKE '192.168%'
```

**Benefits:**
| Benefit | Description |
|:---|:---|
| **Queryable** | Parameters indexed in log stores |
| **Type-safe** | No ToString() surprises |
| **Performance** | No string allocation for disabled levels |
| **PII redaction** | Automatic masking of sensitive fields |
| **Aggregation** | Group by UserId, count by IpAddress |

**Sys.Kernel Standard:**
```csharp
public sealed class SysKernelLogger
{
    public void LogConfigurationLoaded(string configPath, int settingsCount)
    {
        // Template uses placeholders
        // Parameters are separate (type-safe)
        _logger.LogInformation(
            "Configuration loaded from {ConfigPath} with {SettingsCount} settings",
            configPath,
            settingsCount);
    }
    
    // PII-sensitive logging
    public void LogUserAction(
        string userId,
        [SensitiveData] string email,
        string action)
    {
        _logger.LogInformation(
            "User {UserId} (email: {Email}) performed {Action}",
            userId,
            email,  // Will be redacted as [REDACTED]
            action);
    }
}
```

**Primary Prompt:** [Sys.Kernel.Diagnostics.Telemetry.prompt.md](./Sys.Kernel.Diagnostics.Telemetry.prompt.md)

**See Also:** [EventSource](#eventsource), [Secure-by-Default](#secure-by-default)

---

## 🔄 Versioning Terms

### SemVer (Semantic Versioning)

**Definition:**  
Versioning scheme using `MAJOR.MINOR.PATCH` format with strict compatibility rules.

**Format:** `MAJOR.MINOR.PATCH[-PRERELEASE][+BUILD]`

**Sys.Kernel Rules:**

| Version Component | Increment When | Compatibility |
|:---|:---|:---|
| **MAJOR** | Breaking changes, API removal/modification | ❌ Breaking |
| **MINOR** | New features, backward-compatible additions | ✅ Compatible |
| **PATCH** | Bug fixes, documentation, performance | ✅ Compatible |
| **PRERELEASE** | `-alpha`, `-beta`, `-rc.1` | 🔶 Unstable |
| **BUILD** | `+sha.abc123` | ℹ️ Metadata only |

**Examples:**
```
1.0.0 → 1.0.1   Bug fix (safe to upgrade)
1.0.1 → 1.1.0   New feature (safe to upgrade)
1.1.0 → 2.0.0   Breaking change (review required)
2.0.0-beta.1    Pre-release version
2.0.0+sha.a3f   Build metadata
```

**Breaking Changes (MAJOR bump):**
- Remove public API
- Rename type/method
- Change method signature
- Modify behavior (incompatibly)
- Remove deprecated APIs (after grace period)

**Compatible Additions (MINOR bump):**
- Add new public method
- Add optional parameter (with default)
- Add new overload
- Extend enum (carefully)
- Deprecate API (with `[Obsolete]`)

**Non-Breaking Fixes (PATCH bump):**
- Bug fixes
- Performance improvements
- Documentation updates
- Internal refactoring

**Primary Prompt:** [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)

**See Also:** [Public API Surface](#public-api-surface), [Semantic Version Integrity](#semantic-version-integrity)

---

### Semantic Version Integrity

**Definition:**  
Consistent SemVer management with **PublicApiAnalyzer verification**, ensuring backward compatibility promises are kept.

**Mechanism:**
```
Project Files:
├─ PublicAPI.Shipped.txt     (Released APIs - immutable)
└─ PublicAPI.Unshipped.txt   (Upcoming APIs - mutable)
```

**Workflow:**
1. **Development:** Add new APIs to `Unshipped.txt`
2. **Review:** Verify changes don't break contracts
3. **Release:** Move `Unshipped` → `Shipped`, increment version
4. **CI:** Fail build on undeclared API changes

**Example:**
```txt
# PublicAPI.Shipped.txt (v1.0.0)
Syntony.Kernel.Core.ServiceRegistry
Syntony.Kernel.Core.ServiceRegistry.Register<T>() -> void

# PublicAPI.Unshipped.txt (v1.1.0-dev)
Syntony.Kernel.Core.ServiceRegistry.Unregister<T>() -> void  ← New API

# After v1.1.0 release:
# Move Unregister to Shipped.txt
# Bump version to 1.1.0
```

**Analyzer Enforcement:**
```bash
# Fails if public API changed without updating .txt files
dotnet build -warnaserror:RS0016
```

**Primary Prompt:** [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)

**See Also:** [SemVer](#semver-semantic-versioning), [Public API Surface](#public-api-surface)

---

### Public API Surface

**Definition:**  
All types and members marked `public` or `protected`, representing the framework's **contractual interface** with consumers.

**Scope:**
```csharp
// ✅ Part of public API surface
public class ServiceRegistry { }
public interface IService { }
protected virtual void OnInitialized() { }

// ❌ NOT part of public API surface
internal class ServiceRegistryImpl { }
private void Helper() { }
```

**Responsibility:**
Once in the public API surface, a member is a **versioned commitment**:
- Cannot be removed (only deprecated, then removed in MAJOR version)
- Cannot change signature (MAJOR version required)
- Behavior must remain compatible (or document as MAJOR change)

**Documentation Requirement:**
Every public API member must have:
```csharp
/// <summary>Registers a service with the container.</summary>
/// <typeparam name="T">The service type.</typeparam>
/// <remarks>Thread-safe and can be called concurrently.</remarks>
public void Register<T>() where T : class;
```

**Primary Prompt:** [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)

**See Also:** [SemVer](#semver-semantic-versioning), [XML Documentation](#xml-documentation)

---

## 🤖 Prompt System Terms

### Beast Mode

**Definition:**  
Autonomous AI agent execution mode that **persists until task completion** without requiring user intervention.

**Activation Triggers:**
1. Task complexity score > 7 (calculated by Master prompt)
2. Multiple domain prompts required (≥3)
3. User explicitly requests "full autonomous mode"
4. Critical failures detected requiring deep analysis

**Operational Creed:**
> "Plan precisely, act decisively, verify relentlessly."

**Workflow:**
```
User Request
    ↓
Master Evaluates Complexity
    ↓
Complexity > 7? ───→ Yes ───→ BeastMode
    ↓                              ↓
    No                         Planning Phase
    ↓                              ↓
Direct Domain Prompt      Sequential Sub-Prompt Execution
                               (Arch → Perf → Security → ...)
                                  ↓
                          Validation Loop (re-run failures)
                                  ↓
                          Final Report (JSON + Markdown)
```

**Characteristics:**
- **Autonomous:** No user confirmation between steps
- **Persistent:** Continues until complete or blocked
- **Thorough:** Uses all available tools and prompts
- **Verified:** Tests every change, ensures analyzer-clean
- **Documented:** Produces comprehensive reports

**Primary Prompt:** [Original.BeastMode31.prompt.md](./Original.BeastMode31.prompt.md)

**See Also:** [Sub-Prompt Orchestration](#sub-prompt-orchestration), [Confidence Score](#confidence-score)

---

### Confidence Score

**Definition:**  
Quantitative measure (0.0-1.0) of AI analysis certainty, combining multiple quality factors.

**Calculation:**
```csharp
public static double CalculateConfidence(AnalysisResult result)
{
    return
        (result.AnalyzerWarnings == 0 ? 0.25 : 0.0) +
        (result.TestsPassed / (double)result.TotalTests * 0.25) +
        ((100 - result.ComplexityScore) / 100.0 * 0.15) +
        (result.DocumentationCoverage / 100.0 * 0.15) +
        (result.PerformanceScore / 100.0 * 0.20);
}
```

**Factors:**
| Factor | Weight | Measurement |
|:---|:---|:---|
| **Analyzer Cleanliness** | 25% | Zero warnings = full points |
| **Test Coverage** | 25% | Passed tests / Total tests |
| **Code Complexity** | 15% | Inverse of cyclomatic complexity |
| **Documentation** | 15% | XML doc coverage % |
| **Performance** | 20% | Regression % (inverted) |

**Interpretation:**
| Range | Status | Action |
|:---|:---|:---|
| **0.98-1.00** | Production-ready | ✅ Merge approved |
| **0.95-0.97** | Minor improvements needed | 🔶 Review suggested fixes |
| **0.90-0.94** | Significant work required | ⚠️ Major refactoring needed |
| **< 0.90** | Not ready for review | ❌ Block merge |

**Usage in CI:**
```yaml
- name: Calculate Confidence
  run: |
    CONFIDENCE=$(dotnet run --project AnalysisTool -- --calculate-confidence)
    echo "Confidence: $CONFIDENCE"
    if (( $(echo "$CONFIDENCE < 0.98" | bc -l) )); then
      echo "❌ Confidence too low for merge"
      exit 1
    fi
```

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**See Also:** [Analyzer-Clean](#analyzer-clean), [Beast Mode](#beast-mode)

---

### Sub-Prompt Orchestration

**Definition:**  
Master prompt's ability to invoke specialized domain prompts in dependency order, coordinating analysis across architecture, performance, security, and other domains.

**Invocation Syntax:**
```
@invoke Architecture_Verification {
  "target": "Syntony.Kernel.Runtime",
  "strict": true,
  "output_format": "json"
}
```

**Execution Flow:**
```
Master Prompt
    ↓
┌───────────────────────────┐
│   Architecture Review     │ (dependency boundaries)
└───────────┬───────────────┘
            ├────────────────────┐
            ↓                    ↓
    ┌───────────────┐    ┌──────────────┐
    │  Performance  │    │   Security   │
    └───────┬───────┘    └──────┬───────┘
            ↓                    ↓
    ┌───────────────────────────┐
    │     Thread Safety         │
    └───────────┬───────────────┘
                ↓
        ┌───────────────┐
        │ Documentation │
        └───────┬───────┘
                ↓
        ┌───────────────┐
        │    Testing    │
        └───────────────┘
```

**Dependencies:**
- **Architecture** must pass before Performance/Security
- **Thread Safety** blocks Naming and Documentation
- **Testing** requires completed Documentation
- **Versioning** is final validation step

**Response Format:**
```json
{
  "prompt": "Architecture_Verification",
  "version": "3.1",
  "status": "success",
  "violations": 0,
  "confidence": 0.99,
  "details": { /* ... */ }
}
```

**Primary Prompt:** [Sys.Kernel.Master.prompt.md](./Sys.Kernel.Master.prompt.md)

**See Also:** [Beast Mode](#beast-mode), [Confidence Score](#confidence-score)

---

## 📐 Code Quality Terms

### Member Ordering

**Definition:**  
Strict sequence for declaring members within a type to ensure consistency and readability.

**Standard Order:**
1. **Constants** (`const`, `static readonly`)
2. **Static fields**
3. **Instance fields** (private `_camelCase`)
4. **Constructors** (public → internal → protected → private)
5. **Static constructors**
6. **Properties** (auto → full → expression-bodied)
7. **Indexers**
8. **Events**
9. **Public methods** (interface implementations first, then alphabetical)
10. **Protected methods**
11. **Internal methods**
12. **Private methods**
13. **Nested types** (enums, records, structs, classes)

**Example:**
```csharp
public sealed class ServiceRegistry
{
    // 1. Constants
    private const int DefaultCapacity = 16;
    
    // 2. Static fields
    private static readonly object s_lock = new();
    
    // 3. Instance fields
    private readonly ConcurrentDictionary<Type, object> _services;
    private int _registrationCount;
    
    // 4. Constructors
    public ServiceRegistry()
    {
        _services = new(Environment.ProcessorCount, DefaultCapacity);
    }
    
    // 5. Properties
    public int Count => _services.Count;
    
    // 6. Events
    public event EventHandler<ServiceRegisteredEventArgs>? ServiceRegistered;
    
    // 7. Public methods
    public void Register<T>(T instance) where T : class
    {
        // Implementation
    }
    
    // 8. Private methods
    private void OnServiceRegistered(Type serviceType)
    {
        ServiceRegistered?.Invoke(this, new ServiceRegisteredEventArgs(serviceType));
    }
    
    // 9. Nested types
    public sealed class ServiceRegisteredEventArgs : EventArgs
    {
        public Type ServiceType { get; }
        public ServiceRegisteredEventArgs(Type serviceType) => ServiceType = serviceType;
    }
}
```

**Enforcement:**  
`.editorconfig` + `dotnet_sort_system_directives_first` + Roslynator analyzers

**Primary Prompt:** [Sys.Kernel.Better.Naming.prompt.md](./Sys.Kernel.Better.Naming.prompt.md)

**See Also:** [EditorConfig Compliance](#editorconfig-compliance)

---

### EditorConfig Compliance

**Definition:**  
Adherence to project-wide code style rules defined in `.editorconfig` file.

**Key Rules:**
| Rule | Value | Rationale |
|:---|:---|:---|
| **Indentation** | 4 spaces | .NET standard |
| **Line endings** | LF | Cross-platform compatibility |
| **Charset** | UTF-8 with BOM | C# compiler requirement |
| **Braces** | Required for all control blocks | Prevent bugs |
| **Using directives** | Outside namespaces | Simplify refactoring |
| **Nullable reference types** | Enabled | Null safety |
| **File-scoped namespaces** | Preferred | Reduce indentation |

**Validation:**
```bash
# Format check (no modifications)
dotnet format --verify-no-changes

# Apply formatting
dotnet format

# CI enforcement
dotnet format --verify-no-changes || exit 1
```

**Primary Prompt:** [Sys.Kernel.Framework.Architecture.prompt.md](./Sys.Kernel.Framework.Architecture.prompt.md)

**See Also:** [Analyzer-Clean](#analyzer-clean), [Member Ordering](#member-ordering)

---

### CLS Compliance

**Definition:**  
Code conforming to **Common Language Specification**, ensuring interoperability across .NET languages (C#, F#, VB.NET).

**Requirement:**
```csharp
[assembly: CLSCompliant(true)]
```

**Rules:**
| Prohibited | Reason | Alternative |
|:---|:---|:---|
| **Unsigned types** in public API (`uint`, `ulong`) | Not CLS-compliant | Use `int`, `long` |
| **Case-only differences** (`MyType` vs `myType`) | Case-insensitive languages | Use distinct names |
| **`ref`/`out` overloads** | Indistinguishable in VB.NET | Use different names |
| **Exposed pointers** | Not supported in all languages | Use `Span<T>` |

**Example:**
```csharp
// ❌ NOT CLS-compliant
public class DataService
{
    public uint GetCount(); // Unsigned type
    public void Process(ref int value); // ref parameter
}

// ✅ CLS-compliant
public class DataService
{
    public int GetCount();
    public int Process(int value); // Returns modified value
}
```

**Verification:**
```bash
# Analyzer CA1014 warns about CLS violations
dotnet build -warnaserror:CA1014
```

**Primary Prompt:** [Sys.Kernel.API.Stability.Versioning.prompt.md](./Sys.Kernel.API.Stability.Versioning.prompt.md)

**See Also:** [Public API Surface](#public-api-surface), [Analyzer-Clean](#analyzer-clean)

---

## 🧵 Concurrency Terms

### Thread Safety Principle

**Definition:**  
Ensures all shared resources are **lock-free**, **idempotent**, and **consistent** across async boundaries.

**Core Tenet:**  
*"Concurrency bugs are prevented by design, not detected by testing."*

**Key Principles:**
1. **Immutability first** (see [Immutable Core](#immutable-core))
2. **No shared mutable state** without synchronization
3. **Lock hierarchy** when locks required (see [Lock Hierarchy](#lock-hierarchy))
4. **Async all the way** (no blocking on async code)
5. **CancellationToken** in all async APIs

**Primary Prompt:** [Sys.Kernel.Thread.Safety.Concurrency.prompt.md](./Sys.Kernel.Thread.Safety.Concurrency.prompt.md)

---

## 📜 License - Copyright

© 2025 Josef Hahnl — *Syntony Austria*  
All rights reserved.  
For details, visit [https://syntonyblog.wordpress.com/](https://syntonyblog.wordpress.com/)  
📧 Contact: [SyntonyAustria@outlook.com](mailto:SyntonyAustria@outlook.com)

***Clarity · Strength · Dignity — life.exe - Syntony - #syntony - #LifeDotExe***

---
