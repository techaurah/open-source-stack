# Tool card: Kokoro-82M (local TTS)

**Replaces:** ElevenLabs-style text-to-speech for non-Tara animated content.
**Repo:** https://github.com/hexgrad/kokoro · Weights: https://huggingface.co/hexgrad/Kokoro-82M
**Licence:** Apache-2.0 (code and weights). Commercial use is allowed.
**Verified:** 2026-11-03 (see `QA.md`). **Status:** Researched and verified. NOT yet installed.
**Runs on:** This VM (CPU only). 82M parameters; no GPU needed or used.

## Hard rule

Tara reels keep the locked Aria voice. Kokoro is for the animated brand-video line and experiments only. It has no voice cloning and a fixed voice roster; do not present its output as any real person.

## Requirements

- Python 3.10+ and a venv under `~/workspace/tools/`
- `espeak-ng` on the system (phoneme fallback for English and several languages)
- ~330 MB one-time model download from Hugging Face on first run
- No API keys. No accounts. No secrets of any kind.

## Install steps (run only after Tech approves the trial)

```bash
cd ~/workspace/tools
python3 -m venv kokoro-venv
./kokoro-venv/bin/pip install kokoro soundfile
# system dependency (package manager step, run with normal admin rights):
#   espeak-ng
```

## First trial run

```python
from kokoro import KPipeline
import soundfile as sf

pipeline = KPipeline(lang_code='a')  # 'a' = American English, 'b' = British English
text = open('script.txt').read()     # the next animated video's real script
for i, (_, _, audio) in enumerate(pipeline(text, voice='af_heart', speed=1)):
    sf.write(f'narration-{i}.wav', audio, 24000)
```

1. Put the next scheduled animated video's script in `script.txt` (about 20 seconds of speech for the trial).
2. Generate the WAV parts, join them in order, and mux under the video exactly as the current voiceover is handled.
3. A/B against the same video with its current voiceover. Judge on: clarity, pacing at the locked caption timing, and whether it passes the frame-by-frame review standard.

## Config template (no secrets exist for this tool)

```bash
# ~/workspace/tools/kokoro/config.env.example
KOKORO_LANG=a            # a = US English, b = UK English
KOKORO_VOICE=af_heart    # any voice id from the Kokoro-82M voice list
KOKORO_SPEED=1.0
KOKORO_OUTDIR=~/workspace/tools/kokoro/out
```

## Workflow it serves

Daily animated brand videos (HyperFrames line): script → Kokoro narration (local, $0) → captions → render → review → post. If the trial passes, wiring Kokoro into the morning pipeline is a separate PROPOSED step in `docs/utilization-pipeline.md` and needs Tech's explicit approval; this card does not change any job.

## Known limitations

- Fixed voices only; less expressive range than ElevenLabs flagship models.
- English is strongest; other languages vary by voice pack.
- The library is a small, stable codebase (71 commits at verification): treat it as a finished utility, pin the version in the venv.
