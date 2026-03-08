# Catalog

The catalog is the operational map of what YAI proves, how it is tested, and how coverage evolves across domains.

## What lives here

- scenarios
- domain packs (descriptive and qualification-facing)
- trials
- qualification gates

## Domain-pack boundary

Domain packs in `ops` are descriptive/qualification surfaces.
They are not canonical normative execution logic.

Canonical domain logic lives in `law/domains/*`.

## How this maps to other repos

- `law`: canonical normative source and domain/compliance authority
- `yai`: runtime consumer and enforcement realization
- `ops`: qualification, evidence, rollout visibility, publication
