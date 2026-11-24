# CoreBlow RTT

Streaming Time-To-First-Token (TTFT) and Round-Trip Time (RTT) profiler for CoreBlow.

## Overview

CoreBlow RTT is part of the CoreBlow public repository family. It provides real-time streaming latency profiling tools measuring Time-To-First-Token (TTFT), total Round-Trip Time (RTT), streaming token chunk intervals, and percentile distributions (min/median/p95/max) across CoreBlow Gateway endpoints.

This repository follows the same ecosystem split that CoreBlow uses to keep release surfaces small, auditable, and independently governed.

## Repository Role

- Status: Active
- Phase: 4
- Priority: quality
- Kind: measurement
- Family: CoreBlow public repository family
- Branding: CoreBlow

## Features

- **Streaming Latency Breakdown**: Directly captures `TTFT` (delay until first token chunk arrives) and total `RTT` (delay until stream completes).
- **Protocol Flexibility**: Supports Server-Sent Events (SSE), HTTP chunked transfer, and REST endpoints.
- **Percentile Distributions**: Reports min, median (p50), p95, and max response times across multiple configurable sample runs.
- **Multi-Format Output**: Summary console views, structured JSON reports, and Markdown tables.

## Usage

### Command Line Interface

```sh
# Profile streaming endpoint with 10 samples
node bin/coreblow-rtt.mjs --url http://127.0.0.1:18789/api/chat/stream --samples 10

# Generate structured JSON
node bin/coreblow-rtt.mjs --url http://127.0.0.1:18789/api/chat/stream --json

# Generate Markdown table
node bin/coreblow-rtt.mjs --url http://127.0.0.1:18789/api/chat/stream --markdown
```

### Programmatic Usage

```js
import { profileStreamingSession, formatRttMarkdownReport } from "@coreblow/coreblow-rtt";

const report = await profileStreamingSession({
  url: "http://127.0.0.1:18789/api/chat/stream",
  sampleCount: 5,
});

console.log(`Median TTFT: ${report.ttft.medianMs}ms | Median RTT: ${report.rtt.medianMs}ms`);
```

### Running Tests

```sh
npm test
```

## Release Policy

Do not publish packages, tags, installers, or release artifacts from this repository without explicit CoreBlow release approval.

Version changes must follow the coordinated CoreBlow release plan.

## Links

- [CoreBlow](https://github.com/coreblow/coreblow)
- [Documentation](https://docs.coreblow.com)
- [Website](https://coreblow.com)
- [Security Policy](SECURITY.md)
- [Contributing](CONTRIBUTING.md)
