---
title: Git basic command line
layout: default
parent: Git and CL
nav_order: 1
---

# Git Command line
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## **Start**

`git init`

`git clone URL `

`git remote add origin URL `connect local repo to remote repo (URL)

`git add .` all files in the folder

`git add -A ` only changed files

`git status  `

`git commit -m "comment"`  staging 

`git reset`  cancel staging 

`git push origin master` 


---

## **Advanced**
* how to revert back to particular commit

get commit number which you want to go back to 

```
$ git log
```

result

{% highlight markdown %}

commit 6843810259be199b6ce28529db23eef77b5f75c8 (HEAD -> master, origin/master, origin/HEAD)
Author: ginyandrew <ginyandrew@gmail.com>
Date:   Mon May 25 10:28:08 2020 -0400

    customize jekyll theme code color

commit 20228c91928378c63d7d751378073480e9a44db6
Author: ginyandrew <ginyandrew@gmail.com>
Date:   Mon May 25 10:18:06 2020 -0400

    update code css

commit 65f84e5039bafd09c3c048a1db083f8ed1fe3f0c
Author: ginyandrew <ginyandrew@gmail.com>
Date:   Mon May 25 10:14:46 2020 -0400

    update config
{% endhighlight %}


if you want to go back to 2nd commit (starting 20228c91)

```
git reset --hard 20228c91 

git push -f origin master(branch name)
```

**Warning** it removes entire commit history 

## **Branch**

`git branch  ` check which branch im in

`git branch BRANCHNAME`  create a new branch 

`git checkout BRANCHNAME `switch remote repo to the branch

`git push origin BRANCHNAME ` now push to the switched branch only

---

## **Disconnect remote repo from local repo**

It removes .git file to disconnect remote repo from local repo


```
find ./ -name ".git" | xargs rm -Rf

find ./ -name ".gitignore" | xargs rm -Rf
```
