# Utilization Pipeline: how TechAura actually runs this stack

This is the operating pipeline for the open-source stack. Every tool moves through three stages, and nothing skips a stage:

- **Verify** — the repo, licence and costs are checked against live sources. Entry criteria: GitHub repo opened and recorded in `QA.md`; licence read in the repo itself, not in a blog post; the real cost (data, hosting, licences) named in one line. *All seven categories in this repo have passed Verify on 2026-11-03.*
- **Trial** — the tool runs on one real, bounded workflow with a time box. Entry criteria: Tech approves any spend or hosting the trial needs; a named workflow and a single success metric are written down before the trial starts.
- **Adopt** — the tool becomes part of a standing workflow. Entry criteria: the trial hit its metric, the operating cost is known and accepted, and the run notes live in `tools/<name>.md`.

**Hard constraints that shape every stage:** the Aurah VM has no GPU, ~7 GB RAM and 2 CPUs, and no guaranteed public inbound endpoint. Anything needing a GPU or a public web endpoint is marked **machine-blocked on this VM** and named with its real home instead. Nothing in this document edits or assumes a scheduled job: where a daily job could later consume a tool, the step is labelled **PROPOSED** and stays unimplemented until Tech approves it.

---

## 1. Kokoro-82M — narration for animated content (ElevenLabs slot)

- **Workflow it plugs into:** Content/video production. The daily HyperFrames animated-video line (live since 2026-11-03) needs a voiceover for every video. Kokoro serves the non-Tara animated content only. Tara reels keep the locked Aria voice; this tool never touches them.
- **Stage:** Verify passed 2026-11-03. Ready for Trial on Tech's word (no spend, no hosting needed).
- **Who runs it:** Aurah, on this VM's CPU, inside `~/workspace/tools/`. This is the one AI model in the stack that fits the VM.
- **First step on approval:** Follow `tools/kokoro-82m.md`: create the venv, install, render a ~20-second narration from the next scheduled animated video's script, and A/B it against that video's current voiceover.
- **Success metric:** Cost per finished video narration = $0, and the A/B narration passes the same frame-by-frame review standard as current output. If quality fails review twice, the trial ends and narration stays as-is.
- **PROPOSED wiring (not implemented):** if the trial passes, propose adding a Kokoro narration step to the morning video pipeline's animated-video stage, with the existing voice kept as fallback. Requires Tech's explicit approval before any job changes.

## 2. Handy — founder dictation (Wispr Flow slot)

- **Workflow it plugs into:** Founder dictation. Tech runs TechAura by voice note; Handy puts dictation into every text field on his own computer (WhatsApp, email, documents, browser forms), offline, with no word caps.
- **Stage:** Verify passed 2026-11-03. Ready for Trial; the trial is Tech's own usage, no approval gate beyond his choice to install.
- **Who runs it:** Tech's machine only (macOS, Windows or Linux desktop). It cannot run on this VM (no microphone, no desktop) and does not need to.
- **First step on approval:** Follow `tools/handy.md`: install, choose the Parakeet V3 model (CPU-optimised), set one hotkey, dictate one real instruction end to end.
- **Success metric:** Tech is still dictating with it after 7 days of normal work. That is the whole test.

## 3. OpenSEO — SEO for techaurah.com and client audits (SEMrush slot)

- **Workflow it plugs into:** Website growth (SEO/GEO/AEO for techaurah.com and the GitHub portfolio) and the client audit offer (a real site-audit and competitor module inside the free audit).
- **Stage:** Verify passed 2026-11-03. Trial is gated on one spend decision: a $50 minimum DataForSEO deposit (data is pay-per-request after that; the software itself is MIT and free).
- **Who runs it:** Aurah. Hosting options that fit our constraints: self-host on Cloudflare (the project documents a free-plan deployment) or Docker on this VM. All data calls go to DataForSEO's API.
- **First step on approval:** Create the DataForSEO account and deposit, deploy OpenSEO on Cloudflare, connect techaurah.com, and run one baseline: keyword set + rank snapshot + full site audit for techaurah.com.
- **Success metric:** One complete baseline audit produced for techaurah.com, and a per-audit data cost (in dollars) measured and recorded. If a full audit costs more than a few dollars in data, the trial pauses for a cost review.
- **PROPOSED wiring (not implemented):** connect OpenSEO's MCP server to the agent tooling so scheduled SEO checks can query rankings directly. Proposal only until the trial passes.

## 4. Chatwoot — website front desk inbox (Intercom slot)

- **Workflow it plugs into:** The website front desk: live chat on techaurah.com plus one owned inbox for site, email and social inquiries, feeding the qualify, warm, hand-over flow Aurah already runs. Second life: a deployable component inside client AI Lead Automation builds.
- **Stage:** Verify passed 2026-11-03. Trial is gated on a hosting decision.
- **Who runs it:** **Machine-blocked on this VM** for production: Chatwoot needs a public HTTPS endpoint for its widget and channel webhooks, and ~2-4 GB RAM of headroom. Real home: a small VPS (~$5-10/mo) under TechAura's control. Aurah operates it once hosted.
- **First step on approval:** Provision the VPS, deploy the Docker Compose production stack, put the live-chat widget on a staging page of techaurah.com only, and run one week of real inquiries through it in parallel with the current front-desk handling.
- **Success metric:** Zero inquiries lost versus the current handling during the parallel week, measured by comparing inquiry counts day by day. Any lost inquiry ends the trial.
- **Licence honesty for the trial:** the inbox core is MIT and free; the Captain AI agent is effectively a paid/enterprise feature, so the trial is for the inbox, not for a free Fin clone.

## 5. Cap — client demos and walkthroughs (Loom slot)

- **Workflow it plugs into:** Client demos: audit walkthroughs, async client updates, and short product demos recorded on Tech's screen and shared as links.
- **Stage:** Verify passed 2026-11-03. Trial needs one small decision: Desktop License at $29/yr for commercial use of the prebuilt app, or build from source for $0, or self-host later.
- **Who runs it:** Tech's machine (desktop recorder). The optional self-host stack (Docker: web, media server, MySQL, MinIO) would go on the same VPS class as Chatwoot if ever needed; it is not needed to start.
- **First step on approval:** Install the desktop app, record one real audit walkthrough, send it to one real client conversation, and note the time taken versus the current way of explaining.
- **Success metric:** The walkthrough is used in a live client thread and replaces at least one explanatory call or long message exchange.

## 6. VoiceStudio — voice cloning and dubbing bench (ElevenLabs slot, second seat)

- **Workflow it plugs into:** Content experiments: dubbing and cloned-voice drafts, on demand only. It does not feed the daily pipeline (that is Kokoro's seat, if adopted).
- **Stage:** Verify passed 2026-11-03, with a hype caution recorded in the research doc. Trial only if a concrete cloning or dubbing need appears.
- **Who runs it:** Tech's machine (Electron desktop app). The Docker backend on this VM is technically possible but CPU inference on 2 cores would be slow; not its home.
- **First step on approval:** Install on Tech's machine, clone one consented voice (Tech's own), generate one short script, judge quality against the need that triggered the trial.
- **Success metric:** The generated clip is good enough to use in the piece of work that triggered the trial. No usage, no adoption.

## 7. Higgsfield slot — no tool adopted

- **Open Higgsfield: rejected at Verify.** No licence file (not open source in law), 3 commits, and it is a front-end over a paid generation API. There is no trial stage for it.
- **Wan2.2 (the real open video model): machine-blocked.** Its own README puts the flagship model at 80 GB VRAM and the small model on a 24 GB consumer GPU; this VM has no GPU. The only sanctioned experiment route is the official Hugging Face Space for the TI2V-5B model, used manually, with no pipeline depending on it.
- **Standing position:** daily video content continues on the HyperFrames animated line, which needs no generative model. This slot is revisited only if GPU hardware or a legitimate free hosted tier appears.

## Notion slot — closed

AppFlowy and AFFiNE both passed Verify as healthy open source, and both are **closed on fit**: TechAura's knowledge already lives in agent-readable files and the Command Center. Reopen only if a human team needs a shared visual workspace.

---

## Adoption ledger

| Tool | Category | Stage | Gate |
|---|---|---|---|
| Kokoro-82M | ElevenLabs | Trial-ready | Tech's word only |
| Handy | Wispr Flow | Trial-ready | Tech installs on his machine |
| OpenSEO | SEMrush | Trial-gated | $50 DataForSEO deposit (Tech's call) |
| Chatwoot | Intercom | Trial-gated | VPS hosting decision (~$5-10/mo) |
| Cap | Loom | Trial-gated | $29/yr licence or source build (Tech's call) |
| VoiceStudio | ElevenLabs | On demand | A real cloning/dubbing need |
| Wan2.2 | Higgsfield | Machine-blocked | GPU hardware we do not have |
| Open Higgsfield | Higgsfield | Rejected | No licence; paid API wrapper |
| AppFlowy / AFFiNE | Notion | Closed | Reopen only for a human team workspace |
