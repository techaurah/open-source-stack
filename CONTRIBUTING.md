# Contributing

This repo is TechAura's internal adoption record for open-source tools, published so the research is reusable. Contributions follow the same standard the repo was built to:

1. **Verify at the source.** Any claim about a tool (stars, licence, pricing, requirements) must be checked on the project's own GitHub repo or official docs, and the check date recorded in `QA.md`. Blog posts and listicles are leads, never evidence.
2. **Licences are read, not assumed.** Quote the licence from the repo itself. If a project has no licence file, say exactly that. If code and model weights carry different licences, both go in the record.
3. **Costs stay honest.** If a "free" tool needs a paid API, a licence for commercial use, or hosting, the cost is named in the same breath as the tool.
4. **Status labels are real.** A tool is "researched", "verified", "in trial" or "adopted", and the label only changes when the stage gate in `docs/utilization-pipeline.md` is actually met. Nothing here is described as installed unless it is.
5. **No secrets, ever.** Config examples are templates with placeholders only. No API keys, tokens or credentials in any file, commit or issue.

To propose a change to a verdict: open an issue or a pull request with the new evidence (repo link, what changed, date checked) and the QA.md entry updated to match.
