---
layout: page
title: Blog
permalink: /jf/blog/
section: jf
description: JuicyForgJF's project write-ups and notes
nav: false
---

<div data-section="jf">

# 🐟 Fish's Blog

Project write-ups, research notes, and things worth sharing.

---

## Projects

<div style="display:grid;gap:20px;margin:24px 0;">

  <!-- Post 1: LLM Red Team -->
  <a href="{{ '/blog/2026/llm-redteam-framework/' | relative_url }}" style="text-decoration:none;color:inherit;">
  <div style="border-left:4px solid #06D6A0;padding:22px 24px;background:#f0fdf9;border-radius:0 14px 14px 0;transition:all 0.2s ease;cursor:pointer;" onmouseover="this.style.transform='translateX(4px)';this.style.boxShadow='0 4px 20px rgba(6,214,160,0.15)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;margin-bottom:8px;">
      <h3 style="margin:0;color:#023E8A;font-size:1.05rem;">🤖 Open-Source Automated LLM Red-Teaming Framework</h3>
      <span style="color:#5a7a8a;font-size:0.8rem;white-space:nowrap;">Mar 2026 – Present</span>
    </div>
    <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px;">
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">AI Security</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">LLM</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Multi-Agent</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Red Team</span>
    </div>
    <p style="margin:0;color:#3a5a6a;font-size:0.9rem;line-height:1.6;">
      Independently built an automated LLM red-teaming platform with a multi-agent Orchestrator coordinating Attacker, Target, and Judge. Features hybrid attack flows (Crescendo + PAIR + ArtPrompt), a non-linear attack state machine with tactical fallback, anti-injection judge sandbox isolation, and demonstrated 100% jailbreak on Llama 3.1 in high-risk scenarios.
    </p>
    <div style="margin-top:10px;color:#06D6A0;font-size:0.85rem;font-weight:600;">Read write-up →</div>
  </div>
  </a>

  <!-- Post 2: NES RE -->
  <a href="{{ '/blog/2025/nes-reverse-engineering/' | relative_url }}" style="text-decoration:none;color:inherit;">
  <div style="border-left:4px solid #06D6A0;padding:22px 24px;background:#f0fdf9;border-radius:0 14px 14px 0;transition:all 0.2s ease;cursor:pointer;" onmouseover="this.style.transform='translateX(4px)';this.style.boxShadow='0 4px 20px rgba(6,214,160,0.15)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;margin-bottom:8px;">
      <h3 style="margin:0;color:#023E8A;font-size:1.05rem;">🎮 NES Game Reverse Engineering & Game Genie Code Development</h3>
      <span style="color:#5a7a8a;font-size:0.8rem;white-space:nowrap;">Dec 2025 – Jan 2026</span>
    </div>
    <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px;">
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Reverse Engineering</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">6502 ASM</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Game Hacking</span>
    </div>
    <p style="margin:0;color:#3a5a6a;font-size:0.9rem;line-height:1.6;">
      Dynamic analysis of NES ROMs with the Mesen debugger. Studied 6502 assembly, memory mapping, and zero-page memory management. Reversed collision detection and timer logic via memory dumps; reconstructed PRNG-based entity spawning logic; developed stable Game Genie codes for invincibility and infinite items.
    </p>
    <div style="margin-top:10px;color:#06D6A0;font-size:0.85rem;font-weight:600;">Read write-up →</div>
  </div>
  </a>

  <!-- Post 3: Web Pentest -->
  <a href="{{ '/blog/2025/web-pentest/' | relative_url }}" style="text-decoration:none;color:inherit;">
  <div style="border-left:4px solid #06D6A0;padding:22px 24px;background:#f0fdf9;border-radius:0 14px 14px 0;transition:all 0.2s ease;cursor:pointer;" onmouseover="this.style.transform='translateX(4px)';this.style.boxShadow='0 4px 20px rgba(6,214,160,0.15)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;margin-bottom:8px;">
      <h3 style="margin:0;color:#023E8A;font-size:1.05rem;">🔐 Authorized Black-Box Pentest: RCE & SQLi on a Visa Platform</h3>
      <span style="color:#5a7a8a;font-size:0.8rem;white-space:nowrap;">Sep – Oct 2025</span>
    </div>
    <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px;">
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Web Security</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">Pentest</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">RCE</span>
      <span style="background:rgba(6,214,160,0.15);color:#028A6E;padding:2px 10px;border-radius:12px;font-size:0.72rem;font-weight:600;">SQLi</span>
    </div>
    <p style="margin:0;color:#3a5a6a;font-size:0.9rem;line-height:1.6;">
      Authorized black-box assessment of a public-facing visa information platform (13 high-risk assets). Discovered and safely verified a critical RCE vulnerability in the CMS architecture, plus SQL injection (blind and UNION-based) with evidence of sensitive user data exposure. Submitted 2 high-severity reports; confirmed remediated.
    </p>
    <div style="margin-top:10px;color:#06D6A0;font-size:0.85rem;font-weight:600;">Read write-up →</div>
  </div>
  </a>

</div>

---

*For collaborative CTF writeups, check the [shared CTF section](/ctf/).*

</div>
