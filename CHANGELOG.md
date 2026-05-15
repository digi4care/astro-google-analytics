# Changelog

All notable changes to this project will be documented in this file.

## [2.0.0] - 2025-05-15

### Breaking Changes
- **Requires Astro 6+** — dropped support for Astro 1–5 (peer dependency `astro: ^6.0.0`)
- **Removed `@digi4care/astro-google-tagmanager` runtime dependency**

### Added
- **View Transitions / ClientRouter support**: GA page views are now re-tracked after client-side navigation via `astro:after-swap` event listener (fixes #1)
- Uses `define:vars={{ id }}` for passing the measurement ID to the inline script (Astro 6 native approach)

### Changed
- Removed fake default prop values (`"GA_MEASUREMENT_ID"`, `"GA4_MEASUREMENT_ID"`) — `id` is now required
- Removed redundant `is:inline` directive where `define:vars` is present (Astro 6 implies it)
- Fixed all component export names in README (`Analytics` → `GoogleAnalytics`, `AnalyticsNoScript` → `GoogleAnalyticsNoscript`)
- Removed Dutch HTML comments from component templates

## [1.1.1] - 2025-05-09

- Added `SiteVerification` component export
- Expanded domain prop usage details

## [1.1.0] - 2025-05-09

- Added Astro v5 support
- Bumped package version

## [1.0.0] - 2024-07-04

- Initial release
