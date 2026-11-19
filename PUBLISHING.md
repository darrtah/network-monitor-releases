# Network Monitor — manual GitHub Pages publishing

This public repository contains only the binary update channel. Source and the Windows self-hosted runner remain private in `darrtah/network-monitor-windows`.

**No publishing PAT is required.** An authorized owner uploads files through the GitHub website.

## One-time Pages setup

1. In this repository, open Settings → Pages.
2. Set Deploy from a branch, branch `main`, folder `/(root)`.
3. Check `https://darrtah.github.io/network-monitor-releases/`.

## Publish a verified Alpha NN

1. In the **private** source repo, run the Windows build workflow on `feature/network-only`.
2. Confirm every build and updater test passed.
3. Download the matching `NetworkMonitor-alphaNN-win-x64` artifact from the successful private CI run.
4. Extract the archive on your Windows PC.
5. Confirm `NetworkMonitor.exe`, `LICENSE`, `NOTICE.md`, `README.txt` exist.
6. Run `Get-FileHash .\NetworkMonitor.exe -Algorithm SHA256` in PowerShell. Record the lowercase 64-digit digest.
7. Rename a **copy** of the executable to `NetworkMonitor-alphaNN.exe`. Do not change its contents.
8. Upload that copy to public `stable/` using GitHub → Add file → Upload files. Do not overwrite an old version.
9. Upload LICENSE and NOTICE.md with each release, or retain them as public files; do not omit license attribution.
10. Confirm direct anonymous download from `https://darrtah.github.io/network-monitor-releases/stable/NetworkMonitor-alphaNN.exe`.
11. Recalculate SHA-256 for the downloaded file and compare with the original digest.
12. Create or edit `updates/stable.txt` using **exactly** these three lines:

```text
alpha=NN
url=https://darrtah.github.io/network-monitor-releases/stable/NetworkMonitor-alphaNN.exe
sha256=64_lowercase_hex_character_digest
```

13. Publish `updates/stable.txt` **last**, after verifying the EXE. Use actual values; never publish sample data as a release.
14. Verify that `https://darrtah.github.io/network-monitor-releases/updates/stable.txt` returns the new version.
15. Test the installed Network Monitor → Проверить обновления, including the short restart and rollback.

## Rules

- Keep `network-monitor-windows` private; keep its local Windows runner there.
- Public uploads must contain **only** approved EXEs, version metadata, and attribution documents.
- Do not create a fake update feed before a real EXE exists.
- Each new public version must use a higher alpha number and a new immutable EXE filename.
- Do not rely on a Pages update being instantaneous: wait until the binary is visible before publishing the feed.
- If a release is bad, restore the previous known-good `stable.txt`. Do not delete the old EXE.
- Current Alpha 22 needs a one-time manual installation because earlier Alpha 21 referenced GitHub Releases rather than the new Pages EXE path.
- The updater checks SHA-256 but does **not** verify a Windows Authenticode signature. Keep the public repo account secure.

## SHA-256 verification example

```powershell
$expected = 'PASTE_ACTUAL_64_CHARACTER_SHA256'
$actual = (Get-FileHash .\NetworkMonitor-alphaNN.exe -Algorithm SHA256).Hash.ToLowerInvariant()
if ($actual -ne $expected) { throw 'SHA-256 mismatch' }
```
