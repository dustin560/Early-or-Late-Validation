# Early or Late — Survey Handoff
*Last updated: 30 June 2026*

## 30 June 2026 — Six new Michelle Fine shirts added (M06–M11)

**Programme N°01 is now 16 artworks** (6 Conor + 10 Michelle). "Five get made" preserved — 5 × 50 = 250 pieces still holds. Edition numbers continue from N°016 to N°021 (the N°007–N°011 gap from Peter's removal is left intact; do not renumber).

New shirts, with **Claude-invented titles + descriptions** (Dustin to review against Michelle's preferences):

| Card | Title | Description |
|---|---|---|
| M·06 | Patron | "A crown made of yesterday's noise. The dog knows." |
| M·07 | The Whole Cast | "Everyone showed up. Nobody got top billing." |
| M·08 | Listening Face | "She heard you. She has thoughts." |
| M·09 | What Remains | "When the herd moves on, the shape stays." |
| M·10 | Half Done | "Caught between two thoughts. Neither finished." |
| M·11 | Saturday Eyes | "Sunglasses indoors. The right call." |

**JPEG files** are live in `renders/` (M06.jpg–M11.jpg). Dustin saved the originals as `.jpeg`; Claude retinted and re-saved as `.jpg` (the convention). Heavy lavender on M06/M07/M11 was successfully replaced with warm stone (RGB 234, 232, 227); M08/M09/M10 had pale grey/white backgrounds that the v3 threshold correctly skipped. Originals preserved in `renders/.bak/` (gitignored). **Orphan `.jpeg` files** in `renders/` (M06–M11.jpeg) — Dustin to delete via Finder before next push or they'll be committed alongside the .jpg.

Copy updated everywhere: "Ten artworks" → "Sixteen artworks" (3 places), "5 of 10" → "5 of 16", signup footer + intro both updated. Both clones synced.

## 25 June 2026 — Peter Rapp removed from the programme

**Decision:** Peter Rapp is out. Programme N°01 is now **two artists** (Conor Devlin-Powell + Michelle Fine) with **ten artworks total** — 6 Conor + 4 Michelle. "Five get made" still holds (5 of 10 chosen, 50 each, 250 total pieces).

Survey changes (live in `index.html`, synced to both clones):
- Entire `<!-- ===== PETER RAPP ===== -->` section removed from Q1.
- All copy updated: "Fifteen artworks" → "Ten artworks" (3 places); "three artists" → "two artists" (2 places); "Drop: 5 of 15" → "Drop: 5 of 10"; signup footer copy + hero strap line updated to two-artist naming.
- 10 shirt cards in Q1 (C01–C06 + M01, M02, M03, M05).

**Distribution Sheet docx** also updated: Peter's table row removed and his name dropped from the footer signature.

**Orphaned files (Dustin — please delete manually via Finder before next push):**
- `peter-images/` (entire folder)
- `renders/P01.jpg`, `renders/P02.jpg`, `renders/P03.jpg`, `renders/P04.jpg`, `renders/P05.jpg`
- (`renders/.bak/P*.jpg` already gitignored — leave or delete, no impact)

## 23 June 2026 — usability fixes from first test wave

- **Roman numerals re-aligned to question numbers.** Was: II=Q1 … XI=signup (entry gate implicitly I.). Now: I=Q1, II=Q2, … IX=Q9, **X=signup**. The user feedback "XI is 11 and it is on question 10" was the trigger — numerals now match the question number 1:1 and the small "I." meta tag on the hero (which caused the offset) was removed.
- **Q7 ad-reaction visibility on Android/Ecosia.** Root cause: forced auto-dark-mode rewriting the buttons to unreadable colours. Fixes applied:
  - Added `<meta name="color-scheme" content="light only">` + `<meta name="supported-color-schemes" content="light">` in `<head>`, plus `color-scheme: light only;` on `:root`. Tells the browser to render in light mode and don't auto-invert.
  - Hardened `.ad-reaction` CSS with **explicit hex** (`#F5F5F3` bg, `#0A0A0A` text) including `!important` on color/bg so a forced-dark stylesheet can't override them. Same on `.ad-reactions` container and `.selected` state.
  - Added `-webkit-appearance: none` to neutralise browser-native button styling on Chromium-on-Android.
  - **New mobile breakpoint** at `max-width: 520px`: the 3-column grid stacks vertically (1 column) with the icon inline next to the label. Stops cramped text on narrow phones.
- Both clones (`Early-or-Late-Validation/` and `early-or-late-deploy/`) synced. Push from whichever one GitHub Desktop has wired up.


> **⚠️ Two clones exist.** GitHub Desktop has historically pointed at a *different* clone of this repo (location unknown), which pushed the logo commits ("Logo update", "Logo fix"). THIS folder is the one Claude works in. To avoid divergence: in GitHub Desktop use **Add Existing Repository** → this folder, and retire the other clone.

## Quick context

Early or Late is a contemporary art curation house launching as wearable artworks — heavyweight 265gsm cotton tees with artist prints, milled in Leicester, designed in Hackney. **Programme 01** is the validation survey at `https://earlyorlatevalidation.netlify.app`, collecting buy intent and artist/garment preferences from ~100 respondents before the public launch.

## Repo & deploy

- **Local path**: `~/Documents/Claude/Projects/Unicorn/Early-or-Late-Validation/`
- **GitHub repo**: `Early-or-Late-Validation` (dustin560)
- **Deploy**: Netlify auto-deploy on push to `main`
- **Workflow**: Edit locally → GitHub Desktop commit → Push origin → Netlify deploys in ~30 seconds

## Two artists in Programme 01

**16 finished shirts total in Q1** (after Peter removal + Michelle expansion 30 June 2026):

- **Conor Devlin-Powell** — launch artist. **6 finished shirts in survey** (C01–C06). Source artwork files: 5 in `conor-images/` (c01–c05); the sixth shirt (C06) uses an additional piece rendered into `renders/C06.jpg`.
- **Michelle Fine** — equal partner in this drop. **10 finished shirts in survey** (M01, M02, M03, M05, M06–M11 — note M04 still not rendered). M06–M11 added + retinted to warm stone on 30 June 2026.

Totals: 6 + 10 = 16 finished-shirt cards in Q1. The site copy now says "sixteen artworks · five get made" (still 5 chosen × 50 each = 250 pieces).

Chris Sullivan was deferred during this session — handled separately due to scheduling.

## Survey structure (9 questions)

*Q1/Q2 redesigned 11 June 2026 (client decision, supersedes the earlier "interactive builder" lock):*

1. **Drop ranking** — Tap every **finished shirt** you'd choose (16 completed-shirt composites across 2 artists, multi-select).
2. **Shirt style** — Which shirt would you wear? Single-select: Black/White × Classic/Cropped, captured as `shirt_style_choice` (note: per-combo buy intent from the old builder no longer exists; buy intent is Q9 only)
3. **Promise ranking** — Top 3 of 8 brand promises
4. Retailers
5. Motivation
6. Proposition
7. Ad reactions
8. Price
9. Buy intent (general)

Plus an entry gate (age + gender) and a final signup form (email).

## Logo

Updated this session — wordmark is now **TT Hoves Pro** rendered as **inline SVG vector paths** (extracted from the AI source via `pdftocairo`). No font loading required. 8 instances throughout the page, all self-contained.

Shape reference (matches the source AI exactly):
- `early` — solid bold sans
- `or` — outlined sans
- `LA` — outlined sans uppercase
- `(t)` — outlined parens, outlined italic sans-serif `t`
- `E` — outlined sans uppercase

Standalone copy at `logo.svg` in the repo root. Inline structure adds ~12KB per use × **7 instances** (the earlier "8" was a miscount); file size is now ~254KB (was ~150KB). Acceptable trade-off for pixel-perfect rendering with no font dependency.

**Verified live 11 June 2026** — desktop and 390px mobile width both render the wordmark correctly (solid bold `early`, outlined `or`, outlined `LA(t)E`, italic `t` in parens).

## Recently completed (this session)

- ✅ Two-artist programme (Conor + Michelle — Peter Rapp removed 25 June 2026; Chris Sullivan deferred earlier)
- ✅ Q2 "Build your shirt" interactive builder
- ✅ 60 AI-generated mockup composites in `mockups/` (~31MB) — **placeholder**, pro designer will replace
- ✅ Mobile entry gate scroll fix (works on small screens)
- ✅ Logo replacement (TT Hoves Pro inline vector paths, pixel-perfect to AI source)
- ✅ Logo verified on live site, desktop + mobile (11 June 2026)
- ✅ Deleted `index.html.bak-prelogo` and `mockups-test/` (11 June 2026)
- ✅ Repo synced with origin; placeholder mockups committed locally (11 June 2026)
- ✅ Launch date copy updated everywhere: Jul/Aug 2026 → **Autumn 2026** (4 instances)
- ✅ Q7 ad mockups now dynamically pull the user's Q1 selections (`renders/{artId}.jpg`) into all 5 ad placeholders.
  - **Each of the 5 ads shows a different selection in rank order**, cycling if the respondent picked fewer than 5 (e.g. 2 picks → ads show 1,2,1,2,1).
  - **Ad background switched to bone** (was ink/black) — shirt renders read cleaner on the lighter ground.
  - **Each ad's headline + sub now relate to the respondent's Q3 promise ranking.** Top-ranked promise → Ad A, second → Ad B, etc., cycling. 7 promise→copy variants (one per brand promise). Skipping or unanswered Q3 → defaults to the original static ad copy. Hooks: `rankPromise()` and `skipQuestion('promise_ranking')`.
- ✅ Final copy & layout pass (11 June 2026):
  - "Two-fifty" → "**250**" (3 instances)
  - "UK cotton" → "**organic cotton**"
  - Removed the **Repaired for life** promise — now 7 promises in Q3 (renumbered N°01–N°07). Removed corresponding entry from `PROMISE_AD_COPY` JS.
  - Updated Q3 heading: "Eight things…" → "**Seven things that hold for every piece**"
  - Removed the **£148 price tag** from all 15 Q1 shirt cards (price is captured later in Q8)
  - Card backgrounds (`.shirt-placeholder`, `.ad-product`) changed from bone → **stone** (#D8D2C8) so white shirts have visible edges against the page
  - 10 of the 15 render JPEGs (C01, C02, C04, M02, M03, M05, P02–P05) had a baked-in **lavender** background that overrode the CSS card bg. Retinted to a warm neutral (RGB 234, 232, 227) matching the Abtu (P01) reference. Originals preserved in `renders/.bak/` (gitignored). Minor JPEG-edge speckles remain but are invisible at thumbnail size.
  - All remaining `July / July-August / Jul–Aug '26` date references converted to **Autumn 2026** / `Autumn '26`. Survey submission confirmation also reads "We'll see you in autumn."
  - **Backend verified end-to-end** — Netlify Forms hidden form is correctly named `early-or-late-survey` with all field declarations. JS POSTs to `/` with `application/x-www-form-urlencoded` and includes `form-name` field. Honeypot field present. The full survey state is captured in the `survey_data` JSON field for deep analysis.
  - **Attribution capture added.** URL params (`utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `from`) and `document.referrer` are captured on page load into `surveyData.attribution`, and submitted as their own fields (`utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `from_cohort`, `referrer`) in addition to the `survey_data` JSON. Use these for channel-level attribution in the Netlify Forms CSV.
  - **Open Graph + Twitter Card meta tags added** for social link previews. The image at `og-card.png` (1200×630) is served with each shared link — logo wordmark + tagline on bone background, clay accent rules. Distribution links work as simply `?from=<name>` from any channel and the preview card stays consistent.
  - **Unicorn attribution added** (per `unicornunited.co` brand):
    - Top nav: small "Created by [Unicorn mark + wordmark]" link under the place line, in the Unicorn violet→magenta gradient, opens unicornunited.co in a new tab.
    - Post-submission Unicorn panel: heavily-branded dark purple panel (`--night` to `--ink` gradient) appears below the "On the list" thank-you. Contains the Unicorn zigzag mark, gradient wordmark, "We help you build belief" tagline, brand body copy, and a "Visit unicornunited.co" gradient CTA. Uses Sora typeface (loaded in head).

**Correction:** there is no separate `artist-selection` Netlify form in the repo — only `early-or-late-survey`. The builder choice and all per-question answers are captured inside the `survey_data` JSON field of that form. (Earlier handoff claim was stale.)

## Pending / open items

- [x] **End-to-end test passed (11 June 2026)** — full run-through on the live site: entry gate, all 9 questions, exit form, submission. No console errors. Q1/Q2 verified at desktop + 390px mobile. One test submission in Netlify Forms from `dustin+e2etest@warpspeed.agency` — **ignore it in results**.
- [ ] **Replace AI mockups with pro designer's** — the 60 composites in `mockups/` are placeholders. **Decision (11 June): distribution waits for the pro renders.** When delivered, drop them in `mockups/` with the same filename pattern (`{artId}_{shirtId}.png`) — no code changes needed. Ask the designer for web-optimised files (current placeholders are ~500KB each; aim for ≤150KB or WebP).
- [ ] **Client will supply new artwork** for the redesigned survey — incorporate when shared (Dustin, 11 June voice note).
- ~~Drop in new Defatigable render~~ — N/A, Peter Rapp removed 25 June 2026.
- [ ] **Distribution** — blocked on pro renders per decision above. Everything else is ready.
- [ ] **Watch:** Promise B / Ad B still say "Designed by neurodivergent artists" — intentional (the exit gate tests ND framing), but flag against the May brand-board decision to lead with "independent artists" before any public-facing reuse.

## Files to know

| File / folder | What it is |
|---|---|
| `index.html` | Main survey (~254KB; large because logo SVG is inlined 8×) |
| `logo.svg` | Clean standalone wordmark, also extracted from AI source |
| `conor-images/` | 5 Conor Devlin-Powell artworks (PNG) |
| ~~`peter-images/`~~ | Removed from project 25 June 2026 — folder can be deleted from disk |
| `michelle-images/` | 5 Michelle Fine artworks (PNG, from her Instagram via desktop save) |
| `shirt-mockups/` | 4 blank shirt mockups (t01–t04: black/white × classic/cropped) |
| `mockups/` | **60 AI-generated artwork×shirt composites — PLACEHOLDER**, replace with pro designer's renders |
| `index_v1_backup.html` | Older backup, kept for reference |
| `index.html.bak-prelogo` | Pre-logo-update backup (gitignored, safe to delete) |
| `privacy.html` | Privacy policy page |
| `netlify.toml` | Netlify config |
| `.gitignore` | Excludes OS junk, editor configs, `*.bak*` |
| `README.md` | Brief repo intro |

## Voice / brand reminders

- Curation house register, Hackney coded — not pure streetwear, not stuffy gallery
- Bold Minimalism executed bravely (don't drift into institutional gallery quietness)
- Voice: dry humour, em-dashes, British English, mixed rhythm, concrete specifics
- Two-tone treatment in the brand colour system: bone, black, clay
- For wordmark, default to the inline SVG paths — never substitute fonts

## Decisions locked (this session, don't undo)

- 3 artists × 5 works = 15 in the survey (no Chris Sullivan)
- Conor leads the launch; Michelle framed as "could be next?" (Peter Rapp removed 25 June 2026)
- Q2 = interactive "Build your shirt" with single-select buy intent (yes / maybe / not for me) per combo
- Logo: TT Hoves Pro outlined treatment, no italic on `early`, outlined `or`, outlined italic sans-serif `t` inside outlined parens
- Programme N°01 framing throughout
- Mockup pipeline: pre-rendered composites (lookup via `mockups/{artId}_{shirtId}.png`), not live overlay

## Live URL & ops

- **Site**: https://earlyorlatevalidation.netlify.app
- **Form submissions**: Netlify dashboard → Forms → `artist-selection` (artist preview) and the survey form
- **Analytics**: Microsoft Clarity (consent-gated), tracking key `wqxnrfu5up`
- **Storage key for consent**: `eol_consent_v1`

## What to do next chat

The likely finalisation tasks in priority order:

1. Push pending commits via GitHub Desktop, verify the live site shows the new logo correctly on desktop + mobile
2. Decide on the AI mockups — either replace with pro designer's now or revert Q2 to the simpler 4-shirt picker until pro renders arrive
3. Run an end-to-end test, fix anything broken
4. Wider distribution — share the link with the target ~100 respondents

— Dustin · Unicorn United Ltd
