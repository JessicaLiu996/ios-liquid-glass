---
name: ios-liquid-glass
description: Review, adopt, and refine Apple's native Liquid Glass visuals and interactions in iOS apps. Use for explicit requests involving glass UI, native glass navigation bars, or related control upgrades in existing or new SwiftUI/UIKit apps. Inspect project compatibility first and prefer system components before custom effects.
license: MIT
---

# Native iOS Liquid Glass

Treat material and interaction as one result: transparency, refraction, highlights, and floating layers must work with state transitions and touch feedback. Keep navigation and controls expressive while content stays stable and readable. Do not inherit a particular app's name, colors, tab count, or business structure.

## Match the requested scope

- **Review or discussion:** inspect the project and report findings, options, and scope without modifying product code.
- **Existing app:** change only authorized screens and controls, preserving navigation and business structure.
- **New app:** choose suitable native components from the start; do not invent a migration phase.
- Carry forward established goals and authorization. Do not introduce repeated approvals after implementation is authorized; ask only about unresolved product tradeoffs that materially affect the result.

## Inspect the real project

Read project instructions and establish:

- SwiftUI, UIKit, or the native iOS layer of a cross-platform framework.
- Available Xcode/SDK, deployment target, runtime OS, and device. Distinguish build SDK from minimum supported OS.
- Whether tab bars, navigation bars, toolbars, menus, and buttons use system or custom implementations.
- Custom backgrounds, materials, appearance overrides, and availability branches that may suppress system behavior.

Without source code, offer design and implementation guidance only; screenshots do not prove the technology stack. For cross-platform projects, inspect framework support and a local native integration before considering broader changes. Do not rewrite an app for one visual effect.

## Choose the smallest useful implementation

### Prefer system components

Choose native navigation and controls for their existing roles. Evaluate `TabView` for SwiftUI bottom navigation and `UITabBarController` for UIKit. Observe default behavior on an appropriate SDK/runtime combination before adding customization.

Appearance depends on the build SDK, runtime OS, component configuration, and accessibility settings. A new SDK does not automatically give every custom-drawn view glass behavior, and adopting it does not inherently require a higher deployment target. Check declarations in the actual SDK.

Adjust obstructing backgrounds or appearance overrides individually rather than clearing styles globally. Preserve navigation state, page lifecycle, hit areas, and safe-area behavior; the glass bar must not hide the final content item.

### Add custom glass only where needed

| Need | Public capability to verify |
| --- | --- |
| Custom SwiftUI material | `glassEffect(_:in:)`, appropriate shape and tint |
| Glass buttons and touch response | Native glass button styles; `interactive(_:)` where appropriate |
| Merging, separating, or morphing glass elements | `GlassEffectContainer`, `glassEffectID`, coordinated state and transitions |
| UIKit custom glass | `UIVisualEffectView` with `UIGlassEffect`, checked against current documentation and SDK |

A material modifier does not reproduce the system tab bar's selection, gestures, and navigation behavior. Preserve system interactions where possible. For custom controls, validate state, shape transitions, and material response together. Avoid redundant glass layers and unnecessary sampling cost.

### Keep the purpose clear

- Apply glass mainly to navigation and controls floating above content. Favor stable readable surfaces for long lists, reading cards, and body text.
- Motion should explain taps, switches, and expansion. Keep idle controls quiet; do not add looping floating, flashing, or background motion by default.
- Transparency or blur alone is not full Liquid Glass. Let native APIs handle material behavior instead of building a shader engine or adding a third-party glass library without need.
- Preserve brand identity, hierarchy, and readability. A reference app's colors, layout, and exaggerated motion are not universal requirements.
- Use reference recordings to identify desired characteristics, not to claim knowledge of their implementation. Actual behavior may differ across systems and settings.

## Implement and preserve compatibility

Complete one representative real screen or control first, verify it at runtime, then expand within the authorized scope. Reuse the project's existing components and extract shared styles only when real repetition justifies it.

Use availability checks for new APIs and retain an appropriate existing appearance or conventional material on older systems. Do not silently raise the deployment target or change business behavior. Check light/dark appearance, Reduce Transparency, and Reduce Motion; custom behavior must respect those preferences.

## Verify and report

Use the project's existing build and verification tools, scaled to the change:

- Build for supported targets and exercise navigation, buttons, menus, and existing actions.
- On a simulator or device, test taps, rapid switching, scrolling, and relevant dragging. Observe continuity, responsiveness, and state synchronization. A static screenshot cannot prove interaction quality.
- Check text/icon legibility on representative backgrounds and verify unobstructed content and usable hit areas.
- Check older-system fallback and relevant accessibility settings. Do not add test infrastructure for a small style change without need.

For a review, report the project facts, native adoption opportunities, custom/compatibility work, and a useful first scope. For implementation, report actual changes, executed build/runtime checks, and remaining limits. If runtime access is unavailable, say so; code integration is not verified animation.

## Official references

Consult current Apple documentation, samples, and local SDK declarations for concrete API or compatibility questions:

- [Adopting Liquid Glass](https://developer.apple.com/documentation/TechnologyOverviews/adopting-liquid-glass)
- [Applying Liquid Glass to custom views](https://developer.apple.com/documentation/SwiftUI/Applying-Liquid-Glass-to-custom-views)
- [Meet Liquid Glass](https://developer.apple.com/videos/play/wwdc2025/219/)
- [Build a SwiftUI app with the new design](https://developer.apple.com/videos/play/wwdc2025/323/)
- [Build a UIKit app with the new design](https://developer.apple.com/videos/play/wwdc2025/284/)
