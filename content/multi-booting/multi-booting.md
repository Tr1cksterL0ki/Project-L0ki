# Dual-booting (optional, advanced)

A separate “gaming OS” can be convenient, but **multi-booting is not required** for low latency and it can create security/anti-cheat headaches if done wrong.

For VALORANT on Windows 11, Riot Vanguard generally expects:
- UEFI boot
- Secure Boot enabled
- TPM 2.0 enabled

See: https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions

## What this repo recommends
✅ If you dual-boot:
- use **supported Windows builds** (don’t use ancient releases “for performance”)
- keep **UEFI + Secure Boot** (avoid enabling CSM for “compatibility”)
- prefer a **separate drive** if possible (simpler recovery)

❌ Avoid
- Windows 7 for VALORANT (incompatible with modern Vanguard expectations)
- partitioning “tricks” that require old installers or disabling security features

## Minimal safe approach (high level)
1) Back up important data
2) Shrink your main partition in Disk Management
3) Install Windows to the new space (still UEFI)
4) Re-enable/verify Secure Boot + TPM state after installation

This guide intentionally avoids step-by-step partition surgery; errors here can be catastrophic. If you need a full tutorial, use a reputable Windows dual-boot guide and validate that Secure Boot remains enabled afterwards.
