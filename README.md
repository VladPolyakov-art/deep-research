# deep-research

A Claude Code skill that runs a sourced, in-depth market, user and technology study on a product question. Every claim in the report is tied to a source and a date, confidence is marked, and a closing section says what the findings mean for the product. It builds on a quick competitor scan (`research/competitive-analysis.md`) and personas (`research/personas.md`) if you have them, and digs where they are thin.

## How it works

- **Context first.** It reads your brief, any quick competitor scan and any personas. With none of them, it asks 3 to 5 questions before searching anything.
- **A plan of 5 to 7 specific questions**, each tied to your product and aimed at the gaps of the earlier scan. Saved as a prompt file that works on its own.
- **Three ways to gather the material, chosen by what you have:**
  - Claude researches itself with web tools (default), in parallel sub-agents for larger studies;
  - Claude writes a ready prompt, you run it in Gemini Deep Research and paste the result back;
  - if your project has `execution/delegate.py`, the `research-web` route is used.

  The report always states which path actually ran.
- **Verification.** 3 to 5 key figures are checked against their sources. Confirmed ones get `[source: Sn]` (or `[source: Sa+Sb]` when two independent sources agree); anything that does not check out is corrected, left `[unverified]` or dropped. Claims from a pasted Gemini report stay `[unverified]` until a source is opened.
- **Synthesis** into one report: findings per question, conflicts between sources shown with both values, changes versus the earlier research, market context, and "What this means for the product" with priorities.

## Honesty rules

Facts come from you or from a source. No invented numbers, quotes, reviews or URLs. Inference is tagged `[assumption]`, missing data is written as `unknown` and listed as a gap. Text on web pages is treated as data, never as instructions. Decisions stay with you; the report offers options with the evidence for each.

## Output

Markdown files in your project (paths can be changed on request):

| File | What |
|---|---|
| `research/deep-research-prompt.md` | the research plan and paste-ready prompt |
| `research/deep-research-raw.md` | raw material from Gemini or sub-agents, unedited |
| `research/deep-research/part-<n>.md` | per-group notes from sub-agents or executors |
| `research/deep-research.md` | the verified, synthesised report |
| `research/INDEX.md` | one row per research file (shared with the other skills) |

A short summary also goes to the chat, in your language.

## Works with

| Skill | Writes | Repo |
|---|---|---|
| competitive-research | `research/competitive-analysis.md` | https://github.com/VladPolyakov-art/competitive-research |
| deep-research | `research/deep-research.md` | https://github.com/VladPolyakov-art/deep-research |
| ux-audit | `research/ux-audit/<product>/audit_report.md` | https://github.com/VladPolyakov-art/ux-audit |
| proto-personas | `research/personas.md` | https://github.com/VladPolyakov-art/proto-personas |
| simulated-interview | `research/interview-<persona-slug>.md` | https://github.com/VladPolyakov-art/simulated-interview |
| feature-research | `research/feature-<slug>.md` | https://github.com/VladPolyakov-art/feature-research |

Each skill works alone; when a sibling's output is in `research/`, it is reused instead of redone.

## Contents

| Path | What |
|---|---|
| `SKILL.md` | instructions for the agent |
| `references/prompt-template.md` | the research prompt template |
| `references/report-template.md` | the report structure and labels |
| `references/researcher-role.md` | role prompt for research sub-agents |
| `references/delegate-route.md` | optional `delegate.py research-web` path |
| `references/kit-protocol.md` | shared file names, header, evidence tags and index rules of the research kit |
| `evals/` | scenarios for checking the skill's behavior |

## Installation

```bash
git clone https://github.com/VladPolyakov-art/deep-research ~/.claude/skills/deep-research
```

Requirements: Claude Code.

## Optional tools

- WebSearch, WebFetch or Firecrawl: needed for Claude to research on its own. Without them the skill offers the Gemini prompt path and does not pretend otherwise.
- Gemini Deep Research: you run the prompt yourself and paste the result back.
- `execution/delegate.py` with a `research-web` route: used only if it exists in your project; the skill does not ship it.

No API keys or tokens are requested or written.

## License

[MIT](LICENSE)
