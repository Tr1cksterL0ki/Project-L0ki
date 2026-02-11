# Ryzen X3D CPU Setup (PC#1 focus)

This page covers conservative, esports-friendly setup for **Ryzen X3D** CPUs (PC#1: Ryzen 7 9800X3D).
Goal: **consistent frametimes** and **stability**.

## 1) BIOS/UEFI (safe defaults)
✅ Do
- Update BIOS to a stable release for your motherboard.
- Enable UEFI + Secure Boot + TPM 2.0 (Windows 11 + Vanguard friendly).
- Enable your memory profile (EXPO/DOCP) **only if stable**.
- Enable CPPC / preferred cores (leave default unless you have a reason).

⚠️ Consider
- PBO: leave on Auto / Motherboard default initially.
- Curve Optimizer (negative): try small steps and validate stability (WHEA-free).

❌ Avoid
- Manual all-core overclocks on X3D for gaming: high risk / low gain.
- Extreme CO values copied from others.

## 2) Windows power behavior
- Start on **Balanced**.
- Avoid extreme power plans unless you have measured benefits.
- If you see frequency “yo-yo” correlated with frametime spikes, test small adjustments one at a time.

## 3) Stability validation
After any BIOS change:
- Run a CPU stability test (and then **play VALORANT** for at least an hour).
- Watch for WHEA errors, random reboots, driver crashes, USB disconnects.

Rollback: revert the last change, or load BIOS defaults.
