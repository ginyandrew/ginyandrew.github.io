---
title: Apply Jekyll to Git Page
layout: default
parent: Git and CL
nav_order: 2
---

# Git Command line
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


---
- **what is Jekyll?**

A Static complier. It complies .md (markdown), .yml to run in WEB. it is built in Ruby.

---

## Install Jekyll

**(1) Install Ruby**

go to [Ruby](https://rubyinstaller.org/downloads) and download the most stable version Ruby+Devkit 
![](../../assets/images/git001_ruby.png)

Double click and install.

**(2) Verify the installation**

```
ruby --version
```

**(3) Install Jekyll**

```
gem install Jekyll

gem install bundler
```

**(4) add 'admin' plug in**

open 'Gemfile' file from the root folder and add the line below at the bottom

```
gem 'jekyll-admin', group: :jekyll_plugins
```

**(5) deploy Jekyll again to apply the new admin plug in, and check at [admin page](http://localhost:4000/admin)**

```
bundle install

jekyll serve
```

---
## Apply jekyll theme

- **Search 'Jekyll free theme' and download git source , unzip the files and copy all files to the root folder of the github page project**

![](../../assets/images/git002_jekyll.png)

Copy all files from theme project to your root project folder, except for _config.xml and gemfile.

compare config.xml and gemfile and edit the original accordingly.

once copy is completed, compile again and run it.

```
bundle install

jekyll serve
```

Git deploys everytime commit is done. If deployment fails, it sends an warning email to alarm user failure of the deployment with the reason.
