# iOS Liquid Glass

**Agent Skill · iOS UI Development**

Bring native Liquid Glass to your iOS app.

An Agent Skill for reviewing and upgrading SwiftUI and UIKit interfaces with Apple's native glass materials and interaction behavior. It guides your coding agent through the actual project, compatibility decisions, implementation, and runtime checks.

## Why use it?

A glass-looking background is only part of the work. Navigation state, touch feedback, scrolling, accessibility, and older-system behavior need to work together. This skill starts with native controls and makes targeted changes to an existing app.

## Example request

```text
Use $ios-liquid-glass to review this app's bottom navigation.
Check the project SDK and deployment target first.
Prefer native controls, preserve the current tabs and navigation state,
and explain the smallest useful change before implementing it.
```

**Expected output:** an assessment of the actual code, a scoped implementation when authorized, and a report separating build checks from interaction checks.

See [a review scenario and acceptance criteria](examples/navigation-review.md). This is a workflow example; this repository does not yet include a recorded app demo.

## What it helps with

- Audit native and custom navigation bars, toolbars, menus, and buttons.
- Adopt system components before adding custom glass effects.
- Coordinate custom glass containers, transitions, and interaction when needed.
- Preserve older-OS behavior, readable content, and accessibility preferences.
- Verify the result on a simulator or device, including rapid switching and scrolling.

## Quick start

Install with the [Skills CLI](https://github.com/vercel-labs/skills), using its supported Node.js version:

```bash
npx skills add JessicaLiu996/ios-liquid-glass --skill ios-liquid-glass
```

Choose your agent, open your iOS project, and use the example request above. The installable package is [`skills/ios-liquid-glass/`](skills/ios-liquid-glass/).

For manual installation, copy that entire directory into your agent's configured skill directory. Reload skills or start a new session as required by your client. This package was prepared and checked in Codex; other clients have not been behaviorally tested.

## Requirements and limitations

- An agent that can read Agent Skills and inspect your project.
- App source code for implementation; screenshots alone support design discussion only.
- A suitable Xcode SDK and simulator or device for build and interaction checks. The skill checks actual API availability instead of silently raising the deployment target.
- A cross-platform app needs a usable native iOS integration path; the skill does not replace its framework.

This is a coding workflow, not a drop-in UI library. Without a runtime environment, it can report code changes but cannot verify animation quality.

## Inside the skill

[`SKILL.md`](skills/ios-liquid-glass/SKILL.md) contains the project inspection, native-first implementation, compatibility, and verification workflow. Its Apple documentation links are reference material, not a promise that every API is available in every project.

Created by [Jessica](https://github.com/JessicaLiu996).

## License

Skill instructions and source code are available under the [MIT License](LICENSE).
