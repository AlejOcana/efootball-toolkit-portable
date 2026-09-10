# Changelog — public distribution

## v0.1.0 (upcoming — not released yet)

First public binary release of the portable Windows toolkit.

- Portable WPF app (Release|x64, .NET Framework 4.8): 7 tabs
  (Monitor, Modes, Servers, Overlay, Rivals, Gamepad, Settings) plus
  in-game overlay strip, match detail window and tray icon.
- Seed server catalog (`servers.json`, curated entries with honest `-1`
  default latency) with real per-country latency measurement.
- UI strings in ES/EN (`i18n`, switchable without restart).
- Thursday regional steering seed (`thursdayserver.txt`, 61 lines,
  `IP,port,host` format, CloudFront `:443` entries).
- Firewall handling limited to `ETK-*` rules with cleanup on exit.
- GeoIP approximation via bundled IP2Location LITE DB3 IPv4 plus curated
  table and editable cache; unreachable hosts show `-1` / "no response",
  never invented values.
- Legal pack for binary distribution: EULA-binaria.md (free use, no
  warranty, no rebrand/resale, `ETK-*` cleanup duty) and
  THIRD-PARTY-NOTICES.txt shipped inside the ZIP.
- Verification: `Get-FileHash *.zip -Algorithm SHA256` against the published
  `.sha256` (see docs/VERIFY.md).

Releases (once published):
https://github.com/AlejOcana/efootball-toolkit-portable/releases
