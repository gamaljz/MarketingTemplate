# Prompt 01 — Brand File (Marketing System, Layer 1)

Based on *How I Built an Automated Ad Machine With Claude Code* (James Devonport): "Layer 1: Your brand file … the single source of truth that the whole system references."

**How to run:** fill in `brand/SETTINGS.md`, then tell Claude Code: *"Follow prompts/01-brand-file.md."*

---

# Task: Build this company's brand file

## Inputs
- `brand/SETTINGS.md`: company name, website and extra sources. Read it first.
  If COMPANY_NAME or WEBSITE is blank, stop and ask me.
- `brand/brand.json`: the skeleton you fill in.
- `brand/inbox/`: raw material I've dropped in (brand guide, logos, past ads).
  Read it, but don't edit it.

## Git
- Work on the branch `brand-setup`. Create it from `main` if it doesn't exist,
  or switch to it if it does. If this session has already been assigned a
  working branch (Claude Code on the web does this), use that branch instead.
  The name doesn't matter; what matters is that the work isn't done on `main`.
- Don't merge to `main`. That happens after Prompt 02, through a pull request I review.

## Why this file exists
This repo is the marketing system for one company. This is step 1: the **brand
file**. It is a single file that holds everything about the brand: colours,
fonts, name, logos, key messages, products, target audiences and ad formats.
Every later layer reads from it and must never hard-code brand details.
Later layers include a creative matrix (topic × persona × style), AI image
generation, a Meta ads upload pipeline and performance reports.
If the brand file is right, every ad comes out on-brand. The more specific it is,
the better the output.

Scope: **only the brand file.** Do not build the creative matrix, the image
generator, a Node project, or any API integration yet. Brand voice and writing
preferences go in `CLAUDE.md` (Prompt 02), not here.

## Files you produce
```
brand/
  brand.json        # THE brand file (fill in the skeleton)
  SOURCES.md        # where each fact came from (URL, skill, file, or "owner, <date>")
  assets/logos/     # logo files you can download; I'll supply the rest
  assets/fonts/     # only if the licence allows
  assets/photos/    # approved hero / product imagery
```

## Rules for brand.json
- **Keep the skeleton's shape exactly.** Don't add, remove or rename keys
  without asking me. Every company's repo uses the same shape, so later scripts
  work for all of them.
- Every field holds a real value, or a string that starts with `"TODO:"`
  explaining what's missing.
- Lists (`products`, `sellingPoints`, `audiences`, `logos`) can have as many
  entries as needed. Every entry keeps the same keys.
- What the fields mean:
  - `identity.oneLiner`: what we are, for whom, in one sentence.
  - `colors.*.use`: where the colour is used (e.g. "buttons and links").
  - `typography.*.source`: Google Fonts, Adobe Fonts, or a licensed file.
  - `logos[].variant`: `primary`, `light-on-dark`, `dark-on-light` or `mark`.
  - `products[].priceNote`: only with an "as of" date; otherwise leave it out.
  - `sellingPoints[].proof`: the verifiable fact that backs the point up.
  - `audiences[]`: who they are, what they want, their objections, and the
    hook most likely to work on them.
  - `imageRules`: instructions for AI image generation, e.g. always "brand
    colours prominent", never "text baked into the image" or "stock-looking people".
  - `doNotClaim`: things we must never say or imply, e.g. unverified
    "best / only / first" claims.
  - `adFormats` and `copyLimits`: pre-filled. Change them only if I ask.

## Process
1. **Gather first, ask second.** Don't ask me anything you can find yourself.
   - Read the website: home, about, every product/accommodation/service page,
     FAQ and booking or contact. Pull the name, tagline, products, selling
     points, proof, CTAs and booking URL.
   - Colours and fonts: take exact values from the site's CSS or Webflow
     variables, or from the Canva brand kit. Don't guess hex codes from
     screenshots. If you have to estimate, mark it `TODO: estimated, confirm`.
   - Read the extra sources in `SETTINGS.md` and everything in `brand/inbox/`.
   - Download logos you can find on the site into `brand/assets/logos/`.
2. **Draft** `brand.json`. Never invent statistics, ratings, awards, prices,
   capacities or "best/only/first" claims.
3. **List conflicts.** If two sources disagree, list them side by side. Don't
   pick one silently.
4. **Interview me** about the gaps, the conflicts and the judgement calls: which
   selling points matter most, the 3–5 audiences to target, the image rules, and
   anything we must never claim. Ask at most 10 questions per round. Where you
   can, propose options so I can choose ("A / B / C / other"). For audiences,
   propose personas based on what you found and let me edit them. Wait for my
   answers.
5. **Finalise** `brand.json` and write `SOURCES.md`.
6. **Verify** before you tell me it's done:
   - the JSON parses (run it through `node -e` or `python3 -m json.tool`)
   - the key structure still matches the original skeleton
   - every hex is a valid 6-digit colour
   - every `file` path exists, or is listed as something I still need to supply
   - every product, selling point and proof item has a source in `SOURCES.md`
   - list any `TODO:` still left, and whether I chose to defer it
7. **Report** in under 15 lines: a summary of the brand, the TODOs still open,
   and the asset files I need to drop in (logo SVG/PNG in light and dark
   versions, font files if licensed, approved photos).
8. **Commit and push** to `brand-setup` with the message `brand: add brand file`.

## Ground rules
- One source of truth. If a fact lives in `brand.json`, nothing else should
  restate it differently.
- Facts must be verifiable. Prices and offers change, so include them only with
  an "as of" date.
- No secrets in this repo (API keys, tokens, passwords).
- Keep it machine-friendly: plain strings and arrays, not prose essays.
