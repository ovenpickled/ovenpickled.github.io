---
title: "Flux DB — Redis-Inspired Key-Value Store"
excerpt: "A high-performance key-value store built in C++17 from scratch with zero external dependencies. Features non-blocking I/O, incremental rehashing, and AVL-backed sorted sets.<br/><br/><strong>Tech:</strong> C++17, pthreads, poll(), AOF Persistence"
collection: portfolio
---

## Overview

A Redis-inspired key-value store built entirely from scratch in **C++17** — no external dependencies, no shortcuts. Designed to understand and replicate the core internals of Redis at the systems level.

## Key Technical Details

- **Non-blocking event loop** using `poll()`-based I/O multiplexing with a pthreads worker pool for concurrent request handling
- **Incremental rehashing** across two live hash tables, migrating keys in fixed batches of 128 per operation — eliminates the stop-the-world latency spikes found in naive resize strategies
- **Sorted set** backed by a parallel AVL tree and hash map sharing nodes via intrusive structs, enabling `O(log n)` range queries and `O(1)` point lookups on the same underlying data
- **AOF persistence** with configurable fsync policies for durability without sacrificing throughput

## Performance

| Metric | Value |
|--------|-------|
| Throughput | 110k–150k ops/sec |
| p50 Latency | ~1µs |
| Sub-100µs Completion | 93–99% of requests |

Even with fsync-based AOF persistence enabled, the vast majority of requests complete under 100µs.

## Links

🔗 [GitHub Repository](#) *(placeholder — update with actual link)*
