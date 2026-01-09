# HTML Preview

A lightning-fast, serverless HTML preview application that renders any hosted HTML file with automatic resource resolution.

## Features

- **No server required**: Pure client-side application
- **URL parameter support**: Pass any HTML file URL via `?url=` parameter
- **Automatic resource resolution**: Automatically resolves and loads relative CSS, JavaScript, images, and other assets
- **GitHub support**: Automatically converts GitHub blob URLs to raw URLs
- **Lightning fast**: Minimal overhead with optimized resource rewriting
- **CORS fallback**: Attempts direct fetch first, falls back to CORS proxy if needed

## Usage

Simply append `?url=YOUR_HTML_FILE_URL` to the index.html URL:

```
index.html?url=https://github.com/user/repo/blob/main/public/index.html
```

### Example

```
index.html?url=https://raw.githubusercontent.com/mdn/beginner-html-site-styled/gh-pages/index.html
```

## How it works

1. Extracts the URL from the `?url=` parameter
2. Converts GitHub blob URLs to raw.githubusercontent.com URLs
3. Fetches the HTML file (tries direct fetch, falls back to CORS proxy)
4. Parses and rewrites all relative resource URLs (CSS, JS, images, etc.)
5. Extracts the base URL by removing the filename from the original URL
6. Resolves all relative paths against the base URL
7. Injects the modified HTML into an iframe for rendering

## Supported Resources

- CSS files (`href` in `<link>` tags)
- JavaScript files (`src` in `<script>` tags)
- Images (`src` in `<img>` tags, `srcset` attributes)
- Background images in CSS (`url()` in style attributes)
- Other relative resources

## Deployment

Deploy the `index.html` file to any static hosting service:
- GitHub Pages
- Netlify
- Vercel
- Any static file server

No build process or server-side code required!