# GitHub → Netlify Deployment Guide

## Step 1: Create GitHub Repository
1. Go to https://github.com/new
2. Repository name: `pharmcare-pro-mvp`
3. Description: "PharmaCare Pro - MVP Demo"
4. **Keep it Private** (or Public if you want)
5. **DO NOT** initialize with README, .gitignore, or license
6. Click "Create repository"

## Step 2: Push Code to GitHub
Copy and run these commands in your terminal (from the MVP directory):

```bash
git remote add origin https://github.com/YOUR_USERNAME/pharmcare-pro-mvp.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

## Step 3: Connect to Netlify
1. Go to https://app.netlify.com/
2. Click "Add new site" → "Import an existing project"
3. Choose "GitHub"
4. Authorize Netlify to access your repositories
5. Select `pharmcare-pro-mvp`
6. **Build settings**:
   - Build command: `npm run build`
   - Publish directory: `dist`
7. **Environment variables** (CRITICAL):
   - Click "Add environment variables"
   - Add each variable separately:
     
     **Variable 1:**
     - Key: `VITE_SUPABASE_PROJECT_ID`
     - Value: `luhbkhosuawobupmzzrv`
     
     **Variable 2:**
     - Key: `VITE_SUPABASE_PUBLISHABLE_KEY`
     - Value: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imx1aGJraG9zdWF3b2J1cG16enJ2Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjA0NjM1NTAsImV4cCI6MjA3NjAzOTU1MH0.P0tLyVW_RonIasOO7r1ElMB9u6ErRIZVb4WHxC2bBRo`
     
     **Variable 3:**
     - Key: `VITE_SUPABASE_URL`
     - Value: `https://luhbkhosuawobupmzzrv.supabase.co`

8. Click "Deploy site"

## Step 4: Get Your Live URL
- Netlify will build and deploy automatically (~2 minutes)
- You'll get a URL like: `https://pharmcare-pro-mvp.netlify.app`
- Share this with your client!

## Future Updates
Any changes you push to GitHub will automatically redeploy to Netlify.
