# CDN Demo

This is a minimal example project demonstrating how to publish a static,
JavaScript bundle via Cloudflare Pages.

## Structure

cdn/
 ├─ native-framework/bundle.js
 └─ _headers

## Usage

```html
<script src="https://<project-name>.pages.dev/native-framework/bundle.js" defer></script>
```

## Features
- Global CDN delivery via Cloudflare Pages
- Long-term cache headers
