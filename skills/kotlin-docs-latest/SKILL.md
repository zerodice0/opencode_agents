---
name: kotlin-docs-latest
description: Verify Kotlin implementation decisions against the latest official docs while staying compatible with local build constraints.
license: MIT
compatibility: opencode
metadata:
  audience: kotlin-engineers
  policy: official-docs-first
---

## Purpose
Provide a repeatable process for making Kotlin changes that are up to date and compatible with the current project toolchain.

## Source Priority
Use sources in this order:
1. https://kotlinlang.org/docs/home.html
2. https://kotlinlang.org/api/core/kotlin-stdlib/
3. https://kotlinlang.org/docs/releases.html
4. https://kotlinlang.org/docs/compatibility-guide-*.html and migration pages for the target release
5. https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/ and other relevant official Kotlin API docs matching local dependency constraints

## Required Procedure
1. Read local constraints first:
   - `build.gradle.kts`, `build.gradle`, `settings.gradle.kts`, `settings.gradle`
   - `gradle/libs.versions.toml`, `gradle.properties`, Maven `pom.xml`
   - Kotlin plugin version, language/api/jvm target, and JDK/toolchain constraints
   - lint/style constraints (`detekt`, `ktlint`, `spotless`, and project conventions)
2. For uncertain APIs or patterns:
   - discover with Kotlin MCP tools first
   - optionally cross-check with Context7
   - confirm final usage against official Kotlin docs and APIs
3. If docs conflict with local constraints:
   - implement the local-compatible approach now
   - include a short upgrade path for adopting the newer API
4. Avoid deprecated or experimental APIs unless local constraints require them or the user explicitly requests them.

## Output Contract
When this skill is used, always include:
- docs consulted (URL and what was verified)
- local compatibility notes (Kotlin, Gradle/Maven, JDK, and dependency constraints)
- decision rationale (why this approach is safest now)
- explicit risks or unknowns

## Guardrails
- Do not claim API availability without source-backed verification.
- Prefer stable APIs over experimental APIs unless explicitly requested.
- Keep recommendations minimal, actionable, and easy to review.
