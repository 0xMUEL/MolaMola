---
layout: post
title: "NES Game Reverse Engineering: ROM Analysis & Game Genie Code Development"
date: 2025-12-01
author: JuicyForgJF
tags: [jf, reverse-engineering, nes, "6502", game-hacking]
categories: [jf]
description: Dynamic analysis of NES ROMs using the Mesen debugger — reversing collision detection, timer logic, PRNG-based entity spawning, and developing stable Game Genie codes.
---

> **Duration:** Dec 2025 – Jan 2026
> **Tools:** Mesen debugger · 6502 assembly · Memory dump analysis

---

## Overview

A deep dive into NES ROM reverse engineering using the **Mesen** emulator's built-in debugging and memory inspection tools. The goal: understand how a classic NES game works at the machine level, reverse key subsystems, and develop working Game Genie codes (cheat codes) by finding and patching the right memory locations.

---

## Technical Breakdown

### 1. Dynamic Analysis with Mesen

The Mesen debugger provides a powerful environment for NES RE:

- **CPU debugger**: Step through 6502 instructions, set breakpoints on memory reads/writes/execution
- **Memory viewer**: Real-time inspection of all addressable memory (RAM, ROM, mapped registers)
- **PPU viewer**: Inspect sprite tables, pattern tables, nametables for visual context

The 6502 architecture uses a **zero page** (first 256 bytes of RAM) as fast-access scratch space — this is where most game state variables live. Understanding which zero-page addresses correspond to which game state was the first major challenge.

### 2. Reversing Collision Detection & Timer Logic

Approach: set write breakpoints on suspicious memory addresses and observe which code paths trigger them.

- **Collision detection**: Traced by watching when the "player health" or "enemy active" flags changed, then walking the call stack backward to find the collision routine
- **Timer logic**: Many NES games use frame counters (decrement every VBlank) for timing. Found the counter by watching for values that decremented at 60Hz (NTSC)
- **Transient variables via memory dump**: For values that only exist for a few frames (e.g., "invincibility frames"), captured memory dumps before/during/after events to diff the state

**Key modification**: By patching the invincibility timer to never decrement (writing `EA EA EA` — three NOP instructions — over the decrement instruction), achieved permanent invincibility.

### 3. PRNG-Based Entity Spawning

NES games often use a **linear feedback shift register (LFSR)** or simple PRNG seeded by frame count for "random" enemy/item spawning. Reversing this:

1. Triggered spawn events repeatedly and recorded the PRNG output sequence
2. Identified the LFSR taps by analyzing the bit pattern
3. Located the PRNG state register in zero page
4. Reconstructed the full parameter memory map: spawn type → spawn location → spawn timing

This allowed predicting exactly what would spawn and when — and by freezing the PRNG state, forcing specific spawns.

### 4. Game Genie Code Development

Game Genie codes work by patching specific ROM addresses at specific bank offsets. Format: `XXXX:YY` where `XXXX` is the address and `YY` is the replacement byte.

Developed stable codes for:
- **Infinite lives**: Patched the lives decrement routine
- **Invincibility**: Patched the damage-taking state transition
- **Infinite items**: Froze item counter decrement

The trickiest part was handling **bank switching** — many NES games use memory mappers (MMC1, MMC3, etc.) to switch ROM banks, so the same CPU address can map to different physical ROM offsets depending on game state.

---

## What I Learned

6502 assembly is surprisingly readable once you get used to the addressing modes. The lack of a stack-based calling convention (6502 uses `JSR`/`RTS` with a hardware stack, but parameters are typically passed through registers or zero page) makes tracing call flows different from x86/ARM RE.

The broader lesson: NES RE is a great training ground for binary RE fundamentals — no OS complexity, no ASLR, no DEP. Just you, the CPU, and the memory map.

---

*If you're interested in NES RE, Mesen's built-in debugger combined with a good memory map reference (nesdev.org) is the fastest way to get started.*
