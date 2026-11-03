# QA: verification log

Every factual claim in `README.md` and `docs/oss-alternatives-7-tools-2026-11-03.md` traces to a source opened on **2026-11-03**. GitHub figures below were read from the live repository page that day (page crawl timestamps 11:34-11:36 UTC). Star counts move daily; re-verify before quoting them elsewhere.

## Pairing sources (where the genre makes each pairing)

| Pairing | Source opened 2026-11-03 |
|---|---|
| OpenSEO → SEMrush; Chatwoot → Intercom; VoiceStudio → ElevenLabs; WeKnora → Notion AI; Open Higgsfield → Higgsfield; Cap → Loom; OpenWhispr → Wispr Flow | techfamz.com, "Replace Your Paid Software With This 9 Free GitHub Repos" (updated ~2026-10-27) |
| AppFlowy → Notion (same list's second telling) | youtube.com/shorts/F-2M0UrqD2w |
| Same nine, independently checked 2026-10-28 | itmunch.com, "9 GitHub Projects To Explore As Alternatives To Popular AI And Business Apps" |

## Repo-by-repo log

| Repo | URL | Stars | Activity signal | Licence as found | Notes |
|---|---|---|---|---|---|
| every-app/open-seo | https://github.com/every-app/open-seo | 26,162 | 926 commits, 50 releases; latest v0.1.14 on 2026-10-19 (exploreai.directory, crawled 2026-11-02) | MIT (GitHub-detected) | DataForSEO key required for all data; hosted tier $10/mo + 28% data markup, both stated in its README |
| chatwoot/chatwoot | https://github.com/chatwoot/chatwoot | 38,792 | 7,033 commits, 153 releases; /releases shows v4.19.1 current | MIT core (repo footer); `enterprise/` under commercial licence; GitHub shows NOASSERTION | Captain AI features tagged [Enterprise] throughout current changelogs; dev.to (July 2026) calls Captain credit-metered, not in free CE |
| OpenWhispr/openwhispr | https://github.com/OpenWhispr/openwhispr | 10,609 | 2,541 commits, 102 releases | MIT | Pro tier $80/user/yr per speakoflow (checked 2026-10-17): open-core |
| cjpais/Handy | https://github.com/cjpais/Handy | 37,246 | 930 commits, 67 releases; latest v0.9.8 on 2026-10-03 (speakoflow) | MIT | No paid tier; Sponsors-funded (getvoibe, Oct 2026) |
| CapSoftware/Cap | https://github.com/CapSoftware/Cap | 24,308 | 12,766 commits, 85 releases | AGPLv3 overall; MIT for cap-camera*/scap-* crates (README License section) | Prebuilt app: personal use free, 5-min caps; commercial Desktop License $29/yr or $58 lifetime (opensourcedrop, Oct 2026; freealternatives.to, Jul 2026) |
| AppFlowy-IO/AppFlowy | https://github.com/AppFlowy-IO/AppFlowy | 78,139 | 7,211 commits, 154 releases | AGPL-3.0 (GitHub-detected) | Genuine Notion-style workspace |
| toeverything/AFFiNE | https://github.com/toeverything/AFFiNE | 74,152 | 11,550 commits, 599 releases | GitHub NOASSERTION; README Editions note: Community Edition MIT for self-host, Enterprise Edition separate | Mixed licence files in root (LICENSE + LICENSE-MIT) |
| debpalash/VoiceStudio | https://github.com/debpalash/VoiceStudio | 99,603 | 6,391 commits, 46 releases; created 2026-04-09 | AGPL-3.0 + LICENSE-NOTICE | Star velocity flagged: findarepo measured +11k stars in 7 days to 2026-11-02. README: "fully usable on the CPU, just slower"; Docker image published |
| hexgrad/kokoro | https://github.com/hexgrad/kokoro | 9,889 | 71 commits; versioned via PyPI (README uses kokoro>=0.9.4) | Apache-2.0; weights Apache-licensed (README) | 82M params; weights at huggingface.co/hexgrad/Kokoro-82M |
| SWivid/F5-TTS | https://github.com/SWivid/F5-TTS | 15,504 | 705 commits, 22 releases | Code MIT; pretrained models CC-BY-NC (README License section, verbatim) | Non-commercial weights: disqualified for our content |
| wide-trace/open-higgsfield | https://github.com/wide-trace/open-higgsfield | 5,272 | **3 commits, 0 releases**; created 2026-08-26 | **No LICENSE file in root listing** | Studio UI over an unnamed paid generation API (README architecture: server action POSTs to a generation API origin with your key). Corroborated by zentor.ai (2026-08-28) and itmunch (2026-10-28) |
| Wan-Video/Wan2.2 | https://github.com/Wan-Video/Wan2.2 | 18,337 | 53 commits; models current (Animate-14B, S2V-14B in README) | Apache-2.0 | README: A14B single-GPU run needs ≥80 GB VRAM; TI2V-5B runs on consumer cards "like 4090"; official HF Space for TI2V-5B linked from README |
| towfiqi/serpbear | https://github.com/towfiqi/serpbear | 2,162 | 305 commits, 16 releases; v3.1.0 in Oct 2026 install guide (dev.to) | MIT | Needs a SERP scraping API; README's own table marks some free scrapers "Doesn't work Anymore"; serper.dev listed at $1/1,000 requests |

## Claims NOT verified (stated as such in the research doc)

- Piper (local TTS) was not re-checked in this pass; Kokoro supersedes it for our use.
- Chatwoot self-host RAM (2-4 GB) is an ops estimate from its stack (Rails + PostgreSQL + Redis + Sidekiq), not a vendor figure.
- The image's "$2,934/year" total could not be reproduced exactly; the listicle's own entry-plan math gives ~$3,264/yr for the same seven tools. Plan and seat assumptions move the number either way.

## Method note

Pairings were never assumed from the image (it names no repos). Each pairing was taken from the genre's own published lists, then verified or refuted at the repo. Two pairings changed under verification: Wispr Flow's strongest pick is Handy, not the paired OpenWhispr; and the Higgsfield pairing failed verification entirely (no licence), with Wan2.2 documented as the real but GPU-blocked open route.
