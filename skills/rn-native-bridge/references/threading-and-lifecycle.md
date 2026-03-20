# Threading And Lifecycle

Use this for event ordering, race conditions, and native lifecycle mismatches.

## Inspect first

- which thread emits the event
- which thread receives the command
- whether the command can arrive after the native state has already changed
- whether view reuse or teardown can invalidate the current bridge target

## Common root causes

- JS sends a command based on stale visible state
- native emits events after the target view is already recycled
- lifecycle ownership is split across RN screen, native view, and native player
- two sides believe they are allowed to trigger the same transition

## Avoid

- fixing race conditions with arbitrary delays
- assuming event order equals visual order
- assuming screen mount equals native view readiness
