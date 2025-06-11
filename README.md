# @digi4care/astro-google-analytics

A seamless integration for injecting Google Analytics snippets into Astro projects, supporting popular web analytics tools.

## Installation

To install the package, use npm or yarn:

```bash
npm install @digi4care/astro-google-analytics
```

or

```bash
yarn add @digi4care/astro-google-analytics
```

## Usage

This package provides components for easily adding Google Analytics (GA4) and Site Verification snippets to your Astro project.

### Example

```astro
---
import { Analytics, AnalyticsNoScript, SiteVerification } from '@digi4care/astro-google-analytics';
---
<!doctype html>
<html lang="en" dir="ltr">
  <head>
    <SiteVerification id="GA_VERIFICATION_ID" />
    <Analytics id="GA4_MEASUREMENT_ID" partytown={false} domain="https://www.some-custom-domain-is-also-supported.com" />
  </head>

  <body>
    <AnalyticsNoScript id="GA4_MEASUREMENT_ID" domain="https://www.some-custom-domain-is-also-supported.com" />
    <slot />
  </body>
</html>
```

### Notes

- **Analytics Component**: This component injects the Google Analytics script into your Astro project. Pass your GA4 measurement ID as the `id` prop. The `domain` prop is particularly important for:
  - Cross-domain tracking: When you want to track user behavior across multiple domains
  - Subdomain tracking: When you want to track across subdomains of your main domain
  - Custom domain configurations: When using a custom domain for the Google Analytics script
  
  For most standard implementations, you can omit the domain parameter unless you specifically need cross-domain or subdomain tracking.
- **AnalyticsNoScript Component**: This component provides a no-script fallback for Google Analytics. Note that there is no `partytown` support for this component.
- **SiteVerification Component**: Use this component to add site verification meta tags. Pass your verification ID as the `id` prop. You can also specify the `name` prop to use different site verification names for various vendors.

### Important

Be aware that the `AnalyticsNoScript` component does not support `partytown`. Do not use it if you want to enable `partytown`.

## Props

### Analytics

- **id** (string): Your GA4 measurement ID.
- **partytown** (boolean): Enable or disable partytown. Default is `false`.
- **domain** (string): Custom domain for the Google Analytics script. Default is `https://www.googletagmanager.com`.

### AnalyticsNoScript

- **id** (string): Your GA4 measurement ID.
- **domain** (string): Custom domain for the Google Analytics script. Default is `https://www.googletagmanager.com`.

### SiteVerification

- **id** (string): Your site verification ID.
- **name** (string): The name attribute for the meta tag. Default is `google-site-verification`. This allows you to use different site verification names for various vendors.

```astro
---
export interface Props {
  name?: string;
  id?: string;
}
const { id, name = "google-site-verification" } = Astro.props;
---

{id && <meta name={name} content={id} />}
```

## License

This project is licensed under the MIT License.
