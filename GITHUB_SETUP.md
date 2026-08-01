# GitHub Pages Setup Guide

## Current Status

✅ **Local Setup Complete**
- Blog configured and ready
- GitHub Actions workflow created
- Git repository initialized
- Remote configured: `https://github.com/caiyizeng/caiyizeng.github.io.git`

## Next Steps

### 1. Create GitHub Repository

**Option A: Manual Creation (Recommended)**

1. Visit: https://github.com/new
2. Repository name: `caiyizeng.github.io` (exact match required)
3. Set as **Public** repository
4. **Do not** initialize with README, .gitignore, or license
5. Click "Create repository"

**Option B: Using GitHub CLI**

```bash
# Install GitHub CLI first (if not installed)
# On macOS: brew install gh

# Then create repository
gh repo create caiyizeng.github.io --public --source=. --remote=origin --push
```

### 2. Push Code to GitHub

After creating the repository:

```bash
# Navigate to blog directory
cd ~/blog

# Push to GitHub
git push -u origin main
```

### 3. Configure GitHub Pages

1. Go to: https://github.com/caiyizeng/caiyizeng.github.io/settings/pages
2. Source: Select **GitHub Actions** (NOT "Deploy from a branch")
3. Click Save

### 4. Verify Deployment

1. Go to Actions tab: https://github.com/caiyizeng/caiyizizeng.github.io/actions
2. Wait for workflow to complete (~1-2 minutes)
3. Visit: https://caiyizeng.github.io

## Important Notes

- **Repository name MUST be**: `username.github.io` (exact format)
- **Must be Public repository** (GitHub Pages free tier requires public repos)
- **Source must be**: GitHub Actions (not "Deploy from branch")
- **Branch**: main (we're using main, not master)

## Troubleshooting

**If workflow fails:**
1. Check Actions tab for error messages
2. Ensure repository is public
3. Verify GitHub Actions is selected as Pages source

**If site doesn't appear:**
1. Wait 2-3 minutes for DNS propagation
2. Clear browser cache
3. Check GitHub Pages status: https://www.githubstatus.com/

## After Setup

Once deployed, update `_config.yml`:

```yaml
url: https://caiyizeng.github.io
```

Commit and push:

```bash
git add _config.yml
git commit -m "config: update production URL"
git push
```

---

*Created: August 1, 2026*
