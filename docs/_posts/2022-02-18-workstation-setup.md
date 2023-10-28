---
layout: post
title:  "Workstation setup"
date:   2022-02-18 06:04:21 +0530
categories: workstation setup
# author: siraj
---

{% highlight bash %}

# make sublime as default editor
export EDITOR='subl -w'

# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew update
brew doctor
brew install node fish jq go yarn imagemagick
brew install libyaml libxslt sqlite
brew install automake libksba openssl pkg-config
brew install iterm wget
brew install minikube # hyperkit 
# use docker instead
# minikube start --driver=hyperkit 
# hyperkit has problems reaching internet from minikube VM as of 4 Mar 2022.
# Install docker desktop to use with minikube.
minikube start --driver=docker

# local CA cert management for development work
brew install mkcert
brew install nss

brew install postgres
# brew install v8
brew install v8@3.15
brew install gawk

# duf nice utility to see attached devices
brew install duf gpg
brew install automake libksba openssl pkg-config
brew tap heroku/brew && brew install heroku

gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys
\curl -sSL https://get.rvm.io | bash -s stable
rvm get stable --auto-dotfiles
echo rvm_auto_reload_flag=2 >> $HOME/.rvmrc

rvm get stable
rvm autolibs enable

gem install libv8 -v '3.16.14.19' -- --with-system-v8
# gem install therubyracer -v '0.12.3' -- --with-system-v8
gem install therubyracer -- --with-v8-dir=/usr/local/opt/v8@315


# Show hidden files on MacOS Finder
# Ctrl + Shift + . # Press these three buttons together.
defaults write com.apple.Finder AppleShowAllFiles true
killAll Finder

# A way to hide file
# chflags hidden <filename>

cat << 'EOF' >> $HOME/.bashrc
if type brew &>/dev/null; then
  HOMEBREW_PREFIX="$(brew --prefix)"
  if [[ -r "${HOMEBREW_PREFIX}/etc/profile.d/bash_completion.sh" ]]; then
    source "${HOMEBREW_PREFIX}/etc/profile.d/bash_completion.sh"
  else
    for COMPLETION in "${HOMEBREW_PREFIX}/etc/bash_completion.d/"*; do
      [[ -r "$COMPLETION" ]] && source "$COMPLETION"
    done
  fi
fi
EOF

source $HOME/.bashrc


# -------------------------- #
#          PYTHON            #
# -------------------------- #
# Anaconda installation
brew install anaconda
echo "export PATH=/usr/local/anaconda3/bin:$PATH" >> $HOME/.bashrc
echo "set -gx PATH /usr/local/anaconda3/bin $PATH" >> $HOME/.config/fish/config.fish
# set -gx PATH /usr/local/anaconda3/bin $PATH

cd $HOME/Development/python/pyfinance/
conda init bash
# or for fish
conda init fish
conda env list
conda activate pyfinance
conda env create -f $HOME/Dev/python/pyfinance/environment.yml

# Profile Fix:
sudo jamf recon
sudo jamf removeFramework
sudo profiles renew -type enrollment
sudo jamf recon

# Set Date:
# date {month}{day}{hour}{minute}{year}
# date 071920362021

# Install locally for a project:
# npm install --save-dev coffeescript

# Install globally to execute .coffee files anywhere:
npm install --global coffeescript


# A way to hide file
# chflags hidden <filename>


# Jekyll Related:
export SDKROOT=$(xcrun --show-sdk-path)
echo "export SDKROOT=$(xcrun --show-sdk-path)" >> ~/.bashrc
gem install --user-install bundler jekyll
bundle exec jekyll build --watch
jekyll serve --livereload

# make sure your pip matches your environment
which pip
pip install --upgrade pip
pip install django django_seed
pip install psycopg2
python3 manage.py runserver

# ----------------------------------------------------------------#
# Remote Machine - Key Addition
export USER_AT_HOST="username@host.com"
export PUBKEYPATH="$HOME/.ssh/id_rsa.pub"
ssh-copy-id -i "$PUBKEYPATH" "$USER_AT_HOST"

export LDFLAGS="-L/usr/local/opt/v8@3.15/lib"
export CPPFLAGS="-I/usr/local/opt/v8@3.15/include"

{% endhighlight %}