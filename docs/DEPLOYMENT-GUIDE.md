# GitHub Pages Deployment Guide

## 📋 Overview
This guide walks you through deploying your Docker Learning Hub to GitHub Pages and managing your site.

---

## 🚀 Initial Deployment Steps

### Step 1: Push Your Code to GitHub

```bash
# Navigate to your project directory
cd docker-learning-hub

# Check current status
git status

# Add all changes
git add .

# Commit your changes
git commit -m "Add new pages and enhance landing page for GitHub Pages"

# Push to GitHub
git push origin main
```

### Step 2: Enable GitHub Pages

1. **Navigate to your repository** on GitHub:
   - URL: `https://github.com/manju838/docker-learning-hub`

2. **Go to Settings**:
   - Click the "Settings" tab in the top navigation

3. **Find Pages section**:
   - Scroll down the left sidebar
   - Click on "Pages"

4. **Configure the source**:
   - **Source**: Select "Deploy from a branch"
   - **Branch**: Select `main` (or `master` if that's your default branch)
   - **Folder**: Select `/docs` ⚠️ **IMPORTANT** - Your Jekyll site is in the docs folder!
   - Click "Save"

5. **Wait for deployment**:
   - GitHub Actions will automatically build your site
   - This takes 1-3 minutes typically
   - You'll see a green checkmark when complete

### Step 3: Access Your Live Site

Your site will be available at:
```
https://manju838.github.io/docker-learning-hub/
```

---

## 📄 How to Add More Pages

### Method 1: Create a Simple Page

Create a new `.md` file in the `docs/` folder:

```markdown
---
layout: page
title: Your Page Title
nav_order: 5
---

# Your Page Title
{: .fs-9 }

Your subtitle here
{: .fs-6 .fw-300 }

---

## Section 1

Your content here...

## Section 2

More content...
```

**Key elements explained:**
- `layout: page` - Uses the standard page layout
- `title` - Appears in browser tab and navigation
- `nav_order` - Controls position in navigation menu (lower numbers appear first)
- `{: .fs-9 }` - Jekyll styling class for font size
- `---` - Creates horizontal dividers

### Method 2: Create a Page with Subsections

For pages with child pages (like a tutorial series):

**Parent page** (`docs/tutorials.md`):
```markdown
---
layout: page
title: Tutorials
nav_order: 4
has_children: true
---

# Docker Tutorials
{: .fs-9 }

Step-by-step guides for mastering Docker
{: .fs-6 .fw-300 }
```

**Child page** (`docs/tutorials/basic-commands.md`):
```markdown
---
layout: page
title: Basic Commands
parent: Tutorials
nav_order: 1
---

# Docker Basic Commands

Learn the essential Docker CLI commands...
```

### Method 3: Create a Page in a Subdirectory

For better organization, create folders:

```
docs/
├── index.md
├── about.md
├── tutorials/
│   ├── index.md
│   ├── beginner.md
│   ├── intermediate.md
│   └── advanced.md
└── guides/
    ├── installation.md
    └── troubleshooting.md
```

---

## 🎨 Customization Options

### Update Site Configuration

Edit `docs/_config.yml`:

```yaml
# Jekyll Configuration File
title: Docker Learning Hub
description: Master Docker from basics to production
theme: architect
url: https://manju838.github.io
baseurl: /docker-learning-hub
search_enabled: true
color_scheme: dark

# Additional options you can add:
logo: "/assets/images/logo.png"
aux_links:
  "GitHub": "https://github.com/manju838/docker-learning-hub"
  "Contribute": "https://github.com/manju838/docker-learning-hub/issues"

# Footer content
footer_content: "Copyright &copy; 2026 Docker Learning Hub. Distributed under the MIT License."
```

### Add Custom CSS

Create `docs/assets/css/custom.css`:

```css
/* Custom styles for your site */
.btn-primary {
  background-color: #0066cc;
}

.highlight {
  background-color: #f4f4f4;
  padding: 10px;
  border-radius: 5px;
}
```

Then reference it in your `_config.yml` or pages.

---

## 🔧 Common Page Elements

### Buttons

```markdown
[Button Text](link-url){: .btn .btn-primary }
[Secondary Button](link-url){: .btn .btn-outline }
[Green Button](link-url){: .btn .btn-green }
```

### Callouts/Alerts

```markdown
{: .warning }
> This is a warning message!

{: .note }
> This is an informational note.

{: .important }
> This is important information!
```

### Code Blocks

````markdown
```bash
# This is a bash code block
docker run hello-world
```

```python
# This is a Python code block
print("Hello, Docker!")
```
````

### Tables

```markdown
| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Row 1    | Data     | Data     |
| Row 2    | Data     | Data     |
```

### Images

```markdown
![Alt text](/assets/images/diagram.png)
```

### Links

```markdown
[Internal link](page-name)
[External link](https://example.com)
[Link with title](page-name "Hover text")
```

---

## 🔄 Updating Your Site

Every time you make changes:

```bash
# 1. Make your changes to .md files

# 2. Check what changed
git status

# 3. Add changes
git add .

# 4. Commit with a descriptive message
git commit -m "Add new tutorial page on Docker volumes"

# 5. Push to GitHub
git push origin main

# 6. Wait 1-3 minutes for GitHub Pages to rebuild
```

---

## 📁 Recommended Site Structure

```
docs/
├── index.md                    # Landing page
├── about.md                    # About the project
├── getting-started.md          # Installation & setup
├── resources.md                # Learning resources
├── fundamentals/
│   ├── index.md               # Fundamentals overview
│   ├── images.md              # Docker images
│   ├── containers.md          # Docker containers
│   └── commands.md            # Basic commands
├── networking/
│   ├── index.md               # Networking overview
│   ├── bridge-networks.md     # Bridge networks
│   └── port-mapping.md        # Port mapping
├── orchestration/
│   ├── index.md               # Orchestration overview
│   ├── docker-compose.md      # Docker Compose
│   └── multi-container.md     # Multi-container apps
├── advanced/
│   ├── index.md               # Advanced topics
│   ├── security.md            # Security best practices
│   └── production.md          # Production deployment
└── assets/
    ├── images/                # Image files
    └── css/                   # Custom CSS
```

---

## ✅ Testing Locally (Optional)

To preview your site locally before pushing:

```bash
# Install Jekyll (requires Ruby)
gem install bundler jekyll

# Navigate to docs folder
cd docs

# Create Gemfile if it doesn't exist
echo "source 'https://rubygems.org'" > Gemfile
echo "gem 'github-pages', group: :jekyll_plugins" >> Gemfile

# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve

# Open in browser: http://localhost:4000/docker-learning-hub/
```

---

## 🐛 Troubleshooting

### Site not updating after push
- Check the "Actions" tab in GitHub for build errors
- Wait 3-5 minutes for changes to propagate
- Clear your browser cache (Ctrl+Shift+R)

### 404 errors on pages
- Ensure `baseurl` in `_config.yml` is correct: `/docker-learning-hub`
- Use relative links without leading slash: `[Link](page-name)` not `[Link](/page-name)`

### Theme not applying
- Verify theme name in `_config.yml`
- Check if theme is supported by GitHub Pages
- Supported themes: https://pages.github.com/themes/

### Navigation not showing
- Ensure `nav_order` is set in front matter
- Check that `title` is defined
- Verify YAML front matter syntax (three dashes before and after)

---

## 📚 Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [Jekyll Themes](https://jekyllrb.com/docs/themes/)

---

## 🎯 Quick Reference

### Page Template
```markdown
---
layout: page
title: Page Title
nav_order: 1
---

# Page Title
{: .fs-9 }

Subtitle
{: .fs-6 .fw-300 }

---

## Content Section

Your content here...
```

### Deployment Checklist
- [ ] Create/edit `.md` files in `docs/` folder
- [ ] Add YAML front matter to each page
- [ ] Set appropriate `nav_order` values
- [ ] Test links are working
- [ ] Commit changes: `git commit -m "message"`
- [ ] Push to GitHub: `git push origin main`
- [ ] Wait for deployment (check Actions tab)
- [ ] Verify changes at `https://manju838.github.io/docker-learning-hub/`

---

**Happy Publishing! 🚀**
