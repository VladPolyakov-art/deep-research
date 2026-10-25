# Report template: `research/deep-research.md`

Fill every section. If a section has nothing, write "none" and why. Source ids (S1, S2, ...) point to the Sources list at the end. Dates are ISO (YYYY-MM-DD). Shared tags and rules: `kit-protocol.md`. On a rerun, update the file in place and add a dated line under "Changes".

```markdown
# Deep research: <topic or product>

> Skill: deep-research · Date: <YYYY-MM-DD> · Product: <name, one line>
> Inputs: <files and sources this file was built from, e.g. "research/competitive-analysis.md, research/personas.md, docs/brief.md, 14 web sources opened"; or "user answers in chat only">
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)

> Scope: <market, languages, period, competitors>
> Path used: <A Claude with web tools | B Gemini Deep Research pasted by the user | C delegate.py research-web | combination, say which parts>
> Confidence: High / Medium / Low per finding (rules in the legend). Prices, vendor rules and rankings change quickly; this is a snapshot of the date above.

## 1. Executive summary
Five to seven findings, most decision-relevant first. Each: the finding, tag, confidence, source ids.
1. **<Finding>.** [source: S3+S7] High
2. ...

## 2. Scope and method
- Questions asked (numbered, as in the prompt file).
- How the raw material was gathered (what actually ran; which tools; how many sources per question).
- Sibling files reused and how (e.g. "gaps 1 to 4 of competitive-analysis.md became Q1 to Q4"). Stale ones flagged.
- What was verified (section 8) and what was not (section 9).

## 3. Findings by question
### Q1. <question>
**Answer.** <3 to 6 sentences, facts only.>

| Claim | Evidence (what the source says) | Source | Date | Tag | Confidence |
|---|---|---|---|---|---|
| ... | ... | S1 | 2026-.. | [source: S1] | Medium |
| ... | lead: <URL cited by Gemini> | none | 2026-.. | [unverified] | Low |

**Interpretation.** [assumption] <what this suggests, kept apart from the table> (G1)
**Conflicts.** <both values and both sources, or "none found">
**Gaps.** unknown: <what could not be found> (G2)

(repeat for each question)

## 4. Changes versus earlier research
Only if sibling files were reused (quick scan, personas, other). Do not edit those files; record the difference here.
| # | Claim in the earlier file (file, tag as it was) | What this research showed | Effect |
|---|---|---|---|
| 1 | ... | ... | confirmed / weakened / refuted / refined |

## 5. Market context
Size and growth, segments, trends, pricing models. Each figure with source, date and tag. If figures from different sources disagree, a table with both values and the publisher of each.

## 6. What this means for the product
Implications are [assumption]: they rest on the facts above but are judgement. Decisions remain with the owner.
| # | Implication | Based on | Tag | Confidence | Priority | Feeds decision |
|---|---|---|---|---|---|---|
| 1 | <e.g. table stakes to match / gap to exploit / risk to plan for> | S2, S5 | [assumption] (G3) | Low | P1 | <scope / pricing / positioning> |

Then, in a few lines: what to do first, what to validate with real users before committing, and which options the evidence leaves open.

## 7. Open questions for the owner
Decisions or data only the owner can supply.

## 8. Verified
| Claim | Source | Check done | Result | Date |
|---|---|---|---|---|
| ... | S4 | opened page, matched exact sentence | confirmed (now [source: S4]) / differs: real value ... / page dead | 2026-.. |

## 9. Not verified
Claims left as `[unverified]`, `[snippet]` or `[source: Sn, relayed]` that conclusions still lean on, and claims dropped for lack of a source ("not carried over").

## 10. Gaps
G1 · <what is unknown or unchecked> · <why it matters> · <what would close it>

## Sources
S1 · <title, publisher, published YYYY-MM-DD> · <URL> · accessed <YYYY-MM-DD> · <official / review / forum / vendor / news / research>
S2 · ... (add ", relayed" to the type when only a sub-agent opened the page)

## Tag legend
| Tag | Meaning |
|---|---|
| `[user]` | said by the user in chat or written in their own files; name the file when there is one: `[user: docs/brief.md]` |
| `[source: Sn]` | from a page or document that was actually opened; `Sn` is its row in the file's Sources list |
| `[snippet: Sn]` | seen only in a search-result excerpt, page not opened |
| `[unverified]` | known from model memory, not checked against a source |
| `[assumption]` | reasoning or inference, not checked; should point to a gap `G<n>` when the file has a gaps list |
| `[estimate]` | a size, effort or quantity guess, with what it assumes |
| `[synthetic]` | said by a simulated persona; a hypothesis, never evidence |

Qualifiers after a comma: `[source: S3, vendor]`, `[source: S4, weak]`, `[source: S1+S5]` (two independent sources agree), `[source: S6, relayed]` (page opened by a sub-agent, not by the author). No data: `unknown`, listed under Gaps.
Confidence: High = two independent opened sources, or an official primary source opened and checked. Medium = one decent opened source or a matching relayed quote. Low = vendor, weak, conflicting, snippet, unverified or assumption.

## Changes
- <YYYY-MM-DD> · <what changed in this run>
```

## Style notes
- Facts in tables; interpretation tagged and kept apart.
- Paraphrase sources; keep direct quotes short and only ones you actually saw.
- Voice-of-user evidence from public reviews is direction, not proof. Say so.
- Do not round up certainty: a single blog post is Low, however confident its tone.
