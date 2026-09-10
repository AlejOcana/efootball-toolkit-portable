# Security policy

## Supported versions

Only the latest binary release published under
[Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases)
is supported. Older ZIPs may contain fixed issues; update before reporting.

## Reporting a vulnerability

Open a confidential report via
[Issues](https://github.com/AlejOcana/efootball-toolkit-portable/issues/new?template=bug_report.yml)
and mark it as security-sensitive in the title (prefix `[security]`), or
contact the maintainer through the profile linked on
[Ko-fi](https://ko-fi.com/alejandroocanagarcia). Do not open public proof of
concepts for unpatched issues.

Include: app version (from Settings), Windows build, admin or limited mode,
steps to reproduce, and logs under `logs/` with personal IPs redacted.

## Scope notes

- The app needs administrator rights for capture/block and touches only
  `ETK-*` firewall rules; a report showing any other rule touched is critical.
- Bundled drivers (WinDivert, Npcap as external install) follow their own
  advisories; report here only issues in this tool's use of them.
- No source is published in this repo (binary distribution); reports must be
  reproducible against a release ZIP whose SHA256 matches the published
  `.sha256`.
