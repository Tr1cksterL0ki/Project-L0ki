# VALORANT settings (low-latency + consistency)

## Key reality: peeker’s advantage is math
Riot breaks it down as a sum of:
- enemy frametime
- enemy one-way lag
- server frametime (128 tick)
- your one-way lag
- interpolation delay (tunable via Network Buffering)

Source: https://playvalorant.com/en-us/news/game-updates/04-on-peeker-s-advantage-ranked/

### What that means
The most reliable “feel” improvements come from:
1) reducing **frametime spikes**
2) reducing **packet loss / jitter**
3) reducing **ping** (server selection / routing)

## Network buffering
If you see instability icons or loss, Riot recommends using buffering and fixing the underlying connection quality.
- Network instability basics: https://playvalorant.com/en-us/news/game-updates/valorant-game-and-network-instability-basics/

Rule of thumb:
- **Clean connection:** keep buffering low
- **Loss/jitter present:** increase buffering to trade a small delay for fewer drops/pops

## NVIDIA Reflex (RTX 2080 Ti)
- Start with **Reflex: ON**
- Only use **ON + BOOST** if you confirm your GPU clocks are downshifting during fights and it improves frametime consistency.

Reflex references:
- Reflex overview: https://www.nvidia.com/en-us/geforce/news/reflex-low-latency-platform/
- System latency optimization guide (Reflex vs driver low-latency mode):  
  https://www.nvidia.com/en-us/geforce/guides/gfecnt/202010/system-latency-optimization-guide/

## FPS cap guidance
Pick a cap you can hold with strong 1% lows:
- For VRR users: cap a few FPS below max refresh
- For fixed refresh: cap at a stable target (often lower than your peak)

Avoid chasing “max FPS” if it causes spikes.

## Graphics settings (practical)
Competitive baseline usually prefers:
- Low/Medium settings where they reduce spikes
- Avoid settings that create large VRAM/CPU spikes
- Keep temps controlled to prevent throttling

## Display / monitor
- Use the monitor’s **Game Mode / low-latency preset** (turn off heavy post-processing like motion interpolation).
- If you use VRR, verify your OSD shows VRR active in-game.

## NVIDIA Control Panel (RTX 2080 Ti)
- Prefer configuring latency in-game via **Reflex**.
- If Reflex is enabled in-game, leave **Low Latency Mode** off to avoid redundant/contradictory settings (Reflex takes priority in supported games).
- Consider “Prefer maximum performance” **per-game** only if you observe downclock-related spikes (watch GPU clocks/temps).
