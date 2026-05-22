# Deployment Guide: GitHub → Netlify

This guide walks you through connecting this repository to Netlify for automatic deployments.

## Step 1: Create GitHub Repository

**Already done!** The code is ready to push to GitHub.

## Step 2: Connect to Netlify (5 minutes)

### 2a. Log into Netlify
1. Go to [netlify.com](https://netlify.com)
2. Sign in with your account

### 2b. Create New Site from Git
1. Click **"New site from Git"** (or "Add new site")
2. Select **GitHub** as your Git provider
3. Authorize Netlify to access your GitHub account (if prompted)
4. Search for and select the **`sam-prentice`** repository

### 2c. Configure Build Settings
1. **Build command:** Leave empty (or just press space)
2. **Publish directory:** `.` (current directory)
3. **Environment variables:** None needed
4. Click **"Deploy site"**

Netlify will now deploy your site! 🎉

## Step 3: Update DNS in Manus

Once Netlify has deployed (takes 1-2 minutes):

1. **Get your Netlify DNS info:**
   - Go to your Netlify site dashboard
   - Click **Site Settings** → **Domain Management**
   - Look for "Nameservers" or "DNS records"
   - Netlify will show you the A record and CNAME values

2. **Update DNS in Manus:**
   - Go to your Manus project → **Settings** → **Domains**
   - Find **sam-prentice.com**
   - Update the DNS records to match Netlify's values
   - Save changes

3. **Wait for DNS propagation** (5-30 minutes)
   - Your site will now be live on Netlify!

## Step 4: Verify Everything Works

1. Visit [sam-prentice.com](https://sam-prentice.com) in your browser
2. Run a [Lighthouse audit](https://pagespeed.web.dev/) to verify 85-95/100 score
3. Check that all content, images, and forms work correctly

## Automatic Deployments

From now on, every time code is pushed to GitHub:
1. Netlify automatically detects the change
2. Netlify rebuilds and deploys your site
3. Your site is live within 1-2 minutes

## Making Updates

To update your site in the future:

### Option A: Edit Files in GitHub
1. Go to your GitHub repository
2. Click on the file you want to edit (e.g., `index.html`)
3. Click the pencil icon to edit
4. Make your changes
5. Click "Commit changes"
6. Netlify automatically deploys! ✨

### Option B: Push Changes from Command Line
```bash
git clone https://github.com/YOUR_USERNAME/sam-prentice.git
cd sam-prentice
# Make your changes to files
git add .
git commit -m "Update: [describe your changes]"
git push origin main
# Netlify automatically deploys!
```

## Performance Expectations

After deployment to Netlify, you should see:

| Metric | Expected |
|--------|----------|
| **Lighthouse Performance** | 85-95/100 |
| **First Contentful Paint** | 1-2 seconds |
| **Largest Contentful Paint** | 1.5-2.5 seconds |
| **Cumulative Layout Shift** | 0 (perfect) |
| **Total Blocking Time** | <100ms |

## Troubleshooting

### Site shows "Not Found" after DNS change
- **Cause:** DNS propagation takes 5-30 minutes
- **Solution:** Wait and refresh your browser

### Netlify shows "Page not found"
- **Cause:** Build settings incorrect
- **Solution:** Check Netlify Site Settings → Build & Deploy
  - Build command: (empty)
  - Publish directory: `.`

### Images not loading
- **Cause:** Image paths incorrect
- **Solution:** Check that image files exist in repository

### Forms not working
- **Cause:** Email service not configured
- **Solution:** Update the form submission endpoint in `index.html`

## Support

- **Netlify Help:** [docs.netlify.com](https://docs.netlify.com/)
- **GitHub Help:** [docs.github.com](https://docs.github.com/)
- **Performance:** [pagespeed.web.dev](https://pagespeed.web.dev/)

## Next Steps

1. ✅ Code is ready
2. ⏳ You: Connect to Netlify
3. ⏳ You: Update DNS in Manus
4. ✅ Automatic deployments enabled!

---

**Questions?** Refer to the README.md for more details about the site structure and customization.
