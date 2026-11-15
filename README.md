# metalX
metalX is a conversion tool that lets windows apps or games run on macOS with GPTK4 using SwiftUI
<p align="center">
  <img src="Resources/AppIcon.png" width="128" alt="metalX icon">
</p>

<h1 align="center">metalX</h1>

<p align="center">
  Run Windows apps on your Mac, export them as native <code>.app</code> / <code>.dmg</code>, and choose your graphics API, all from one minimalist SwiftUI window.
</p>

---

## Features

- **EXE to App / DMG:** drop in a Windows `.exe` and export it as a macOS `.app`, or as a `.dmg` with the standard drag-to-Applications layout.
- **Graphics API selector:** pick **D3DMetal**, **DXMT**, **DXVK** or **WineD3D (OpenGL)** from a dropdown, with a short description of each.
- **Steam launcher:** one click sets up a dedicated Windows bottle, downloads the Steam installer and launches Steam.
- **Metal HUD toggle:** show Apple's Metal performance overlay.
- **First-launch setup:** if Wine isn't installed, metalX offers to download and install it in the background.
- **Minimal SF Pro interface:** native SwiftUI, nothing extra.

## Requirements

- macOS 13 or later
- Apple Silicon (M1/M2/M3/M4/M5)

## Installing

1. Download `metalX.dmg` from Releases
2. Open it and drag **metalX** into **Applications**.
3. The app is ad-hoc signed, so the first time, right-click it and choose **Open**.
4. On first launch, click **Install** in the "Install Dependencies" popup. Wine (about 230 MB) is downloaded and installed in the background. Click **Finish** when it's done.

## Usage

1. Drop a `.exe` onto the window, or click the drop area to choose one.
2. Choose a **Graphics API**.
3. Press **Run** to launch it, or **Export .app** / **Export .dmg** to package it.
4. Press **Steam (Windows bottle)** to set up and launch Steam.

Exported apps contain a copy of the `.exe`'s folder and a launcher that runs it in its own Wine bottle with your chosen graphics API. The folder is copied in full, so large games make large apps.

## Graphics APIs

| Option | Best for | Notes |
|---|---|---|
| **D3DMetal** | DirectX 11 / 12 | Apple's translation layer. Requires a Game Porting Toolkit Wine build, which metalX does not install automatically. |
| **DXMT** | DirectX 10 / 11 | Metal-native. Place the DXMT files in `~/Library/Application Support/metalX/Backends/DXMT/x64/`. |
| **DXVK** | DirectX 9 / 10 / 11 | Runs through Vulkan (MoltenVK). Place the DXVK DLLs in `~/Library/Application Support/metalX/Backends/DXVK/x64/`. |
| **WineD3D (OpenGL)** | Fallback | Built into Wine. Slowest, but works out of the box. This is the default. |

For DXVK and DXMT, metalX copies the DLLs into the bottle and sets the DLL overrides for you.

## Data locations

- Wine: `~/Library/Application Support/metalX/Wine`
- Bottles: `~/Library/Application Support/metalX/Bottles`
- Backend files: `~/Library/Application Support/metalX/Backends`

## Known limitations

- Not every Windows app or game will run, and performance varies by title and graphics API.
- Anti-cheat and kernel-level drivers generally don't work under Wine.
- D3DMetal, DXVK and DXMT files must currently be added manually.

## Credits

Made by **OptimisaGH**.

metalX relies on third-party projects, each under its own license:

- [Wine](https://www.winehq.org) and the macOS builds by [Gcenx](https://github.com/Gcenx/macOS_Wine_builds)
- [DXVK](https://github.com/doitsujin/dxvk) and [DXMT](https://github.com/3Shain/dxmt)
- Apple's Game Porting Toolkit / D3DMetal

metalX is not affiliated with or endorsed by Apple, Microsoft, Valve, NVIDIA or the Wine project. All trademarks belong to their respective owners.

## License

Copyright (c) 2026 OptimisaGH. **All Rights Reserved.**

The source code is published for viewing only. No permission is granted to copy, modify, distribute or use it without prior written permission from the copyright holder. See [LICENSE](LICENSE).
