---
name: sql
description: "Guidelines for generating SQL statements and stored procedures. Colibri conventions."
---

# SQL — Colibri Conventions

## Schema
- Table/column names: **singular**.
- Every table must have: `id` (PK), `created_at`, `updated_at`.
- FK constraints: named, inline, `ON DELETE CASCADE`, `ON UPDATE CASCADE`, referencing parent PK.

## Naming
- Stored procedures: `usp_PascalCase` (plural for collections: `usp_GetProducts`, singular for one: `usp_GetProduct`).
- Parameters: `@camelCase`, required first then optional with defaults.
- Temp tables: prefix `tmp_`.

## Query rules
- UPPERCASE SQL keywords.
- Explicit column names (no `SELECT *`); qualify with table/alias in multi-table queries.
- Prefer JOINs over subqueries.
- Avoid functions on indexed columns in WHERE.
- Include TOP/LIMIT to restrict result sets.

## Stored procedure structure
- Header comment: description, parameters, return values.
- `SET NOCOUNT ON` for procedures that modify data.
- Explicit `BEGIN`/`COMMIT` transactions; avoid long-running locks.
- Validate parameters before use.
- Standardized error codes; do not expose system details.

## Security
- Parameterize all queries (prevent SQL injection).
- Avoid dynamic SQL in stored procedures.
- No credentials in SQL scripts.
