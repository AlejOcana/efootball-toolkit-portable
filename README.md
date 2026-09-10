<div align="center">

# eFootball Toolkit Portable

**Stop guessing your connection. See it live, then act on it.**

Portable Windows diagnostics for eFootball: P2P or server, real ping, network modes, servers, overlay, rivals, gamepad — no install.

[![Windows](https://img.shields.io/badge/Windows-10%2F11_x64-0078D6?logo=windows&logoColor=white)](https://github.com/AlejOcana/efootball-toolkit-portable/releases)
[![Latest release](https://img.shields.io/github/v/release/AlejOcana/efootball-toolkit-portable?label=latest%20release)](https://github.com/AlejOcana/efootball-toolkit-portable/releases)
[![License](https://img.shields.io/badge/license-MIT%20%2B%20binary%20EULA-blue)](EULA-binaria.md)

[**Download the latest release**](https://github.com/AlejOcana/efootball-toolkit-portable/releases) · [**Support on Ko-fi**](https://ko-fi.com/alejandroocanagarcia)

_No install. Unzip and run._

</div>

> Binary distribution. The ZIP files published under [Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases) are governed by [EULA-binaria.md](EULA-binaria.md), not by the MIT LICENSE in this repo (that LICENSE covers only the texts, docs and scripts in this repo). Third-party components are listed in [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).

## What it is

Desktop app (WPF, .NET Framework 4.8, inbox on Windows 10/11) with a dark Fluent UI: 7 tabs (Monitor, Modes, Servers, Overlay, Rivals, Gamepad, Settings) plus a live in-game overlay strip (`OverlayWindow`), a match detail window and a tray icon. Labels switch between ES and EN without restart.

Independent project, no affiliation with KONAMI. Nominative use of eFootball.

### Feature tour

| Area | What you get |
|------|--------------|
| **Monitor** | Live connection type (P2P / `SERVIDOR_UDP`), local IP, server IP, rival IP, confirmed endpoint, protocol, real ping over tcping and ICMP, approximate region from local GeoIP, events and current connections. Scope: eFootball UDP `30000-35000` + `5736`. |
| **Modes** | Competitive (blocks lag-prone TCP), COOP (competitive plus blocking of problematic UDP ranges), NORMAL (monitor only). Scope: eFootball only, whole system, or no rules. Every rule uses the `ETK-*` prefix and is reversible in one click. |
| **Servers** | Per-country and per-IP list with real latency (test all, by country, or one by one), adding IPv4 and IPv6, allow and block, plus automatic catalog of newly observed IPs. Includes regional steering (preferred countries versus the rest while searching) with the pending list and Thursday logic. No separate tab. |
| **Overlay** | Compact 1-2 line strip over the game (status, mode, ping, region, endpoint, time), configurable opacity, Mark IP button. |
| **Rivals** | Local match history (200 cap), visual and sound alert on re-encounter, current blocks. |
| **Gamepad** | Live buttons, LT and RT triggers, sticks, polling rate, battery and rumble state (Windows inbox XInput; Xbox works out of the box, PlayStation through DS4Windows). |
| **Settings** | Launcher that detects the Steam and XboxPC install, starts the game at high priority and shows its current connections. Strictly portable: everything lives next to the exe (`data/`, `config/`, `logs/`), nothing in the registry. |

## Requirements

- Windows 10/11 x64.
- Administrator rights for traffic capture and blocking.
- Wired LAN with no VPN and no proxy, for live-match validation.
- Npcap as an external piece, never bundled (download from https://npcap.com/#download), for packet capture.
- WinDivert driver files (`WinDivert.dll` / `WinDivert*.sys`) ship unmodified next to the exe when present in the build output (they must stay there because `LoadLibrary` ignores probing). See [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).

<details>
<summary>Running without admin rights?</summary>

If you deny the UAC prompt, the app shows a one-time limited-mode warning and keeps running with partial read. It never stops with a hard failure.

</details>

<details>
<summary>Folder is write-protected?</summary>

When the exe folder does not allow writes, runtime state falls back to `%LocalAppData%/EtkPortable`. For full portable behavior, prefer a folder you own.

</details>

## Install

1. Download the ZIP from [Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases) and unzip it into a short path without odd characters.
2. Double-click `EtkPortable.exe` — right-click then **Run as administrator** to capture traffic and apply blocks. On UAC deny you get limited mode once and the app keeps running with partial read.
3. Open the app and press Start while eFootball searches for a match.
4. Apply competitive with eFootball-only scope, test servers, flag rivals, check the gamepad.
5. When done, press Clean `ETK-*`. Rules are temporary, and cleanup also runs on exit.

<details>
<summary>Old ZIPs and launcher files?</summary>

No launcher script is shipped. Delete `INICIAR.bat` if it comes inside old ZIPs.

</details>

## Verify the download

Every release ships `EtkPortable-wpf-win64.zip` plus a `.sha256` file. Compare:

```powershell
Get-FileHash *.zip -Algorithm SHA256
```

The hash must match the `.sha256` published next to the ZIP on the [Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases) page. See [docs/VERIFY.md](docs/VERIFY.md) for the full checklist.

## Firewall

The app creates and deletes only rules named `ETK-*` (prefix `ETK`). Cleanup runs on exit and on crash.

<details>
<summary>Manual cleanup (admin PowerShell)</summary>

```powershell
powershell -ExecutionPolicy Bypass -File scripts\cleanup-etk.ps1
```

Verify afterwards that nothing remains:

```powershell
netsh advfirewall firewall show rule name=all | Select-String "ETK-"
```

</details>

## Honest measurements

Ping and region are never invented: unreachable hosts show `-1` and empty values plus a "no response" label. GeoIP is an approximation backed by an editable cache.

This product uses the IP2Location LITE database for IP geolocation (data from https://lite.ip2location.com, used under its LITE license).

## Credits

Thanks to the XJBT example team ([SuNingXJBT/efootball-toolkits](https://github.com/SuNingXJBT/efootball-toolkits), [Network_Monitor_Tool](https://github.com/SuNingXJBT/eFootball_Network_Monitor_Tool), [Block_TCP_Matches](https://github.com/SuNingXJBT/eFootball_Block_TCP_Matches), [t.me/eFootballxjbt](https://t.me/eFootballxjbt)) whose public reference docs and observable behavior (`isPSPmsg` / `isp2pmsg`, `XjbtReference2026` profile 2026-09-07 `0x8261` len76) helped build this tool. No XJBT code or binaries are redistributed here.

## License and docs

- Texts, docs and scripts in this repo: MIT, see [LICENSE](LICENSE).
- Downloadable binaries (ZIP): [EULA-binaria.md](EULA-binaria.md).
- Third-party notices: [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).
- Security policy: [SECURITY.md](SECURITY.md).
- Changelog: [CHANGELOG-0.1.md](CHANGELOG-0.1.md).
- Verification checklist: [docs/VERIFY.md](docs/VERIFY.md).

---

If it saves you matchmaking headaches: [Buy me a coffee on Ko-fi](https://ko-fi.com/alejandroocanagarcia).
