---
name: swift-docs-latest
description: Verify Swift implementation decisions against the latest official docs while staying compatible with local toolchain and project constraints.
license: MIT
compatibility: opencode
metadata:
  audience: swift-engineers
  policy: official-docs-first
---

## Purpose
Provide a repeatable process for making Swift changes that are up to date and compatible with the current project toolchain.

## Source Priority
Use sources in this order:
1. https://docs.swift.org/swift-book/documentation/the-swift-programming-language/
2. https://developer.apple.com/documentation/swift
3. https://www.swift.org/documentation/
4. https://www.swift.org/blog/ and official Swift release notes/migration guidance
5. Relevant Apple framework docs (for Foundation, concurrency, UI, and platform APIs) matching local deployment targets

## Required Procedure
1. Read local constraints first:
   - `Package.swift` (swift-tools-version, `platforms`, products, dependencies, targets)
   - `Package.resolved` (locked dependency revisions/versions)
   - Xcode build settings from `*.xcodeproj/project.pbxproj` or `*.xcworkspace` context when present
   - local toolchain indicators (`.swift-version`, `swift --version`, `xcodebuild -version`)
   - lint/style constraints (`.swiftlint.yml`, `.swiftformat`, and project conventions)
2. For uncertain APIs or patterns:
   - discover with Swift MCP tools first
   - optionally cross-check with Context7
   - confirm final usage against official Swift and Apple docs
3. If docs conflict with local constraints:
   - implement the local-compatible approach now
   - include a short upgrade path for adopting the newer API
4. Avoid deprecated or underscored/internal APIs unless local constraints require them or the user explicitly requests them.

## Output Contract
When this skill is used, always include:
- docs consulted (URL and what was verified)
- local compatibility notes (Swift toolchain, Xcode version, deployment targets, dependency constraints)
- decision rationale (why this approach is safest now)
- explicit risks or unknowns

## Guardrails
- Do not claim API availability without source-backed verification.
- Prefer stable APIs over experimental APIs unless explicitly requested.
- Keep recommendations minimal, actionable, and easy to review.
