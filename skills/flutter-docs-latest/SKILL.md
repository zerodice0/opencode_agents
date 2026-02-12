---
name: flutter-docs-latest
description: Verify Flutter and Dart implementation decisions against current official docs while staying compatible with local SDK constraints.
license: MIT
compatibility: opencode
metadata:
  audience: flutter-engineers
  policy: official-docs-first
---

## Purpose
Provide a repeatable process for making Flutter/Dart changes that are both up-to-date and compatible with the current project toolchain.

## Source Priority
Use sources in this order:
1. https://docs.flutter.dev
2. https://api.flutter.dev
3. https://dart.dev
4. https://pub.dev (matching the local package version constraints)
5. Flutter and Dart release notes or breaking change docs when migration risk exists

## Required Procedure
1. Read local constraints first:
   - `pubspec.yaml` (`environment.sdk` and `environment.flutter`)
   - package versions in `pubspec.yaml` and `pubspec.lock` when available
   - lint and style constraints from `analysis_options.yaml`
2. For uncertain APIs or patterns:
   - discover with Context7
   - confirm final usage against official docs
3. If docs conflict with local constraints:
   - implement the local SDK-compatible approach
   - include a short upgrade path for adopting the newer API
4. Avoid deprecated or removed APIs unless local constraints require them.

## Output Contract
When this skill is used, always include:
- docs consulted (URL and what was verified)
- local compatibility notes (SDK and dependency constraints)
- decision rationale (why this approach is safest now)
- explicit risks or unknowns

## Guardrails
- Do not claim API availability without source-backed verification.
- Prefer stable APIs over experimental APIs unless explicitly requested.
- Keep recommendations minimal, actionable, and easy to review.
