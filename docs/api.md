# API Reference

[简体中文](api.zh-CN.md) | [Docs Index](README.md)

This inventory is generated from `go doc -short` for the packages in this repository. It is a quick public-surface map; source files and tests remain the authority for exact semantics.

## Packages

### `gnalloy.org/observability-otel`

Package name: `otel`

```text
var ErrInvalidMeter = errors.New("gnalloy/observability/otel: invalid meter")
type Config struct{ ... }
type ContextProvider func() context.Context
type Recorder struct{ ... }
    func NewRecorder(cfg Config) (*Recorder, error)
```
