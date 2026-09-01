# Overview

[简体中文](overview.zh-CN.md) | [Docs Index](README.md)

## Purpose

OpenTelemetry adapter for Gnalloy observability metrics.

This module provides telemetry contracts or adapters. It records bounded metrics and traces without forcing transport, protocol, or vendor-specific dependencies into the core.

## Repository Identity

- Module path: `gnalloy.org/observability-otel`
- GitHub repository: `github.com/gnalloy/observability-otel`
- Default branch: `dev`
- License: Apache-2.0

## Package Map
- `gnalloy.org/observability-otel` (`otel`)

## Direct Gnalloy Dependencies

- `gnalloy.org/gnalloy`

## Direct Dependents in the Current Repository Set

- No repository in the current local Gnalloy set directly depends on this module.

## Architecture Position

Gnalloy keeps the core small and dependency-light. This repository is a replaceable module around one responsibility, connected through explicit Go packages instead of runtime discovery.

## Compatibility

The public import path is `gnalloy.org/observability-otel`. Until the first stable tag is published, use `@dev` or an explicit pseudo-version selected by your dependency policy.
