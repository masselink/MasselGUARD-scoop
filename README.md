# MasselGUARD Scoop bucket

Official [Scoop](https://scoop.sh/) bucket for **[MasselGUARD](https://github.com/masselink/MasselGUARD)** — a WireGuard tunnel manager for Windows with a WPF GUI and a companion CLI.

## Install

```powershell
scoop bucket add masselguard https://github.com/masselink/MasselGUARD-scoop
scoop install masselguard
```

This installs both executables:

- **`MasselGUARD.exe`** — the GUI (also added to the Start menu as *MasselGUARD*).
- **`MasselGUARDcli.exe`** — the CLI, shimmed onto your `PATH` as `masselguard` so you can drive tunnels from a terminal.

Both x64 and ARM64 Windows are supported; Scoop picks the matching build automatically.

> **Note:** MasselGUARD requires administrator rights to manage tunnels (it drives the wireguard-NT kernel driver), so it triggers a UAC prompt on launch. The informational CLI commands (`help`, `version`, `selftest`) run without elevation.

## Usage

```powershell
masselguard help
masselguard list
masselguard connect <tunnel>
masselguard status
```

Full command reference: see the [MasselGUARD README](https://github.com/masselink/MasselGUARD) and manual.

## Update

```powershell
scoop update masselguard
```

## Uninstall

```powershell
scoop uninstall masselguard
```

## Maintenance

The manifest lives in [`bucket/masselguard.json`](bucket/masselguard.json). It uses `checkver: "github"` and per-architecture `autoupdate` templates, so version and hashes track upstream releases automatically. The [Excavator workflow](.github/workflows/excavator.yml) runs `checkver -u` on a schedule to keep it current.

To bump manually against a specific installed Scoop checkout:

```powershell
.\bin\checkver.ps1 masselguard <path-to-this-bucket> -Update
```

## Credits

This bucket builds on the manifest originally contributed by **[@qoreQyaS](https://github.com/qoreQyaS)** ([sven-scoop](https://github.com/qoreQyaS/sven-scoop)), offered in [issue #49](https://github.com/masselink/MasselGUARD/issues/49). Thanks, Sven! The official bucket extends it with ARM64 support, a CLI `PATH` shim, and automated updates.
