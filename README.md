# Network Monitor — releases

Public download channel for **Network Monitor**, a Windows taskbar network speed and HTTPS availability monitor.

This repository contains **compiled releases and update metadata only**. It does not contain the private source repository, Windows build runner configuration or developer credentials.

## Releases

Download reviewed Windows x64 builds from [Releases](https://github.com/darrtah/network-monitor-releases/releases).

Every release includes:
- `NetworkMonitor.exe` — Windows x64 executable.
- `NetworkMonitor.sha256` — expected SHA-256 for the executable.
- `LICENSE` and `NOTICE.md` — original license and attribution.
- `README.txt` — application notes.

## Update feed

The file `updates/stable.txt` is published only after a release passes private CI and a maintainer approves publication.

Network Monitor downloads the release via HTTPS, verifies the SHA-256 and asks before installing. The app stays active during downloading and restarts briefly during installation.

**Security:** Never upload passwords, access tokens, diagnostics, private source history or runner files here.

## Attribution

Network Monitor is derived from [TrafficMonitor by zhongyang219](https://github.com/zhongyang219/TrafficMonitor). The application retains upstream attribution and the original **Anti 996 License Version 1.0 (Draft)** in every distributed build.

## Status

This channel is being initialized. A release is available only when its GitHub Release and `updates/stable.txt` have both been published and checked.
