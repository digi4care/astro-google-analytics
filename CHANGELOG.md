# Changelog

All notable changes to this project will be documented in this file.

## [1.1.1-beta.0] - 2025-05-09

### 🧪 Beta Release
This is a beta release that needs thorough testing before being promoted to a stable release.

### 🔄 Changed
- **[View Transitions Support]** Enhanced Google Analytics implementation to properly handle Astro View Transitions
  - Added event listener for `astro:after-swap` to handle page transitions
  - Re-initializes GA after each view transition
  - Maintains proper page view tracking during client-side navigation
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
