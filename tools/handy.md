# Tool card: Handy (offline dictation)

**Replaces:** Wispr Flow.
**Repo:** https://github.com/cjpais/Handy · Site: https://handy.computer
**Licence:** MIT. **Cost:** $0. There is no paid tier; the project runs on GitHub Sponsors.
**Verified:** 2026-11-03 (see `QA.md`). **Status:** Researched and verified. NOT yet installed.
**Runs on:** Tech's own computer (macOS, Windows, Linux). Fully offline: audio never leaves the machine.

## Why this one

One job: press a shortcut, speak, and the words appear in whatever app is focused. It uses Whisper models plus NVIDIA Parakeet V3, which is CPU-optimised, so it is fast without a gaming GPU. Wispr Flow, by contrast, caps its free tier at 2,000 words/week and transcribes in the cloud.

## Requirements

- A desktop or laptop with a microphone (built-in is fine; a headset is better in a noisy room)
- ~1-3 GB disk for the app plus the speech model you pick
- macOS, Windows 10/11, or Linux
- No account, no API key, no secrets.

## Install steps (on Tech's machine, when he chooses)

Pick one:

```bash
# Windows
winget install cjpais.Handy

# macOS
brew install --cask handy

# Linux: download the .deb from the GitHub releases page, then
sudo apt install ./Handy_*.deb
```

## First-run setup (5 minutes)

1. Launch Handy and grant the two permissions it asks for: microphone, and accessibility (macOS) so it can type into other apps.
2. In Settings, choose the **Parakeet V3** model (best speed/accuracy balance on CPU). Whisper Large is the fallback if accuracy on a specific accent matters more than speed.
3. Set one push-to-talk hotkey you will actually use (hold to talk, release to paste).
4. Test in three places: a WhatsApp message, an email draft, and a document. Speak naturally; expect near-verbatim text.

## Workflow it serves

Founder dictation: instructions, replies and documents dictated instead of typed, across every app, with no subscription and no cloud copy of the audio. The trial succeeds if it is still in daily use after 7 days (see `docs/utilization-pipeline.md`).

## Known limitations

- Output is near-verbatim: filler words and rough punctuation stay in. Wispr Flow's AI polish is the thing you give up; a quick manual tidy is the price of $0 and offline.
- No mobile app. Phone dictation stays with the phone's built-in tools.
- On Linux/Wayland, text insertion needs a helper tool (`wtype` or `dotool`); the repo README documents the per-distro steps.
- Bluetooth headset microphones on macOS can drop playback quality while recording (documented in the repo); use the built-in or a wired mic if it bites.
