# Polytoria Android Client

An experimental Android client project for [Polytoria](https://polytoria.com/), built from the [Polytoria game source](https://github.com/Polytoria/polytoria-game) and adapted for Android.

> **Status: Work in progress.** This project is under active development. It is not an official Polytoria release, and working Android builds are not guaranteed yet.

## Project goals

- Bring the Polytoria game client to Android devices.
- Target **Android ARM64 (arm64-v8a)**.
- Use Godot's Mobile renderer and optimize for mobile hardware.
- Keep the client lightweight and responsive.

## Technology

| Component | Version / target |
|---|---|
| Engine | Godot 4.7.0 .NET |
| Runtime / SDK | .NET 10 |
| Platform | Android |
| Architecture | ARM64 (arm64-v8a) |
| Renderer | Godot Mobile |

The project uses Godot C#/.NET. The standard non-.NET Godot editor is not suitable for building this project.

## Development requirements

To build the Android project locally, install:

- **Godot 4.7.0 .NET** for Windows or Linux.
- **Godot 4.7.0 .NET export templates**.
- **.NET 10 SDK**.
- **Java JDK 17**.
- **Android SDK**, including Android Platform 35 and Build-Tools 35.0.1.
- **Android NDK 28.1.13356709**.
- **CMake 3.10.2.4988404**.
- **Git**, including Git LFS if required by repository assets.

Configure the Android SDK and Java paths in Godot Editor Settings before exporting.

## Getting the source

Clone this repository and its submodules:

```bash
git clone --recurse-submodules https://github.com/Natarizki/polytoria-android.git
cd polytoria-android
```

Open the Godot project in the `Polytoria/` directory using the **Godot .NET 4.7.0** editor.

## Building

1. Install the development requirements listed above.
2. Open `Polytoria/` in Godot .NET.
3. Allow the project to import its assets.
4. Restore and build the C# solution.
5. Configure the Android export preset named `Client Android APK`.
6. Export a debug APK for Android ARM64.

Build automation is maintained in [GitHub Actions](https://github.com/Natarizki/polytoria-android/actions). The workflow and its artifacts are experimental; a successful upload alone does not guarantee that the exported APK is fully functional.

## Project structure

- `Polytoria/` — Godot game project and C# source.
- `.github/workflows/` — automated build workflows.
- `docs/` — project documentation and assets.

## Upstream project

This project is based on [Polytoria/polytoria-game](https://github.com/Polytoria/polytoria-game). Please refer to the upstream project for information about the Polytoria platform.

## License

Unless otherwise noted:

- Source code is licensed under the Mozilla Public License 2.0. See [LICENSE](LICENSE).
- Polytoria brand assets, logos, names, and trademarks are not licensed for reuse by this project.
- Third-party assets and native binaries remain subject to their respective licenses.

This repository is an independent development effort and is not an official Polytoria product.
