# Research kit protocol

This skill is one of six research skills that work on their own and also work together:

| Skill | Writes | Repo |
|---|---|---|
| competitive-research | `research/competitive-analysis.md` | https://github.com/VladPolyakov-art/competitive-research |
| deep-research | `research/deep-research.md` | https://github.com/VladPolyakov-art/deep-research |
| ux-audit | `research/ux-audit/<product>/audit_report.md` (+ `research/ux-audit/summary.md`) | https://github.com/VladPolyakov-art/ux-audit |
| proto-personas | `research/personas.md` | https://github.com/VladPolyakov-art/proto-personas |
| simulated-interview | `research/interview-<persona-slug>.md` | https://github.com/VladPolyakov-art/simulated-interview |
| feature-research | `research/feature-<slug>.md` | https://github.com/VladPolyakov-art/feature-research |

None of them needs another. When a sibling's output is already in the project, use it instead of redoing the work. The rules below are what makes that possible, so every skill in the kit follows them the same way.

## 1. One folder, fixed names

- Everything goes into `research/` at the project root unless the user names another folder. If they do, use that folder for every file and say so in the summary.
- Use the file names in the table above exactly. Siblings find each other's work by these names, not by asking.
- Extra material (raw dumps, screenshots, transcripts, per-competitor notes) goes into files or subfolders that start with the same stem, e.g. `research/deep-research-raw.md`, `research/competitive-analysis/screenshots/`.
- Rerun on an existing file: update it in place and add a dated line under "Changes" at the bottom. Do not create `-v2` copies.

## 2. Header block

Every main output file starts with this block, right under the title:

```markdown
> Skill: <skill name> · Date: <YYYY-MM-DD> · Product: <name, one line>
> Inputs: <files and sources this file was built from, e.g. "research/personas.md, user brief in chat, 14 web sources">
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)
```

The `Inputs` line is how a reader, or a sibling skill, knows what the file rests on.

## 3. Shared evidence tags

Every claim that matters carries one tag. The same tags mean the same thing in every skill, so a claim can travel from one file to another without losing its weight.

| Tag | Meaning |
|---|---|
| `[user]` | said by the user in chat or written in their own files; name the file when there is one: `[user: docs/brief.md]` |
| `[source: Sn]` | from a page or document that was actually opened; `Sn` is its row in the file's Sources list |
| `[snippet: Sn]` | seen only in a search-result excerpt, page not opened |
| `[unverified]` | known from model memory, not checked against a source |
| `[assumption]` | reasoning or inference, not checked; should point to a gap `G<n>` when the file has a gaps list |
| `[estimate]` | a size, effort or quantity guess, with what it assumes |
| `[synthetic]` | said by a simulated persona; a hypothesis, never evidence |

- A qualifier may follow after a comma: `[source: S3, vendor]`, `[source: S4, weak]`, `[source: S1+S5]` (two independent sources agree).
- No data at all: write `unknown` in plain text and add the item to the gaps or open questions. Never fill the hole with a guess.
- Every file that uses `[source]` or `[snippet]` ends with a **Sources** list: `S<n> · title · URL · accessed YYYY-MM-DD · type (official / review / forum / vendor / news / research)`.
- Every file ends with the tag legend (copy the table above, it is short), so the file reads on its own.

## 4. Reusing a sibling's output

At the start (in the read-only reconnaissance step), list `research/`. For each file from the table that exists:

- read it and use it as an input; name it in your `Inputs` line;
- keep its tags when you carry a claim over. Re-cite its source in your own Sources list (same URL, your own `Sn`); do not upgrade the tag. An `[assumption]` in personas stays an `[assumption]` in a feature report;
- `[synthetic]` claims stay `[synthetic]` wherever they go;
- if it looks stale (older than about 3 months, or the product changed), say so and ask whether to refresh it, unless the user already said;
- do not edit a sibling's file. If you find an error in it, mention it in your summary.

If nothing is there, work from what the user gives you. Never ask the user to run another skill first.

## 5. Index

After writing, update `research/INDEX.md` (create it if missing). One row per file, newest first; replace your own row on a rerun:

```markdown
# Research index

| File | Skill | Date | One-line takeaway |
|---|---|---|---|
| research/personas.md | proto-personas | 2026-10-25 | Primary: shift nurse who swaps shifts by chat; 41% of items are assumptions |
```

## 6. Next step

In the final chat summary, add at most one line suggesting the sibling that would deepen the weakest part of this result, e.g. "personas rest mostly on assumptions -> `simulated-interview` can find what to ask real users". If that skill is not installed (check `~/.claude/skills/<name>/` and `.claude/skills/<name>/`), give its repo link from the table. Suggest; never run it without the user's go-ahead.
