# @digi4care/astro-google-analytics

Google Analytics (GA4) integration for Astro 6+ with ClientRouter (View Transitions) and Partytown support.

## Requirements

- **Astro 6.0.0 or higher** — this package does not work with Astro 1–5.

## Installation

```bash
npm install @digi4care/astro-google-analytics
```

## Usage

```astro
---
import { GoogleAnalytics, GoogleAnalyticsNoscript, SiteVerification } from '@digi4care/astro-google-analytics';
---
<!doctype html>
<html lang="en" dir="ltr">
  <head>
    <SiteVerification id="GA_VERIFICATION_ID" />
    <GoogleAnalytics id="G-XXXXXXXXXX" />
  </head>

  <body>
    <GoogleAnalyticsNoscript id="G-XXXXXXXXXX" />
    <slot />
  </body>
</html>
```

> **Note:** `id` is required. There is no default value — you must pass your real GA4 measurement ID.

## ClientRouter / View Transitions

Page views are automatically re-tracked after client-side navigation. The component listens for the `astro:after-swap` event internally. No extra configuration needed — just make sure you're using `<ClientRouter />` from Astro.

## Partytown

The `GoogleAnalytics` component supports offloading the GA scripts to a web worker via [Partytown](https://partytown.builder.io/).

### Step 1: Install and configure Partytown in your project

This package does **not** include Partytown. You must install and configure it separately in your Astro project:

```bash
npm install @astrojs/partytown
```

```js
// astro.config.mjs
import partytown from "@astrojs/partytown";

export default defineConfig({
  integrations: [partytown()],
});
```

### Step 2: Enable the `partytown` prop

```astro
<GoogleAnalytics id="G-XXXXXXXXXX" partytown={true} />
```

That's it. The component sets `type="text/partytown"` on the script tags, which Partytown picks up and runs in a web worker.

> **Important:** `GoogleAnalyticsNoscript` does **not** support Partytown. It renders a `<noscript>` fallback that must run on the main thread.

## Props

### GoogleAnalytics

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | **(required)** | Your GA4 measurement ID |
| `partytown` | `boolean` | `false` | Offload GA scripts to a web worker via Partytown |
| `domain` | `string` | `"https://www.googletagmanager.com"` | Custom domain for the GA script (useful for cross-domain or subdomain tracking) |

### GoogleAnalyticsNoscript

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | **(required)** | Your GA4 measurement ID |
| `domain` | `string` | `"https://www.googletagmanager.com"` | Custom domain for the GA script |

### SiteVerification

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | **(required)** | Your site verification ID |
| `name` | `string` | `"google-site-verification"` | The meta tag name attribute (change for non-Google vendors) |

## Migration from v1.x

| Change | Action |
|--------|--------|
| Requires Astro 6+ | Update your Astro project to `^6.0.0` |
| Import `Analytics` | Rename to `GoogleAnalytics` |
| Import `AnalyticsNoScript` | Rename to `GoogleAnalyticsNoscript` |
| `id` had a fake default | You must now pass a real measurement ID |

## License

MIT
