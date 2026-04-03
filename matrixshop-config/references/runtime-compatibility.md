# MatrixShop Runtime Compatibility

Use this reference when the user asks:

- which MatrixShop versions are currently tested
- which server versions are verified
- whether a compatibility claim is based on source metadata or on a real runtime test

## Response rule

Always separate:

1. verified runtime tests
2. source-level build facts

Do not present untested platforms as verified compatibility.

## Current verified runtime tests

Verified on `2026-04-02`:

| MatrixShop | Server Software | Server Version | Result | Test Type | Notes |
| --- | --- | --- | --- | --- | --- |
| `1.5.0` | `Paper` | `1.21.8` | Pass | smoke boot | plugin load, enable, and server ready state confirmed |
| `1.5.0` | `Paper` | `1.21.11` | Pass | smoke boot | plugin load, enable, and server ready state confirmed |

## Current source-level build facts

| Item | Real Value | Basis |
| --- | --- | --- |
| Plugin version | `1.5.0` | `gradle.properties` |
| Build target API | `Bukkit API 1.12.2` | `build.gradle.kts` |
| Required dependency | `MatrixLib 1.0.1` | `gradle.properties` and `build.gradle.kts` |
| Runtime artifact | `build/libs/MatrixShop-1.5.0-all.jar` | local `./gradlew build` result |

## Practical wording rules

- You may say `Paper 1.21.8` and `Paper 1.21.11` are currently verified for `MatrixShop 1.5.0` smoke boot.
- You may say the plugin is built against `Bukkit API 1.12.2`.
- Do not say `Folia`, `Spigot`, `Bukkit`, or other Paper versions are verified unless a fresh test result exists.
- If the user asks for broader compatibility, say that the current repository facts only prove the build target and the verified runtime tests listed above.
