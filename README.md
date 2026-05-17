# StatFlow

Lightweight macOS menu-bar system monitor for Apple Silicon. Replaces Activity Monitor with what it hides: GPU/ANE/DRAM watts, per-USB-C-port power, fan %, temperatures, per-process energy, 12h history.

**No sudo. No daemon. ~80 MB RAM. ~0.5% CPU.**

## Install

1. Download `StatFlow.dmg` from [Releases](https://github.com/Katoru-Cattor/StatFlow/releases/latest).
2. Open the `.dmg`, drag `StatFlow.app` to `/Applications`.
3. **First launch:** right-click `StatFlow.app` in `/Applications` → **Open** → confirm.
   - This is because the app is signed ad-hoc (no $99 Apple Developer cert). macOS Gatekeeper warns once; after you confirm, it never warns again.
   - Alternative one-liner to skip the prompt:
     ```
     xattr -d com.apple.quarantine /Applications/StatFlow.app
     ```

## What it shows

- **CPU**: per-core %, average, package watts
- **GPU**: watts (Apple Silicon Energy Model via IOReport, same source as Stats.app)
- **ANE / DRAM**: watts
- **Memory**: used / pressure / compressed / swap
- **Per-USB-C port**: instant watts (PD RDO decoded), V·A contract, port role (sink/source), attached device VID/PID, physical position (left/right)
- **MagSafe**: detected as separate port type
- **Battery**: %, time-remaining, temperature, health, cycle count
- **Adapter**: instant DC In watts (`SystemPowerIn`)
- **Fans**: RPM + % of max
- **Temperatures**: CPU, GPU, battery, ambient (via IOHIDEventSystemClient)
- **Per-process**: CPU %, memory, energy impact, 12h avg CPU %, 12h total Wh
- **Browser tabs**: Edge/Chrome/Safari tab titles via Accessibility API (optional)
- **Network / Disk I/O**: live throughput + sparklines

## Requirements

- Apple Silicon Mac (M1 or newer)
- macOS 14.0+

## Updates

Settings → Updates → **Check for Update**. App queries the GitHub Releases API and points you to the new `.dmg`. Manual install (drag-replace into `/Applications`).

## Privacy

100% local. No telemetry. No accounts. Update check is the only network call (GitHub releases API).

## Why no source in this repo?

This repo holds only the packaged builds. Source code is kept private.

## License / support

Personal-use binary. No warranty. Issues / feature requests welcome via Issues tab.
