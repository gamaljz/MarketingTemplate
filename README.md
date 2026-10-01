# Marketing System Template

Starter repo for one company's marketing system. Make one repo per company from this template (e.g. `KosmosMarketing`).

## What's inside
```
CLAUDE.md               ← placeholder; Prompt 02 turns it into the brand memory
brand/
  SETTINGS.md           ← fill in first: company, website, sources
  brand.json            ← empty skeleton; Prompt 01 fills it
  assets/  inbox/       ← logos/fonts/photos; raw material you drop in
prompts/
  01-brand-file.md      ← builds brand/brand.json
  02-claude-md.md       ← builds CLAUDE.md, opens the PR
```

**How the two files fit together:** `brand/brand.json` is the single source of truth for facts and visuals, and later scripts (creative matrix, image generation, Meta upload) read it. `CLAUDE.md` is the memory Claude reads every session. It covers how we talk, and it points back to `brand.json` for the facts.

## Setting up a new company
1. On GitHub, open this template repo and click **Use this template → Create a new repository**. Name it `<Company>Marketing`.
2. Fill in `brand/SETTINGS.md` on `main`.
3. Put logos (SVG/PNG, light and dark versions) and any brand guide in `brand/inbox/`. Have 3–5 pieces of copy you like and 1–2 you dislike ready.
4. In Claude Code, say *"Follow prompts/01-brand-file.md"*, then *"Follow prompts/02-claude-md.md"*. Both run on a temporary branch (`brand-setup`, or the branch Claude Code on the web assigns).
5. Review the pull request Prompt 02 opens, merge it into `main`, and delete the branch.

From then on, every piece of work starts from `main` and inherits the brand. Use branches for in-progress work only; anything permanent lives on `main`.

## Kosmos values for `brand/SETTINGS.md`
```
- COMPANY_NAME: Kosmos Stargazing Resort & Spa
- WEBSITE: https://kosmosresort.com
- Claude skill with brand/content rules: kosmos-content-system
- Webflow site: kosmosresort.com (if the Webflow connector is available)
- Canva brand kit: Kosmos (if the Canva connector is available)
- Email / ad history: Mailchimp, Gmail, Meta (if connected)
```

## Changing the template
If you change `brand/brand.json`'s shape or improve a prompt, do it here first, so every new company gets the change. Then copy it into the existing company repos.
