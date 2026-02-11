# PC#1 Valorant Profile (Ryzen 7 9800X3D + RTX 2080 Ti)

This profile is tailored to **stable, low-latency VALORANT** on PC#1 (Ryzen 7 9800X3D + RTX 2080 Ti).

## Goals
- Consistent frametimes (low spikes, strong 1% / 0.1% lows)
- Low *and predictable* end-to-end latency
- High stability (no WHEA errors, driver resets, Vanguard issues)
- Minimal security / maintenance downsides

## Quick checks (before tuning)
- Update BIOS to a stable release for your board (avoid beta unless needed).
- Enable **UEFI + Secure Boot + TPM 2.0** (required for Windows 11 + Vanguard on many setups).
- Install a known-stable NVIDIA driver branch (clean install if you have issues).
- Ensure the system is not thermal/power throttling under VALORANT load.

## Tier 1 (highest ROI, lowest risk)
1. **Enable NVIDIA Reflex** in VALORANT (start with *On*).
2. Pick a **stable FPS cap** you can hold (optimize for 1%/0.1% lows, not peak FPS).
3. If you use a wireless mouse: place the dongle on a **USB 2.0 extension** away from USB 3.x ports/cables.
4. Close unnecessary background apps that hook input/overlays (RGB suites, capture overlays) during matches.
5. Keep Windows security features enabled; avoid “debloat” and kernel-driver hacks.

## Tier 2 (measure-first)
- **Reflex On + Boost** and/or NVCP “Prefer maximum performance” (only if you see downclocking or GPU latency variance).
- Game Mode / Xbox Game Bar: A/B test (keep what yields fewer spikes).
- MSI/MSI-X enabling: only on devices that are known-good and only with rollback.

## Avoid (high risk / low expected upside)
- Disabling Defender / Firewall
- Disabling Windows Update entirely
- Disabling Microsoft vulnerable driver blocklist to load low-level tools (RWEverything, etc.)
- Renaming system files (SmartScreen, microcode DLLs)
- Disabling CPU security mitigations (Spectre/Meltdown/Downfall)
- RWEverything-based XHCI IMOD scripts (anti-cheat/security risk)

## Measurement loop
Baseline -> change one thing -> measure -> keep/revert.

Recommended tools:
- PresentMon / CapFrameX for frametime graphs
- In-game VALORANT stats + network graphs (packet loss/jitter)
- xperf DPC/ISR trace when diagnosing driver interrupt spikes

## References
- Riot: Vanguard Restrictions (Windows 11 security requirements) — https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions
- Intel/USB-IF: USB 3.0 RF interference with 2.4GHz devices — https://www.usb.org/sites/default/files/327216.pdf
- NVIDIA: System latency optimization guide — https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/
