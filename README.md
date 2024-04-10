# <img src="https://opentelemetry.io/img/logos/opentelemetry-logo-nav.png" alt="OpenTelemetry Icon" width="45" height=""> opentelemetry-swift

[![CI](https://github.com/open-telemetry/opentelemetry-swift/actions/workflows/BuildAndTest.yml/badge.svg)](https://github.com/open-telemetry/opentelemetry-swift/actions/workflows/BuildAndTest.yml?query=branch%3Amain+)
[![codecov](https://codecov.io/gh/open-telemetry/opentelemetry-swift/branch/master/graph/badge.svg)](https://codecov.io/gh/open-telemetry/opentelemetry-swift)

## About

The repository contains the Swift [OpenTelemetry](https://opentelemetry.io/) client

## Getting Started

This package includes several libraries. The `OpenTelemetryApi` library includes protocols and no-op implementations that comprise the OpenTelemetry API following the [specification](https://github.com/open-telemetry/opentelemetry-specification). The `OpenTelemetrySdk` library is the reference implementation of the API.

Libraries that produce telemetry data should only depend on `OpenTelemetryApi`, and defer the choice of the SDK to the application developer. Applications may depend on `OpenTelemetrySdk` or another package that implements the API.

### Adding the dependency

opentelemetry-swift is designed for Swift 5. To depend on the  opentelemetry-swift package, you need to declare your dependency in your `Package.swift`:

```swift
.package(url: "https://github.com/open-telemetry/opentelemetry-swift", from: "1.0.0"),
```

and to your application/library target, add `OpenTelemetryApi` or  `OpenTelemetrySdk`to your `dependencies`, e.g. like this:

```swift
.target(name: "ExampleTelemetryProducerApp", dependencies: ["OpenTelemetryApi"]),
```

or

```swift
.target(name: "ExampleApp", dependencies: ["OpenTelemetrySdk"]),
```

## Documentation

Official documentation for the library can be found in the official opentelemetry [documentation  page](https://opentelemetry.io/docs/instrumentation/swift/), including:

* Documentation about installation and [manual instrumentation](https://opentelemetry.io/docs/instrumentation/swift/manual/)

* [Libraries](https://opentelemetry.io/docs/instrumentation/swift/libraries/) that provide automatic instrumentation

## Current status

### API and SDK

Tracing and Baggage are considered stable

Logs are considered beta quality

Metrics is implemented using an outdated spec, is fully functional but will change in the future

### Supported exporters and importers

#### Traces

* Exporters: Stdout, Zipkin and OpenTelemetry (OTLP) collector
* Importers: OpenTracingShim

#### Metrics

* Exporters: Prometheus, and OpenTelemetry (OTLP) collector
* Importers: SwiftMetricsShim

#### Logs

* Exporters: OpenTelemetry (OTLP) collector

> **_NOTE:_** OTLP exporters are supported both in GRPC and HTTP, only GRPC is production ready, HTTP is still experimental

### Instrumentation libraries

* `SDKResourceExtension`

## Contributing

For an overview of how to contribute, see the contributing guide in [CONTRIBUTING.md](CONTRIBUTING.md).

We are also available in the [#otel-swift](https://cloud-native.slack.com/archives/C01NCHR19SB) channel in the [CNCF slack](https://slack.cncf.io/). Please join us there for further discussions.
