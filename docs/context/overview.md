# Obelisk Context Pack Overview

This repository ships a repo-local Context Pack so engineers and AI tools can work from the same baseline without depending on tribal knowledge or external wiki pages.

## What this pack is for

- Explain the Obelisk backend golden path as it exists in this template today.
- Keep stable repository facts close to the code.
- Make common delivery work easier to do safely with AI assistance.
- Give one worked backend example that shows the intended end-to-end flow.

## How to use it

Default read path:

1. `overview.md`
2. `architecture.md`
3. `_generated/repo-map.md`
4. `feature-delivery-guide.md`
5. `patterns-and-anti-patterns.md`

Open when relevant:

- `_generated/dependency-inventory.md`: package versions, dependency changes, or project references
- `_generated/config-surface.md`: appsettings, configuration keys, secrets, or environment behavior
- `_generated/auth-surface.md`: authentication setup, controller authorization, or endpoint auth surface
- `examples/create-user-flow.md`: users, authentication, email, or password-link flows
- `maintenance.md`: release, generator, or Context Pack maintenance work

## Generated vs handwritten

Generated files live in `docs/context/_generated/`.
Use them for facts that can be derived from the repository when the task touches that surface:

- project layout
- package inventory
- configuration surface
- authentication and authorization surface

Handwritten files live in `docs/context/`.
Use them for guidance that should stay intentional:

- architecture explanation
- where to add new code
- preferred implementation patterns
- AI usage boundaries
- worked examples

Template files live in `docs/context/templates/`.
Use them only when creating project-specific context, not as default coding-session context.

## Refresh workflow

Refresh generated facts whenever you change:

- projects or solution structure
- package references or package versions
- appsettings, host, or local settings files
- authentication setup or controller auth surface

Command:

```powershell
dotnet run --project tools/Obelisk.ContextPack -- generate-template --repo .
```

## Maintenance rules

- Treat `_generated` as committed build artifacts for repository facts.
- Treat handwritten docs as the delivery contract for how new work should follow Obelisk.
- If code and docs disagree, fix the mismatch instead of leaving both versions in place.
- Refresh the Context Pack before template releases.
