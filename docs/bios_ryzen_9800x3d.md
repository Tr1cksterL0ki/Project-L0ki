# BIOS / UEFI baseline (Ryzen 7 9800X3D)

Goal: **stable boosts + stable memory + no thermal throttling**, while staying **Vanguard-compliant**.

## Always do (high ROI / low risk)

### 1) Update BIOS (and chipset drivers)
- Update to a **stable** BIOS for your motherboard (avoid “beta” unless you need a specific fix).
- After updating, **load optimized defaults**, then re-apply only the settings you actually use.

### 2) Keep VALORANT / Windows 11 requirements satisfied
Riot’s Vanguard guidance for Windows 11 generally expects:
- **UEFI boot**
- **Secure Boot enabled**
- **TPM 2.0 enabled**
- (in some environments) **IOMMU + VBS/HVCI (Memory Integrity)**

Source: Vanguard Restrictions (Riot):  
https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions

> Practical takeaway: **don’t enable CSM** just to “simplify” booting. Keep the platform modern and compliant.

### 3) Memory (EXPO) first, then stability
- Enable your kit’s **EXPO profile** (or whatever your board calls it).
- Validate stability *before* you touch PBO/Curve Optimizer.

**How to validate (quick + useful):**
- 2–3 long VALORANT sessions (watch for WHEA errors / crashes)
- A memory test you trust (Karhu, TM5, etc.)
- If you see WHEA or random app crashes: back off memory settings first.

### 4) PCIe / ReBAR (only if supported)
- Enable **Above 4G Decoding**.
- Enable **Resizable BAR** *only if your GPU + VBIOS support it*. RTX 20-series support can vary by vendor model.

## Optional (measure-first)

### PBO + Curve Optimizer (CO)
**Why people do it:** lower voltage/temps can improve sustained boost and reduce throttling, which can improve **frametime consistency**.

**Reality check for X3D parts:**
- Zen 5 X3D parts allow PBO/CO adjustments on many boards, but the “best” values are highly silicon- and cooling-dependent.
- Go conservative: a stable, cool CPU beats a fragile high-boost profile in esports.

A starting approach (safe-ish):
1) Leave PBO on **Auto** first; test stock behavior.
2) If you optimize, use **small negative CO** steps and test stability.
3) Avoid “maxing out” limits blindly (PPT/TDC/EDC) unless you understand your thermals.

General context (review / discussion of the part and boosting behavior):
- HotHardware review (overview): https://hothardware.com/reviews/amd-ryzen-7-9800x3d-processor-review

### C-states / power idle controls
Avoid blanket “disable all C-states” recommendations.
Only consider changing idle behavior if you can **prove** wake-latency spikes or stutter that correlates with idle transitions.

## What to leave alone unless you know why

- **Spread Spectrum**: usually leave default unless you’re diagnosing EMI or extreme OC edge cases.
- **SVM/Virtualization toggles**: don’t change these unless you have a reason. Vanguard guidance can sometimes prefer security features rather than less.

## Quick rollback plan
If anything regresses:
1) Revert to BIOS defaults (save a photo of your settings first)
2) Re-enable only: UEFI/Secure Boot/TPM + EXPO + fan curves
3) Re-test frametime stability and crash rate

