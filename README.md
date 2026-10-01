# Fragrance House Positioning Analysis: a Claude skill

A [Claude skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that builds a two-axis **positioning map** (perceptual map) of fragrance houses and backs every factual claim with a **verified, MLA 9 citation**.

It works for any set of perfume brands: heritage luxury maisons, designer houses, niche and indie perfumers, mass-market, direct-selling, celebrity and dupe brands.

## What it does

1. Scopes the competitor set, market and deliverable.
2. Chooses two axes that vary independently (e.g. distribution volume × prestige).
3. Places each house in a quadrant with evidence bullets and strategic implications.
4. Reads the map: competing strategies, outliers, white space and why it may be empty.
5. Lists the map's advantages and limitations.
6. Finds every claim that needs a source, opens and verifies each source, and adds MLA in-text citations and a Works Cited page.
7. Delivers a new write-up, or edits an existing Google Doc in place.

## Install

**Claude Code**
```bash
git clone https://github.com/<you>/fragrance-positioning-skill.git
cp -r fragrance-positioning-skill/fragrance-house-positioning ~/.claude/skills/
```

**Claude.ai**: zip the `fragrance-house-positioning` folder and upload it under Settings → Capabilities → Skills.

## Example prompts

- "Make a positioning map of Byredo, Diptyque, Dior, Zara and Maison Margiela Replica for my marketing class."
- "I'm advising an indie perfumer. Where's the white space against Le Labo and Jo Malone?"
- "Here's my positioning-map homework in Google Docs. Find what needs citations and add MLA in-text citations and a Works Cited page."

## Files

```
fragrance-house-positioning/
  SKILL.md                         workflow
  references/axes-library.md       candidate dimensions and how to pick a pair
  references/house-archetypes.md   typical positions of house types
  references/output-template.md    deliverable structure and a worked example
  references/citation-workflow.md  source hierarchy, verification, MLA 9 rules
  references/google-docs-editing.md  editing a Google Doc in place
```

## Notes

- The skill never invents citations. If it can't find or verify a source, it says so and asks.
- The worked example's sources were checked when it was written. Re-verify before reuse.
- This is not affiliated with any brand mentioned.

## License

MIT
