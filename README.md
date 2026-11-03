# open-source-stack

**open-source-stack is TechAura's verified shortlist of open-source replacements for rented SaaS tools: seven paid products from a viral "7 GitHub repos" post, each paired with the open-source project the genre actually means, every repo checked live on GitHub on 2026-11-03, every licence read in the repo itself, and every tool mapped to a real TechAura workflow with an adoption gate.**

Most "open-source alternatives" lists are catalogues. This one is an operating document for a single business: what each tool would do here, what it truly costs (several "free" swaps are not free), what hardware it needs, and what happens next. Two of the seven pairings fail verification or fit, and this repo says so instead of repeating the post.

## The 7 pairings, verified 2026-11-03

| Paid tool | Open alternative | Licence | Stars* | Verdict |
|---|---|---|---|---|
| SEMrush ($139/mo) | [OpenSEO](https://github.com/every-app/open-seo) | MIT | 26.2k | Trial later: software free, data is pay-per-use (DataForSEO) |
| Intercom ($39/mo) | [Chatwoot](https://github.com/chatwoot/chatwoot) | MIT core, proprietary enterprise dir | 38.8k | Trial later: needs a small hosted home, not this VM |
| Wispr Flow ($15/mo) | [Handy](https://github.com/cjpais/Handy) | MIT | 37.2k | **Adopt first**: $0, offline, no paid tier (the posts pair OpenWhispr; Handy is the stronger pick) |
| Loom ($18/mo) | [Cap](https://github.com/CapSoftware/Cap) | AGPLv3 + MIT parts | 24.3k | Trial later: commercial desktop use is $29/yr unless self-built or self-hosted |
| Notion ($20/mo) | [AppFlowy](https://github.com/AppFlowy-IO/AppFlowy) / [AFFiNE](https://github.com/toeverything/AFFiNE) | AGPL-3.0 / MIT (CE) | 78.1k / 74.2k | Skip for now: healthy projects, redundant with our files + Command Center |
| ElevenLabs ($22/mo) | [Kokoro-82M](https://github.com/hexgrad/kokoro) | Apache-2.0 (code and weights) | 9.9k | **Adopt first**: runs on a plain CPU, drops into our daily animated-video pipeline |
| Higgsfield ($19/mo) | "Open Higgsfield" | **None: no licence file** | 5.3k | Skip: not verifiably open source, 3 commits, a UI over a paid API |

*Stars as read on each GitHub repo page on 2026-11-03. Prices are the listicles' single-seat entry plans. Full evidence, catches and per-tool analysis: [docs/oss-alternatives-7-tools-2026-11-03.md](docs/oss-alternatives-7-tools-2026-11-03.md). Verification log: [QA.md](QA.md).

Two traps this repo exists to catch:

- **F5-TTS** looks like the ElevenLabs answer (15.5k stars, MIT code) but its pretrained weights are **CC-BY-NC, non-commercial**. It cannot legally voice commercial content. Details in the research doc.
- **"Open Higgsfield"** is not a video model and not licensed open source. The real open video models (Wan2.2, Apache-2.0) need a GPU we do not have; that is stated plainly in the pipeline doc rather than wished away.

## Honest status

- **Researched and verified:** all seven categories, 2026-11-03.
- **Installed:** nothing yet. Adoption follows the stage gates in [docs/utilization-pipeline.md](docs/utilization-pipeline.md) (verify → trial → adopt), and two tools are trial-ready with zero spend: Kokoro-82M and Handy.
- **Savings claim, corrected:** TechAura pays $0 today for the seven paid tools, so this stack is capability gained at near-zero cost, not $2,934/yr saved. Where a swap has a real cost (OpenSEO's data, Chatwoot's hosting, Cap's licence), the pipeline doc names it before any trial.

## How this differs from the big lists

- [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) (~333k stars) is the definitive general catalogue of self-hostable software; breadth is its job.
- [findarepo.com](https://findarepo.com/categories/self-hosted/) ranks self-hosted repos by measured star velocity, daily.
- [ossfind.com](https://www.ossfind.com/) scores SaaS alternatives on adoption, maintenance and commercial-use risk.
- [purist.online](https://www.purist.online/pages/open-source-tools) builds replacement stacks interactively from your current subscriptions.
- This repo is deliberately narrower than all of them: one company's seven slots, verified on a date, with licence traps flagged, hardware limits applied, and a named workflow, owner and success metric per tool.

## Contents

- `docs/oss-alternatives-7-tools-2026-11-03.md` — the full research: per-tool verification, value assessment, limitations, ranked shortlist.
- `docs/utilization-pipeline.md` — the operating pipeline: stage gates, who runs each tool and where, the exact first step on approval, one success metric per tool.
- `tools/kokoro-82m.md`, `tools/handy.md` — install and usage cards for the two Adopt First tools. Config templates only; no secrets; nothing installed by this repo.
- `QA.md` — the verification log behind every claim in the table above.

## Licence

This documentation is MIT licensed (see `LICENSE`). Each tool named here keeps its own licence, recorded in the research doc; check it there before use.
