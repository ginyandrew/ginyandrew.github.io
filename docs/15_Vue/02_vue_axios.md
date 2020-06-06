---
title: Axios
layout: default
parent: Vue JS
nav_order: 2
---

# Vue - Axios 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## What is Axios ?  
one of HTTP clicnt library. It helps to use Ajax request in Vue.js

* Ajax (Axynchronous javascript And Xml) - loading data by using XmlHttpRequest (API transferring data between server-web browser) object 

---

## Axios basic
### how to access to 'this' in axios
* example

```js
data: function(){
	return { param: ""}
},
methods() {
	getFnc: function(){
		var self = this;
		axios.get("url").then (function(response){
			self.param = response.data;
		})
	}
}
```
