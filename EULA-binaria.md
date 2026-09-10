# Binary EULA — eFootball Toolkit Portable

Version 0.1. Applies to the downloadable binary ZIPs
(`EtkPortable-wpf-win64.zip` and similar) published under
[Releases](https://github.com/AlejOcana/efootball-toolkit-portable/releases).
The texts, docs and scripts in this repository are covered by the MIT LICENSE
instead; third-party components are listed in THIRD-PARTY-NOTICES.txt, which
is also shipped inside every ZIP.

## 1. Free use

You may download, run and share the unmodified ZIP free of charge, for
personal and non-commercial use. No account, key or activation is required.

## 2. No warranty

The binaries are provided "AS IS", without warranty of any kind, express or
implied, including but not limited to merchantability, fitness for a
particular purpose and non-infringement. In no event shall the authors be
liable for any claim, damages or other liability arising from the use of the
binaries. Network blocking features touch your Windows Firewall and packet
path: you use them at your own risk.

## 3. No rebrand, no resale

You may not sell the binaries, bundle them with paid offers, or redistribute
them under a different name, brand or authorship. Redistribution of the
unmodified ZIP with attribution and a link to the official Releases page is
allowed. Removing or altering credits, license files or third-party notices
from the ZIP is not allowed.

## 4. Firewall cleanup duty

The app creates Windows Firewall rules named `ETK-*` only (prefix `ETK`) and
removes them on exit. If rules remain after a crash, you must remove them:
run the bundled cleanup as administrator or verify with
`netsh advfirewall firewall show rule name=all | Select-String "ETK-"`.
See [docs/VERIFY.md](docs/VERIFY.md). Leftover `ETK-*` rules are your
responsibility once pointed out by the app.

## 5. Third parties and game terms

Npcap, WinDivert, PresentMon, WPF-UI and the IP2Location LITE database keep
their own licenses and terms (see THIRD-PARTY-NOTICES.txt). Using this tool
with eFootball does not grant any right over the game; respect KONAMI's terms
and your network's acceptable-use policy.

## 6. Independent project

This project is not affiliated with KONAMI, Npcap, WinDivert, IP2Location or
the XJBT example team. Nominative use of their names does not imply
endorsement.
