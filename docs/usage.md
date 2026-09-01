# Usage

[简体中文](usage.zh-CN.md) | [Docs Index](README.md)

## Requirements

- Go 1.25 or newer, matching the module `go` directive.
- A Gnalloy application, recipe, example, or benchmark harness that owns lifecycle and deployment configuration.
- Standalone module verification should set `GOWORK=off` so the module is tested through its published dependency graph.

## Install
```bash
go get gnalloy.org/observability-otel@dev
```

## Import
```go
import "gnalloy.org/observability-otel"
```

## Integration Pattern
- Configure recorder/exporter instances at the service boundary and pass them into handlers or transports explicitly.
- Keep metric labels low-cardinality; never use raw payloads, full URLs, user IDs, SQL text, or full error strings as labels.
- Choose aggregation interval and export path based on the deployment, not inside hot protocol loops.

## API Selection

Use the API inventory to choose the exact constructor or option type for your protocol path:

```bash
go doc gnalloy.org/observability-otel
```

Common current entry points:
- `var ErrInvalidMeter = errors.New("gnalloy/observability/otel: invalid meter")`
- `type Config struct{ ... }`

## Cross-Module Assembly

When multiple Gnalloy repositories are developed together, create a local `go.work` file in your chosen workspace. Keep application-local `replace` directives out of published library modules unless the change is intentionally temporary and never committed.

## Error Handling

Network input, peer behavior, platform capability, and timeout failures must be handled as normal errors. Do not recover protocol correctness by panicking. Return or propagate the module error and close the affected Channel when ownership requires it.
