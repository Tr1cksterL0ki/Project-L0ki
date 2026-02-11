# Mouse polling rate & testing (VALORANT)

## Polling vs. motion reports (practical)
For USB mice, the host schedules **interrupt transfers** at a fixed interval (for high-speed devices the minimum is typically **125 µs**, i.e. 8000 Hz). What your software *observes* can still vary depending on:
- system load / scheduling delay
- whether the app is in the foreground
- whether motion data is being produced (some sensors/buffers behave differently at low DPI or low movement)

**Competitive baseline:** start at **1000 Hz**, then A/B test 2000/4000/8000 only if frametime remains clean.

## MouseTester (what it measures)
MouseTester timestamps **raw input messages** it receives. That is **not** a perfect hardware-side polling oscilloscope; it is “messages delivered to this process.”

Repo tool: https://github.com/valleyofdoom/MouseTester

### Usage tips (to reduce measurement noise)
- Use very high DPI (e.g. 15k+) so sensor quantization doesn’t dominate the data.
- Close background apps that hook input (RGB suites, overlays, macro tools).
- Keep the MouseTester window **focused** (see next section).
- Move continuously while recording; avoid hitting taskbar/screen edges (UI collisions create spikes).

### Why `Frequency vs. Time` can show huge peaks
MouseTester converts interval → frequency (Hz = 1000 / ms).  
If one message is delayed by scheduling, the next delta can be smaller and look like an unrealistically high Hz “peak.”

TL;DR: prefer **Interval vs. Time** for sanity checks.

## “Why am I stuck at 8 ms / 125 Hz?”
On recent Windows 11 builds, background recipients of raw input may be **rate-limited** (with payload coalescing). That means a background app can “see” ~125 msg/s even if the device is actually higher-rate.

Explanation commonly quoted from a Microsoft engineer discussion thread:
https://reddit.com/r/Windows11/comments/109ca82/call_to_action_can_you_see_if_fps_drops_in_games/

**Fix for testing:** keep MouseTester **focused**.

## VALORANT guidance
- If you run 4k/8k polling and see frametime spikes: try 2k or 1k, and close background suites.
- Wireless users: put the dongle on a short USB2 extension and away from USB3 devices/cables (see Intel RFI note in README).
