# VALORANT Network & “Desync” Feel (Verified Guidance)

VALORANT “dying before you see them” is often explained by **peeker’s advantage + frametime + network stability**.
Before chasing PC tweaks, confirm whether the issue is **packet loss/jitter**, **frametime spikes**, or simply expected peeker’s advantage.

## 1) Riot’s peeker’s advantage components (concept)
Peeker’s advantage is influenced by:
- both players’ frametimes
- one-way lag (ping/2)
- server tick frametime
- network interpolation (buffering)

Practical takeaway: reduce **frametime spikes**, fix **packet loss/jitter**, and keep **ping** low and stable.

## 2) Packet loss first
If you see network warnings or packet loss:
- Prefer **wired Ethernet**
- Reboot modem/router
- Remove Wi‑Fi extenders / powerline adapters during testing
- Try a different server/route if your ISP path is poor
- Use **Network Buffering** if you have unstable internet (tradeoff: slightly more interpolation delay)

## 3) Port forwarding
Port forwarding can help if your router is blocking connectivity, but it is **not** a general “reduce ping / improve hitreg” knob.
Only do it when troubleshooting connection problems and undo it if it doesn’t help.

## 4) Firewall
Do **not** disable Windows Firewall as a “performance tweak.”
If something is blocked, allow the specific app/rule instead.

## 5) Measurement plan
Baseline -> one change -> retest:
- In-game: ping graph, packet loss graph, network warning indicator frequency
- Frametime graphs (PresentMon/CapFrameX)

## References
- Riot: Peeker’s advantage breakdown — https://playvalorant.com/en-us/news/game-updates/04-on-peeker-s-advantage-ranked/
- Riot: Game & network instability basics — https://playvalorant.com/en-us/news/game-updates/valorant-game-and-network-instability-basics/
- Riot Support: Port forwarding (connectivity troubleshooting) — https://support-valorant.riotgames.com/hc/en-us/articles/4402306473619-How-to-Set-Up-Port-Forwarding
- Microsoft: Firewall guidance (don’t disable; allow apps/rules) — https://support.microsoft.com/en-us/windows/firewall-and-network-protection-in-the-windows-security-app-ec0844f7-aebd-0583-67fe-601ecf5d774f
