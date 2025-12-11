# KentMuzik - Netlify Deployment Guide

## Prerequisites
- A Netlify account (sign up at https://netlify.com)
- Your project code ready to deploy

## Method 1: Deploy via Netlify CLI (Recommended)

### Step 1: Install Netlify CLI
```bash
npm install -g netlify-cli
```

### Step 2: Login to Netlify
```bash
netlify login
```
This will open a browser window for authentication.

### Step 3: Initialize and Deploy
From your project directory:
```bash
netlify init
```

Follow the prompts:
- Create & configure a new site
- Choose your team
- Site name: `kentmuzik` (or your preferred name)
- Build command: `npm run build`
- Directory to deploy: `dist`

### Step 4: Set Environment Variables
```bash
netlify env:set VITE_SUPABASE_URL "https://cfdtrfwcquivltqjjnlw.supabase.co"
netlify env:set VITE_SUPABASE_ANON_KEY "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNmZHRyZndjcXVpdmx0cWpqbmx3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUxODQ2NDksImV4cCI6MjA4MDc2MDY0OX0.gLDb7LmYbw1qVJ319OfTp6As6WDJERGs1PxrLyJnS_c"
```

### Step 5: Deploy
```bash
netlify deploy --prod
```

---

## Method 2: Deploy via Netlify Dashboard (Manual)

### Step 1: Prepare Your Build
Run the build locally to ensure everything works:
```bash
npm install
npm run build
```

### Step 2: Go to Netlify Dashboard
1. Visit https://app.netlify.com
2. Click "Add new site" > "Deploy manually"

### Step 3: Drag and Drop
- Drag your entire `dist` folder to the upload area

### Step 4: Configure Site Settings
After deployment:
1. Go to "Site settings" > "Build & deploy" > "Environment"
2. Add environment variables:
   - `VITE_SUPABASE_URL`: `https://cfdtrfwcquivltqjjnlw.supabase.co`
   - `VITE_SUPABASE_ANON_KEY`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNmZHRyZndjcXVpdmx0cWpqbmx3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUxODQ2NDksImV4cCI6MjA4MDc2MDY0OX0.gLDb7LmYbw1qVJ319OfTp6As6WDJERGs1PxrLyJnS_c`

### Step 5: Redeploy
Click "Trigger deploy" to rebuild with environment variables.

---

## Method 3: Deploy from Git Repository

### Step 1: Push to GitHub
If you haven't already, push your code to GitHub:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

### Step 2: Connect to Netlify
1. Go to https://app.netlify.com
2. Click "Add new site" > "Import an existing project"
3. Choose "GitHub" (or your Git provider)
4. Authorize Netlify to access your repositories
5. Select your repository

### Step 3: Configure Build Settings
Netlify will auto-detect settings, but verify:
- **Build command**: `npm run build`
- **Publish directory**: `dist`
- **Base directory**: (leave empty)

### Step 4: Add Environment Variables
Before deploying, click "Show advanced" > "New variable":
- `VITE_SUPABASE_URL`: `https://cfdtrfwcquivltqjjnlw.supabase.co`
- `VITE_SUPABASE_ANON_KEY`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNmZHRyZndjcXVpdmx0cWpqbmx3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUxODQ2NDksImV4cCI6MjA4MDc2MDY0OX0.gLDb7LmYbw1qVJ319OfTp6As6WDJERGs1PxrLyJnS_c`

### Step 5: Deploy
Click "Deploy site" and wait for the build to complete.

---

## Post-Deployment Steps

### 1. Custom Domain (Optional)
1. Go to "Domain settings"
2. Click "Add custom domain"
3. Follow the instructions to configure your DNS

### 2. Enable HTTPS
Netlify automatically provides free SSL certificates. Ensure "Force HTTPS" is enabled in Domain settings.

### 3. Set Site Name
1. Go to "Site settings" > "General"
2. Change site name to something memorable (e.g., `kentmuzik`)
3. Your site will be available at `https://kentmuzik.netlify.app`

---

## Verify Deployment

After deployment, test your site:
1. Check all pages load correctly
2. Test navigation between pages
3. Verify products load from Supabase
4. Test contact form
5. Check responsive design on mobile

---

## Troubleshooting

### Build Fails
- Check build logs in Netlify dashboard
- Ensure all dependencies are in `package.json`
- Verify environment variables are set correctly

### Page Not Found (404) on Refresh
- This should be handled by `netlify.toml` redirects
- If still occurs, check that `_redirects` file exists in `dist` folder

### Products Not Loading
- Verify Supabase environment variables are set
- Check browser console for errors
- Ensure Supabase database has data

### Images Not Loading
- Check that all image paths are correct
- Verify images in `public` folder are being copied to `dist`

---

## Continuous Deployment

If using Method 3 (Git), Netlify will automatically:
- Deploy every push to main branch
- Create preview deployments for pull requests
- Run build checks before deploying

---

## Support

If you encounter issues:
1. Check Netlify build logs
2. Review browser console errors
3. Visit Netlify documentation: https://docs.netlify.com
4. Contact Netlify support

---

## Important Files

- `netlify.toml`: Netlify configuration
- `dist/_redirects`: SPA routing rules
- `.env`: Local environment variables (NOT deployed)
- `package.json`: Build scripts and dependencies
