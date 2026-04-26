---
title: "x86 Bootable Kernel"
excerpt: "A bare-metal x86 kernel written in C and Assembly that boots via GRUB, writes directly to VGA memory, and runs with zero OS abstraction.<br/><br/><strong>Tech:</strong> C, x86 Assembly (NASM), GCC, GRUB/Multiboot"
collection: portfolio
---

## Overview

A bootable x86 kernel written from scratch in **C and Assembly**, no operating system, no libraries, just raw hardware. Boots via GRUB using the Multiboot specification and renders text by writing directly to VGA video memory.

## Key Technical Details

- **Direct memory-mapped I/O** — writes to VGA memory at `0xb8000` without any operating system abstraction layer
- **Multiboot-compliant binary** built using NASM assembler and GCC with a custom linker script positioning code at physical address `0x100000` for GRUB bootloader compatibility
- **Hardware initialization** including interrupt disabling via `CLI` instruction and 8KB stack allocation in BSS section for bare-metal execution
- **VGA text mode interface** writing 2-byte character-attribute pairs directly to video memory, demonstrating hardware-level display protocol understanding

## What I Learned

This project was about understanding what happens between pressing the power button and seeing text on screen: the boot process, memory layout, segmentation, and how software communicates with hardware when there's nothing else running.

## Links

🔗 [GitHub Repository](https://github.com/ovenpickled/v0id-kernel)
