# Site Reliability Engineering (SRE) Introduction

## What is SRE?
Site Reliability Engineering (SRE) is a discipline that applies software engineering practices to infrastructure and operations problems. Its goal is to create scalable and highly reliable systems.

---

## Observability
Observability is the ability to understand the internal state of a system by examining its outputs.  
It goes beyond monitoring by answering *why* something is happening.

Key pillars of observability:
1. **Metrics** – Numeric measurements of system performance.
2. **Logs** – Text records of discrete events.
3. **Traces** – End-to-end request flow through a distributed system.

---

## Metrics
- Quantitative data points that measure system health and performance.
- Common examples:
  - CPU and memory usage
  - Request latency
  - Error rates
  - Throughput (requests per second)
- Metrics are usually aggregated and visualized in dashboards (e.g., Prometheus, Grafana).

---

## Logs
- Immutable, timestamped records of events within a system.
- Provide context for understanding specific issues or debugging failures.
- Types of logs:
  - Application logs
  - System logs
  - Security logs
- Useful for root cause analysis and audits.

---

## Traces
- Show the life cycle of a single request across multiple services in a distributed system.
- Helps identify bottlenecks and latency issues.
- Key concepts:
  - **Span**: A single unit of work in a trace.
  - **Trace**: A collection of spans showing the full request journey.
- Common tools: Jaeger, Zipkin, OpenTelemetry.

---

## Why Observability Matters in SRE
- Ensures reliability and uptime by proactively identifying issues.
- Improves mean time to detect (MTTD) and mean time to resolve (MTTR).
- Enables data-driven decisions for scaling, performance, and resilience.

---

## Summary
SRE leverages observability through metrics, logs, and traces to maintain reliable systems.  
Together, these provide a comprehensive view of system health, enabling faster debugging and more resilient infrastructure.
