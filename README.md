# PC-Tuning (Esports / VALORANT) — Stability-first, Measurement-first

This repository is a **de-risked** tuning guide for **stable low-latency VALORANT performance**.
It prioritizes:
- **Consistent frametimes** over fragile peak benchmarks
- **Reversible changes** with rollback steps
- **Security + anti-cheat compatibility** (Vanguard-friendly)
- **Measurement before belief**

> ⚠️ Do not “apply everything.” Change **one variable at a time**, measure, and keep only what improves *your* frametimes/latency.

## Target system
This fork is tailored to **PC#1: Ryzen 7 9800X3D + RTX 2080 Ti**.  
Start here: **docs/pc1-valorant-profile.md**

## What changed vs the legacy guide
The previous “kitchen sink” tuning guide was **removed** from this repo because it included high-risk / low-evidence tweaks
(security disablement, kernel-driver hacks, fragile installer edits, etc.).

A short explanation and migration pointers are here:
- **docs/legacy.md**

## Quick Start (highest ROI, lowest risk)

### 1) Measure a baseline
- Record frametime consistency (PresentMon / CapFrameX) in a repeatable scenario.
- In VALORANT, enable network graphs and watch **packet loss** and **jitter**.

### 2) Fix the big three
1. **Enable NVIDIA Reflex** in VALORANT (*On* to start).
2. Set a **stable FPS cap** you can hold (reduce spikes; don’t run permanently at 99% GPU).
3. If using a wireless mouse: move the dongle to a **USB 2.0 extension** away from USB 3 devices/cables.

### 3) Cut the noise
- Close RGB suites, overlays, capture tools you don’t need mid-match.
- Keep Windows fully supported and patched (avoid Preview/insider builds on a competitive PC).

## Sections
- **PC#1 profile**: docs/pc1-valorant-profile.md
- **Ryzen X3D basics**: docs/configure-ryzen-x3d.md
- **GPU (NVIDIA)**: docs/configure-nvidia.md
- **USB & peripherals**: docs/usb-peripherals.md
- **VALORANT network**: docs/valorant-network.md
- **Registry options (safe, reversible)**: docs/registry-opts.md
- **Windows Update strategy**: docs/windows-update-strategy.md
- **Research & methodology (advanced)**: docs/research.md

## Principles (read once)
- **Truth > novelty**: popular tweaks are not automatically real.
- **Stability-first**: any change that increases WHEA errors, driver resets, or frametime spikes is a regression.
- **Reversible**: export settings / create restore point before anything wide-impact.
- **Anti-cheat safe**: avoid kernel-driver hacks and security disablement.

## References (high credibility)
- Riot on peeker’s advantage and network stability (packet loss/jitter/buffering)
- Intel on USB 3.0 RF interference with 2.4 GHz wireless dongles
- NVIDIA on Reflex / latency optimization
- Microsoft on vulnerable driver blocklist and platform security

(See the legacy README for additional links; this curated README focuses on what is reliably beneficial for esports gaming.)
