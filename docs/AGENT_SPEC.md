# Agent Specification (Minimal Public Contract)

This document defines the minimal public contract for HoluBot custom agents.

## Required Fields

- `id`
- `display_name`
- `description`
- `executor`
- `backend`
- `triggers`
- `steps`

## Field Rules

### `id`

- Type: `string`
- Pattern: `^[a-z0-9_\\-]{2,40}$`
- Example: `standup_agent`

### `display_name`

- Type: `string`
- Max length: `60`
- Example: `Standup Assistant`

### `description`

- Type: `string`
- Max length: `240`

### `executor`

- Type: `string`
- Allowed values: `runtime_plan`, `direct_task`

### `backend`

- Type: `string`
- Example: `mock`

### `triggers`

- Type: `array[string]`
- Purpose: keywords used by routing/classification hint logic

### `steps`

- Type: `array[object]`
- Minimum items: `1`
- Each step should contain:
  - `id`
  - `action`
  - `output`

## Best Practices

- Keep steps short and deterministic.
- Do not store secrets in `agent.yaml`.
- Keep descriptions focused on one business responsibility.

## Reference

- Public schema file: [`../examples/agent.schema.yaml`](../examples/agent.schema.yaml)
- Minimal example: [`../examples/standup_agent/agent.yaml`](../examples/standup_agent/agent.yaml)
