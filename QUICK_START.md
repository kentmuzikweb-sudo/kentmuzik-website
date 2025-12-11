# Quick Deployment to Netlify - KentMuzik

## Fastest Method: Netlify CLI (5 minutes)

### 1. Install Netlify CLI
```bash
npm install -g netlify-cli
```

### 2. Login
```bash
netlify login
```

### 3. Deploy from Project Root
```bash
cd /tmp/cc-agent/61229115/project
netlify deploy --prod
```

When prompted:
- Create new site? **Yes**
- Team: Choose your team
- Site name: `kentmuzik` (or your choice)
- Publish directory: `dist`

### 4. Set Environment Variables
After first deployment:
```bash
netlify env:set VITE_SUPABASE_URL "https://cfdtrfwcquivltqjjnlw.supabase.co"
netlify env:set VITE_SUPABASE_ANON_KEY "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNmZHRyZndjcXVpdmx0cWpqbmx3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUxODQ2NDksImV4cCI6MjA4MDc2MDY0OX0.gLDb7LmYbw1qVJ319OfTp6As6WDJERGs1PxrLyJnS_c"
```

### 5. Redeploy with Environment Variables
```bash
netlify deploy --prod
```

**Done! Your site is live!** 🚀

---

## Alternative: Manual Upload (3 minutes)

### 1. Build Locally
```bash
npm run build
```

### 2. Go to Netlify
- Visit: https://app.netlify.com/drop
- Drag the entire `dist` folder to the page

### 3. Add Environment Variables
After upload:
1. Click on your new site
2. Go to: Site settings → Environment variables
3. Add these two variables:
   - `VITE_SUPABASE_URL`: `https://cfdtrfwcquivltqjjnlw.supabase.co`
   - `VITE_SUPABASE_ANON_KEY`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNmZHRyZndjcXVpdmx0cWpqbmx3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUxODQ2NDksImV4cCI6MjA4MDc2MDY0OX0.gLDb7LmYbw1qVJ319OfTp6As6WDJERGs1PxrLyJnS_c`

4. Go to: Deploys → Trigger deploy → Deploy site

**Done!** 🎉

---

## After Deployment

### Change Site Name
1. Go to: Site settings → General → Site details
2. Click "Change site name"
3. Enter: `kentmuzik` (or your preferred name)
4. Your site: `https://kentmuzik.netlify.app`

### Enable Form Notifications (Optional)
1. Go to: Site settings → Forms
2. Enable form notifications
3. Add your email for contact form submissions

---

## Test Your Site

Visit your site and check:
- ✅ Homepage loads
- ✅ Navigation works
- ✅ Products page displays items
- ✅ Contact page loads
- ✅ All images display
- ✅ Mobile responsive

---

## Troubleshooting

**Products not loading?**
- Check environment variables are set in Netlify dashboard
- Trigger a new deploy after adding variables

**404 on page refresh?**
- The `_redirects` file should handle this automatically
- Check it exists in your `dist` folder after build

**Need help?**
See full guide: `DEPLOYMENT_GUIDE.md`
