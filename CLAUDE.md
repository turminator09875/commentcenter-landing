# CommentCenter — Landing page

Static marketing site for `commentcenter.nl`. Single `index.html`, served via `npx serve` (or Vercel static deploy).

**Sister repo:** `/Users/karaca/Downloads/fb-comment-tool/` (Next.js app at `app.commentcenter.nl`)

---

## Design DNA — Mobbin Clean v3 (light mode)

- **Canvas:** `#FFFFFF` everywhere. Hairline elevation (`inset 0 0 0 1px var(--line)`), no heavy borders.
- **Brand:** `#3b82f6` — used sparingly. Per Kral's hard rule: **brand-blue CTA only on hero + final CTA** (and mobile menu = hero). Pricing CTA stays ink-100. Top-right nav CTA stays ink-100 (chrome restraint).
- **Type:** DM Sans 700 for headlines (with `<em>` styled as brand-blue weight 700, NOT italic). JetBrains Mono for numerics/eyebrows.
- **No emojis** in UI — use SVG or stylized text.
- **No Instrument Serif** — removed entirely.
- **Tokens** in `:root` at top of `index.html` (`--canvas`, `--tx-1..4`, `--brand`, `--line*`, `--elev-*`).

## Section structure (AIDA flow — don't reorder)

1. `#hero` — H1 "Je beste leads zitten in je *comments*"
2. `#probleem` — pain agitation
3. `#hoe` — 3-step flow
4. `#kernfunctie` — AI reads intent
5. `#features` — 6 feature cards (NOT 5 — 5-card grid is forbidden by Kral, produces orphan)
6. `#differentiator` — vs other tools
7. `#voorwie` — 3 personas
8. `#bewijs` — proof section (4 verifiable stat cards + stack credibility line). **No fake testimonials** — placeholder HTML comment for when first 3 paying customers consent.
9. `#pricing` — 3 tiers with monthly/yearly toggle
10. `#faq` — accordion
11. `#cta` — final crescendo (brand-blue button with heavier glow than hero)

## Voice

- Dutch, informal `je/jij`.
- No generic SaaS jargon (no "streamline", "optimize", "innovative").
- Operator language: CPL, ROAS, leads, conversie, hot leads.
- CTAs: action + outcome ("Scan gratis je eerste post" not "Begin nu").
- Headlines: one strong idea, brand-em on the strongest noun.

## Hard rules — invoke before any design work

**`commentcenter-qa` skill is mandatory** before writing a brief or shipping a design change. Anti-patterns to never repeat:
- 5-card grid (always orphans — use 6 cards or vertical list)
- Blue accent on every section heading (kills impact — hero + final CTA only)
- Horizontal-scroll table on mobile (convert to stacked cards)
- Large colored side borders for categories (badge pills only)
- "Verberg 0 spam" / dead UI (hide when count=0)

## Footer links

- Privacy + Terms link to `https://app.commentcenter.nl/privacy` and `/terms` (cross-domain, app pages on Next.js subdomain). NOT relative paths — would 404 on landing root.

## Current state (last session: 2026-04-25)

P0 trio shipped:
- **#bewijs section** added between #voorwie and #pricing (4 proof-cards + stack line)
- Footer privacy/terms switched to absolute app URLs
- `--tx-4` darkened from `#A3A3A3` to `#8A8A8A` (WCAG AA pass)
- Hero CTA + mobile menu CTA already brand-blue (Kral standard)

Last commit: `7c5c19c`. Branch: `main`. Pushed.

## Next: P1-batch (landing items)

1. **P1-5** Demo-GIF/video onder hero of na `#hoe` (15s product walkthrough)
2. **P1-6** FAQ uitbreiden met 4 vragen: pricing/billing, opzeggen, data-locatie, setup-tijd
3. **P1-7** Hero trust-line social proof element (instead of just "Geen creditcard")
4. **P1-8** OG:image 1200×630 (currently missing for social shares)
5. **P1-16** Core Web Vitals run + fixes (preconnect Google Fonts, defer demo JS, lazy-load below-fold)
6. **P1-17** Pricing audit: jaarlijkse korting + decoy/anchoring check

## Workflow

- **Preview:** `mcp__Claude_Preview__preview_*` tools. Server name `landing` (port 3456) in `.claude/launch.json`.
- **Mobile QA at:** 390, 430, 768, 1280, 1440. No horizontal overflow allowed.
- **Commit format:** `<type>(<scope>): <imperative>` — types: `design`, `copy`, `fix`, `seo`, `polish`.
