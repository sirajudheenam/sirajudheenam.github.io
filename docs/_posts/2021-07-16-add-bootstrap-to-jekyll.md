---
layout: post
title:  "Add Bootstrap CSS to Jekyll site"
date: 2021-07-15 01:02:21 +0530
author: Sirajudheen Mohamed Ali
categories: jekyll
---

```bash
# Create a directory, if it does not exist
mkdir _scss
cd _sass

# Clone Bootstrap git repo as submodule
git submodule add https://github.com/twbs/bootstrap.git
cd bootstrap

# Get the latest tag
git tag

# Do git checkout to the latest version
git checkout v5.0.2

# create a styles.scss file under `css` directory.
mkdir css
cat << 'EOF' >> css/styles.scss
---

---
@import  "main";
EOF 

# create an empty file called variables.scss under `_sass`
touch _sass/variables.scss

cat << 'EOF' >> _sass/main.scss
@import  "variables";
@import  "bootstrap/scss/bootstrap";
EOF

# Add the following code to `_config.yml` file
cat << 'EOF' >> _config.yml
sass:
  sass_dir: _sass
  style: compressed
EOF

# Add the following files to your Gemfile
gem 'jekyll-autoprefixer'
gem 'therubyracer'

# Add these plugins to `_config.yaml` file.

cat << 'EOF' >> _config.yml
plugins:
  - jekyll-feed
  - jekyll-seo-tag
  - jekyll-autoprefixer
EOF

```