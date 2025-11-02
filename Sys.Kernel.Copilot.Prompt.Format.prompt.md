---
title: "VS Code Copilot Prompt-File Generator"
author: "Josef Hahnl"
version: "1.0.0"
description: "AI prompt that creates, validates, and formats .prompt.md files according to VS Code Copilot’s official specification with Syntony-style consistency and clarity."
mode: ask
model: gpt-5
tools: [workspace, fileSystem, copilotPromptTools]
---

# 🧩 Purpose

Generate or validate **VS Code Copilot prompt files** (`*.prompt.md`)
that follow the official [Prompt File Structure](https://code.visualstudio.com/docs/copilot/customization/prompt-files) and
align with the **Syntony Framework** coding and documentation philosophy.

---

## 🧭 Expected Output

A complete, analyzer-clean `.prompt.md` file that contains:

1. ✅ **YAML Front-Matter Header**
   Includes at least:

   - `title`
   - `description`
   - `mode` (`ask`, `edit`, or `agent`)
   - `model` (e.g. `gpt-5` or `${input:modelName:gpt-5}`)
   - `tools` (optional array of tool set names)

2. 🧱 **Prompt Body (Markdown)**

   - Written in Syntony’s clear, structured Markdown style
   - Explains the role, context, and task to the AI
   - Defines output expectations and formatting rules
   - Can include relative links to other prompts or instruction files
   - May reference workspace variables:
     `${workspaceFolder}`, `${fileBasename}`, `${selection}`, `${input:variableName}`

3. ⚙️ **Compliance Notes**

   - All Markdown syntax must render correctly in VS Code
   - Paths must be relative and valid within the workspace
   - File should end with a newline
   - Indentation = 2 spaces (no tabs)

---

## 🧩 Example Output Template

```markdown
---
title: "C# Code Review Prompt"
description: "Analyzes selected C# code for correctness, performance, and maintainability using .NET 9 and C# 13 best practices."
mode: ask
model: gpt-5
tools: [dotnetTools, analyzers, performanceBenchmarks]
---

# 🔍 .NET 9 / C# 13 Code Review Prompt

Analyze the provided C# source (${selection} or ${fileBasename}) according to:

1. Correctness
2. Performance and memory efficiency
3. Maintainability and analyzer cleanliness

Use the following references if present:
- [../Guidelines/AnalyzerRules.prompt.md](../Guidelines/AnalyzerRules.prompt.md)
- [../Framework/framework_architecture_performance_test.prompt.v3.1.md](../Framework/framework_architecture_performance_test.prompt.v3.1.md)

Return results in Markdown with sections:
- **Findings**
- **Analyzer Compliance**
- **Refactored Code (if edit mode)**
- **Summary & Recommendations**
```

---

## 🧠 Validation Rules

When generating `.prompt.md` files:

- Verify that YAML keys are syntactically correct and valid.
- Ensure `mode` is one of: `ask`, `edit`, `agent`.
- Ensure front-matter and body are separated by `---` lines.
- Test Markdown rendering (headers, code blocks, tables).
- Confirm that any `${variables}` follow Copilot syntax.
- Confirm relative links resolve within the workspace folder.

---

## 🪶 Style & Tone (Syntony Standard)

- Write in **clarity, strength, and dignity** — concise yet complete.
- Prefer imperative voice (“Generate…”, “Analyze…”).
- Avoid filler text or redundancy.
- Use consistent emoji section headers (`# 🧩`, `## ⚙️`, etc.) for readability.
- End file with a newline and no trailing spaces.

---

## 🔧 Example Invocation

> 🧠 *“Create a new Copilot prompt file for generating NUnit 4.4 test fixtures from a selected C# class.”*
>
> Output: `Prompts/nunit_test_generator.prompt.md`
> — includes YAML header, description, mode, and structured task body.

---

## 🧭 Notes for Integration

- Works with **VS Code Copilot Chat** in **ask** or **edit** mode.
- Supports modular composition via Markdown links.
- Prompts can reference project variables or input placeholders for reuse across the Syntony ecosystem.

---

## 📜 License - Copyright

© 2025 Josef Hahnl — *Syntony Austria* - All rights reserved.

💎 For details, visit [https://syntonyblog.wordpress.com/](https://syntonyblog.wordpress.com/)

📧 Contact: [SyntonyAustria@outlook.com](mailto:SyntonyAustria@outlook.com)

***Clarity · Strength · Dignity — life.exe - Syntony - #syntony - #LifeDotExe***

---