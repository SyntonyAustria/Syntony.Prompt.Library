---
title: "Syntony C# Coding Standards Reference"
author: "Josef Hahnl"
version: "1.0.0"
description: "Comprehensive reference prompt describing the Syntony C# Coding Standards — consistent with .editorconfig, analyzer rules, and the Königsweg principles of clarity, strength, and dignity."
mode: ask
model: gpt-5
tools: [workspace, analyzers, copilotPromptTools]
---

# 🧩 Syntony C# Coding Standards Reference

> *Klarheit. Stärke. Würde. Im Einklang.*
> The following standards define the **Syntony C# Coding Philosophy** — designed for precision, maintainability, and harmony between human and system.

---

## 🧱 1. Naming Conventions

| Element                         | Rule                                     | Example                                                  |
|:------------------------------- |:---------------------------------------- |:-------------------------------------------------------- |
| **Classes / Structs / Records** | `PascalCase`                             | ✅ `MessageTemplateParser`<br>❌ `message_template_parser` |
| **Interfaces**                  | Prefix with `I`, `PascalCase`            | ✅ `ILoggerFactory`<br>❌ `logger_factory`                 |
| **Methods**                     | `PascalCase`                             | ✅ `CreateLogger()`<br>❌ `create_logger()`                |
| **Async Methods**               | Must end with `Async`                    | ✅ `LoadConfigurationAsync()`<br>❌ `LoadConfiguration()`|
| **Parameters**                  | `camelCase`                              | ✅ `void Log(string message)`                            |
| **Fields (private/protected)**  | `_camelCase`                             | ✅ `_options`<br>❌ `options`                             |
| **Constants**                   | `PascalCase`                             | ✅ `DefaultTimeout`                                       |
| **Type Parameters**             | Prefix with `T`                          | ✅ `TValue`, `TResult`                                    |
| **Namespaces**                  | `PascalCase`, follow folder structure    | ✅ `Syntony.Sys.Kernel.Diagnostics`                       |
| **Files**                       | One type per file, file name = type name | ✅ `ConfigurationManager.cs`                              |

---

## ⚙️ 2. Class Member Order

All types follow a fixed structure for readability and reflection stability:

1. Constants (`const`, `static readonly`)
2. Static fields
3. Instance fields
4. Constructors (public → internal → protected → private)
5. Static constructors
6. Properties (auto → full → expression-bodied)
7. Indexers
8. Events
9. Public methods
10. Protected methods
11. Internal methods
12. Private methods
13. Nested types

✅ **Correct:**

```csharp
public sealed class Example
{
    public const int DefaultSize = 8;

    private readonly ILogger _logger;
    private int _count;

    public Example(ILogger logger) => _logger = logger;

    public int Count => _count;

    public void Increment() => _count++;
}
```

❌ **Incorrect:**

```csharp
public class Example
{
    private int _count;
    public const int DefaultSize = 8;
    public void Increment() => _count++;
}
```

---

## 🧩 3. Formatting & Layout

- Indentation: **4 spaces** (no tabs)
- Line endings: **LF**
- Charset: **UTF‑8 with BOM**
- Always use braces `{ }`, even for one-line statements
- Newline at end of file required
- **Using directives:** outside namespaces, alphabetically sorted
- Keep line length ≤ 120 characters

✅ **Good:**

```csharp
if (isEnabled)
{
    logger.Log("Started");
}
```

❌ **Bad:**

```csharp
if (isEnabled) logger.Log("Started");
```

---

## 🧭 4. Code Style & Semantics

- **Expression-bodied members:** use only for short accessors.
- **Object/collection initializers:** prefer explicit property names.
- **Null checks:** use `ArgumentNullException.ThrowIfNull(...)`.
- **String interpolation:** prefer over `string.Format`.
- **`var`:** only when the type is obvious from context.
- **Access modifiers:** explicit and ordered `public` → `internal` → `protected` → `private`.
- **Field visibility:** always explicit.

✅ **Good:**

```csharp
ArgumentNullException.ThrowIfNull(config);
var message = $"Loaded {config.Name}";
```

❌ **Bad:**

```csharp
if (config == null) throw new Exception();
string message = string.Format("Loaded {0}", config.Name);
```

---

## 🧠 5. Asynchronous Code

- Use `async` / `await` correctly with `Task` or `ValueTask`.
- Never block async calls with `.Result` or `.Wait()`.
- Use `ConfigureAwait(false)` in library code.
- Methods performing I/O must be async by convention.

✅ **Good:**

```csharp
public async Task<string> ReadTextAsync(string path)
{
    using var reader = new StreamReader(path);
    return await reader.ReadToEndAsync().ConfigureAwait(false);
}
```

❌ **Bad:**

```csharp
public string ReadText(string path)
{
    return File.ReadAllText(path); // Blocking
}
```

---

## 🧩 6. Documentation

- Every **public member** must have an XML `<summary>` comment.
- `<remarks>` for detailed explanation.
- `<param>` and `<returns>` tags required where applicable.
- Use `<devdoc>` for developer-specific notes or analyzer exceptions.

✅ **Good:**

```csharp
/// <summary>Represents a configuration provider for Syntony.</summary>
/// <remarks>Handles structured configuration and hot reload.</remarks>
public interface IConfigurationProvider
{
    string Get(string key);
}
```

---

## 🧮 7. Analyzer & .editorconfig Compliance

All code must compile with **zero warnings** under:

- AsyncFixer
- Meziantou.Analyzer
- Microsoft.CodeAnalysis.* analyzers
- Microsoft.VisualStudio.Threading.Analyzers
- NetArchTest.Rules
- Roslynator.Analyzers
- SonarAnalyzer.CSharp

No `#pragma disable` or suppression attributes allowed.
Every analyzer warning must be either **resolved or justified** in comments.

---

## 🧰 8. Exception Handling

- Never swallow exceptions silently.
- Log and rethrow using contextual message templates.
- Use specific exception types, not `Exception`.
- Prefer `throw;` to preserve stack trace.
- Use structured logging (`{Property}` placeholders).

✅ **Good:**

```csharp
try
{
    Execute();
}
catch (IOException ex)
{
    _logger.LogError(ex, "Error reading configuration from {Path}", configPath);
    throw;
}
```

❌ **Bad:**

```csharp
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

---

## 🧩 9. Test Conventions (NUnit 4.4)

- All test methods use:

  ```csharp
  [Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]
  ```
- Tests end with:

  ```csharp
  Assert.Pass(TestMessage.TestPassed);
  ```
- Follow **AAA pattern** (Arrange / Act / Assert).
- Async tests use `async Task`.
- Public test classes are `sealed` and marked with `[TestOf(typeof(TargetType))]`.

✅ **Good:**

```csharp
[TestFixture]
[TestOf(typeof(ConfigurationManager))]
public sealed class ConfigurationManagerTests
{
    [Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]
    public void LoadConfigurationReturnsExpectedResultTest()
    {
        // Arrange
        var manager = new ConfigurationManager();

        // Act
        var result = manager.LoadConfiguration("prod");

        // Assert
        Assert.That(result, Is.Not.Null);
        Assert.Pass(TestMessage.TestPassed);
    }
}
```

---

## 🧭 10. Summary Principles

| Königsweg Principle    | Application in Code                                 |
|:---------------------- |:--------------------------------------------------- |
| **Klarheit (Clarity)** | Clear naming, explicit structure, no ambiguity      |
| **Stärke (Strength)**  | Strong typing, analyzer compliance, thread safety   |
| **Würde (Dignity)**    | Respectful code — consistent, readable, intentional |

> *“Code ist nicht nur Logik — es ist geformter Geist.”*
> — Josef Hahnl

---

## 📜 License - Copyright

© 2025 Josef Hahnl — *Syntony Austria* - All rights reserved.

💎 For details, visit [https://syntonyblog.wordpress.com/](https://syntonyblog.wordpress.com/)

📧 Contact: [SyntonyAustria@outlook.com](mailto:SyntonyAustria@outlook.com)

***Clarity · Strength · Dignity — life.exe - Syntony - #syntony - #LifeDotExe***

---