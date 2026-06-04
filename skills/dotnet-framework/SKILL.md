---
name: dotnet-framework
description: "Guidance for working with .NET Framework projects. Includes project structure, C# language version, NuGet management, and best practices."
---

# .NET Framework — Colibri Project

## Build
- Use `msbuild /t:rebuild` (not `dotnet build`).

## Project file (non-SDK format)
- All `.cs` files **must** be explicitly declared: `<Compile Include="Path\To\File.cs" />` (no auto-discovery).
- Uses `<TargetFrameworkVersion>` (e.g., `v4.7.2`), not `<TargetFramework>`.
- Multiple C# versions across projects — use latest compatible per `.csproj`.

## NuGet
- **Do NOT install/update NuGet packages.** Ask user to use Visual Studio NuGet Manager.
- Packages must be compatible with .NET Framework or .NET Standard 2.0.

## .NET Framework specific patterns
- Prefer `DateTimeOffset` over `DateTime`; if using `DateTime`, specify `DateTimeKind.Utc`.
- Use `CultureInfo.InvariantCulture` for serialization/parsing.
- Always specify `StringComparison` in string operations.
- Use `ConfigurationManager.AppSettings` for settings; connection strings in `<connectionStrings>`.
- Use web.config transformations for environment-specific settings.
- Avoid boxing value types; cache `MethodInfo`/`PropertyInfo` in hot paths.
- Use `Lazy<T>` for expensive object creation.
