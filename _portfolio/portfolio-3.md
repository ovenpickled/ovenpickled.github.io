---
title: "TCP Chat Server — Real-Time Messaging in Go"
excerpt: "A concurrent, multi-room TCP chat server built in Golang with channel-driven command processing, per-client goroutines, and O(1) room lookups.<br/><br/><strong>Tech:</strong> Go, TCP Sockets, Goroutines, Channels"
collection: portfolio
---

## Overview

A real-time, multi-room TCP chat server built in **Golang** — designed around Go's concurrency primitives to handle multiple simultaneous clients and chat rooms without race conditions.

## Key Technical Details

- **Centralized, channel-driven command processor** to handle concurrent client commands, preventing race conditions and simplifying concurrency management across goroutines
- **Per-client goroutines** with line-delimited TCP parsing for scalable, real-time messaging across multiple concurrent chat rooms
- **Map-backed room registries** with broadcast logic for `O(1)` member lookups, enabling efficient fan-out delivery
- **Clean architecture** with modular design for maintainability and easy extension

## Architecture Highlights

```
Client A ──┐                    ┌── Room "general"
Client B ──┤── Command Channel ─┤── Room "random"
Client C ──┘                    └── Room "dev"
```

Each client runs in its own goroutine, sending parsed commands through a central channel. The command processor routes messages to the appropriate room, which handles fan-out delivery to all members.

## Links

🔗 [GitHub Repository](#) *(placeholder — update with actual link)*
