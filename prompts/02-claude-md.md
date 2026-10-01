# Prompt 02 — CLAUDE.md (the brand's permanent memory)

Based on *The Marketer's Guide to Claude Code* (Robert Gillespie), step 5: "Set up your CLAUDE.md file. This is your brand's permanent memory … brand voice, target audience, terminology, products, and preferences. Claude reads it at the start of every session."

**How to run:** after Prompt 01, tell Claude Code: *"Follow prompts/02-claude-md.md."*

---

# Task: Write this company's CLAUDE.md, the brand's permanent memory

## Inputs
- `brand/SETTINGS.md`: company name, website and extra sources.
- `brand/brand.json` from Prompt 01. If it's still the empty skeleton, stop
  and tell me to run Prompt 01 first.
- `brand/inbox/` and the extra sources listed in `SETTINGS.md`.

## Git
- Stay on the same branch Prompt 01 used (`brand-setup` or this session's
  assigned branch).
- When you finish, open a pull request from that branch into `main` for me to
  review. Don't merge it yourself.

## Why this file exists
Claude Code reads the `CLAUDE.md` at the repo root automatically at the start of
every session. It's what keeps every output on-brand without me re-explaining
the business each time. "95% of bad AI output is a context problem, not a model
problem." This file solves that.

It holds the **soft** side of the brand: voice, audience, terminology, products
(summarised) and my preferences. The **hard** facts and visual identity live in
`brand/brand.json`. That file wins on facts. Point to it; don't copy it.

## What to write: replace the root `CLAUDE.md` entirely
The current `CLAUDE.md` is a "not set up yet" placeholder. Replace all of it.
Aim for 80–150 lines. Every line should change what Claude writes; cut anything
that doesn't. Use these sections:

0. **Header.** One line saying this repo is the marketing system for
   <company>. Then: "Facts, colours, fonts, products, audiences and ad formats:
   `brand/brand.json` (source of truth; read it before any marketing task)."
1. **Who we are.** Three lines: what we are, for whom, and why we're different.
2. **Voice.**
   - 3–5 traits, each written as "We are X, not Y", with a one-line example in
     our voice.
   - Sentence-level rules: person (we/you), sentence length, contractions,
     exclamation marks, emoji, heading case, US or UK spelling, numbers and units.
3. **Audience.** One short paragraph per persona. Names must match the
   `audiences` in `brand.json`. Cover what they care about, what makes them book
   or buy, and what puts them off.
4. **Terminology.** A Use / Avoid table: what we call our products, places,
   experiences and customers, plus proper nouns spelled and capitalised correctly.
5. **Products.** Name, one line and a link. Then: "Details, prices, proof:
   `brand/brand.json`."
6. **Preferences.** Default formats and lengths per channel (Instagram caption,
   Meta ad, email, web section), approved CTA wording, how to handle prices and
   dates, and what I always want or never want.
7. **Never say or claim.** Mirrors `brand.json → doNotClaim`, plus the voice
   no-gos (banned words, clichés, competitor mentions).
8. **On-brand vs off-brand.** One short paragraph in our voice and one that
   misses it, with a line on why.
9. **Keeping this file current.** One line: when I correct an output on voice or
   facts, propose the exact one-line edit to this file or to `brand.json`.

## Process
1. **Gather.** Read `brand.json`, the website copy and the extra sources. Infer
   the voice from real copy, not from adjectives. Ask me for 3–5 pieces I'm proud
   of (emails, ads, posts) and 1–2 I dislike, and learn from both.
2. **Draft** the file. Mark anything you inferred but couldn't confirm with
   `(confirm)`.
3. **Interview me** about the gaps and judgement calls: banned words, emoji,
   tone per channel, terms we avoid, how formal to be. Ask at most 8 questions
   per round, with options where you can. Wait for my answers.
4. **Blind test.** Spawn a subagent that has only `CLAUDE.md` and
   `brand/brand.json` as context. Have it write: an Instagram caption, a Meta ad
   (primary text, headline, description, within the `copyLimits`), and an
   80-word email opener. Show me the three pieces, ask me to rate each 1–5 and
   say what's off, then fold the fixes into `CLAUDE.md`. Repeat once if any
   piece scores under 4.
5. **Check before finishing:**
   - persona names and product names match `brand.json` exactly
   - nothing contradicts `brand.json` or the brand skill named in `SETTINGS.md`
     (if there's a conflict, ask me)
   - no secrets, prices without dates or unverified claims
   - the file is 150 lines or less, and none of the placeholder text is left
6. **Commit and push** with the message `brand: add CLAUDE.md memory`, then open
   the pull request into `main`. Use the title `Brand setup: brand file +
   CLAUDE.md` and a short summary of what's in each file and any TODOs left.

## Ground rules
- Point, don't duplicate. Facts belong in `brand.json`; CLAUDE.md says how we
  talk about them.
- Write it as instructions to Claude, short and direct, not as a brand essay.
- It's a living file. It should get better every time I correct an output.
