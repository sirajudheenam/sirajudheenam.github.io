---
title: "How I deployed a Hugo Site on my github page"
date: 2022-03-08T12:03:27+05:30
draft: false
---

# Instructions to publish a site. 

```
brew install hugo
hugo version
hugo new site blog
cd blog
# add a theme
# list of themes: https://themes.gohugo.io/
git init.
git submodule add https://github.com/razonyang/hugo-theme-bootstrap themes/hugo-theme-bootstrap
echo theme = \"hugo-theme-bootstrap\" >> config.toml
hugo new posts/my-first-post.md

cat >> posts/my-first-post.md <<EOF
---
title: "First Post"
date: 2019-03-26T08:47:11+01:00
draft: false
---

# This is the heading of my first post
EOF
hugo server
# or For full rebuilds on change:
hugo server --disableFastRender

http://localhost:1313/



Create a file in `.github/workflows/gh-pages.yml` with below content.

mkdir -p .github/workflows
vim .github/workflows/gh-pages.yml

```yaml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public 
```
Now add everything to github.

```
echo "# blog" >> README.md
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/sirajudheenam/blog.git
git push -u origin main

# If everything works fine, then create a gh-pages branch on your github.

git branch -b gh-pages

# If you push anything, then it will build and generate hugo static pages and push to `gh-pages` branch.
```