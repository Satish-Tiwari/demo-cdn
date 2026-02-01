# Demo CDN

A production-ready CDN setup for hosting static JavaScript assets via Cloudflare Pages with optimized caching and global delivery.

## Project Structure

```
demo-cdn/
└── public/
    ├── cdn/
    │   └── native-framework/
    │       └── bundle.v1.0.0.min.js
    ├── _headers
    ├── LICENSE
    └── README.md
```

## Asset URL

```
https://demo-cdn-83f.pages.dev/cdn/native-framework/bundle.v1.0.0.min.js
```

## Usage

### Include in HTML

```html
<script src="https://demo-cdn-83f.pages.dev/cdn/native-framework/bundle.v1.0.0.min.js" defer></script>
```

### Load via JavaScript

```javascript
// Dynamic import
import('https://demo-cdn-83f.pages.dev/cdn/native-framework/bundle.v1.0.0.min.js')
  .then(module => {
    // Use the module
  });

// Or create script element
const script = document.createElement('script');
script.src = 'https://demo-cdn-83f.pages.dev/cdn/native-framework/bundle.v1.0.0.min.js';
script.defer = true;
document.head.appendChild(script);
```

## Features

✨ **Global CDN Delivery** - Powered by Cloudflare's global network for low-latency access worldwide

🚀 **Optimized Caching** - Configured with `max-age=31536000, immutable` for 1-year browser caching

🔒 **CORS Enabled** - Cross-origin resource sharing enabled for use on any domain

⚡ **High Performance** - Minified bundle with efficient delivery through Cloudflare Pages

🔄 **Version Control** - Versioned assets (v1.0.0) for cache busting and deployment management

## Cache Configuration

The `_headers` file configures optimal caching behavior:

```
/cdn/*
  Cache-Control: public, max-age=31536000, immutable
  Access-Control-Allow-Origin: *
  X-Content-Type-Options: nosniff
```

### Cache Behavior

- **max-age=31536000**: Assets cached for 1 year (31,536,000 seconds)
- **immutable**: Browsers won't revalidate during cache period
- **public**: Can be cached by CDNs and proxies
- **CORS enabled**: Accessible from any origin

## Deployment

This project is automatically deployed via Cloudflare Pages connected to the GitHub repository:

**Repository:** `Satish-Tiwari/demo-cdn`  
**Branch:** `master`  
**Build Configuration:**
- Root directory: `public`
- Build output directory: `/`
- Build command: (none - static files)

### Adding New Assets

1. Place your files in `public/cdn/native-framework/`
2. Update versioning in filename (e.g., `bundle.v1.0.1.min.js`)
3. Commit and push to trigger automatic deployment
4. Cloudflare Pages will deploy within 1-2 minutes

## Custom Domain (Optional)

To use a custom domain:

1. Go to Cloudflare Pages dashboard
2. Navigate to **Custom domains**
3. Add your domain (e.g., `cdn.yourdomain.com`)
4. Update DNS records as instructed
5. Use your custom domain in production:
   ```
   https://cdn.yourdomain.com/cdn/native-framework/bundle.v1.0.0.min.js
   ```

## Versioning Strategy

Use semantic versioning in filenames for cache management:

- **Major changes:** `bundle.v2.0.0.min.js` (breaking changes)
- **Minor updates:** `bundle.v1.1.0.min.js` (new features)
- **Patches:** `bundle.v1.0.1.min.js` (bug fixes)

This approach ensures:
- Users automatically get cached versions
- New versions require URL updates (explicit opt-in)
- No cache invalidation needed

## Performance Benefits

With this CDN setup, you get:

- **~0ms latency** for cached assets (served from browser disk cache)
- **<50ms latency** for uncached assets (Cloudflare edge network)
- **Zero origin hits** after initial load (1-year cache)
- **Bandwidth savings** from aggressive caching
- **Global availability** via 300+ Cloudflare data centers

## License

MIT

## Support

For issues or questions, please open an issue in the GitHub repository.