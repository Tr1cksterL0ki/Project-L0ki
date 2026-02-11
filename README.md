# Project L0ki (L0ki's PC: Ryzen 7 9800X3D + RTX 2080 Ti)

A **measurement-first** optimization hub for **stable, low-latency VALORANT**:
- prioritize **frame-time consistency** (1%/0.1% lows, spike frequency)
- reduce **end-to-end latency** where it’s measurable (render queue, clocks, input stability)
- avoid “tweaks” that are **security regressions**, **anti-cheat hostile**, or **hard to roll back**

> This repo is tailored to **L0ki's PC** (Ryzen 7 9800X3D + RTX 2080 Ti). Most items still apply generally, but the defaults and examples assume an AM5 X3D CPU and an NVIDIA Turing GPU.

---

## Core principles

1. **Stability > peak benchmarks** (esports cares about spikes, not one good run).
2. **One change at a time**. Always keep a rollback path (restore point / notes).
3. **No anti-cheat bypasses.** If a step weakens platform security or relies on loading vulnerable drivers, it’s out-of-scope for VALORANT.
4. **Prefer documented mechanisms** over folklore (especially around timers/interrupts).

---

## Quick start (highest ROI / lowest risk)

### A. Game + GPU (do these first)
- **VALORANT:** enable **NVIDIA Reflex: ON** (test **ON + BOOST** only if you confirm GPU downclocking / frametime variance).
  - NVIDIA Reflex overview:  
    https://www.nvidia.com/en-us/geforce/news/reflex-low-latency-platform/
- Use a **frame cap you can hold** with clean 1% lows. If you use VRR (G-SYNC/FreeSync), cap a few FPS below max refresh (e.g., **237 for 240 Hz**).
- **RTX 2080 Ti note:** if you see frequency oscillation during play, try setting **Power management mode → Prefer maximum performance** *for VALORANT only* (NVIDIA Control Panel per-game profile), then re-test frametime variance.

### B. Network (the “dying too fast” reality check)
- Riot explains peeker’s advantage as a sum of frametime + one-way lag + server frametime + interpolation delay:  
  https://playvalorant.com/en-us/news/game-updates/04-on-peeker-s-advantage-ranked/
- If you see packet-loss icons or inconsistent fights, follow Riot’s network instability guidance (enable graphs, try Ethernet, adjust **Network Buffering**):  
  https://playvalorant.com/en-us/news/game-updates/valorant-game-and-network-instability-basics/

### C. Peripherals / USB
- If you use a **wireless 2.4 GHz mouse/keyboard**, keep the dongle away from active USB 3.x ports/cables (USB 3 can interfere with 2.4 GHz).  
  USB-IF / Intel whitepaper: https://www.usb.org/sites/default/files/327216.pdf
- Close unnecessary background “peripheral suites” and overlays while playing (RGB suites can add background load and sometimes extra input hooks).
- Start at **1000 Hz polling** and increase only if frametime remains clean (see: https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/content/peripherals/mouse%20faq.md).

---

## Start here (docs)

- **Measurement & test workflow:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/measurement.md
- **VALORANT settings & network buffering:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/valorant.md
- **Windows settings that are actually worth doing:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/windows.md
- **USB layout & wireless stability:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/usb.md
- **BIOS / Ryzen 9800X3D baseline:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/bios_ryzen_9800x3d.md
- **Do-not-use (unsafe / low-value tweaks):** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/do_not_use.md
- **Third-party guide notes:** https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/third_party_guides.md

---

## What changed vs the original upstream hub?

This repo removes or rewrites content that commonly causes harm for competitive PCs:
- **No RWEverything / vulnerable driver workflows** (high security + Vanguard risk)
- No “disable all security features” playbooks (Defender off, exploit mitigations off, etc.)
- No “use ancient Windows builds / enable CSM” suggestions (conflicts with Secure Boot requirements)

---

## Contributing

If you add a tweak, include:
1) exact location + rollback  
2) mechanism  
3) evidence (prefer primary docs)  
4) a simple A/B test plan  

---

## Changelog
- https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/CHANGELOG.md
