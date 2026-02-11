# USB layout & wireless stability (low risk)

Goal: keep mouse/keyboard input **stable and consistent** (no micro-dropouts, no polling jitter).

## Why USB 3.x can matter for wireless mice
USB 3.0 devices/cables can emit interference in the 2.4 GHz band, which can reduce reliability for 2.4 GHz wireless dongles.

Reference (USB-IF / Intel whitepaper):  
https://www.usb.org/sites/default/files/327216.pdf

## Practical layout rules (works for most PCs)
✅ Do
- Prefer **rear motherboard ports** for competitive peripherals.
- If you use a **wireless 2.4 GHz dongle**, use a short **USB extension cable** and place the dongle closer to the mousepad (away from USB 3.x cables/devices).
- Keep high-activity USB 3 devices (external SSDs, webcams, capture devices) **away from** your wireless dongle port.

⚠️ Consider
- Use a **USB 2.0 port** for the dongle if you have one (many boards still provide some).
- Avoid chaining through a low-quality unpowered hub.

❌ Avoid
- Plugging a 2.4 GHz dongle directly next to a busy USB 3.x storage device/cable.
- Front-panel ports with long internal cables *if* you notice instability (they vary by case/board quality).

## How to test
1) Baseline a few deathmatches with your current layout.
2) Move only the dongle (USB2 port / extension cable / different side of the I/O cluster).
3) Re-test and watch for:
- micro-stutter coinciding with input
- audio/USB disconnect sounds
- packet loss icons that correlate with USB dropouts (rare, but happens with noisy setups)

If you have a wired mouse and still see issues, suspect software (overlays, RGB suites) or broader system instability rather than USB RFI.
