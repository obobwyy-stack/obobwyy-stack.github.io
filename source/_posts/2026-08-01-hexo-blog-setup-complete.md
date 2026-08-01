---
title: Complete Hexo Blog Setup Tutorial
date: 2026-08-01 20:00:00
categories: 
  - Tutorial
  - Web Development
tags:
  - Hexo
  - Blogging
  - Static Sites
  - GitHub Pages
  - Web Development
---

## Introduction

Welcome to my first blog post! In this tutorial, I'll share my complete experience of setting up a professional technical blog using Hexo static site generator. This guide covers everything from initial setup to deployment on GitHub Pages.

## Why Hexo?

After researching various blogging platforms, I chose Hexo for several reasons:

- **Fast and lightweight**: Static site generation means lightning-fast page loads
- **Markdown support**: Write posts in Markdown with live preview
- **Powerful theming**: Beautiful themes like NexT with extensive customization
- **Free hosting**: Can be deployed to GitHub Pages at no cost
- **Git-based workflow**: Version control for all your content
- **Extensible**: Rich plugin ecosystem for additional features

## Prerequisites

Before starting, ensure you have the following installed:

- **Node.js** (v18.x or higher): `node --version`
- **npm** (v9.x or higher): `npm --version`  
- **Git** (v2.30+): `git --version`

I'm using macOS with Node.js v22.13.1, npm 10.9.2, and Git 2.39.5.

## Step 1: Installation

### Install Hexo CLI

```bash
npm install -g hexo-cli@4.3.0
```

Verify installation:
```bash
hexo version
```

### Create Blog Project

```bash
# Navigate to your desired location
cd ~

# Initialize new Hexo blog
hexo init blog
cd blog

# Install dependencies
npm install
```

## Step 2: Basic Configuration

### Main Configuration (_config.yml)

Edit `_config.yml` with your blog information:

```yaml
title: Your Blog Title
subtitle: 'A personal blog'
description: 'Your personal blog description'
keywords: blogging, programming, technology
author: Your Name
language: en
timezone: 'Asia/Shanghai'

url: http://localhost:4000  # Update later with production URL
permalink: :year/:month/:day/:title/
```

### Install Essential Plugins

```bash
# Core generators
npm install hexo-generator-archive hexo-generator-category hexo-generator-index hexo-generator-tag --save

# Feed and sitemap
npm install hexo-generator-feed hexo-generator-sitemap --save

# Search functionality
npm install hexo-generator-searchdb --save

# Deployment
npm install hexo-deployer-git --save
```

## Step 3: Theme Installation

### Install NexT Theme

```bash
npm install hexo-theme-next@latest --save
```

### Configure Theme

Create `_config.next.yml` and configure:

```yaml
# Scheme Selection
scheme: Muse

# Dark Mode
darkmode: true

# Navigation Menu
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive

# Sidebar
sidebar:
  position: left
  display: post

# Code Highlighting
codeblock:
  theme:
    light: default
    dark: stackoverflow-dark
  copy_button:
    enable: true

# Local Search
local_search:
  enable: true
  trigger: auto
```

## Step 4: Create Basic Pages

### About Page

```bash
mkdir -p source/about
cat > source/about/index.md << 'EOF'
---
title: About
---

## About Me

Welcome to my blog! I'm a developer passionate about technology and sharing knowledge.
EOF
```

### Categories and Tags Pages

```bash
# Categories page
mkdir -p source/categories
cat > source/categories/index.md << 'EOF'
---
title: Categories
type: categories
---
EOF

# Tags page  
mkdir -p source/tags
cat > source/tags/index.md << 'EOF'
---
title: Tags
type: tags
---
EOF
```

## Step 5: Testing Locally

```bash
# Clean and generate
hexo clean
hexo generate

# Start development server
hexo server
```

Visit `http://localhost:4000` to see your blog in action!

## Step 6: Git Setup

```bash
# Initialize Git repository
git init

# Create .gitignore
cat > .gitignore << 'EOF'
node_modules/
public/
.deploy_git/
db.json
*.log
.DS_Store
EOF

# Initial commit
git add .
git commit -m "Initial commit: Hexo blog setup"
```

## Step 7: GitHub Pages Deployment

### Create GitHub Repository

1. Go to GitHub and create a new repository: `username.github.io`
2. Replace `username` with your GitHub username

### Configure Deployment

Update `_config.yml`:

```yaml
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: main
```

### Deploy

```bash
# Generate static files
hexo generate

# Deploy to GitHub Pages
hexo deploy
```

Your blog will be available at `https://username.github.io`

## Advanced Configuration

### Search Functionality

The search functionality is already enabled in the NexT theme configuration. To use it:

1. Ensure `hexo-generator-searchdb` is installed
2. Add search configuration to `_config.yml`:

```yaml
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

### RSS Feed

Configure feed generation in `_config.yml`:

```yaml
feed:
  type:
    - atom
    - rss2
  limit: 20
  icon: icon.png
```

### Sitemap

```yaml
sitemap:
  path: sitemap.xml
  tags: true
  categories: true
```

## Writing Blog Posts

### Create New Post

```bash
hexo new "My New Post"
```

### Post Front Matter

```yaml
---
title: Post Title
date: 2026-08-01 20:00:00
categories:
  - Category Name
tags:
  - tag1
  - tag2
---
```

### Publishing Workflow

```bash
# 1. Create content
hexo new "article-title"

# 2. Edit content
# Edit the created markdown file

# 3. Local preview
hexo clean && hexo server

# 4. Generate and deploy
hexo generate
hexo deploy
```

## Theme Customization

### Avatar Setup

1. Place your avatar image in `source/images/avatar.gif`
2. Update `_config.next.yml`:

```yaml
avatar:
  url: /images/avatar.gif
  rounded: true
  rotated: false
```

### Social Links

```yaml
social:
  GitHub: https://github.com/yourusername || fab fa-github
  E-Mail: mailto:youremail@example.com || fa fa-envelope
  LinkedIn: https://linkedin.com/in/yourprofile || fab fa-linkedin
```

## Performance Optimization

### Enable Minification

```bash
npm install hexo-neat --save
```

Add to `_config.yml`:

```yaml
neat:
  enable: true
```

### Image Optimization

- Use compressed images
- Consider WebP format for better compression
- Implement lazy loading for images

## Troubleshooting

### Common Issues

**Port 4000 already in use:**
```bash
hexo server -p 4001
```

**Build errors:**
```bash
hexo clean
hexo generate
```

**Theme not loading:**
```bash
npm list hexo-theme-next
# Verify theme setting in _config.yml
```

## Next Steps

Now that your blog is set up, here are some ideas for next steps:

1. **Custom domain**: Set up a custom domain name
2. **Analytics**: Add Google Analytics or similar
3. **Comments**: Integrate a commenting system like Disqus or giscus
4. **SEO**: Optimize for search engines
5. **Backup**: Set up automated backups

## Conclusion

Setting up a Hexo blog is a rewarding process that gives you full control over your blogging platform. The combination of Hexo's simplicity and NexT theme's elegance creates a powerful blogging solution.

I hope this tutorial helps you get started with your own blog. Happy blogging!

## Resources

- [Hexo Documentation](https://hexo.io/docs/)
- [NexT Theme Documentation](https://theme-next.js.org/docs/)
- [GitHub Pages Guide](https://pages.github.com/)
- [Markdown Guide](https://www.markdownguide.org/)

---

*Published: August 1, 2026*
*Category: Web Development*
*Tags: Hexo, Blogging, Static Sites*
