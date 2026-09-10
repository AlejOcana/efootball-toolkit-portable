# Verify your download

All checks run in PowerShell on Windows.

## 1. Check the hash

Every release publishes `EtkPortable-wpf-win64.zip` plus a `.sha256` file on
the [Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases)
page.

```powershell
Get-FileHash *.zip -Algorithm SHA256
```

The printed hash must equal the contents of the published `.sha256` file. If
it differs, delete the ZIP and download it again; never run a mismatched ZIP.

## 2. Unzip to a short path

Extract into a short folder without odd characters, e.g.
`C:\ETK\`. Long paths or special characters break sidecar loading.

## 3. Run as administrator

Right-click `EtkPortable.exe` -> **Run as administrator** for traffic capture
and blocking. If you deny the UAC prompt, the app shows a one-time
limited-mode warning and keeps running with partial read (servers, rules and
gamepad stay checkable; live monitor needs capture).

## 4. Know the fallbacks

- Write-protected exe folder: runtime state (`data/`, `config/`, `logs/`)
  falls back to `%LocalAppData%/EtkPortable`.
- Missing GeoIP BIN: the app keeps working with its curated table.
- Missing PresentMon sidecar: FPS shows an honest gap with a once-per-match
  warning.
- Without a live match only idle + servers + rules + gamepad are checkable;
  full monitor (P2P vs SERVIDOR_UDP, endpoint, ping) needs a real match
  search on wired LAN without VPN/proxy.

## 5. Firewall: only ETK-* rules

The app creates and deletes only rules named `ETK-*`. After closing the app,
zero `ETK-*` rules should remain. Check:

```powershell
netsh advfirewall firewall show rule name=all | Select-String "ETK-"
```

Manual cleanup (admin) if leftovers remain after a crash:

```powershell
powershell -ExecutionPolicy Bypass -File scripts\cleanup-etk.ps1
```
