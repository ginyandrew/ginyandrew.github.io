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
