# TalentBridge — static UI (Week 1)

Two hand-coded pages sharing one stylesheet: `landing.html` (public) and `dashboard.html` (app shell). HTML5 + CSS3 only, no JavaScript.

## Run
Open `landing.html` in a browser (or `npx serve .`).

## CSS architecture decisions
1. **One `styles.css`, six numbered sections** (tokens → base → utilities → components → landing → dashboard) so reuse is obvious and nothing is duplicated between pages.
2. **Design tokens as CSS variables** in `:root`: colour, a 6-step spacing scale (`--s-1…6`), a type scale (fluid `clamp()` for headings), radius and layout widths. No magic numbers in components.
3. **BEM naming** (`.field__control`, `.btn--primary`) keeps specificity flat (single class selectors), so rules never fight each other.
4. **Mobile-first**: base styles are the phone layout; `min-width` queries at 30em, 48em (768px) and 64em add layout. Widths are fluid (`%`, `fr`, `minmax`, `max-width`), never fixed pixels.
5. **Flexbox for 1D** (header bar, nav, bottom nav, button rows); **Grid for 2D** (feature/pricing grids, dashboard shell with `grid-template-areas`, stat cards).
6. **No-JS interactions** use native controls (checkbox, `<details>`) so they work with the keyboard; Week 2 can add `aria-expanded` syncing.

## Layout decisions borrowed from real dashboards (verify against the live products)
- **Vercel / Linear — persistent left sidebar with a collapsed icon rail:** keeps navigation one click away and gives data more room.
- **Linear — search in the top bar, not in the page:** it's a global action, so it stays in one predictable place.
- **Notion / Vercel — stat summary above the detail table:** users see the headline numbers first, then drill down.

## Responsive images
The hero uses `<picture>` with a cropped image under 768px and a wide one above (art direction), plus `width`/`height` to prevent layout shift (MDN: Responsive images).

## Screenshots
Add after running DevTools responsive mode: `docs/mobile-375.png`, `docs/tablet-768.png`, `docs/desktop-1280.png` for each page.

## QA checklist
- [ ] Lighthouse Accessibility ≥ 90 on both pages
- [ ] No horizontal scroll at 320, 375, 768, 1024, 1440px
- [ ] Tab through menu, form, sidebar, user menu; focus ring always visible

## Suggested commits
`chore: init repo` · `feat: design tokens and base styles` · `feat: landing header and hero` · `feat: features, testimonials, pricing` · `feat: accessible signup form` · `feat: dashboard shell` · `feat: responsive table` · `docs: README and screenshots`
