# PC-Tuning (2026) — Stable Low-Latency VALORANT  
**Target system (current focus): Ryzen 7 9800X3D (AM5) + GeForce RTX 2080 Ti (Turing) + Windows 11**

> [!CAUTION]
> **Stability > “secret tweaks.”** For esports, consistent frame times and reliable input/network latency beat fragile peak benchmarks.
>
> [!CAUTION]
> **Change one thing at a time.** Every section includes a rollback and a “how to measure” note. Don’t stack 20 tweaks and guess.
>
> [!CAUTION]
> **No anti-cheat hostile hacks.** Avoid modified OS builds, kernel driver loaders, “blocked driver” tools, and security-bypass methods.
> These can break Vanguard and/or lower system integrity.

---

## Table of Contents
- [0. Quick Start Checklist (15–30 minutes)](#0-quick-start-checklist-1530-minutes)
- [1. What “better” means in VALORANT](#1-what-better-means-in-valorant)
- [2. Measurement First (baseline + tools)](#2-measurement-first-baseline--tools)
- [3. BIOS/UEFI (AM5 / 9800X3D)](#3-biosuefi-am5--9800x3d)
- [4. USB Ports & Peripherals (mouse/keyboard/headset)](#4-usb-ports--peripherals-mousekeyboardheadset)
- [5. Windows 11 Configuration (safe defaults)](#5-windows-11-configuration-safe-defaults)
- [6. NVIDIA Driver + GPU Settings (RTX 2080 Ti)](#6-nvidia-driver--gpu-settings-rtx-2080-ti)
- [7. VALORANT In-Game Settings (latency + stability)](#7-valorant-in-game-settings-latency--stability)
- [8. Network Basics (ping, jitter, packet loss)](#8-network-basics-ping-jitter-packet-loss)
- [9. Hardware Stability: temps, undervolt, memory](#9-hardware-stability-temps-undervolt-memory)
- [10. Advanced / Niche Tweaks (only if measured)](#10-advanced--niche-tweaks-only-if-measured)
- [11. Do-Not-Use List (common myths & high-risk changes)](#11-do-not-use-list-common-myths--high-risk-changes)
- [12. References (primary sources)](#12-references-primary-sources)

---

## 0. Quick Start Checklist (15–30 minutes)

### ✅ Do now
- [ ] Update BIOS to the latest **stable** vendor release (AM5 stability + security + memory training improvements).
- [ ] Enable **TPM 2.0** + **Secure Boot** (VALORANT on Windows 11 requires these; otherwise VAN errors).  
- [ ] Install latest **AMD Chipset** drivers and GPU driver (clean install if coming from an older branch).
- [ ] Use **wired Ethernet** if possible (packet loss/jitter matters more than tiny “OS tweaks”).
- [ ] In VALORANT: turn **NVIDIA Reflex = ON** (or ON+BOOST only if needed—see below).
- [ ] Close heavy background apps (browser tabs, video capture you don’t need, RGB suites if they’re misbehaving).
- [ ] Establish a **baseline**: record frametime stability + in-game packet loss/jitter graphs.

### ⚠️ Only if you have symptoms
- [ ] USB “random disconnects” / input spikes → check USB topology and disable selective suspend **only** for the affected hub/controller.
- [ ] GPU downclocking / inconsistent FPS → set NVIDIA “Prefer maximum performance” **for VALORANT only** and/or test Reflex ON+BOOST.
- [ ] Thermal throttling → clean dust, fix fan curves, consider a mild undervolt.

Rollback: every item above is reversible (BIOS options can be reset to defaults; driver settings can be restored; VALORANT settings are in-game).

---

## 1. What “better” means in VALORANT
For competitive play, optimize in this order:
1. **Frame time consistency** (stutter-free 1%/0.1% lows)
2. **Input-to-photon latency** (your click → server → frame displayed)
3. **Network stability** (packet loss/jitter = inconsistent fights even at “good ping”)
4. Average FPS (only matters if it improves the above)

> [!NOTE]
> If you “die instantly” while peeking, some of it is normal **peeker’s advantage math** (frametime + one-way latency + server tick + interpolation).

---

## 2. Measurement First (baseline + tools)

### Recommended tools
- **PresentMon** (frametime capture / frame pacing).  
- **NVIDIA FrameView** (frametimes + optional PC latency in supported titles).
- **VALORANT in-game graphs**: FPS, Frame Time, Packet Loss (in/out), Jitter, RTT/Ping.

### Baseline procedure (10 minutes)
1. Reboot.
2. Run VALORANT Practice Range for 3–5 minutes.
3. Record:
   - Average FPS, 1% low, biggest frametime spikes
   - GPU utilization (is the 2080 Ti pinned at 99%?)
   - In-game packet loss/jitter graphs

**Rule:** only keep a tweak if it reduces spikes or improves repeatable latency—not just “feels smoother once.”

---

## 3. BIOS/UEFI (AM5 / 9800X3D)

### ✅ Must-have
- **Update BIOS** (AM5 memory training + stability improves over time).
- **Enable TPM 2.0** (fTPM) and **Secure Boot** (Windows 11 + Vanguard).  
  - If Secure Boot/TPM is off, VALORANT can fail with VAN9001/VAN9003.  
- **EXPO memory profile**: enable the rated DDR5 kit profile (then test stability).  
- **Resizable BAR**: for RTX 2080 Ti, treat this as **unsupported** by NVIDIA (don’t BIOS-mod to force it). (NVIDIA’s official ReBAR firmware update tool is for RTX 30-series only.)

### ✅ Recommended defaults for esports stability
- **Precision Boost / boosting**: leave default unless you have a proven stability issue.
- **Global C-states**: leave enabled unless you can prove idle-state transitions cause spikes (rare).
- **CPPC / Preferred cores**: enable (defaults on most boards).

### ⚠️ Optional (measure first)
- **Curve Optimizer (CO)**: try mild negative offsets *only after* you have a stable baseline.  
  - Goal: lower temps / reduce throttling / improve sustained boost—not “max benchmark score.”
- **PBO limits**: for X3D chips, avoid aggressive “one-click” BCLK/boost profiles unless you can stress-test thoroughly.

### Rollback
- BIOS: “Load Optimized Defaults” → re-enable only EXPO + Secure Boot/TPM.
- If the system becomes unstable after memory changes: disable EXPO and retest.

---

## 4. USB Ports & Peripherals (mouse/keyboard/headset)

### ✅ Port layout (high ROI, low risk)
- Prefer plugging **mouse + keyboard** directly into motherboard USB ports (avoid front-panel hubs if possible).
- If your board has multiple USB controllers, spread devices:
  - Controller A: mouse + keyboard  
  - Controller B: headset DAC / webcam / capture device

### ✅ Polling rate guidance
- Start at **1000 Hz**.
- If you run 2000/4000/8000 Hz, watch for:
  - Higher CPU usage
  - Frametime spikes
  - USB stutter when multiple devices share one hub/controller

### ⚠️ Selective suspend / power saving
Only change if you have symptoms (mouse disconnects, USB sleep/wake glitches):
- Device Manager → USB Root Hub / Generic USB Hub → Power Management → uncheck “Allow the computer to turn off…”

Rollback: re-check the box.

> [!CAUTION]
> Avoid “xHCI interrupt moderation hacks” (RWEverything / blocked drivers). They’re high-risk and often require security compromises.

---

## 5. Windows 11 Configuration (safe defaults)

### ✅ Keep
- **Windows Security / Defender ON**
- **Firewall ON**
- **Core OS security features ON** unless you have a specific measured reason

### ✅ Recommended
- **Game Mode**: leave ON (test if you suspect issues).
- **Disable background capture** if you don’t use it (Xbox Game Bar captures).
- **Startup apps**: disable obvious junk (RGB suites that misbehave, auto-updaters you don’t need while playing).

### ✅ Power plan
- Start with **Balanced**.
- If you see frequency downclock / inconsistent boost while gaming, test **High Performance** and compare frametime spikes.

Rollback: switch plan back.

### ⚠️ Updates
- Prefer stable cumulative/security updates; avoid “Preview” updates unless they fix a bug you have.
- If an update causes stutter/crashes, roll back and pause updates temporarily (don’t permanently disable Windows Update).

---

## 6. NVIDIA Driver + GPU Settings (RTX 2080 Ti)

### ✅ Baseline driver approach
- Use a **clean install** if you’re coming from very old drivers or have unexplained stutter.
- Avoid “debloated driver packs” unless you can reproduce and roll back reliably.

### NVIDIA Control Panel (Program Settings → VALORANT)
Recommended starting point:
- **Low Latency Mode:** OFF (use Reflex in-game instead)
- **Power management mode:** Normal  
  - If you see downclocking or inconsistent GPU clocks: test **Prefer maximum performance**
- **Vertical sync:** OFF
- **Triple buffering:** OFF

### ✅ GPU undervolt (often improves consistency)
A mild undervolt can reduce heat/power spikes and help frametimes.
- Change one step at a time (voltage/frequency curve)
- Validate in VALORANT + a GPU stress test

Rollback: reset curve to default.

---

## 7. VALORANT In-Game Settings (latency + stability)

### ✅ Latency-critical
- **NVIDIA Reflex:** ON  
  - Use **ON + BOOST** only if your GPU is frequently downclocking or you’re chasing the last few ms and temps are fine.
- **FPS cap:** pick a cap that keeps frametimes consistent.
  - If you use VRR (G-SYNC Compatible / FreeSync): cap a few FPS below max refresh to avoid “ceiling” behavior.
  - If no VRR: cap where 1% lows are stable and GPU isn’t pinned at 99% constantly.

### ✅ Network
- Turn on network graphs.
- If you see packet loss/jitter, adjust **Network Buffering** to stabilize (it trades a little delay for fewer “network pops”).

---

## 8. Network Basics (ping, jitter, packet loss)

### ✅ Priorities
1. **Packet loss = 0%** (or as close as possible)
2. Low jitter (stable connection)
3. Lower ping

### ✅ Actions that usually work
- Use **Ethernet**.
- Reboot modem/router occasionally (if you suspect bufferbloat or instability).
- Avoid powerline adapters if they’re noisy.
- Don’t disable your firewall “for ping.”

### ⚠️ Port forwarding
Only consider if you have actual **connectivity/voice** issues. It usually does *not* reduce ping.

---

## 9. Hardware Stability: temps, undervolt, memory

### ✅ Cooling and thermals
- Keep CPU/GPU temps under control to avoid throttling-induced spikes.
- Set sensible fan curves (avoid rapid ramping that creates oscillation).

### ✅ Memory stability (AM5)
- EXPO is great when stable.
- If you get crashes/WHEA errors:
  - Lower memory speed one step or use a more conservative EXPO profile
  - Update BIOS (memory training improvements)

---

## 10. Advanced / Niche Tweaks (only if measured)

These are for **specific symptoms**—not “default tuning.”

- CPU Curve Optimizer tuning (per-core if possible)
- Per-device power management changes (USB/NIC) only when you’ve identified the culprit
- VRR + FPS cap strategy based on your monitor/GPU headroom

If you can’t measure the effect, don’t do it.

---

## 11. Do-Not-Use List (common myths & high-risk changes)

❌ Avoid for a competitive VALORANT PC:
- Disabling **Defender**, **Firewall**, or broad OS security mitigations
- Modified Windows builds / “debloat OS” images
- “Timer resolution / HPET / dynamic tick” folklore tweaks as a default
- Standby-list cleaners on a schedule
- Forcing Resizable BAR or BIOS-mods for RTX 2080 Ti
- USB controller register hacks requiring risky tools/drivers

---

## 12. References (primary sources)
- Riot: **Troubleshooting VAN9001/VAN9003/VAN9090 (Windows 11)** — TPM 2.0 + Secure Boot required  
  https://support-valorant.riotgames.com/hc/en-us/articles/10088435639571-Troubleshooting-the-VAN-9001-VAN-9003-or-VAN-9090-Error-on-Windows-11-VALORANT
- Riot: **Vanguard Restrictions** (platform security posture)  
  https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions
- Riot: **On Peeker’s Advantage** (explains interpolation delay + why fights can feel “instant”)  
  https://playvalorant.com/en-us/news/game-updates/04-on-peeker-s-advantage-ranked/
- NVIDIA: **Understanding and Measuring PC Latency** (I2FS/FS2P/P2D pipeline concepts)  
  https://developer.nvidia.com/blog/understanding-and-measuring-pc-latency/
- NVIDIA: **Aiming Faster in Games with Low System Latency** (latency affects performance; 2080 Ti used in study)  
  https://developer.nvidia.com/blog/aiming-faster-in-games-with-low-computer-system-latency/
- PresentMon (frametime capture / frame pacing)  
  https://github.com/GameTechDev/PresentMon
- NVIDIA: Resizable BAR firmware update tool (RTX 30-series)  
  https://nvidia.custhelp.com/app/answers/detail/a_id/5165/


