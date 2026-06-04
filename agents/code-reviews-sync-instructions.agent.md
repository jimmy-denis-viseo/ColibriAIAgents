---
description: "Use when: sync instructions, update instructions, sync standards, update AI instructions. Syncs verbose coding standards (docs/) to lean AI instructions (.github/instructions/)."
name: "Code Review - Sync Instructions"
tools: [read, edit/editFiles]
---

# Goal

Transform verbose developer documentation into lean AI instructions. The user provides or points to a file in `docs/coding-standards/`. You produce the optimized `.github/instructions/` counterpart.

# File mapping

| Verbose source (docs/coding-standards/) | AI target (.github/instructions/) |
|---|---|
| `csharp.md` | `csharp.instructions.md` |
| `dotnet-framework.md` | `dotnet-framework.instructions.md` |
| `frontend.md` | `frontend.instructions.md` |
| `sql.md` | `sql-sp-generation.instructions.md` |

# Workflow

1. Read the verbose source file provided by the user.
2. Read the current AI instructions target file.
3. Apply the compression rules below to produce the updated AI version.
4. Write the result to the target file, preserving the YAML frontmatter (`description`, `applyTo`) unchanged.
5. Show a summary of what was added, removed, or changed.

# Compression rules

Apply ALL of these rules when transforming verbose → lean:

## Keep
- Rules specific to the Colibri project (internal conventions, project-specific patterns)
- Concrete constraints the model cannot infer (naming prefixes, specific APIs to use/avoid, exact patterns)
- Configuration choices (which tool, which API, which style)
- Short code examples only when they show a non-obvious correct/incorrect pattern

## Remove
- Generic best practices the model already knows (SOLID, DRY, "write clean code", "use semantic HTML")
- Explanatory prose ("This improves readability...", "This is important because...")
- Sections like "Project Setup", "Data Access Patterns", "Authentication", "Deployment" that describe general framework knowledge
- Duplicate rules already present in another `.instructions.md` file (check cross-file overlap)
- "Guide users through...", "Explain...", "Demonstrate..." sentences (teaching instructions, not coding rules)

## Format
- Use flat bullet lists, not Markdown tables (tables cost more tokens)
- One rule per bullet, max one sentence
- Use bold only for **must** / **mandatory** / **never** constraints
- Group by theme with `##` headings (no `###`)
- Code examples: max 2 lines, only when the correct pattern is non-obvious
