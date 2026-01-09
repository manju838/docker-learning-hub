This file contains code snippets for this initial repo creation.

This repo is first created locally and then directly pushed to GitHub using code, no repo is created in Browser before pushing changes.

```bash
# 1. Clone and reset
git clone https://github.com/hayk96/trafficlight-docker-challenge.git docker-learning-hub
cd docker-learning-hub
rm -rf .git
git init

# 2. Create structure
mkdir -p {docs,v0-fundamentals,v1-persistence,v2-caching,v3-sql,tests,.github/workflows}

# 3. Initialize Git
git add .
git commit -m "Initial commit: Project structure"

# 4. Create GitHub repo
gh repo create docker-learning-hub --public --source=. --remote=origin

# 5. Rename 'master' to 'main'
git branch -M main

# 6. Push to GitHub
git push -u origin main
```