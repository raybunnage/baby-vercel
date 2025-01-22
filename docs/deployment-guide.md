# DHG Hub Deployment Guide

## Project Overview
This is a minimal Vite + React + TypeScript project configured for Vercel deployment, serving as a template for dhg-hub.org.

## Step-by-Step Vercel Deployment

### 1. GitHub Repository Setup
1. Ensure your code is pushed to GitHub
2. Your repository should contain:
   - `frontend/` directory with all React files
   - `.gitignore` file
   - `docs/` directory
   - `.cursorrules` file

### 2. Vercel Account Setup
1. Go to [vercel.com](https://vercel.com)
2. Sign in with your GitHub account
3. If this is your first time, Vercel will ask for permissions to access your GitHub repositories

### 3. Create New Project in Vercel
1. Click "Add New..." button
2. Select "Project" from the dropdown
3. Find and select your GitHub repository
4. Click "Import"

### 4. Configure Project Settings
In the configuration screen:
1. **Project Name**: Enter your project name (e.g., "dhg-hub")
2. **Framework Preset**: Select "Vite" from the dropdown
3. **Root Directory**: Set to `frontend`
4. **Build and Output Settings**:
   - Build Command: `npm run build` (should be auto-filled)
   - Output Directory: `dist` (should be auto-filled)
5. Click "Deploy"

### 5. Verify Deployment
1. Vercel will show the deployment progress
2. Once complete, you'll see "Congratulations! Your project has been successfully deployed"
3. Click the "Visit" button to see your live site
4. Your site will be available at: `https://your-project-name.vercel.app`

### 6. Custom Domain Setup (dhg-hub.org)
1. In your project dashboard, go to "Settings"
2. Click "Domains"
3. Enter "dhg-hub.org"
4. Follow Vercel's DNS configuration instructions

### Understanding Environments

#### Production (main branch)
- What: The live website at dhg-hub.org
- When: After merging to `main` branch
- URL: https://dhg-hub.org

#### Development (development branch)
- What: Testing environment for new features
- When: After merging feature branches
- URL: https://dev.dhg-hub.org or https://development.dhg-hub.org

#### Preview (feature branches)
- What: Temporary deployments for testing individual features
- When: On every push to feature branches
- URL: https://feature-branch-name.dhg-hub.org

### Common Tasks

#### Making Changes
1. Create a new feature branch:
   ```bash
   git checkout -b feature/my-new-feature
   ```
2. Make your changes
3. Push to GitHub:
   ```bash
   git push origin feature/my-new-feature
   ```
4. Vercel automatically creates a preview deployment
5. Check your changes at the preview URL

#### Troubleshooting
- **Build Fails**: Check the build logs in Vercel dashboard
- **404 Errors**: Verify the root directory setting is `frontend`
- **Styling Issues**: Ensure Tailwind CSS is building correctly

## Project Structure
```
.
├── frontend/          # React application
│   ├── src/          # Source code
│   ├── public/       # Static assets
│   └── package.json  # Dependencies and scripts
└── docs/             # Documentation
```

## Need Help?
- Check Vercel's deployment logs for detailed error messages
- Review build settings in Vercel project dashboard
- Ensure all environment variables are properly set

## Environment Setup
- Production (main branch)
- Development (development branch)
- Preview (feature branches)

## Local Development
1. Install dependencies:
   ```bash
   cd frontend
   npm install
   ```

2. Start development server:
   ```bash
   npm run dev
   ```

## Deployment
### Vercel Configuration
1. Connect your GitHub repository to Vercel
2. Configure project settings:
   - Framework Preset: Vite
   - Root Directory: `frontend`
   - Build Command: `npm run build`
   - Output Directory: `dist`

### Branch Strategy
- `main` → Production (dhg-hub.org)
- `development` → Development environment
- `feature/*` → Preview deployments

## Project Structure 