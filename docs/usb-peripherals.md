# USB & Peripherals (Low-risk wins)

## 1) Wireless dongle placement (biggest win)
USB 3.x ports/cables and high-speed devices can interfere with 2.4 GHz wireless dongles.
- Use a **USB 2.0 extension** to place the dongle closer to the mouse and away from USB 3.x.

## 2) Port selection
- Prefer rear motherboard ports for mouse/keyboard.
- Avoid chaining through hubs during troubleshooting.
- Separate high-throughput devices (external SSDs/capture cards) from input devices.

## 3) High polling mice
Very high polling (2k/4k/8k) can expose background input listeners/overlays causing spikes.
- Close peripheral suites/overlays you don’t need during matches.
- If spikes persist, drop to 1000 Hz and retest.

## 4) Avoid: USB “IMOD” / RWEverything hacks
Kernel-driver tools and “disable vulnerable driver blocklist” workflows are not recommended on a Vanguard PC.
They create security and anti-cheat risks for unproven wins.

## References
- Intel/USB-IF: USB 3.0 RF interference with 2.4GHz devices (whitepaper) — https://www.usb.org/sites/default/files/327216.pdf
