# Examples

[简体中文](examples.zh-CN.md) | [Docs Index](README.md)

## Example 1: Add the Module to an Application

```bash
mkdir gnalloy-app && cd gnalloy-app
go mod init example.com/gnalloy-app
go get gnalloy.org/observability-otel@dev
go doc gnalloy.org/observability-otel
```

## Example 2: Inspect Current Packages

The current source tree exposes these package import paths:
- `gnalloy.org/observability-otel`

Use `go doc` against the package that matches the behavior you need:

```bash
go doc gnalloy.org/observability-otel
```

Selected current exported entry points:
- `var ErrInvalidMeter = errors.New("gnalloy/observability/otel: invalid meter")`
- `type Config struct{ ... }`
- `type ContextProvider func() context.Context`
- `type Recorder struct{ ... }`

## Example 3: Use Executable Tests as Behavioral Examples

Repository tests are executable examples of supported behavior. Start with the selected names below, then read the matching `_test.go` files for complete setup and assertions. See [Testing and Performance](testing.md) for the complete discovered list.

```bash
GOWORK=off GOTOOLCHAIN=local go test ./... -run Test -count=1
```

Selected current test, benchmark, fuzz, and example entry points:
- `TestRecorderMapsChannelEventsToInstruments`
- `TestRecorderUsesNoopMeterByDefault`
- `TestRecorderWrapsInstrumentCreationError`

## Example 4: Cross-Module Assembly

Direct Gnalloy dependencies for this module:
- `gnalloy.org/gnalloy`

Assembly guidance:
- Use this observability module from handlers, transports, applications, or adapters that need metrics and tracing contracts.
- Keep vendor-specific exporters outside hot-path core packages unless this module explicitly owns the adapter.
- Validate emitted metric names, cardinality, and labels under pressure tests.

## Example 5: Pressure-Test Harness

For sustained load, wire this module into a scenario under `gnalloy.org/benchmarks` or a runnable client under `gnalloy.org/examples` when the module participates in network traffic. Record host, OS, CPU, Go version, protocol, payload, concurrency, warmup, repetitions, throughput, and p99 latency in the report.
