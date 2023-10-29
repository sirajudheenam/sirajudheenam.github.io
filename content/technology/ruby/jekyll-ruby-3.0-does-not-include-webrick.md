---
title:  "Jekyll - Ruby 3.0 does not include webrick"
date:   2022-02-18 06:04:21 +0530
categories: jekyll install
draft: false
---

`bundle exec jekyll serve`

When I tried to serve jekyll locally I get this. 

```
cannot load such file -- webrick (LoadError)

 Incremental build: disabled. Enable with --incremental

      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.196 seconds.
 Auto-regeneration: enabled for '/Users/i072278/Development/github.com/sirajudheenam/sirajudheenam.github.io/docs'

..../.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3
:in `require': cannot load such file -- webrick (LoadError)
```

### Solution:


```
# This is because webrick is no longer a bundled gem in Ruby 3.0.
# let us add manually to our project


bundle add webrick
bundle exec jekyll serve
```

