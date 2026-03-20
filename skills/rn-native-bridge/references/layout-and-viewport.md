# Layout And Viewport Ownership

Use this for size mismatches between RN layout and native rendering.

## Distinguish three layers

1. RN host size
2. native root container size
3. actual video or render viewport size

These are not automatically the same thing.

## Recommended rule

- RN decides the host frame
- native decides the viewport frame
- render mode decides how content fits inside the viewport

## Common failure modes

- RN stretches host size and native content also stretches unexpectedly
- RN host changes but native viewport does not update
- viewport is correct but content mode makes the visual result look wrong
- bridge API treats host size and viewport size as the same value

## Avoid

- assuming host size equals actual render area
- letting business text height directly drive video viewport sizing
- using classic bridge for per-frame layout sync
