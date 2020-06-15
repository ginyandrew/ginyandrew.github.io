---
title: Basic
layout: default
parent: Vue JS
nav_order: 1
---

# Vue - Basic 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
##Basic NPM command line 


---
## Basic Vue Config setup
**how to chage port number of vue-cli project** : in webpack.config.js,

```json
module: {
	devServer: { port: 9000} }
```
	
---
## How to initiate a new Vue project
check if vue is installed and version. if not installed, install it.
```shell
vue --version    #@vue/cli 4.3.1  
npm install -g @vue/cli
vue create myProjectName  #select 'default' and all pre-set selected options and complete installing.
```
Once the installation is completed, you can run the Vue server.
```shell
npm run serve
# DONE  Compiled successfully in 3655ms4:40:06 PM
#<s> [webpack.Progress] 100%
# App running at:
#  - Local:   http://localhost:8080/
#  - Network: http://192.168.1.163:8080/
```
**Tada ~** 

![](/assets/images/vue_001.JPG)


---
## how to integrate Vue project in Spring boot
Once spring boot is initiated,  move to SpringProjectName/src.  In Src folder, initiate a new Vue Project.

```powershell
Gin@DESKTOP- .. workspace/SpringProjectName/src (master)
$ vue create vue-project-name 
# vue project is initiated.
$ cd vue-project-name
Gin@DESKTOP- .. workspace/SpringProjectName/src/vue-project-name (master)
```

now, set up where dist folder (compiled file of Vue project) will be created.

create a new file '`vue.config.js`' in /ProjectName/src/vue-project-name (root folder of Vue project)  with the json below.

```json
module.exports= {
	outputDir: "../main/resources/static",
	indexPath: "../static/index.html"
}
```

now build the vue project.
```powershell
npm run build
```

and you can see the dist folder with Vue compiled files in **/src/main/resources/static** folder.

![](/assets/images/vue_002.JPG)

Now run the spring boot project. check the port number in application.properties file.
```properties
server.port=8081
```

once Spring project is running, you can check at  _http://localhost:8081/index.html_
