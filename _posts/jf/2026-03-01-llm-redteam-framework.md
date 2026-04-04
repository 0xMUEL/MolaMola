---
layout: post
title: "Building an Open-Source Automated LLM Red-Teaming Framework"
date: 2026-03-01
author: JuicyForgJF
tags: [jf, ai-security, llm, red-team, research]
categories: [jf]
description: An automated multi-agent red-teaming platform for testing LLM alignment — featuring hybrid attack flows, non-linear state machines, and prompt sandbox isolation.
---

> **Status:** Active (Mar 2026 – Present)
> **Core Tech:** Multi-Agent Orchestration · Hybrid Attacks · Non-Linear State Machines · Prompt Sandbox Isolation · SOTA Jailbreak Techniques (Crescendo / PAIR / ArtPrompt / Many-Shot)

---

## Overview

This project is an open-source automated red-teaming platform specifically designed for testing large language model (LLM) alignment and safety boundaries. The guiding philosophy is **"AI For Security, For AI Security"** — using AI to attack AI, closing the loop on LLM safety evaluation.

The core design centers on a **three-party orchestrated adversarial game** between an Attacker agent, a Target model, and a Judge agent. Each component is modular and composable, enabling high-complexity, multi-dimensional attack campaigns that go far beyond single-prompt jailbreaks.

---

## Key Technical Contributions

### 1. Multi-Agent Orchestration & Hybrid Attack Flows

Designed a central **Orchestrator** that coordinates the Attacker, Target, and Judge in a closed-loop evaluation pipeline. The framework breaks the "single strategy silo" problem by enabling deep fusion of multiple attack techniques:

- **Crescendo** (multi-turn gradual escalation) combined with **ArtPrompt** / **Many-Shot** injection
- Multi-dimensional payload composition for high-stealth compound APT-grade attacks
- Bypasses context and cognitive limitations of frontier alignment models

### 2. Iterative PAIR & Non-Linear Attack State Machine

Extended the original **PAIR (Prompt Automatic Iterative Refinement)** algorithm with a closed-loop feedback mechanism:

- **Iterative PAIR**: The attacker receives structured feedback from the judge and dynamically refines its approach across turns
- **Non-linear state machine**: The Attacker monitors the target model's "alert level" in real time and executes tactical **fallback/downgrade** maneuvers — e.g., retreating from an aggressive extraction state to a "warm-up and rapport-building" state to lower the target's guard
- Achieves highly anthropomorphic social engineering penetration

### 3. Anti-Injection High-Precision Judge Engine

A key challenge in automated red-teaming: the target model may produce **false disclaimers** while still conveying harmful content. Solutions:

- **DISCLAIMER PENALTY heuristic**: Custom scoring algorithm that penalizes the judge for being fooled by surface-level refusals while rewarding extraction of substantive harmful content
- **Prompt Sandbox Isolation**: The Judge node runs in an isolated prompt context, preventing the target's adversarial output from triggering a "secondary reverse injection attack" on the judge itself

### 4. From Vuln Discovery to Kill Chain

Successfully demonstrated end-to-end exploitation in realistic high-risk scenarios:

- Achieved **100% deep jailbreak** on frontier strongly-aligned models (including Llama 3.1) in medical fraud and phishing email generation scenarios
- Designed automated vulnerability verification interface to translate text-level PoC into executable payloads (e.g., sandboxed execution validation)
- Builds a full **kill chain threat model**: from vulnerability discovery → weaponization → payload delivery

---

## Reflections

The most interesting engineering challenge was designing the state machine. Purely greedy strategies (always escalating) fail quickly — the model detects the pattern. The non-linear fallback mechanism was inspired by social engineering research: real attackers don't just push harder when they hit resistance, they retreat, reframe, and re-approach. Encoding that into an automated agent was the core insight.

The anti-injection work on the judge was also non-trivial. An unprotected judge is itself a potential attack surface, and a compromised judge completely invalidates the evaluation loop.

---

*This is an ongoing research project. More details and (eventually) the open-source release coming soon.*
