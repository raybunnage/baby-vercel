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

## Example Workflow: Making a Small Change

### 1. Create and Switch to Development Branch
```bash
# Create and switch to development branch
git checkout -b development
git push -u origin development
```
- Go to Vercel dashboard
- Verify development branch is deployed to development environment
- Check https://development.dhg-hub.org (or your assigned URL)

### 2. Create and Switch to Feature Branch
```bash
# Create and switch to feature branch
git checkout -b feature/update-welcome-text
```

### 3. Make a Small Change
Update the welcome text in frontend/src/App.tsx:
```tsx
function App() {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-100">
      <div className="text-center">
        <h1 className="text-4xl font-bold text-gray-800">
          Welcome to DHG Hub
        </h1>
        <p className="mt-4 text-gray-600">
          Vercel Deployment Test - Updated!
        </p>
      </div>
    </div>
  );
}
```

### 4. Test Feature Branch Locally
```bash
cd frontend
npm run dev
# Check changes at http://localhost:5173
```

### 5. Push Feature Branch and Test in Preview
```bash
git add .
git commit -m "Update welcome text"
git push -u origin feature/update-welcome-text
```
- Go to Vercel dashboard
- Find your feature branch deployment
- Test at https://feature-update-welcome-text.dhg-hub.org (or your assigned preview URL)

### 6. Merge to Development
```bash
# Switch to development branch
git checkout development

# Merge feature branch
git merge feature/update-welcome-text

# Push to trigger development deployment
git push origin development
```
- Check Vercel dashboard
- Verify changes in development environment
- Test at https://development.dhg-hub.org

### 7. Merge to Production
```bash
# Switch to main branch
git checkout main

# Merge development branch
git merge development

# Push to trigger production deployment
git push origin main
```
- Check Vercel dashboard
- Verify changes in production environment
- Test at https://dhg-hub.org

### 8. Clean Up
```bash
# Delete feature branch locally
git branch -d feature/update-welcome-text

# Delete feature branch on GitHub
git push origin --delete feature/update-welcome-text
```

### Verification Checklist
- [ ] Changes work in local development
- [ ] Changes work in feature branch preview deployment
- [ ] Changes work in development environment
- [ ] Changes work in production environment

### Troubleshooting Common Issues
- **Preview Not Updating**: Wait a few minutes, Vercel needs time to build
- **Merge Conflicts**: Resolve conflicts locally before pushing
- **Wrong Branch**: Use `git branch` to verify current branch
- **Build Failures**: Check Vercel deployment logs

### Best Practices
1. Always create feature branches from development
2. Test changes in all environments before merging
3. Use meaningful commit messages
4. Clean up feature branches after merging
5. Monitor deployment status in Vercel dashboard