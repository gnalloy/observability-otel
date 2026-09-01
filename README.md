# observability-otel

[简体中文](README.zh-CN.md) | [Documentation](docs/README.md)

OpenTelemetry adapter for Gnalloy observability metrics.

This module provides telemetry contracts or adapters. It records bounded metrics and traces without forcing transport, protocol, or vendor-specific dependencies into the core.

## Status

- Import path: `gnalloy.org/observability-otel`
- Repository: `github.com/gnalloy/observability-otel`
- Default branch: `dev`
- Preview install: `go get gnalloy.org/observability-otel@dev`
- License: Apache-2.0

## Install
```bash
go get gnalloy.org/observability-otel@dev
go doc gnalloy.org/observability-otel
GOWORK=off GOTOOLCHAIN=local go test ./... -count=1
```

## Documentation
- [Overview](docs/overview.md) ([中文](docs/overview.zh-CN.md))
- [Usage](docs/usage.md) ([中文](docs/usage.zh-CN.md))
- [Examples](docs/examples.md) ([中文](docs/examples.zh-CN.md))
- [Configuration](docs/configuration.md) ([中文](docs/configuration.zh-CN.md))
- [Testing and Performance](docs/testing.md) ([中文](docs/testing.zh-CN.md))
- [API Reference](docs/api.md) ([中文](docs/api.zh-CN.md))
- [Notes and Caveats](docs/notes.md) ([中文](docs/notes.zh-CN.md))
- [ADR-001 Module Boundary](docs/decisions/0001-module-boundary.md) ([中文](docs/decisions/0001-module-boundary.zh-CN.md))

## Module Boundary

This repository owns: OpenTelemetry adapter for Gnalloy observability metrics.

It does not absorb neighboring module responsibilities. Core primitives stay in `gnalloy.org/gnalloy`; protocol codecs, transports, handlers, resolvers, examples, and benchmarks stay in their own repositories.

## Packages
- `gnalloy.org/observability-otel` (`otel`)

## Gnalloy Dependencies

- `gnalloy.org/gnalloy`

## Common Integration Pattern
- Configure recorder/exporter instances at the service boundary and pass them into handlers or transports explicitly.
- Keep metric labels low-cardinality; never use raw payloads, full URLs, user IDs, SQL text, or full error strings as labels.
- Choose aggregation interval and export path based on the deployment, not inside hot protocol loops.

## Current Public Entry Points

The generated API reference lists the full public surface. Common constructors or option types currently include:
- `var ErrInvalidMeter = errors.New("gnalloy/observability/otel: invalid meter")`
- `type Config struct{ ... }`

## Verification

```bash
GOWORK=off GOTOOLCHAIN=local go test ./... -count=1
GOWORK=off GOTOOLCHAIN=local go vet ./...
GOWORK=off GOTOOLCHAIN=local go test ./... -run '^$' -bench . -benchmem -count=1
```

For pressure tests, assemble this module with the relevant transport, codec, and handler stack and run the scenario from `gnalloy.org/benchmarks` or `gnalloy.org/examples`. Keep host, operating system, payload, concurrency, warmup, and repetitions in the report.

## Caveats
- This repository is intentionally narrow. Cross-module behavior should be assembled in applications, recipes, examples, or benchmark harnesses.
- Public APIs should remain Go-native and explicit; avoid runtime scanning, hidden global registries, and reflection-heavy behavior in hot paths.
- Treat network input as untrusted. Configure parser limits and return typed errors instead of panics.
- Keep benchmark claims tied to a concrete host, operating system, protocol, payload, concurrency, warmup, and repetition count.
