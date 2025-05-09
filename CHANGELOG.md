# Changelog

All notable changes to this project will be documented in this file.

## [1.1.1-beta.1] - 2025-05-09

### 🧪 Beta Release
This is a beta release that needs thorough testing before being promoted to a stable release.

### 🔄 Changed
- **[Universal Analytics Support]** Enhanced Google Analytics implementation to work seamlessly in all navigation scenarios
  - Works with regular page navigation (default Astro behavior)
  - Added support for Astro View Transitions via `astro:after-swap` event
  - Properly tracks page views in both navigation modes
  - Maintains analytics continuity during client-side transitions
  - Preserves script functionality with `is:inline` directive

### 🧪 Testing Needed
Please test this beta release thoroughly, especially:
1. Page views with View Transitions enabled
2. GA script reinitialization after navigation
3. Analytics tracking in GA4 Real-Time dashboard
4. Browser back/forward navigation tracking
5. Rapid page transitions handling

### 📝 Notes
- This is a beta release addressing View Transitions compatibility
- Report any issues on GitHub
- Test in both development and production environments
- Verify page views appear in GA4 Real-Time reports

## [1.1.0] - Previous Release
- Previous stable release with Astro v5.0 support
