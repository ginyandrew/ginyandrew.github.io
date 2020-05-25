---
title: JS ES6
layout: default
parent: Javascript
nav_order: 5
---

# Javascript - ES6 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## **Promise** 

Javascript is single thread and Asynchronous processing model 

```js
console.log('1');
axios.get('http://localhost:8081/test').then (function (response){ console.log(2) })
console.log('3');
```

Result ( while waiting for 2nd task to be completed, it continues to move on)
```console
1,3,2 
```

to prevent this, we use callback, but it makes using try-catch very difficult.

Promise is a library to resolve this issue, and now ES6 supports it.     

---

* **Promise example**

```js
// create promise 
const thePm = function(value){
	return new Promise(function (resolve, reject){
		if (value) {
			resolve("resolve! ");
		} else {
			reject ("reject! ");
		}
	});
}

// execute promise
thePm(true).then(function(result){
	console.log(result);  // it prints 'resolve!'
}, function (err){
	console.log(err);  // it prints 'reject!'
} )
```

* **Promise example 2**

```js
// before Promise applied
function getData(callbackFunc) {
	$.get('http://localhost:8081/test', function(response) {
		callbackFunc(response); // received the data from server, and pass to callback function
	});
}
getData(function(result){
	console.log(result); // response above is sent to this 'result'
})

// after Promise applied
function getData(callbackFunc) {
	return new Promise(function(resolve, reject){  // new Promise() is added
		$.get('http://localhost:8081/test', function(response) {
			resolve(response); // once data is received, call resolve() method.
		});
	});
}
getData().then (function(result){  //'then' is added. once getData() above is completed, then- is executed.
	console.log(result); // response above is sent to this 'result'
})

```
