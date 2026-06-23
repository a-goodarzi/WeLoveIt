# Changelog

All notable changes to this project will be documented in this file.

## [0.1.0](https://github.com/a-goodarzi/WeLoveIt/releases/tag/v0.1.0) (2026-06-23)

### Features

* Native RTL layout support for Farsi/Arabic content ([`dir` attribute on `<html>`](layouts/baseof.html))
* Farsi (Persian) i18n translation (`i18n/fa.toml`)
* GDPR cookie consent banner with per-script granular control (`layouts/_partials/consent.html`)
* GDPR consent banner styled with theme design tokens — full dark/light mode support, logical CSS properties
* Synced with upstream [dillonzq/LoveIt](https://github.com/dillonzq/LoveIt) (100 commits, July 2022 → June 2025)
  * Hugo 0.128+ compatibility, `hugo.toml` config format
  * New search engines: Pagefind and Fuse.js
  * Content-Security-Policy meta tag support
  * Blockquote alert rendering hook
  * Refactored admonition shortcode
  * FontAwesome v7.2.0, simple-icons v16.9.0
  * New i18n: Japanese, Swedish, Dutch, Bengali, Hindi
  * GoatCounter analytics support
  * Layouts restructured from `partials/` to `_partials/`
  * `theme.js` rewritten as modern ES6

### Bug Fixes

* Replace deprecated `.Language.LanguageDirection` with `.Language.Direction` (Hugo v0.158+) in `baseof.html` and `header.html`
* Fix `animate__FadeIn` → `animate__fadeIn` (wrong casing broke scroll-in animation on fixed buttons)
* Fix consent overlay backdrop click using `classList.toggle` → `classList.remove` (could re-open a dismissed overlay)

### Accessibility & UX

* Add `role="dialog"`, `aria-modal`, `aria-label` to consent overlay
* Add Escape key dismissal for the consent overlay
* Add `aria-label` to desktop and mobile search inputs
* Add `aria-label` to desktop and mobile language `<select>` elements
* Restore `:focus-visible` outlines on fixed buttons (was incorrectly suppressed)
* Add `:focus-visible` outlines on all consent banner buttons
* Raise secondary text contrast to meet WCAG AA: `#a9a9b3 → #767676` (light), `#5d5d5f → #8e8e8e` (dark)
* Add `rel="noopener noreferrer"` to author link in footer

### CSS / RTL

* Migrate physical CSS properties to logical equivalents in `_header.scss`, `_media.scss`, and `_consent.scss` (`margin-left/right` → `margin-inline-*`, `padding-left/right` → `padding-inline-*`, `text-align: left` → `text-align: start`)
* Remove dead duplicate `@media (max-width: 1440px)` block in `_media.scss`

### Miscellaneous

* Replace all `numb95` GitHub username references with `a-goodarzi`
* Update Hugo compatibility badge to `^0.128.0`
* Add Farsi to supported languages list in README
