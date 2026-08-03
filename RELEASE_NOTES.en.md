# ZippyTuck v1.0.0 2026-08-03

ZippyTuck v1.0.0 is the first stable release.
It refreshes modal operation around direct move sessions without Normal mode, and adds target switching, session undo / redo, window marks, grid mode, help, and the `zippytuck://` URL scheme.

## Major Changes

- Reworked modal operation so the startup shortcut enters move mode directly; `e` / `r` switch move and resize, a single `Enter` commits, and `Esc` restores every window touched in the session to its starting frame
- Added an `Option+Tab` / `Option+Shift+Tab` target switcher so the active window can be changed during a session
- Added session-local window-batch undo / redo with `u` / `Ctrl+r`
- Added case-sensitive 52-slot window marks (`a-z` / `A-Z`) for updating a single window, saving and applying all-window layouts, visualization, deletion, and preview cycling
- Added grid mode from `Ctrl+w`, with cell navigation, window assignment, auto assignment, multi-cell spans, boundary adjustment, shape bookmarks, and shape preview / restore
- Added a menu-bar Data menu for running and deleting marks and grid shapes, plus mark export / import and clear-all operations
- Added a `?` / menu Help overlay with pages for overview, move, resize, grid, quick operations, and URL scheme reference with copy buttons
- Added the `zippytuck://` URL scheme for applying marks, applying grid shapes, starting sessions, opening help, and opening Settings
- Improved mode HUD behavior so it stays visible during sessions and can dim to a configurable opacity; added a setting to enable or skip confirmations before applying all-window layouts
- Revised grid defaults and persistence: default grid is now `2x2`, valid dimensions are `1...100`, and in-session division changes no longer overwrite Settings defaults

# ZippyTuck v0.0.3 2026-07-29

ZippyTuck v0.0.3 is a pre-release.
It fixes bulk `Esc` undo after combining move and resize in Global Quick Ops, restoring the window to the position and size from the start of the quick operation.

## Improvements and Fixes

- Fixed `Esc` after "move -> resize" or "resize -> move" in Global Quick Ops so both position and size return to the quick-operation start frame
- Improved restore frame writes for size-changing undo by separating `AXPosition` and `AXSize` writes, adding a short landing gap, and retrying once when the target frame does not land
- Preserved the quick undo baseline when the same quick chord is re-engaged during the 1-second linger, even if main-thread AX work delays the next begin event
- Improved restore reliability for apps with `AXEnhancedUserInterface` enabled
- Added `restore_probe` to diagnose environment-specific `Esc` restore failures on real Macs, and moved the existing AX probe under `tools/probes`

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
