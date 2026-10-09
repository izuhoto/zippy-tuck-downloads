# ZippyTuck v1.0.7 2026-10-09

ZippyTuck v1.0.7 makes it easier to control which saved window is used when the same app has several saved positions.
In the Marks and Display Layout lists in Settings, you can move a row up or down to change the order.

## Major Changes

- Added Move Up and Move Down in the Marks and Display Layout tabs in Settings so you can reorder the selected row
- When the same app has several saved windows, ZippyTuck prefers a matching window title (and similar details); only when that does not decide does it use the list order from the top. You can change that order with Move Up / Move Down
- Updated the on-screen help for apps with several saved windows so it explains this matching and reordering

# ZippyTuck v1.0.6 2026-10-05

ZippyTuck v1.0.6 fixes cases where the Settings Marks and Display Layout tabs could make the window taller than the screen and prevent resizing it vertically.
You can also delete a list entry from the right-click menu.

## Improvements and Fixes

- Fixed an issue where the Marks and Display Layout tabs in Settings could grow taller than the screen when the list was long, so the window could not be shortened vertically and the buttons at the bottom were hard to reach
- Improved cases where resizing the Settings window on those tabs could stretch it too tall
- Added Delete to the right-click menu on Marks and Display Layout list entries, with a confirmation before deletion

# ZippyTuck v1.0.5 2026-10-04

ZippyTuck v1.0.5 improves choosing among multiple windows of the same app under the same mark, and makes it easier to review and delete marks and display layouts in Settings.
You can also align a window to its saved position from Settings.

## Major Changes

- When the same mark has multiple saved windows for the same app, you can switch candidates right after applying to pick another saved window, apply without moving focus, or delete just that saved entry
- Improved mark visualization so the entry count and window title are easier to see
- Split Settings into General, Marks, and Display Layout tabs for browsing and deleting saved entries
- Added the ability to align a window to its saved position and size from the Marks and Display Layout lists in Settings
- Clarified candidate-switching steps in Help and fixed key labels that overflowed their columns

# ZippyTuck v1.0.4 2026-09-26

ZippyTuck v1.0.4 makes regular mouse-based window adjustment easier when windows sit side by side.
During continuous move or continuous resize, hold `A` to keep multiple windows lined up while changing their position or size.

## Major Changes

- Added the ability to hold `A` during continuous move or continuous resize so adjacent windows move or resize together
- When starting near an edge or corner, adjacent windows resize while keeping their edges together; when starting from the middle, adjacent windows move along with the window you are operating

# ZippyTuck v1.0.3 2026-08-25

ZippyTuck v1.0.3 makes display-configuration layouts easier to carry forward.
It adds export / import for saved layouts and automatic restore when apps launch, and improves Global Quick Ops target resolution in apps such as Excel.

## Major Changes

- Added Display Layout export / import from the menu, using JSON files for saved display-configuration layouts
- Added a Settings option to restore layout when apps launch, restoring only that app's operable windows from the layout saved for the current display setup
- Fixed Global Quick Ops target lookup from Excel cell grids and sheet tabs, so continuous move, continuous resize, direction-snap move, and direction-snap resize can start from those areas

# ZippyTuck v1.0.2 2026-08-20

ZippyTuck v1.0.2 adds display-configuration layouts.
It can restore saved all-window positions after displays are connected, disconnected, or rearranged, and adds per-operation disabling for Global Quick Ops.

## Major Changes

- Added a Display Layout menu for saving, restoring, and deleting the positions and sizes of all operable windows for the current display setup
- Added per-operation enable / disable controls for Global Quick Ops in Settings, so unused mouse chords and corner shortcuts can stop registering while keeping their shortcut assignments

# ZippyTuck v1.0.1 2026-08-10

ZippyTuck v1.0.1 is a maintenance release.
It fixes gradually worsening cursor responsiveness during continuous Global Quick Ops, and improves HUD click handling for the pending HUD and completion toasts after quick operations.

## Improvements and Fixes

- Fixed an issue where Ctrl+Cmd Global Quick Ops could rebuild hot keys and the Escape event tap unnecessarily during continuous move / resize, gradually making cursor interaction slower
- Explicitly disabled and released the Escape event tap when uninstalling it, preventing leftover taps from degrading system-wide cursor responsiveness
- Made the pending HUD after releasing quick-operation modifiers clickable, so the quick session can be committed without waiting for the linger timeout
- Made quick-operation and modal-session completion toasts dismissible by click, and skips the extra completion toast when a click already committed the quick session
- Kept move / resize / grid mode HUDs and modal-session warnings click-through, while exposing only clickable HUDs as button-like controls

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
