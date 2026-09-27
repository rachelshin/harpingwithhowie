# Handoff: Harping with Howie — Website Redesign

## Overview
A one-page website for **Harping with Howie**, a podcast in which participants in the award-winning Howie the Harp Peer Support Specialist Training program (New York City) share their experience, strength and hope. The site has two goals: get people to press play, and give funders a clear path to support the show.

Look and feel: 90s after-school special crossed with a minimal "blue album" cover. It uses one flat color per section, plain readable type, a lot of empty space, and Pepper Auerbach's cover art as the only image. **It must be easy to read for older listeners: no text smaller than 20px anywhere.**

## About the Design Files
`Harping with Howie Site.dc.html` is a **design reference built in HTML**. It shows the intended look and behavior; it is not production code to copy. It uses an in-house component runtime (`support.js`, template holes such as `{{ hosts }}`, `<sc-for>`/`<sc-if>`, and inline `style-hover` attributes) that won't exist in the real site.

**Target:** the existing repo `harpingwithhowiesite/` is a static site (`index.html` + `assets/` + `netlify.toml`) with no build step. Keep it that way. Rewrite `index.html` as plain HTML with a `<style>` block (use CSS classes, custom properties and media queries) and a small vanilla-JS `<script>`. Do not add a framework. Replace the current `index.html` completely. None of its VHS overlay, intro card, tapes, TV channels, "classified" file or "The End" sections carry over.

To view the reference, open `Harping with Howie Site.dc.html` in a browser with `support.js` next to it and `assets/cover.jpg` at `assets/cover.jpg`.

## Fidelity
**High fidelity.** Colors, type, spacing, copy and interactions are final. Recreate it pixel for pixel. The only placeholders are host bios and portraits, and the two Support links (see Open items).

## Global Layout
- Page background `#B9E4F4`. Text `#151515`.
- Every section spans the full width, with its own background, and is separated from the next by `border-top: 2px solid #151515`.
- Inner container: `max-width: 1200px; margin: 0 auto; padding-inline: clamp(20px, 4vw, 56px)`.
- Section vertical padding: `clamp(64px, 10vw, 100px)` top and bottom (except the hero and footer, below).
- `html { scroll-behavior: smooth }`.
- The page must never scroll horizontally, from 320px wide upward.

## Sections (top to bottom)

### 1. Nav (sticky header)
- `position: sticky; top: 0; z-index: 10; background: #B9E4F4; border-bottom: 2px solid #151515`.
- Row: `display: flex; flex-wrap: nowrap; justify-content: space-between; align-items: center; gap: 12px`. Vertical padding `clamp(14px, 2.5vw, 20px)`.
- Type: Young Serif 400, `clamp(20px, 2vw, 21px)`, line-height 1. Letter-spacing `.045em` and word-spacing `.08em`, except below 640px, where letter-spacing is `0`.
- Left: "harping with howie" (links to `#top`, `white-space: nowrap`, no underline).
- Right (`gap: 32px`):
  - "about" → `#about`, "hosts" → `#hosts`, "support" → `#support`. **These three are hidden below 720px.** Hover: underline, `text-underline-offset: 6px`.
  - "listen" pill → `#listen`: background `#151515`, text `#B9E4F4`, `border-radius: 999px`, padding `12px 22px` (`10px 16px` below 640px), `white-space: nowrap`. Hover: background `#333`.
- On a 375px phone the nav must stay **one row, about 64–70px tall**.

### 2. Hero (`#top`)
Background `#B9E4F4`. Content is a centered column, `text-align: center`, gap `clamp(24px, 4vw, 34px)`, padding `clamp(32px, 6vw, 56px)` top and `clamp(48px, 7vw, 70px)` bottom.
1. **H1 "An After-School Special"** (use a non-breaking hyphen, U+2011, so "After-School" never splits): Shrikhand 400, `clamp(38px, 9vw, 64px)`, line-height 1.05, color `#FFF6D8`, `-webkit-text-stroke: 3px #151515; paint-order: stroke fill; text-shadow: 4px 4px 0 #151515; text-wrap: balance`.
2. **Cover art** `assets/cover.jpg` (1205×1272): a wrapper `width: min(476px, 100%); aspect-ratio: 476/528; overflow: hidden; border: 2px solid #151515`, and inside it the img at `width/height 100%; object-fit: cover; object-position: 20% 50%`. The full height must show, including the hand-lettered "with" banner at the bottom. Alt text: "Harping with Howie cover art by Pepper Auerbach: a yellow face with glasses, a wild blue beard and a red cap, with a hand reaching down from the sky".
3. **"for grown-ups"** (non-breaking hyphen): Gochi Hand 400, `clamp(44px, 12vw, 60px)`, line-height 1.1, `display: inline-block; padding: 0 6px`. **Write-on animation** (see Interactions).
4. **Description** "A podcast about the peer support specialists of New York City." Young Serif 22px/1.6, letter-spacing `.045em`, word-spacing `.08em`, `max-width: 600px`, `text-wrap: pretty`. Gap between items 3 and 4: 14px.
5. **Play button** "▶ Play" → `#listen`: background `#151515`, text `#B9E4F4`, padding `18px 34px`, radius 999px, Young Serif 21px, letter-spacing `.045em`. Hover: background `#333`.

**Latest strip** (still inside the hero, below the column): `border-top: 2px solid #151515`. The inner row is `display: flex; flex-wrap: wrap; justify-content: space-between; gap: 12px 30px`, padding `clamp(16px, 3vw, 22px)` vertical, Young Serif 20px/1.35, letter-spacing `.045em`.
- Left: "Latest: Ep. 06 · ACAB!!! BMDIC, with Raff"
- Right: link "All episodes" → `#listen`, underlined, `text-underline-offset: 5px`.

### 3. About (`#about`)
Background `#F7F2EA`. Two columns: `display: grid; grid-template-columns: repeat(auto-fit, minmax(min(100%, 420px), 1fr)); gap: clamp(24px, 4vw, 48px) 80px`. They stack on narrow screens.
- Left column (flex column, gap 18px):
  - Eyebrow "about the show": Gochi Hand `clamp(28px, 4vw, 34px)`, line-height 1.
  - H2 "What is peer support?": Shrikhand `clamp(38px, 6vw, 58px)`, line-height 1.05, **fill `#B9E4F4`**, 3px `#151515` stroke, 4px 4px 0 `#151515` shadow (same treatment as the H1), `text-wrap: balance`.
- Right column: paragraphs in Young Serif 22px/1.6, letter-spacing `.045em`, word-spacing `.08em`, gap 22px:
  1. "One of the best-kept secrets in mental healthcare."
  2. "It's help from someone who's been there. Peer specialists use their own lived experience of mental health challenges and recovery to walk alongside the people they support. Not above them. Next to them."
  3. "On Harping with Howie, participants in the award-winning Howie the Harp Peer Support Specialist Training program share their experience, strength and hope: what worked, what didn't, and what they learned along the way."

### 4. Hosts (`#hosts`)
Background `#B9E4F4`. Flex column, gap 48px.
- Eyebrow "starring". H2 "Your hosts", with the same H2 treatment but **fill `#F2C94C`**.
- Grid: `repeat(3, minmax(0, 1fr))` at 720px and wider; a single column (three stacked full-width squares) below 720px. Gap `clamp(24px, 4vw, 40px)`.
- Each **host card is a `<button>`** with the accessible label "More about {name}". It is a flex column, gap 18px. Hover: `transform: translate(-3px, -3px)`.
  - Portrait: `width: 100%; aspect-ratio: 1/1; border: 2px solid #151515; background: #F7F2EA; box-shadow: 4px 4px 0 #151515`. For now it shows centered initials in Gochi Hand 72px. **Replace with host photos** (`object-fit: cover`) when they arrive.
  - Below it, a row (`justify-content: space-between; align-items: baseline`) with the name (Young Serif 28px/1.2, letter-spacing `.03em`) and "more +" (Gochi Hand 26px, nowrap).
- Hosts: Anna Butler (AB), John F. O'Donnell (JO), Ben Roberts (BR).

### 5. Host pop-up (modal)
Opens when a host card is clicked or tapped.
- Overlay: `position: fixed; inset: 0; z-index: 50; background: rgba(21,21,21,.6)`, with the panel centered and 20px padding.
- Panel: `role="dialog" aria-modal="true"`, `width: min(100%, 620px); max-height: calc(100vh - 40px); overflow: auto; background: #F7F2EA; border: 2px solid #151515; box-shadow: 8px 8px 0 #151515`.
- Close button, top-right (14px inset): 48×48 circle, background `#151515`, a `#F7F2EA` "×" in Young Serif 28px, `aria-label="Close"`.
- Portrait area: `aspect-ratio: 16/10; background: #B9E4F4; border-bottom: 2px solid #151515`. Initials in Gochi Hand 96px for now; replace with the photo.
- Body: padding `clamp(24px, 5vw, 40px)`, gap 16px:
  - Name: Shrikhand `clamp(30px, 5vw, 38px)`, line-height 1.15, no stroke.
  - Role: "Host and participant, Howie the Harp Peer Support Specialist Training" in Young Serif 20px/1.45.
  - Bio: Young Serif 22px/1.6, letter-spacing `.045em`. **Placeholder.** The real copy is still to come.
- Close it with the × button, a click on the overlay (clicks inside the panel must not close it), or the Esc key. When it opens, move focus to the close button. When it closes, return focus to the card. Trap Tab inside the dialog. Lock body scroll while it's open.

### 6. Support (`#support`)
Background `#F2C94C`. The same two-column grid as About, `align-items: start`.
- Eyebrow "for funders and friends". H2 "Support the show", with the H2 treatment and fill `#FFF6D8`.
- Paragraph (22px body style): "Harping with Howie is made by people training to become peer specialists, for anyone who's wondered whether things can get better. Your support pays for recording, editing and getting these stories to the people who need them."
- Buttons in a grid, `repeat(auto-fit, minmax(min(100%, 220px), max-content))`, gap 14px, centered text. They are full width on phones.
  - "Become a funder": background `#151515`, text `#F2C94C`, padding `18px 30px`, radius 999px, Young Serif 21px. Hover: background `#333`.
  - "Get in touch": 2px `#151515` border, padding `16px 30px`, same type. Hover: background `#151515`, text `#F2C94C`.

### 7. Tune in (`#listen`)
Background `#F7F2EA`. A centered column, gap 36px.
- Eyebrow "wherever you get your podcasts". H2 "Tune in", with fill `#FFF6D8`.
- Buttons in a grid, `repeat(auto-fit, minmax(min(100%, 220px), 1fr))`, `width: min(100%, 780px)`, gap 14px. Each button: background `#151515`, text `#B9E4F4`, padding `18px 30px`, radius 999px, Young Serif 21px, `target="_blank" rel="noopener"`. Hover: background `#333`.
  - Apple Podcasts → `https://podcasts.apple.com/us/search?term=Harping%20with%20Howie`
  - Spotify → `https://open.spotify.com/search/Harping%20with%20Howie`
  - YouTube → `https://www.youtube.com/results?search_query=Harping+with+Howie`
  - (Swap in the real show URLs if they're known.)

### 8. Footer
Background `#151515`, text `#F7F2EA`. Padding `clamp(48px, 8vw, 72px)` top and `clamp(40px, 6vw, 60px)` bottom. Grid `repeat(auto-fit, minmax(min(100%, 260px), 1fr))`, gap 30px. Young Serif 20px/1.5.
Three credit blocks. Each has a Gochi Hand 26px `#B9E4F4` label, then the text:
- "a production of": Participants in the Howie the Harp Peer Support Specialist Training program, New York City
- "hosted by": Anna Butler, John F. O'Donnell & Ben Roberts
- "cover art by": Pepper Auerbach, [@iwasateenagepepper](https://www.instagram.com/iwasateenagepepper/)

The owner asked for no 988 line and no "The End?" heading.

## Interactions & Behavior
- **"for grown-ups" write-on:** it plays once on load. `@keyframes write { from { clip-path: inset(-20% 100% -20% 0) } to { clip-path: inset(-20% 0 -20% 0) } }`, `animation: write 1.8s cubic-bezier(.45,.05,.55,.95) .4s both`. Under `prefers-reduced-motion: reduce`, show the text with no animation.
- **Anchor links** scroll smoothly and must land with the section title below the sticky header. Use `scroll-margin-top` equal to the header height on each section. If the page loads with a hash, it must land correctly too.
- **Hover states** are listed per component above. Give links and buttons clear `:focus-visible` rings too (for example, `outline: 3px solid #151515; outline-offset: 3px`). The current site removes outlines entirely; don't carry that over.
- Breakpoints: **640px** (nav letter-spacing and pill padding) and **720px** (nav links shown, hosts go to 3 columns).

## State
- `openHost: null | index`: opens and closes the modal.
- Nothing is fetched. Host data is a static array of `{ name, initials, bio, photo? }`.

## Design Tokens
Colors:
- `#B9E4F4`: sky (from the cover art)
- `#F7F2EA`: cream
- `#F2C94C`: yellow
- `#FFF6D8`: headline fill
- `#151515`: ink
- `#333333`: hover for dark buttons
- `rgba(21,21,21,.6)`: modal overlay

Fonts (Google Fonts): `Shrikhand` (headlines), `Young Serif` 400 only (all UI and body text; never set a heavier weight, because the browser would fake the bold), `Gochi Hand` (hand-written accents).
`https://fonts.googleapis.com/css2?family=Shrikhand&family=Young+Serif&family=Gochi+Hand&display=swap`

Type scale:
- Body 22px
- UI and small text 20–21px (**20px minimum anywhere**)
- Host name 28px
- Eyebrow 28–34px
- H2 38–58px
- H1 38–64px

Body text uses `letter-spacing: .045em; word-spacing: .08em` for readability.

Headline treatment: 3px ink stroke, `paint-order: stroke fill`, 4px 4px 0 ink hard shadow.

Borders: 2px `#151515`. Shadows: hard, no blur (4px or 8px offsets). Radius: 999px pills only. Everything else is square.

## Assets
- `assets/cover.jpg`: cover art by Pepper Auerbach. It's already in the repo.
- Host photos: **still to come.**

## Open items for the site owner
- Host bios (2–3 sentences each) and photos.
- Destination links for "Become a funder" and "Get in touch".
- Direct show URLs for Apple Podcasts, Spotify and YouTube, if you want them instead of search links.
- Meta tags: keep the existing `<head>` meta, OG and Twitter tags from the current `index.html`, but set `theme-color` to `#B9E4F4`.

## Files
- `Harping with Howie Site.dc.html`: the full design reference, desktop and mobile.
- `Harping with Howie Mobile Preview.dc.html`: shows the site in phone frames at 390×844.
- `support.js`: the runtime needed to open the reference files locally.
- `assets/cover.jpg`: the cover art.
