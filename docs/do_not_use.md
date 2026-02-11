# Do-not-use list (unsafe / low-value for VALORANT)

These show up in “tweak culture” a lot. They are either:
- security regressions
- anti-cheat hostile
- or too unstable / low ROI

## Kernel / driver security bypasses
❌ Do not disable the **Microsoft Vulnerable Driver Blocklist** to run tools like RWEverything (security + Vanguard risk).
- Microsoft KB: https://support.microsoft.com/en-gb/topic/kb5020779-the-vulnerable-driver-blocklist-after-the-october-2022-preview-release-3fcbe13a-6013-4118-b584-fcfbc6a09936

❌ Do not use RWEverything-based scripts to change **xHCI IMOD / interrupt moderation registers** for a gaming PC.
- If you can’t explain the USB controller register-level change and validate it across sleep/resume, updates, and device hotplug, it’s not esports-safe.

## “Disable security for performance”
❌ Do not disable Microsoft Defender or the firewall for “performance.”
❌ Do not disable exploit mitigations, CPU security mitigations, or memory protections as a default.
❌ Do not disable Secure Boot / TPM 2.0 / UEFI requirements (VALORANT on Windows 11 can fail to launch or trigger Vanguard compliance errors).
- Riot Vanguard restrictions: https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions
- VAN9001/VAN9003 errors (Windows 11): https://support-valorant.riotgames.com/hc/en-us/articles/10088435639571-Troubleshooting-the-VAN-9001-VAN-9003-or-VAN-9090-Error-on-Windows-11-VALORANT

## “Debloated OS” images
❌ AtlasOS / ReviOS / random stripped Windows ISOs / unattended “gaming OS” images.
- These often break update servicing, security, and/or kernel features that anti-cheat expects.

## Networking myths
❌ Port-forwarding does not “reduce ping” on a healthy connection. Do it only for connectivity troubleshooting / NAT issues.
- Riot port forwarding guidance: https://support-valorant.riotgames.com/hc/en-us/articles/4402306473619-How-to-Set-Up-Port-Forwarding

## Folklore fixes
❌ Blindly downgrading Visual C++ runtimes to “fix hitreg” (if you suspect corruption, reinstall the latest supported runtimes instead).
- Microsoft VC++ redist: https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170

❌ “Clear standby list every 5 minutes” scheduled tasks.

❌ Timer superstition playbooks (HPET on/off, bcdedit platformclock toggles) without repeatable measurement.

## High-risk “tuning stacks”
❌ Applying 50 registry tweaks at once, then “feeling” smoother gameplay.
- The fastest way to waste time is to remove your ability to attribute cause → effect.
