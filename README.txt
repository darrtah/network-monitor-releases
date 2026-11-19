Network Monitor Alpha 23 — Windows x64

Based on TrafficMonitor by zhongyang219.
Read LICENSE and NOTICE.md before redistribution.

Network Monitor is a Windows taskbar monitor with download/upload speed
and HTTPS availability indicators. Green means available; red means unavailable.
The large dot checks general internet; the small dot checks YouTube access.
YouTube reachability does not prove that VPN is connected.

In-app updates use the public GitHub Pages release feed over HTTPS.
SHA-256 is verified before replacement. Installation requires a brief restart.
The updater keeps a .previous executable backup.

Diagnostics:
%LOCALAPPDATA%\NetworkMonitor\Diagnostics\checks-YYYYMMDD.csv
%LOCALAPPDATA%\NetworkMonitor\Diagnostics\statistics.txt
%LOCALAPPDATA%\NetworkMonitor\watchdog.log

Experimental: user validation of updater restart and rollback is pending.
The source repository and Windows build runner remain private.
