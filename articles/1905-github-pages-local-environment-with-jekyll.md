---
title: 1905-github-pages-local-environment-with-jekyll
date: 2019/05/06 16:42
file: 1905-github-pages-local-environment-with-jekyll

---

[home](../)

# GitHub Pagesでmarkdownを公開する３：Local環境を構築

## overview

- Jekyll Themeが適用されたGitHub Pagesのrepositoryを、Local PC側でも閲覧可能とする。

[![Image from Gyazo](https://i.gyazo.com/9e342624040c91eb80a0ccb10ee18bb1.png)](https://gyazo.com/9e342624040c91eb80a0ccb10ee18bb1)

## *** reference

- Github Pagesのデフォルトテーマをローカル上でJekyllサーバで確認出来るようにする
    - https://sakanasoft.net/github-pages-by-localhost/#configure_github_pages

- The Leap day theme
    - https://github.com/pages-themes/leap-day 

## environment

```
(base) g:\workspace\www>ruby --version
ruby 2.6.3p62 (2019-04-16 revision 67580) [x64-mingw32]

(base) g:\workspace\www>bundle --version
Bundler version 2.0.1
```

## procedure

### note
- Jekyll本体とSupported Themeをまとめてinstallする`github-pages gem`を利用してinstallする。
    - Gemfileを作成して、実行する。 


### logs

#### install

- `bundle install` 

```
(base) g:\workspace\www>bundle init
Writing new Gemfile to g:/workspace/www/Gemfile

(base) g:\workspace\www>vim Gemfile

(base) g:\workspace\www>type Gemfile
# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

gem "github-pages", group: :jekyll_plugins

(base) g:\workspace\www>bundle install
Fetching gem metadata from https://rubygems.org/...........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies....
Using concurrent-ruby 1.1.5
Using i18n 0.9.5
Using minitest 5.11.3
Using thread_safe 0.3.6
Using tzinfo 1.2.5
Using activesupport 4.2.11.1
Using public_suffix 3.0.3
Using addressable 2.6.0
Using bundler 2.0.1
Using coffee-script-source 1.11.1
Using execjs 2.7.0
Using coffee-script 2.4.1
Using colorator 1.1.0
Using ruby-enum 0.7.2
Using commonmarker 0.17.13
Using dnsruby 1.61.2
Using eventmachine 1.2.7 (x64-mingw32)
Using http_parser.rb 0.6.0
Using em-websocket 0.5.1
Using ffi 1.10.0 (x64-mingw32)
Using ethon 0.12.0
Using multipart-post 2.0.0
Using faraday 0.15.4
Using forwardable-extended 2.6.0
Using gemoji 3.0.1
Using sawyer 0.8.2
Using octokit 4.14.0
Using typhoeus 1.3.1
Using github-pages-health-check 1.16.1
Using rb-fsevent 0.10.3
Using rb-inotify 0.10.0
Using sass-listen 4.0.0
Using sass 3.7.4
Using jekyll-sass-converter 1.5.2
Using ruby_dep 1.5.0
Using listen 3.1.5
Using jekyll-watch 2.2.1
Using kramdown 1.17.0
Using liquid 4.0.0
Using mercenary 0.3.6
Using pathutil 0.16.2
Using rouge 2.2.1
Using safe_yaml 1.0.5
Using jekyll 3.8.5
Using jekyll-avatar 0.6.0
Using jekyll-coffeescript 1.1.1
Using jekyll-commonmark 1.3.1
Using jekyll-commonmark-ghpages 0.1.5
Using jekyll-default-layout 0.1.4
Using jekyll-feed 0.11.0
Using jekyll-gist 1.5.0
Using jekyll-github-metadata 2.12.1
Using mini_portile2 2.4.0
Using nokogiri 1.10.3 (x64-mingw32)
Using html-pipeline 2.11.0
Using jekyll-mentions 1.4.1
Using jekyll-optional-front-matter 0.3.0
Using jekyll-paginate 1.1.0
Using jekyll-readme-index 0.2.0
Using jekyll-redirect-from 0.14.0
Using jekyll-relative-links 0.6.0
Using rubyzip 1.2.2
Using jekyll-remote-theme 0.3.1
Using jekyll-seo-tag 2.5.0
Using jekyll-sitemap 1.2.0
Using jekyll-swiss 0.4.0
Using jekyll-theme-architect 0.1.1
Using jekyll-theme-cayman 0.1.1
Using jekyll-theme-dinky 0.1.1
Using jekyll-theme-hacker 0.1.1
Using jekyll-theme-leap-day 0.1.1
Using jekyll-theme-merlot 0.1.1
Using jekyll-theme-midnight 0.1.1
Using jekyll-theme-minimal 0.1.1
Using jekyll-theme-modernist 0.1.1
Using jekyll-theme-primer 0.5.3
Using jekyll-theme-slate 0.1.1
Using jekyll-theme-tactile 0.1.1
Using jekyll-theme-time-machine 0.1.1
Using jekyll-titles-from-headings 0.5.1
Using jemoji 0.10.2
Using minima 2.5.0
Using unicode-display_width 1.5.0
Using terminal-table 1.8.0
Using github-pages 198
Bundle complete! 1 Gemfile dependency, 85 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

- view directory

```
(base) g:\workspace\www>tree /F
Folder PATH listing for volume Users
Volume serial number is 04A1-7D2F
G:.
│  .Gemfile.un~
│  .gitignore
│  .index.md.un~
│  Gemfile
│  Gemfile.lock
│  index.md
│  README.md
│  _config.yml
│
├─.sass-cache
│
├─logs
│      1905-clone-and-push-markdowns-for-jekyll-publishment.md
│      1905-github-pages-with-jekyll-publishment.md
│
└─_site
    │  index.html
    │  README.html
    │
    ├─assets
    │  ├─css
    │  ├─fonts
    │  ├─images
    │  │
    │  └─js
    │          main.js
    │
    └─logs
            1905-clone-and-push-markdowns-for-jekyll-publishment.html
            1905-github-pages-with-jekyll-publishment.html
```

#### * bundle exec jekyll serve

```
(base) g:\workspace\www>jekyll serve
Traceback (most recent call last):
        10: from C:/Ruby26-x64/bin/jekyll:23:in `<main>'
         9: from C:/Ruby26-x64/bin/jekyll:23:in `load'
         8: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/jekyll-3.8.5/exe/jekyll:11:in `<top (required)>'
         7: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/jekyll-3.8.5/lib/jekyll/plugin_manager.rb:50:in `require_from_bundler'
         6: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler.rb:107:in `setup'
         5: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:26:in `setup'
         4: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:26:in `map'
         3: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/spec_set.rb:148:in `each'
         2: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/spec_set.rb:148:in `each'
         1: from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:31:in `block in setup'
C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:319:in `check_for_activated_spec!': You have already activated liquid 4.0.3, but your Gemfile requires liquid 4.0.0. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```

```
(base) g:\workspace\www>bundle exec jekyll serve
Configuration file: g:/workspace/www/_config.yml
Invalid theme folder: _includes
Invalid theme folder: _includes
            Source: g:/workspace/www
       Destination: g:/workspace/www/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                    done in 1.448 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for 'g:/workspace/www'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

### access url
- 127.0.0.1:4000

[![Image from Gyazo](https://i.gyazo.com/e52126322ad3cb76a0c30670c689f7d5.png)](https://gyazo.com/e52126322ad3cb76a0c30670c689f7d5)

#### modify _config.yml

```
(base) g:\workspace\www>type _config.yml
title: Memoru's Page
description: This site is sample site

theme: jekyll-theme-leap-day


(base) g:\workspace\www>bundle exec jekyll serve
Configuration file: g:/workspace/www/_config.yml
Invalid theme folder: _includes
Invalid theme folder: _includes
            Source: g:/workspace/www
       Destination: g:/workspace/www/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                    done in 1.504 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for 'g:/workspace/www'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```


[![Image from Gyazo](https://i.gyazo.com/e8775aedd725d9158a69a3eb6ac08dd3.png)](https://gyazo.com/e8775aedd725d9158a69a3eb6ac08dd3)


#### git push

```
(base) g:\workspace\www>git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   _config.yml

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Gemfile
        Gemfile.lock

no changes added to commit (use "git add" and/or "git commit -a")

(base) g:\workspace\www>git add .
warning: LF will be replaced by CRLF in Gemfile.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in Gemfile.lock.
The file will have its original line endings in your working directory.

(base) g:\workspace\www>git commit -m "set local env for jekyll"
[master 80f8694] set local env for jekyll
 3 files changed, 261 insertions(+), 1 deletion(-)
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock

(base) g:\workspace\www>git push
fatal: AggregateException encountered.
   One or more errors occurred.
Username for 'https://github.com': sakai-memoru
Password for 'https://sakai-memoru@github.com':
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 2.33 KiB | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/sakai-memoru/www.git
   cb6b658..80f8694  master -> master
```


[![Image from Gyazo](https://i.gyazo.com/c9feae0bf2a34af3ff01af20786ebd21.png)](https://gyazo.com/c9feae0bf2a34af3ff01af20786ebd21)

// --- end of markdown --- //

