# ai-automation demo

A minimal Spring Boot demo exposing a single `/hello-world` endpoint.

## Stack

- **Spring Boot** 4.1.0
- **Java** 21 (Eclipse Temurin)
- **Gradle** with the Kotlin DSL (`build.gradle.kts`)
- **[Devbox](https://www.jetify.com/devbox)** to provision the toolchain (JDK, Gradle) and expose convenience scripts

## Getting started

Install [Devbox](https://www.jetify.com/devbox/docs/installing_devbox/), then from the repo root:

```bash
# Enter a shell with the JDK and Gradle on PATH
devbox shell

# Or run a one-off command without entering the shell
devbox run build
devbox run test
devbox run run
```

Available scripts (defined in `devbox.json`):

| Script  | Description                          |
|---------|---------------------------------------|
| `build` | `gradle build`                        |
| `test`  | `gradle test`                         |
| `run`   | `gradle bootRun`                      |
| `clean` | `gradle clean`                        |

These same `devbox run <script>` commands can be used from CI or from Claude Code, so the toolchain doesn't need to be installed separately on the host.

## Endpoint

```
GET /hello-world -> "Hello, World!"
```

Once running (`devbox run run`), try:

```bash
curl http://localhost:8080/hello-world
```

## Notes

Exact "latest" Spring Boot / Gradle / JDK patch versions were selected from training knowledge since this environment had no outbound network access at the time this project was scaffolded. Run `devbox update` and bump `build.gradle.kts` plugin versions if newer patches are available.
