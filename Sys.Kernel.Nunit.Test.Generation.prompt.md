---
title: "NUnit 4.4 Test Fixture Generation Prompt"
author: "Josef Hahnl"
version: "3.1.0"
tags: [".NET 9", "C# 13", "NUnit 4.4", "Testing", "Automation", "Prompt"]
created: "2025-10-31"
updated: "2025-10-31"
description: "AI prompt for generating enterprise-grade NUnit 4.4 test fixtures for C# classes and methods with consistent structure, quality validation, and CI/CD readiness."
---

# 🧪 NUnit 4.4 Test Fixture Generation Prompt

## 🎯 Role

Act as a **Senior .NET Test Engineer** with deep expertise in **NUnit 4.x** and modern **C# (C# 13/14, .NET 9+)**.  
Your task is to produce **production-ready NUnit test fixtures** following enterprise-grade conventions.

---

## 🧱 Task Overview

Given one or more **C# classes or methods**, generate a corresponding **NUnit 4.4 TestFixture** that:

- Compiles directly in a **.NET 9+** solution  
- Follows the **Arrange / Act / Assert (AAA)** pattern  
- Includes consistent XML documentation and attribute usage  
- Provides at least one test per public method, plus edge cases

---

## ⚙️ Test Class Rules

| Aspect                      | Rule                                                                  |
|:--------------------------- |:--------------------------------------------------------------------- |
| **Attributes**              | `[TestFixture]` and `[TestOf(typeof(<TargetClass>))]` must be applied |
| **Naming Convention**       | `<TargetClass>Tests`                                                  |
| **Framework Compatibility** | Must compile under **.NET 8+ / NUnit 4.4**                            |
| **Structure**               | Explicit **AAA pattern** in all methods                               |
| **Coverage**                | At least one test per public method + branch/edge-case tests          |
| **Namespace**               | Use `file-scoped` namespaces for clarity                              |

---

## 🧪 Test Method Rules

| Aspect                | Rule                                                                                                                                                      |
|:--------------------- |:--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Naming**            | End with `Test`, use PascalCase (no underscores)                                                                                                          |
| **Attributes**        | `[Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]`                                                               |
| **XML Documentation** | Begin with `<summary>` describing test intent                                                                                                             |
| **Assertions**        | Use **constraint model** only: <br>`Assert.That(actual, Is.EqualTo(expected));`<br>`Assert.That(obj, Is.Not.Null);`<br>`Assert.That(condition, Is.True);` |
| **Final Statement**   | Always end with `Assert.Pass(TestConstants.TestPassed);`                                                                                                  |

---

## ⚡ Async Test Rules

- Async methods must use `async Task` return type.  
- Await all async calls in the **Act** section.  
- Example:

```csharp
[Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]
public async Task FetchDataReturnsExpectedResultTest()
{
    // Arrange
    var service = new MyService();

    // Act
    var result = await service.FetchDataAsync();

    // Assert
    Assert.That(result, Is.Not.Null);
    Assert.Pass(TestConstants.TestPassed);
}
```

---

## 🧠 Edge-Case Generation

For every public method:

- Identify failure or exception paths (null, zero, overflow, invalid state).  
- Generate tests for **expected exceptions**:

```csharp
Assert.That(() => MyClass.Method(null), Throws.ArgumentNullException);
```

---

## 📈 Coverage & Complexity Guidelines

- Aim for **≥80% branch coverage**.  
- Add **dedicated tests** for:  
  - Exception conditions  
  - Null / boundary values  
  - Asynchronous behavior  
  - Generics and interfaces  
- For algorithms or data processing: include a **performance smoke test**.

---

## ✅ Test Quality Checklist

Each generated test must:

- ✅ Compile successfully  
- ✅ Use AAA structure  
- ✅ Include XML doc comments  
- ✅ Use constraint model only  
- ✅ End with `Assert.Pass`  
- ✅ Contain meaningful input data (no “test” or `123` placeholders)  

If any guideline is not met, mark the test with a **⚠️ Severity** level:

| Severity   | Description                               |
|:---------- |:----------------------------------------- |
| **Low**    | Minor naming or doc inconsistency         |
| **Medium** | AAA pattern unclear or missing attributes |
| **High**   | Logic incorrect or test non-functional    |

---

## 🧩 Input Schema

Provide C# code to be tested via:  

- Inline ```csharp``` blocks, or  
- Referenced method names from a source file

## 🧾 Output Schema

AI should return a **complete C# test fixture file**:

| Field         | Description                                           |
|:------------- |:----------------------------------------------------- |
| **File Name** | `<TargetClass>Tests.cs`                               |
| **Namespace** | `<TargetNamespace>.Tests`                             |
| **Content**   | Fully compilable test class conforming to above rules |

---

## 🧩 CI/CD Integration Notes

- Compatible with: `dotnet test --filter Category=Short`  
- Include `[Parallelizable(ParallelScope.All)]` where thread-safe  
- Keep execution time short (`MaxTimeShortCategory` enforced)  
- Retry transient tests automatically using `Retry` attribute  

---

## 🧭 Prompt Optimization Notes

- Use deterministic formatting (consistent indentation, braces).  
- Never include generic “example” placeholders in generated code.  
- Prefer correctness and compile-ability over verbosity.  
- Keep summaries concise and action-oriented.

---

## 🧰 Example Output

```csharp
[TestFixture]
[TestOf(typeof(MyUtilityClass))]
public sealed class MyUtilityClassTests
{
    /// <summary>Validates that AddNumbers correctly sums two positive integers.</summary>
    [Test, Category(TestCategory.Short), MaxTime(TestTimeout.UnitTest), Retry(TestRetry.Min)]
    public void AddNumbersReturnsCorrectSumTest()
    {
        // Arrange
        int a = 5;
        int b = 7;

        // Act
        int result = MyUtilityClass.AddNumbers(a, b);

        // Assert
        Assert.That(result, Is.EqualTo(12));
        Assert.Pass(TestConstants.TestPassed);
    }
}
```

---

## 🔍 Suggested Enhancements for Future Versions

- Add **automatic test naming heuristics** (based on behavior verbs)  
- Include **mock generation hints** for common patterns (ILogger, HttpClient)  
- Extend prompt for **parameterized tests** using `[TestCase]`  
- Integrate with **AI-based coverage estimation tools** (e.g., Roslyn analyzers)  
- Add **code complexity metrics** to suggest additional test cases  

---

© 2025 Josef Hahnl — Syntony Austria  
Refined AI Engineering Prompt for Automated NUnit 4.4 Test Generation  
