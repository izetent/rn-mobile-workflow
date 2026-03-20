---
name: rn-native-bridge
description: Use for React Native bridge work involving Native Modules, Native Components, TurboModules, Fabric, JSI, bridge event and command design, ownership boundaries between RN and native, host size versus native viewport size mismatches, scroll or playback hot-path design, and cross-platform bridge behavior divergence. Prioritize explicit ownership, stable identities, low-ambiguity APIs, and keeping high-frequency visual work out of the classic bridge.
---

# RN Native Bridge

Use this skill when the main problem is in the RN-to-native boundary rather than ordinary RN screen logic.

## Core rules

- Identify whether the issue is API shape, lifecycle, threading, event ordering, sizing, or ownership.
- Decide the single source of truth before changing any bridge code.
- Use stable identities such as `itemId` instead of `index` for business ownership.
- Keep high-frequency visual sync and timing-sensitive playback control out of the classic bridge.
- Prefer low-ambiguity command and event contracts over flexible but vague payloads.

## First pass

1. Classify the bridge surface:
   - Native Module
   - Native Component
   - TurboModule
   - Fabric component
   - JSI-backed sync path

2. Read only the relevant reference file:
   - bridge design principles: `references/bridge-design.md`
   - event and command patterns: `references/event-command-boundaries.md`
   - sizing and viewport ownership: `references/layout-and-viewport.md`
   - threading and lifecycle: `references/threading-and-lifecycle.md`
   - validation checklist: `references/bridge-validation.md`

3. Before editing, state:
   - which side owns the state
   - which side emits events
   - which side sends commands
   - what can arrive out of order

## Design guidance

- Use commands for control intent.
- Use events for state observation.
- Do not use events as hidden command channels.
- Keep payloads small and explicit.
- Separate host size from actual render viewport size.
- Make command names intention-revealing, such as:
  - `setData`
  - `patchItems`
  - `scrollToItem`
  - `pauseCurrent`
  - `resumeCurrent`

## Hot-path rule

If the operation must track native scroll or rendering frame by frame, the classic bridge is the wrong path. Use a native-owned path or a UI-thread or JSI-backed synchronization path instead.

## Validation

Always report:

- final ownership model
- bridge contract changes
- backward-compatibility risk
- affected platforms
- what was verified
