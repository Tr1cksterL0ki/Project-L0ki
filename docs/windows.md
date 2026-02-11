# Windows configuration (safe, VALORANT-friendly)

This is a curated set of **low-risk** changes. It explicitly avoids:
- disabling Windows security (Defender, firewall)
- disabling kernel mitigations
- “debloat scripts” that break updates or components

## Keep Windows updated, but avoid preview updates
- Prefer normal monthly security updates.
- Skip optional “Preview” updates unless they fix a problem you have.
- If a bad patch hits, follow Microsoft’s **Windows Release Health / Known Issues** for your Windows version.

## Background load: remove the real offenders
✅ Do
- Disable unnecessary startup apps (Task Manager → Startup)
- Uninstall unused RGB/peripheral suites and overlays (or stop them from auto-starting)
- Disable Xbox Game Bar *if you don’t use it*

⚠️ Consider
- Disable Search indexing **only if** you can see it causing disk/CPU activity during play

❌ Avoid
- Disabling Windows Update entirely
- Disabling Microsoft Defender entirely
- Renaming system executables (e.g., SmartScreen)

## Game Mode + windowed game optimizations
- **Game Mode:** keep it **ON** unless you can prove a regression.
  - Microsoft: https://support.microsoft.com/en-us/windows/5c94107e-a537-206e-e9e9-20600523bc43
- **Optimizations for windowed games:** if you play borderless, understand this feature and test it (some systems see improvements, others don’t).
  - Microsoft: https://support.microsoft.com/en-us/windows/optimizations-for-windowed-games-in-windows-11-3f006843-2c7e-4ed0-9a5e-f9389e535952

## Hardware-Accelerated GPU Scheduling (HAGS)
Treat HAGS as a **toggle to A/B test**, not a universal “ON is better” tweak.
- If you get stutter or frametime spikes after changing GPU drivers or Windows builds, test HAGS **ON vs OFF** and keep whichever is cleaner.

## Paging file
Don’t disable it. Some games still stutter without a page file even on high-RAM systems.

## Visual C++ runtimes
Don’t “downgrade runtimes for hitreg.”
If you suspect runtime corruption, reinstall the **latest supported** Visual C++ redistributables from Microsoft.
- Microsoft: https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170

## Timer / “HPET” tweaks
Do not chase timer myths. Modern Windows timing behavior varies by build and hardware.
Only touch timer behavior if you can show a repeatable improvement in frametime/latency.

## Core isolation / Memory Integrity (HVCI/VBS)
This is a security vs performance trade.
For VALORANT, Vanguard restrictions can require security features depending on your environment:
- https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions

If you change it, measure and keep a rollback plan.

## Useful built-in + legit tools
- Sysinternals Process Explorer: https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer
- Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- PresentMon / CapFrameX (frametime capture): see https://github.com/Tr1cksterL0ki/Project-L0ki/blob/main/docs/measurement.md
