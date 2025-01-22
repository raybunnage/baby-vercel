# DHG Hub Deployment Guide

## Project Overview
This is a minimal Vite + React + TypeScript project configured for Vercel deployment, serving as a template for dhg-hub.org.

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