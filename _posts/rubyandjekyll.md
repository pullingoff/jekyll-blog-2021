---
title: "jekyll serve Permission Error on Mac OS Monterey"
layout: post
date: 2022-02-15 11:00
# bannerpic: /assets/images/markdown.jpg
headerImage: false
tag:
- blog
- github page
- ruby
- jekyll

category: blog
author: Hailey Park
description:
---

# Jekyll serve Permission Error on Mac OS Monterey

Facing with many errors while setting up a Jekyll github page, I'm logging it for the people like me.

The problom was, I wanted to run the local server with the instruction

```
bundle exec jekyll serve
```
but the terminal showed me **Permission errors**.  

Some said I should **change the system preference to give iTerm the full disk access** but I don't think it was the reason.

Thanks to Vidyut, I **solved the error** and the helpful link is 
https://luther.io/macos/how-to-install-latest-ruby-on-a-mac/

## To do list 
- [ ] Delete previous Gemfile.lock
- [ ] Install Command Line Tools for Xcode
- [ ] Install Homebrew.
- [ ] Install rbenv and helpers.
- [ ] Modify your shell startup script.
- [ ] Install Ruby.
- [ ] Install Bundle
- [ ] Bundle add webrick



For me, it was the problem **I didn't install 'Command Line Tools for Xcode'.**

Also, you need to remove the **Gemfile.lock** in your github page directory before you install bundle.

I followed his track and reinstalled homebrew, ruby, and jekyll.

And after 'bundle exec jekyll serve', 

```
 ~/H/hailey99.github.io  on master !4  bundle exec jekyll serve
Configuration file: /Users/blah/blah/hailey99.github.io/_config.yml
            Source: /Users/blah/blah/hailey99.github.io
       Destination: /Users/blah/blah/hailey99.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 2.645 seconds.
 Auto-regeneration: enabled for '/Users/blah/blah/hailey99.github.io'
                    ------------------------------------------------
      Jekyll 4.2.1   Please append `--trace` to the `serve` command 
                     for any additional information or backtrace. 
                    ------------------------------------------------
/Users/blah/.gem/ruby/3.1.0/gems/jekyll-4.2.1/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
```
Another error 😂  
It's just because **webrick got out of the default gem lists.**

All you need to do is type
```
bundle add webrick
```
then the terminal will install webrick.


And it works!