---
layout: post
title:  "Story of rubytracer and libv8"
date:   2022-02-18 06:04:21 +0530
categories: jekyll install
# author: siraj
---
I was trying to install jekyll on my macOS.

{% highlight bash %}
bundle install
{% endhighlight %}

{% highlight log %}
$HOME/.rvm/gems/ruby-3.0.0/gems/libv8-3.16.14.19/ext/libv8/location.rb:50:in `configure': By using --with-system-v8, you have
chosen to use the version  (Libv8::Location::System::NotFoundError)
of V8 found on your system and *not* the one that is bundled with
the libv8 rubygem.

However, your system version of v8 could not be located.

Please make sure your system version of v8 that is compatible
with 3.16.14.19 installed. You may need to use the
--with-v8-dir option if it is installed in a non-standard location
	from $HOME/.rvm/gems/ruby-3.0.0/gems/libv8-3.16.14.19/lib/libv8.rb:7:in `configure_makefile'
	from extconf.rb:32:in `<main>'

To see why this extension failed to compile, please check the mkmf.log which can be found here:

  $HOME/.rvm/gems/ruby-3.0.0/extensions/x86_64-darwin-21/3.0.0/therubyracer-0.12.3/mkmf.log

extconf failed, exit code 1

Gem files will remain installed in $HOME/.rvm/gems/ruby-3.0.0/gems/therubyracer-0.12.3 for inspection.
Results logged to $HOME/.rvm/gems/ruby-3.0.0/extensions/x86_64-darwin-21/3.0.0/therubyracer-0.12.3/gem_make.out

An error occurred while installing therubyracer (0.12.3), and Bundler cannot continue.
Make sure that `gem install therubyracer -v '0.12.3' --source 'https://rubygems.org/'` succeeds before bundling.

In Gemfile:
  therubyracer
{% endhighlight %}

After researching a while, the solution is

{% highlight bash %}
brew install v8-315
gem install libv8 -v '3.16.14.19' -- --with-system-v8
gem install therubyracer -- --with-v8-dir=/usr/local/opt/v8@3.15
bundle install
{% endhighlight %}

