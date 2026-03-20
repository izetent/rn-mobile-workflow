# Bridge Design

Use this when defining or reviewing the shape of a bridge API.

## Prefer explicit contracts

- commands should represent intent
- events should represent observation
- avoid catch-all dictionaries unless the native API is itself dynamic

## Identity rules

- stable business identity should use `itemId`
- `index` is only a positional helper
- avoid commands that depend on stale visible index assumptions

## Ownership rules

- RN owns business UI and low-frequency product state
- native owns timing-sensitive rendering and playback state
- shared ownership should be treated as a bug until proven otherwise

## Avoid

- one API that mixes data mutation, playback control, and visual sync
- hidden state transitions caused by event callbacks
- commands that require RN to know native internal timing
