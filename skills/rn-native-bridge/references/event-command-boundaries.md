# Event And Command Boundaries

Use this file when deciding what should be an event and what should be a command.

## Commands

Good command examples:

- `setData(items)`
- `appendData(items)`
- `patchItems(items)`
- `removeItems(itemIds)`
- `scrollToItem(itemId)`
- `pauseCurrent()`
- `resumeCurrent()`

Commands should:

- be explicit
- be idempotent where practical
- not depend on hidden native state

## Events

Good event examples:

- `onCurrentItemChange`
- `onReachEnd`
- `onPlayStateChange`
- `onError`

Events should:

- describe what happened
- avoid requiring JS to immediately send corrective timing commands

## Avoid

- event streams used for frame-by-frame visual sync over classic bridge
- event payloads that force JS to reconstruct native internal state
- command names that hide side effects
