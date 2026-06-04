---
name: frontend
description: "Front-end standards and best practices: VueJS 3 (Option API), jQuery, Razor, LESS. Colibri internal conventions."
---

# Front-End — Colibri Conventions

These rules **take precedence** over general conventions.

## Colibri-specific rules
- Boolean conditions **must** use strict equality (`===`).
- No Bootstrap classes.

## VueJS 3
- **Option API** only (not Composition API).
- PascalCase for component/file names.
- Separate presentational from container components.
- Clean up side effects in `onUnmounted` or `watch` cleanup callbacks.
- `<style scoped>` with BEM class naming.

## jQuery (legacy)
- Cache selectors in variables; prefix with `$`: `const $btn = $('.btn-submit');`
- Separate business logic from DOM manipulation.
- No nested `$(document).ready()`.
- Event delegation via `.on()` on parent for dynamic elements.
- All AJAX calls must have `.fail()` / `.catch()` error handling.

## Razor (.cshtml)
- No complex C# in views — logic stays in controllers/ViewModels.
- `@model` must match controller.
- Escape user output; `@Html.Raw()` must be justified.

## LESS (.less)
- Use LESS variables for colors/sizes/spacing (no hardcoded values).
- Max 3 nesting levels.
- BEM class naming; no IDs, no `!important` unless justified.
- Prefer mixins over copy-pasting.
- Do not duplicate existing theme variables.
