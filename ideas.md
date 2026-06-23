# WeLoveIt — Feature Ideas & Improvements

A product backlog for the WeLoveIt Hugo theme (fork of LoveIt). Ideas are grouped by area, each with a rough priority. The RTL/multilingual section is treated as the primary differentiator for this fork.

> Priority key: **High** = strong value, foundational, or a current gap; **Medium** = nice improvement, not urgent; **Low** = polish or niche.

---

## RTL & Internationalization

This is the fork's differentiator. Today RTL is wired only through the `dir` attribute on `<html>` (`baseof.html`) plus a couple of inline `direction` styles in the header. The SCSS still uses physical properties (`margin-left`, `padding-right`, `left:`, `text-align: left`) with **no** logical properties and **no** `[dir="rtl"]` selectors, so many components will visually break or misalign when mirrored. Most ideas below address that.

1. **Migrate SCSS to CSS logical properties** — Replace physical properties (`margin-left`, `padding-right`, `left/right`, `text-align: left/right`) with logical equivalents (`margin-inline-start`, `padding-inline`, `inset-inline`, `text-align: start/end`) so layouts mirror automatically in RTL. *Priority: High*

2. **Audit & fix mirrored components in RTL** — Visually QA header, TOC, pagination, archive/terms, code copy button, share buttons, and the consent banner in RTL and fix the elements that don't flip. *Priority: High*

3. **Bundled high-quality Persian/Arabic webfont** — Ship an optional Vazirmatn (FA) / a well-hinted Arabic font with proper `font-display` and subsetting, since default system fonts render Farsi/Arabic poorly. *Priority: High*

4. **Per-language font stacks** — Allow the active language to pick its own `font-family` (Latin vs. Arabic-script) instead of one global stack, improving legibility for mixed-script sites. *Priority: Medium*

5. **Directional icon flipping** — Auto-mirror directional icons (arrows, chevrons, "back/next", read-more) under `[dir="rtl"]` so navigation cues point the correct way. *Priority: Medium*

6. **Logical-aware shortcodes** — Review `admonition`, `image`, `version`, and `person` shortcodes for hardcoded left/right alignment and make them direction-aware. *Priority: Medium*

7. **Mixed LTR/RTL content helper** — A `bdi`/`dir="auto"` wrapper utility (and shortcode) for embedding code, URLs, English terms, or numbers inside RTL prose without breaking word order. *Priority: Medium*

8. **Eastern Arabic numeral option** — Optional per-language toggle to render dates, reading time, and pagination using Persian/Arabic-Indic digits (`۱۲۳`) via `toReplace`/format helpers. *Priority: Low*

9. **Jalali (Shamsi) date formatting** — Support the Persian solar calendar for post dates, a frequent request for Farsi blogs that Hugo doesn't handle natively. *Priority: Medium*

10. **Complete & sync the Farsi i18n file** — `fa.toml` (198 lines) trails `en.toml` (207 lines); audit for missing keys and add the gaps so no English strings leak into Farsi pages. *Priority: High*

11. **RTL-aware search UI** — The header already injects inline `direction` styles for the search input; extend correct direction/alignment to the results dropdown, highlight tags, and "no results" states. *Priority: Medium*

12. **Documented RTL setup recipe** — A short docs section + an RTL example language in `exampleSite` showing `languageDirection = "rtl"`, recommended fonts, and known caveats. *Priority: Medium*

---

## UX/UI

13. **Reading progress bar** — A thin top-of-page progress indicator on post pages; a common, low-cost engagement feature. *Priority: Medium*

14. **Back-to-top refinement** — A scroll-percentage ring around the existing fixed button, with reduced-motion respect. *Priority: Low*

15. **Series / multi-part post navigation** — Auto-generated "Part X of Y" navigation linking related posts in a series via front matter. *Priority: Medium*

16. **Related posts block** — Surface related content (by tags/keywords) at the end of posts using Hugo's built-in `.Site.RegularPages.Related`. *Priority: Medium*

17. **TOC scroll-spy** — Highlight the current section in the TOC as the reader scrolls. *Priority: Medium*

18. **Theme-color skinning** — Expose a small set of accent-color presets (or a single SCSS variable) so owners can rebrand without forking the stylesheet. *Priority: Medium*

19. **Configurable home layout variants** — Offer card grid vs. list vs. compact for the home posts list, selectable in config. *Priority: Low*

---

## Content Features

20. **Callout/admonition expansion** — Add collapsible state and a few more types (e.g., `quote`, `example`) to the existing `admonition` shortcode. *Priority: Low*

21. **Native image gallery shortcode** — A lightweight grid/lightbox gallery (the theme already has a `lightgallery` flag) driven by a folder or list of images. *Priority: Medium*

22. **Footnote popovers** — Show footnote content in a hover/tap popover instead of jumping to the page bottom. *Priority: Low*

23. **Video embed shortcode** — A privacy-friendly (click-to-load) YouTube/Vimeo shortcode to complement the existing `bilibili` one. *Priority: Medium*

24. **Tabs shortcode** — Tabbed content blocks, useful for code-in-multiple-languages and OS-specific instructions. *Priority: Low*

25. **Author profiles for multi-author sites** — Extend the `person` shortcode / author config into reusable author taxonomy pages with bio and social links. *Priority: Low*

---

## Developer Experience

26. **Trim & document config** — `hugo.toml` ships a huge 200+ entry `[params.social]` block and mixed Chinese/English comments; split into a documented minimal default plus an "all options" reference. *Priority: Medium*

27. **Consent config consolidation** — Two overlapping mechanisms exist (`[params.cookieconsent]` and the newer `[params.consent]` with script items). Unify or clearly document which to use. *Priority: Medium*

28. **CI: build + htmltest + linkcheck** — Add a GitHub Actions workflow that builds `exampleSite`, runs an HTML/link checker, and lints SCSS on PRs. *Priority: Medium*

29. **Stylelint with logical-property rule** — Add stylelint configured to flag physical properties, locking in the RTL migration (idea #1) going forward. *Priority: Medium*

30. **Versioned upgrade/migration notes** — A CHANGELOG and a "diff from upstream LoveIt" doc so fork-specific changes (RTL, Farsi, consent) are traceable. *Priority: Low*

---

## Performance

31. **Responsive images pipeline** — Use Hugo image processing to emit `srcset`/`sizes` and modern formats (WebP/AVIF) for content and cover images. *Priority: High*

32. **Lazy-load heavy plugins** — Load Mermaid, ECharts, Mapbox, KaTeX, and the music player only when a page actually uses them (per-page asset gating). *Priority: High*

33. **Self-host or SRI-pin CDN assets** — The CDN data file (`jsdelivr.yml`) pulls third-party libs; offer a fully self-hosted bundle option for privacy and offline reliability. *Priority: Medium*

34. **Critical-CSS / unused-CSS trimming** — Inline above-the-fold CSS and tree-shake unused rules to cut render-blocking weight. *Priority: Medium*

35. **Font subsetting & `font-display: swap`** — Especially impactful for the bundled Arabic/Persian webfonts (idea #3). *Priority: Medium*

---

## Accessibility

36. **RTL + a11y audit pass** — Run axe/Lighthouse on both LTR and RTL builds; fix focus order, landmark roles, and color-contrast issues. *Priority: High*

37. **Visible focus states & skip-to-content link** — Ensure keyboard focus is always visible and add a skip link before the header nav. *Priority: High*

38. **Reduced-motion support** — Honor `prefers-reduced-motion` for TypeIt, theme transitions, and any scroll animations. *Priority: Medium*

39. **Accessible theme toggle & menus** — Verify the dark/light toggle and mobile menu expose proper `aria-pressed`/`aria-expanded` state and are operable by keyboard and screen readers. *Priority: High*

40. **Consent banner accessibility** — Make the GDPR/consent banner a proper focus-trapped dialog with labeled controls and screen-reader announcement. *Priority: Medium*

---

*Drafted from a read of `hugo.toml`, `exampleSite/hugo.toml`, `layouts/` (baseof, header, partials, shortcodes), `assets/css/`, and the `i18n/` files. No code was changed.*
