# 概览

[English](overview.md) | [文档索引](README.zh-CN.md)

## 目标

Gnalloy observability metrics 的 OpenTelemetry 适配器。

该模块提供 telemetry 契约或适配器，在不把具体 transport、protocol 或厂商依赖塞进核心的前提下记录有界 metrics 和 traces。

## 仓库身份

- 模块路径：`gnalloy.org/observability-otel`
- GitHub 仓库：`github.com/gnalloy/observability-otel`
- 默认分支：`dev`
- 许可证：Apache-2.0

## 包结构
- `gnalloy.org/observability-otel`（`otel`）

## 直接 Gnalloy 依赖

- `gnalloy.org/gnalloy`

## 当前仓库集合中的直接下游

- 当前本地 Gnalloy 仓库集合中没有仓库直接依赖本模块。

## 架构位置

Gnalloy 保持核心小而轻依赖。本仓库围绕单一职责形成可替换模块，通过显式 Go package 连接，而不是依靠运行时发现。

## 兼容性

公共导入路径是 `gnalloy.org/observability-otel`。首个稳定 tag 发布前，请按依赖策略使用 `@dev` 或明确的 pseudo-version。
