# Grantproof

A free Claude Skill that rewrites founder prose into the register government R&D grant reviewers reward — across **NSF SBIR/STTR, DoD SBIR, NIH SBIR, DOE, DARPA, NASA**, and similar federal R&D grant programs.

Paste your draft → get back specific, falsifiable, reviewer-ready rewrites — with explanations for every change.

> Most founders write R&D grant pitches in marketing register: confident, absolute, feature-focused. Reviewers reward the opposite — **describe uncertainty, not capability**. This skill teaches the inversion on your own draft.

---

## What it does

The skill scans your prose for seven common writing-style mistakes government R&D grant reviewers consistently downgrade:

1. **Absolute terms** (*always, every, all, completely, guarantee, the best, the most, revolutionary*)
2. **Marketing superlatives** (*unparalleled, breakthrough, game-changing*)
3. **Product-development framing** (*spin out of, version 2 of, fork of, build out the X feature*)
4. **No-prior-work claims** (*"nobody has done this before," "we are the first to," "unprecedented," "never been attempted"*)
5. **Vague impact language** (*will help [vague noun]*, "if we do this, something good will happen")
6. **Over-claiming measurement** (*"measures critical thinking" / "measures situational awareness"*)
7. **Uncited factual claims** (dollar figures, percentages, trend statements without sources)

For each mistake detected, you get:
- The exact phrase quoted from your draft
- A one-sentence explanation of why it backfires with reviewers
- A sample rewrite structure — an abstract template you apply to your own content

The skill does **not** rewrite your passage for you. It teaches the pattern; you write the substance. The deeper frameworks behind these patterns (Three-Tier Mountain of Challenges, PRSEL, Three-Tier Impact Structure, Falsifiable Hypothesis Test, Reference Relocation Strategy, and others) live in the full **NSF SBIR Pitch Playbook**.

The patterns apply across NSF SBIR/STTR, DoD SBIR, NIH SBIR, DOE, DARPA, NASA, NOAA, and similar federal R&D grant programs.

### Who uses it

**Primarily founders editing their own drafts** — short Project Pitches through full Phase I proposals.

**Also useful for evaluators**: program officers, foundation reviewers, and R&D-savvy angels paste incoming drafts to surface the questions they should ask before approving or investing. The same pattern detection serves both sides — founders read it as "what to fix"; evaluators read it as "what to challenge."

---

## How to use it

### The easy path — get install instructions + a starter prompt by email

**→ [Get the skill at elleyuanwang.com/sbir-pitch](https://elleyuanwang.com/sbir-pitch)**

Drop your email and you'll get:
- The install command for Claude Code
- A sample passage to try the skill on first
- Launch-week pricing for the full **NSF SBIR Pitch Playbook** when it ships (the first in the playbook series)
- Occasional notes on what the author is seeing across recent reviewer panels

No spam, unsubscribe one click.

---

## Installation

### Claude Code via custom marketplace source

Install directly from this public GitHub repo. Run these as **two separate Claude Code messages** — do not paste both lines into the prompt at once.

```
/plugin marketplace add https://github.com/ellewangyuan/grantproof
```

After that finishes, run:

```
/plugin install grantproof@grantproof
```

Use the HTTPS URL. The shorter `ellewangyuan/grantproof` form may make Claude Code try SSH, which can fail if GitHub is not already in your known_hosts file.

Then use it by typing `/grantproof:grantproof` in Claude Code. Claude Code namespaces plugin-installed skills as `/plugin-name:skill-name`.

### Claude Code via npx (one command, agent-agnostic)

```bash
npx skills add ellewangyuan/grantproof --global
```

Installs to `~/.claude/skills/grantproof/` and the skill is available in every Claude Code session. Drop the `--global` flag to install only to the current project (`./.claude/skills/grantproof/`).

The `skills` CLI (Vercel Labs) is agent-agnostic — it also targets Codex, Cursor, OpenCode, Gemini CLI, Kimi Code, and 60+ other agents. Use `-a <agent>` to install for a specific one.

Useful follow-ups:

```bash
npx skills add ellewangyuan/grantproof --list   # see what's in the repo before installing
npx skills add ellewangyuan/grantproof -a codex # install for Codex instead of Claude Code
```

### Claude Code manual install

Clone directly into your skills directory:

```bash
git clone https://github.com/ellewangyuan/grantproof.git ~/.claude/skills/grantproof
```

Then use it by typing `/grantproof` in Claude Code. Standalone skills (not installed via the plugin marketplace) are not namespaced.

### Other coding agents

Codex, Cursor, OpenCode, Kimi Code, Gemini CLI, and other local coding assistants can use the same core skill. The simplest path is to send the agent this repo link and ask it to use the Grantproof skill:

https://github.com/ellewangyuan/grantproof

If the agent can read GitHub repos or browse files, it should start from [SKILL.md](./SKILL.md). Some agents can also install the skill for you if they have filesystem access and a known local skills directory.

The Claude Code plugin gives Claude Code a custom marketplace-source install flow and the `/grantproof:grantproof` command. Other agents usually do not use that command surface.

---

## How this skill is structured

```
grantproof/
├── SKILL.md                 # Orchestration: voice, output format, calibration, what-not-to-do
├── triggers.json            # Closed-world trigger word/phrase lists per pattern
├── patterns/                # One file per detection pattern
│   ├── M1-absolute-terms.md
│   ├── M2-marketing-superlatives.md
│   ├── M3-product-development-framing.md
│   ├── M4-no-prior-work-claim.md
│   ├── M5-vague-impact.md
│   ├── M6-over-claiming-measurement.md
│   └── M7-uncited-claims.md
├── README.md                # This file
├── LICENSE
├── .claude-plugin/          # Claude Code marketplace manifest
└── plugins/grantproof/      # Plugin layout for /plugin install
```

The skill is data-driven. `SKILL.md` is the orchestrator — it owns the voice rules, the output format, calibration logic, and what's out of scope. The detection catalog itself lives in `triggers.json` (closed-world word/phrase lists) and `patterns/MN-*.md` (one file per pattern with the reviewer-side rationale and the canonical rewrite structure). Edits to a pattern's wording live in the pattern file, not in SKILL.md.

---

## Example

**Your draft:**

> Company A's continuous glucose sensor delivers the most accurate readings of any wearable on the market.

**Skill output:**

### Suggestion 1
**Where**: *"the most accurate readings"*
**Pattern**: M1 — Absolute terms
**Why this lands wrong with reviewers**: Nothing in the claim can be tested. "The most" has no defined comparator and no measurement method — reviewers either dismiss it as marketing or look for one counter-example to attack the whole claim.
**Rewrite structure**:
`[Your product / system] [achieved / demonstrated / produced] [your measured outcome] on [named metric] in [defined sample], compared to [named comparator condition].`

### Suggestion 2
**Where**: *"of any wearable on the market"*
**Pattern**: M7 — Uncited factual claims
**Why this lands wrong with reviewers**: A comparative claim against every other wearable, presented without a source. Reviewers cannot evaluate a comparison they can't verify.
**Rewrite structure**:
`[Your claim] ([citation — name the peer-reviewed paper, government report, or industry data source]).`

> Found **2** writing-style issues. The deeper frameworks behind these patterns live in the full **NSF SBIR Pitch Playbook**.
>
> Launch-week pricing for waitlist subscribers: **https://elleyuanwang.com/sbir-pitch**

**Found a rewrite that helped?** Share the screenshot on LinkedIn or send it to your co-founders. The skill's outputs are plain text — they paste cleanly anywhere.

---

## Philosophy

> Describe uncertainty, not capability.

This is the single most counter-intuitive rule in grant writing — and the one founders most reliably get wrong.

Founders write R&D grant pitches in marketing register: confident claims, absolute terms, product features. They've been trained for it by every investor pitch they've ever given. Reviewers reward the opposite. Specific, falsifiable, evidence-anchored prose wins. Vague, absolute, unfalsifiable prose loses.

This skill exists to enforce that inversion on your draft, line by line, until it feels natural. The full playbook teaches the underlying mental model — *why* reviewers reward uncertainty, and how to write prose that survives the panel.

---

## Privacy

Your draft is processed by Claude (Anthropic). [Anthropic's data policies apply](https://www.anthropic.com/legal/privacy). The skill itself doesn't transmit your data anywhere else.

---

## About the author

Created by **Dr. Elle Yuan Wang**:

- **PhD, Cognitive Sciences & Learning Analytics** — Columbia University
- **Served as an NSF SBIR/STTR reviewer** (America's Seed Fund)
- **Lead Scientist & Advisor**, AI-ALOE (National AI Institute for Adult Learning and Online Education)
- **Advisor**, ASU Online
- **Judge / advisory board**: $5M XPRIZE IBM Watson AI for Good · $1M XPRIZE-IES Digital Learning Challenge · $4M Learning Engineering Tools Competition
- **Coached and supported $21M in collective R&D grant funding** over 10 years across federal R&D grant programs
- Strategic roles: Columbia Tech Ventures · MTV Networks · NYC Mayor Bloomberg's Office

> A note on what this skill can and cannot do: it enforces a more rigorous writing register that R&D grant reviewers reward. Writing register is one layer of why a proposal gets funded — it does not guarantee approval. Strong writing supports a strong project; it cannot substitute for one.

---

## Get the full playbook

The skill catches surface-level patterns. The full **NSF SBIR Pitch Playbook** — the first launch in the playbook series — covers what the skill cannot:

- 12 register patterns reviewers consistently downgrade (with deeper explanation)
- The reviewer's mental model — what the panel actually scores and how
- The 4-section NSF SBIR Pitch storyline order, with notes on how it adapts to other agencies' formats
- 5 worked before/after examples across SBIR-relevant domains
- A 20-point pre-submission checklist
- A 60-minute reviewer mini-training video

Launch-week pricing for waitlist subscribers: **https://elleyuanwang.com/sbir-pitch**

---

## Contributing

Issues and PRs welcome. Spotted a pattern that should be flagged? Open an issue.

---

## License

**MIT** — use it, fork it, share it. See [LICENSE](./LICENSE).
