# Review an existing tab bar

This is an illustrative task, not a benchmark or a completed app migration.

## Input

Provide an existing SwiftUI or UIKit project and identify the bottom navigation you want to review. Include the supported OS range and one real screen where content scrolls behind the bar.

```text
Use $ios-liquid-glass to inspect the bottom navigation in this project.
First tell me which existing appearance overrides prevent native behavior.
Keep the current destinations, selected tab, and minimum supported OS.
After we agree on the scope, implement one representative screen and
verify it in the simulator.
```

## What a useful result includes

1. **Project facts:** framework, build SDK, deployment target, relevant files, native or custom tab bar.
2. **Proposed change:** which overrides to remove or adapt and whether custom glass is actually necessary.
3. **Implementation:** the authorized changes, preserving navigation and business behavior.
4. **Evidence:** build output plus observed tap, rapid-switching, scroll, light/dark, and accessibility behavior.
5. **Limits:** clearly list checks that could not be performed.

## Review criteria

- The last content item remains reachable above or behind the navigation safely.
- The selected tab and destination remain synchronized during rapid switching.
- Labels and icons stay readable against representative backgrounds.
- Older OS versions retain a usable fallback without a silent deployment-target increase.
- A screenshot is not presented as proof of touch response or animation continuity.
