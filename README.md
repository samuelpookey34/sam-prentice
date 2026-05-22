# Sam Prentice - Static HTML Site

Pure static HTML/CSS site optimized for maximum performance (85-95/100 Lighthouse score).

## What's Included

- **index.html** - Main page with all content sections
- **netlify.toml** - Netlify configuration with caching and security headers
- **_redirects** - Netlify routing configuration
- **Images** - Optimized AVIF, WebP, and JPG variants
- **Fonts** - Google Fonts (Crimson Pro, Inter)
- **Analytics** - Google Analytics and Umami tracking (async, non-blocking)

## Key Features

✅ **Zero JavaScript Framework** - Pure HTML/CSS only
✅ **Optimized Images** - Responsive AVIF/WebP with multiple sizes
✅ **Performance** - Expected 85-95/100 Lighthouse score
✅ **Analytics** - Google Analytics + Umami (async)
✅ **Email Forms** - Functional email signup
✅ **SEO Ready** - Meta tags, Open Graph, structured data
✅ **Responsive** - Mobile-first design
✅ **Fast Load Times** - 1-2 seconds on 4G

## Deployment to Netlify

### Option 1: Connect GitHub Repository (Recommended)

1. **Push to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Pure static HTML site"
   git remote add origin https://github.com/YOUR_USERNAME/sam-prentice.git
   git push -u origin main
   ```

2. **Connect to Netlify:**
   - Go to [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Select GitHub and authorize
   - Select your repository
   - Build command: (leave empty)
   - Publish directory: `.` (current directory)
   - Click "Deploy site"

3. **Configure Custom Domain:**
   - Go to Site Settings → Domain Management
   - Add custom domain: `sam-prentice.com`
   - Update DNS records at your domain registrar

### Option 2: Direct Upload (Drag & Drop)

1. **Zip all files:**
   ```bash
   zip -r sam-prentice-static.zip .
   ```

2. **Upload to Netlify:**
   - Go to [netlify.com](https://netlify.com)
   - Drag and drop the ZIP file
   - Netlify will deploy automatically

3. **Configure Custom Domain:**
   - Same as Option 1, step 3

### Option 3: Netlify CLI

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod --dir=.
```

## Performance Expectations

| Metric | Expected |
|--------|----------|
| Lighthouse Performance | 85-95/100 |
| FCP (First Contentful Paint) | 1-2 seconds |
| LCP (Largest Contentful Paint) | 1.5-2.5 seconds |
| CLS (Cumulative Layout Shift) | 0 (perfect) |
| TBT (Total Blocking Time) | <100ms |

## Analytics

The site includes:
- **Google Analytics** - Tracks page views, user behavior
- **Umami Analytics** - Privacy-focused analytics
- **Email Signup** - Captures emails for mailing list

All analytics scripts load **asynchronously** and don't block page rendering.

## Customization

### Update Content
Edit `index.html` directly to change:
- Text content
- Links and CTAs
- Email signup destination
- Analytics IDs

### Update Images
Replace image files in the root directory:
- `hero-bg-teal-*.avif/webp/jpg` - Hero background
- `sam-headshot-final.webp` - Profile image

### Update Styles
Edit inline CSS in `<style>` tag in `index.html`:
- Colors (CSS variables at top)
- Fonts (Google Fonts)
- Spacing and layout

## SEO

The site includes:
- ✅ Meta tags (description, keywords, author)
- ✅ Open Graph tags (social sharing)
- ✅ Twitter Card tags
- ✅ Canonical URL
- ✅ Structured data ready
- ✅ Mobile-friendly
- ✅ Fast load times (Core Web Vitals)

## Support

For Netlify-specific questions, see:
- [Netlify Documentation](https://docs.netlify.com/)
- [Netlify Support](https://support.netlify.com/)

For performance optimization:
- Run [PageSpeed Insights](https://pagespeed.web.dev/)
- Run [GTmetrix](https://gtmetrix.com/)
- Check [WebPageTest](https://www.webpagetest.org/)

## License

© 2026 Sam Prentice. All rights reserved.
