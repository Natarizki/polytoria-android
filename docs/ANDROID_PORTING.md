# Android Porting Plan

## Project

- Project: Polytoria Android (unofficial community fork)
- Upstream: https://github.com/Polytoria/polytoria-game
- Fork: https://github.com/Natarizki/polytoria-android
- Development branch: `android-development`
- Baseline: upstream-compatible `main` snapshot at `c9ce4d156931afe5bb68c258101546d137ff361b`
- License: MPL-2.0 (retain upstream notices and comply with the license)

## Scope

This project ports and improves the existing Polytoria Godot/.NET client for Android. It does not reimplement the Polytoria backend, authentication protocol, multiplayer protocol, or Luau runtime.

Initial target:
- Android ARM64 (`arm64-v8a`)
- APK for direct testing
- Existing Godot Android export presets
- Existing mobile UI and native Android Luau libraries

## Repository findings

The upstream snapshot already contains:
- `Polytoria/export_presets.cfg.template` with `Client Android` and `Client Android APK` presets.
- Both Android presets currently enable `arm64-v8a`.
- `Polytoria/scripts/mobile/MobileUI.cs` handles mobile startup, authentication/deep links, mobile navigation, and world joining.
- `Polytoria/scenes/client/ui/touch_controls.tscn` and the `JoystickArea`, `CameraTurnArea`, and `JumpButton` scripts already implement touch movement, camera drag/zoom, and a jump control. The joystick emulates gamepad axes and sprint input.
- Android native builds of `Luau.VM` and `Luau.Compiler` are present.

These findings establish that Android support is already partially implemented. They do not prove that the current source exports, installs, authenticates, or runs a world successfully on a physical device.

## Work plan

### Phase 0 — Baseline and build validation
- Keep upstream `main` untouched.
- Work on `android-development`.
- Verify the existing .NET/Godot build.
- Add a reproducible GitHub Actions Android APK export.
- Record build failures before changing gameplay code.
- Inspect the existing touch-control scene and input routing before adding or replacing controls.

### Phase 1 — First installable APK
- Export a debug APK for `arm64-v8a`.
- Upload the APK as a workflow artifact.
- Install and launch-test on a physical Android device.
- Check startup, orientation, permissions, and crash logs.

### Phase 2 — Mobile client flow
- Verify authentication and deep links.
- Verify home/world discovery and place details.
- Verify joining and leaving a multiplayer world.

### Phase 3 — In-world touch controls
- Validate the existing joystick, camera drag/zoom area, and jump control on a physical device.
- Audit input routing and the touch-control scene for missing actions or layout defects.
- Modify existing controls only where testing identifies a concrete defect.
- Preserve keyboard/controller input on desktop.

### Phase 4 — Device compatibility and performance
- Test lifecycle interruptions, different aspect ratios, and safe areas.
- Profile CPU, GPU, memory, and frame pacing on physical ARM64 devices.
- Tune quality settings based on measurements, not assumptions.

## Acceptance criteria

A phase is not complete merely because the project compiles.

The first usable Android build must:
1. Produce an installable ARM64 APK.
2. Install and launch on a physical Android device.
3. Reach the mobile home screen without crashing.
4. Complete authentication.
5. Join a world and provide usable touch movement and camera controls.

## Development rules

- Keep changes isolated in `android-development`.
- Prefer small, reviewable commits.
- Do not replace existing mobile systems before auditing them.
- Do not claim device compatibility without a physical-device test.
- Preserve upstream copyright and MPL-2.0 notices.
