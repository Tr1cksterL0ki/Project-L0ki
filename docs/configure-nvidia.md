<h1 id="configure-the-nvidia-driver">Configure the NVIDIA Driver <a href="#configure-the-nvidia-driver">(permalink)</a></h1>

This page is optimized for **VALORANT** and PC#1’s GPU (**RTX 2080 Ti**).

> [!IMPORTANT]
> **Start with in-game NVIDIA Reflex.** Driver “tweaks” are secondary and should be A/B tested.

## 1. Clean driver strategy (safe)
### 1.1 Pick a stable driver
- Prefer a **known-stable Game Ready** driver for your GPU.
- Update only when you need a fix/security patch, or when you can afford to validate stability.

### 1.2 Install with minimal components (no file hacking)
Use NVIDIA’s installer and select **Custom (Advanced)**:
- ✅ **Graphics Driver**
- ✅ **PhysX**
- ⚠️ **HD Audio** (only if you use HDMI/DP audio)
- ⚠️ **USB-C / VirtualLink** (only if you actually use it)
- ❌ Avoid editing `setup.cfg` or repacking installers. It’s fragile and creates troubleshooting debt.

If you are troubleshooting a broken driver state, a clean reinstall can help; otherwise prefer simple updates.

## 2. VALORANT settings (highest ROI)
### 2.1 NVIDIA Reflex (in-game)
- Set **NVIDIA Reflex Low Latency** to **On** (baseline).
- Consider **On + Boost** only if:
  - you observe GPU downclocking during matches, or
  - you can measure reduced latency / improved frametime stability without higher spikes.

> Note: Reflex replaces most of what “Low Latency Mode” (ULLM) used to do; don’t stack random latency features without measuring.

## 3. NVIDIA Control Panel (NVCP)
Create a **Program Settings** profile for `VALORANT-Win64-Shipping.exe` and start with:

- **Power management mode**
  - Default: **Normal/Optimal**
  - If you see downclocking or latency variance: **Prefer maximum performance** (per-game)

- **Low Latency Mode**
  - **Off** when using Reflex (keep it simple; avoid feature stacking)

- **Vertical sync**
  - For competitive latency: **Off**
  - If you use VRR (G-SYNC Compatible): use a stable cap and avoid running pinned at 99% GPU.

- **Texture filtering quality**
  - Use **High performance** only if you need the FPS; otherwise leave default.

Everything else: leave defaults unless you have a reason and a measurement plan.

## 4. Avoid / deprecated
### 4.1 Registry hacks to “lock P-states”
Older guides recommend registry flags like `DisableDynamicPstate` to force high clocks.
This is **not recommended** here:
- it increases heat/power and can worsen frametime spikes via thermals,
- it’s unsupported and increases maintenance burden.

Prefer supported levers first:
- Reflex **On + Boost** (if needed)
- NVCP **Prefer maximum performance** (per-game)

## 5. How to test safely (A/B)
1. Baseline 10–15 minutes of DM/TDM + one match
2. Change one variable (e.g., Reflex Boost or NVCP power mode)
3. Measure:
   - frametime spikes (PresentMon/CapFrameX)
   - in-game latency stats (if available)
4. Keep only if:
   - 1%/0.1% lows improve **and**
   - spikes reduce **and**
   - no new instability/thermal throttling

Rollback is always: revert NVCP setting / revert in-game Reflex / clean reinstall driver if needed.

## References
- NVIDIA: System latency optimization / Reflex overview — https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/
- NVIDIA: Reflex Low Latency Platform — https://www.nvidia.com/en-us/geforce/news/reflex-low-latency-platform/
