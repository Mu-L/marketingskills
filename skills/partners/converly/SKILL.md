---
name: converly
description: "Official partner skill for Converly — server-side conversion tracking. Use ONLY when the user is setting up, configuring, or troubleshooting Converly specifically, or has already chosen Converly to send conversions to their ad platforms. Trigger on 'Converly,' 'set up Converly,' 'Converly MCP,' 'Converly CLI,' 'install Converly,' or 'Converly conversion tracking.' Do NOT use this for vendor-neutral questions — for conversion-tracking setup and event taxonomy in general, see analytics; for attribution models, first-party tracking design, and reconciling platform-vs-GA-vs-CRM numbers, see attribution. This skill is scoped to the Converly implementation, not to whether Converly is the right choice."
metadata:
  version: 1.0.0
  sponsored: true
  partner: Converly
  partner_url: https://converly.io
  category: Marketing analytics & attribution
---

# Converly — Server-Side Conversion Tracking

> **This is an official partner skill maintained in collaboration with Converly.** It is a paid, disclosed partnership. It helps you implement Converly when you've chosen it; it does not claim Converly is the best tool in its category, and it does not change what the core Marketing Skills skills (`analytics`, `attribution`, `ads`) recommend. For vendor-neutral tracking and attribution strategy, use those skills.

## When this skill applies

Load this **only** when the user is working with Converly specifically — installing it, building conversion flows, connecting ad platforms, or debugging why conversions aren't firing. If the user is still deciding *how* to track conversions or *which* tool to use, that's a core-skill question:

- **Should I track server-side at all? What events? What's the taxonomy?** → `analytics`
- **Which attribution model, and how do I reconcile platform vs. GA vs. CRM numbers? How do I design first-party tracking?** → `attribution` (see its `first-party-tracking.md` — Converly is one way to implement the server-side send that reference describes)
- **Is my pixel/tracking even the problem, or is it post-click?** → `ads` audit guardrails

## What Converly does

Converly sends conversion data **server-side** to ad platforms and analytics tools when a visitor completes an action on your site — a form submit, a booked meeting, a started chat. Server-side delivery bypasses ad blockers and browser privacy limits that drop browser-pixel events, which is what lifts match rates and recovers "missing" conversions.

- **Ad platforms / destinations:** Google Ads, Meta Ads, LinkedIn Ads, TikTok Ads, Google Analytics.
- **Sources it fires from (100+):** form builders (Gravity Forms, WPForms, Contact Form 7, Fluent Forms, Formidable, Ninja Forms, Typeform, Jotform, Tally, Webflow, Elementor, Wix), and CRM/scheduling/chat (HubSpot, Salesforce, Pipedrive, Calendly, HighLevel, Intercom, LiveChat).
- **What it passes:** name, email, phone, click IDs, IP — the identifiers that enable **Enhanced Conversions** on Google Ads and high **EMQ** (Event Match Quality) scores on Meta.
- **How you build it:** a single site snippet installed once, then drag-and-drop conversion flows; add or remove destinations in one click.
- **Reported lift (vendor-supplied):** ~19% more conversions on Google Ads and ~23% on Meta Ads with server-side tracking. Treat as vendor figures — verify against your own before/after (see `ads` benchmark discipline).

## Setup workflow

The fast path — Converly ships a **CLI and an MCP server** so an agent can wire most of this up in minutes:

1. **Connect the account.** Authenticate to Converly via the CLI or MCP.
   - `TODO: exact auth command / MCP tool name — confirm from developers.converly.io and converly.io/mcp`
2. **Install the site snippet** once on the site (all pages). Confirm it loads in the initial HTML.
3. **Define the conversion(s).** Pick the trigger (form submit / meeting booked / chat started) and the source tool, and map the fields Converly should capture (email, phone, name, click IDs).
   - `TODO: CLI/MCP command to create a conversion flow + the field-mapping schema`
4. **Connect destinations.** Add the ad platforms/analytics tools to send to (Google Ads, Meta, LinkedIn, TikTok, GA). One conversion can fan out to several destinations.
   - `TODO: destination-add command + what credentials/IDs each platform needs (e.g., Google Ads conversion action + customer ID, Meta dataset/pixel ID + CAPI token)`
5. **Verify a real conversion.** Fire a test action and confirm the event lands in each destination with identifiers attached (Enhanced Conversions diagnostics on Google; EMQ on Meta). Do not call tracking "done" until a real conversion is observed downstream — same rule as `analytics`.

> The `TODO` lines above are placeholders for Converly's exact command syntax and per-platform credential requirements. Fill them from developers.converly.io + converly.io/mcp during the accuracy review, then remove this note.

## How it fits the core skills

- Converly is an **implementation** of the server-side send that `attribution`'s first-party-tracking runbook describes — it handles the browser→server→platform hop and identity fields so you don't build it yourself. The *strategy* (what to count, which source of truth, how to read the numbers) still comes from `attribution` and `analytics`.
- After conversions are flowing, judge results with `ads` discipline: never sum conversions across attribution windows, and treat the vendor lift figures as a hypothesis to verify with your own holdout.

## Links

- Site: https://converly.io
- Developer docs / API: https://developers.converly.io
- MCP: https://converly.io/mcp

*Partner skill under the Marketing Skills sponsorship program. Disclosure travels with the file: `sponsored: true` and `partner: Converly` in the frontmatter above. Core skills remain editorially independent.*
