---
title: 1905-clone-and-push-markdowns-for-jekyll-publishment
date: 2019/05/06 14:39
file: 1905-clone-and-push-markdowns-for-jekyll-publishment

---
[home](../)

# **** GitHub Pagesでmarkdownを公開する２：Repositoryをcloneし,markdownをpushする

## *** overview
- GitHub repositoryと連携して、GitHub Pagesにmarkdownファイルを公開する。

[![Image from Gyazo](https://i.gyazo.com/9e342624040c91eb80a0ccb10ee18bb1.png)](https://gyazo.com/9e342624040c91eb80a0ccb10ee18bb1)

## *** relative posts
- 1905-github-pages-with-jekyll-publishment
    - GitHubにrepositoryを作成して、README.mdを公開してみた
    - http://sakai-memoru.hateblo.jp/entry/1905-github-pages-with-jekyll-publishment

## *** reference
- N/A

## *** procedure

### ** note
- Jekyllを使ってGitHub Pagesで、markdownを公開するようにしたrepositoryを、 Localにcloneして、markdownを追加して、pushして公開してみる。

### ** logs

#### * git clone

```
(base) g:\workspace>git clone https://github.com/sakai-memoru/www.git
Cloning into 'www'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 13 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (13/13), done.

(base) g:\workspace\www>powershell ls


    Directory: G:\workspace\www


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/6/2019     15:11            278 README.md
-a----         5/6/2019     15:11             28 _config.yml

```

#### * modify index.md

```
(base) g:\workspace\www>type index.md
---
---

# memoru's page

## *** overview
- GitHub repository で、markdown filesを公開！

## *** contents

### ** Jekyll
    + [./logs/1905-github-pages-with-jekyll-publishment.md](./logs/1905-github-pages-with-jekyll-publishment.html)

    + [./logs/1905-clone-and-push-markdowns-for-jekyll-publishment.md](./logs/1905-clone-and-push-markdowns-for-jekyll-publishment.html)

// --- end of index --- //
```

#### * add /logs/1905-github-pages-with-jekyll-publishment.md, etc
- Save target md files as UTF-8.

```
(base) g:\workspace\www\logs>powershell ls


    Directory: G:\workspace\www\logs


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/6/2019     15:33           2087 1905-clone-and-push-markdowns-for-jekyll-publishment.md
-a----         5/6/2019     15:32           2502 1905-github-pages-with-jekyll-publishment.md
```

#### * create .gitignore from gibo template

```
(base) g:\workspace\www>gibo dump vim python jekyll > .gitignore

(base) g:\workspace\www>ls

(base) g:\workspace\www>powershell ls


    Directory: G:\workspace\www


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/6/2019     15:33                logs
-a----         5/6/2019     15:35           1607 .gitignore
-a----         5/6/2019     15:25          13022 .index.md.un~
-a----         5/6/2019     15:26            407 index.md
-a----         5/6/2019     15:11            278 README.md
-a----         5/6/2019     15:11             28 _config.yml
```

#### * git commit and push

```
(base) g:\workspace\www>git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore
        index.md
        logs/

nothing added to commit but untracked files present (use "git add" to track)

(base) g:\workspace\www>git add .
warning: LF will be replaced by CRLF in logs/1905-clone-and-push-markdowns-for-jekyll-publishment.md.
The file will have its original line endings in your working directory.

(base) g:\workspace\www>git commit -m "add index.md and logs"
[master 3f72697] add index.md and logs
 4 files changed, 298 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 index.md
 create mode 100644 logs/1905-clone-and-push-markdowns-for-jekyll-publishment.md
 create mode 100644 logs/1905-github-pages-with-jekyll-publishment.md

(base) g:\workspace\www>git push
fatal: AggregateException encountered.
   One or more errors occurred.
Username for 'https://github.com': sakai-memoru
Password for 'https://sakai-memoru@github.com':
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (7/7), 3.26 KiB | 0 bytes/s, done.
Total 7 (delta 0), reused 0 (delta 0)
To https://github.com/sakai-memoru/www.git
   864f39e..3f72697  master -> master
```

#### * access url

- index
    - https://sakai-memoru.github.io/www/ 

- logs/1905-github-pages-with-jekyll-publishment.html
    - https://sakai-memoru.github.io/www/logs/1905-github-pages-with-jekyll-publishment.html


[![Image from Gyazo](https://i.gyazo.com/63f0cf961c90a445ed2772e29376f6d8.png)](https://gyazo.com/63f0cf961c90a445ed2772e29376f6d8)


[![Image from Gyazo](https://i.gyazo.com/92e3c574ceff89ebb078aaa91c0d98ee.png)](https://gyazo.com/92e3c574ceff89ebb078aaa91c0d98ee)

### ** notice
- mdが、utf-8でない場合など、GitHub側のJekyllのgenerationでerrorが発生すると、以下のmailが飛んでくる。（GitHubも、LocalでJekyllを動かして、正しく生成されることを確認して、pushすることを推奨している）


[![Image from Gyazo](https://i.gyazo.com/2ef5f5af34c20cb44c8490f46d2a2423.png)](https://gyazo.com/2ef5f5af34c20cb44c8490f46d2a2423)

- 次のpostで、LocalでのJekyllの確認について、記述する

// --- end of markdown --- //
