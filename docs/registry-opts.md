# Registry Options (Safe + Reversible)

Registry options are applied via **bin/apply-registry.ps1** and controlled by **bin/registry-options.json**.

## Guidance
- These tweaks target **usability, background noise, and stability**, not “secret FPS.”
- Avoid disabling core security features or update mechanisms.
- Always create a restore point and export registry changes when experimenting.

## Removed (deprecated) options
The legacy guide included options like **Disable Windows Defender** and **Disable Windows Update entirely**.
These were removed because the security/maintenance risk is disproportionate and can conflict with anti-cheat/platform integrity.

## Recommended defaults (PC#1 / VALORANT)
✅ Do:
- disable pointer acceleration
- disable sticky keys
- show file extensions
- disable fast startup

⚠️ Consider:
- disable driver installation via windows update (keeps driver stack stable)
- disable automatic windows updates (schedule updates rather than surprise reboots)
- disable gamebarpresencewriter / disable widgets (if you don’t use them)
- privacy toggles (telemetry/CEIP/etc.) (small/no FPS impact)

## Options

### `disable automatic windows updates`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Turns off fully-automatic update behavior so you can schedule installs/reboots (do **not** stop patching entirely).

### `disable driver installation via windows update`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Prevents Windows Update from automatically installing device drivers (helps keep a known-good driver stack).

### `disable automatic store app updates`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Stops automatic Store app updates (reduce surprise background activity; update manually occasionally).

### `disable gamebarpresencewriter`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables a Game Bar capture presence component (can reduce background capture hooks on some systems).

### `disable background apps`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables background execution for many Microsoft Store apps.

### `disable transparency effects`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Turns off UI transparency effects (tiny GPU/CPU savings; mostly preference).

### `disable notifications network usage`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Reduces network usage related to some notifications features (small effect).

### `disable sticky keys`
- **Default in this repo:** `true`
- **Recommendation:** ✅ Do
- **What it does:** Disables Sticky Keys prompts/behavior (prevents accidental input interruptions).

### `disable pointer acceleration`
- **Default in this repo:** `true`
- **Recommendation:** ✅ Do
- **What it does:** Disables mouse acceleration for consistent aiming.

### `disable fast startup`
- **Default in this repo:** `true`
- **Recommendation:** ✅ Do
- **What it does:** Disables Fast Startup (hybrid shutdown). Helps troubleshooting and can reduce weird driver resume states.

### `disable customer experience improvement program`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables CEIP telemetry participation (privacy).

### `disable windows error reporting`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Limits Windows Error Reporting background activity (may reduce useful crash reporting).

### `disable clipboard history`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables clipboard history (privacy).

### `disable activity feed`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables Timeline/activity history (privacy).

### `disable advertising id`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables Advertising ID (privacy).

### `disable autoplay`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables AutoPlay prompts (safety).

### `disable cloud content`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables certain consumer cloud content in Windows UI (preference).

### `disable suggestions and web results in the search box and in search home`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables web suggestions/results in Windows Search (preference).

### `disable sending inking and typing data to microsoft`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables sending typing/inking data (privacy).

### `disable automatic maintenance`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables automatic maintenance scheduling (can reduce surprise background tasks; but you must maintain the PC yourself).

### `disable computer is out of support message`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables certain out-of-support notifications (cosmetic).

### `disable fault tolerant heap`
- **Default in this repo:** `true`
- **Recommendation:** ❌ Avoid unless troubleshooting
- **What it does:** Disables Fault Tolerant Heap (only change if you have a specific compatibility reason; can reduce resilience).

### `disable sign-in and lock last interactive user after a restart`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Stops Windows from auto-signing in the last user after restart (privacy/security).

### `show file extensions`
- **Default in this repo:** `true`
- **Recommendation:** ✅ Do
- **What it does:** Shows file extensions in Explorer (safety).

### `disable widgets`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables Widgets (reduces background UI services on some builds).

### `disable remote assistance`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables Remote Assistance (security).

### `disable telemetry`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Reduces some Windows telemetry (privacy).

### `disable retrieval of online tips and help in the immersive control panel`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables online tips/help content (preference).

### `disable typing insights`
- **Default in this repo:** `true`
- **Recommendation:** ⚠️ Consider
- **What it does:** Disables typing insights (privacy).


## References
- Microsoft: Fast startup overview — https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6e9b
