# Partner Skills

This directory holds **partner skills** — skills for specific tools whose makers fund the Marketing Skills library through the [sponsorship program](https://marketing-skills.com/sponsorship). They are a separate class from the core skills in `skills/`, with stricter rules.

## The rules (non-negotiable)

1. **Disclosure travels with the file.** Every partner skill carries `sponsored: true` and `partner: <Name>` in its frontmatter, plus a plain disclosure sentence at the top of the body: *"This is an official partner skill maintained in collaboration with [Tool]."* Skills get forked and re-indexed across the ecosystem — file-level disclosure survives that.
2. **Sponsorship funds the work, not the recommendations.** A partner skill never changes what a core skill says or recommends. If a core skill names a competitor because it's the right answer, payment doesn't touch it.
3. **Scoped triggering.** A partner skill activates only when the user is working with or asking about that specific tool. It must defer vendor-neutral questions ("how should I track conversions?", "which tool?") to the relevant core skill. It never hijacks generic queries.
4. **Editorial control stays with the maintainer.** Partner skills are drafted collaboratively but Corey Haines holds final editorial control, including the right to edit for accuracy at any time.
5. **The badge means:** paid, disclosed, vetted-for-fit — *not* "best in category."

## Not counted as core skills

Partner skills are **not** included in the "N marketing skills" count, the auto-generated core skills table in the root `README.md`, or the core-skill versioning scheme. They're listed in the root README's **Partners** section instead.

## Current partners

| Partner | Category | Skill |
|---|---|---|
| [Converly](https://converly.io) | Marketing analytics & attribution | [converly](converly/) — server-side conversion tracking |

## House tools

Tools built by the maintainer (e.g. Truelist, email verification) follow the same disclosure rules with an **extra** note in frontmatter that the repo author owns the tool — over-disclosing the self-dealing rather than hiding it.
