# 🌐 Making Air Piano Publicly Accessible

This guide will help you deploy the Air Piano website so anyone can access it online.

## Option 1: GitHub Pages (Recommended - Free & Easy)

GitHub Pages is the easiest way to host your Air Piano game for free.

### Step 1: Enable GitHub Pages

1. **Go to your GitHub repository:**
   - Visit: https://github.com/zliu31/piano

2. **Navigate to Settings:**
   - Click the "Settings" tab in the top menu

3. **Go to Pages section:**
   - In the left sidebar, click "Pages" (under "Code and automation")

4. **Configure the source:**
   - Under "Build and deployment"
   - **Source:** Select "Deploy from a branch"
   - **Branch:** Select your branch (e.g., `claude/test-piano-connection-01V5uEDYLw3LK9BbSAgoVDio` or create a `main` branch)
   - **Folder:** Select `/ (root)`
   - Click "Save"

5. **Wait for deployment:**
   - GitHub will build and deploy your site (takes 1-2 minutes)
   - A green checkmark will appear when ready

6. **Get your public URL:**
   - Your site will be available at:
   - `https://zliu31.github.io/piano/air-piano.html`
   - Or if you rename the file to `index.html`:
   - `https://zliu31.github.io/piano/`

### Step 2: (Optional) Set a Custom Domain

If you own a domain name:

1. In the Pages settings, add your custom domain
2. Configure DNS settings with your domain provider
3. Follow GitHub's instructions for custom domain setup

### Note: Branch Requirements

If GitHub doesn't allow deployment from the `claude/` branch, you'll need to:

1. **Create a main branch via GitHub web interface:**
   - Go to your repository
   - Click the branch dropdown
   - Type "main" and create a new branch from the current branch

2. **Or merge your changes to an existing main branch:**
   - If you already have a main branch, merge the claude branch into it

## Option 2: Quick Test with GitHub Raw Content

For immediate testing (not ideal for production):

1. Access your file directly via GitHub's raw content:
   ```
   https://raw.githubusercontent.com/zliu31/piano/claude/test-piano-connection-01V5uEDYLw3LK9BbSAgoVDio/air-piano.html
   ```

2. **Note:** This won't work perfectly because:
   - Browsers block webcam access on raw.githubusercontent.com
   - No HTTPS security for localhost features
   - Better for viewing code, not running the app

## Option 3: Netlify Drop (Easiest Alternative)

If GitHub Pages doesn't work, use Netlify Drop:

1. **Go to:** https://app.netlify.com/drop

2. **Drag and drop** your `air-piano.html` file

3. **Get instant URL:**
   - Netlify gives you a random URL like: `https://random-name-12345.netlify.app`
   - You can customize the URL in settings

4. **Advantages:**
   - No git required
   - Instant deployment
   - Free HTTPS
   - Custom domain support

## Option 4: Vercel (Professional Alternative)

For more advanced features:

1. **Install Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Deploy from command line:**
   ```bash
   cd /home/user/piano
   vercel
   ```

3. **Follow prompts:**
   - Login to Vercel
   - Configure project
   - Get instant URL

4. **Advantages:**
   - Automatic deployments on git push
   - Free HTTPS
   - Analytics
   - Edge network (fast worldwide)

## Option 5: Self-Hosted (Advanced)

If you have your own server:

### Using Python:
```bash
cd /home/user/piano
python3 -m http.server 8080
# Access at: http://your-server-ip:8080/air-piano.html
```

### Using Node.js:
```bash
npx http-server -p 8080
# Access at: http://your-server-ip:8080/air-piano.html
```

### Using Nginx:
```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /path/to/piano;
    index air-piano.html;
}
```

## Recommended Setup for Best Results

### Rename for Cleaner URLs

For a cleaner URL (no `/air-piano.html` suffix):

```bash
# Rename the file to index.html
mv air-piano.html index.html
git add index.html
git commit -m "Rename to index.html for cleaner URL"
git push
```

Then your site will be accessible at just:
- `https://zliu31.github.io/piano/`

### Add Custom Domain (Optional)

1. Purchase a domain (e.g., `air-piano.com`)
2. Configure in GitHub Pages settings
3. Update DNS records at your domain registrar
4. Enable HTTPS in GitHub settings

## Troubleshooting

### "Repository is private"
- Go to Settings → General
- Scroll to "Danger Zone"
- Click "Change visibility" → "Make public"

### "Pages not available"
- Ensure repository is public (free GitHub Pages requires public repos)
- Or upgrade to GitHub Pro for private repo Pages

### "Webcam not working on deployed site"
- Ensure site is served over HTTPS (GitHub Pages provides this)
- HTTP sites can't access webcam for security reasons

### "MediaPipe not loading"
- Check browser console for errors
- Ensure CDN links are accessible
- Try different browser (Chrome/Edge recommended)

## Security Note

The Air Piano app:
- ✅ Runs entirely in the browser
- ✅ No server-side code
- ✅ No data collection
- ✅ Webcam processing is local only
- ✅ No data sent to external servers (except MediaPipe CDN for library)

Perfect for public hosting!

## Next Steps After Deployment

1. **Share your URL** on social media
2. **Add a custom domain** for branding
3. **Enable analytics** to see visitor stats
4. **Add to portfolio** or resume
5. **Iterate and improve** based on feedback

## Quick Start: Enable GitHub Pages Now

**TL;DR - Fastest way:**

1. Go to: https://github.com/zliu31/piano/settings/pages
2. Source: "Deploy from a branch"
3. Branch: `claude/test-piano-connection-01V5uEDYLw3LK9BbSAgoVDio`
4. Folder: `/ (root)`
5. Click "Save"
6. Wait 2 minutes
7. Visit: https://zliu31.github.io/piano/air-piano.html

Done! 🎉

---

**Need help?** Check the repository settings or try one of the alternative deployment options above.
