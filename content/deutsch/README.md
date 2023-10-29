# sirajudheen.netlify.app

Hugo Personal Website on netlify and github pages

- create personal site on github (<git-username>.github.io)
- clone the repo locally (`git clone https://github.com/sirajudheenam/<git-username>.github.io`)
- install hugo (`brew install hugo`)
- create a site with Hugo (hugo new site hugo_personal_site)
- cd hugo_personal_site
- git init
- git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/paperMod
- echo "theme: 'paperMod'" >> config.yaml
- hugo server --buildDrafts # with a flag to build the draft for preview
- create a github actions for hugo on github settings for pages, where you can create a config file and commit it.
- To deploy using `GitHub Actions for Hugo`. 
- create a config file in `.github/workflows/hugo.yml`




