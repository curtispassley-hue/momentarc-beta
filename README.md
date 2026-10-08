# MomentArc Beta

**Turn local gameplay into comic-styled vertical Shorts.** Freeware beta for
Windows 10/11 x64, still improving with creator feedback.

## Download

Open [Releases](https://github.com/curtispassley-hue/momentarc-beta/releases) and
download **MomentArc-0.1.0-beta.1-windows-x64-setup.exe** from Beta 1.
Compare its SHA-256 with the accompanying `SHA256SUMS.txt`.
This is unsigned beta software; Windows may report an unknown publisher.
Do not disable antivirus or workplace security controls to install it.

Python and the app are included. During setup, explicitly select the optional
**Download rendering tools** task if FFmpeg/FFprobe are not already installed.
It downloads about 109 MB directly from the external tool provider and verifies
a pinned SHA-256. Internet is needed for that one-time step, not for editing.
The GPLv3 rendering tools are not inside our installer and retain their own license.
[Provider, source information and licenses](https://www.gyan.dev/ffmpeg/builds/),
[FFmpeg licensing](https://ffmpeg.org/legal.html).

## What works now

- Local clip library, raw preview, editing checklist and previous-edit history.
- One-click 1080 x 1920 edits; new variations preserve earlier outputs.
- Pro comic captions, selective slowdown, measured shake and paired combat framing.
- Enlarged stats/status/kill-feed panels for standard 16:9 League layouts.
- Saved video location, observed progress and safe connection recovery.

Choose a gameplay folder, scan, select/preview a clip, then create a Short.
Finished videos are saved on your PC; **Show saved file** opens their location.
Use **Exit MomentArc** when idle. Closing the browser tab alone leaves it running.

## Private by default — honest about learning

Gameplay is never uploaded automatically or altered in place. Analyses, versioned
edit decisions and output history stay in your local `.momentarc` workspace.
There is no telemetry, automatic feedback submission or pooled player database.
The explicit tool download contacts its provider; clicked feedback links contact GitHub.

The software preserves data needed for future learning. The existing core has
guarded learning-ledger/preference/performance workflows; it does **not** automatically
learn from other players or treat an export as an approval/performance outcome.
Shared learning, analytics sync, publishing, easy feedback controls and model
training are future work. Any future shared-data feature needs separate opt-in controls.

## Help improve the beta

[Report a bug or editing suggestion](https://github.com/curtispassley-hue/momentarc-beta/issues/new/choose).
Include beta/Windows version, game, steps and expected versus actual behavior.
For zoom/pacing/text feedback, include the exact output time. Manually share only
media you may publish, after removing names/chat/private information. Never attach
your whole database, media folder, tokens or keys. No files are attached automatically.

## Known limits

Camera/game understanding is heuristic, not certified identity/attack detection.
Some framing still needs improvement. HUD panels assume standard League layouts
and show the most recent two feed rows. Raw preview is MP4-only up to 256 MB.
Rendering can take minutes; avoid running multiple copies against one workspace.
Only Windows x64 is packaged; there is no native ARM64 claim.
No game footage, fonts, AI models or optional OCR stack are shipped.

Updates are manual. Close MomentArc, back up `.momentarc`, then run a newer
verified installer over the existing install. Uninstall preserves original gameplay,
saved renders and the local database. Beta features and future improvements are not guaranteed.

This repository hosts downloads and feedback only. MomentArc source stays private.
The beta is proprietary freeware under [LICENSE](LICENSE), not open-source software.
Third-party components retain their separate rights. See the installer quick-start
and included third-party notices for details.
