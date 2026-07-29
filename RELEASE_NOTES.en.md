# ZippyTuck v0.0.2 2026-07-29

ZippyTuck v0.0.2 is a pre-release.
It improves cases where, on Macs with many resident apps, the HUD after the startup shortcut and keyboard operations could take several seconds to respond.

## Improvements and Fixes

- Faster response for the startup-shortcut HUD and keyboard operations in move / resize mode, even when many apps are running
- Narrower snap-candidate collection to on-screen windows, plus AX messaging timeouts to limit stalls from unresponsive apps
- Reuse of the snap-candidate cache for keyboard relative move / resize so candidates are not re-collected on every keystroke
- Immediate HUD display without a fade-in delay, so the HUD stays visible even when heavy work follows right after show

# ZippyTuck v0.0.1 2026-07-27

ZippyTuck v0.0.1 is an initial pre-release.
As an early version before the formal release, it provides the core window moving and resizing workflow for macOS using both keyboard and mouse operations.

## Key Features

- Native macOS menu bar app for moving and resizing windows
- ZippyTuck normal, move, and resize modes launched from a configurable startup shortcut
- Keyboard-centered window control with `h` / `j` / `k` / `l`, numeric prefixes, edge commands, and grid operations
- Direction snapping with `zh` / `zj` / `zk` / `zl` and `z` + mouse movement
- Global Quick Ops for direct window control from the normal macOS state with modifier-key mouse gestures
- Continuous move, continuous resize, direction-snap move, and direction-snap resize
- Corner shortcuts for placing the active window at the screen's visible-frame corners
- Live HUD and target-window highlight during operations
- Configurable startup shortcut, Global Quick Ops, grid, language, and snap-related settings
- English and Japanese UI, with optional system-language following
- First-launch Terms and Disclaimer agreement, About window, and web-distribution update checking
