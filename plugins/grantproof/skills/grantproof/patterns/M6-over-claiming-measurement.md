# M6 — Over-claiming measurement

**Trigger pattern**: *"measures [an inferred or unobservable phenomenon]"* — claiming direct measurement of something that is actually inferred from observable indicators.

This is a semantic pattern, not a literal word match. `../triggers.json` lists representative phrases; detection should also catch close variants.

## Why this lands wrong with reviewers

Most "measurements" of unobservable phenomena are correlations between observable indicators and the phenomenon — established through validity studies. Claiming direct measurement invites reviewers with measurement training to attack the methodology, which is rarely the focal R&D question.

## Rewrite structure

`[Your system] extracts [specific behavioral indicators] that plausibly relate to [what you're trying to measure]; the focal R&D question is whether these indicators predict [an established external measure] in [defined sample].`

## Note on voice

When writing this back to the user, say "what you're trying to measure" — not "construct."
