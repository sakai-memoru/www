---
title: 1905-clone-and-push-markdowns-for-jekyll-publishment
date: 2019/05/06 14:39
file: 1905-clone-and-push-markdowns-for-jekyll-publishment

---
## *** overview
- GitHub repositoryと連携して、GitHub Pagesにmarkdownファイルを公開する。

[![Image from Gyazo](https://i.gyazo.com/9e342624040c91eb80a0ccb10ee18bb1.png)](https://gyazo.com/9e342624040c91eb80a0ccb10ee18bb1)

## *** relative posts
- 1905-github-pages-with-jekyll-publishment
    - GitHubにrepositoryを作成して、README.mdを公開してみた
    - http://sakai-memoru.hateblo.jp/entry/1905-github-pages-with-jekyll-publishment

## *** reference
- 

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





// --- end of markdown --- //
