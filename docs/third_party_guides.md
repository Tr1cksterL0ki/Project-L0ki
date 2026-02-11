# Third-party guides (what we keep vs reject)

This repo cross-references popular communities and guides, but does **not** endorse everything in them.

## PC-Tuning (valleyofdoom/PC-Tuning)
Useful for:
- structured checklists that encourage **A/B testing**
- measurement tooling (PresentMon, xperf, etc.)

We reject (for a VALORANT PC) any guidance that:
- weakens Windows/platform security (Defender off, firewall off, exploit mitigations off)
- disables the Microsoft Vulnerable Driver Blocklist to run kernel-driver tools (Vanguard risk)
- relies on undocumented/unsafe driver poking (RWEverything, “IMOD scripts”, etc.)

References:
- Microsoft vulnerable driver blocklist (why it exists / how it’s controlled):  
  https://support.microsoft.com/en-gb/topic/kb5020779-the-vulnerable-driver-blocklist-after-the-october-2022-preview-release-3fcbe13a-6013-4118-b584-fcfbc6a09936
- Riot Vanguard compliance expectations (Secure Boot / TPM / security posture):  
  https://support-valorant.riotgames.com/hc/en-us/articles/22291331362067-Vanguard-Restrictions

## PC-Optimization-Hub (BoringBoredom)
Useful for:
- good peripheral fundamentals (USB placement, wireless interference awareness)
- practical “reduce background junk” advice

We removed or rewrote:
- xHCI IMOD / interrupt “register hacks” (high-risk, low-confidence, and often requires vulnerable drivers)
- “disable security for performance” patterns

## Calypto’s latency guide
Good for:
- conceptual framing (latency pipeline, why spikes matter)
- reminders to measure instead of chasing placebo

Risky sections to treat as **non-default**:
- broad security disable recommendations
- “runtime downgrades” or OS tampering steps presented as gameplay fixes

## Community threads (Reddit/YouTube/Discord)
We treat these as hypotheses until confirmed by:
- official docs
- reputable labs / reproducible measurements

Tip: if a tweak cannot be described as a *mechanism* and measured with a simple A/B test, assume it’s placebo until proven otherwise.
