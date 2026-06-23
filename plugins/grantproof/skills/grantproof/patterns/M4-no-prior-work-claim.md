# M4 — No-prior-work claim

**Trigger pattern**: Any framing that explicitly or implicitly asserts the absence of prior credible work — the "no anchor" claim class.

This is a semantic pattern, not a literal word match. `../triggers.json` lists representative anchor phrases; detection should also catch paraphrases and variant families that make the same underlying claim.

## Variant families to catch

- **Direct negation of prior work**: *"nobody has done this before," "no one has tried this," "no prior work exists," "there is no published research on this," "no existing literature addresses this."*
- **First-mover claims**: *"we are the first to investigate / develop / measure …," "first ever," "first of its kind."*
- **Absence-by-implication**: *"unprecedented in our field," "never been attempted," "never been tried."*
- **Pioneer framing**: *"we are pioneering …," "we are blazing a trail in …."*
- **Until-now framing**: *"until now, nobody has …," "to date, no work has …."*

If the phrasing carries the message *"there is no credible prior effort to anchor against,"* it triggers M4 — even if none of the exact anchor phrases appear.

**Stay silent on** claims that acknowledge prior work while asserting a specific gap (e.g., *"existing approaches focus on X; we propose Y"*). Those are anchored, not no-anchor.

## Why this lands wrong with reviewers

Counter-intuitively backfires. Claiming "nobody has done this" gives reviewers no anchor and invites them to find prior work themselves to attack the claim. Reviewers reward founders who can place their work on a clear map of past credible efforts.

## Rewrite structure

`Prior work in [adjacent domain] has [established result — with citation]; our R&D addresses the open question of [the specific gap your work fills].`
