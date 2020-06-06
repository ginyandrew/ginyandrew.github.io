---
title: Security
layout: default
parent: Java
nav_order: 10
---

# Java - Security
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## XXS (Sross Site Scripting) Attach 

Users enter the input value with HTML tag (with '< script //>') that can be executed to attack. 
To dissable, it either needs to 'escape' the HTML tag or assigns the whitelist of allowed inputs and prohibits rest of inputs.

these methods can be implemented either on the client-side(front end) or the server-side (back end).

**Java (server-side) implementation example**

* add apache-commons-text dependency 

```xml
<dependency>
	<groupId>org.apache.commons</groupId>
	<artifactId>commons-text</artifactId>
	<version>1.8</version>
</dependency>
```
* result

```java
String escaped = StringEscapeUtils.escapeHtml4(param);
// when param is '<script>', it is transformed to  *&lt;script&gt;*
```
