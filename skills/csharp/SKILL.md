---
name: csharp
description: "C# coding standards for the Colibri project. Use when working on .cs files."
---

# C# — Colibri Conventions

These rules **take precedence** over general C# conventions.

## Explicit types
- Use explicit types instead of `var` whenever possible.

## Async / CancellationToken
- Every `async` method **must** accept a `CancellationToken` parameter — **no default value**.
- `ConfigureAwait(false)` **mandatory** on all `await` calls.
- Avoid `Task.Run()` — use `HostingEnvironment.QueueBackgroundWorkItem` for background work.

## IDisposable / inline using
- Use **inline using** (declaration without block) for every `IDisposable`.
- `SqlDataReader` **must** be declared with `using`:
  ```csharp
  using SqlDataReader reader = await command.ExecuteReaderAsync(cancellationToken).ConfigureAwait(false);
  ```

## SqlDataReader — reading values
- Use `reader.GetFieldValue<T>("column")` (not `reader.GetInt32(0)` or `Convert.ToInt32(reader["col"])`).
- Use `reader.GetFieldValue<int?>("col", null)` for nullable with default.
- Requires `using Microsoft.Data.SqlClient;` (not deprecated `System.Data.SqlClient`).

## Class member ordering
1. Constants → 2. Fields → 3. Constructor → 4. Properties → 5. Events → 6. Public methods → 7. Protected methods → 8. Private methods → 9. Nested types.
Within each section: `public` → `protected` → `private`.

## Operators & patterns
- Use `is null` / `is not null` (not `== null`).
- Use `is` for type casting: `if (obj is string s)`.
- Use pattern matching: `if (result is { Count: > 0 })`.
- Use discard `_` to ignore unused values.

## Naming
- PascalCase: public members, methods, component names.
- camelCase: private fields, local variables.
- Interface prefix: `I` (e.g., `IUserService`).

## Formatting
- Follow `.editorconfig`.
- File-scoped namespaces, single-line usings.
- Newline before opening brace.
- Final return on its own line.
- Use `nameof` instead of string literals.
- XML doc comments on public APIs.

## Nullable reference types
- Declare non-nullable by default; check `null` at entry points only.
- Trust null annotations — no redundant null checks.

## Testing
- Do not emit "Act", "Arrange" or "Assert" comments.
- Copy existing style in nearby files for test method names.
