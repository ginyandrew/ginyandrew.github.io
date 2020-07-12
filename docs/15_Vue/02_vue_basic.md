---
title: Vue Basic
layout: default
parent: Vue JS
nav_order: 2
---

# Vue - Basic
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## What is directive?
a directive is some special token in the markup that tells the library to do something to a DOM element. it renders dom elements.

---
## Frequently used directive

v-if
{: .label .label-yellow} 

```vue
<div>
  Hello <span v-if="show">show me if true</span>
</div>
```
```js
new Vue({
  data: {
    show: false
  }
})
```

v-for
{: .label .label-yellow} 

```vue
<ul>
  <li v-for="item in items">{{ item }}</li>
</ul>
```
```js
new Vue({
  data: {
    items: ['apple', 'banana', 'strawberry']
  }
})
```

v-bind
{: .label .label-yellow} 

```html
<!-- why use v-bind, instead of { { } } ?  : double mustach can't be used in HTML attribute.-->
<a href="{ { link } }">google link </a> 
```

```html
<div id="app">
  <a v-bind:href="link">google link</a>
</div>
```
```js
//this is appropriate way to bind vue data in dom
new Vue({ 
  el: "#app", 
  data: {
    link:"https://google.com"
  }
})
```

v-model
{: .label .label-yellow} 

```html
<div id="app">
  <input type="text" v-model="businessname">
  { { businessname } }
</div>
```

```js
/* while double mustach { { } } is one-way data binding (only reflecting data), 
v-model is two-way data binding and user input change vue data */
new Vue({ 
  el: "#app", 
  data: {
    businessname: "sandwichshop"
  }
})
```

## Vue Component
How to create component
{: .label .label-yellow} 

```js
// create 'header' component.
Vue.component('header', {   // 'header' - app-component name 
  template: '<h1>Top header component</h1>'
});
```
```html
<!-- now we insert the 'header' component in single page application. -->
<div id="app">
  <header></header>
</div>

<!-- it will be rendered like this. -->
<div id="app">
  <h1>Top header component</h1>
</div>
```


## Vue Props
Props is used to send data from parent to child component.

```js
// parent component (app) - send 'message' to childComponent.
new Vue({
  el: '#app',
  components: {
    'child-component': childComponent
  },
  data: {
    message: 'this is message from parent component. '
  }
})
```
```js
// childComponent
var childComponent = {
  props: ['parentmessage'],
  template: '<p>{ { parentmessage } }</p>'
}
```
```html
<div id="app">
  <child-component v-bind:parentmessage="message"></child-component>
  <!-- it will print 'this is message from parent component.' -->
</div>
```

## Vue Emit
Emit is used to send data from child to parent component. 

![](/assets/images/vue_006.JPG)

<details>
<summary>Original code</summary>
	<p>
```js	
// parent component 
new Vue({
  el: '#app',
  components: {
    'child-component': childComponent
  },
  methods: {
    showAlert: function() {
      alert('child is sending this alert!');
    }
  }
})
```
```js	
//  childComponent
var childComponent = {
  methods: {
    sendEvent: function() {
      this.$emit('update');
    }
  }
}
``` 
```html
<div id="app">
  <child-component v-on:update="showAlert"></child-component>
</div>
```

	</p>
	</details>
